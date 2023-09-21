---
title: Propriétés du dossier de contrôle
description: Propriétés du dossier de contrôle
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# Propriétés du dossier de contrôle {#watched-folder-properties}

Chaque dossier de contrôle contient un fichier appelé [!DNL properties/watchfolder.properties]. Ce fichier contient les options de package du contenu placé dans ce dossier, y compris les éléments à chiffrer et les stratégies à appliquer. Toute modification apportée aux valeurs du fichier de propriétés prend effet lors de la prochaine exécution du module de dossier de contrôle (vous n’avez pas besoin de redémarrer le serveur).

En cas d’erreur de configuration dans le fichier de propriétés de packager, le thread de packager s’arrête. Pour reprendre le module de dossier de contrôle, redémarrez le serveur. En cas d’erreur de configuration dans un fichier de propriétés du dossier de contrôle, ce dernier est temporairement supprimé de la liste des dossiers traités par le programme de configuration. Pour réajouter le dossier de contrôle à la liste, redémarrez le serveur ou modifiez le fichier de propriétés du package. Si une erreur se produit lors du regroupement d’un fichier particulier (par exemple, car le fichier est corrompu), le fichier est ignoré et les fichiers restants du dossier sont traités.
