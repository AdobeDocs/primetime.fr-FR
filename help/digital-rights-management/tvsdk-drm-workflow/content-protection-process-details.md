---
seo-title: Détails du processus d'acquisition de licence
title: Détails du processus d'acquisition de licence
uuid: 4825c49e-fa6f-4c98-9d21-a2743930ca2e
translation-type: tm+mt
source-git-commit: 3fdef12b717bb6f70ca27d9278de61d709f8349c
workflow-type: tm+mt
source-wordcount: '968'
ht-degree: 0%

---


# Détails du processus d&#39;acquisition de licence {#license-acquisition-process-details}

Ce processus présente une vue détaillée au niveau de l’API du flux de travaux de contenu protégé DRM Primetime :

1. A l’aide d’un objet `URLLoader`, chargez les octets du fichier de métadonnées du contenu protégé.

   Définissez cet objet sur une variable, telle que `metadata_bytes`. Tout le contenu contrôlé par Primetime DRM comporte des métadonnées DRM Primetime. Lorsque le contenu est compressé, ces métadonnées peuvent être enregistrées dans un fichier de métadonnées distinct ( [!DNL .metadata]) en même temps que le contenu. Les métadonnées peuvent également être codées en base 64 et insérées dans le corps du fichier de manifeste vidéo. Pour plus d’informations, voir [Création de packages de fichiers multimédias](../protecting-content/packaging-media-overview/packaging-media-files.md).
   1. Si nécessaire, supprimez le point d’exclamation `!` du début de la chaîne.
   1. Si nécessaire pour le contenu HLS ou HDS, décodez les métadonnées incluses dans la chaîne codée en Base64 en données binaires avant de les transmettre.
1. Créez une instance `DRMContentData`.

   Placez ce code dans un bloc try-catch :

   ```
   new DRMContentData(metadata_bytes)
   ```

   où `metadata_bytes` est l&#39;objet `URLLoader` obtenu à l&#39;étape 1.

   [iOS : DRMMetadata](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_metadata.html)

   [Android : DRMMetadata](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/index.html)

1. Créez des écouteurs pour écouter les `DRMStatusEvent` et `DRMErrorEvent` envoyés à partir de l’objet `DRMManager`.

   ```
   DRMManager.addEventListener(DRMStatusEvent.DRM_STATUS, onDRMStatus); 
   DRMManager.addEventListener(DRMErrorEvent.DRM_ERROR, onDRMError);
   ```

   Dans le module d’écoute `DRMStatusEvent`, vérifiez que la licence est valide (et non nulle). Dans l&#39;écouteur `DRMErrorEvent`, gérez `DRMErrorEvents`. Voir *Utilisation de la classe DRMStatusEvent* et *Utilisation de la classe DRMErrorEvent* dans ce guide.

1. Chargez la licence requise pour lire le contenu.
Tout d&#39;abord, essayez de charger une licence stockée localement pour lire le contenu :

   ```
   DRMManager.loadvoucher(drmContentData, LoadVoucherSetting.LOCAL_ONLY)
   ```

   [Android : DRMManager.purchaseLicense()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#acquireLicense(com.adobe.ave.drm.DRMMetadata,%20com.adobe.ave.drm.DRMAcquireLicenseSettings,%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMLicenseAcquiredCallback))

   [iOS : acquérirLicense :](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a52accb5ed5b49d6e5d91277d78279f1b)

   Une fois le chargement terminé, l’objet `DRMManager` distribue `DRMStatusEvent.DRM_Status`.

1. Vérifiez l&#39;objet `DRMVoucher`.


   Si l&#39;objet `DRMVoucher` n&#39;est pas nul, la licence est valide. Accédez à l’étape 9.

   [Android : DRMLicenseAcquiredCallback](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMLicenseAcquiredCallback.html)

   [iOS : DRMLicenseAcquired](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/_d_r_m_interface_8h.html#afe5a9e3a003f312ee268d9b00927fa6d)
1. Vérifiez la méthode d’authentification requise par la stratégie pour ce contenu.

   Utilisez la propriété `DRMContentData.authenticationMethod`.
   1. Si la méthode d’authentification est `ANONYMOUS`, passez à l’étape 9. 

      [Android : DRMAuthenticationMethod](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/index.html?com/adobe/ave/drm/DRMLicenseAcquiredCallback.html)

      [iOS : DRMAuthenticationMethod](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/_d_r_m_interface_8h.html#a2003f29af93898b52a4123c2dd92c457)
   1. Si la méthode d’authentification est `USERNAME_AND_PASSWORD`, votre application doit fournir un mécanisme permettant à l’utilisateur de saisir des informations d’identification.

      Transmettez les informations d’identification de l’utilisateur au serveur de licences pour authentifier l’utilisateur :

      ```
      DRMManager.authenticate( metadata.serverURL, metadata.domain, username, password)
      ```

      `DRMManager` distribue un `DRMAuthenticationErrorEvent` en cas d&#39;échec de l&#39;authentification ou un `DRMAuthenticationCompleteEvent` en cas de réussite de l&#39;authentification. Créez des écouteurs pour ces événements.

      [Android : authenticate()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#authenticate(com.adobe.ave.drm.DRMMetadata,%20java.lang.String,%20java.lang.String,%20java.lang.String,%20java.lang.String,%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMAuthenticationCompleteCallback))

      [iOS : authentifier :](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a169c1441f196a834094a8e0f5ecb4aca)

      >[!NOTE]
      >
      >Adobe recommande d’utiliser un mécanisme plus sécurisé pour fournir des informations d’identification. Pour obtenir une référence, voir [KeyGenParameterSpec](https://developer.android.com/reference/android/security/keystore/KeyGenParameterSpec.html).

   1. Si la méthode d&#39;authentification est `UNKNOWN`, vous devez utiliser une méthode d&#39;authentification personnalisée.

      Dans ce cas, le fournisseur de contenu a pris les dispositions nécessaires pour que l’authentification soit faite hors bande, sans utiliser les API Primetime. La procédure d&#39;authentification personnalisée doit produire un jeton d&#39;authentification qui peut être transmis à la méthode `DRMManager.setAuthenticationToken()`.

      [Android : setAuthenticationToken()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#setAuthenticationToken(com.adobe.ave.drm.DRMMetadata,%20java.lang.String,%20byte[],%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMOperationCompleteCallback))

      [iOS : setAuthenticationToken :](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a17884b5d9bcc5b0b39503f61140f9b09)

      >[!NOTE]
      >
      >Vous pouvez également utiliser `.setAuthenticationToken()`, quelle que soit la méthode d’authentification utilisée, pour envoyer des données personnalisées du client au serveur de licences. Il s’agit d’une surcharge de l’API, car ce mécanisme est le seul moyen d’envoyer des données personnalisées dynamiques du client au serveur de licences au moment de l’acquisition de la licence. Cette méthode de transport de données personnalisées est examinée en détail dans plusieurs publications de forum dans les [forums DRM (Accès aux Adobes) de Primetime ](https://forums.adobe.com/community/adobe_access).

1. Si l’authentification échoue, votre application doit revenir à l’étape 6.

   Assurez-vous que votre application dispose d’un mécanisme permettant de gérer et de limiter les échecs d’authentification répétés. Par exemple, après trois tentatives, vous affichez un message à l’utilisateur indiquant que l’authentification a échoué et que le contenu ne peut pas être lu.
1. Pour utiliser le jeton stocké au lieu d’inviter l’utilisateur à entrer des informations d’identification, définissez le jeton avec la méthode `DRMManager.setAuthenticationToken()`.

   Vous pouvez ensuite télécharger la licence à partir du serveur de licences et lire le contenu comme à l’étape 6.
   1. **Facultatif :** si l’authentification réussit, vous pouvez capturer le jeton d’authentification, qui est un tableau d’octets mis en cache dans la mémoire.

      Obtenez ce jeton avec la propriété `DRMAuthenticationCompleteEvent.token`. Vous pouvez stocker et utiliser le jeton d’authentification afin que l’utilisateur n’ait pas à entrer à plusieurs reprises les informations d’identification pour ce contenu. Le serveur de licences détermine la période de validité du jeton d’authentification.

      [Android : OperationComplete()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMOperationCompleteCallback.html)

      [iOS : DRMOperationComplete](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/_d_r_m_interface_8h.html#a5f2392ec6661b51bf7b0df71cd514731)
1. Si l’authentification réussit, téléchargez la licence à partir du serveur de licences :

   ```
   DRMManager.loadvoucher( 
      drmContentData, 
      LoadVoucherSetting.FORCE_REFRESH)
   ```

   Une fois le chargement terminé, l’objet `DRMManager` distribue `DRMStatusEvent.DRM_STATUS`. Prêtez attention à ce événement et, lorsqu’il est distribué, vous pouvez lire le contenu.  Lisez la vidéo en créant un objet Primetime, puis en appelant sa méthode `play()` :

   ```
   stream = new Primetime(connection); 
   stream.addEventListener(DRMStatusEvent.DRM _STATUS, drmStatusHandler); 
   stream.addEventListener(DRMErrorEvent.DRM_ERROR, drmErrorHandler); 
   stream.addEventListener(NetStatusEvent.NET_STATUS, netStatusHandler); 
   stream.client = new CustomClient(); 
   video.attachPrimetime(stream); 
   stream.play(videoURL);
   ```

   [Android : acquisitionLicense()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#acquireLicense(com.adobe.ave.drm.DRMMetadata,%20com.adobe.ave.drm.DRMAcquireLicenseSettings,%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMLicenseAcquiredCallback))

   [iOS : acquérirLicense :](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a52accb5ed5b49d6e5d91277d78279f1b)