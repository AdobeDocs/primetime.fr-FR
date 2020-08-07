---
seo-title: 'Outils de ligne de commande pour la création de packages de contenu et la création de listes de révocation '
title: 'Outils de ligne de commande pour la création de packages de contenu et la création de listes de révocation '
uuid: 2c740521-2004-4320-88e1-118b84e80e31
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---


# Outils de ligne de commande pour la création de packages de contenu et la création de listes de révocation {#command-line-tools-for-packaging-content-revocation-lists}

L’implémentation de référence comprend les outils de ligne de commande suivants :

* Gestionnaire de stratégies : Outil de création et de gestion des stratégies
* Gestionnaire de Listes de mise à jour des stratégies : Outil permettant de créer et d’afficher des listes de mise à jour de stratégie
* Gestionnaire de Listes de révocation : Outil de création et d’affichage des listes de révocation
* Media Packager : Outil de création de fichiers FLV et F4V chiffrés
* ID de l’éditeur AIR
* Générateur de licences d&#39;utilitaire
* Incorporation de licence

## Conditions requises {#requirements}

Les exigences relatives à l’utilisation des outils de ligne de commande disponibles dans les implémentations de référence sont les suivantes :

* Tous les outils de ligne de commande nécessitent Java 1.5 ou version ultérieure.
* Informations d’identification de Packager et License Server (certificat et mot de passe) émises par l’Adobe. Vous avez besoin d’informations d’identification pour chiffrer et signer des fichiers vidéo, pour signer des listes de mise à jour et de révocation des stratégies et pour prégénérer des licences.

>[!NOTE]
>
>En raison d’un bogue Java, les arguments utilisés sur la ligne de commande (tels que les noms de fichier, les noms de stratégie ou les descriptions) ne doivent utiliser que les caractères du jeu de caractères par défaut du système d’exploitation.

## Fichier de configuration {#configuration-file}

Plusieurs des outils de ligne de commande nécessitent un fichier de configuration contenant des informations pour les outils à utiliser pour l’application de stratégies et le chiffrement de fichiers.

Le fichier de configuration par défaut est [!DNL flashaccesstools.properties]. Il se trouve dans le répertoire de travail ; c&#39;est-à-dire le répertoire à partir duquel vous exécutez les outils (voir Installation des outils de ligne de commande). Chaque outil contient également une option ( `-c`) qui vous permet de pointer vers le fichier de configuration à utiliser si vous préférez ne pas utiliser la valeur par défaut.

Le fichier de configuration utilise le format de fichier de propriétés Java. Si les valeurs de l’une des propriétés contiennent des caractères spéciaux, gardez à l’esprit les restrictions suivantes :

* Echapper aux barres obliques inverses avec une barre oblique inverse supplémentaire. Par exemple, pour spécifier le [!DNL C:\credentials.pfx] fichier, spécifiez-le comme [!DNL C:\\credentials.pfx] ou `C:/credentials.pfx`. Pour spécifier un fichier sur un serveur réseau, spécifiez `\\\\server\\folder\\filename.pfx`.
* Le fichier de configuration ne peut contenir que des caractères latins-1. Si vous devez utiliser des caractères non latins-1, utilisez la séquence d’échappement Unicode appropriée (en utilisant, éventuellement, l’outil [!DNL native2ascii] fourni avec Java).

Définissez les valeurs des propriétés dans le fichier de configuration avant d’exécuter les outils. Pour certains outils de ligne de commande, vous pouvez définir les valeurs de certaines options par le biais de la ligne de commande ou du fichier de configuration. Dans ces cas, les valeurs définies par le biais de la ligne de commande sont prioritaires sur les valeurs du fichier de configuration.

## Installation des outils de ligne de commande  {#installing-the-command-line-tools}

Vous pouvez copier les fichiers dont vous avez besoin à partir du [!DNL \Reference Implementation\Command Line Tools] répertoire du DVD, qui contient le fichier de [!DNL flashaccesstools.properties] configuration par défaut, et un [!DNL libs] répertoire, qui contient les fichiers JAR des outils.

Le [!DNL samples] répertoire contient plusieurs exemples de fichiers source Java démontrant l’utilisation des API Adobe Access SDK. Pour créer et exécuter les exemples, utilisez le script [!DNL build-samples.xml] Ant.