---
seo-title: Mise à jour d’une stratégie à l’aide de l’API Java
title: Mise à jour d’une stratégie à l’aide de l’API Java
uuid: 23c50f05-799e-4f5a-869b-4b5e29a36ce1
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---


# Mise à jour d’une stratégie à l’aide de l’API Java {#updating-a-policy-using-the-java-api}

Pour mettre à jour une stratégie à l’aide de l’API Java, procédez comme suit :

1. Configurez votre environnement de développement et incluez tous les fichiers JAR mentionnés dans [Configuration de l&#39;environnement de développement](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md) dans votre projet.
1. Créez une instance `Policy` et lisez la stratégie à partir d&#39;un fichier ou d&#39;une base de données.

   ```
   Policy policy = new Policy(policyBytes);
   ```

1. Mettez à jour l&#39;objet `Policy` en définissant ses propriétés, telles que son nom et ses règles d&#39;utilisation.

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

1. Sérialisez l&#39;objet `Policy` mis à jour et stockez-le dans un fichier ou une base de données.

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

Pour obtenir la source complète de cet exemple de code, voir `com.adobe.flashaccess.samples.policy.UpdatePolicy` dans le répertoire Reference Implementation Command Line Tools &quot;samples&quot;.
