---
description: 'null'
seo-description: 'null'
seo-title: Définition du jeton XSTS dans votre lecteur
title: Définition du jeton XSTS dans votre lecteur
uuid: 8995e029-deee-4e23-9cda-a50de8c4f2c0
translation-type: tm+mt
source-git-commit: c37061c116b8a6bc8ce085dc89dc8aadd0a2e490
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 0%

---


# Diffusion en flux continu sur Xbox360 (facultatif) {#streaming-to-xboc360}

Primetime DRM est disponible sur la plate-forme Xbox360. Cependant, seul le cas d’utilisation de la diffusion en flux continu protégée est pris en charge, et non la suite complète de droits de stratégie DRM. Les droits de stratégie DRM non liés à la diffusion en continu, tels que les groupes de domaines de périphériques, ne sont pas pris en charge. La Xbox360 ignore les droits non pris en charge lors de la tentative de lecture de contenu.

Les droits de stratégie DRM Primetime pris en charge pour Xbox sont les suivants :
* Protection de la sortie numérique
* Date de fin de mise en cache hors licence
* Date du Début de licence
* Date de fin de la licence
* Durée de la fenêtre de lecture (secondes)

Il n’est peut-être pas nécessaire de reconditionner le contenu pour le diffuser sur Xbox360, s’il l’était déjà pour une autre plateforme Primetime, telle que iOS, Android ou Desktop.

Une mise en garde avec Xbox360 est qu&#39;il doit toujours contacter un serveur clé chaque fois qu&#39;une balise EXT-X-KEY est rencontrée dans le M3U8. Contrairement à iOS, où un paramètre de stratégie DRM (policy.requireKeyServer) entraîne le lecteur vidéo Primetime iOS à récupérer la clé de déchiffrement AES depuis localhost, Xbox tente toujours de récupérer la clé de déchiffrement depuis un serveur de clés distant. Aucune stratégie DRM ne permet d&#39;indiquer à l&#39;application Xbox de récupérer le déchiffrement AES.
de localhost. En raison de cette exigence, les entrées EXT-X-KEY doivent se trouver dans le M3U8 pointant vers le point de terminaison DRM de Primetime Cloud. Cette URL est définie via &lt;key_url> dans le fichier de configuration OfflinePackager.jar config_hls.xml.

Si vous souhaitez regrouper le contenu une fois et le diffuser en continu sur toutes les cibles Primetime, ainsi que configurer les périphériques iOS pour ne pas récupérer une clé d’un serveur de clés distant, vous pouvez regrouper le contenu à l’aide d’une stratégie DRM qui possède la stratégie de propriété.requireKeyServer=false (par exemple, dans policy_ios_localkeyserver.pol). Les périphériques iOS récupéreront la clé AES localement, tandis que les périphériques Xbox ignoreront cette propriété et accéderont au serveur clé DRM de Primetime Cloud.
pour une clé de déchiffrement.

>!Note
>
>Toutes les demandes Xbox360 doivent utiliser l&#39;authentification personnalisée/>Entitlement. En effet, sur la plateforme Xbox360, Xbox Live >utilise un jeton Xbox Secure Token Server (XSTS) à des fins d&#39;authentification.
>Le serveur de licence DRM de Primetime Cloud utilise le jeton XSTS pour >valider l&#39;intégrité du périphérique Xbox et de l&#39;utilisateur qui fait >la demande de licence. Cependant, la validation du jeton XSTS nécessite une clé de fournisseur Xbox Live privée du client, que Primetime Cloud DRM >ne stocke pas. Par conséquent, lorsque Primetime Cloud DRM reçoit >une demande de licence d’un client Xbox 360, Primetime Cloud DRM >transmet le jeton XSTS au serveur principal du client Primetime >Authentification/Droits. Serveur du client Primetime
>analysera et validera ensuite le jeton XSTS pour vérifier qu’il a été >signé à l’aide de la clé d’éditeur de l’application du client.
>Pour transmettre un jeton XSTS à partir du client Xbox360, définissez le jeton >de manière synchrone en réponse au événement MediaPlayer.RequestKeyAttribute >décrit plus en détail ici : **Définissez le jeton XSTS dans votre lecteur.** Un exemple de serveur d’authentification/de droits dorsaux >est inclus dans la version du logiciel dans le répertoire d’authentification personnalisée >et de droits.La validation des jetons XSTS est abordée >plus en détail ici :  **Validation du jeton Xbox Live XSTS.**


## Définir le jeton XSTS dans votre lecteur {#set-the-xsts-token-in-your-player}

Dans Xbox360, vous définissez le jeton de manière asynchrone en réponse au événement `MediaPlayer.RequestKeyAttribute`.

Définissez le jeton XSTS.

L’exemple d’application fourni avec votre logiciel montre comment définir le jeton XSTS dans votre lecteur. Voici le fragment de code correspondant extrait du lecteur d’exemple :

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

Pour les requêtes XSTS, le champ `customerSpecificAuthToken` contient le jeton XSTS codé en Base64. L&#39;exemple de code `XSTSValidator` examine le jeton décodé Base64 pour déterminer l&#39;existence de l&#39;élément `EncryptedAssertion`; toutefois, vous pouvez utiliser d’autres méthodes pour faire la distinction entre ces requêtes et les requêtes non Xbox. Par exemple, vous pouvez utiliser une autre URL.

La stratégie renvoyée dans le message de réponse remplacera la stratégie d&#39;origine dans les métadonnées DRM fournies avec la demande de clé Xbox. Seul un sous-ensemble de fonctionnalités de stratégie est pris en charge par le client Xbox, et ces champs sont les seuls à remplacer la stratégie d&#39;origine.

D’autres étapes de configuration sont nécessaires pour prendre en charge le déchiffrement et la validation des jetons. Vous devez charger les informations d’identification [!DNL xsts_partner_cert.pfx] et [!DNL x_secure_token_service.part.xboxlive.com.cer] dans un fichier de stockage de clés au format JKS, que vous fournissez ensuite à votre serveur de droits principal en tant que propriété système `xsts-keystore`. Par défaut, le partenaire [!DNL .pfx] a l’alias `xsts` et le certificat de validation du jeton a l’alias `xsts-verify-cert`. Vous pouvez également les remplacer à l’aide des propriétés système. Enfin, il existe une propriété système `xsts-keystore-password` qui n&#39;a pas de valeur par défaut et qui contient le mot de passe du fichier de stockage des clés. Les propriétés système lues par le code `XSTSValidator` sont résumées ci-dessous :

| Propriété système | Valeur par défaut | Commentaire |
|---|---|---|
| xsts-keystore | xsts.jks | Fichier de stockage de clés au format JKS utilisé par le programme de validation. |
| xsts-keystore-password |  | Mot de passe du fichier de stockage des clés |
| xsts-alias | xsts | Alias utilisé pour récupérer la clé de déchiffrement dans le fichier de stockage des clés |
| xsts-verify-cert-alias | xsts-verify-cert | Alias utilisé pour récupérer le certificat de validation dans le fichier de stockage des clés |

## Création de JKS pour un validateur XSTS{#create-jks-for-an-xsts-validator}

1. Recherchez le nom d’alias du certificat privé, situé dans le fichier [!DNL .pfx] partenaire.

   ```
   keytool -list -storetype pkcs12 -keystore xsts_partner_cert.pfx -v 
   ```

1. Convertir [!DNL .pfx] en [!DNL .jks].

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

1. Placez [!DNL xsts.jks] dans votre répertoire d’accueil Tomcat et définissez `-Dxsts-keystore-password=****` pour Tomcat.

Si [!DNL xsts_partner_cert.pfx] et [!DNL xsts.jks] utilisent des mots de passe différents, mettez à jour le mot de passe `xsts` dans `jks` pour qu&#39;ils soient identiques.

```
keytool -keypasswd -keystore xsts.jks -alias xsts 
```
