---
seo-title: Création d’une stratégie à l’aide de l’API Java
title: Création d’une stratégie à l’aide de l’API Java
uuid: c653548d-4abf-46b9-8669-d68b966da359
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Création d’une stratégie à l’aide de l’API Java {#creating-a-policy-using-the-java-api}

Pour créer une stratégie à l’aide de l’API Java, procédez comme suit :

1. Configurez votre  de développement   et incluez tous les fichiers JAR mentionnés dans [Configuration du](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md) de développement  dans votre projet.
1. Créez un `com.adobe.flashaccess.sdk.policy.Policy` objet et spécifiez ses propriétés, telles que les droits, la durée de mise en cache de la licence et la date de fin de la stratégie.

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

1. Sérialisez l’ `Policy` objet et stockez-le dans un fichier ou une base de données.

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

Pour obtenir la source complète de cet exemple de code, voir *com.adobe.flashaccess.samples.policy.CreatePolicy* dans le répertoire &quot; [!DNL samples]&quot; des outils de ligne de commande d’implémentation des références.
