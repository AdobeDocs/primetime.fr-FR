---
title: Validation de configuration
description: Validation de configuration
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# Validation de configuration {#configuration-validator}

Adobe recommande d’exécuter l’utilitaire de validation de configuration avant de démarrer le serveur à chaque modification apportée au fichier de configuration. Cet utilitaire peut détecter la plupart des erreurs de configuration plus tôt, avant qu’elles ne provoquent des échecs lors du traitement des demandes.

Pour exécuter le programme de validation, utilisez la commande :

```
Validator.bat options  
```

ou la commande :

```
java -jar libs/flashaccess-validator.jar options 
```

Pour chacun des fichiers de configuration du serveur de licences, le programme de validation peut effectuer une validation basée sur les fichiers, ce qui garantit que le fichier XML est correctement formé et conforme au schéma du fichier de configuration. Pour effectuer une validation basée sur un fichier sur le fichier de configuration global, exécutez la commande :

```
Validator --file path/flashaccess-global.xml --global
```

Pour effectuer une validation basée sur un fichier sur le fichier de configuration du client, exécutez la commande :

```
Validator --file path/flashaccess-tenant.xml --tenant
```

L’outil de validation peut également effectuer une validation basée sur le déploiement. En plus de vérifier la conformité avec le schéma, ce niveau de validation vérifie également que les valeurs spécifiées sont valides (par exemple, il s’assure que les fichiers référencés existent). La validation basée sur le déploiement peut être effectuée à deux niveaux :

* Client : valide le fichier de configuration et les informations d’identification d’un client spécifique. Pour valider la configuration de &quot;tenant1&quot;, exécutez la commande :

```
Validator --root-path-to-LicenseServer.ConfigRoot -d flashaccessserver/tenant1 -t 
```

* Global : valide le fichier de configuration global et la validation du client pour tous les clients. Pour effectuer une validation globale basée sur le déploiement, exécutez la commande :

```
Validator --root-path-to-LicenseServer.ConfigRoot -g 
```
