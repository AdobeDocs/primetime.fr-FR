---
seo-title: Liste de mise à jour de stratégie
title: Liste de mise à jour de stratégie
uuid: ecc74b66-5b53-4ec3-9641-8b78929e2932
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---


# Liste de mise à jour de la stratégie {#policy-update-list}

Vous pouvez utiliser les Listes de mise à jour de stratégie pour communiquer les modifications de stratégie à un serveur de licences. Si une stratégie est modifiée après avoir été utilisée pour créer un pack de contenu, il est souhaitable que le serveur de licences connaisse la version la plus récente de la stratégie, de sorte que cette version puisse être utilisée pour émettre une licence.

Pour créer une Liste de mise à jour de stratégie pour la première fois, cliquez sur **[!UICONTROL Add policies]** pour vue de toutes les stratégies disponibles sur le serveur. Pour toute stratégie mise à jour depuis qu’elle a été utilisée pour regrouper le contenu, sélectionnez l’option **[!UICONTROL update]**.

Si vous ne souhaitez plus utiliser une stratégie pour émettre des licences et si la stratégie a déjà été utilisée pour regrouper le contenu, vous pouvez révoquer la stratégie. Pour ce faire, sélectionnez le bouton radio **[!UICONTROL revoke]**. Une fois les stratégies sélectionnées, choisissez **[!UICONTROL Create Policy Update List]**. Un fichier appelé [!DNL PolicyUpdateList.dat] sera enregistré dans le répertoire [!DNL Resources].

Pour modifier une Liste de mise à jour de stratégie existante, cliquez sur **[!UICONTROL Add policies]** pour vue toutes les stratégies disponibles sur le serveur. Sélectionnez les stratégies supplémentaires à ajouter ou à révoquer. Les entrées existantes dans la Liste Mise à jour de la stratégie peuvent être modifiées dans la section supérieure de l’écran. Les stratégies marquées **[!UICONTROL updated]** peuvent être remplacées par **[!UICONTROL revoked]**, mais une fois qu&#39;une stratégie est **[!UICONTROL revoked]**, il n&#39;est plus possible de la remplacer par **[!UICONTROL updated]**.

Une fois les modifications souhaitées effectuées, choisissez **[!UICONTROL Create Policy Update List]** et le fichier [!DNL PolicyUpdateList.dat] est régénéré. Si une stratégie figure déjà dans la liste de mise à jour de la stratégie et a été mise à jour depuis la dernière génération de la liste, la version la plus récente de la stratégie est utilisée lorsque la Liste de mise à jour de la stratégie est générée à nouveau.
