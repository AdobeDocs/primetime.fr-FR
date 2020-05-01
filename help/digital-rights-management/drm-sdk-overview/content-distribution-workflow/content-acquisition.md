---
description: 'Lorsqu’un utilisateur acquiert un fichier de contenu protégé d’un site Web ou d’un réseau de diffusion de contenu, il doit également acquérir une licence qui contient une clé pour déchiffrer la vidéo avant de pouvoir la lire. Les étapes suivantes illustrent un processus courant d’accès au contenu protégé par un ordinateur exécutant Flash Player ou Adobe AIR. '
seo-description: 'Lorsqu’un utilisateur acquiert un fichier de contenu protégé d’un site Web ou d’un réseau de diffusion de contenu, il doit également acquérir une licence qui contient une clé pour déchiffrer la vidéo avant de pouvoir la lire. Les étapes suivantes illustrent un processus courant d’accès au contenu protégé par un ordinateur exécutant Flash Player ou Adobe AIR. '
seo-title: Acquisition de contenu
title: Acquisition de contenu
uuid: 80253746-bc31-43f0-b28b-7a1aa7fe34a7
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Acquisition de contenu{#content-acquisition}

Lorsqu’un utilisateur acquiert un fichier de contenu protégé d’un site Web ou d’un réseau de diffusion de contenu, il doit également acquérir une licence qui contient une clé pour déchiffrer la vidéo avant de pouvoir la lire. Les étapes suivantes illustrent un processus courant d’accès au contenu protégé par un ordinateur exécutant Flash Player ou Adobe AIR :

1. Le consommateur consulte le site Web du détaillant et sélectionne une vidéo à regarder. Le client tente de télécharger ou de diffuser en continu la vidéo protégée sur son ordinateur à l’aide de Flash Player ou d’une application Adobe AIR.

   Si c’est la première fois que le client tente d’accéder à un contenu protégé à l’aide de cet ordinateur spécifique, le runtime de Flash Player ou d’Adobe AIR doit d’abord être personnalisé comme décrit à l’étape 2. Si le client d’exécution a déjà été individualisé, le processus d’acquisition d’une licence se produit comme décrit à l’étape 3.

1. Le client d’exécution Flash Player ou Adobe AIR acquiert un certificat numérique unique (appelé certificat ** machine) auprès d’un serveur hébergé par Adobe.

   Ce processus d&#39;attribution d&#39;un certificat unique est appelé *individualisation*. L’individualisation identifie de manière unique à la fois l’ordinateur et le runtime Flash Player ou Adobe AIR utilisé pour lire le contenu.

   Le processus d’individualisation permet de lier les licences téléchargées à un ordinateur spécifique sur lequel le client est installé. Chaque ordinateur reçoit des informations d’identification d’ordinateur uniques (clé privée de l’ordinateur et certificat de l’ordinateur). Si un client spécifique doit être compromis, il peut être révoqué et interdit d’acquérir des licences pour le nouveau contenu.

1. Le client analyse le contenu protégé lorsqu’il commence à télécharger ou à diffuser en continu sur l’ordinateur du consommateur et extrait l’URL du serveur de licences du détaillant à partir des métadonnées DRM Primetime incorporées dans le fichier.

   En règle générale, les métadonnées DRM de Primetime sont distinctes du contenu, par exemple incorporées dans un fichier manifeste ou sous forme de blob binaire, mais peuvent également être incorporées dans le fichier de contenu. Le client contacte le serveur de licences à l’URL spécifiée et acquiert une licence (comme décrit ci-dessous à l’étape 4).
1. Le client acquiert une licence auprès du serveur de licences du détaillant.

   Pendant l&#39;acquisition de la licence, le client envoie des informations identifiant le contenu demandé (les métadonnées *DRM* Primetime) et le certificat de l&#39;ordinateur (identifiant l&#39;ordinateur du consommateur) au serveur de licences du détaillant. La demande de licence envoyée au serveur est chiffrée à l’aide de la clé publique Transport, qui est également incluse dans les métadonnées DRM Primetime.

   Le serveur de licences, qui peut être intégré à l&#39;infrastructure de facturation et d&#39;authentification du détaillant, peut effectuer un contrôle des règles de fonctionnement pour vérifier que l&#39;utilisateur est autorisé à vue le contenu demandé. Si les règles de fonctionnement l’autorisent, le serveur de licences délivre une licence contenant la clé de chiffrement du contenu pour déchiffrer le contenu et les règles d’utilisation associées au compte de cet utilisateur. Pour traiter une demande de licence, le serveur de licences déchiffre la demande à l’aide de sa clé privée Transport. Le CEK des métadonnées est déchiffré à l’aide de la clé privée License Server et recyclé pour lier la licence au périphérique qui fait la demande. La licence est signée à l’aide de la clé privée du serveur de licences. La réponse de licence est signée à l’aide de la clé privée Transport et chiffrée avant d’être renvoyée au client.

   Si la licence l’autorise, le client stocke la licence pour activer l’accès ** hors ligne à la licence. La mise en cache des licences permet au consommateur de vue du contenu protégé sans avoir à réacquérir une licence chaque fois qu’il souhaite vue du contenu.

1. Une fois que le client d’exécution Flash Player ou Adobe AIR dispose d’une licence, le client extrait le CEK de la licence et le client peut vue le contenu auquel il est autorisé à accéder.

   <!--<a id="fig_s43_gc2_44"></a>-->

   ![](assets/FMRMS_fig01_web.png)

   L&#39;exemple précédent ne montre qu&#39;un seul processus possible. Vous pouvez également utiliser un flux de travaux avec un téléchargement proactif de contenu lorsque l’acquisition de licence se produit bien plus tard. Une autre option consiste à implémenter un processus de pré-commande dans lequel l’acquisition de licence se produit avant l’accès au contenu.

