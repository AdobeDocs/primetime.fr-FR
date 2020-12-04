---
seo-title: Package media
title: Package media
uuid: f6e877be-d916-4766-bc44-99891a3df3a8
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---


# Support du package {#package-media}

Utilisez l’onglet Package Media pour regrouper du contenu. La section Propriétés de Packager affiche les paramètres de Packager entrés dans l’onglet Préférences. Pour modifier ces paramètres, accédez à l&#39;onglet Préférences, modifiez les paramètres et enregistrez.

Si vous souhaitez compresser un seul fichier FLV ou F4V, choisissez l’option **[!UICONTROL Select Single File]** et saisissez le chemin d’accès complet au fichier source et le chemin d’accès complet où le fichier chiffré doit être enregistré.

Si vous souhaitez compresser tous les fichiers d’un dossier, choisissez l’option **[!UICONTROL Select Single Folder]**. Spécifiez le dossier contenant les fichiers source. Seuls les fichiers du dossier d’entrée correspondant aux critères **[!UICONTROL Input Media File Selection]** seront compressés (les fichiers des sous-dossiers ne sont pas compressés). Choisissez de chiffrer des fichiers [!DNL .flv], des fichiers [!DNL .f4v] ou de saisir une expression régulière personnalisée (par exemple &quot;.*&quot; chiffre tous les fichiers du dossier). Les fichiers chiffrés seront enregistrés dans le dossier de sortie spécifié, en utilisant le même nom de fichier que le fichier d’origine.

>[!NOTE]
>
>Les chemins d’accès aux fichiers doivent faire référence aux fichiers disponibles pour le serveur d’emballage. Si vous exécutez Flash Access Manager sur un autre ordinateur que le serveur de création de package, vous devez spécifier un chemin d’accès accessible par le serveur (situé sur un lecteur réseau ou sur le serveur lui-même).

Le tableau suivant décrit les préférences de Package Media :

| Préférence | Description |
|---|---|
| Nom(s) du fichier de stratégie | Sélectionnez une ou plusieurs stratégies dans la liste déroulante à appliquer au contenu. Pour sélectionner plusieurs stratégies, maintenez la touche CTRL enfoncée tout en sélectionnant les stratégies. |
| Secondes non chiffrées | Indique le nombre de secondes de contenu à laisser non chiffré au début du fichier. Pour chiffrer à partir du début, saisissez &quot;0&quot;. |
| Chiffrer la vidéo | Cochez cette case pour chiffrer les données vidéo. |
| Niveau de chiffrement | Si le chiffrement vidéo est activé, sélectionnez le niveau de chiffrement des données vidéo. Elevé chiffre toutes les données vidéo. Moyenne et Faible chiffrent certaines portions de la vidéo de manière sélective. (Uniquement pour F4V avec vidéo H.264) |
| Chiffrer l’audio | Cochez cette case pour chiffrer les données audio. |
| Chiffrer le script | Cochez cette case pour chiffrer les données de script (FLV uniquement). |
| Propriétés personnalisées | Spécifiez les propriétés personnalisées à inclure dans le contenu assemblé. Ces propriétés seront disponibles pour le serveur de licences lors de l’émission d’une licence. (Facultatif) |

Une fois les options d’emballage sélectionnées, cliquez sur le bouton **[!UICONTROL Package Media]** pour commencer à créer un pack pour les fichiers.
