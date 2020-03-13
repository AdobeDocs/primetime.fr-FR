---
seo-title: Données de configuration du serveur global
title: Données de configuration du serveur global
uuid: f6d6cb01-2645-4cd2-83ec-0272323a67cd
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Données de configuration du serveur global{#global-server-configuration-data}

Outre la configuration utilisée par le serveur de licences, `HandlerConfiguration` stocke les informations de configuration qui peuvent être envoyées au client pour contrôler la manière dont les licences sont appliquées. Pour ce faire, créez une `ServerConfigData` classe et appelez `HandlerConfiguration.setServerConfigData()` (ces paramètres s’appliquent uniquement aux licences délivrées par ce serveur de licences). La tolérance au vent de l’horloge est une propriété qui peut être définie par le serveur de licences pour contrôler la manière dont le client applique les licences. Par défaut, les utilisateurs peuvent redéfinir l’horloge de leur ordinateur sur 4 heures sans invalider les licences. Si un opérateur de serveur de licences souhaite utiliser un paramètre différent, la nouvelle valeur peut être définie dans la `ServerConfigData` classe. Lorsque vous modifiez la valeur de l’un de ces paramètres, veillez à incrémenter le numéro de version en appelant `setVersion()`. Les nouvelles valeurs ne sont envoyées au client que si la version sur le client est inférieure à la `ServerConfigData` version actuelle.
