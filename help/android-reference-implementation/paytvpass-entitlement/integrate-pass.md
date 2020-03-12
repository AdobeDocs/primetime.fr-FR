---
description: Personnalisez votre implémentation de référence pour intégrer l’authentification Adobe Primetime à vos  de  de production.
seo-description: Personnalisez votre implémentation de référence pour intégrer l’authentification Adobe Primetime à vos  de  de production.
seo-title: Intégration de l’authentification Primetime
title: Intégration de l’authentification Primetime
uuid: 34cdf1da-261e-462c-a194-4fcb439e5dfb
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Intégration de l’authentification Primetime {#integrate-primetime-authentication}

Personnalisez votre implémentation de référence pour intégrer l’authentification Adobe Primetime à vos  de  de production.

L’intégration de l’implémentation de référence du service d’authentification Primetime fonctionne de manière prête à l’emploi comme une démonstration. Toutefois, pour utiliser l’intégration dans un lecteur prêt à la production, vous devez implémenter les personnalisations suivantes :

1. Activez ou désactivez les flux de droits.

   Le `EntitlementManager` doit d’abord initialiser et obtenir une instance du SDK d’authentification Primetime pour être activé. Si la bibliothèque `EntitlementManager` n’est pas initialisée, le gestionnaire est désactivé.
1. Activez le `EntitlementManger`, à partir de votre classe d’applications principale :

   ```java
   // initialize the AccessEnabler library, required for Primetime PayTV Pass entitlement workflows 
   EntitlementManager.initializeAccessEnabler(this); // comment out this line to disable entitlement workflows
   ```

1. Utilisez la `ManagerFactory` classe pour obtenir une instance de la `EntitlementManager`.

   Vous devez toujours utiliser le `ManagerFactory` pour obtenir une instance du `EntitlementManager`, car `ManagerFactory` le gère une instance unique de EntitlementManager pour votre application. N’instanciez jamais les classes `EntitlementManager` ou `EntitlementManagerOn` en utilisant leurs constructeurs.

   ```java
   EntitlementManager entitlementManager =  
   ManagerFactory.getEntitlementManager();
   ```

   Le `ManagerFactory` renvoie une instance de `EntitlementManagerOn`, avec les flux de droits activés, si vous avez déjà appelé `EntitlementManager.initializeAccessEnabler`. Si vous n&#39;appelez pas `EntitlementManager.initializeAccessEnabler`d&#39;abord, `ManagerFactory` renvoie une instance de `EntitlementManager`, avec les flux de droits désactivés. 1. Configurez l’ID du demandeur.

   L’implémentation de référence est préconfigurée avec l’ID du demandeur de test défini sur : &quot;REF&quot;. Vous pouvez utiliser cet ID de demandeur pour tester votre application. Lorsque vous êtes prêt à utiliser l’ID du demandeur fourni par votre représentant d’authentification Primetime, mettez à jour le [!DNL res/values/strings.xml] fichier de l’application avec votre ID de demandeur.

   ```xml
   <!-- Programmer Requestor ID, change to ID provided by your Adobe  
        Primetime pay-TV pass representative --> 
   <string name="adobepass_requestor_id">REF</string> 
   
   <!-- Adobe Primetime pay-TV pass service provider endpoint for production 
        environment --> 
   <string name="adobepass_sp_url_production">sp.auth.adobe.com</string> 
   
   <!-- Adobe Primetime pay-TV pass service provider endpoint for staging  
        environment --> 
   <string name="adobepass_sp_url_staging">sp.auth-staging.adobe.com</string>
   ```

   De plus, vous devrez peut-être modifier les URL utilisées par votre application pour vous connecter aux services d’authentification Primetime. Il s’agit notamment des URL du serveur d’évaluation et de production d’authentification Primetime, ainsi que d’une URL vers un service de vérification des jetons. Pour plus d’informations, contactez votre représentant Adobe Primetime. 1. Signez l’ID du demandeur.

   Afin d&#39;établir l&#39;identité du Programmetime dans le système d&#39;authentification Primetime, l&#39;ID du Demandeur du Programmetime est envoyé au système d&#39;authentification Primetime. En tant que couche supplémentaire de sécurité, l’ID du demandeur doit être signé par le programmeur avant de l’envoyer à Adobe. Adobe conseille au programmeur de configurer un service pour signer l’ID du demandeur sur un réseau approuvé.

   L’implémentation de référence Primetime montre comment signer l’ID du demandeur, mais uniquement à des fins de démonstration. Adobe recommande vivement de ne pas inclure le certificat de signature et le code du générateur de signatures, sous `com.adobe.primetime.reference.crypto`, dans une application de production. Vous devez plutôt le déplacer vers un service réseau approuvé.

1. Configurez le  serveur .

   Le service d’authentification Primetime peut s’exécuter dans deux  distincts  :

   * Test : le  intermédiaire est utilisé pour tester votre application.
   * Production : le de  de production est utilisé pour les déploiements en direct de votre application.
   Vous définissez les URI pour le d’évaluation et de  de production  à l’aide de l’application. Toutefois, vous devez définir ceux qui sont utilisés par l’application dans le code. Dans la `com.adobe.primetime.reference.manager.EntitlementManger` classe, définissez la `environmentUri` variable sur `STAGING_URI` ou `PRODUCTION_URI` selon le service d’authentification Primetime  le que vous utilisez.

   >[!NOTE]
   >
   >L’ID de demandeur fourni (&quot;REF&quot;) ne doit être utilisé qu’avec le  de  d’évaluation.

   `com.adobe.primetime.reference.manager.EntitlementManager`:

   ```java
     // Adobe Primetime authentication service provider endpoint for production environment 
     PRODUCTION_URI = 
         application.getResources().getString(R.string.adobepass_sp_url_production); 
   
     // Adobe Primetime authentication service provider endpoint for staging environment 
     STAGING_URI = 
       application.getResources().getString(R.string.adobepass_sp_url_staging); 
   
     // Set to STAGING_URI when testing against the staging/test environment 
     // Set to PRODUCTION_URI when deploying the application for production use 
     String environmentUri = STAGING_URI; 
   
     // Adobe Primetime authentication service URI used by this application 
     PAYTV_PASS_URI = environmentUri + "/adobe-services"; 
   
     // Token Verification Service URL 
     TVS_URL = "https://" + environmentUri + "/tvs/v1/validate";
   ```

1. Personnaliser la grille de sélection de la DPSC.

   La page de sélection du fournisseur de contenu affiche un tableau des neuf principaux descripteurs de projet de programme multivarié parmi lesquels l’utilisateur peut choisir. L&#39;application extrait les neuf principales MVPD d&#39;un ordonné dans l&#39;application qui correspond aux MVPD disponibles intégrées au Programmetime dans le système d&#39;authentification Primetime. L&#39; ordonnée des principales DPSC est inscrite sur l&#39;ID de la DPSC dans le système d&#39;authentification Primetime et non sur le nom d&#39;affichage de la DPSC. Il est important de vérifier que les identifiants de la DPSC dans le principal des DPSC  correspondent aux identifiants de la DPSC intégrés au compte du programmeur, car, dans certains cas, les identifiants peuvent être différents d&#39;une intégration à l&#39;autre. Ci-dessous se trouve la  ordonnée des DVPM primaires qui se trouve dans la classe `com.adobe.primetime.reference.ui.entitlement.MvpdPickerFragment`.

   ```java
   /* Array of MVPDs to display in a Grid of icons 
   When displaying a grid, only the MVPDs which intersect this array and the 
   ArrayList of all MVPDs are displayed. 
   The array contents are ordered by display preference as only a maximum of 
   MAX_DISPLAY_ICONS are displayed. 
   */ 
   private static final String[] PRIMARY_MVPDS = { 
   "Comcast_SSO",                         // Comcast XFINITY 
   "DTV",                                 // DirectTV 
   "Dish",                                // Dish 
   "TWC",                                 // Time Warner Cable 
   "Cox",                                 // Cox 
   "Charter_Direct",                      // Charter 
   "Verizon",                             // Verizon FiOS 
   "Cablevision",                         // Cablevision Optimum 
   "ATT",                                 // AT&T U-verse 
   "Brighthouse",                         // Brighthouse 
   "Suddenlink",                          // Suddenlink 
   "Mediacom",                            // Mediacom 
   "CableOne",                            // CableOne 
   "WOW",                                 // WOW! 
   "RCN",                                 // RCN 
   "auth_atlanticbb_net",                 // Atlantic Broadband 
   "auth_armstrongmywire_com",            // Armstrong 
   "knology_auth-gateway_net",            // KNOLOGY 
   "serviceelectric_auth-gateway_net",    // Service Electric Cablevision 
   "msauth_midco_net",                    // Midcontinent Communications 
   "auth_metrocast_net",                  // MetroCast 
   "www_websso_mybrctv_com",              // Blue Ridge Communications 
   };
   ```

   Le tableau ci-après donne un exemple de l&#39;utilisation des  ordonnées des DVPM primaires. La première colonne  les DPSC intégrés au programmeur. La deuxième colonne est la  ordonnée (abrégée) des MVPD. La troisième colonne est le de résultats utilisé pour afficher les six premiers descripteurs de population multivariée à l’utilisateur.

   Cet exemple utilise les six premiers PVM au lieu des neuf actuels simplement pour garder l&#39;exemple simple. Remarquez comment le de résultats contient l’intersection des deux premières  et a le même ordre que le second . De plus, notez que AT&amp;T U-verse n&#39;est pas dans le final, puisque seuls les six premiers participants correspondants sont pris.

| MVPD disponibles | Principales MVPD | Affichage de 6 MVPD |
|--- |--- |--- |
| <ol><li>Comcast XFINITY</li><li>TWC</li><li>Mediacom</li><li>RCN</li><li>Disque</li><li>AT&amp;T U-verse</li><li>CableOne</li><li>Brighthouse</li><li>Haut débit atlantique</li><li>WOW !</li><li>MetroCast</li><li>DirectTV </li><li>Cox</li><li>Cablevision Optimum</li></ol> | <ol><li>Comcast XFINITY</li><li>DirectTV</li><li>Disque</li><li> TWC</li><li>Cox</li><li>Charte</li><li>Verizon FiOS</li><li>Cablevision Optimum</li><li>AT&amp;T U-verse</li></ol> | <ol><li>Comcast XFINITY</li><li>DirectTV</li><li>Disque</li><li>TWC</li><li>Cox</li><li>Cablevision Optimum</li></ol> |
