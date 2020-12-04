---
seo-title: Principales fonctionnalités
title: Principales fonctionnalités
uuid: bee91fd7-a335-4881-abad-8972f28630d5
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '1147'
ht-degree: 0%

---


# Principales fonctionnalités{#key-features}

Adobe Primetime DRM offre les fonctionnalités clés suivantes :

* **Prise en charge de la diffusion en flux continu HLS (nécessite l’Adobe Primetime) :** utilisez la technologie DRM Primetime avec du contenu HLS qui peut être diffusé en flux continu sur n’importe quelle plate-forme prise en charge par Flash ou Adobe Primetime (tel que Bureau, iOS et Android).
* **Prise en charge des applications iOS natives (requiert l’Adobe Primetime) :** utilisez la technologie DRM Primetime pour protéger les vidéos dans vos applications iOS.
* **Prise en charge des applications Android natives (requiert l’Adobe Primetime) :** utilisez la technologie DRM Primetime pour protéger les vidéos dans vos applications Android.
* **Diffusion en flux continu protégée sur Xbox (nécessite l&#39;Adobe Primetime)**.
* **Diffusion de clés iOS distantes (requiert Adobe Primetime) :** Prise en charge de la diffusion de clés iOS distantes via un serveur de clés à plusieurs clients, appelé serveur de clés DRM Primetime.
* **Protection du contenu persistant :** le contenu reste protégé tout au long de la chaîne de distribution. Une fois le contenu assemblé, il reste protégé en tout temps et certaines parties ne sont déchiffrées qu’au moment de la lecture et conformément aux règles d’utilisation.
* Comme le contenu est inclus dans un pack contenant des règles d’utilisation et des informations de licence, la protection se déplace toujours avec le contenu. Si des clients sans licence tentent de lire le contenu, la stratégie intégrée dans le contenu les redirige afin qu’ils puissent obtenir une licence valide pour le contenu.
* **Lecture sécurisée d’un contenu protégé : les schémas de chiffrement** prouvés sont utilisés pour protéger le contenu contre la lecture non autorisée.
* **Règles d’utilisation flexibles : les règles** d’utilisation déterminent comment les consommateurs peuvent utiliser le contenu protégé. Les règles d’utilisation prises en charge par Primetime DRM permettent la mise en place de plusieurs modèles commerciaux différents, notamment le paiement par vue, la location de films, les abonnements ou les services financés par des fonds publicitaires. Les règles d’utilisation sont spécifiées par la stratégie que vous incorporez au contenu lors de l’assemblage ou peuvent être spécifiées par le serveur de licences pendant l’acquisition de la licence.
* **Protection de la sortie :** Les contrôles de protection de la sortie peuvent être utilisés pour mettre en oeuvre des systèmes de protection tels que HDCP, CGMS-A ou Rovi (anciennement Macrovision) ACP. Cela peut aider à protéger la sortie du contenu par rapport aux sorties numériques (par exemple, HDMI, DVI et UDI) et analogiques (par exemple, S-Video et Component Video).

   Vous pouvez spécifier des options de protection de sortie dans la stratégie que vous créez pour votre contenu, en autorisant ou en refusant l’accès au contenu en fonction des capacités de protection de sortie d’un périphérique. Par exemple, vous pouvez spécifier que la protection de sortie n’est pas requise pour certains contenus, mais que vous avez besoin d’une protection de sortie pour les contenus vidéo haut de gamme, ce qui empêche la sortie du contenu sur les systèmes d’exploitation qui ne disposent pas de cette fonctionnalité.

   Bien que ces règles soient appliquées de manière cohérente sur toutes les plates-formes, il n’est actuellement possible d’activer la protection de sortie en toute sécurité que sur les plates-formes Windows.

* **Prise en charge de la diffusion en flux continu dynamique :** utilisez la fonction de diffusion en flux continu dynamique du HTTP Dynamic Streaming d’Flash Media Server ou d’Adobe pour protéger le contenu codé à plusieurs débits. La diffusion en flux continu dynamique utilise un flux vidéo qui ajuste dynamiquement le débit binaire et la qualité de lecture en fonction de la bande passante disponible, ce qui permet d’améliorer l’expérience de l’utilisateur. Primetime DRM permet d’utiliser la même clé de chiffrement de contenu et la même licence pour les différents codages d’une même ressource.
* **Affichage hors ligne :** le client d’exécution Adobe AIR permet aux utilisateurs de télécharger et de stocker du contenu pour un affichage ultérieur, que l’ordinateur reste ou non connecté à Internet.
* **Licence basée sur les identités :** lie les autorisations d’accès aux identités des utilisateurs, ce qui nécessite que les utilisateurs s’authentifient eux-mêmes (en fournissant un ID utilisateur et un mot de passe) afin d’accéder au contenu. Les licences basées sur l’identité exigent que le développeur de l’application cliente mette en oeuvre l’authentification des utilisateurs dans le cadre du processus d’acquisition de licences.
* **Chaînage de licence :** permet aux utilisateurs de prolonger la durée de vie de tout leur contenu en renouvelant une licence racine unique. L’un des Principaux usages du chaînage de licences est celui des modèles commerciaux basés sur l’abonnement, où, à la fin d’une période d’abonnement, les licences d’un grand nombre de fichiers de contenu peuvent être renouvelées en renouvelant simplement la licence racine.

   Les licences root et leaf sont liées à l&#39;ordinateur du consommateur. La licence feuille contient le CEK et une référence à la licence racine. La licence racine peut étendre les droits accordés dans la licence feuille. Par exemple, un consommateur peut disposer de licences &quot;feuille&quot; pour 50 éléments de contenu qui expireront à la fin d’une période d’abonnement donnée. Si le client télécharge une nouvelle licence racine avec une nouvelle date d’expiration, les 50 éléments de contenu peuvent être lus jusqu’à l’expiration de la licence mise à jour.

   Primetime DRM 2.0 a introduit le chaînage de licences dans lequel les licences feuille et racine sont liées à un ordinateur spécifique. Primetime DRM 3.0 introduit une forme améliorée de chaînage de licences, dans laquelle une feuille est liée à une licence racine, et seule la licence racine est liée à un ordinateur ou domaine spécifique. Lisez *Chaîne de licence améliorée* dans *Utilisation du SDK DRM Adobe Primetime pour la protection du contenu*.

* **Rotation des clés :** lors d’un pack classique, le contenu est chiffré à l’aide de la clé de chiffrement de contenu (CEK) et le client obtient une licence contenant le CEK afin de consommer le contenu. Lorsque la rotation des clés est activée, la clé utilisée pour chiffrer le contenu peut être modifiée de sorte que la clé ne soit utilisée que pour chiffrer une partie du contenu. Lisez *Rotation de clé* dans *Utilisation du SDK DRM Adobe Primetime pour la protection du contenu*.

* **Licences hors bande :** avec la gestion DRM Primetime, il est possible de mettre en oeuvre un processus dans lequel les clients obtiennent des licences prégénérées hors bande, éliminant ainsi la nécessité de déployer un serveur de licences.
* **Prise en charge des domaines :** comme alternative à la liaison d’une licence à un périphérique spécifique, Primetime DRM prend en charge la liaison de licences à un domaine. Plusieurs périphériques peuvent rejoindre un domaine et recevoir un jeton de domaine permettant de déplacer des licences entre les périphériques du domaine. Lisez *Enregistrement de domaine* dans *Utilisation du SDK DRM Adobe Primetime pour la protection du contenu*.

* **Chiffrement partiel :** indique si toutes les trames, ou seulement un sous-ensemble de trames, doivent être chiffrées. Il existe trois niveaux de chiffrement : bas, moyen et élevé. La réduction du niveau de chiffrement peut réduire la charge du processeur sur les ordinateurs de bas de gamme.
* **Emballage de contenu déconnecté : l’assemblage de** contenu ne nécessite pas de connexion réseau au serveur de licences. Cela permet des opérations dorsales sécurisées en limitant l&#39;exposition du contenu compressé qui n&#39;a pas encore été protégé.
* **Contrôle de la restauration de l&#39;horloge : **Primetime DRM permet le calcul sécurisé et précis du temps nécessaire pour détecter la restauration de l&#39;horloge sur l&#39;ordinateur client. Cela permet d&#39;appliquer les droits liés à l&#39;accès au contenu pendant une durée déterminée et d&#39;empêcher les consommateurs de subvertir les droits d&#39;accès en modifiant l&#39;heure sur leur ordinateur.
* **Individualisation** : Permet de lier du contenu à un ordinateur particulier.
* **Liste autorisée de l’application :** permet à l’exécution du client de s’assurer que le contenu protégé n’est lu que dans un fichier SWF ou une application AIR autorisé.
* **Révocation de clients compromis : le logiciel client** compromis peut être révoqué. Si l&#39;exécution du Flash Player ou de l&#39;Adobe AIR est jugée compromise, le service peut être refusé à ces clients jusqu&#39;à ce qu&#39;ils effectuent une mise à niveau vers une version plus récente et plus sécurisée du logiciel client.
* **Plusieurs stratégies pour le même fichier vidéo :** une seule partie du contenu vidéo peut comporter plusieurs stratégies intégrées lors de la création de packs. Lors de l’émission d’une licence, le serveur de licences peut décider des stratégies à utiliser, ce qui permet à un distributeur de contenu d’utiliser le même fichier protégé pour différents modèles commerciaux (tels que la location et la vente électronique).