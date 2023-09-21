---
description: Les fichiers journaux générés par le serveur DRM Adobe Primetime pour l’application de diffusion en continu protégée se trouvent dans le répertoire spécifié par LicenseServer.LogRoot.
title: Fichiers de log
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# Fichiers de log{#log-files}

Les fichiers journaux générés par le serveur DRM Adobe Primetime pour l’application de diffusion en continu protégée se trouvent dans le répertoire spécifié par LicenseServer.LogRoot.

>[!NOTE]
>
>Si les fichiers journaux actuels sont supprimés ou déplacés pendant l’exécution du serveur, il est possible que le fichier journal ne soit pas recréé. Par conséquent, certaines informations de journal peuvent être supprimées.

## Structure du répertoire de journal {#section_F490A483D60145ADBC21038914C39203}

Les répertoires de logs sont structurés pour faciliter leur utilisation. Le répertoire des journaux présente la structure suivante :

```
<i class="+ topic ph hi-d="" i "="">
 LicenseServer.LogRoot/ 
 flashaccess-global.log 
     flashaccessserver/ 
         flashaccess-partition.log 
         tenants/ 
             
 <i class="+ topic ph hi-d="" i "="">
  tenantname/ 
                  flashaccess-tenant.log
 </i class="+ topic>
</i class="+ topic>
```

## Fichier journal global {#section_1CFA90748142439C9F3BE380969539DA}

Le fichier journal global, `flashaccess-global.log`, se trouve dans *LicenseServer.LogRoot*. Le journal peut inclure des messages de journal générés par le SDK Java DRM d’Adobe Primetime ou des messages de journal pendant l’initialisation du serveur.

## Fichier journal de partition {#section_5660137CD6AA40519E72A4315534846B}

Le fichier journal de la partition, `flashaccess-partition.log`, se trouve dans la variable `<LicenseServer.LogRoot>/flashaccesserver` répertoire . Il inclut les messages de journal qui ont été générés pendant le traitement d’une demande de licence.

## Fichier journal du client {#section_F0257CC0831647F18A746B4F02E3E910}

le fichier journal du client de chaque client, `flashaccess-tenant.log`, se trouve dans `<LicenseServer.LogRoot>/flashaccesserver/tenants/<tenantname>`. Le journal du client comprend des informations d’audit qui décrivent chaque licence générée pour ce client.
