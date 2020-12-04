---
seo-title: Prévisualisation de licence
title: Prévisualisation de licence
uuid: 3171647d-1437-48ab-9659-3eb363993618
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---


# Prévisualisation de licence{#license-preview}

Le client peut envoyer une demande de prévisualisation de licence, ce qui signifie que l’application peut effectuer une opération de prévisualisation avant de demander à l’utilisateur d’acheter le contenu afin de déterminer si l’ordinateur de l’utilisateur satisfait réellement à tous les critères requis pour la lecture. *Le* prévisualiseur de licence fait référence à la capacité du client à prévisualisation la licence (pour déterminer les droits autorisés par la licence) plutôt qu’à prévisualiser le contenu (en visualisant une petite partie du contenu avant de décider d’acheter). Voici quelques-uns des paramètres propres à chaque machine : sorties disponibles et leur état de protection, la version d’exécution/DRM disponible et le niveau de sécurité du client DRM. Le mode de prévisualisation des licences permet au client d’exécution/DRM de tester la logique métier du serveur de licences et de fournir des informations à l’utilisateur afin qu’il puisse prendre une décision éclairée. Ainsi, le client peut voir à quoi ressemble une licence valide mais ne recevra pas réellement la clé pour déchiffrer le contenu. La prise en charge de la prévisualisation de licence est facultative et n’est nécessaire que si vous implémentez un client personnalisé qui utilise cette fonctionnalité.

Pour déterminer si le client a envoyé une demande de prévisualisation ou d&#39;acquisition de licence, appelez `LicenseRequestMessage.getRequestPhase()`et comparez-la à `LicenseRequestMessage.RequestPhase.Acquire`
