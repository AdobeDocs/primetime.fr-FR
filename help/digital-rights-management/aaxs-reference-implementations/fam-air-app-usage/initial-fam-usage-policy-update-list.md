---
title: Liste de mise à jour des stratégies
description: Liste de mise à jour des stratégies
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Liste de mise à jour des stratégies {#policy-update-list}

Vous pouvez utiliser des listes de mise à jour de stratégie pour communiquer les modifications de stratégie à un serveur de licences. Si une stratégie est modifiée après avoir été utilisée pour empaqueter du contenu, il est souhaitable que le serveur de licences connaisse la version la plus récente de la stratégie, de sorte que cette version puisse être utilisée pour émettre une licence.

Pour créer une liste de mise à jour de stratégie pour la première fois, cliquez sur **[!UICONTROL Add policies]** pour afficher toutes les stratégies disponibles sur le serveur. Pour toute stratégie mise à jour depuis qu’elle a été utilisée pour empaqueter du contenu, sélectionnez la variable **[!UICONTROL update]** bouton radio.

Si vous ne souhaitez plus utiliser de stratégie pour émettre des licences et que la stratégie a déjà été utilisée pour compresser le contenu, vous pouvez révoquer la stratégie. Pour ce faire, sélectionnez la variable **[!UICONTROL revoke]** bouton radio. Lorsque les stratégies souhaitées ont été sélectionnées, choisissez **[!UICONTROL Create Policy Update List]**. Un fichier appelé [!DNL PolicyUpdateList.dat] est enregistré dans la variable [!DNL Resources] Répertoire.

Pour modifier une liste de mise à jour de stratégie existante, cliquez sur **[!UICONTROL Add policies]** pour afficher toutes les stratégies disponibles sur le serveur. Sélectionnez les stratégies supplémentaires à ajouter ou à révoquer. Les entrées existantes dans la liste de mise à jour des stratégies peuvent être modifiées dans la section supérieure de l’écran. Stratégies marquées **[!UICONTROL updated]** peut être remplacé par **[!UICONTROL revoked]**, mais une fois qu’une stratégie est **[!UICONTROL revoked]**, il ne peut pas être rétabli sur **[!UICONTROL updated]**.

Lorsque les modifications souhaitées ont été apportées, choisissez **[!UICONTROL Create Policy Update List]**, et la variable [!DNL PolicyUpdateList.dat] est régénéré. Si une stratégie figure déjà dans la liste de mise à jour des stratégies et a été mise à jour depuis la dernière fois que la liste a été générée, la version la plus récente de la stratégie est utilisée lors de la nouvelle génération de la liste de mise à jour des stratégies.
