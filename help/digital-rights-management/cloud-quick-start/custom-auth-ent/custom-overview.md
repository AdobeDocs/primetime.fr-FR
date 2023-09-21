---
title: Présentation de l’authentification/des droits personnalisés (facultatif)
description: Présentation de l’authentification/des droits personnalisés (facultatif)
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---

# Présentation de l’authentification/des droits personnalisés (facultatif){#custom-authentication-entitlement-overview-optional}

Primetime Cloud DRM peut être configuré pour atteindre votre propre service d’authentification/de droits principal afin de déterminer :

* Cet utilisateur est-il autorisé à acquérir une licence ?
* Quels droits/restrictions devrait être inclus dans la licence ?

Primetime Cloud DRM comprend une implémentation de référence d’un service d’authentification/de droits principal. À des fins de démonstration, ce serveur émet des réponses &quot;autorisées&quot; aux demandes BEES. Voir [!DNL BEESServlet.java] pour modifier le comportement du serveur.

>[!NOTE]
>
>Auparavant, il s’agissait d’un produit distinct appelé *Serveur de droits back-end* (BEES), donc les références à BEES dans ce document et dans les fichiers sources.
