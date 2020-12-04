---
description: Adobe fournit un service DRM Cloud aux clients Adobe Primetime DRM qui ne souhaitent pas développer et gérer leur propre serveur de licences DRM Primetime. En utilisant ce service, les clients peuvent réduire la complexité opérationnelle et de développement liée à l'émission de licences DRM. Primetime Cloud DRM peut émettre des licences DRM sur tous les périphériques capables d’exécuter une application vidéo compatible avec le SDK du navigateur Primetime, telle que iOS, Android, Ordinateurs de bureau et Xbox360. Ce service DRM est hébergé et géré par Adobe, avec une disponibilité 24h/24 et 7j/7.
seo-description: Adobe fournit un service DRM Cloud aux clients Adobe Primetime DRM qui ne souhaitent pas développer et gérer leur propre serveur de licences DRM Primetime. En utilisant ce service, les clients peuvent réduire la complexité opérationnelle et de développement liée à l'émission de licences DRM. Primetime Cloud DRM peut émettre des licences DRM sur tous les périphériques capables d’exécuter une application vidéo compatible avec le SDK du navigateur Primetime, telle que iOS, Android, Ordinateurs de bureau et Xbox360. Ce service DRM est hébergé et géré par Adobe, avec une disponibilité 24h/24 et 7j/7.
seo-title: Contexte
title: Contexte
uuid: 11a5b9ea-ebd2-47e0-b078-af2a3e1f7bf6
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---


# Arrière-plan {#background}

Adobe fournit un service DRM Cloud aux clients Adobe Primetime DRM qui ne souhaitent pas développer et gérer leur propre serveur de licences DRM Primetime. En utilisant ce service, les clients peuvent réduire la complexité opérationnelle et de développement liée à l&#39;émission de licences DRM. Primetime Cloud DRM peut émettre des licences DRM sur tous les périphériques capables d’exécuter une application vidéo compatible avec le SDK du navigateur Primetime, telle que iOS, Android, Ordinateurs de bureau et Xbox360. Ce service DRM est hébergé et géré par Adobe, avec une disponibilité 24h/24 et 7j/7.

>[!NOTE]
>
>Adobe Primetime DRM s&#39;appelait auparavant Adobe Access, et avant cela, Flash Access.

## Qu’est-ce qui est inclus avec le DRM de Primetime Cloud {#section_788D0DD5F6DB41678FD87CFBD21B25FD}

* Module d’authentification/droits personnalisés et instructions sur la façon d’utiliser l’authentification personnalisée pour votre contenu. Pour plus de documentation, consultez le répertoire [!DNL Custom Authentication Entitlement].
* Certificat de serveur de licence spécifique à Cloud DRM ( [!DNL .pem/.cer/.der])

* Certificat de transport de serveur de licences DRM spécifique à Cloud ( [!DNL .pem/.cer/.der])

* Primetime Java Offline Packager
* Exemples de stratégies DRM pour la création de package

   * **policy_24h**  - Cache des licences sur le disque pendant 24 heures. Après 24 heures, une nouvelle licence doit être acquise pour vue du contenu. Toutes les autres stratégies de ce kit disposent également d’une mise en cache des licences 24 heures sur 24.
   * **policy_ios_remotekeyserver**  - Sur les périphériques iOS, la licence DRM est acquise à partir de Cloud DRM. De plus, le client acquerra toutes les clés de déchiffrement AES de Cloud DRM. La lecture n’est pas autorisée sur les appareils iOS endommagés.

   * **policy_ios_localkeyserver**  - Sur les périphériques iOS, la licence DRM est acquise à partir de Cloud DRM. En outre, le client acquiert toutes les clés de déchiffrement HLS AES d’un serveur HTTP local, au lieu de Cloud DRM. La lecture n’est pas autorisée sur les appareils iOS endommagés.

   * **policy_adobePass**  : le client doit d’abord s’authentifier avec (anciennement appelé Adobe Pass), sinon une licence sera refusée.

* Outil Gestionnaire de stratégies d&#39;Adobe pour créer des stratégies DRM supplémentaires
* Exemple de contenu vidéo à utiliser pour le conditionnement

