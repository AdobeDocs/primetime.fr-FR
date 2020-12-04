---
seo-title: Utilisation de l’outil Primetime Offline Packager inclus
title: Utilisation de l’outil Primetime Offline Packager inclus
uuid: 16b535a9-81b5-43bc-9e42-a64eb6649d9a
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---


# Utilisez l’outil Primetime Offline Packager inclus{#use-the-included-primetime-offline-packager}

Votre outil Primetime Java Packager est préconfiguré avec la plupart des paramètres nécessaires pour compresser le contenu. Il n&#39;y a que quelques zones à mettre à jour pour commencer.

## Mettre à jour les propriétés du package {#section_99904D35E99944A28FF43D924E516CC2}

Contexte de la tâche actuelle

* Mettez à jour les propriétés de packager suivantes avant d’utiliser le fichier de configuration pour regrouper votre contenu :

### Propriétés du fichier de configuration XML fourni par l’utilisateur

| Nom de la propriété | Description |
|---|---|
| `policy_file` | chemin d’accès au fichier de stratégie. L&#39;Adobe fournit plusieurs stratégies préconfigurées parmi lesquelles choisir. |
| `pkgr_pfx` | Chemin d’accès des informations d’identification de Packager. Vous devez fournir ici vos propres informations d’identification de packager émises par l’Adobe ( [!DNL .pfx]). |
| `pkgr_pfx_pwd` | Mot de passe des informations d’identification de Packager. Vous devez fournir le mot de passe à vos informations d’identification de packager émises par l’Adobe ici. |

## Package utilisant la ligne de commande {#section_DFBE462679E34D62963BE201FD3321F9}

Avant d’empaqueter le contenu, assurez-vous que toutes les informations requises sont fournies dans le fichier de configuration.

* Pour compresser le contenu avec votre fichier de configuration, utilisez la syntaxe suivante sur la ligne de commande :

```
java -jar OfflinePackager.jar -conf_path [configuration filename]
```

Des exemples de fichiers de configuration permettant d&#39;assembler votre contenu au format HLS ou HDS sont fournis, nommés [!DNL config_hds.xml] et [!DNL config.hls.xml].

Le contenu HDS ou HLS sera généré dans le dossier [!DNL /output] sous le répertoire du kit de protection. Tous les artefacts écrits dans ce répertoire doivent être hébergés sur un serveur Web HTTP pour être lus.
