---
title: Intégration du vérificateur de jeton multimédia
description: Intégration du vérificateur de jeton multimédia
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 0%

---


# Intégration du vérificateur de jeton multimédia

>[!NOTE]
>
>Le contenu de cette page est fourni à titre d’information uniquement. L’utilisation de cette API nécessite une licence actuelle de Adobe. Aucune utilisation non autorisée n’est autorisée.

## À propos du vérificateur de jeton multimédia {#about-media-token-verifier}

Lorsque l’autorisation réussit, l’authentification Adobe Primetime crée un jeton d’autorisation de longue durée (AuthZ).  Le jeton AuthZ est transmis côté client ou stocké côté serveur, selon la plateforme du client.  (Voir [Présentation des jetons](/help/authentication/programmer-overview.md#understanding-tokens) pour savoir comment les jetons sont stockés sur différents systèmes clients, avec d’autres détails.)


Un jeton AuthZ autorise l’utilisateur du site à afficher une ressource donnée.  La durée de vie est généralement comprise entre 6 et 24 heures, après quoi le jeton expire. **Pour un accès réel à l’affichage, l’authentification Primetime utilise le jeton AuthZ pour générer un jeton multimédia de courte durée que vous obtenez et transmettez à votre serveur multimédia.**. Ces jetons multimédias de courte durée ont une durée de vie très courte (généralement, quelques minutes).


Dans les intégrations AccessEnabler, vous obtenez le jeton multimédia de courte durée via le `setToken()` rappel. Pour les intégrations d’API sans client, vous obtenez le jeton multimédia de courte durée avec le `<SP_FQDN>/api/v1/tokens/media` appel API. Le jeton est une chaîne envoyée en texte clair, signée par l’Adobe, à l’aide de la protection des jetons basée sur PKI (Public Key Infrastructure, infrastructure de clé publique). Avec cette protection basée sur PKI, le jeton est signé à l’aide d’une clé asymétrique, émise à l’Adobe par une autorité de certification.


Comme il n’existe aucune validation côté client pour le jeton, un utilisateur malveillant peut utiliser des outils pour injecter du faux. `setToken()` appels . Par conséquent, **cannot** s&#39;appuyer simplement sur le fait que `setToken()` a été déclenché lors de la prise en compte d’un utilisateur autorisé ou non. Vous devez vérifier que le jeton de courte durée lui-même est légitime. L’outil pour effectuer la validation est la bibliothèque du vérificateur de jeton multimédia.


>[!TIP]
>
>Pour validation, vous devez transmettre toute la longueur de la chaîne de jeton renvoyée au vérificateur de jeton multimédia.

## Validation de jetons de courte durée à l’aide du vérificateur de jeton multimédia {#validate-short-livedttokens}

Nous recommandons aux programmeurs d’envoyer le jeton à un service web qui utilise la bibliothèque du vérificateur de jeton multimédia, afin de valider le jeton avant de réellement démarrer le flux vidéo. La durée de vie très courte des jetons multimédias de courte durée est définie comme suffisamment longue pour permettre des problèmes de synchronisation de l’horloge entre le serveur générant le jeton et le serveur validant le jeton, mais pas plus.



Le [Bibliothèque du vérificateur de jeton multimédia](https://adobeprimetime.zendesk.com/auth/v2/login/signin?return_to=https%3A%2F%2Ftve.zendesk.com%2Fhc%2Fen-us%2Farticles%2F204963159-Media-Token-Verifier-library&amp;theme=hc&amp;locale=en-us&amp;brand_id=343429&amp;auth_origin=343429%2Cfalse%2Ctrue){target=_blank} est disponible pour les partenaires d’authentification Primetime.



La bibliothèque du vérificateur de jeton multimédia est contenue dans l’archive Java. `mediatoken-verifier-VERSION.jar`. La bibliothèque définit :

* Une API de vérification de jeton (`ITokenVerifier` ), avec la documentation JavaDoc
* Clé publique Adobe utilisée pour vérifier que le jeton provient bien d’un Adobe
* Une implémentation de référence (`com.adobe.entitlement.test.EntitlementVerifierTest.java`) qui indique comment utiliser l’API de vérification et comment utiliser la clé publique d’Adobe contenue dans la bibliothèque pour vérifier son origine.


L’archive contient toutes les dépendances et les clés de certificat. Le mot de passe par défaut du fichier de stockage des clés de certificat inclus est &quot;123456&quot;.

* La bibliothèque de vérification requiert le JDK version 1.5 ou ultérieure.
* Utilisez votre fournisseur JCE préféré pour l’algorithme de signature &quot;SHA256WithRSA&quot;.


**La bibliothèque de vérification doit être le seul moyen utilisé pour analyser le contenu du jeton. Les programmeurs ne doivent pas analyser le jeton et extraire les données eux-mêmes, car le format du jeton n’est pas garanti et est sujet à de futurs changements.** Seule l’API de vérification est garantie pour fonctionner correctement. L’analyse directe de la chaîne peut fonctionner temporairement, mais peut entraîner des problèmes à l’avenir lorsque le format risque de changer. L’API Vérificateur récupère des informations à partir du jeton, telles que :

* Le jeton est valide (la variable `isValid()` ) ?
* L’ID de ressource associé au jeton (le `getResourceID()` ); il peut être comparé à (et il doit correspondre) l’autre paramètre de la variable `setToken()` rappel de fonction. Si elle ne correspond pas, cela peut indiquer un comportement frauduleux.
* L’heure à laquelle le jeton a été émis (`getTimeIssued()` ).
* TTL (`getTimeToLive()` ).
* Un GUID d’authentification anonyme reçu du MVPD (`getUserSessionGUID()` ).
* L’ID du distributeur qui a authentifié l’utilisateur et, dans le cas présent, le proxy-MVPD qui a fourni l’authentification pour le distributeur.

## Utilisation de l’API de vérification {#using-verifier-api}

Le `ITokenVerifier` définit les méthodes que vous utilisez pour valider l’authentification des jetons pour une ressource donnée. Utilisez la variable `ITokenVerifier` méthodes d’analyse d’un jeton reçu en réponse à un `setToken()` requête.


Le `isValid()` est le moyen Principal de valider un jeton. Il prend un argument, un ID de ressource. Si vous transmettez un identifiant de ressource nul, la méthode ne valide que l’authenticité et la période de validité du jeton.


Le `isValid()` renvoie l’une des valeurs d’état suivantes :



| VALID_TOKEN | Toutes les validations réussies |
|--------------------|-----------------------------------------|
| INVALID_TOKEN_FORMAT | Le format du jeton n&#39;est pas valide |
| INVALID_SIGNATURE | L’authenticité du jeton n’a pas pu être validée |
| TOKEN_EXPIRED | La durée de vie du jeton n’est pas valide |
| INVALID_RESOURCE_ID | Jeton non valide pour une ressource donnée |
| ERROR_UNKNOWN | Le jeton n&#39;a pas encore été validé |

Les méthodes supplémentaires offrent un accès spécifique à l’ID de ressource, à l’heure émise et à la durée de vie d’un jeton donné.

* Utilisation `getResourceID()` pour récupérer l’ID de ressource associé au jeton et le comparer à l’ID renvoyé par la requête setToken() .
* Utilisation `getTimeIssued()` pour récupérer l’heure à laquelle le jeton a été émis.
* Utilisation `getTimeToLive()` pour récupérer la durée de vie (TTL).
* Utilisation `getUserSessionGUID()` pour récupérer un GUID anonyme défini par le MVPD.
* Utilisation `getMvpdId()` pour récupérer l’identifiant du MVPD qui a authentifié l’utilisateur.
* Utilisation `getProxyMvpdId()` pour récupérer l’identifiant du proxy MVPD qui a authentifié l’utilisateur.

## Exemple de code {#sample-code}

L’archive du vérificateur de jeton multimédia contient une mise en oeuvre de référence (`com.adobe.entitlement.test.EntitlementVerifierTest.java`) et un exemple d’appel de l’API avec la classe test. Cet exemple (`com.adobe.entitlement.text.EntitlementVerifierTest.java`) illustre l’intégration de la bibliothèque de vérification de jeton dans un serveur multimédia.


```Java
package com.adobe.entitlement.test; 
import com.adobe.entitlement.verifier.CryptoDataHolder;
import com.adobe.entitlement.verifier.ITokenVerifier;
import com.adobe.entitlement.verifier.ITokenVerifierFactory;
import com.adobe.entitlement.verifier.SimpleTokenPKISignatureVerifierFactory;
import com.adobe.tve.crypto.SignatureVerificationCredential; 
import java.io.InputStream; 

public class EntitlementVerifierTest { 
    String mRequestorID = null;
    String mTokenToVerify = null;
    String mPathToCertificate = null;
    String mKeystoreType = null;
    String mKeystorePasswd = null;
    String mResourceID = null;

    public static void main(String[] args) { 
        if (args == null || args.length < 2 ) {
            System.out.println("Incorrect args: Usage: EntitlementVerifierTest requestorID tokenToVerify [resourceID]");
            return;
        } 
        String requestorID = args[0];
        String tokenToVerify = args[1];
        String pathToCertificate = "media_token_keystore.jks"; // the default keystore provided in the entitlement jar 
        String keystoreType = "jks";
        String keystorePasswd = "123456"; // password for the default keystore 
        if (requestorID == null || tokenToVerify == null) {
            System.out.println("One or more arguments is null");
            return;
        } 
        System.out.println("RequestorID: " + requestorID);
        System.out.println("token: " + tokenToVerify);
        System.out.println("cert: " + pathToCertificate);
        System.out.println("keystoretype: " + keystoreType);
        System.out.println("keystore passwd: " + keystorePasswd);
        String resourceID = null;
        if (args.length > 2) {
            resourceID = args[2];
        }
        System.out.println("Resource ID: " + resourceID);
        EntitlementVerifierTest verifier = new EntitlementVerifierTest(requestorID,
            tokenToVerify, pathToCertificate, keystoreType, keystorePasswd, resourceID);
        verifier.verifyToken();
    } 

    protected EntitlementVerifierTest(String inRequestorID,
                                      String inTokenToVerify,
                                      String inPathToCertificate,
                                      String inKeystoreType,
                                      String inKeystorePasswd, String inResourceID) {
        mRequestorID = inRequestorID;
        mTokenToVerify = inTokenToVerify;
        mPathToCertificate = inPathToCertificate;
        mKeystoreType = inKeystoreType;
        mKeystorePasswd = inKeystorePasswd;
        mResourceID = inResourceID;
    } 

    protected void verifyToken() {
        // It is expected that the SignatureVerificationCredential and 
        // CryptoDataHolder could be created at Init time in a web application 
        // and be reused for all token verifications. 
        CryptoDataHolder cryptoData = createCryptoDataHolder(mPathToCertificate, mKeystoreType, mKeystorePasswd);
        ITokenVerifierFactory tokenVerifierFactory = new SimpleTokenPKISignatureVerifierFactory();
        ITokenVerifier tokenVerifier = tokenVerifierFactory.getInstance(mRequestorID, mTokenToVerify, cryptoData);
        ITokenVerifier.eReturnValue status = tokenVerifier.isValid(mResourceID);
        System.out.println("Is token Valid? : " + status.toString());
        System.out.println("Token User ID: " + tokenVerifier.getUserSessionGUID());
        System.out.println("Token was generated at: " + tokenVerifier.getTimeIssued());

        System.out.println("Token Mvpd ID: " + tokenVerifier.getMvpdId());
        System.out.println("Token Proxy Mvpd ID: " + tokenVerifier.getProxyMvpdId());
    } 
    protected CryptoDataHolder createCryptoDataHolder(String pathToCertificate,
                                                      String keystoreType, String keystorePasswd) {
        SignatureVerificationCredential verificationCredential =
            readShortTokenVerificationCredential(pathToCertificate, keystoreType, keystorePasswd);
        CryptoDataHolder cryptoData = new CryptoDataHolder();
        cryptoData.setCertificateInfo(verificationCredential);
        return cryptoData;
    } 
    protected SignatureVerificationCredential readShortTokenVerificationCredential(String keystoreFile,
                                                                                   String keystoreType,
                                                                                   String keystorePasswd) {
        SignatureVerificationCredential cred = null; 
        if (keystoreFile != null){
            try {
                // load the keystore file 
                ClassLoader loader = EntitlementVerifierTest.class.getClassLoader();
                InputStream certInputStream =  loader.getResourceAsStream(keystoreFile);
                if (certInputStream != null) {
                    cred = new SignatureVerificationCredential(certInputStream, keystorePasswd, keystoreType);          
                }
            }
            catch (Exception e) {
                System.out.println("Error creating short token server credentials: " + e.getMessage());
            }
        }
        if (cred == null) {
            System.out.println("Error creating short token server credentials");
        } 
        return cred;
    } 
}
```
