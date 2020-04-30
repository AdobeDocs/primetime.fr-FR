---
cloud: experience-cloud
product: primetime
audience: end-user
user-guide-title: Aide sur l’implémentation des références Primetime
translation-type: tm+mt
source-git-commit: ''

---


# Mise en oeuvre de la référence PSDK 1.4 pour Android {#reference-implementation}

+ [Présentation de la mise en oeuvre des références Android](home.md)
+ Implémentation de référence Primetime {#reference}
   + [Utilisation de l’implémentation de référence Primetime](ref-implementation/how-to-use-ref-player.md)
   + [Structure d&#39;implémentation de référence](ref-implementation/ref-player-structure.md)
   + Utilisation des gestionnaires de fonctionnalités {#feature-managers}
      + [Utilisation des gestionnaires de fonctionnalités](ref-implementation/using-feature-managers/how-to-use-feature-managers.md)
      + [Création des gestionnaires de fonctionnalités en transmettant les informations de configuration au lecteur Media...](ref-implementation/using-feature-managers/creating-feature-managers.md)
      + [Activation ou désactivation des fonctionnalités à l’aide de ManagerFactory](ref-implementation/using-feature-managers/turning-features-on-off.md)
      + [Gestion des événements](ref-implementation/using-feature-managers/handling-events.md)
   + Configuration de votre environnement de développement {#setup-dev}
      + [Configuration de votre environnement de développement](set-up-dev-environment/set-up-dev-environment-overview.md)
      + [Téléchargement et configuration des logiciels prérequis](set-up-dev-environment/download-prereqs-android.md)
      + [Création de l’implémentation de référence Primetime](set-up-dev-environment/install-the-ref-player-project.md)
   + Explorez le code {#explore-code}
      + [PlayerFragment](set-up-dev-environment/exploring-code/player-fragment.md)
      + [Gestionnaires de fonctionnalités](set-up-dev-environment/exploring-code/about-psdk-feature-managers.md)
      + [ConfigProvider](set-up-dev-environment/exploring-code/config-provider.md)
      + [SettingsActivity](set-up-dev-environment/exploring-code/settings-activity.md)
      + [Format du catalogue](set-up-dev-environment/exploring-code/catalog-format.md)
      + [Objet JSON pour les annonces Primetime](set-up-dev-environment/exploring-code/json-pt-ads.md)
      + [Objet JSON pour les coupures publicitaires directes](set-up-dev-environment/exploring-code/json-direct-ad-breaks.md)
      + [Objet JSON pour les marqueurs publicitaires personnalisés](set-up-dev-environment/exploring-code/json-custom-ad-markers.md)
      + [Objet JSON pour l&#39;ID de ressource de droits](set-up-dev-environment/exploring-code/json-entitlement-resource-id.md)
      + [Exemple de format de flux JSON](set-up-dev-environment/exploring-code/example-json-feed-format.md)
   + Mise en oeuvre de la lecture vidéo {#implement-video}
      + [Opérations essentielles de lecture vidéo](implement-video-playback/video-playback.md)
      + [Activer la lecture vidéo](implement-video-playback/enable-video-playback.md)
      + [Protection du contenu DRM](implement-video-playback/content-protection.md)
   + [Débit multiple](implement-video-playback/mbr.md)
   + Configuration d’un lecteur pour lecture DVR avec publicités {#dvr}
      + [DVR sans insertion de publicité](implement-video-playback/dvr/dvr-without-ad-insertion.md)
      + [DVR avec insertion publicitaire](implement-video-playback/dvr/dvr-with-ad-insertion.md)
      + [Choix d’un point de départ personnalisé pour la magnétoscopie numérique](implement-video-playback/dvr/dvr-custom-start-point.md)
      + [Définir une heure de début personnalisée dans l’implémentation de référence](implement-video-playback/dvr/set-custom-start-time-dvr.md)
   + [Affichage des statistiques de lecture de la qualité de service et des périphériques](implement-video-playback/qos-statistics.md)
   + Insérer des annonces {#insert-ads}
      + [Insertion publicitaire](insert-ads/ad-insertion.md)
      + [Types d’insertion publicitaire](insert-ads/ad-insertion-types.md)
      + [Publicité Ajouter](insert-ads/add-advertising.md)
      + [Documentation sur les API connexes](insert-ads/aps-callbacks-ad-insertion.md)
   + Audio à liaison tardive {#late-binding-audio}
      + [Présentation](late-binding-audio/late-binding-audio-overview.md)
      + [Intégration d’un fichier audio à liaison tardive](late-binding-audio/aa-enable.md)
      + [Sélectionner les pistes audio](late-binding-audio/select-audio-tracks.md)
      + [Documentation sur les API connexes](late-binding-audio/aa-api-callbacks.md)
   + Flux de droits d’authentification Primetime {#primetime-authentications}
      + [Présentation](paytvpass-entitlement/paytvpass-entitlement-overview.md)
      + [Présentation du Gestionnaire de droits](paytvpass-entitlement/entitlement-overvivew.md)
      + [Intégration de l’authentification Primetime](paytvpass-entitlement/integrate-pass.md)
      + [Configuration d’Adobe Analytics Rapports](paytvpass-entitlement/pass-analytics-setup.md)
      + [Documentation sur les API connexes](paytvpass-entitlement/pass-apis-callbacks.md)
   + Analyses vidéo {#video-analytics}
      + [Analyses vidéo](video-analytics/video-analytics-overview.md)
      + [Création du gestionnaire d’analyses vidéo](video-analytics/create-video-analytics-manager.md)
      + [Configuration des analyses vidéo](video-analytics/configure-video-analytics-manager.md)
      + [Documentation sur les API connexes](video-analytics/va-apis-callbacks.md)
   + [Création d’une interface utilisateur personnalisée](build-custom-ui.md)
   + [Dépannage](troubleshooting.md)
