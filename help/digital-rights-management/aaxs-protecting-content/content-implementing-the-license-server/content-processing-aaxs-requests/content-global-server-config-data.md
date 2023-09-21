---
title: Données de configuration du serveur global
description: Données de configuration du serveur global
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---

# Données de configuration du serveur global{#global-server-configuration-data}

En plus de la configuration utilisée par le serveur de licences, `HandlerConfiguration` stocke des informations de configuration qui peuvent être envoyées au client pour contrôler la manière dont les licences sont appliquées. Pour ce faire, créez une `ServerConfigData` classe et appel `HandlerConfiguration.setServerConfigData()` (ces paramètres s’appliquent uniquement aux licences délivrées par ce serveur de licences). La tolérance au vent arrière est une propriété qui peut être définie par le serveur de licences pour contrôler la manière dont le client applique les licences. Par défaut, les utilisateurs peuvent redéfinir l’horloge de leur ordinateur sur 4 heures sans invalider les licences. Si un opérateur de serveur de licences souhaite utiliser un autre paramètre, la nouvelle valeur peut être définie dans la variable `ServerConfigData` classe . Lorsque vous modifiez la valeur de l’un de ces paramètres, veillez à incrémenter le numéro de version en appelant `setVersion()`. Les nouvelles valeurs ne sont envoyées au client que si la version du client est inférieure à la version actuelle. `ServerConfigData` version.
