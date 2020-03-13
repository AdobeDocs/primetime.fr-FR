---
seo-title: Création d’un gestionnaire DRMErrorEvent
title: Création d’un gestionnaire DRMErrorEvent
uuid: dde660fc-6899-47d4-97d4-46acda2db262
translation-type: tm+mt
source-git-commit: 5749142d42f7d7b36c96592955d1f71f6a7956fc

---


# Création d’un gestionnaire DRMErrorEvent{#create-a-drmerrorevent-handler}

Créez un gestionnaire de  pour traiter le d’erreur  distribué à partir de Primetime lorsqu’il rencontre une erreur lors de la tentative de lecture d’un contenu protégé.

Normalement, lorsqu’une application rencontre une erreur, elle effectue un nombre indéfini de  de nettoyage. Il informe ensuite l’utilisateur de l’erreur et fournit des options pour résoudre le problème.

```
private function drmErrorEventHandler(event:DRMErrorEvent):void {  
    trace(event.toString());  
} 
```

