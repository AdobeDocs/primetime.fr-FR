---
seo-title: Création d’un gestionnaire DRMStatusEvent
title: Création d’un gestionnaire DRMStatusEvent
uuid: 64f539d9-344c-4372-88b8-c8d098af9dd8
translation-type: tm+mt
source-git-commit: 5749142d42f7d7b36c96592955d1f71f6a7956fc

---


# Création d’un gestionnaire DRMStatusEvent{#create-a-drmstatusevent-handler}

L’exemple suivant crée un gestionnaire de  qui génère les informations d’état du contenu DRM pour l’objet Primetime à l’origine de l’ de.

Ajouter un gestionnaire de  de à un objet Primetime qui pointe vers un contenu protégé :

```
function drmStatusEventHandler(event:DRMStatusEvent):void { trace(event); } 
```

