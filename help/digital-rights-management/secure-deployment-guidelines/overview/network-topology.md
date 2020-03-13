---
seo-title: Présentation de la topologie du réseau
title: Présentation de la topologie du réseau
uuid: b8b072dc-8dc0-46ba-bb01-1e9b58af2681
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Présentation {#network-topology-overview}

Après avoir déployé Adobe Primetime DRM, vous devez conserver la sécurité du serveur de production DRM Primetime.

>[!NOTE]
>
>Primetime DRM était auparavant connu sous le nom d’Adobe Access, et auparavant, Flash Access.

Vous pouvez utiliser un proxy ** inverse pour vous assurer que différents ensembles d’URL pour les applications Web DRM Primetime sont accessibles aux utilisateurs externes et internes. *Le proxy* inverse est plus sécurisé que de permettre aux utilisateurs de se connecter directement au serveur d’applications sur lequel le DRM Primetime s’exécute. Cette configuration exécute toutes les requêtes HTTP pour le serveur d’applications qui exécute le DRM Primetime. Les utilisateurs peuvent accéder uniquement au proxy inverse et uniquement aux connexions URL prises en charge par le proxy inverse.

<!--<a id="fig_8083A8C794B646CD87985EC891B60663"></a>-->

![](assets/AdobeAccess_4_SecureDeployment.png)