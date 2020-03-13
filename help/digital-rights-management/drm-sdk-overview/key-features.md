---
seo-title: Principales fonctionnalités
title: Principales fonctionnalités
uuid: bee91fd7-a335-4881-abad-8972f28630d5
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc

---


# Principales fonctionnalités{#key-features}

Adobe Primetime DRM propose les principales fonctionnalités suivantes :

* **Prise en charge de la diffusion en flux continu HLS (nécessite Adobe Primetime) :** Utilisez le DRM Primetime avec du contenu HLS qui peut être diffusé en continu sur n’importe quelle plate-forme prise en charge par Flash ou Adobe Primetime (bureau, iOS et Android, par exemple).
* **Prise en charge des applications iOS natives (nécessite Adobe Primetime) :** Utilisez Primetime DRM pour protéger la vidéo dans vos applications iOS.
* **Prise en charge des applications Android natives (nécessite Adobe Primetime) :** Utilisez Primetime DRM pour protéger la vidéo dans vos applications Android.
* **Diffusion en flux continu protégée sur Xbox (nécessite Adobe Primetime)**.
* **de clé iOS distante (nécessite Adobe Primetime) :** Prise en charge de la diffusion de clés iOS distantes via un serveur de clés multi-locataires, appelé serveur de clés DRM Primetime.
* **Protection du contenu persistant :** Le contenu reste protégé tout au long de la chaîne de distribution. Une fois le contenu compressé, il reste protégé en tout temps et certaines parties ne sont déchiffrées qu’au moment de la lecture et conformément aux règles d’utilisation.
* Etant donné que le contenu est conditionné avec des règles d’utilisation et des informations de licence, la protection se déplace toujours avec le contenu. Si des utilisateurs sans licence tentent de lire le contenu, la stratégie intégrée dans le contenu les redirige afin qu’ils puissent acquérir une licence valide pour le contenu.
* **Lecture sécurisée du contenu protégé :** Des schémas de chiffrement éprouvés sont utilisés pour protéger le contenu contre la lecture non autorisée.
* **Règles d’utilisation flexibles :** Les règles d’utilisation déterminent la manière dont les consommateurs peuvent utiliser le contenu protégé. Les règles d’utilisation prises en charge par Primetime DRM permettent d’utiliser plusieurs modèles d’entreprise différents, notamment le paiement par, la location de films, les  d’ou les services financés par des annonces publicitaires. Les règles d’utilisation sont spécifiées par la stratégie que vous incorporez dans le contenu lors de l’assemblage ou peuvent être spécifiées par le serveur de licences lors de l’acquisition de la licence.
* **Protection de sortie :** Les contrôles de protection de la sortie peuvent être utilisés pour engager des systèmes de protection tels que HDCP, CGMS-A ou Rovi (anciennement Macrovision) ACP. Cela permet de protéger la sortie du contenu par rapport aux sorties numériques (par exemple, HDMI, DVI et UDI) et analogiques (par exemple, S-Video et Component Video).

   Vous pouvez spécifier des options de protection de sortie dans la stratégie que vous créez pour votre contenu, autorisant ou refusant l’accès au contenu en fonction des capacités de protection de sortie d’un périphérique. Par exemple, vous pouvez spécifier que la protection de sortie n’est pas requise pour certains contenus, mais qu’elle nécessite une protection de sortie pour le contenu vidéo de qualité supérieure, ce qui empêche la sortie du contenu sur les systèmes d’exploitation qui ne disposent pas de cette fonctionnalité.

   Bien que ces règles soient appliquées de manière cohérente sur toutes les plates-formes, il n’est actuellement possible d’activer la protection de sortie en toute sécurité que sur les plates-formes Windows.

* **Prise en charge de la diffusion dynamique en flux continu :** Utilisez la fonction de diffusion en flux continu dynamique de Flash Media Server ou de diffusion en flux continu dynamique HTTP Adobe pour protéger le contenu codé à plusieurs débits. La diffusion en flux continu dynamique utilise un flux vidéo qui ajuste dynamiquement le débit et la qualité de lecture en fonction de la bande passante disponible, ce qui permet d’améliorer l’expérience utilisateur. La gestion des droits numériques Primetime permet d’utiliser la même clé de chiffrement de contenu et la même licence pour les différents codages d’un même fichier.
* **Affichage hors ligne :** Le client d’exécution Adobe AIR permet aux clients de télécharger et de stocker du contenu pour une consultation ultérieure, que l’ordinateur reste connecté ou non à Internet.
* **Licences basées sur l’identité :** Liez les autorisations aux identités des utilisateurs, en demandant aux utilisateurs de s’authentifier (en fournissant un ID utilisateur et un mot de passe) afin d’accéder au contenu. Les licences basées sur l’identité exigent que le développeur de l’application cliente mette en oeuvre l’authentification de l’utilisateur dans le cadre du processus d’acquisition de licence.
* **Chaîne de licence :** Permet aux consommateurs de prolonger la durée de vie de tout leur contenu en renouvelant une licence racine unique. L’une des principales utilisations du chaînage de licences est  les modèles d’entreprise basés sur , où, à la fin d’une  période de, les licences d’un grand nombre de fichiers de contenu peuvent être renouvelées simplement en renouvelant la licence racine.

   Les licences root et leaf sont liées à l&#39;ordinateur du consommateur. La licence feuille contient le CEK et une référence à la licence racine. La licence racine peut étendre les droits accordés dans la licence feuille. Par exemple, un consommateur peut avoir des licences en feuilles pour 50 éléments de contenu qui expireront à la fin d’une période   donnée. Si le consommateur télécharge une nouvelle licence racine avec une nouvelle date d’expiration, les 50 éléments de contenu peuvent être lus jusqu’à l’expiration de la licence mise à jour.

   Primetime DRM 2.0 a introduit le chaînage de licences dans lequel les licences feuille et racine sont liées à un ordinateur spécifique. Primetime DRM 3.0 introduit une forme améliorée de chaînage de licence, dans laquelle une feuille est liée à une licence racine, et seule la licence racine est liée à un ordinateur ou un domaine spécifique. Lisez la section *Amélioration du chaînage* de licence dans *Utilisation du SDK DRM d’Adobe Primetime pour la protection du contenu*.

* **Rotation clé :** Lors d’un pack classique, le contenu est chiffré à l’aide de la clé de chiffrement de contenu (CEK) et le client obtient une licence contenant le CEK afin de consommer le contenu. Lorsque la rotation des clés est activée, la clé utilisée pour chiffrer le contenu peut être modifiée afin que la clé ne soit utilisée que pour chiffrer une partie du contenu. Lisez la section Rotation *des* clés dans *Utilisation du SDK DRM d’Adobe Primetime pour la protection du contenu*.

* **Licences hors bande :** Grâce à la gestion des droits numériques Primetime, il est possible de mettre en oeuvre un processus dans lequel les clients obtiennent des licences prégénérées hors bande, éliminant ainsi la nécessité de déployer un serveur de licences.
* **Prise en charge des domaines :** Plutôt que de lier une licence à un périphérique spécifique, Primetime DRM prend en charge la liaison de licences à un domaine. Plusieurs périphériques peuvent rejoindre un domaine et recevoir un jeton de domaine permettant de déplacer des licences entre des périphériques du domaine. Lisez Enregistrement *de* domaine dans *Utilisation du SDK DRM d’Adobe Primetime pour la protection du contenu*.

* **Chiffrement partiel :** Indique si toutes les images, ou uniquement un sous-ensemble de cadres, doivent être chiffrées. Il existe trois niveaux de chiffrement : low, medium et high. La réduction du niveau de chiffrement peut réduire la charge CPU sur les ordinateurs bas de gamme.
* **Assemblage de contenu déconnecté :** La mise en package de contenu ne nécessite pas de connexion réseau au serveur de licences. Cela permet des opérations dorsales sécurisées en limitant l&#39;exposition du contenu compressé qui n&#39;a pas encore été protégé.
* **Contrôle sur la restauration de l&#39;horloge : **Primetime DRM permet un calcul sécurisé et précis du temps nécessaire pour détecter le retour arrière de l&#39;horloge sur l&#39;ordinateur client. Cela permet d’appliquer les droits d’accès au contenu pendant une durée déterminée et d’empêcher les consommateurs de subvertir les droits d’accès en modifiant le temps passé sur leur ordinateur.
* **Personnalisation**: Permet de lier du contenu à un ordinateur particulier.
* **Liste blanche des applications :** Permet au client runtime de s’assurer que le contenu protégé est uniquement lu dans un fichier SWF ou une application AIR autorisé.
* **Révocation des clients compromis :** Le logiciel client compromis peut être révoqué. Si l’exécution de Flash Player ou d’Adobe AIR est jugée compromise, le service peut être refusé à ces clients jusqu’à ce qu’ils passent à une version plus récente et plus sécurisée du logiciel client.
* **Plusieurs stratégies pour le même fichier vidéo :** Plusieurs stratégies peuvent être intégrées à un seul élément de contenu vidéo lors de l’assemblage. Lors de l’émission d’une licence, le serveur de licences peut décider des stratégies à utiliser, ce qui permet au distributeur de contenu d’utiliser le même fichier protégé pour différents modèles commerciaux (tels que la location et la vente électronique).