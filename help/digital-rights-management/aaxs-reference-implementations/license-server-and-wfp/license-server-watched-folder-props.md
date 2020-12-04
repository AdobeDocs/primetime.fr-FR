---
seo-title: Propriétés du dossier de contrôle
title: Propriétés du dossier de contrôle
uuid: fc204bb4-033a-46fe-8642-737f6a4cd1f1
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---


# Propriétés du dossier de contrôle {#watched-folder-properties}

Chaque dossier de contrôle contient un fichier appelé [!DNL properties/watchfolder.properties]. Ce fichier contient les options d’emballage du contenu placé dans ce dossier, y compris les éléments à chiffrer et les stratégies à appliquer. Toute modification apportée aux valeurs du fichier de propriétés prend effet lors de la prochaine exécution du gestionnaire de package du dossier de contrôle (vous n’avez pas besoin de redémarrer le serveur).

S’il existe une erreur de configuration dans le fichier de propriétés de packager, le thread de packager s’arrête. Pour reprendre l’outil Watched Folder Packager, redémarrez le serveur. Si une erreur de configuration se produit dans un fichier de propriétés du dossier de contrôle, ce dernier est temporairement supprimé de la liste des dossiers traités par le gestionnaire de package. Pour ajouter à nouveau le dossier de contrôle à la liste, redémarrez le serveur ou modifiez le fichier de propriétés de packager. Si une erreur survient lors de la création du package d’un fichier particulier (par exemple, parce que le fichier est endommagé), le fichier est ignoré et les fichiers restants du dossier sont traités.
