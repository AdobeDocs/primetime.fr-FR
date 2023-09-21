---
title: Outils de ligne de commande pour empaqueter du contenu et créer des listes de révocation
description: Outils de ligne de commande pour empaqueter du contenu et créer des listes de révocation
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Outils de ligne de commande pour empaqueter du contenu et créer des listes de révocation {#command-line-tools-for-packaging-content-revocation-lists}

L’implémentation de référence comprend les outils de ligne de commande suivants :

* Gestionnaire de stratégies : outil de création et de gestion des stratégies
* Gestionnaire de listes de mises à jour de stratégie : outil permettant de créer et d’afficher des listes de mises à jour de stratégie.
* Gestionnaire de listes de révocation : outil de création et d’affichage de listes de révocation
* Media Packager : outil de création de fichiers FLV et F4V chiffrés
* AIR Publisher ID
* UtilityLicense Generator
* Incorporation de licences

## Conditions {#requirements}

Les exigences d’utilisation des outils de ligne de commande disponibles dans les implémentations de référence sont les suivantes :

* Tous les outils de ligne de commande requièrent Java 1.5 ou version ultérieure.
* Informations d’identification du Packager et du serveur de licences (certificat et mot de passe) qui sont émises par l’Adobe. Vous avez besoin d’informations d’identification pour chiffrer et signer des fichiers vidéo, signer des listes de mise à jour et de révocation des stratégies et prégénérer des licences.

>[!NOTE]
>
>En raison d’un bogue Java, les arguments utilisés sur la ligne de commande (tels que les noms de fichier, les noms de stratégie ou les descriptions) ne doivent utiliser que les caractères du jeu de caractères par défaut du système d’exploitation.

## Fichier de configuration {#configuration-file}

Plusieurs des outils de ligne de commande nécessitent un fichier de configuration contenant des informations pour les outils à utiliser pour appliquer des stratégies et chiffrer des fichiers.

Le fichier de configuration par défaut est : [!DNL flashaccesstools.properties]. Il se trouve dans le répertoire de travail, c’est-à-dire le répertoire à partir duquel vous exécutez les outils (voir Installation des outils de ligne de commande). Chaque outil contient également une option ( `-c`) qui vous permet de pointer vers le fichier de configuration à utiliser si vous préférez ne pas utiliser la valeur par défaut.

Le fichier de configuration utilise le format de fichier de propriété Java. Si les valeurs de l’une des propriétés contiennent des caractères spéciaux, gardez à l’esprit les restrictions suivantes :

* Échapper les barres obliques inverses avec une barre oblique inverse supplémentaire. Par exemple, pour spécifier la variable [!DNL C:\credentials.pfx] fichier, indiquez-le comme [!DNL C:\\credentials.pfx] ou `C:/credentials.pfx`. Pour spécifier un fichier sur un serveur réseau, spécifiez `\\\\server\\folder\\filename.pfx`.
* Le fichier de configuration ne peut contenir que des caractères latins-1. Si vous devez utiliser des caractères non latins-1, utilisez la séquence d’échappement Unicode appropriée (en utilisant, éventuellement, la variable [!DNL native2ascii] outil fourni avec Java).

Définissez des valeurs pour les propriétés dans le fichier de configuration avant d’exécuter les outils. Pour certains outils de ligne de commande, vous pouvez définir les valeurs de certaines options via la ligne de commande ou le fichier de configuration. Dans ce cas, les valeurs définies via la ligne de commande sont prioritaires sur les valeurs du fichier de configuration.

## Installation des outils de ligne de commande  {#installing-the-command-line-tools}

Vous pouvez copier les fichiers dont vous avez besoin à partir de l’ [!DNL \Reference Implementation\Command Line Tools] répertoire sur le DVD, qui contient la valeur par défaut [!DNL flashaccesstools.properties] fichier de configuration et un [!DNL libs] qui contient les fichiers JAR des outils.

La variable [!DNL samples] Le répertoire contient plusieurs exemples de fichiers source Java illustrant l’utilisation des API SDK Adobe Access. Pour créer et exécuter des exemples, utilisez la méthode [!DNL build-samples.xml] Script Ant.
