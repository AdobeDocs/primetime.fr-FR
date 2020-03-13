---
description: Adobe recommande que si vous apportez des modifications au fichier de configuration, vous exécutiez l’utilitaire Configuration Validator avant de  le serveur. Cet utilitaire peut détecter la plupart des erreurs de configuration plus tôt, avant qu’elles ne provoquent des erreurs lors du traitement de la demande.
seo-description: Adobe recommande que si vous apportez des modifications au fichier de configuration, vous exécutiez l’utilitaire Configuration Validator avant de  le serveur. Cet utilitaire peut détecter la plupart des erreurs de configuration plus tôt, avant qu’elles ne provoquent des erreurs lors du traitement de la demande.
seo-title: Validateur de configuration
title: Validateur de configuration
uuid: 7b44919a-0319-4675-95e2-ad1ad72ec0cb
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Validateur de configuration{#configuration-validator}

Adobe recommande que si vous apportez des modifications au fichier de configuration, vous exécutiez l’utilitaire Configuration Validator avant de  le serveur. Cet utilitaire peut détecter la plupart des erreurs de configuration plus tôt, avant qu’elles ne provoquent des erreurs lors du traitement de la demande.

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

Pour chacun des fichiers de configuration du serveur de licences, le programme de validation peut effectuer une validation basée sur des fichiers, ce qui garantit que le fichier XML est bien formé et conforme au de fichiers de configuration.

Pour effectuer une validation basée sur des fichiers sur le fichier de configuration global, saisissez:

```
Validator --<file path>/flashaccess-global.xml --global
```

Pour effectuer une validation basée sur des fichiers sur le fichier de configuration du client, saisissez:

```
Validator --<file path>/flashaccess-tenant.xml --tenant
```

Le programme de validation peut également effectuer une validation basée sur le déploiement. Outre la vérification de la conformité avec le  de, ce niveau de validation vérifie également que les valeurs que vous avez spécifiées sont valides. Par exemple, il s’assure que les fichiers référencés existent.

La validation basée sur le déploiement peut être effectuée aux niveaux suivants :

* `Tenant` — Valide le fichier de configuration et les informations d’identification d’un client spécifique. Si vous souhaitez valider la configuration pour `<tenant1>`, saisissez :

   ```
       Validator --<root-path-to-LicenseServer.ConfigRoot> -d flashaccessserver/tenant1 -t
   ```

* `Global` — Valide le fichier de configuration global et la validation des locataires pour tous les locataires. Si vous souhaitez effectuer une validation globale basée sur un déploiement, saisissez :

   ```
       Validator --<root-path-to-LicenseServer.ConfigRoot> -g
   ```

