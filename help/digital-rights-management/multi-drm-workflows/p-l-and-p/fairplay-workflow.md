---
description: Les workflows DRM impliquent la création d’un pack de contenu, l’octroi de licences pour le contenu et la lecture du contenu protégé depuis votre propre application vidéo. Le flux de travail est généralement similaire pour chaque solution DRM, mais certaines différences se trouvent dans les détails.
seo-description: Les workflows DRM impliquent la création d’un pack de contenu, l’octroi de licences pour le contenu et la lecture du contenu protégé depuis votre propre application vidéo. Le flux de travail est généralement similaire pour chaque solution DRM, mais certaines différences se trouvent dans les détails.
seo-title: Processus multi-DRM pour FairPlay
title: Processus multi-DRM pour FairPlay
uuid: cd940a70-400c-435e-8322-55bd624164e1
translation-type: tm+mt
source-git-commit: 29149594c4b41956a091ef27093304e74ff15f2f

---


# Processus multi-DRM pour FairPlay {#multi-drm-workflow-for-fairplay}

Les workflows DRM impliquent la création d’un pack de contenu, l’octroi de licences pour le contenu et la lecture du contenu protégé depuis votre propre application vidéo. Le flux de travail est généralement similaire pour chaque solution DRM, mais certaines différences se trouvent dans les détails.

Ce flux de travaux multi-DRM vous guide tout au long de la configuration, de l’emballage, de la licence et de la lecture de contenu HLS protégé par Apple FairPlay. Ce processus comprend également des instructions facultatives pour la mise en oeuvre de la lecture hors ligne et de la rotation des licences.

## Activer le service ExpressPlay pour FairPlay {#enable-expressplay-service-for-fairplay}

La solution FairPlay DRM d&#39;Apple nécessite une configuration lorsque vous l&#39;utilisez avec les services ExpressPlay DRM. Cela implique d’obtenir des informations d’identification d’Apple et de les télécharger vers ExpressPlay.

Suivez ces étapes pour activer le service ExpressPlay pour la protection du contenu FairPlay.

1. Récupérez les informations d’identification auprès d’Apple.

   Ces informations d’identification sont attribuées de manière unique à chaque prestataire. Vous devez les demander en remplissant le formulaire suivant : [https://developer.apple.com/contact/fps/](https://developer.apple.com/contact/fps/).

   >[!NOTE]
   >
   >Sélectionnez **[!UICONTROL Content Provider]** le rôle principal.

   Une fois votre demande approuvée, Apple vous enverra un pack *de déploiement en flux continu* FairPlay.
1. Générer une demande de signature de certificat.

   Vous pouvez utiliser [!DNL openssl] pour générer votre paire de clés publique/privée et votre demande de signature de certificat (CSR).

   1. Générez votre paire de clés.

      ```
      openssl genrsa -aes256 -out privatekey.pem 1024 
      ```

   1. Générez votre CSR.

      ```
      openssl req -new -sha1 -key privatekey.pem -out certreq.csr  
        -subj "/CN=SubjectName /OU=OrganizationalUnit /O=Organization /C=US"
      ```

      >[!NOTE]
      >
      >Les instructions de cette étape se trouvent dans votre package *de déploiement en flux continu* FairPlay, mais sont incluses ici pour votre commodité. Si vous rencontrez des problèmes avec cette partie du processus, consultez les instructions du fichier *FairPlayCertificateCreation.pdf* (dans votre pack de déploiement).

1. Téléchargez votre CSR sur le portail des développeurs Apple.
   1. L&#39;agent d&#39;équipe de votre équipe de développement doit se connecter à [!DNL developer.apple.com/account].
   1. Cliquez sur **[!UICONTROL Certificates, Identifiers & Profiles]**, puis sélectionnez la liste **[!UICONTROL iOS, tvOS, watchOS]** déroulante en haut à gauche de la page, puis cliquez sur **[!UICONTROL Certificates->Production]** à gauche de la page.
   1. Cliquez sur le **[!UICONTROL +]** bouton en haut à droite de la page pour demander un nouveau certificat. Sélectionnez l’ **[!UICONTROL FairPlay Streaming Certificate]** option sous **[!UICONTROL Production]**.

      La boîte de dialogue Certificat *iOS* Ajouter s’ouvre.
   1. Dans le certificat *iOS* Ajouter, téléchargez le fichier CSR que vous avez généré à l’étape 2.b, puis cliquez sur **[!UICONTROL Generate]** le bouton.

      Votre clé de Clé secrète (ASK) s’affiche dans la même boîte de dialogue.
   1. Écrivez votre demande et stockez-la dans un endroit sûr.
   1. Cliquez sur dans votre ASK pour terminer la génération de certificats et cliquez sur **[!UICONTROL Continue]**.
   1. Après avoir vérifié que vous avez enregistré votre demande de service financier, cliquez sur **[!UICONTROL Generate]** pour continuer.

      >[!NOTE] {importance=&quot;high&quot;}
      >
      >Il est important que vous enregistriez une copie de votre demande et que vous la stockiez en toute sécurité. *Si votre ASK est compromis, vous ne pourrez plus protéger votre contenu avec FairPlay Streaming.* Un seul (1) ASK est attribué à votre équipe. La valeur ne sera plus fournie et vous ne pourrez plus la récupérer ultérieurement.

   1. Téléchargez votre certificat FPS.

      Assurez-vous d&#39;enregistrer une copie de sauvegarde de votre clé privée (à partir de l&#39;étape 2.a) et de votre clé publique (le certificat FPS que vous avez téléchargé au cours de cette étape) dans un endroit sûr.
1. Configurez votre compte ExpressPlay avec vos informations d’identification FairPlay.
   1. Supposons que le nom du certificat que vous avez téléchargé à l’étape 3.h. est [!DNL fairplay.cer].
   1. Ouvrez le [!DNL fairplay.cer] fichier à l’aide de l’utilitaire Apple Keychain Access.
   1. Filtrez vos nombreux certificats en entrant &quot; `fairplay`&quot; dans le champ de recherche situé en haut à droite.
   1. Identifiez le certificat FairPlay de votre société.

      Votre nom de société doit être associé au certificat émis par Apple.
   1. Développez le certificat en sélectionnant la flèche de développement, puis cliquez avec le bouton droit de la souris sur votre clé privée.
   1. Sélectionnez **[!UICONTROL Export "Your Company Name"]** et enregistrez le [!DNL .p12] fichier.

      Vous serez invité à attribuer un mot de passe pour protéger ce fichier. Notez ce mot de passe car vous devrez l&#39;envoyer avec votre paquet d&#39;informations d&#39;identification.
   1. Connectez-vous à votre compte sur [www.expressplay.com](https://www.expressplay.com).
   1. Cliquez sur **[!UICONTROL DRM SERVICES]** en haut à gauche, puis sélectionnez l’ **[!UICONTROL FairPlay]** onglet.
   1. Téléchargez vos informations d’identification FairPlay vers votre compte ExpressPlay.

      1. Créez un fichier texte contenant la valeur de votre ASK (32 caractères doivent être indiqués, par exemple : `1234567890abcdef1234567890abcdef`) et sélectionnez ce fichier pour le télécharger.
      1. Sélectionnez le fichier PKCS12 à l’étape 4.f. pour le téléchargement.
      1. Saisissez le mot de passe du fichier PKCS12 à l’étape 4.f.
      1. Cliquez sur le bouton Télécharger.

Vous pouvez désormais créer des applications iOS ou des pages HTML5 avec la protection de contenu FairPlay et votre [!DNL fairplay.cer] certificat à l’aide du service ExpressPlay pour FairPlay.

<!--<a id="fig_sjr_2pn_sv"></a>-->

![](assets/multi_drm_expressplay_drm_services_web.png)

### Assemblage de votre contenu pour FairPlay {#package-your-content-for-fairplay}

Pour créer un pack contenant votre contenu, vous pouvez utiliser Adobe Offline Packager ou d’autres outils tels que le Packager Bento4 d’ExpressPlay.

Les développeurs préparent la vidéo pour la lecture (par exemple, fragmentation du fichier d’origine et placement de celui-ci dans un manifeste) et protègent la vidéo avec la solution DRM que vous avez choisie (dans ce cas, FairPlay) :

* [Adobe Offline Packager for FairPlay DRM](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf#page=21)
* [ExpressPlay Packagers - Bento4 pour HLS](https://www.bento4.com/developers/hls/)

<!--<a id="fig_jbn_fw5_xw"></a>-->

![](assets/pkg_lic_play_hls_web.png)

1. Empaquetez votre contenu.

   Voici un exemple d’assemblage utilisant Adobe Offline Packager. L’outil Packager utilise un fichier de configuration ( [!DNL fairplay.xml]par exemple) qui ressemble à ce qui suit :

   ```
   <config>
   <in_path>mp4_file_path</in_path>
   <out_type>hls</out_type>
   <out_path>out_file_path</out_path>
   <drm/>
   <drm_sys>FAIRPLAY</drm_sys>
   <frag_dur>4</frag_dur>
   <target_dur>6</target_dur>
   <key_file_path>creds/fairplay.bin</key_file_path>
   <iv_file_path>creds/iv.bin</iv_file_path>
   <key_url>user_provided_value</key_url>
   <content_id>_default_</content_id>
   </config>
   ```

   * `in_path` - Cette entrée indique l&#39;emplacement de la vidéo source sur votre machine d&#39;emballage locale.
   * `out_type` - Cette entrée décrit le type de sortie emballée, dans ce cas HLS pour FairPlay.
   * `out_path` - L&#39;emplacement sur la machine locale où vous voulez que votre sortie aille.
   * `drm_sys` - La solution DRM que vous incluez dans votre pack. C&#39;est `FAIRPLAY` dans ce cas.
   * `frag_dur` - Durée du fragment en secondes.
   * `target_dur` - Durée de cible de la sortie HLS.
   * `key_file_path` - Il s’agit de l’emplacement du fichier de licence sur votre machine de conditionnement qui sert de clé de chiffrement de contenu (CEK). Il s’agit d’une chaîne hexadécimale codée en base 64 et codée sur 16 octets.
   * `iv_file_path` - Il s&#39;agit de l&#39;emplacement du fichier IV sur votre machine d&#39;emballage.
   * `key_url` - Paramètre URI de la `EXT-X-KEY` balise du [!DNL .m3u8] fichier.
   * `content_id` - Valeur par défaut.
   Comme indiqué dans la documentation [de](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf#page=7)Packager, &quot;Il est recommandé de créer un fichier de configuration contenant les options courantes que vous souhaitez utiliser pour générer les sorties. Ensuite, créez la sortie en fournissant des options spécifiques sous forme d&#39;argument de ligne de commande.&quot;

   ```
   java -jar OfflinePackager.jar -in_path sample.mp4 -out_type hls 
   -out_path out_file_path -drm -drm_sys FAIRPLAY -key_file_path "creds/fairplay.bin" 
   -key_url "user_provided_value"
   ```

   Le fichier M3U8 généré possède un `EXT-X-KEY` attribut qui s’affiche comme suit :

   ```
   #EXT-X-KEY:METHOD=SAMPLE-AES,URI="user_provided_value",​
   KEYFORMAT="com.apple.streamingkeydelivery",KEYFORMATVERSIONS="1" 
   ```

### Définition de stratégies pour FairPlay {#setting-policies-for-fairplay}

Vous pouvez définir des stratégies pour le contenu protégé par FairPlay à l’aide d’un serveur de droits. Vous pouvez configurer le vôtre ou utiliser un exemple de serveur de droits fourni par Adobe.

Adobe fournit un exemple de serveur de droits ExpressPlay (SEES) qui indique comment effectuer des droits basés sur *le* temps et liés *aux* périphériques. Cet exemple de serveur de droits est construit sur les services ExpressPlay.

[Serveur de référence : Exemple de serveur de droits ExpressPlay (SEES)](../../multi-drm-workflows/feature-topics/sees-reference-server.md)

* [Service de référence : Droits basés sur le temps](../../multi-drm-workflows/feature-topics/sees-reference-server-time-entitlement.md)
* [Service de référence : Droits de liaison de périphérique](../../multi-drm-workflows/feature-topics/sees-reference-server-binding-entitlement.md)

## Licence et lecture pour FairPlay {#licensing-and-playback-for-fairplay}

La licence et la lecture d’un contenu protégé par FairPlay nécessitent l’échange de schémas d’URL entre le schéma utilisé dans le fichier de manifeste vidéo (skd:) et celui utilisé dans les demandes de jeton ExpressPlay (https:).

Vous trouverez ici les instructions relatives à la mise en oeuvre de la licence et de la lecture d’un client TVSDK iOS : [Activez Apple FairPlay dans les applications](../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md)TVSDK. Vous pouvez également mettre en oeuvre la lecture hors ligne et la rotation des licences pour FairPlay (facultatif).

## HLS hors ligne avec FairPlay {#section_047A05D1E3B64883858BC601CFC8F759}

Vous souhaitez peut-être permettre aux utilisateurs de lire du contenu protégé par FairPlay lorsque l’autorisation n’est pas récupérable car le lecteur est isolé du Web (par exemple sur un avion).

Avant de commencer cette tâche, téléchargez et lisez le document Apple **&quot;Lecture hors ligne avec la diffusion en flux continu FairPlay et la diffusion en flux continu HTTP Live&quot;**. Lisez le guide pour savoir comment télécharger des segments de flux de transport (TS) et les enregistrer sur votre ordinateur local.

Mettez en oeuvre la lecture hors ligne pour FairPlay avec ce flux de travail :

1. Téléchargez le segment HLS TS.
1. Demande de licence de location permanente auprès du serveur FairPlay (voir **&quot;Politique de location permanente FairPlay&quot;**).
1. Enregistrez le `persistentContentKey`.
1. Lire le contenu FairPlay hors ligne.

>[!NOTE]
>
>FairPlay Streaming sur le client ne début pas le déchiffrement si la clé de contenu persistante a expiré. Cependant, l’expérience utilisateur se poursuivra si la clé de contenu expire au cours de la lecture.
>
>Voir [Utilisation du document de diffusion en flux continu](https://developer.apple.com/library/content/documentation/AudioVideo/Conceptual/MediaPlaybackGuide/Contents/Resources/en.lproj/HTTPLiveStreaming/HTTPLiveStreaming.html#//apple_ref/doc/uid/TP40016757-CH11-SW3) HTTP Live pour plus d’informations.

### Rotation des licences FairPlay {#section_D32AA08C61474B4F876AC2A5F18CB879}

La rotation des licences est un système destiné à empêcher le piratage de licences de contenu qui est lu pendant longtemps.

Dans un manifeste M3U8, chaque balise de clé s’applique aux segments TS suivants jusqu’à la balise de clé suivante ou jusqu’à la fin du fichier.

Pour ajouter la rotation des licences, procédez comme suit :

* Insérez une nouvelle balise de clé FairPlay pendant la rotation de la licence.

   N’importe quel nombre de balises clés peut être ajouté.

   Pour le contenu linéaire, veillez à conserver la balise clé la plus récente dans la fenêtre M3U8. iOS va demander le prochain M3U8 lorsqu&#39;il reste environ deux segments TS à lire (environ 20 secondes). Si le nouveau M3U8 contient de nouvelles balises de clés, toutes les requêtes de clés surviennent immédiatement. Les clés existantes précédentes ne seront plus demandées. iOS attend la fin de toutes les requêtes clés avant que la lecture ne début.

   Pour le contenu VOD avec rotation de licence, toutes les requêtes clés surviennent au début de la lecture.

   Voici un exemple de M3U8 avec rotation de clé :

   ```
   #EXTM3U
   #EXT-X-TARGETDURATION:10
   #EXT-X-VERSION:5
   #EXT-X-MEDIA-SEQUENCE:0
   #EXT-X-PLAYLIST-TYPE:VOD
   #EXT-X-KEY:METHOD=SAMPLE-AES,URI="skd://one?cek=1dc2cc71d913f4f74eca0c4632
   212b25&iv=e21f0f72b6363ff6143737cb1e9ca8d7",KEYFORMAT="com.apple.streaming
   keydelivery",KEYFORMATVERSIONS="1"
   #EXTINF:10,
   fileSequence0.ts
   #EXTINF:10,
   fileSequence1.ts
   #EXTINF:10,
   fileSequence2.ts
   #EXTINF:10,
   fileSequence3.ts
   #EXTINF:10,
   fileSequence4.ts
   #EXTINF:10,
   fileSequence5.ts
   #EXTINF:10,
   fileSequence6.ts
   #EXTINF:10,
   fileSequence7.ts
   #EXTINF:10,
   #EXT-X-KEY:METHOD=SAMPLE-AES,URI="skd://two?cek=f6efc698b96cf8f4fa46d5237d
   337c77&iv=18401077091784bcda8079acf978dc95",KEYFORMAT="com.apple.streaming
   keydelivery",KEYFORMATVERSIONS="1"
   #EXTINF:10,
   fileSequence8.ts
   #EXTINF:10,
   ```
