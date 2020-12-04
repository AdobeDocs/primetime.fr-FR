---
seo-title: Acquisition de contenu
title: Acquisition de contenu
uuid: f3d8b4ef-bc45-4c2d-962b-638512ca0ef3
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---


# Acquisition de contenu {#content-acquisition}

Lorsqu’un utilisateur acquiert un fichier de contenu protégé d’un site Web ou d’un réseau de diffusion de contenu, il doit également acquérir une licence qui contient une clé pour déchiffrer la vidéo avant de pouvoir la lire. Les étapes suivantes illustrent un processus commun d’accès au contenu protégé par un Flash Player d’exécution ou un Adobe AIR d’ordinateur :

1. Le consommateur consulte le site Web du détaillant et sélectionne une vidéo à regarder. Le client tente de télécharger ou de diffuser la vidéo protégée sur son ordinateur à l’aide d’un Flash Player ou d’une application Adobe AIR.

   Si c’est la première fois que le consommateur tente d’accéder à un contenu protégé à l’aide de cet ordinateur spécifique, l’exécution du Flash Player ou de Adobe AIR doit d’abord être individualisée comme décrit à l’étape 2. Si le client d’exécution a déjà été individualisé, le processus d’acquisition d’une licence se produit comme décrit à l’étape 3.

1. Le Flash Player ou le client d’exécution Adobe AIR acquiert un certificat numérique unique (appelé *certificat d’ordinateur*) à partir d’un serveur hébergé par un Adobe.

   Ce processus d&#39;attribution d&#39;un certificat unique s&#39;appelle *individualisation*. L’individualisation identifie de manière unique à la fois l’ordinateur et le Flash Player ou l’exécution Adobe AIR utilisé pour lire le contenu.

   Le processus d’individualisation permet de lier les licences téléchargées à un ordinateur spécifique sur lequel le client est installé. Chaque ordinateur reçoit des informations d’identification d’ordinateur uniques (clé privée de l’ordinateur et certificat de l’ordinateur). Si un client spécifique est compromis, il peut être révoqué et interdit d’acquérir des licences pour le nouveau contenu.

1. Le client analyse le contenu protégé lorsqu’il commence à télécharger ou à diffuser en continu sur l’ordinateur du consommateur et extrait l’URL du serveur de licences du détaillant des métadonnées DRM intégrées au fichier.

   En règle générale, les métadonnées DRM sont distinctes du contenu, par exemple incorporées dans un fichier de manifeste qui les accompagne ou sous la forme d’un objet blob binaire, mais elles peuvent également être incorporées dans le fichier de contenu. Le client contacte le serveur de licences à l’URL spécifiée et acquiert une licence (comme décrit ci-dessous à l’étape 4).
1. Le client acquiert une licence auprès du serveur de licences du détaillant.

   Lors de l&#39;acquisition de la licence, le client envoie au serveur de licence du détaillant les informations identifiant le contenu demandé (les *métadonnées DRM*) et le certificat de l&#39;ordinateur (identifiant l&#39;ordinateur du consommateur). La demande de licence envoyée au serveur est chiffrée à l’aide de la clé publique Transport, qui est également incluse dans les métadonnées DRM.

   Le serveur de licences, qui peut être intégré à l&#39;infrastructure de facturation et d&#39;authentification du détaillant, peut effectuer un contrôle des règles de fonctionnement pour vérifier que l&#39;utilisateur est autorisé à vue le contenu demandé. Si les règles de fonctionnement l’autorisent, le serveur de licences délivre une licence contenant la clé de chiffrement du contenu pour déchiffrer le contenu et les règles d’utilisation associées au compte de cet utilisateur. Pour traiter une demande de licence, le serveur de licences déchiffre la demande à l’aide de sa clé privée Transport. Le CEK des métadonnées est déchiffré à l’aide de la clé privée License Server et recyclé pour lier la licence au périphérique qui fait la demande. La licence est signée à l’aide de la clé privée du serveur de licences. La réponse de licence est signée à l’aide de la clé privée Transport et chiffrée avant d’être renvoyée au client.

   Si la licence l’autorise, le client stocke la licence pour activer *l’accès hors ligne* à la licence. La mise en cache des licences permet au consommateur de vue du contenu protégé sans avoir à réacquérir une licence chaque fois qu’il souhaite vue du contenu.

1. Une fois que le Flash Player ou le client d’exécution Adobe AIR a une licence, le client extrait le CEK de la licence et le consommateur peut vue le contenu auquel il est autorisé à accéder.

   <!--<a id="fig_s43_gc2_44"></a>-->

   ![](assets/FMRMS_fig01_web.png)

   L&#39;exemple précédent ne montre qu&#39;un seul processus possible. Vous pouvez également utiliser un flux de travaux avec un téléchargement proactif de contenu lorsque l’acquisition de licence se produit bien plus tard. Une autre option consiste à implémenter un processus de pré-commande dans lequel l’acquisition de licence se produit avant l’accès au contenu.

