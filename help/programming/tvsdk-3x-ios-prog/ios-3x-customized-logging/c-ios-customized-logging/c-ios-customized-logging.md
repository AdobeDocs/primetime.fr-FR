---
description: Vous pouvez mettre en oeuvre votre propre système de journalisation.
seo-description: Vous pouvez mettre en oeuvre votre propre système de journalisation.
seo-title: Présentation de la journalisation personnalisée
title: Présentation de la journalisation personnalisée
uuid: f056d7d7-ec3a-4cf1-997f-72a89bbc9447
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Journalisation personnalisée {#customized-logging}

Vous pouvez mettre en oeuvre votre propre système de journalisation.

Outre la journalisation à l’aide de notifications prédéfinies, vous pouvez mettre en oeuvre un système de journalisation qui utilise vos messages et messages journaux générés par TVSDK. Pour plus d’informations sur les notifications prédéfinies, voir [Le système](https://help.adobe.com/en_US/primetime/psdk/ios/index.html#PSDKs-concept-The_Notification_System)de notification. Vous pouvez utiliser ces journaux pour résoudre les problèmes de vos applications de lecteur et pour mieux comprendre le flux de lecture et de publicité.

La journalisation personnalisée utilise une instance singleton partagée du `PSDKPTLogFactory`, qui fournit un mécanisme pour consigner les messages à plusieurs journaux. Vous définissez et ajoutez (enregistrez) un ou plusieurs journaux de journalisation au `PTLogFactory`. Cela vous permet de définir plusieurs journaux avec des implémentations personnalisées, comme un journal de console, un journal Web ou un journal d&#39;historique de console.

TVSDK génère des messages de journal pour la plupart de ses activités, que les `PTLogFactory` transmettent à tous les journaliseurs enregistrés. Votre application peut également générer des messages de journal personnalisés, qui sont transférés à tous les journaux enregistrés. Chaque journal peut filtrer les messages et prendre les mesures appropriées.

Il existe deux implémentations pour `PTLogFactory`:

* Pour l’écoute des journaux.
* Pour ajouter des journaux à un `PTLogFactory`journal.

## Écoute des journaux {#listen-to-logs}

Pour vous inscrire pour écouter les journaux :
1. Implémentez une classe personnalisée qui suit le protocole `PTLogger`:

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

1. Pour enregistrer l&#39;instance pour recevoir les entrées de journalisation, ajoutez une instance du `PTLogger` au `PTLoggerFactory`:

   ```
   PTConsoleLogger *logger = [PTConsoleLogger consoleLogger]; 
   // Either use the addLogger method: 
   [[PTLogFactory sharedInstance] addLogger:(logger)] 
   
   //Or replace the preceding line with this macro for ease of use 
   //PTLogAddLogger(logger); 
   ```

<!--<a id="example_3738B5A8B4C048D28695E62297CF39E3"></a>-->

Voici un exemple de filtrage des journaux en utilisant le `PTLogEntry` type :

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

## Ajouter nouveaux messages du journal {#add-new-log-messages}

Pour vous inscrire pour écouter les journaux :

Créez un nouveau fichier `PTLogEntry` et ajoutez-le à `thePTLogFactory`:

Vous pouvez instancier manuellement une `PTLogEntry` instance et l’ajouter à l’instance `PTLogFactory` partagée ou utiliser l’une des macros pour accomplir la même tâche.

Voici un exemple de journalisation à l’aide de la `PTLogDebug` macro :

<!--<a id="example_F014436E1686468F941F4EBD1A21B18E"></a>-->

```
// The following line creates an instance of PTLogEntry with type PTLogEntryDebug, 
// tag "DEBUG_PLAYBACK", and message "Playback has started". 
// Then the PTLogEntry is automatically added to the PTLogFactory  
 
PTLogDebug(@"[DEBUG_PLAYBACK] Playback has started");
```
