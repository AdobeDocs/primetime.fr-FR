---
seo-title: Authentification Adobe Primetime et DRM Adobe Primetime
title: Authentification Adobe Primetime et DRM Adobe Primetime
uuid: 44fe3956-efb5-4fc5-97e2-37abb6554322
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5

---


# Authentification Adobe Primetime et DRM Adobe Primetime {#adobe-primetime-authentication-and-adobe-primetime-drm}

L’authentification Adobe Primetime ( [https://www.adobe.com/products/adobepass/](https://www.adobe.com/products/adobepass/)) permet l’authentification et l’autorisation des utilisateurs/périphériques sur plusieurs fournisseurs de contenu. L&#39;utilisateur doit disposer d&#39;une télévision par câble ou d&#39;un abonnement TV par satellite valide.

<!--<a id="fig_cln_bc2_44"></a>-->

![](assets/AdobePass_web.png)

L’authentification Adobe Primetime peut être utilisée avec Adobe Primetime DRM pour protéger le contenu multimédia. Dans ce scénario, le lecteur vidéo (SWF) peut charger un autre fichier SWF appelé *Access Enabler*, qui est hébergé par Adobe Systems. L’ *Access Enabler* permet de se connecter au service d’authentification Adobe Primetime et de faciliter l’intégration de l’authentification unique SAML aux systèmes de fournisseurs d’identité de MVPD (Multichannel Video Programming Distributor). Cela implique de rediriger brièvement le navigateur de l’utilisateur vers la page de connexion de la MVPD, puis de conserver un jeton AuthN et de revenir finalement au site Web de contenu avec une session AuthN mise en cache.

L’ *Access Enabler* peut alors faciliter les autorisations d’arrière-plan entre le service d’authentification Adobe Primetime et le MVPD. La DPSC maintient la logique opérationnelle et détermine le contenu auquel l&#39;utilisateur a droit. Les droits sont conservés dans un jeton AuthZ supplémentaire pour cette ressource de contenu et sont renvoyés au client.

Les jetons d’authentification et d’autorisation sont signés à l’aide de l’identifiant unique et de la clé privée du client DRM Primetime afin d’éviter toute manipulation ou usurpation de données. Ce jeton est accessible uniquement via *Access Enabler*.

Le lecteur vidéo peut déclencher le processus en appelant `getAuthorization` l’ *Access Enabler*. Lorsque des jetons AuthN/AuthZ valides sont présents, *AccessEnabler* envoie un rappel au lecteur vidéo qui inclut un jeton multimédia de courte durée pour lire le contenu vidéo.

L’authentification Adobe Primetime fournit une bibliothèque Java de validation de jetons multimédias qui peut être déployée sur un serveur. Lors de l’utilisation du serveur DRM Primetime pour la protection du contenu, vous pouvez intégrer le validateur de jeton multimédia à un module externe côté serveur DRM Primetime pour émettre automatiquement une licence générique après avoir validé le jeton multimédia. Le contenu est ensuite diffusé en continu des serveurs CDN vers le client. Pour acquérir une licence de contenu, le jeton multimédia de courte durée peut être envoyé au serveur DRM Primetime, où la validité du jeton est vérifiée et une licence peut être émise.

Le jeton AuthN de longue durée est généralement utilisé par l&#39; *Access Enabler* sur tous les développeurs de contenu pour représenter l&#39;AuthN pour cet abonné MVPD. En outre, le serveur DRM Primetime et le vérificateur de jeton peuvent être exploités par le CDN ou un prestataire pour le compte du fournisseur de contenu.