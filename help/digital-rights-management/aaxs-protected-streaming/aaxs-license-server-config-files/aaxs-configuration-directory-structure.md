---
description: 'Adobe Access Server for Protected Streaming requiert deux types de fichiers de configuration : un fichier de configuration global (flashaccess-global.xml) et un fichier de configuration client pour chaque client (flashaccess-tenant.xml).'
title: Structure du répertoire de configuration
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# Fichiers de configuration du serveur de licences et structure du répertoire de configuration {#configuration-directory-structure}

Adobe Access Server for Protected Streaming requiert deux types de fichiers de configuration : un fichier de configuration global (flashaccess-global.xml) et un fichier de configuration client pour chaque client (flashaccess-tenant.xml).

Après avoir modifié les fichiers de configuration, Adobe recommande d’utiliser les utilitaires fournis avec Adobe Access Server for Protected Streaming pour vérifier que les fichiers sont bien formés. Pour plus d’informations, voir &quot;[Validation de configuration](../../aaxs-protected-streaming/aaxs-protected-streaming-utilities/configuration-validator.md)&quot;.

Pour éviter de rendre les mots de passe disponibles en texte clair dans les fichiers de configuration, tous les mots de passe spécifiés dans les fichiers de configuration globale et client doivent être chiffrés. Pour plus d’informations sur le chiffrement des mots de passe, voir &quot;[Scrambler de mot de passe](../../aaxs-protected-streaming/aaxs-protected-streaming-utilities/password-scrambler.md)&quot;.

Les répertoires de configuration présentent la structure suivante :

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
