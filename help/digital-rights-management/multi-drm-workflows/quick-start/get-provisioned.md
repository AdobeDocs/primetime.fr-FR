---
description: Pour commencer à utiliser Primetime DRM Cloud, optimisé par ExpressPlay, vous devez configurer des comptes Adobe Cert et ExpressPlay avec l’aide de votre représentant d’Adobe.
title: Obtention de la configuration (comptes, etc.)
exl-id: 2543d997-3495-4545-9395-072c07431aba
source-git-commit: a0917e128862184ce18050792c2ee2ac265050d2
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# Obtention de la configuration (comptes, etc.) {#get-provisioned-accounts-etc}

Pour commencer à utiliser Primetime DRM Cloud, optimisé par ExpressPlay, vous devez configurer des comptes Adobe Cert et ExpressPlay avec l’aide de votre représentant d’Adobe.

1. Contactez votre représentant d’Adobe et demandez les comptes Adobe Cert et ExpressPlay dont vous aurez besoin pour mettre en oeuvre Multi-DRM avec TVSDK.

   Indiquez à votre représentant d’Adobe l’adresse électronique que vous utiliserez comme point de contact. Adobe crée alors deux comptes pour vous :

   * ***Compte du portail de certificats*** - ( https://certportal.primetime.adobe.com) : Le *Équipe de gestion de l’inscription des certificats DRM à l’accès aux Adobes/Primetime* envoie un courrier électronique aux adresses que vous leur avez fournies. Le courrier électronique comprend l’URL du portail de certificat d’Adobe, ainsi qu’un lien vers la documentation sur l’inscription au certificat d’Adobe (les derniers documents sont disponibles ici : [Guide d’inscription au certificat](../../../digital-rights-management/certificate-enrollment-guide/about-certs.md)).

   * ***Compte ExpressPlay*** - Adobe vous envoie un courrier électronique contenant un lien que vous utilisez pour vous enregistrer pour votre compte administrateur ExpressPlay.

1. Connectez-vous au portail Adobe cert à l’aide de votre Adobe ID (utilisez la même adresse électronique que celle que vous avez fournie à votre représentant d’Adobe). Si vous ne disposez pas encore d’Adobe ID, vous pouvez rapidement en créer un en suivant les *Obtention d’une Adobe ID* lien du portail cert :

   <!--<a id="fig_mst_gtj_wv"></a>-->

   ![](assets/cert_portal_sign-in-page-web.png)

1. Sur le portail Adobe cert, demandez un *Évaluation* cert.

   Pour l’évaluation multi-DRM, un seul certificat d’évaluation couvrira tous les aspects de la protection du contenu : emballage, licences et transport. Vous devrez fournir les vôtres. [CSR](../../../digital-rights-management/certificate-enrollment-guide/request-certs/gen-cert-signing-req.md) pour effectuer une demande de certificat :
   <!--<a id="fig_op1_xwj_wv"></a>-->

   ![](assets/cert_portal_trial_request-web.png)

   Adobe vous enverra un email qui indique l’acceptation ou le rejet de votre demande de certificat. Vous pouvez voir l’état de vos demandes de certificat sur le *Historique des requêtes* sur le portail cert :
   <!--<a id="fig_gkl_myj_wv"></a>-->

   ![](assets/cert_portal_request_history-web.png)

1. Créez votre compte d’administrateur ExpressPlay.

   Suivez le lien vers ExpressPlay que cet Adobe vous a fourni. Cela ouvre la fenêtre *Création d’un compte* sur ExpressPlay. Renseignez les informations requises et envoyez le formulaire. Vous recevrez un e-mail de `operations@expressplay.com` contenant un lien d’activation valable pour une semaine. Une fois que vous avez activé, configurez votre service ExpressPlay :
   <!--<a id="fig_cjl_ztk_wv"></a>-->

   ![](assets/expressplay_create_service-web.png)

   Une fois votre service créé, votre propre page d’administration s’affiche. Outre certains champs de suivi des activités, vous verrez vos champs Production et Test . *authentificateurs de clients* (Clés API) et vos URL de service de production et de test :

   <!--<a id="fig_c5h_xdl_wv"></a>-->

   ![](assets/expressplay_admin_dashboard_2-web.png) ![](assets/expressplay_admin_dashboard-web.png)

1. Si vous utilisez FairPlay, d’autres étapes sont nécessaires (sur le site de développement Apple) pour configurer ExpressPlay. Voir [Activer le service ExpressPlay pour FairPlay](../../multi-drm-workflows/p-l-and-p/fairplay-workflow.md#enable-expressplay-service-for-fairplay) pour obtenir des instructions.
