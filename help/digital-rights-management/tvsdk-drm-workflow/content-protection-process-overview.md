---
seo-title: Présentation du processus d'acquisition de licence
title: Présentation du processus d'acquisition de licence
uuid: c2eedd0a-3e3a-4c2f-a781-855f0ba65b15
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Présentation du processus d&#39;acquisition de licence{#license-acquisition-process-overview}

L’activation de votre application pour lire du contenu sous la protection de Primetime DRM est décrite dans les sections suivantes, à l’aide d’exemples de code ActionScript 3 (AS3). Les écarts nuancés par rapport à ce processus pour les applications natives sur les plateformes mobiles sont présentés le cas échéant. Les workflows DRM de Primetime sont très similaires sur toutes les plates-formes, cependant, votre compréhension du code AS3 rendra l&#39;extrapolation à d&#39;autres plateformes assez simple.

**Processus d&#39;acquisition de licence :**

1. Obtenez les métadonnées DRM du contenu protégé.
1. Vérifiez si une licence est disponible localement :

   * Si la licence est disponible localement, chargez-la et passez à l’étape 6.
   * Si la licence n’est pas disponible localement, passez à l’étape 3.

1. Vérifiez si l&#39;authentification est requise :

   * Si l’authentification est requise, récupérez les informations d’identification d’authentification auprès de l’utilisateur et transmettez-les au serveur de licences.
   * Si l’authentification n’est pas requise, passez à l’étape 6.

1. Si l’enregistrement du domaine de l’appareil est requis, joignez-le au domaine de l’appareil.
1. Si l’authentification était nécessaire et est maintenant terminée, téléchargez la licence à partir du serveur de licences.
1. Lisez le contenu.

Si aucune erreur ne s’est produite et que l’utilisateur a été autorisé à vue du contenu, Primetime distribue un `DRMStatusEvent` objet et l’application commence la lecture. L’ `DRMStatusEvent` objet contient les informations de licence associées, qui identifient la stratégie et les autorisations de l’utilisateur. Par exemple, `DRMStatusEvent` peut contenir des informations indiquant si le contenu peut être rendu disponible hors ligne, à l’expiration de la licence, etc.

L’application peut utiliser les informations de licence pour informer l’utilisateur de l’état de sa stratégie. Par exemple, l’application peut afficher le nombre de jours restant à l’utilisateur pour afficher le contenu dans une barre d’état. Si l’utilisateur est autorisé à accéder hors connexion, la licence est mise en cache et le contenu chiffré est téléchargé sur l’ordinateur de l’utilisateur. Le contenu est rendu accessible pendant la durée définie dans la mise en cache de la licence. La propriété detail du événement contient `DRM.voucherObtained`. L’application décide de l’emplacement de stockage local du contenu afin qu’il soit disponible hors ligne. Vous pouvez également précharger des licences en utilisant la `DRMManager` classe.
