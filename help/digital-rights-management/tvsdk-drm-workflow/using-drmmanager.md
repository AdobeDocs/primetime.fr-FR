---
title: Utilisation de la classe DRMManager - Aperçu
description: Utilisation de la classe DRMManager - Aperçu
copied-description: true
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---


# Utilisation de la classe DRMManager {#using-the-drmmanager-class}

Utilisez la variable `DRMManager` pour gérer les licences et les sessions de serveur de licences Primetime DRM dans les applications.

**Gestion des licences**

Chaque fois qu’un appareil lit du contenu protégé, l’exécution obtient et met en cache la licence requise pour afficher le contenu. Si l’application enregistre le contenu localement et que la licence permet la lecture hors ligne, l’utilisateur peut afficher le contenu dans l’application sans connexion réseau. En utilisant la variable `DRMManager`, vous pouvez pré-mettre en cache la licence. L’application n’a pas besoin d’obtenir la licence nécessaire pour afficher le contenu. Par exemple, votre application peut télécharger le fichier multimédia, puis obtenir la licence lorsque l’utilisateur est toujours en ligne.

Pour précharger une licence, utilisez une `DRMContentData` . La variable `DRMContentData` contient l’URL du serveur de licences DRM Primetime qui peut fournir la licence et décrit si l’authentification de l’utilisateur est requise. Grâce à ces informations, vous pouvez appeler la fonction `DRMManager` `loadVoucher()` pour obtenir et mettre en cache la licence. Le workflow des licences de préchargement est décrit plus en détail dans la section *Licences de préchargement pour la lecture hors ligne*.

**Gestion des sessions**

Vous pouvez également utiliser la variable `DRMManager` pour authentifier l’utilisateur sur un serveur de licences DRM Primetime et pour gérer les sessions persistantes. Appelez le `DRMManager` `authenticate()` pour établir une session avec le serveur de licences Primetime DRM. Une fois l’authentification terminée, la variable `DRMManager` distribue une `DRMAuthenticationCompleteEvent` . Cet objet contient un jeton de session. Vous pouvez enregistrer ce jeton pour établir les sessions suivantes afin que l’utilisateur n’ait pas à fournir les informations d’identification de son compte. Transmettez le jeton à la fonction `setAuthenticationToken()` pour établir une nouvelle session authentifiée. (Les paramètres du serveur qui a généré le jeton déterminent l’expiration du jeton et d’autres attributs.)

## Gestion des événements DRMStatus {#handling-drmstatus-events}

La variable `DRMManager` distribue une `DRMStatusEvent` après un appel à la fonction `loadVoucher()` se termine correctement. Si une licence est obtenue, la propriété detail de l’objet d’événement a la valeur : `DRM.voucherObtained`et la propriété de bon contient le paramètre `DRMVoucher` . Si aucune licence n’est obtenue, la propriété detail a toujours la valeur : `DRM.voucherObtained`; toutefois, la propriété du bon est nulle. Une licence ne peut pas être obtenue si, par exemple, vous utilisez la méthode `LoadVoucherSetting` de `localOnly` et il n’existe pas de licence mise en cache localement. Si la variable `loadVoucher()` L’appel ne se termine pas correctement, peut-être en raison d’une erreur d’authentification ou de communication, alors la variable `DRMManager` distribue une `DRMErrorEvent` ou `DRMAuthenticationErrorEvent` à la place.

## Gestion des événements DRMAuthenticationComplete{#handling-drmauthenticationcomplete-events}

La variable `DRMManager` distribue une `DRMAuthenticationCompleteEvent` lorsqu’un utilisateur est authentifié avec succès au moyen d’un appel à la fonction `authenticate()` . La variable `DRMAuthenticationCompleteEvent` contient un jeton réutilisable pouvant être utilisé pour conserver l’authentification de l’utilisateur entre les sessions d’application. Transmettre ce jeton à `DRMManager` `setAuthenticationToken()` pour rétablir la session. (Le créateur de jetons définit des attributs de jeton tels que l’expiration. Adobe ne fournit pas d’API pour examiner les attributs de jeton.)

## Gestion des événements DRMAuthenticationError{#handling-drmauthenticationerror-events}

La variable `DRMManager` distribue une `DRMAuthenticationErrorEvent` lorsqu’un utilisateur ne peut pas être authentifié avec succès au moyen d’un appel à la fonction `authenticate()` ou `setAuthenticationToken()` méthodes.