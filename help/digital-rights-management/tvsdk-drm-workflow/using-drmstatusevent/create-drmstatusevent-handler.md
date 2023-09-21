---
title: Création d’un gestionnaire DRMStatusEvent
description: Création d’un gestionnaire DRMStatusEvent
copied-description: true
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 0%

---


# Création d’un gestionnaire DRMStatusEvent{#create-a-drmstatusevent-handler}

L’exemple suivant crée un gestionnaire d’événements qui génère les informations d’état du contenu DRM pour l’objet Primetime à l’origine de l’événement.

Ajoutez un gestionnaire d’événements à un objet Primetime qui pointe vers du contenu protégé :

```
function drmStatusEventHandler(event:DRMStatusEvent):void { trace(event); } 
```

