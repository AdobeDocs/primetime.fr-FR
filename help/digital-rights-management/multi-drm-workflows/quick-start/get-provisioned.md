---
description: Pour commencer à utiliser Primetime DRM Cloud, proposé par ExpressPlay, vous devez configurer des comptes Cert d'Adobe et ExpressPlay avec l'aide de votre représentant d'Adobe.
title: Obtenir des privilèges d'accès (comptes, etc.)
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---


# Obtenir l&#39;approvisionnement (comptes, etc.) {#get-provisioned-accounts-etc}

Pour commencer à utiliser Primetime DRM Cloud, proposé par ExpressPlay, vous devez configurer des comptes Cert d&#39;Adobe et ExpressPlay avec l&#39;aide de votre représentant d&#39;Adobe.

1. Contactez votre représentant Adobe et demandez les comptes Adobe Cert et ExpressPlay dont vous aurez besoin pour mettre en oeuvre Multi-DRM avec TVSDK.

       Indiquez à votre représentant d’Adobe l’adresse électronique que vous utiliserez comme point de contact. Adobe crée ensuite deux comptes pour vous : 
   
   * ***Compte***  du portail de certificats - ( <span></span>https://certportal.primetime.adobe.com) : L&#39; *équipe de gestion de l&#39;inscription aux certificats DRM Accès* Adobe / Primetime envoie un courriel aux adresses que vous lui avez fournies. Le courrier électronique contient l’URL du portail de certificats d’Adobe, ainsi qu’un lien vers la documentation sur l’inscription des certificats d’Adobe (les derniers documents sont disponibles ici : [Guide d&#39;inscription de certificat](../../../digital-rights-management/certificate-enrollment-guide/about-certs.md)).

   * ***Compte***  ExpressPlay - Adobe vous envoie un courrier électronique contenant un lien que vous utilisez pour vous inscrire à votre compte d’administrateur ExpressPlay.

1. Connectez-vous au portail de certificats d’Adobe à l’aide de votre Adobe ID (utilisez la même adresse électronique que celle que vous avez fournie à votre représentant d’Adobe). Si vous n’avez pas encore d’Adobe ID, vous pouvez rapidement en créer un en suivant le lien *Obtenir un Adobe ID* à partir du portail cert :

   <!--<a id="fig_mst_gtj_wv"></a>-->

   ![](assets/cert_portal_sign-in-page-web.png)

1. Sur le portail des certificats d’Adobe, demandez un certificat *Trial*.

   Pour l’essai Multi-DRM, un certificat d’essai unique couvrira tous les aspects de la protection du contenu : emballage, licence et transport. Vous devrez fournir votre propre [CSR](../../../digital-rights-management/certificate-enrollment-guide/request-certs/gen-cert-signing-req.md) pour faire une demande de certificat :
   <!--<a id="fig_op1_xwj_wv"></a>-->

   ![](assets/cert_portal_trial_request-web.png)

   L&#39;Adobe vous enverra un courriel indiquant l&#39;acceptation ou le rejet de votre demande de certificat. Vous pouvez afficher l’état de vos demandes de certificat dans l’onglet *Historique des demandes* du portail de certificats :
   <!--<a id="fig_gkl_myj_wv"></a>-->

   ![](assets/cert_portal_request_history-web.png)

1. Créez votre compte d’administrateur ExpressPlay.

   Suivez le lien vers ExpressPlay que vous a fourni cet Adobe. Cette opération ouvre la page *Créer un compte* sur ExpressPlay. Renseignez les informations requises et envoyez le formulaire. Vous recevrez un courriel de `operations@expressplay.com` contenant un lien d&#39;activation valable pour une semaine. Après avoir activé, configurez votre service ExpressPlay :
   <!--<a id="fig_cjl_ztk_wv"></a>-->

   ![](assets/expressplay_create_service-web.png)

   Une fois votre service créé, votre propre page d’administration s’affiche. Outre certains champs de suivi des activités, vous verrez vos authentificateurs de clients Production et Test ** (clés d&#39;API) et vos URL de service Production et Test :

   <!--<a id="fig_c5h_xdl_wv"></a>-->

   ![](assets/expressplay_admin_dashboard_2-web.png) ![](assets/expressplay_admin_dashboard-web.png)

1. Si vous utilisez FairPlay, d’autres étapes sont nécessaires (sur le site des développeurs Apple) pour configurer ExpressPlay. Voir [Activer le service ExpressPlay pour FairPlay](../../multi-drm-workflows/p-l-and-p/fairplay-workflow.md#enable-expressplay-service-for-fairplay) pour obtenir des instructions.
