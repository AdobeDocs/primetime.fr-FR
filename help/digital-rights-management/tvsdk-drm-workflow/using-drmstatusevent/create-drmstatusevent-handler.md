---
title: Création d’un gestionnaire DRMStatusEvent
description: Création d’un gestionnaire DRMStatusEvent
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 0%

---


# Créer un gestionnaire DRMStatusEvent{#create-a-drmstatusevent-handler}

L’exemple suivant crée un gestionnaire de événements qui génère les informations d’état du contenu DRM pour l’objet Primetime à l’origine du événement.

Ajoutez un gestionnaire de événements à un objet Primetime qui pointe vers un contenu protégé :

```
function drmStatusEventHandler(event:DRMStatusEvent):void { trace(event); } 
```

