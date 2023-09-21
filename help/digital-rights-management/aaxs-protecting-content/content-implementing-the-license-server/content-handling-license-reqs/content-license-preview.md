---
title: Aperçu de la licence
description: Aperçu de la licence
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# Aperçu de la licence{#license-preview}

Le client peut envoyer une demande d’aperçu de licence, ce qui signifie que l’application peut effectuer une opération d’aperçu avant de demander à l’utilisateur d’acheter le contenu afin de déterminer si l’ordinateur de l’utilisateur répond réellement à tous les critères requis pour la lecture. *Aperçu de la licence* fait référence à la capacité du client à prévisualiser la licence (pour voir quels droits la licence autorise) plutôt qu’à prévisualiser le contenu (visionner une petite partie du contenu avant de décider d’acheter). Certains des paramètres uniques à chaque machine sont les suivants : sorties disponibles et état de protection, version d’exécution/DRM disponible et niveau de sécurité du client DRM. Le mode d’aperçu des licences permet au client d’exécution/DRM de tester la logique commerciale du serveur de licences et de fournir des informations à l’utilisateur afin qu’il puisse prendre une décision éclairée. Ainsi, le client peut voir à quoi ressemble une licence valide mais ne reçoit pas réellement la clé pour déchiffrer le contenu. La prise en charge de l’aperçu de licence est facultative et n’est nécessaire que si vous implémentez un client personnalisé qui utilise cette fonctionnalité.

Pour déterminer si le client a envoyé une demande d’aperçu ou d’acquisition de licence, appelez `LicenseRequestMessage.getRequestPhase()`et comparez-le à `LicenseRequestMessage.RequestPhase.Acquire`
