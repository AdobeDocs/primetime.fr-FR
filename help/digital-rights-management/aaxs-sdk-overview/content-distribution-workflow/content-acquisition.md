---
title: Acquisition de contenu
description: Acquisition de contenu
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---

# Acquisition de contenu {#content-acquisition}

Lorsqu’un client acquiert un fichier de contenu protégé sur un site web ou un réseau de diffusion de contenu, il doit également acquérir une licence contenant une clé pour déchiffrer la vidéo avant de pouvoir la lire. Les étapes suivantes illustrent un workflow courant permettant d’accéder à un contenu protégé par un ordinateur exécutant un Flash Player ou Adobe AIR :

1. Le consommateur se rend sur le site web du détaillant et sélectionne une vidéo à regarder. Le client tente de télécharger ou de diffuser en continu la vidéo protégée sur son ordinateur à l’aide d’une application Flash Player ou Adobe AIR.

   S’il s’agit de la première fois que le client tente d’accéder à du contenu protégé à l’aide de cet ordinateur spécifique, le Flash Player ou l’exécution Adobe AIR doit d’abord être individualisé, comme décrit à l’étape 2. Si le client d’exécution a déjà été personnalisé, le processus d’acquisition d’une licence se produit comme décrit à l’étape 3.

1. Le client d’exécution Flash Player ou Adobe AIR acquiert un certificat numérique unique (appelé *certificat de la machine*) à partir d’un serveur hébergé par un Adobe.

   Ce processus d’attribution d’un certificat unique est appelé *individualisation*. L’individualisation identifie de manière unique l’ordinateur et le runtime Flash Player ou Adobe AIR utilisé pour lire le contenu.

   Le processus d’individualisation permet aux licences téléchargées d’être liées à un ordinateur spécifique sur lequel le client est installé. Chaque ordinateur reçoit des informations d’identification de machine uniques (clé privée de machine et certificat de machine). Si un client spécifique doit être compromis, il peut être révoqué et interdit d’acquérir des licences pour le nouveau contenu.

1. Le client analyse le contenu protégé au fur et à mesure qu’il commence à télécharger ou à diffuser sur l’ordinateur du consommateur, et extrait l’URL du serveur de licences du détaillant des métadonnées DRM incorporées dans le fichier.

   Les métadonnées DRM sont généralement distinctes du contenu, telles qu’elles sont incorporées dans un fichier de manifeste qui les accompagne ou sous la forme d’un objet blob binaire, mais elles peuvent également être incorporées dans le fichier de contenu. Le client contacte le serveur de licences à l’URL spécifiée et acquiert une licence (comme décrit ci-dessous à l’étape 4).
1. Le client acquiert une licence auprès du serveur de licences du détaillant.

   Lors de l’acquisition de la licence, le client envoie des informations identifiant le contenu demandé (le *Métadonnées DRM*) et le certificat de la machine (identifiant l’ordinateur du consommateur) au serveur de licences du détaillant. La demande de licence envoyée au serveur est chiffrée à l’aide de la clé publique Transport, qui est également incluse dans les métadonnées DRM.

   Le serveur de licences, qui peut être intégré à l’infrastructure de facturation et d’authentification du détaillant, peut effectuer un contrôle des règles de fonctionnement afin de vérifier que l’utilisateur est autorisé à afficher le contenu demandé. Si les règles de fonctionnement le permettent, le serveur de licences émet une licence contenant la clé de chiffrement du contenu pour déchiffrer le contenu et les règles d’utilisation associées au compte de cet utilisateur. Pour traiter une demande de licence, le serveur de licences décrypte la demande à l’aide de sa clé privée de transport. Le CEK des métadonnées est déchiffré à l’aide de la clé privée du serveur de licences et re-chiffré pour lier la licence à l’appareil qui émet la demande. La licence est signée à l’aide de la clé privée du serveur de licences. La réponse de licence est signée à l’aide de la clé privée Transport et chiffrée avant d’être renvoyée au client.

   Si la licence l’autorise, le client stocke la licence pour activer *accès hors ligne* à la licence . La mise en cache de licence permet au consommateur d’afficher du contenu protégé sans acquérir à nouveau une licence chaque fois qu’il souhaite afficher du contenu.

1. Une fois que le client d’exécution Flash Player ou Adobe AIR dispose d’une licence, le client extrait le CEK de la licence, et le consommateur peut visualiser le contenu auquel il est autorisé à accéder.

   <!--<a id="fig_s43_gc2_44"></a>-->

   ![](assets/FMRMS_fig01_web.png)

   L’exemple précédent ne présente qu’un seul workflow possible. Vous pouvez également utiliser un workflow avec un téléchargement proactif de contenu où l’acquisition de licence se produit beaucoup plus tard. Une autre option consiste à mettre en oeuvre un workflow de pré-commande dans lequel l’acquisition de licence se produit avant l’accès au contenu.
