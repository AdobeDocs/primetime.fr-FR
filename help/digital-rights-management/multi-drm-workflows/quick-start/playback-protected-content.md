---
description: Pour tester votre solution DRM, vous avez besoin d’une application vidéo qui peut traiter la solution DRM particulière que vous utilisez. Ce lecteur peut être un exemple de lecteur mis à disposition par Adobe ou votre propre application vidéo basée sur TVSDK.
title: Lecture du contenu protégé
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 0%

---

# Lecture du contenu protégé {#playback-your-protected-content}

Pour tester votre solution DRM, vous avez besoin d’une application vidéo qui peut traiter la solution DRM particulière que vous utilisez. Ce lecteur peut être un exemple de lecteur mis à disposition par Adobe ou votre propre application vidéo basée sur TVSDK.

1. Utilisez l’URL du serveur de licences provenant de la réponse du jeton que vous avez récupérée du serveur ExpressPlay pour tester si vous pouvez lire votre contenu protégé.

   * **Widevine** - Utilisez la réponse Widevine directement comme reçue de votre demande de jeton de licence ExpressPlay.
   * **PlayReady** - Obtenez l’URL et le jeton du serveur de licences de l’objet JSON renvoyé par votre demande de jeton de licence.
   * **FairPlay** - Utilisez la réponse FairPlay directement comme reçue de votre demande de jeton de licence ExpressPlay.

1. Testez la lecture de votre contenu protégé en utilisant votre propre lecteur ou un exemple de lecteur d’Adobe existant.

   Indiquez l’URL de votre contenu protégé (l’emplacement de votre manifeste M3U8 ou MPD, en fonction de la solution DRM que vous testez).

   Selon l’interface fournie par le lecteur avec lequel vous effectuez le test, vous devrez peut-être fournir l’URL de licence et le jeton séparés sous forme de chaînes dans les champs de saisie, ou sous forme d’objet JSON collé dans une zone de texte, ou peut-être sous forme de paramètre de requête dans l’URL.

   Voici quelques possibilités pour les lecteurs de test :

   * Lecteur de référence HTML5 :

     ```
     https://ptdemos.com/html5/internal/1_2/2.4_GM/samples/reference/reference_player.html
     ```

   * Shaka Player :

     ```
     https://shaka-player-demo.appspot.com
     ```

   * Exemple de lecteur TVSDK (en développement) -

   ```
   https://drmtest2.adobe.com/TVSDK_HTML5/samples/reference/reference_player.html
   ```

   **Vérification de la lecture lors du test de votre configuration FairPlay :** FairPlay nécessite quelques étapes supplémentaires pour lire le contenu lorsque vous utilisez les serveurs de licence ExpressPlay. Si vous utilisez [!DNL curl] pour tester vos connexions (comme décrit dans la section [Licences](../../multi-drm-workflows/quick-start/handle-the-licensing.md)), vous devez *Modifier votre manifeste M3U8* (votre contenu empaqueté) comme suit :

1. Ajoutez la réponse que vous avez récupérée de votre requête de jeton de licence à la variable `#EXT-X-KEY:` dans le manifeste ; et
1. Modifiez le protocole de cette URL à partir de la réponse (maintenant dans le manifeste), à partir de `https://` to `skd://`.

   Voici un exemple complet de test de lecture avec FairPlay, y compris l’étape de licence :

1. Utilisez la demande de jeton de licence FairPlay pour obtenir l’URL de votre jeton de licence. (Utilisez votre propre authentificateur client de production et assurez-vous d’utiliser le même CEK et `iv` qui a été utilisé pour empaqueter votre contenu FairPlay.) Exécutez la commande suivante pour obtenir l’URL du jeton de licence de l’exemple de contenu :

   ```
   curl -v "https://fp-gen.service.expressplay.com/hms/fp/token? 
   customerAuthenticator=[YOUR-PRODUCTION-AUTHENTICATOR]&errorFormat=json 
   &contentKey CEK as query parameter contentKey 
   =[YOUR CONTENT KEY]&iv=[YOUR IV]"
   ```

   Vous devriez obtenir une réponse avec l’URL du jeton de licence qui ressemble à ceci :

   ```
   https://fp.service.expressplay.com:80/hms/fp/rights/? 
   ExpressPlayToken=AQAAABNlKcEAAABQaTjshua3cWjG_Il3fvhf3g-CR1rn 
   JKdtaVaAnhkfTCW0bWAU76YgwForbrXhD5tXUHhfP7FD1svvLPxN5qomYsnwY 
   SSwcDq1ZnRtXunFLueTw6LAL52aZllMLasCSzYRMaAVHw 
   ```

1. Insérez la réponse URL de jeton de licence renvoyée dans votre manifeste M3U8, et *remplacez le modèle d’URL de jeton de licence par* `sdk://` de `https://`. Voici un exemple de la balise #EXT-X-KEY dans votre manifeste M3U8 :

   ```
   #EXT-X-KEY:METHOD=SAMPLE-AES, 
   URI="skd://fp.service.expressplay.com:80/hms/fp/rights/? 
   ExpressPlayToken=AQAAABNlKcEAAABQaTjshua3cWjG_Il3fvhf3g- 
   CR1rnJKdtaVaAnhkfTCW0bWAU76YgwForbrXhD5tXUHhfP7FD1svvLPx 
   N5qomYsnwYSSwcDq1ZnRtXunFLueTw6LAL52aZllMLasCSzYRMaAVHw", 
   KEYFORMAT="com.apple.streamingkeydelivery",KEYFORMATVERSIONS="1"
   ```

   >[!NOTE]
   >
   >Les informations précédentes s’appliquent uniquement au test de votre configuration FairPlay. Il peut ne pas s’appliquer à votre configuration de production, selon la manière dont vous configurez votre gestionnaire FairPlay. Voir [Activation d’Apple FairPlay dans les applications iOS](../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md) pour plus d’informations.

Si votre vidéo est lue, votre contenu a été empaqueté et sous licence. Si votre vidéo ne s’affiche pas, consultez la page de dépannage pour trouver des solutions à vos problèmes.

<!--<a id="example_603D92A1F3924467B5D66EC862B8F59C"></a>-->

Par exemple, voici la partie de l’interface utilisateur du premier lecteur de test répertoriée ci-dessus, où vous fournissez les informations de licence obtenues à partir du serveur ExpressPlay :

<!--<a id="fig_zjy_q2c_rw"></a>-->

![](assets/sample-player-drm-settings-web.png)
