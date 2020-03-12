---
seo-title: ' de mise à jour des stratégies'
title: ' de mise à jour des stratégies'
uuid: ecc74b66-5b53-4ec3-9641-8b78929e2932
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


#  de mise à jour des stratégies {#policy-update-list}

Vous pouvez utiliser le de mise à jour de stratégie pour communiquer les modifications de stratégie à un serveur de licences. Si une stratégie est modifiée une fois qu’elle a été utilisée pour compresser du contenu, il est souhaitable que le serveur de licences connaisse la version la plus récente de la stratégie, de sorte que cette version puisse être utilisée pour émettre une licence.

Pour créer un de mise à jour de stratégie pour la première fois, cliquez **[!UICONTROL Add policies]** pour  toutes les stratégies disponibles sur le serveur. Pour toute stratégie mise à jour depuis son utilisation pour compresser le contenu, sélectionnez le bouton **[!UICONTROL update]** radio.

Si vous ne souhaitez plus utiliser une stratégie pour émettre des licences et que la stratégie a déjà été utilisée pour compresser du contenu, vous pouvez révoquer la stratégie. Pour ce faire, sélectionnez le bouton **[!UICONTROL revoke]** radio. Lorsque les stratégies souhaitées ont été sélectionnées, choisissez **[!UICONTROL Create Policy Update List]**. Un fichier appelé [!DNL PolicyUpdateList.dat] sera enregistré dans le [!DNL Resources] répertoire.

Pour modifier un  de mise à jour de stratégie existant, cliquez **[!UICONTROL Add policies]** pour  toutes les stratégies disponibles sur le serveur. Sélectionnez les stratégies supplémentaires à ajouter ou à révoquer. Les entrées existantes dans le Mise à jour de stratégie peuvent être modifiées dans la section supérieure de l’écran. Les stratégies marquées **[!UICONTROL updated]** peuvent être remplacées **[!UICONTROL revoked]**, mais une fois qu’une stratégie est **[!UICONTROL revoked]** définie, elle ne peut plus être redéfinie **[!UICONTROL updated]**.

Une fois les modifications souhaitées effectuées, choisissez **[!UICONTROL Create Policy Update List]**, puis le [!DNL PolicyUpdateList.dat] fichier est régénéré. Si une stratégie figure déjà dans le  de mise à jour de la stratégie et a été mise à jour depuis la dernière fois que le a été généré, la version la plus récente de la stratégie sera utilisée lorsque lejournal de mise à jour de la stratégie sera généré de nouveau.
