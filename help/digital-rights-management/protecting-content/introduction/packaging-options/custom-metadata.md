---
title: Métadonnées personnalisées
description: Métadonnées personnalisées
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '117'
ht-degree: 0%

---

# Métadonnées personnalisées {#custom-metadata}

Utilisez cette option pour ajouter des paires clé/valeur personnalisées aux métadonnées de contenu qui peuvent être interprétées par l’application serveur.

Le format de métadonnées pour le contenu DRM Primetime vous permet d’inclure des paires clé/valeur personnalisées au moment du conditionnement. Ces métadonnées personnalisées peuvent ensuite être traitées par le serveur de licences lors de la délivrance de la licence. Les métadonnées sont distinctes d’une stratégie DRM Primetime et peuvent être uniques pour chaque section de contenu.

Exemple de cas d’utilisation : pendant une phase bêta, vous pouvez inclure la propriété personnalisée `Release:BETA` au moment de l’emballage. Les serveurs de licences peuvent vendre des licences pour ce contenu pendant la période bêta. Cependant, une fois la période bêta terminée, les serveurs de licences n’autorisent plus l’accès au contenu.
