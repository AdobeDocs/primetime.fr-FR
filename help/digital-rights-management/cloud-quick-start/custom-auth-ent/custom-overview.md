---
title: Présentation de l'authentification personnalisée/des droits (facultatif)
description: Présentation de l'authentification personnalisée/des droits (facultatif)
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---


# Présentation de l’authentification personnalisée/des droits (facultatif){#custom-authentication-entitlement-overview-optional}

Primetime Cloud DRM peut être configuré pour accéder à votre propre service d’authentification/de droits dorsaux afin de déterminer :

* Cet utilisateur est-il autorisé à acquérir une licence ?
* Quels droits/restrictions devraient figurer dans la licence ?

Primetime Cloud DRM comprend une implémentation de référence d’un service d’authentification/de droits principal. À des fins de démonstration, ce serveur émet des réponses &quot;autoriser&quot; aux demandes BEES. Voir [!DNL BEESServlet.java] pour modifier le comportement du serveur.

>[!NOTE]
>
>Auparavant, il s’agissait d’un produit distinct appelé *Serveur de droits dorsaux* (BEES), ce qui fait référence à BEES tout au long de ce document et dans les fichiers source.

