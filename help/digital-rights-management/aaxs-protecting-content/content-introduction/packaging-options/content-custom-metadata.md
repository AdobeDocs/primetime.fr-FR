---
title: Métadonnées personnalisées
description: Métadonnées personnalisées
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 0%

---

# Métadonnées personnalisées {#custom-metadata}

**Spécifiez la clé/valeur personnalisée à ajouter aux métadonnées de contenu pouvant être interprétées par l’application serveur.**

Le format de métadonnées de contenu Accès Adobe permet d’inclure des paires clé/valeur personnalisées au moment du conditionnement qui seront traitées par le serveur de licences lors de la délivrance de la licence. Ces métadonnées sont distinctes de la stratégie et peuvent être uniques pour chaque élément de contenu.

Exemple de cas d’utilisation : lors d’une phase bêta, vous incluez la propriété personnalisée &quot;Release:BETA&quot; au moment du conditionnement. Les serveurs de licences peuvent vendre des licences pour ce contenu pendant la période bêta, mais une fois la période bêta expirée, les serveurs de licences interdisent l’accès au contenu.
