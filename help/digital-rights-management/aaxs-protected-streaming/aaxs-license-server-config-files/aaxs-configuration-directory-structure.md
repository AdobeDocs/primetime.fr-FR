---
description: 'L’Adobe Access Server for Protected Streaming nécessite deux types de fichiers de configuration : un fichier de configuration global (flashaccess-global.xml) et un fichier de configuration de client pour chaque client (flashaccess-locataire.xml).'
title: Structure d'annuaire de configuration
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# Fichiers de configuration du serveur de licences et structure du répertoire de configuration {#configuration-directory-structure}

L’Adobe Access Server for Protected Streaming nécessite deux types de fichiers de configuration : un fichier de configuration global (flashaccess-global.xml) et un fichier de configuration de client pour chaque client (flashaccess-locataire.xml).

Après avoir modifié les fichiers de configuration, l’Adobe recommande d’utiliser les utilitaires fournis avec l’Adobe Access Server for Protected Streaming pour vérifier que les fichiers sont bien formés. Pour plus d’informations, voir &quot;[Configuration Validator](../../aaxs-protected-streaming/aaxs-protected-streaming-utilities/configuration-validator.md)&quot;.

Pour éviter de rendre les mots de passe disponibles en texte clair dans les fichiers de configuration, tous les mots de passe spécifiés dans les fichiers de configuration globale et locataire doivent être chiffrés. Pour plus d&#39;informations sur le chiffrement des mots de passe, consultez &quot;[Mot de passe Scrambler](../../aaxs-protected-streaming/aaxs-protected-streaming-utilities/password-scrambler.md)&quot;.

Les répertoires de configuration ont la structure suivante :

```
<i class="+ topic ph hi-d="" i "="">
  LicenseServer.ConfigRoot/  
  flashaccess-global.xml  
  pkcs11.cfg (optional)  
  flashaccessserver/  
   libs/ (optional)  
   tenants/  
     
 <i class="+ topic ph hi-d="" i "="">
   tenantname/  
      flashaccess-tenant.xml  
       
  <i class="+ topic ph hi-d="" i "="">
    credential.pfx (optional)  
        
   <i class="+ topic ph hi-d="" i "="">
     packagercert.cer (optional) 
   </i class="+ topic> 
  </i class="+ topic> 
 </i class="+ topic> 
</i class="+ topic>
```

