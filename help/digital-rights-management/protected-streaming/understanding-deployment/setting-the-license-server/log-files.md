---
description: Les fichiers journaux générés par le serveur DRM d’Adobe Primetime pour l’application de diffusion en flux continu protégée se trouvent dans le répertoire spécifié par LicenseServer.LogRoot.
seo-description: Les fichiers journaux générés par le serveur DRM d’Adobe Primetime pour l’application de diffusion en flux continu protégée se trouvent dans le répertoire spécifié par LicenseServer.LogRoot.
seo-title: Fichiers journaux
title: Fichiers journaux
uuid: 4498fe60-65af-4f99-8f9b-e85013d0c9e9
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Fichiers journaux{#log-files}

Les fichiers journaux générés par le serveur DRM d’Adobe Primetime pour l’application de diffusion en flux continu protégée se trouvent dans le répertoire spécifié par LicenseServer.LogRoot.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Si les fichiers journaux actuels sont supprimés ou déplacés pendant l&#39;exécution du serveur, il est possible que le fichier journal ne soit pas recréé. Par conséquent, certaines informations de journal peuvent être supprimées.

## Structure du répertoire de journalisation {#section_F490A483D60145ADBC21038914C39203}

Les répertoires de journaux sont structurés pour faciliter leur utilisation. Le répertoire des journaux possède la structure suivante :

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

Le fichier journal global [!DNL flashaccess-global.log]se trouve dans *LicenseServer.LogRoot*. Le journal peut inclure des messages journaux que le SDK Java DRM d’Adobe Primetime ou des messages journaux peuvent avoir générés pendant l’initialisation du serveur.

## Fichier journal de partition {#section_5660137CD6AA40519E72A4315534846B}

Le fichier journal des partitions [!DNL flashaccess-partition.log]se trouve dans le [!DNL <LicenseServer.LogRoot>/flashaccesserver] répertoire. Il comprend les messages du journal qui ont été générés pendant le traitement d’une demande de licence.

## Fichier journal du client {#section_F0257CC0831647F18A746B4F02E3E910}

Le fichier journal de chaque client, [!DNL flashaccess-tenant.log], se trouve dans [!DNL &lt;LicenseServer.LogRoot>/flashaccesserver/locants/<tenantname>]. Le journal du client contient des informations de contrôle décrivant chaque licence générée pour ce client.
