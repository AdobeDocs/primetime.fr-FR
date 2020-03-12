---
description: 'Lorsqu’un utilisateur acquiert un fichier de contenu protégé d’un site Web ou d’un CDN, il doit également acquérir une licence contenant une clé pour déchiffrer la vidéo avant de pouvoir la lire. Les étapes suivantes illustrent un flux de travail commun sur la manière dont un ordinateur exécutant Flash Player ou Adobe AIR accède au contenu protégé. '
seo-description: 'Lorsqu’un utilisateur acquiert un fichier de contenu protégé d’un site Web ou d’un CDN, il doit également acquérir une licence contenant une clé pour déchiffrer la vidéo avant de pouvoir la lire. Les étapes suivantes illustrent un flux de travail commun sur la manière dont un ordinateur exécutant Flash Player ou Adobe AIR accède au contenu protégé. '
seo-title: Acquisition de contenu
title: Acquisition de contenu
uuid: 80253746-bc31-43f0-b28b-7a1aa7fe34a7
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Acquisition de contenu{#content-acquisition}

Lorsqu’un utilisateur acquiert un fichier de contenu protégé d’un site Web ou d’un CDN, il doit également acquérir une licence contenant une clé pour déchiffrer la vidéo avant de pouvoir la lire. Les étapes suivantes illustrent un flux de travail commun sur la manière dont un ordinateur exécutant Flash Player ou Adobe AIR accède au contenu protégé :

1. Le consommateur visite le site Web du détaillant et sélectionne une vidéo à regarder. Le client tente de télécharger ou de diffuser en continu la vidéo protégée sur son ordinateur à l’aide de Flash Player ou d’une application Adobe AIR.

   S’il s’agit de la première fois que le client tente d’accéder à un contenu protégé à l’aide de cet ordinateur spécifique, le runtime de Flash Player ou d’Adobe AIR doit d’abord être individualisé, comme décrit à l’étape 2. Si le client d’exécution a déjà été individualisé, le processus d’acquisition d’une licence se déroule comme décrit à l’étape 3.

1. Le client d’exécution Flash Player ou Adobe AIR acquiert un certificat numérique unique (appelé certificat *de* machine) à partir d’un serveur hébergé par Adobe.

   Ce processus d’attribution d’un certificat unique est appelé *individualisation*. L’individualisation identifie de manière unique l’ordinateur et le runtime Flash Player ou Adobe AIR utilisé pour lire le contenu.

   Le processus d’individualisation permet de lier les licences téléchargées à un ordinateur spécifique sur lequel le client est installé. Chaque ordinateur se voit attribuer des informations d’identification d’ordinateur uniques (clé privée de l’ordinateur et certificat de l’ordinateur). Si un client spécifique est compromis, il peut être révoqué et interdit d’acquérir des licences pour le nouveau contenu.

1. Le client analyse le contenu protégé lorsqu’il commence à télécharger ou à diffuser en continu sur l’ordinateur du consommateur et extrait l’URL du serveur de licences du détaillant à partir des métadonnées DRM Primetime intégrées au fichier.

   Les métadonnées DRM Primetime sont généralement distinctes du contenu, par exemple incorporées dans un fichier manifeste associé ou sous la forme d’un objet blob binaire, mais elles peuvent également être intégrées dans le fichier de contenu. Le client contacte le serveur de licences à l’URL spécifiée et acquiert une licence (comme décrit à l’étape 4 ci-dessous).
1. Le client acquiert une licence auprès du serveur de licences du détaillant.

   Lors de l’acquisition de la licence, le client envoie des informations identifiant le contenu demandé (les métadonnées *DRM* Primetime) et le certificat de la machine (identifiant l’ordinateur du consommateur) au serveur de licences du détaillant. La demande de licence envoyée au serveur est chiffrée à l’aide de la clé publique Transport, qui est également incluse dans les métadonnées DRM Primetime.

   Le serveur de licences — qui peuvent être intégrées à l&#39;infrastructure de facturation et d&#39;authentification du détaillant — peut effectuer une vérification des règles de fonctionnement afin de vérifier que l’utilisateur est autorisé à  le contenu demandé. Si les règles de fonctionnement l’autorisent, le serveur de licences délivre une licence contenant la clé de chiffrement du contenu afin de déchiffrer le contenu et les règles d’utilisation associées au compte de cet utilisateur. Pour traiter une demande de licence, le serveur de licences déchiffre la demande à l’aide de sa clé privée Transport. Le CEK dans les métadonnées est déchiffré à l’aide de la clé privée du serveur de licences et re-chiffré pour lier la licence au périphérique qui effectue la demande. La licence est signée à l’aide de la clé privée du serveur de licences. La réponse de licence est signée à l’aide de la clé privée Transport et chiffrée avant d’être renvoyée au client.

   Si la licence l’autorise, le client stocke la licence pour activer l’accès ** hors ligne à la licence. La mise en cache de la licence permet au consommateur de  contenu protégé sans avoir à reprendre une licence chaque fois qu’il souhaite  contenu.

1. Une fois que le client d’exécution Flash Player ou Adobe AIR dispose d’une licence, le client extrait le CEK de la licence et le consommateur peut  le contenu auquel il est autorisé à accéder.

   <!--<a id="fig_s43_gc2_44"></a>-->

   ![](assets/FMRMS_fig01_web.png)

   L’exemple précédent ne montre qu’un seul processus possible. Vous pouvez également utiliser un flux de travail avec un téléchargement proactif de contenu lorsque l’acquisition de licence se produit bien plus tard. Une autre option consiste à implémenter un processus de pré-commande dans lequel l’acquisition de licence survient avant l’accès au contenu.

