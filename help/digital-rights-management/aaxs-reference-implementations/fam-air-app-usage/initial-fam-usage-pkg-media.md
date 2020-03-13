---
seo-title: Support du package
title: Support du package
uuid: f6e877be-d916-4766-bc44-99891a3df3a8
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Support du package {#package-media}

Utilisez l’onglet Package Media pour regrouper du contenu. La section Propriétés de Packager affiche les paramètres de Packager saisis dans l’onglet Préférences. Pour modifier ces paramètres, accédez à l’onglet Préférences, modifiez les paramètres et enregistrez.

Si vous souhaitez compresser un seul fichier FLV ou F4V, sélectionnez l’ **[!UICONTROL Select Single File]** option et saisissez le chemin d’accès complet au fichier source et le chemin d’accès complet où le fichier chiffré doit être enregistré.

Si vous souhaitez compresser tous les fichiers d’un dossier, choisissez l’ **[!UICONTROL Select Single Folder]** option. Spécifiez le dossier contenant les fichiers source. Seuls les fichiers du dossier d’entrée correspondant aux **[!UICONTROL Input Media File Selection]** critères seront compressés (les fichiers des sous-dossiers ne sont pas compressés). Choisissez de chiffrer [!DNL .flv] des fichiers, [!DNL .f4v] des fichiers ou de saisir un  de  normal personnalisé (par exemple &quot;.*&quot; chiffre tous les fichiers du dossier). Les fichiers chiffrés seront enregistrés dans le dossier de sortie spécifié, en utilisant le même nom de fichier que le fichier d’origine.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Les chemins d’accès aux fichiers doivent faire référence aux fichiers disponibles pour le serveur de création de package. Si vous exécutez Flash Access Manager sur un ordinateur différent du serveur de création de package, vous devez spécifier un chemin accessible par le serveur (situé sur un lecteur réseau ou sur le serveur lui-même).

Le tableau suivant décrit les préférences de création de packages de médias :

| Préférence | Description |
|---|---|
| Nom(s) du fichier de stratégie | Sélectionnez une ou plusieurs stratégies dans le déroulant à appliquer au contenu. Pour sélectionner plusieurs stratégies, maintenez la touche CTRL enfoncée lors de la sélection des stratégies. |
| Secondes non chiffrées | Indique le nombre de secondes de contenu à laisser non chiffré au début du fichier. Pour chiffrer à partir du début, saisissez &quot;0&quot;. |
| Chiffrer la vidéo | Cochez cette case pour chiffrer les données vidéo. |
| Niveau de chiffrement | Si le chiffrement vidéo est activé, sélectionnez le niveau de chiffrement des données vidéo. Elevé chiffre toutes les données vidéo. Moyenne et Faible chiffrent sélectivement des portions de la vidéo. (Uniquement pour F4V avec vidéo H.264) |
| Chiffrer l’audio | Cochez cette case pour chiffrer les données audio. |
| Chiffrer le script | Cochez cette case pour chiffrer les données de script (FLV uniquement). |
| Propriétés personnalisées | Spécifiez les propriétés personnalisées à inclure dans le contenu assemblé. Ces propriétés seront disponibles pour le serveur de licences lors de l’émission d’une licence. (Facultatif) |

Une fois les options de création de package sélectionnées, cliquez sur le **[!UICONTROL Package Media]** bouton pour commencer à créer un package des fichiers.
