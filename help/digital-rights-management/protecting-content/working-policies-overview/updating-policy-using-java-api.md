---
seo-title: Mise à jour d’une stratégie DRM avec l’API Java
title: Mise à jour d’une stratégie DRM avec l’API Java
uuid: ec21351c-900e-48f5-845a-c0b430c210d7
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Mise à jour d’une stratégie DRM avec l’API Java {#updating-a-drm-policy-with-the-java-api}

Pour mettre à jour une stratégie DRM avec l’API Java :

1. Configurez votre environnement de développement et incluez dans votre projet tous les fichiers JAR répertoriés dans [Configuration de l’environnement](../../protecting-content/setting-up-the-sdk/setup-dev-env.md)de développement.
1. Créez une `Policy` instance DRM et lisez la stratégie DRM à partir d’un fichier ou d’une base de données.

   ```
   Policy policy = new Policy(policyBytes);
   ```

1. Mettez à jour l’ `Policy` objet DRM en définissant ses propriétés, telles que son nom et ses règles d’utilisation.

   ```java
   // Change the DRM policy name.  
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

1. Sérialisez l’objet DRM mis à jour et stockez-le dans un fichier ou une base de données. `Policy`

   ```java
   // Serialize the DRM policy.  
   byte[] policyBytes = policy.getBytes();  
   System.out.println("New DRM policy revision number: "  
       +  policy.getRevision());      
   // Write the DRM policy to a file.   
   // Alternatively, the DRM policy may be stored in a database.  
   FileOutputStream out = new FileOutputStream("demopolicy-updated.pol");  
   out.write(policyBytes);  
   out.close();
   ```

Voir `com.adobe.flashaccess.samples.policy.UpdatePolicy` dans le répertoire Reference Implementation Command Line Tools [!DNL samples] pour connaître la source de cet exemple de code.
