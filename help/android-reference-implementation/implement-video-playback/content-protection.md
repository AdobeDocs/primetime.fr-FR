---
description: Le lecteur Primetime prend en charge l’intégration de DRM Primetime en tant que workflows DRM personnalisés. Cela signifie que votre application doit mettre en oeuvre les workflows d’authentification DRM avant de lire le flux.
seo-description: Le lecteur Primetime prend en charge l’intégration de DRM Primetime en tant que workflows DRM personnalisés. Cela signifie que votre application doit mettre en oeuvre les workflows d’authentification DRM avant de lire le flux.
seo-title: Protection du contenu DRM
title: Protection du contenu DRM
uuid: 95c446f6-8304-4d70-9bef-7368b9364025
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Protection du contenu DRM {#drm-content-protection}

Le lecteur Primetime prend en charge l’intégration de DRM Primetime en tant que workflows DRM personnalisés. Cela signifie que votre application doit mettre en oeuvre les workflows d’authentification DRM avant de lire le flux.

Pour activer cette fonction, TVSDK fournit le gestionnaire DRM pour l’authentification. L’implémentation de référence fournit un exemple des workflows suivants :

* Comment charger et lire les flux HLS avec la protection de contenu Access, optimisée pour des taux d&#39;erreur bas et un début rapide.
* Comment charger et lire les flux HLS avec la protection de contenu AES128.
* Comment charger et lire les flux HLS avec la protection de contenu PHLS, optimisée pour des taux d&#39;erreur bas et un début rapide.

Tout le contenu protégé par DRM est automatiquement géré par les bibliothèques DRM intégrées à TVSDK. Cependant, vous pouvez exposer la gestion des erreurs, l’optimisation de l’individualisation des périphériques et l’acquisition de licences à l’aide des rappels d’API TVSDK.

## Protection Ajouter contenu du lecteur {#section_F1FC4322C35C4FE8A3B47FDC0A74221B}

Vous pouvez ajouter une protection de contenu au lecteur en créant un gestionnaire de lecture ou en utilisant la fabrique de gestionnaires.

Pour créer un gestionnaire de protection du contenu :

* Initialisez le système DRM.

   L’exemple de code suivant montre comment appeler `loadDRMServices` la fonction `onCreate()` de l’application pour s’assurer que toute initialisation requise pour le système DRM est initialisée avant le démarrage de la lecture.

   ```java
   @Override 
    public void onCreate() { 
        super.onCreate();  
        DrmManager.loadDRMServices(getApplicationContext()); 
    }
   ```

* Préchargez les licences DRM.

   L&#39;exemple de code suivant montre comment charger la liste `VideoItems` de contenu lorsque le chargement est terminé. Ainsi, les licences DRM sont acquises à partir du serveur de licences et mises en cache localement, de sorte que, lors des débuts de lecture, le contenu se charge avec un délai minimum.

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
   >Vous pouvez définir les licences DRM Precache sur ON dans l’interface utilisateur des paramètres pour qu’elles préviennent les licences DRM lors du chargement de contenu. Cependant, la meilleure pratique consiste à précharger un élément spécifique au lieu de prédéfinir toutes les licences du catalogue.
   >
   >![](assets/precache-drm-licenses.jpg)

* Pour mettre en oeuvre `ManagerFactory` la gestion des erreurs DRM, assurez-vous que la ligne de code suivante figure dans le [!DNL PlayerFragment.java] fichier :

   ```java
   drmManager = ManagerFactory.getDrmManager(config, mediaPlayer);
   ```

**Documentation sur les API connexes**

* [Classe DrmManager](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/DrmManager.html)
* [DrmManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/DrmManager.DrmManagerEventListener.html)