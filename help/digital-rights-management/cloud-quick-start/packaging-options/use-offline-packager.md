---
title: Utilisation de l’outil Primetime Offline Packager inclus
description: Utilisation de l’outil Primetime Offline Packager inclus
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# Utilisation de l’outil Primetime Offline Packager inclus{#use-the-included-primetime-offline-packager}

Votre Primetime Java Packager est préconfiguré avec la plupart des paramètres dont vous avez besoin pour compresser le contenu. Il n’y a que quelques zones à mettre à jour pour commencer.

## Mise à jour des propriétés du module {#section_99904D35E99944A28FF43D924E516CC2}

Contexte de la tâche en cours

* Mettez à jour les propriétés de package suivantes avant d’utiliser le fichier de configuration pour empaqueter votre contenu :

### Propriétés du fichier de configuration XML fourni par l’utilisateur

| Nom de la propriété | Description |
|---|---|
| `policy_file` | chemin d’accès au fichier de stratégie. Adobe doit fournir plusieurs stratégies préconfigurées parmi lesquelles choisir. |
| `pkgr_pfx` | Chemin d’accès des informations d’identification du Packager. Vous devez fournir vos propres informations d’identification de packager délivrées par l’Adobe ( [!DNL .pfx]) ici. |
| `pkgr_pfx_pwd` | Mot de passe des informations d’identification du gestionnaire de paquets. Vous devez fournir le mot de passe à vos informations d’identification de packager délivrées par l’Adobe ici. |

## Module à l’aide de la ligne de commande {#section_DFBE462679E34D62963BE201FD3321F9}

Avant de grouper le contenu, assurez-vous que toutes les informations requises sont fournies dans le fichier de configuration.

* Pour empaqueter le contenu avec votre fichier de configuration, utilisez la syntaxe suivante sur la ligne de commande :

```
java -jar OfflinePackager.jar -conf_path [configuration filename]
```

Des exemples de fichiers de configuration pour compresser votre contenu au format HLS ou HDS sont fournis, nommés [!DNL config_hds.xml] et [!DNL config.hls.xml].

Le contenu HDS ou HLS est généré dans la [!DNL /output] sous le répertoire du kit de protection. Tous les artefacts écrits dans ce répertoire doivent être hébergés sur un serveur web HTTP pour être lus.
