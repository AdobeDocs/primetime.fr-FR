---
title: Accès à l'Adobe Pass et aux Adobes
description: Accès à l'Adobe Pass et aux Adobes
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---


# Accès à l&#39;Adobe Pass et à l&#39;Adobe {#adobe-pass-and-adobe-access}

Adobe Pass ( [](https://www.adobe.com/products/adobepass/)) fournit l’authentification et l’autorisation des utilisateurs/périphériques à plusieurs fournisseurs de contenu. L&#39;utilisateur doit disposer d&#39;une télévision par câble ou d&#39;un abonnement TV par satellite valide.

<!--<a id="fig_cln_bc2_44"></a>-->

![](assets/AdobePass_web.png)

Adobe Pass peut être utilisé avec Adobe Access pour protéger le contenu multimédia. Dans ce scénario, le lecteur vidéo (SWF) peut charger un autre fichier SWF appelé *Access Enabler*, qui est hébergé par Adobe Systems. Le *Access Enabler* est utilisé pour se connecter au service Adobe Pass et faciliter l&#39;intégration de l&#39;authentification unique SAML avec les systèmes de fournisseurs d&#39;identité de MVPD (Multichannel Video Programming Distributor). Cela implique de rediriger brièvement le navigateur de l’utilisateur vers la page de connexion de la MVPD, puis de conserver un jeton AuthN et de revenir finalement au site Web de contenu avec une session AuthN mise en cache.

L&#39;outil *Access Enabler* peut alors faciliter les autorisations d&#39;arrière-plan entre le service Adobe Pass et la MVPD. La DPSC maintient la logique opérationnelle et détermine le contenu auquel l&#39;utilisateur a droit. Les droits sont conservés dans un jeton AuthZ supplémentaire pour cette ressource de contenu et sont renvoyés au client.

Les jetons d&#39;authentification et d&#39;autorisation sont signés à l&#39;aide de l&#39;identifiant unique et de la clé privée du client Adobe Access afin d&#39;éviter toute falsification ou usurpation de données. Ce jeton est accessible uniquement via l&#39;*Access Enabler*.

Le lecteur vidéo peut déclencher le processus en appelant `getAuthorization` sur le *Access Enabler*. Lorsque des jetons AuthN/AuthZ valides sont présents, le *AccessEnabler* émet un rappel au lecteur vidéo qui inclut un jeton multimédia de courte durée pour lire le contenu vidéo.

Adobe Pass fournit une bibliothèque Java de validation des jetons de médias qui peut être déployée sur un serveur. Lors de l&#39;utilisation du serveur Flass Access pour la protection du contenu, vous pouvez intégrer le validateur de jeton multimédia à un module externe côté serveur Adobe Access pour émettre automatiquement une licence générique après avoir validé le jeton multimédia. Le contenu est ensuite diffusé en continu des serveurs CDN vers le client. Pour acquérir une licence de contenu, le jeton multimédia de courte durée peut être envoyé au serveur d’accès à l’Adobe, où la validité du jeton est vérifiée et une licence peut être émise.

Le jeton AuthN de longue durée est généralement utilisé par l&#39;*Access Enabler* dans tous les développeurs de contenu pour représenter l&#39;AuthN de cet abonné MVPD. En outre, l&#39;Adobe Access Server et le Vérificateur de jeton peuvent être exploités par le CDN ou un prestataire pour le compte du fournisseur de contenu.
