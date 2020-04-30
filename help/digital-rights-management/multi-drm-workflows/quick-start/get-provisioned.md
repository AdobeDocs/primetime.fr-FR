---
description: Pour commencer à utiliser Primetime DRM Cloud, proposé par ExpressPlay, vous devez configurer des comptes Adobe Cert et ExpressPlay avec l’aide de votre représentant Adobe.
seo-description: Pour commencer à utiliser Primetime DRM Cloud, proposé par ExpressPlay, vous devez configurer des comptes Adobe Cert et ExpressPlay avec l’aide de votre représentant Adobe.
seo-title: Obtenir des privilèges d'accès (comptes, etc.)
title: Obtenir des privilèges d'accès (comptes, etc.)
uuid: 51b95676-2121-4d8b-8756-9fd097185a13
translation-type: tm+mt
source-git-commit: 9792aff8586c46aabb5bfb70864cfe98c28e602d

---


# Obtenir des privilèges d&#39;accès (comptes, etc.) {#get-provisioned-accounts-etc}

Pour commencer à utiliser Primetime DRM Cloud, proposé par ExpressPlay, vous devez configurer des comptes Adobe Cert et ExpressPlay avec l’aide de votre représentant Adobe.

1. Contactez votre représentant Adobe et demandez les comptes Adobe Cert et ExpressPlay dont vous aurez besoin pour mettre en oeuvre Multi-DRM avec TVSDK.

       Indiquez à votre représentant Adobe l’adresse électronique que vous utiliserez comme point de contact. Adobe crée ensuite deux comptes pour vous :
   
   * ***Compte*** du portail de certificats - (<span></span>https://certportal.primetime.adobe.com) : L’équipe *de gestion de l’inscription des certificats DRM d’* Adobe Access / Primetime envoie un courrier électronique aux adresses que vous lui avez fournies. Le courrier électronique comprend l’URL du portail de certificats Adobe, ainsi qu’un lien vers la documentation sur l’inscription aux certificats d’Adobe (les derniers documents sont disponibles ici : [Guide](../../../digital-rights-management/certificate-enrollment-guide/about-certs.md)d&#39;inscription de certificat).

   * ***Compte*** ExpressPlay - Adobe vous envoie un courrier électronique contenant un lien que vous utilisez pour vous inscrire à votre compte d’administrateur ExpressPlay.

1. Connectez-vous au portail de certificats Adobe à l’aide de votre Adobe ID (utilisez la même adresse électronique que celle que vous avez fournie à votre représentant Adobe). Si vous n’avez pas encore d’Adobe ID, vous pouvez rapidement en créer un en suivant le lien *Obtenir un Adobe ID* à partir du portail cert :

   <!--<a id="fig_mst_gtj_wv"></a>-->

   ![](assets/cert_portal_sign-in-page-web.png)

1. Sur le portail des certificats Adobe, demandez un certificat *d’évaluation* .

   Pour l’essai Multi-DRM, un certificat d’essai unique couvrira tous les aspects de la protection du contenu : emballage, licence et transport. Vous devrez fournir votre propre [RSE](../../../digital-rights-management/certificate-enrollment-guide/request-certs/gen-cert-signing-req.md) pour faire une demande de certificat :
   <!--<a id="fig_op1_xwj_wv"></a>-->

   ![](assets/cert_portal_trial_request-web.png)

   Adobe vous enverra un courrier électronique indiquant l’acceptation ou le rejet de votre demande de certificat. Vous pouvez afficher l’état de vos demandes de certificat dans l’onglet Historique *des* requêtes du portail de certificats :
   <!--<a id="fig_gkl_myj_wv"></a>-->

   ![](assets/cert_portal_request_history-web.png)

1. Créez votre compte d’administrateur ExpressPlay.

   Suivez le lien vers ExpressPlay fourni par Adobe. La page *Créer un compte* s’ouvre alors sur ExpressPlay. Renseignez les informations requises et envoyez le formulaire. Vous recevrez un e-mail `operations@expressplay.com` contenant un lien d&#39;activation valable pour une semaine. Après avoir activé, configurez votre service ExpressPlay :
   <!--<a id="fig_cjl_ztk_wv"></a>-->

   ![](assets/expressplay_create_service-web.png)

   Une fois votre service créé, votre propre page d’administration s’affiche. Outre certains champs de suivi des activités, vous verrez vos authentificateurs *de* clients Production et Test (clés d’API) et vos URL de service Production et Test :

   <!--<a id="fig_c5h_xdl_wv"></a>-->

   ![](assets/expressplay_admin_dashboard_2-web.png) ![](assets/expressplay_admin_dashboard-web.png)

1. Si vous utilisez FairPlay, d’autres étapes sont nécessaires (sur le site des développeurs Apple) pour configurer ExpressPlay. Voir [Activer le service ExpressPlay pour FairPlay](../../multi-drm-workflows/p-l-and-p/fairplay-workflow.md#enable-expressplay-service-for-fairplay) pour obtenir des instructions.
