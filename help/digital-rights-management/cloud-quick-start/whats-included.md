---
description: Adobe fournit un service DRM Cloud aux clients Adobe Primetime DRM qui ne souhaitent pas développer ni gérer leur propre serveur de licence DRM Primetime. En utilisant ce service, les clients peuvent réduire la complexité opérationnelle et de développement liée à l’émission de licences DRM. Primetime Cloud DRM peut émettre des licences DRM pour tous les appareils capables d’exécuter une application vidéo Primetime Browser TVSDK compatible, comme iOS, Android, Ordinateurs de bureau et Xbox360. Ce service DRM est hébergé et géré par Adobe, avec une disponibilité 24/7.
title: Contexte
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# Contexte {#background}

Adobe fournit un service DRM Cloud aux clients Adobe Primetime DRM qui ne souhaitent pas développer ni gérer leur propre serveur de licence DRM Primetime. En utilisant ce service, les clients peuvent réduire la complexité opérationnelle et de développement liée à l’émission de licences DRM. Primetime Cloud DRM peut émettre des licences DRM pour tous les appareils capables d’exécuter une application vidéo Primetime Browser TVSDK compatible, comme iOS, Android, Ordinateurs de bureau et Xbox360. Ce service DRM est hébergé et géré par Adobe, avec une disponibilité 24/7.

>[!NOTE]
>
>Adobe Primetime DRM s’appelait auparavant Accès aux Adobes, et avant cela, Flash Access.

## Éléments inclus dans Primetime Cloud DRM {#section_788D0DD5F6DB41678FD87CFBD21B25FD}

* Module d’authentification/droit personnalisé et instructions sur la manière d’utiliser l’authentification personnalisée pour votre contenu. Pour plus d’informations, reportez-vous au [!DNL Custom Authentication Entitlement] répertoire .
* Certificat de serveur de licences spécifique à DRM Cloud ( [!DNL .pem/.cer/.der])

* Certificat de transport de serveur de licences spécifique à DRM Cloud ( [!DNL .pem/.cer/.der])

* Primetime Java Offline Packager
* Exemples de stratégies DRM pour le groupement

   * **policy_24hr** - Licences de cache sur le disque pendant 24 heures. Après 24 heures, une nouvelle licence doit être acquise pour visualiser le contenu. Toutes les autres stratégies de ce kit ont également une mise en cache de licence 24 heures sur 24.
   * **policy_ios_remotekeyserver** - Sur les appareils iOS, la licence DRM sera acquise auprès de Cloud DRM. De plus, le client achètera toutes les clés de décryptage AES à partir de Cloud DRM. La lecture n’est pas autorisée sur les appareils iOS mis en prison.

   * **policy_ios_localkeyserver** - Sur les appareils iOS, la licence DRM sera acquise auprès de Cloud DRM. En outre, le client va acquérir toutes les clés de décryptage HLS AES à partir d’un serveur HTTP local, au lieu de Cloud DRM. La lecture n’est pas autorisée sur les appareils iOS mis en prison.

   * **policy_adobePass** - Le client doit d’abord s’authentifier auprès de (anciennement appelé Adobe Pass), sinon une licence lui sera refusée.

* Outil Adobe Policy Manager pour créer des stratégies DRM supplémentaires
* Exemple de contenu vidéo à utiliser pour le conditionnement
