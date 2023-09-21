---
description: Le lecteur Primetime prend en charge l’intégration DRM Primetime en tant que processus DRM personnalisés. Cela signifie que votre application doit mettre en oeuvre les processus d’authentification DRM avant de lire le flux.
title: Protection du contenu DRM
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# Protection du contenu DRM {#drm-content-protection}

Le lecteur Primetime prend en charge l’intégration DRM Primetime en tant que processus DRM personnalisés. Cela signifie que votre application doit mettre en oeuvre les processus d’authentification DRM avant de lire le flux.

Pour activer cette fonctionnalité, TVSDK fournit le gestionnaire DRM pour l’authentification. L’implémentation de référence fournit un exemple des workflows suivants :

* Comment charger et lire des flux HLS avec protection de contenu Access, optimisée pour des taux d’erreur faibles et un démarrage rapide.
* Comment charger et lire des flux HLS avec protection de contenu AES128.
* Comment charger et lire des flux HLS avec protection de contenu PHLS, optimisée pour des taux d’erreur faibles et un démarrage rapide.

Tout le contenu protégé par DRM est géré automatiquement par les bibliothèques DRM intégrées à TVSDK. Cependant, vous pouvez exposer la gestion des erreurs, l’optimisation de l’individualisation des appareils et l’acquisition de licences à l’aide des rappels d’API TVSDK.

## Ajout d’une protection de contenu au lecteur {#section_F1FC4322C35C4FE8A3B47FDC0A74221B}

Vous pouvez ajouter une protection de contenu au lecteur en créant un gestionnaire de lecture ou à l’aide de la fabrique de gestionnaires.

Pour créer un gestionnaire de protection de contenu :

* Initialisez le système DRM.

  L’exemple de code suivant montre comment appeler `loadDRMServices` dans l’application `onCreate()` pour garantir que toute initialisation requise pour le système DRM est lancée avant le démarrage de la lecture.

  ```java
  @Override 
   public void onCreate() { 
       super.onCreate();  
       DrmManager.loadDRMServices(getApplicationContext()); 
   }
  ```

* Préchargez les licences DRM.

  L’exemple de code suivant illustre le chargement de la variable `VideoItems` lorsque le chargement de la liste de contenu est terminé. Les licences DRM sont ainsi acquises à partir du serveur de licences et mises en cache localement, de sorte que lorsque la lecture démarre, le contenu se charge avec un délai minimal.

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
  >Vous pouvez définir les licences Precache DRM sur ON dans l’interface utilisateur de Paramètres pour qu’elles soient prêtes lors du chargement du contenu. Toutefois, la bonne pratique consiste à précharger un élément spécifique au lieu de précharger toutes les licences du catalogue.
  >
  >![](assets/precache-drm-licenses.jpg)

* Pour utiliser `ManagerFactory` pour mettre en oeuvre la gestion des erreurs DRM, assurez-vous que la ligne de code suivante figure dans la variable [!DNL PlayerFragment.java] fichier :

  ```java
  drmManager = ManagerFactory.getDrmManager(config, mediaPlayer);
  ```

**Documentation sur les API connexe**

* [Classe DrmManager](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/DrmManager.html)
* [DrmManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/DrmManager.DrmManagerEventListener.html)
