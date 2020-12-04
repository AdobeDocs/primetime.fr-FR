---
seo-title: Utilisation de la présentation de la classe DRMManager
title: Utilisation de la présentation de la classe DRMManager
uuid: 71ce061b-75b6-4ab5-8bbd-cafe7c3e4592
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---


# Utilisation de la classe DRMManager {#using-the-drmmanager-class}

Utilisez la classe `DRMManager` pour gérer les licences et les sessions de serveur de licences DRM Primetime dans les applications.

**Gestion des licences**

Chaque fois qu’un périphérique lit du contenu protégé, le runtime obtient et met en cache la licence requise pour la vue du contenu. Si l’application enregistre le contenu localement et que la licence permet la lecture hors ligne, l’utilisateur peut le vue dans l’application sans connexion réseau. En utilisant `DRMManager`, vous pouvez prémettre en cache la licence. L&#39;application n&#39;a pas à obtenir la licence nécessaire pour vue du contenu. Par exemple, votre application peut télécharger le fichier multimédia, puis obtenir la licence pendant que l’utilisateur est encore en ligne.

Pour précharger une licence, utilisez un objet `DRMContentData`. L’objet `DRMContentData` contient l’URL du serveur de licences DRM Primetime qui peut fournir la licence et décrit si l’authentification de l’utilisateur est requise. Avec ces informations, vous pouvez appeler la méthode `DRMManager` `loadVoucher()` pour obtenir et mettre en cache la licence. Le flux de travail des licences de pré-chargement est décrit plus en détail dans *licences de Pré-chargement pour la lecture hors ligne*.

**Gestion des sessions**

Vous pouvez également utiliser `DRMManager` pour authentifier l’utilisateur sur un serveur de licences DRM Primetime et pour gérer les sessions persistantes. Appelez la méthode `DRMManager` `authenticate()` pour établir une session avec le serveur de licences DRM Primetime. Une fois l&#39;authentification terminée, `DRMManager` distribue un objet `DRMAuthenticationCompleteEvent`. Cet objet contient un jeton de session. Vous pouvez enregistrer ce jeton pour établir des sessions futures afin que l’utilisateur n’ait pas à fournir ses informations d’identification de compte. Transmettez le jeton à la méthode `setAuthenticationToken()` pour établir une nouvelle session authentifiée. (Les paramètres du serveur qui a généré le jeton déterminent l’expiration du jeton et d’autres attributs).

## Gestion des Événements DRMStatus {#handling-drmstatus-events}

`DRMManager` distribue un objet `DRMStatusEvent` après un appel à la méthode `loadVoucher()` réussi. Si une licence est obtenue, la propriété detail de l’objet événement a la valeur : `DRM.voucherObtained` et la propriété voucher contient l&#39;objet `DRMVoucher`. Si une licence n’est pas obtenue, la propriété detail a toujours la valeur : `DRM.voucherObtained`; toutefois, la propriété voucher est nulle. Une licence ne peut pas être obtenue si, par exemple, vous utilisez `LoadVoucherSetting` de `localOnly` et qu&#39;il n&#39;existe pas de licence mise en cache localement. Si l&#39;appel `loadVoucher()` ne se termine pas correctement, peut-être en raison d&#39;une erreur d&#39;authentification ou de communication, `DRMManager` envoie à la place un objet `DRMErrorEvent` ou `DRMAuthenticationErrorEvent`.

## Gestion des Événements DRMAuthenticationComplete{#handling-drmauthenticationcomplete-events}

`DRMManager` distribue un objet `DRMAuthenticationCompleteEvent` lorsqu&#39;un utilisateur est authentifié par un appel à la méthode `authenticate()`. L&#39;objet `DRMAuthenticationCompleteEvent` contient un jeton réutilisable qui peut être utilisé pour conserver l&#39;authentification de l&#39;utilisateur au cours des sessions d&#39;application. Transmettez ce jeton à la méthode `DRMManager` `setAuthenticationToken()` pour rétablir la session. (Le créateur de jetons définit des attributs de jeton tels que l’expiration. Adobe ne fournit pas d’API pour examiner les attributs de jeton.)

## Gestion des événements DRMAuthenticationError{#handling-drmauthenticationerror-events}

`DRMManager` distribue un objet `DRMAuthenticationErrorEvent` lorsqu&#39;un utilisateur ne peut pas être authentifié par un appel aux méthodes `authenticate()` ou `setAuthenticationToken()`.