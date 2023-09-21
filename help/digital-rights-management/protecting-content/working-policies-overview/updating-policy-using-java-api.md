---
title: Mise à jour d’une stratégie DRM avec l’API Java
description: Mise à jour d’une stratégie DRM avec l’API Java
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---

# Mise à jour d’une stratégie DRM avec l’API Java {#updating-a-drm-policy-with-the-java-api}

Pour mettre à jour une stratégie DRM avec l’API Java :

1. Configurez votre environnement de développement et incluez dans votre projet tous les fichiers JAR répertoriés dans [Configuration de l’environnement de développement](../../protecting-content/setting-up-the-sdk/setup-dev-env.md).
1. Création d’un DRM `Policy` et lisez la stratégie DRM d’un fichier ou d’une base de données.

   ```
   Policy policy = new Policy(policyBytes);
   ```

1. Mise à jour du DRM `Policy` en définissant ses propriétés, telles que son nom et ses règles d’utilisation.

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

1. Sérialiser le DRM mis à jour `Policy` et stockez-la dans un fichier ou une base de données.

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

Voir `com.adobe.flashaccess.samples.policy.UpdatePolicy` dans les outils de ligne de commande de mise en oeuvre de référence [!DNL samples] pour la source de cet exemple de code.
