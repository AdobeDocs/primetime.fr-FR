---
title: Données de configuration du serveur global
description: Données de configuration du serveur global
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---


# Données de configuration du serveur global{#global-server-configuration-data}

Outre la configuration utilisée par le serveur de licences, `HandlerConfiguration` stocke les informations de configuration qui peuvent être envoyées au client pour contrôler la manière dont les licences sont appliquées. Pour ce faire, créez une classe `ServerConfigData` et appelez `HandlerConfiguration.setServerConfigData()`. Ces paramètres s’appliquent uniquement aux licences délivrées par ce serveur de licences.

La tolérance au retour à l’arrière-plan de l’horloge est une propriété qui peut être définie par le serveur de licences pour contrôler comment le client applique les licences. Par défaut, les utilisateurs peuvent redéfinir l’horloge de leur ordinateur sur 4 heures sans invalider les licences. Si un opérateur de serveur de licences souhaite utiliser un paramètre différent, la nouvelle valeur peut être définie dans la classe `ServerConfigData`. Lorsque vous modifiez la valeur de l&#39;un de ces paramètres, veillez à incrémenter le numéro de version en appelant `setVersion()`. Les nouvelles valeurs ne sont envoyées au client que si la version du client est antérieure à la version actuelle `ServerConfigData`.
