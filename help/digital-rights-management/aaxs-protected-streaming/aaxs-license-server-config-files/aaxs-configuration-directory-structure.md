---
description: 'Adobe Access Server for Protected Streaming requiert deux types de fichiers de configuration : un fichier de configuration global (flashaccess-global.xml) et un fichier de configuration de client pour chaque client (flashaccess-locataire.xml).'
seo-description: 'Adobe Access Server for Protected Streaming requiert deux types de fichiers de configuration : un fichier de configuration global (flashaccess-global.xml) et un fichier de configuration de client pour chaque client (flashaccess-locataire.xml).'
seo-title: Structure d'annuaire de configuration
title: Structure d'annuaire de configuration
uuid: c6cfc734-6b7c-4502-9bdb-c7aaca156e0e
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Fichiers de configuration du serveur de licences et structure du répertoire de configuration {#configuration-directory-structure}

Adobe Access Server for Protected Streaming requiert deux types de fichiers de configuration : un fichier de configuration global (flashaccess-global.xml) et un fichier de configuration de client pour chaque client (flashaccess-locataire.xml).

Après avoir modifié les fichiers de configuration, Adobe recommande d’utiliser les utilitaires fournis avec Adobe Access Server for Protected Streaming pour vérifier que les fichiers sont bien formés. Pour plus d’informations, voir &quot;[Configuration Validator](../../aaxs-protected-streaming/aaxs-protected-streaming-utilities/configuration-validator.md)&quot;.

Pour éviter de rendre les mots de passe disponibles en texte clair dans les fichiers de configuration, tous les mots de passe spécifiés dans les fichiers de configuration globale et locataire doivent être chiffrés. Pour plus d’informations sur le chiffrement des mots de passe, voir &quot;[Password Scrambler](../../aaxs-protected-streaming/aaxs-protected-streaming-utilities/password-scrambler.md)&quot; (Paramètre de saisie de mot de passe).

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

