---
seo-title: Propriétés du dossier de contrôle
title: Propriétés du dossier de contrôle
uuid: fc204bb4-033a-46fe-8642-737f6a4cd1f1
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Propriétés du dossier de contrôle {#watched-folder-properties}

Chaque dossier de contrôle contient un fichier appelé [!DNL properties/watchfolder.properties]. Ce fichier contient les options d’assemblage du contenu placé dans ce dossier, notamment les éléments à chiffrer et les stratégies à appliquer. Toute modification apportée aux valeurs du fichier de propriétés prend effet lors de la prochaine exécution du gestionnaire de package du dossier de contrôle (vous n’avez pas besoin de redémarrer le serveur).

En cas d’erreur de configuration dans le fichier de propriétés de l’outil de création de package, le thread de l’outil de création de package s’arrête. Pour reprendre le gestionnaire de package du dossier de contrôle, redémarrez le serveur. En cas d’erreur de configuration dans un fichier de propriétés du dossier de contrôle, le dossier de contrôle est temporairement supprimé du  des dossiers traités par le gestionnaire de package. Pour réajouter le dossier de contrôle au , redémarrez le serveur ou modifiez le fichier de propriétés du gestionnaire de package. Si une erreur se produit lors de la création d’un package d’un fichier particulier (par exemple, parce que le fichier est endommagé), le fichier est ignoré et les fichiers restants du dossier sont traités.
