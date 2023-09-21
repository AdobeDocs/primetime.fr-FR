---
title: Authentification Adobe Primetime et Adobe Primetime DRM
description: Authentification Adobe Primetime et Adobe Primetime DRM
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# Authentification Adobe Primetime et Adobe Primetime DRM {#adobe-primetime-authentication-and-adobe-primetime-drm}

Authentification Adobe Primetime ( [https://www.adobe.com/products/adobepass/](https://www.adobe.com/products/adobepass/)) permet l’authentification et l’autorisation des utilisateurs et des appareils sur plusieurs fournisseurs de contenu. L&#39;utilisateur doit disposer d&#39;un abonnement TV par câble ou satellite valide.

<!--<a id="fig_cln_bc2_44"></a>-->

![](assets/AdobePass_web.png)

L’authentification Adobe Primetime peut être utilisée avec Adobe Primetime DRM pour protéger le contenu multimédia. Dans ce scénario, le lecteur vidéo (SWF) peut charger un autre SWF appelé *Accéder à l’activateur*, qui est hébergée par Adobe Systems. La variable *Accéder à l’activateur* est utilisé pour se connecter au service d’authentification Adobe Primetime et faciliter l’intégration de l’authentification unique SAML aux systèmes de fournisseur d’identité de MVPD (Multichannel Video Programming Distributor). Cela implique de rediriger brièvement le navigateur de l’utilisateur vers la page de connexion MVPD, puis de conserver un jeton AuthN et de revenir enfin au site web de contenu avec une session AuthN mise en cache.

La variable *Accéder à l’activateur* peut alors faciliter les autorisations principales entre le service d’authentification Adobe Primetime et le MVPD. Le MVPD conserve la logique commerciale et détermine le contenu auquel l’utilisateur a droit. Le droit est conservé dans un jeton AuthZ supplémentaire pour cette ressource de contenu et est renvoyé au client.

Les jetons d’authentification et d’autorisation sont signés à l’aide de l’identifiant unique et de la clé privée du client DRM Primetime afin d’éviter toute falsification ou usurpation de nom. Ce jeton est accessible uniquement via le *Accéder à l’activateur*.

Le lecteur vidéo peut déclencher le processus en appelant `getAuthorization` sur le *Accéder à l’activateur*. En cas de présence de jetons AuthN/AuthZ valides, la variable *AccessEnabler* émet un rappel au lecteur vidéo qui inclura un jeton multimédia de courte durée pour lire le contenu vidéo.

L’authentification Adobe Primetime fournit une bibliothèque Java de validation de jeton multimédia qui peut être déployée sur un serveur. Lors de l’utilisation du serveur DRM Primetime pour la protection du contenu, vous pouvez intégrer le validateur de jeton multimédia à un module externe côté serveur Primetime DRM afin d’émettre automatiquement une licence générique après avoir validé le jeton multimédia avec succès. Le contenu est ensuite diffusé en continu à partir des serveurs CDN vers le client. Pour acquérir une licence de contenu, le jeton multimédia de courte durée peut être soumis au serveur Primetime DRM, où la validité du jeton est vérifiée et une licence peut être émise.

Le jeton AuthN de longue durée est généralement utilisé par la variable *Accéder à l’activateur* sur tous les développeurs de contenu pour représenter l’AuthN de cet abonné MVPD. En outre, le serveur DRM Primetime et le vérificateur de jeton peuvent être exploités par le CDN ou un fournisseur de services pour le compte du fournisseur de contenu.
