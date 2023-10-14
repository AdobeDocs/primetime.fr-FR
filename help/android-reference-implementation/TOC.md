---
product: primetime
audience: end-user
user-guide-title: Aide à l’implémentation des références Primetime
user-guide-description: Permet de comprendre le TVSDK et de modifier les gestionnaires de fonctionnalités pour personnaliser votre lecteur personnel.
source-git-commit: 95626ebde981d1996652a67bc9e0cea05f24aa6d
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 8%

---


# Mise en oeuvre de référence du PSDK 1.4 pour Android {#reference-implementation}

+ [Présentation de l’implémentation de référence Android](home.md)
+ Implémentation de référence Primetime {#reference}
   + [Utilisation de l’implémentation de référence Primetime](ref-implementation/how-to-use-ref-player.md)
   + [Structure de l’implémentation de référence](ref-implementation/ref-player-structure.md)
   + Utilisation des gestionnaires de fonctionnalités {#feature-managers}
      + [Utilisation des gestionnaires de fonctionnalités](ref-implementation/using-feature-managers/how-to-use-feature-managers.md)
      + [Création de gestionnaires de fonctionnalités en transmettant des informations de configuration au lecteur multimédia...](ref-implementation/using-feature-managers/creating-feature-managers.md)
      + [Activation ou désactivation des fonctionnalités à l’aide de ManagerFactory](ref-implementation/using-feature-managers/turning-features-on-off.md)
      + [Gestion des événements](ref-implementation/using-feature-managers/handling-events.md)
   + Configuration de votre environnement de développement {#setup-dev}
      + [Configuration de votre environnement de développement](set-up-dev-environment/set-up-dev-environment-overview.md)
      + [Téléchargement et configuration d’un logiciel prérequis](set-up-dev-environment/download-prereqs-android.md)
      + [Création de l’implémentation de référence Primetime](set-up-dev-environment/install-the-ref-player-project.md)
   + Exploration du code {#explore-code}
      + [PlayerFragment](set-up-dev-environment/exploring-code/player-fragment.md)
      + [Gestionnaires de fonctionnalités](set-up-dev-environment/exploring-code/about-psdk-feature-managers.md)
      + [ConfigProvider](set-up-dev-environment/exploring-code/config-provider.md)
      + [SettingsActivity](set-up-dev-environment/exploring-code/settings-activity.md)
      + [Format du catalogue](set-up-dev-environment/exploring-code/catalog-format.md)
      + [Objet JSON pour les publicités Primetime](set-up-dev-environment/exploring-code/json-pt-ads.md)
      + [Objet JSON pour les coupures publicitaires directes](set-up-dev-environment/exploring-code/json-direct-ad-breaks.md)
      + [Objet JSON pour les marqueurs publicitaires personnalisés](set-up-dev-environment/exploring-code/json-custom-ad-markers.md)
      + [Objet JSON pour l’ID de ressource de droit](set-up-dev-environment/exploring-code/json-entitlement-resource-id.md)
      + [Exemple de format de flux JSON](set-up-dev-environment/exploring-code/example-json-feed-format.md)
   + Mise en oeuvre de la lecture vidéo {#implement-video}
      + [Opérations essentielles de lecture vidéo](implement-video-playback/video-playback.md)
      + [Activation de la lecture vidéo](implement-video-playback/enable-video-playback.md)
      + [Protection du contenu DRM](implement-video-playback/content-protection.md)
   + [Débit binaire multiple](implement-video-playback/mbr.md)
   + Configuration d’un lecteur pour la lecture du contenu numérique (DVR) avec des publicités {#dvr}
      + [DVR sans insertion de publicité](implement-video-playback/dvr/dvr-without-ad-insertion.md)
      + [Enregistreur numérique avec insertion de publicités](implement-video-playback/dvr/dvr-with-ad-insertion.md)
      + [Choix d’un point de départ personnalisé pour la conservation des données](implement-video-playback/dvr/dvr-custom-start-point.md)
      + [Définition d’une heure de début personnalisée dans l’implémentation de référence](implement-video-playback/dvr/set-custom-start-time-dvr.md)
   + [Affichage des statistiques de lecture QoS et d’appareil](implement-video-playback/qos-statistics.md)
   + Insérer des publicités {#insert-ads}
      + [Insertion de publicités](insert-ads/ad-insertion.md)
      + [Types d’insertion de publicités](insert-ads/ad-insertion-types.md)
      + [Ajouter de la publicité](insert-ads/add-advertising.md)
      + [Documentation sur les API connexe](insert-ads/aps-callbacks-ad-insertion.md)
   + Liaison audio tardive {#late-binding-audio}
      + [Présentation](late-binding-audio/late-binding-audio-overview.md)
      + [Intégrer du contenu audio à liaison tardive](late-binding-audio/aa-enable.md)
      + [Sélectionner les pistes audio](late-binding-audio/select-audio-tracks.md)
      + [Documentation sur les API connexe](late-binding-audio/aa-api-callbacks.md)
   + Flux de droits d’authentification Primetime {#primetime-authentications}
      + [Présentation](paytvpass-entitlement/paytvpass-entitlement-overview.md)
      + [Présentation du Gestionnaire de droits](paytvpass-entitlement/entitlement-overvivew.md)
      + [Intégration de l’authentification Primetime](paytvpass-entitlement/integrate-pass.md)
      + [Configuration des rapports Adobe Analytics](paytvpass-entitlement/pass-analytics-setup.md)
      + [Documentation sur les API connexe](paytvpass-entitlement/pass-apis-callbacks.md)
   + Analyses de vidéos {#video-analytics}
      + [Analyses de vidéos](video-analytics/video-analytics-overview.md)
      + [Création de Video Analytics Manager](video-analytics/create-video-analytics-manager.md)
      + [Configuration de Video Analytics](video-analytics/configure-video-analytics-manager.md)
      + [Documentation sur les API connexe](video-analytics/va-apis-callbacks.md)
   + [Création d’une interface utilisateur personnalisée](build-custom-ui.md)
   + [Dépannage](troubleshooting.md)
