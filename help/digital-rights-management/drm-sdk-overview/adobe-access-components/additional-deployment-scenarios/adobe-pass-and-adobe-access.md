---
title: Authentification Adobe Primetime et Adobe Primetime DRM
description: Authentification Adobe Primetime et Adobe Primetime DRM
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---


# Authentification Adobe Primetime et Adobe Primetime DRM {#adobe-primetime-authentication-and-adobe-primetime-drm}

L’authentification Adobe Primetime ( [https://www.adobe.com/products/adobepass/](https://www.adobe.com/products/adobepass/)) permet l’authentification et l’autorisation des utilisateurs/périphériques sur plusieurs fournisseurs de contenu. L&#39;utilisateur doit disposer d&#39;une télévision par câble ou d&#39;un abonnement TV par satellite valide.

<!--<a id="fig_cln_bc2_44"></a>-->

![](assets/AdobePass_web.png)

L’authentification Adobe Primetime peut être utilisée avec le DRM Adobe Primetime pour protéger le contenu multimédia. Dans ce scénario, le lecteur vidéo (SWF) peut charger un autre fichier SWF appelé *Access Enabler*, qui est hébergé par Adobe Systems. L&#39;outil *Access Enabler* permet de se connecter au service d&#39;authentification Adobe Primetime et de faciliter l&#39;intégration de l&#39;authentification unique SAML aux systèmes de fournisseurs d&#39;identité de MVPD (Multichannel Video Programming Distributor). Cela implique de rediriger brièvement le navigateur de l’utilisateur vers la page de connexion de la MVPD, puis de conserver un jeton AuthN et de revenir finalement au site Web de contenu avec une session AuthN mise en cache.

Le *Access Enabler* peut alors faciliter les autorisations d&#39;arrière-plan entre le service d&#39;authentification Adobe Primetime et la MVPD. La DPSC maintient la logique opérationnelle et détermine le contenu auquel l&#39;utilisateur a droit. Les droits sont conservés dans un jeton AuthZ supplémentaire pour cette ressource de contenu et sont renvoyés au client.

Les jetons d’authentification et d’autorisation sont signés à l’aide de l’identifiant unique et de la clé privée du client DRM Primetime afin d’éviter toute manipulation ou usurpation de données. Ce jeton est accessible uniquement via l&#39;*Access Enabler*.

Le lecteur vidéo peut déclencher le processus en appelant `getAuthorization` sur le *Access Enabler*. Lorsque des jetons AuthN/AuthZ valides sont présents, le *AccessEnabler* émet un rappel au lecteur vidéo qui inclut un jeton multimédia de courte durée pour lire le contenu vidéo.

L’authentification Adobe Primetime fournit une bibliothèque Java de validation de jeton multimédia qui peut être déployée sur un serveur. Lors de l’utilisation du serveur DRM Primetime pour la protection du contenu, vous pouvez intégrer le validateur de jeton multimédia à un module externe côté serveur DRM Primetime pour émettre automatiquement une licence générique après avoir validé le jeton multimédia. Le contenu est ensuite diffusé en continu des serveurs CDN vers le client. Pour acquérir une licence de contenu, le jeton multimédia de courte durée peut être envoyé au serveur DRM Primetime, où la validité du jeton est vérifiée et une licence peut être émise.

Le jeton AuthN de longue durée est généralement utilisé par l&#39;*Access Enabler* dans tous les développeurs de contenu pour représenter l&#39;AuthN de cet abonné MVPD. En outre, le serveur DRM Primetime et le vérificateur de jeton peuvent être exploités par le CDN ou un prestataire pour le compte du fournisseur de contenu.