---
title: Création d’une stratégie à l’aide de l’API Java
description: Création d’une stratégie à l’aide de l’API Java
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---

# Création d’une stratégie à l’aide de l’API Java {#creating-a-policy-using-the-java-api}

Pour créer une stratégie à l’aide de l’API Java, procédez comme suit :

1. Configurez votre environnement de développement et incluez tous les fichiers JAR mentionnés dans [Configuration de l’environnement de développement](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md) dans votre projet.
1. Créez un `com.adobe.flashaccess.sdk.policy.Policy` et spécifiez ses propriétés, telles que les droits, la durée de mise en cache de la licence et la date de fin de la stratégie.

   ```java
     // Create a new Policy object.  
     // False indicates the policy does not use license chaining.  
     Policy policy = new Policy(false);  
   
     policy.setName("DemoPolicy");  
   
     // Specify that the policy requires authentication to obtain a license.  
     policy.setLicenseServerInfo  
      (new LicenseServerInfo(AuthenticationType.UsernamePassword));  
   
     // A policy must have at least one Right, typically the play right  
     PlayRight play = new PlayRight();  
   
     // Users may only view content for 24 hours.  
     play.setPlaybackWindow(24L * 60 * 60);  
   
     // Add the play right to the policy.  
     List<Right> rightsList = new ArrayList<Right>();  
     rightsList.add(play);  
     policy.setRights(rightsList);  
   
     // Licenses may be stored on the client for 7 days after downloading  
     policy.setLicenseCachingDuration(7L * 24 * 60 * 60);  
     try {  
      // Content will expire December 31, 2010  
      SimpleDateFormat dateFormat = new SimpleDateFormat("yyyy-MM-dd");  
      policy.setPolicyEndDate(dateFormat.parse("2010-12-31"));  
     } catch (ParseException e) {  
      // Invalid date specified in dateFormat.parse()  
      e.printStackTrace();  
     }
   ```

1. Sérialisez la variable `Policy` et stockez-la dans un fichier ou une base de données.

   ```java
     // Serialize the policy  
     byte[] policyBytes = policy.getBytes();  
     System.out.println("Created policy with ID: " + policy.getId());  
   
     // Write the policy to a file.   
     // Alternatively, the policy may be stored in a database.  
     FileOutputStream out = new FileOutputStream("demopolicy.pol");  
     out.write(policyBytes);  
     out.close();
   ```

Pour obtenir la source complète de cet exemple de code, voir *com.adobe.flashaccess.samples.policy.CreatePolicy* dans les outils de ligne de commande de mise en oeuvre de référence &quot; [!DNL samples]&quot;.
