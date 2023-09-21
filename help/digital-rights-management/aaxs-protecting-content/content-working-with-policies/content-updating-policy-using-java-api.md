---
title: Mise à jour d’une stratégie à l’aide de l’API Java
description: Mise à jour d’une stratégie à l’aide de l’API Java
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---

# Mise à jour d’une stratégie à l’aide de l’API Java {#updating-a-policy-using-the-java-api}

Pour mettre à jour une stratégie à l’aide de l’API Java, procédez comme suit :

1. Configurez votre environnement de développement et incluez tous les fichiers JAR mentionnés dans [Configuration de l’environnement de développement](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md) dans votre projet.
1. Créez un `Policy` et lisez dans la stratégie à partir d’un fichier ou d’une base de données.

   ```
   Policy policy = new Policy(policyBytes);
   ```

1. Mettez à jour le `Policy` en définissant ses propriétés, telles que son nom et ses règles d’utilisation.

   ```java
     // Change the policy name.  
     policy.setName("UpdatedDemoPolicy");  
   
     // Add DRM module restrictions to the play right  
     for (Right r: policy.getRights()) {  
      if (r instanceof PlayRight) {  
       PlayRight pr = (PlayRight) r;  
       // Disallow Linux versions up to and including 1.9.  Allow  
       // all other OSes and Linux versions above 1.9  
       VersionInfo toExclude = new VersionInfo();  
       toExclude.setOS("Linux");  
       toExclude.setReleaseVersion("1.9");  
       Collection<VersionInfo> exclusions = new ArrayList<VersionInfo>();  
       exclusions.add(toExclude);  
       ModuleRequirements drmRestrictions = new ModuleRequirements();  
       drmRestrictions.setExcludedVersions(exclusions);  
       pr.setDRMModuleRequirements(drmRestrictions);  
       break;  
      }  
     }
   ```

1. Sérialiser la mise à jour `Policy` et stockez-la dans un fichier ou une base de données.

   ```java
      // Serialize the policy.  
      byte[] policyBytes = policy.getBytes();  
      System.out.println("New policy revision number: "  
       +  policy.getRevision());      
      // Write the policy to a file.   
      // Alternatively, the policy may be stored in a database.  
      FileOutputStream out = new FileOutputStream("demopolicy-updated.pol");  
      out.write(policyBytes);  
      out.close(); 
   ```

Pour obtenir la source complète de cet exemple de code, voir `com.adobe.flashaccess.samples.policy.UpdatePolicy` dans le répertoire &quot;Exemples&quot; des outils de ligne de commande de mise en oeuvre de référence.
