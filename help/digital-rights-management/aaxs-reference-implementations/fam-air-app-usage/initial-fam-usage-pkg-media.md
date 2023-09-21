---
title: Package Media
description: Package Media
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Package Media {#package-media}

Utilisez l’onglet Média de module pour regrouper le contenu. La section Propriétés de Packager affiche les paramètres de Packager qui ont été saisis dans l’onglet Préférences . Pour modifier ces paramètres, accédez à l’onglet Préférences , modifiez les paramètres et cliquez sur Enregistrer.

Si vous souhaitez compresser un seul fichier FLV ou F4V, choisissez la variable **[!UICONTROL Select Single File]** et saisissez le chemin d’accès complet au fichier source et le chemin d’accès complet où le fichier chiffré doit être enregistré.

Si vous souhaitez regrouper tous les fichiers dans un dossier, choisissez la variable **[!UICONTROL Select Single Folder]** . Spécifiez le dossier contenant les fichiers sources. Seuls les fichiers du dossier d’entrée correspondant au **[!UICONTROL Input Media File Selection]** Les critères seront mis en package (les fichiers des sous-dossiers ne sont pas mis en package). Choisir de chiffrer [!DNL .flv] fichiers, [!DNL .f4v] ou saisissez une expression régulière personnalisée (par exemple, &quot;.&#42;&quot; chiffre tous les fichiers du dossier). Les fichiers cryptés seront enregistrés dans le dossier de sortie spécifié, en utilisant le même nom de fichier que le fichier d’origine.

>[!NOTE]
>
>Les chemins d’accès aux fichiers doivent faire référence aux fichiers disponibles sur le serveur de package. Si vous exécutez Flash Access Manager sur un autre ordinateur que le serveur de package, vous devez spécifier un chemin d’accès accessible par le serveur (situé sur un lecteur réseau ou sur le serveur lui-même).

Le tableau suivant décrit les préférences de Package Media :

| Préférence | Description |
|---|---|
| Nom(s) de fichier(s) de stratégie | Sélectionnez une ou plusieurs stratégies à appliquer au contenu dans la liste déroulante. Pour sélectionner plusieurs stratégies, maintenez la touche CTRL enfoncée lors de la sélection de stratégies. |
| Secondes non chiffrées | Indique le nombre de secondes de contenu à ne pas chiffrer au début du fichier. Pour chiffrer à partir du début, saisissez &quot;0&quot;. |
| Chiffrer la vidéo | Cochez cette case pour chiffrer les données vidéo. |
| Niveau de chiffrement | Si le chiffrement vidéo est activé, sélectionnez le niveau de chiffrement des données vidéo. Chiffre élevé toutes les données vidéo. Les valeurs Moyen et Faible chiffrent sélectivement des parties de la vidéo. (Uniquement pour F4V avec vidéo H.264) |
| Chiffrer l’audio | Cochez cette case pour crypter les données audio. |
| Chiffrer le script | Cochez cette case pour chiffrer les données de script (FLV uniquement). |
| Propriétés personnalisées | Spécifiez les propriétés personnalisées à inclure dans le contenu empaqueté. Ces propriétés seront disponibles pour le serveur de licences lors de l’émission d’une licence. (Facultatif) |

Une fois les options de conditionnement sélectionnées, cliquez sur le bouton **[!UICONTROL Package Media]** pour commencer à compresser les fichiers.
