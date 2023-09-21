---
description: Adobe recommande que si vous apportez des modifications au fichier de configuration, vous exécutiez l’utilitaire Configuration Validator avant de démarrer le serveur. Cet utilitaire peut détecter la plupart des erreurs de configuration plus tôt, avant qu’elles ne provoquent des échecs lors du traitement des demandes.
title: Validateur de configuration
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# Validateur de configuration{#configuration-validator}

Adobe recommande que si vous apportez des modifications au fichier de configuration, vous exécutiez l’utilitaire Configuration Validator avant de démarrer le serveur. Cet utilitaire peut détecter la plupart des erreurs de configuration plus tôt, avant qu’elles ne provoquent des échecs lors du traitement des demandes.

Pour exécuter le programme de validation, saisissez :

```
Validator.bat  
<i class="+ topic ph hi-d="" i "="">
  options  
</i class="+ topic>
```

ou

```
java -jar libs/flashaccess-validator.jar  
<i class="+ topic ph hi-d="" i "="">
  options 
</i class="+ topic>
```

Pour chacun des fichiers de configuration du serveur de licences, le programme de validation peut effectuer une validation basée sur les fichiers, ce qui garantit que le fichier XML est correctement formé et conforme au schéma du fichier de configuration.

Pour effectuer une validation basée sur un fichier sur le fichier de configuration global, saisissez :

```
Validator --<file path>/flashaccess-global.xml --global
```

Pour effectuer une validation basée sur un fichier sur le fichier de configuration du client, saisissez :

```
Validator --<file path>/flashaccess-tenant.xml --tenant
```

La validation peut également effectuer une validation basée sur le déploiement. En plus de vérifier la conformité avec le schéma, ce niveau de validation vérifie également que les valeurs que vous avez spécifiées sont valides. Par exemple, il garantit que les fichiers référencés existent.

La validation basée sur le déploiement peut être effectuée aux niveaux suivants :

* `Tenant` — Valide le fichier de configuration et les informations d’identification d’un client spécifique. Si vous souhaitez valider la configuration pour `<tenant1>`, saisissez :

  ```
      Validator --<root-path-to-LicenseServer.ConfigRoot> -d flashaccessserver/tenant1 -t
  ```

* `Global` — Valide le fichier de configuration global et la validation du client pour tous les clients. Si vous souhaitez effectuer une validation globale basée sur le déploiement, saisissez :

  ```
      Validator --<root-path-to-LicenseServer.ConfigRoot> -g
  ```
