---
seo-title: Utilisation de la présentation de la classe DRMManager
title: Utilisation de la présentation de la classe DRMManager
uuid: 71ce061b-75b6-4ab5-8bbd-cafe7c3e4592
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Utilisation de la classe DRMManager {#using-the-drmmanager-class}

Utilisez la `DRMManager` classe pour gérer les licences et les sessions de serveur de licences DRM Primetime dans les applications.

**Gestion des licences**

Chaque fois qu’un périphérique lit du contenu protégé, le moteur d’exécution obtient et met en cache la licence requise pour  le contenu. Si l’application enregistre le contenu localement et que la licence autorise la lecture hors ligne, l’utilisateur peut le  dans l’application sans connexion réseau. A l’aide `DRMManager`, vous pouvez prémettre en cache la licence. L’application n’a pas besoin d’obtenir la licence nécessaire pour  le contenu. Par exemple, votre application peut télécharger le fichier multimédia, puis obtenir la licence pendant que l’utilisateur est toujours en ligne.

Pour précharger une licence, utilisez un `DRMContentData` objet. L’ `DRMContentData` objet contient l’URL du serveur de licences DRM Primetime qui peut fournir la licence et décrit si l’authentification de l’utilisateur est requise. Avec ces informations, vous pouvez appeler la `DRMManager` méthode `loadVoucher()` pour obtenir et mettre en cache la licence. Le flux de travail relatif aux licences de  est décrit plus en détail dans la section Licences de  *pour la lecture* hors ligne.

**Gestion des sessions**

Vous pouvez également utiliser le `DRMManager` pour authentifier l’utilisateur sur un serveur de licences DRM Primetime et pour gérer les sessions persistantes. Appelez la `DRMManager` méthode `authenticate()` pour établir une session avec le serveur de licences DRM Primetime. Une fois l’authentification terminée, le `DRMManager` répartit un `DRMAuthenticationCompleteEvent` objet. Cet objet contient un jeton de session. Vous pouvez enregistrer ce jeton afin d’établir des sessions futures afin que l’utilisateur n’ait pas à fournir ses informations d’identification de compte. Transmettez le jeton à la `setAuthenticationToken()` méthode pour établir une nouvelle session authentifiée. (Les paramètres du serveur qui a généré le jeton déterminent l’expiration du jeton et d’autres attributs).

## Gestion du DRMStatus {#handling-drmstatus-events}

L’objet `DRMManager` distribue un `DRMStatusEvent` objet une fois qu’un appel à la `loadVoucher()` méthode se termine correctement. Si une licence est obtenue, la propriété detail de l’objet  a la valeur : `DRM.voucherObtained`et la propriété voucher contient l’ `DRMVoucher` objet. Si aucune licence n’est obtenue, la propriété detail a toujours la valeur : `DRM.voucherObtained`; toutefois, la propriété voucher est nulle. Il est impossible d’obtenir une licence si, par exemple, vous utilisez la `LoadVoucherSetting` commande de `localOnly` et qu’il n’existe aucune licence mise en cache localement. Si l’ `loadVoucher()` appel ne se termine pas correctement, peut-être en raison d’une erreur d’authentification ou de communication, alors l’ `DRMManager` objet envoie à la place un `DRMErrorEvent` ou `DRMAuthenticationErrorEvent` .

## Gestion du DRMAuthenticationComplete{#handling-drmauthenticationcomplete-events}

L’objet `DRMManager` distribue un `DRMAuthenticationCompleteEvent` objet lorsqu’un utilisateur est authentifié avec succès par le biais d’un appel à la `authenticate()` méthode. L’ `DRMAuthenticationCompleteEvent` objet contient un jeton réutilisable qui peut être utilisé pour conserver l’authentification de l’utilisateur entre les sessions de l’application. Transmettez ce jeton à la `DRMManager` méthode `setAuthenticationToken()` pour rétablir la session. (L’auteur du jeton définit les attributs du jeton, tels que l’expiration. Adobe ne fournit pas d’API pour examiner les attributs de jeton.)

## Gestion du DRMAuthenticationError{#handling-drmauthenticationerror-events}

Le `DRMManager` système distribue un `DRMAuthenticationErrorEvent` objet lorsqu’un utilisateur ne peut pas être authentifié par un appel aux `authenticate()` méthodes ou `setAuthenticationToken()` .