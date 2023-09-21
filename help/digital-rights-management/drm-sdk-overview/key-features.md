---
title: Fonctionnalités clés
description: Fonctionnalités clés
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1147'
ht-degree: 0%

---

# Fonctionnalités clés{#key-features}

Adobe Primetime DRM offre les fonctionnalités clés suivantes :

* **Prise en charge de la diffusion en continu HLS (nécessite Adobe Primetime) :** Utilisez Primetime DRM avec du contenu HLS qui peut être diffusé en continu sur n’importe quelle plate-forme prise en charge par Flash ou Adobe Primetime (tel que Bureau, iOS et Android).
* **Prise en charge des applications iOS natives (nécessite Adobe Primetime) :** Utilisez Primetime DRM pour protéger la vidéo dans vos applications iOS.
* **Prise en charge des applications Android natives (nécessite Adobe Primetime) :** Utilisez Primetime DRM pour protéger la vidéo dans vos applications Android.
* **Diffusion en continu protégée sur Xbox (nécessite Adobe Primetime)**.
* **Diffusion clé iOS distante (nécessite Adobe Primetime) :** Prise en charge de la diffusion de clés iOS distantes par le biais d’un serveur de clés multi-client, appelé Primetime DRM Key Server.
* **Protection du contenu persistant :** Le contenu reste protégé dans toute la chaîne de distribution. Une fois le contenu empaqueté, il reste protégé en tout temps et certaines parties ne sont décryptées qu’au moment de la lecture et conformément aux règles d’utilisation.
* Comme le contenu est empaqueté avec des règles d’utilisation et des informations de licence, la protection se déplace toujours avec le contenu. Si les clients sans licence tentent de lire le contenu, la stratégie incorporée dans le contenu le redirige afin qu’ils puissent acquérir une licence valide pour le contenu.
* **Lecture sécurisée du contenu protégé :** Les schémas de chiffrement prouvés sont utilisés pour protéger le contenu contre la lecture non autorisée.
* **Règles d’utilisation flexibles :** Les règles d’utilisation déterminent la manière dont les consommateurs peuvent utiliser du contenu protégé. Les règles d’utilisation prises en charge par Primetime DRM permettent plusieurs modèles d’entreprise différents, notamment la paiement à la vue, la location de films, les abonnements ou les services financés par des publicités. Les règles d’utilisation sont spécifiées par la stratégie que vous incorporez dans le contenu lors du conditionnement ou peuvent être spécifiées par le serveur de licences lors de l’acquisition de la licence.
* **Protection de la sortie :** Les contrôles de protection de la sortie peuvent être utilisés pour engager des programmes de protection tels que HDCP, CGMS-A ou Rovi (anciennement Macrovision) ACP. Cela peut vous aider à protéger la sortie du contenu par rapport aux sorties numériques (par exemple, HDMI, DVI et UDI) et analogiques (par exemple, S-Video et Component Video).

  Vous pouvez spécifier des options de protection de sortie dans la stratégie que vous créez pour votre contenu, ce qui permet ou non l’accès au contenu en fonction des fonctionnalités de protection de sortie d’un appareil. Par exemple, vous pouvez spécifier que la protection de sortie n’est pas requise pour certains contenus, mais qu’elle nécessite une protection de sortie pour les contenus vidéo de qualité supérieure, ce qui empêche la sortie du contenu sur les systèmes d’exploitation qui ne disposent pas de cette fonctionnalité.

  Bien que ces règles soient appliquées de manière cohérente sur toutes les plateformes, il est actuellement possible d’activer la protection de sortie en toute sécurité sur les plateformes Windows.

* **Prise en charge de la diffusion en continu dynamique :** Utilisez la fonction de diffusion en continu dynamique du HTTP Dynamic Streaming Flash Media Server ou Adobe pour protéger le contenu codé à plusieurs débits. La diffusion en continu dynamique utilise un flux vidéo qui ajuste dynamiquement le débit et la qualité de lecture en fonction de la bande passante disponible, offrant ainsi une expérience utilisateur améliorée. Primetime DRM permet d’utiliser la même clé de chiffrement de contenu et la même licence pour les différents codages d’une même ressource.
* **Affichage hors ligne :** Le client d’exécution Adobe AIR permet aux clients de télécharger et de stocker du contenu pour un affichage ultérieur, que l’ordinateur reste connecté ou non à Internet.
* **Licences basées sur les identités :** Associe les autorisations aux identités des utilisateurs, ce qui nécessite que les clients s’authentifient (en fournissant un identifiant et un mot de passe utilisateur) pour accéder au contenu. Les licences basées sur les identités exigent que le développeur de l’application cliente mette en oeuvre l’authentification de l’utilisateur dans le cadre du processus d’acquisition de licences.
* **Chaîne de licence :** Permet aux consommateurs de prolonger la durée de vie de tout leur contenu en renouvelant une licence racine unique. L’une des principales utilisations du chaînage de licences est pour les modèles d’entreprise par abonnement, où, à la fin d’une période d’abonnement, les licences d’un grand nombre de fichiers de contenu peuvent être renouvelées simplement en renouvelant la licence racine.

  Les licences racines et terminales sont liées à l&#39;ordinateur du consommateur. La licence feuille contient le CEK et une référence à la licence racine. La licence racine peut étendre les droits accordés dans la licence feuille. Par exemple, un consommateur peut posséder des licences terminales pour 50 éléments de contenu qui expireront à la fin d’une période d’abonnement donnée. Si le consommateur télécharge une nouvelle licence racine avec une nouvelle date d’expiration, les 50 éléments de contenu peuvent être lus jusqu’à l’expiration de la licence mise à jour.

  Primetime DRM 2.0 a introduit la chaîne de licence dans laquelle les licences feuille et racine sont liées à une machine spécifique. Primetime DRM 3.0 introduit une forme améliorée de chaînage de licences, dans laquelle une feuille est liée à une licence racine, et seule la licence racine est liée à une machine ou un domaine spécifique. Lecture *Chaîne de licence améliorée* in *Utilisation du SDK Adobe Primetime DRM pour la protection du contenu*.

* **Rotation des clés :** Lors d’un package type, le contenu est chiffré à l’aide de la clé de chiffrement de contenu (CEK), et le client obtient une licence contenant le CEK pour consommer le contenu. Lorsque la rotation de clé est activée, la clé utilisée pour chiffrer le contenu peut être modifiée de sorte que la clé ne soit utilisée que pour chiffrer une partie du contenu. Lecture *Rotation des clés* in *Utilisation du SDK Adobe Primetime DRM pour la protection du contenu*.

* **Licences hors bande :** Avec Primetime DRM, il est possible de mettre en oeuvre un workflow dans lequel les clients obtiennent des licences prégénérées hors bande, éliminant ainsi la nécessité de déployer un serveur de licences.
* **Prise en charge des domaines :** Au lieu de lier une licence à un appareil spécifique, Primetime DRM prend en charge la liaison de licences à un domaine. Plusieurs appareils peuvent rejoindre un domaine et recevoir un jeton de domaine permettant de déplacer des licences entre les appareils du domaine. Lecture *Enregistrement de domaine* in *Utilisation du SDK Adobe Primetime DRM pour la protection du contenu*.

* **Chiffrement partiel :** Indique si toutes les images, ou uniquement un sous-ensemble d’images, doivent être chiffrées. Il existe trois niveaux de cryptage : bas, moyen et élevé. La réduction du niveau de chiffrement peut réduire la surcharge du processeur sur les ordinateurs de bas niveau.
* **Compilation de contenu déconnecté :** Le package de contenu ne nécessite pas de connexion réseau au serveur de licences. Cela permet des opérations dorsales sécurisées en limitant l’exposition du contenu compressé qui n’a pas encore été protégé.
* **Contrôle du retour arrière sur l’horloge : **Primetime DRM permet un calcul sécurisé et précis du temps pour détecter le retour arrière sur l’ordinateur client. Cela applique les droits liés à l’accès au contenu pendant une période spécifique et empêche les consommateurs de subvertir les droits d’accès en modifiant l’heure sur leur ordinateur.
* **Individualisation**: permet de lier le contenu à une machine particulière.
* **Liste autorisée de l’application :** Permet au composant d’exécution du client de s’assurer que le contenu protégé n’est lu que dans un SWF autorisé ou une application AIR.
* **Révocation des clients compromis :** Les logiciels clients promis peuvent être révoqués. Si le runtime Flash Player ou Adobe AIR est déterminé comme ayant été compromis, le service peut être refusé à ces clients jusqu’à ce qu’ils effectuent une mise à niveau vers une version plus récente et plus sécurisée du logiciel client.
* **Stratégies multiples pour le même fichier vidéo :** Une seule partie du contenu vidéo peut comporter plusieurs stratégies incorporées lors du conditionnement. Lors de l’octroi d’une licence, le serveur de licences peut décider des politiques à utiliser, ce qui permet à un distributeur de contenu d’utiliser le même fichier protégé pour différents modèles d’entreprise (tels que la location et la vente électronique).
