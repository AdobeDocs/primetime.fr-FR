---
title: Présentation du processus d’acquisition de licences
description: Présentation du processus d’acquisition de licences
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# Présentation du processus d’acquisition de licences{#license-acquisition-process-overview}

L’activation de votre application pour lire du contenu sous la protection de Primetime DRM est décrite dans les sections suivantes, à l’aide d’exemples de code ActionScript 3 (AS3). Les écarts nuancés par rapport à ce workflow pour les applications natives sur les plateformes mobiles sont présentés le cas échéant. Toutefois, les workflows DRM Primetime sont très similaires sur toutes les plateformes. Par conséquent, votre compréhension du code AS3 rendra l’extrapolation à d’autres plateformes assez simple.

**Processus d’acquisition de licence :**

1. Obtenez les métadonnées DRM du contenu protégé.
1. Vérifiez si une licence est disponible localement :

   * Si la licence est disponible localement, chargez-la et passez à l’étape 6.
   * Si la licence n’est pas disponible localement, passez à l’étape 3.

1. Vérifiez si l’authentification est requise :

   * Si l’authentification est requise, obtenez les informations d’identification d’authentification de l’utilisateur et transmettez-les au serveur de licences.
   * Si l’authentification n’est pas requise, passez à l’étape 6.

1. Si l’enregistrement du domaine d’appareil est requis, rejoignez le domaine d’appareil.
1. Si une authentification était nécessaire et est maintenant terminée, téléchargez la licence à partir du serveur de licences.
1. Lire le contenu.

Si aucune erreur ne s’est produite et que l’utilisateur a été autorisé à afficher le contenu, Primetime envoie une `DRMStatusEvent` et que l’application commence la lecture. La variable `DRMStatusEvent` contient les informations de licence associées, qui identifient la stratégie et les autorisations de l’utilisateur. Par exemple : `DRMStatusEvent` peut contenir des informations indiquant si le contenu peut être mis hors ligne, à l’expiration de la licence, etc.

L’application peut utiliser les informations de licence pour informer l’utilisateur de l’état de sa stratégie. Par exemple, l’application peut afficher le nombre de jours restant à l’utilisateur pour afficher le contenu dans une barre d’état. Si l’utilisateur est autorisé à accéder hors ligne, la licence est mise en cache et le contenu chiffré est téléchargé sur l’ordinateur de l’utilisateur. Le contenu est rendu accessible pendant la durée définie dans la durée de mise en cache de la licence. La propriété detail de l’événement contient `DRM.voucherObtained`. L’application décide de l’emplacement de stockage local du contenu pour qu’il soit disponible hors ligne. Vous pouvez également précharger des licences à l’aide de la méthode `DRMManager` classe .
