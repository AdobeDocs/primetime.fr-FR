---
description: Vous pouvez mettre en oeuvre votre propre système de journalisation.
title: Présentation de la journalisation personnalisée
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Journalisation personnalisée {#customized-logging}

Vous pouvez mettre en oeuvre votre propre système de journalisation.

Outre la journalisation à l’aide de notifications prédéfinies, vous pouvez mettre en oeuvre un système de journalisation qui utilise vos messages de journal et messages générés par TVSDK. Pour plus d’informations sur les notifications prédéfinies, voir [Le système de notification](https://help.adobe.com/en_US/primetime/psdk/ios/index.html#PSDKs-concept-The_Notification_System). Vous pouvez utiliser ces journaux pour résoudre les problèmes liés aux applications de votre lecteur et pour mieux comprendre le processus de lecture et de publicité.

La journalisation personnalisée utilise une instance singleton partagée de `PSDKPTLogFactory`, qui fournit un mécanisme pour consigner les messages sur plusieurs enregistreurs. Vous définissez et ajoutez (enregistrez) un ou plusieurs enregistreurs à la variable `PTLogFactory`. Vous pouvez ainsi définir plusieurs enregistreurs avec des implémentations personnalisées, telles qu’un enregistreur de console, un enregistreur Web ou un enregistreur d’historique de console.

TVSDK génère des messages de journal pour la plupart de ses activités, que la fonction `PTLogFactory` vers tous les enregistreurs enregistrés. Votre application peut également générer des messages de journal personnalisés, qui sont transférés à tous les enregistreurs enregistrés. Chaque enregistreur peut filtrer les messages et prendre les mesures appropriées.

Il existe deux mises en oeuvre pour `PTLogFactory`:

* Pour écouter les journaux.
* Pour ajouter des journaux à une `PTLogFactory`.

## Écoute des journaux {#listen-to-logs}

Pour vous inscrire pour écouter les journaux :
1. Implémenter une classe personnalisée qui suit le protocole `PTLogger`:

   ```
   @implementation PTConsoleLogger 
   
   + (PTConsoleLogger *) consoleLogger { 
       return [[[PTConsoleLogger alloc] init] autorelease]; 
   } 
   
   - (void)logEntry:(PTLogEntry *)entry { 
       //Log the message to the console using NSLog  
       NSLog(@"[%@] %@", entry.tag, entry.message); 
   } 
   
   @end
   ```

1. Pour enregistrer l’instance afin de recevoir les entrées de journalisation, ajoutez une instance du `PTLogger` à la fonction `PTLoggerFactory`:

   ```
   PTConsoleLogger *logger = [PTConsoleLogger consoleLogger]; 
   // Either use the addLogger method: 
   [[PTLogFactory sharedInstance] addLogger:(logger)] 
   
   //Or replace the preceding line with this macro for ease of use 
   //PTLogAddLogger(logger); 
   ```

<!--<a id="example_3738B5A8B4C048D28695E62297CF39E3"></a>-->

Voici un exemple de filtrage des journaux à l’aide de la variable `PTLogEntry` type :

```
@implementation PTConsoleLogger 
 
+ (PTConsoleLogger *) consoleLogger { 
    return [[[PTConsoleLogger alloc] init] autorelease]; 
} 
 
- (id) init { 
    self = [super init]; 
 
    if (self) { 
        self.logLevel = PTLogEntryTypeInfo; 
    } 
 
    return self; 
} 
 
- (void)logEntry:(PTLogEntry *) entry { 
    //Filtering the entry by log level  
    if (entry.type < _logLevel) { 
        return; 
    } 
 
    //Log the message to the console using NSLog NSLog(@"[%@] %@", entry.tag, entry.message); 
} 
 
@end
```

## Ajout de nouveaux messages de log {#add-new-log-messages}

Pour vous enregistrer afin d’écouter les journaux :

Créer `PTLogEntry` et ajoutez-le à `thePTLogFactory`:

Vous pouvez instancier manuellement une `PTLogEntry` et ajoutez-le à la variable `PTLogFactory` une instance partagée ou utilisez l’une des macros pour accomplir la même tâche.

Voici un exemple de journalisation à l’aide de la variable `PTLogDebug` macro:

<!--<a id="example_F014436E1686468F941F4EBD1A21B18E"></a>-->

```
// The following line creates an instance of PTLogEntry with type PTLogEntryDebug, 
// tag "DEBUG_PLAYBACK", and message "Playback has started". 
// Then the PTLogEntry is automatically added to the PTLogFactory  
 
PTLogDebug(@"[DEBUG_PLAYBACK] Playback has started");
```
