---
description: La licence est le principal mécanisme par lequel les utilisateurs sont autorisés ou privés de la possibilité de lire un élément de contenu vidéo protégé. Un utilisateur légitime (autorisé) peut obtenir une licence (clé) pour déchiffrer et lire un élément spécifique du contenu chiffré de son fournisseur de contenu.
seo-description: La licence est le principal mécanisme par lequel les utilisateurs sont autorisés ou privés de la possibilité de lire un élément de contenu vidéo protégé. Un utilisateur légitime (autorisé) peut obtenir une licence (clé) pour déchiffrer et lire un élément spécifique du contenu chiffré de son fournisseur de contenu.
seo-title: Licence
title: Licence
uuid: 9f433d62-5609-4d88-95fd-c1e7c0f6aa75
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Licence{#licensing}

La licence est le principal mécanisme par lequel les utilisateurs sont autorisés ou privés de la possibilité de lire un élément de contenu vidéo protégé. Un utilisateur légitime (autorisé) peut obtenir une licence (clé) pour déchiffrer et lire un élément spécifique du contenu chiffré de son fournisseur de contenu.

Avant que votre application ou page Web sur le périphérique d’un utilisateur final puisse lire du contenu protégé par DRM, il doit acquérir un jeton d’un serveur de droits ou de stockage que vous, le client, exploitez. Adobe fournit un exemple de serveur de référence à cette fin : Serveur [de référence : Exemple de serveur de droits ExpressPlay (SEES)](../../multi-drm-workflows/feature-topics/sees-reference-server.md).

Votre serveur de droits ou de stockage demandera un jeton de licence au serveur ExpressPlay concerné, uniquement après avoir vérifié auprès de vos propres systèmes dorsaux pour déterminer si l&#39;utilisateur spécifique est autorisé à regarder le contenu demandé. La réponse renvoyée par la demande de jeton de licence est soit une URL prête à l’emploi pour le serveur de licences, soit la réponse contient l’URL dans une structure JSON, selon la solution DRM avec laquelle vous travaillez.

>[!NOTE]
>
>La demande de jeton de licence ne peut pas être effectuée à partir du client lui-même :
>1. Les droits doivent être contrôlés dans un  de confiance ; et
>1. L&#39;authentificateur du client doit être tenu secret.


1. Faites une demande de jeton de licence.

   Dans le cas d’un scénario de  rapide, dans lequel vous souhaitez simplement vous assurer que les différents composants impliqués fonctionnent ensemble, vous pouvez utiliser [!DNL curl] une fonction telle que demander votre jeton de licence (plutôt que d’obtenir une application en cours d’exécution et de tester des appels à partir de là). Par exemple :

   * Widevine :

   ```
   curl "https://wv-gen.test.expressplay.com/hms/wv/token?customerAuthenticator= 
   <Customer Authenticator> 
   &kid 
   <indexterm>
   CEKSID 
     <indexterm>
     as query parameter kid 
    <indexterm>
    Widevine 
    </indexterm> 
    </indexterm> 
    </indexterm>=<CEKSID> 
      &contentKey 
    <indexterm>
    CEK 
    <indexterm>
    as query parameter contentKey 
    <indexterm>
    Widevine 
    </indexterm> 
    </indexterm> 
    </indexterm>=<CEK> 
      &<Any additional licensing attributes desired>" >>WidevineToken 
   ```

   Exemple de jeton de test Widevine :

   ```
   https://wv.test.expressplay.com/widevine/RightsManager.asmx?ExpressPlayToken= 
      AQAAAJJ2Y0MAAABQbyvnJ6KgEg_w-2yZmU-MsjTEZ3f7UkhUcFhDFAvdonzBk 
      RGQU-xe1G-DMbel5-BVH_PozovdWhKZx0_SXRokfh9-FERmBl6OEfGfPqMI1e 
      O1PqRkx59Q2q1s2cFNrqfml8Y3RQ 
   ```

   Notez que la réponse de Widevine est une chaîne URL &quot;prête à l’emploi&quot;.

   * PlayReady :

   ```
   curl "https://pr-gen.test.expressplay.com/hms/pr/token?customerAuthenticator= 
   <Customer Authenticator> 
      &kid 
   <indexterm>
   CEKSID 
   <indexterm>
   as query parameter kid 
   <indexterm>
    PlayReady 
   </indexterm> 
   </indexterm> 
   </indexterm>=<Key ID> 
      &contentKey 
   <indexterm>
    CEK 
    <indexterm>
    as query parameter contentKey 
    <indexterm>
    PlayReady 
   </indexterm> 
   </indexterm> 
   </indexterm>=<CEK> 
      &<Any additional licensing attributes desired>" >>playreadyToken
   ```

   Exemple de jeton de test PlayReady :

   ```
   {"licenseAcquisitionUrl":"https://pr.test.expressplay.com/playready/RightsManager.asmx", 
   "token":"AQAAAxBbWv4AAABgV8_GaWjU80mObLQdfwEdy1lenXmcqvx5VLyqixigtwXLthzjPxq9QDT-TYbudNrMSOpUAy 
   G_2Qt8RdTGJ2_Q_xtRfnj7H6C-yt6By40IhNaSQ0nNYUsY1_MtCrHXIltlVhN2Ekr_RNyTNvCjYs0V5TqzOPY"} 
   ```

   Notez que la réponse PlayReady est un objet JSON, avec des éléments d’URL et de jeton distincts.

   * FairPlay :

   ```
   curl "https://fp-gen.test.expressplay.com/hms/fp/token?customerAuthenticator= 
    <Customer Authenticator> 
    &kid 
    <indexterm>
      CEKSID 
    <indexterm>
      as query parameter kid 
      <indexterm>
        FairPlay 
      </indexterm> 
    </indexterm> 
    </indexterm>=<Key ID> 
          &contentKey 
    <indexterm>
      CEK 
    <indexterm>
      as query parameter contentKey 
      <indexterm>
        FairPlay 
      </indexterm> 
    </indexterm> 
    </indexterm>=<CEK> 
    &iv=<IV ID> 
    &<Any additional licensing attributes desired>"
   ```

   Exemple de jeton de test FairPlay :

   ```
   https://{expressplay_test_domain_license_url}/?ExpressPlayToken= 
   AQAAAJJ2Y0MAAABQbyvnJ6KgEg_w-2yZmU-MsjTEZ3f7UkhUcFhDFAvdonzBk 
   RGQU-xe1G-DMbel5-BVH_PozovdWhKZx0_SXRokfh9-FERmBl6OEfGfPqMI1e 
   O1PqRkx59Q2q1s2cFNrqfml8Y3RQ
   ```

   Notez que la réponse de FairPlay est une chaîne URL &quot;prête à l’emploi&quot;.
