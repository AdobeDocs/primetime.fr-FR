---
seo-title: Présentation de l'authentification personnalisée/des droits (facultatif)
title: Présentation de l'authentification personnalisée/des droits (facultatif)
uuid: 8b5e38a5-562c-4781-ac40-4b3d6cdd97fe
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Présentation de l&#39;authentification personnalisée/des droits (facultatif){#custom-authentication-entitlement-overview-optional}

Primetime Cloud DRM peut être configuré pour accéder à votre propre service d’authentification/de droits dorsaux afin de déterminer :

* Cet utilisateur est-il autorisé à acquérir une licence ?
* Quels droits/restrictions devraient figurer dans la licence ?

Primetime Cloud DRM comprend une implémentation de référence d’un service d’authentification/de droits principal. À des fins de démonstration, ce serveur émet des réponses &quot;autoriser&quot; aux demandes BEES. Voir [!DNL BEESServlet.java] pour modifier le comportement du serveur.

>[!NOTE]
>
>Auparavant, il s&#39;agissait d&#39;un produit distinct appelé *Back End Entitlement Server* (BEES), par conséquent les références à BEES tout au long de ce document et dans les fichiers source.

