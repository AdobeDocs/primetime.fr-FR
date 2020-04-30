---
seo-title: liste de mise à jour de stratégie
title: liste de mise à jour de stratégie
uuid: ecc74b66-5b53-4ec3-9641-8b78929e2932
translation-type: tm+mt
source-git-commit: ''

---


# liste de mise à jour de stratégie {#policy-update-list}

Vous pouvez utiliser les Listes de mise à jour de stratégie pour communiquer les modifications de stratégie à un serveur de licences. Si une stratégie est modifiée après avoir été utilisée pour créer un pack de contenu, il est souhaitable que le serveur de licences connaisse la version la plus récente de la stratégie, de sorte que cette version puisse être utilisée pour émettre une licence.

Pour créer une Liste de mise à jour de stratégie pour la première fois, cliquez sur **[!UICONTROL Add policies]** pour vue toutes les stratégies disponibles sur le serveur. Pour toute stratégie mise à jour depuis son utilisation pour regrouper le contenu, sélectionnez le bouton **[!UICONTROL update]** radio.

Si vous ne souhaitez plus utiliser une stratégie pour émettre des licences et si la stratégie a déjà été utilisée pour regrouper le contenu, vous pouvez révoquer la stratégie. Pour ce faire, sélectionnez le bouton **[!UICONTROL revoke]** radio. Lorsque les stratégies souhaitées ont été sélectionnées, choisissez **[!UICONTROL Create Policy Update List]**. Un fichier appelé [!DNL PolicyUpdateList.dat] sera enregistré dans le [!DNL Resources] Répertoire.

Pour modifier une Liste de mise à jour de stratégie existante, cliquez **[!UICONTROL Add policies]** sur pour vue toutes les stratégies disponibles sur le serveur. Sélectionnez les stratégies supplémentaires à ajouter ou à révoquer. Les entrées existantes dans la Liste Mise à jour de la stratégie peuvent être modifiées dans la section supérieure de l’écran. Les stratégies marquées **[!UICONTROL updated]** peuvent être modifiées en **[!UICONTROL revoked]**, mais une fois qu&#39;une stratégie est **[!UICONTROL revoked]** définie, elle ne peut plus être redéfinie en **[!UICONTROL updated]** tant que telle.

Une fois les modifications souhaitées effectuées, choisissez **[!UICONTROL Create Policy Update List]** et le [!DNL PolicyUpdateList.dat] fichier est régénéré. Si une stratégie figure déjà dans la liste de mise à jour de la stratégie et a été mise à jour depuis la dernière génération de la liste, la version la plus récente de la stratégie est utilisée lorsque la Liste de mise à jour de la stratégie est générée à nouveau.
