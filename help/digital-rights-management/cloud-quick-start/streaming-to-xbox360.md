---
title: Définition du jeton XSTS dans votre lecteur
description: Définition du jeton XSTS dans votre lecteur
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 0%

---

# Diffusion en continu sur Xbox360 (facultatif) {#streaming-to-xboc360}

Primetime DRM est disponible sur la plateforme Xbox360. Cependant, seul le cas d’utilisation de la diffusion en continu protégée est pris en charge, et non la suite complète de droits de stratégie DRM. Les droits de stratégie DRM non liés à la diffusion en continu, tels que les groupes de domaines de périphérique, ne sont pas pris en charge. Le Xbox360 ignore les droits non pris en charge lors de la tentative de lecture de contenu.

Les droits Primetime DRM Policy pris en charge pour Xbox sont les suivants :
* Protection de la sortie numérique
* Date de fin de la mise en cache hors licence
* Date de début de la licence
* Date de fin de licence
* Durée de la fenêtre de lecture (secondes)

Il n’est peut-être pas nécessaire de reconditionner le contenu pour le diffuser sur Xbox360 s’il a déjà été mis en package pour une autre plateforme Primetime, telle qu’iOS, Android ou Desktop.

Un des avertissements avec Xbox360 est qu&#39;il doit toujours atteindre un serveur clé chaque fois qu&#39;une balise EXT-X-KEY est rencontrée dans le M3U8. Contrairement à iOS, où un paramètre de stratégie DRM (policy.requireKeyServer) entraîne le lecteur vidéo iOS Primetime à récupérer la clé de décryptage AES à partir de localhost, Xbox tente toujours de récupérer la clé de décryptage d&#39;un serveur de clés distant . Il n&#39;existe pas de politique DRM pour demander à l&#39;application Xbox de récupérer la clé de décryptage AES à partir de localhost. En raison de cette exigence, les entrées EXT-X-KEY doivent se trouver dans le M3U8 pointant vers le point d’entrée DRM de Primetime Cloud. Cette URL est définie via &lt;key_url> dans le fichier de configuration OfflinePackager.jar config_hls.xml.

Si vous souhaitez regrouper le contenu une fois et le diffuser sur toutes les cibles Primetime, ainsi que configurer les appareils iOS pour ne pas récupérer une clé d’un serveur de clés distant, vous pouvez regrouper le contenu à l’aide d’une stratégie DRM qui possède la propriété policy.requireKeyServer=false (comme dans policy_ios_localkeyserver.pol). Les appareils iOS récupéreront la clé AES localement, tandis que les appareils Xbox ignoreront cette propriété et rejoindront le serveur de clé DRM Primetime Cloud pour obtenir une clé de décryptage.

>!Remarque
>
>Toutes les demandes Xbox360 doivent utiliser l&#39;authentification personnalisée/>Droit, car sur la plateforme Xbox360, Xbox Live utilise un jeton Xbox Secure Token Server (XSTS) à des fins d&#39;authentification.
>Le serveur de licences DRM de Primetime Cloud utilise le jeton XSTS pour >valider l’intégrité du périphérique Xbox et de l’utilisateur qui émet >la demande de licence. Toutefois, la validation du jeton XSTS nécessite une clé du fournisseur Xbox Live privée du client, que Primetime Cloud DRM >ne stocke pas. C’est pourquoi, lorsque Primetime Cloud DRM reçoit >une demande de licence d’un client Xbox 360, Primetime Cloud DRM >transmet le jeton XSTS au serveur principal du client Primetime >Authentification/Droit. Serveur du client Primetime
>analysera et validera ensuite le jeton XSTS pour s’assurer qu’il a été >signé à l’aide de la clé d’éditeur de l’application du client.
>Pour transmettre un jeton XSTS à partir du client Xbox360, définissez le jeton >de manière synchrone en réponse à l’événement MediaPlayer.RequestKeyAttribute >décrit plus en détail ici : **Définissez le jeton XSTS dans votre lecteur.** Un exemple de serveur d’authentification/de droits principal >est inclus dans la version logicielle du répertoire d’authentification personnalisée >et de droits.La validation des jetons XSTS est abordée >plus en détail ici : **Validation du jeton Xbox Live XSTS.**


## Définition du jeton XSTS dans votre lecteur {#set-the-xsts-token-in-your-player}

Dans Xbox360, vous définissez le jeton de manière asynchrone en réponse au `MediaPlayer.RequestKeyAttribute` .

Définissez le jeton XSTS.

L’exemple d’application fourni avec votre logiciel indique comment définir le jeton XSTS dans votre lecteur. Voici le fragment de code approprié de l’exemple de lecteur :

```
   MediaPlayer mMediaPlayer;  
 
mMediaPlayer.RequestKeyAttribute += Player_RequestKeyAttribute;  
 
private void Player_RequestKeyAttribute(object sender, RequestKeyAttributeEventArgs args) {  
    string token = "";  
    // XBOX XSTS Token...  
    KeyAttribute keyAttribute = new KeyAttribute(System.Text.Encoding.UTF8.GetBytes(token), null);  
    mMediaPlayer.SetKeyAttribute(args.RequestIdentifier, keyAttribute);  
} 
```

## Validation du jeton Xbox Live XSTS {#xbox-live-xsts-token-validation}

Pour les requêtes XSTS, la variable `customerSpecificAuthToken` contient le jeton XSTS codé Base64. L’exemple `XSTSValidator` Le code examine le jeton décodé Base64 pour déterminer si la variable `EncryptedAssertion` ; toutefois, vous pouvez utiliser d’autres méthodes pour distinguer ces requêtes des requêtes autres que Xbox. Par exemple, vous pouvez utiliser une autre URL.

La stratégie renvoyée dans le message de réponse remplace la stratégie d’origine dans les métadonnées DRM fournies avec la requête de clé Xbox. Seul un sous-ensemble de fonctionnalités de stratégie est pris en charge par le client Xbox. Ces champs sont les seuls à remplacer la stratégie d’origine.

D’autres étapes de configuration sont nécessaires pour prendre en charge le décryptage et la validation des jetons. Vous devez charger la variable [!DNL xsts_partner_cert.pfx] et [!DNL x_secure_token_service.part.xboxlive.com.cer] informations d’identification dans un fichier de stockage de clés au format JKS, que vous fournissez ensuite à votre serveur de droits principal en tant que propriété système `xsts-keystore`. Par défaut, le partenaire [!DNL .pfx] a l’alias `xsts`et le certificat de validation du jeton a l’alias `xsts-verify-cert`. Vous pouvez également les remplacer à l’aide des propriétés système. Enfin, il existe une propriété système `xsts-keystore-password` qui ne comporte pas de valeur par défaut et qui contient le mot de passe du KeyStore. Les propriétés système lues par la variable `XSTSValidator` sont résumées ci-dessous :

| Propriété du système | Valeur par défaut | Commentaire |
|---|---|---|
| xsts-keystore | xsts.jks | Fichier de stockage de clés au format JKS utilisé par le programme de validation. |
| xsts-keystore-password | | Mot de passe du KeyStore |
| xsts-alias | xsts | Alias utilisé pour récupérer la clé de décryptage du KeyStore |
| xsts-verify-cert-alias | xsts-verify-cert | Alias utilisé pour récupérer le certificat de validation du KeyStore |

## Création de JKS pour un validateur XSTS{#create-jks-for-an-xsts-validator}

1. Découvrez le nom d’alias du certificat privé, situé dans le partenaire [!DNL .pfx] fichier .

   ```
   keytool -list -storetype pkcs12 -keystore xsts_partner_cert.pfx -v 
   ```

1. Convertir [!DNL .pfx] to [!DNL .jks].

   ```
   keytool -importkeystore -srckeystore xsts_partner_cert.pfx -srcstoretype PKCS12 \  
           -keystore xsts.jks -srcalias  
   <alias> -destalias xsts
   ```

   (où `<alias>` est le nom d’alias du certificat privé que vous avez découvert à l’étape 1.)
1. Importer [!DNL x_secure_token_service.part.xboxlive.com.cer].

   ```
   keytool -importcert -alias xsts-verify-cert -keystore xsts.jks \  
           -file x_secure_token_service.part.xboxlive.com.cer 
   ```

1. Put [!DNL xsts.jks] dans votre répertoire racine Tomcat, puis définissez `-Dxsts-keystore-password=****` pour Tomcat.

If [!DNL xsts_partner_cert.pfx] et [!DNL xsts.jks] utilisent des mots de passe différents, mettez à jour la variable `xsts` password in `jks` pour les rendre identiques.

```
keytool -keypasswd -keystore xsts.jks -alias xsts 
```
