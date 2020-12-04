---
seo-title: Validation de configuration
title: Validation de configuration
uuid: 60ebd35c-290a-4f08-9bd0-178903857149
translation-type: tm+mt
source-git-commit: 47b2ed65ff0ea4f54a210cf7627ed535782296b9
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---


# Validation de configuration {#configuration-validator}

Adobe recommande d’exécuter l’utilitaire Configuration Validator avant de démarrer le serveur chaque fois que des modifications sont apportées au fichier de configuration. Cet utilitaire peut détecter la plupart des erreurs de configuration plus tôt, avant qu’elles ne provoquent des erreurs lors du traitement de la demande.

Pour exécuter la validation, utilisez la commande :

```
Validator.bat options  
```

ou la commande :

```
java -jar libs/flashaccess-validator.jar options 
```

Pour chacun des fichiers de configuration du serveur de licences, le programme de validation peut effectuer une validation basée sur des fichiers, ce qui garantit que le fichier XML est bien formé et conforme au schéma de fichiers de configuration. Pour effectuer une validation basée sur des fichiers sur le fichier de configuration global, exécutez la commande :

```
Validator --file path/flashaccess-global.xml --global
```

Pour effectuer une validation basée sur des fichiers sur le fichier de configuration du client, exécutez la commande :

```
Validator --file path/flashaccess-tenant.xml --tenant
```

Le validateur peut également effectuer une validation basée sur le déploiement ; en plus de vérifier la conformité avec le schéma, ce niveau de validation vérifie également que les valeurs spécifiées sont valides (par exemple, il s’assure que les fichiers référencés existent). La validation basée sur le déploiement peut être effectuée à deux niveaux :

* Client : valide le fichier de configuration et les informations d&#39;identification d&#39;un client spécifique. Pour valider la configuration de &quot;client1&quot;, exécutez la commande :

```
Validator --root-path-to-LicenseServer.ConfigRoot -d flashaccessserver/tenant1 -t 
```

* Global — Valide le fichier de configuration global et la validation des locataires pour tous les locataires. Pour effectuer une validation globale basée sur le déploiement, exécutez la commande :

```
Validator --root-path-to-LicenseServer.ConfigRoot -g 
```

