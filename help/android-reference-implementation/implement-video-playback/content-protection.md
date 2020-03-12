---
description: Le lecteur Primetime prend en charge l’intégration DRM Primetime comme DRM personnalisé. Cela signifie que votre application doit implémenter le d’authentification DRM  avant de lire le flux.
seo-description: Le lecteur Primetime prend en charge l’intégration DRM Primetime comme DRM personnalisé. Cela signifie que votre application doit implémenter le d’authentification DRM  avant de lire le flux.
seo-title: Protection du contenu DRM
title: Protection du contenu DRM
uuid: 95c446f6-8304-4d70-9bef-7368b9364025
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Protection du contenu DRM {#drm-content-protection}

Le lecteur Primetime prend en charge l’intégration DRM Primetime comme DRM personnalisé. Cela signifie que votre application doit implémenter le d’authentification DRM  avant de lire le flux.

Pour activer cette fonctionnalité, TVSDK fournit le gestionnaire DRM pour l’authentification. L’implémentation de référence fournit un exemple de  de suivant :

* Comment charger et lire les flux HLS avec la protection de contenu Access, optimisée pour les faibles taux d&#39;erreur et les  rapides.
* Comment charger et lire des flux HLS avec la protection de contenu AES128.
* Comment charger et lire les flux HLS avec protection de contenu PHLS, optimisé pour les faibles taux d&#39;erreurs et les  rapides.

Tout le contenu protégé par DRM est géré automatiquement par les bibliothèques DRM intégrées à TVSDK. Cependant, vous pouvez exposer la gestion des erreurs, l’optimisation de l’individualisation des périphériques et l’acquisition de licences à l’aide des rappels d’API TVSDK.

## Ajouter la protection du contenu au lecteur {#section_F1FC4322C35C4FE8A3B47FDC0A74221B}

Vous pouvez ajouter une protection du contenu au lecteur en créant un gestionnaire de lecture ou en utilisant la fabrique de gestionnaires.

Pour créer un gestionnaire de protection du contenu :

* Initialisez le système DRM.

   L’exemple de code suivant illustre l’appel `loadDRMServices` dans la `onCreate()` fonction de l’application, afin de vous assurer que toute initialisation requise pour le système DRM est lancée avant le démarrage de la lecture.

   ```java
   @Override 
    public void onCreate() { 
        super.onCreate();  
        DrmManager.loadDRMServices(getApplicationContext()); 
    }
   ```

* Préchargez les licences DRM.

   L’exemple de code suivant illustre le chargement de la `VideoItems` page lorsque le chargement du de contenu est terminé. Les licences DRM seront ainsi acquises à partir du serveur de licences et mises en cache localement, de sorte que, lors de la  de lecture, le contenu se chargera avec un délai minimal.

   ```java
   DrmManager.preLoadDrmLicenses(item.getUrl(),  
     new MediaPlayerItemLoader.LoaderListener() { 
   
       @Override 
       public void onLoadComplete(MediaPlayerItem item) { 
           Player.logger.w(LOG_TAG + "::DRMPreload#onLoadComplete", item.getResource().getUrl()); 
       } 
   
       @Override 
       public void onError(MediaErrorCode errorCode, String s) { 
           Player.logger.e(LOG_TAG + "::DRMPreload#onError", s); 
       } 
   } 
   ```

   >[!NOTE]
   >
   >Vous pouvez définir les licences DRM Precache sur Activé dans l’interface utilisateur des paramètres afin qu’elles préviennent les licences DRM lors du chargement du contenu. Toutefois, il est recommandé de précharger un élément spécifique au lieu de prédéfinir toutes les licences du catalogue.
   >
   >![](assets/precache-drm-licenses.jpg)

* Pour `ManagerFactory` mettre en oeuvre la gestion des erreurs DRM, assurez-vous que la ligne de code suivante figure dans le [!DNL PlayerFragment.java] fichier :

   ```java
   drmManager = ManagerFactory.getDrmManager(config, mediaPlayer);
   ```

**Documentation sur les API connexes**

* [Classe DrmManager](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/DrmManager.html)
* [DrmManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/DrmManager.DrmManagerEventListener.html)