---
seo-title: Utilisation de Primetime Offline Packager inclus
title: Utilisation de Primetime Offline Packager inclus
uuid: 16b535a9-81b5-43bc-9e42-a64eb6649d9a
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Utilisation de Primetime Offline Packager inclus{#use-the-included-primetime-offline-packager}

Votre outil Primetime Java Packager est préconfiguré avec la plupart des paramètres dont vous avez besoin pour compresser le contenu. Il n&#39;y a que quelques zones à mettre à jour pour commencer.

## Mettre à jour les propriétés du gestionnaire de package {#section_99904D35E99944A28FF43D924E516CC2}

Contexte de l&#39; actuel

* Mettez à jour les propriétés du gestionnaire de package suivantes avant d’utiliser le fichier de configuration pour compresser votre contenu :

### Propriétés du fichier de configuration XML fourni par l’utilisateur

| Nom de la propriété | Description |
|---|---|
| `policy_file` | chemin d’accès au fichier de stratégie. Adobe fournit plusieurs stratégies préconfigurées parmi lesquelles choisir. |
| `pkgr_pfx` | Chemin d’accès des informations d’identification du gestionnaire de package. Vous devez fournir ici vos propres informations d’identification de packager émises par Adobe ( [!DNL .pfx]). |
| `pkgr_pfx_pwd` | Mot de passe des informations d’identification du gestionnaire de package. Vous devez fournir le mot de passe à vos informations d’identification de Packager émises par Adobe ici. |

## Package à l’aide de la ligne de commande {#section_DFBE462679E34D62963BE201FD3321F9}

Avant de compresser le contenu, assurez-vous que toutes les informations requises sont fournies dans le fichier de configuration.

* Pour compresser le contenu avec votre fichier de configuration, utilisez la syntaxe suivante sur la ligne de commande :

```
java -jar OfflinePackager.jar -conf_path [configuration filename]
```

Des exemples de fichiers de configuration permettant d’assembler votre contenu au format HLS ou HDS sont fournis, nommés [!DNL config_hds.xml] et [!DNL config.hls.xml].

Le contenu HDS ou HLS sera généré dans le [!DNL /output] dossier sous le répertoire du kit de protection. Tous les artefacts écrits dans ce répertoire doivent être hébergés sur un serveur Web HTTP pour pouvoir être lus.
