---
description: Personnalisez votre mise en oeuvre de référence pour intégrer l’authentification Adobe Primetime à votre environnement de production.
title: Intégration de l’authentification Primetime
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '767'
ht-degree: 0%

---

# Intégration de l’authentification Primetime {#integrate-primetime-authentication}

Personnalisez votre mise en oeuvre de référence pour intégrer l’authentification Adobe Primetime à votre environnement de production.

L’intégration de l’implémentation de référence du service d’authentification Primetime fonctionne comme une démonstration prête à l’emploi. Toutefois, pour utiliser l’intégration dans un lecteur prêt pour la production, vous devez mettre en oeuvre les personnalisations suivantes :

1. Activez ou désactivez les flux de droits.

   La variable `EntitlementManager` doit d’abord initialiser et obtenir une instance du SDK d’authentification Primetime à activer. Si la variable `EntitlementManager` n’initialise pas cette bibliothèque, le gestionnaire est désactivé.
1. Activez la variable `EntitlementManger`, depuis votre classe d’applications principale :

   ```java
   // initialize the AccessEnabler library, required for Primetime PayTV Pass entitlement workflows 
   EntitlementManager.initializeAccessEnabler(this); // comment out this line to disable entitlement workflows
   ```

1. Utilisez la variable `ManagerFactory` pour obtenir une instance de la variable `EntitlementManager`.

   Vous devez toujours utiliser la variable `ManagerFactory` pour obtenir une instance de la fonction `EntitlementManager`, en tant que `ManagerFactory` conserve une seule instance de EntitlementManager pour votre application. Ne jamais instancier la variable `EntitlementManager` ou `EntitlementManagerOn` en utilisant leurs constructeurs.

   ```java
   EntitlementManager entitlementManager =  
   ManagerFactory.getEntitlementManager();
   ```

   La variable `ManagerFactory` renvoie une instance de `EntitlementManagerOn`, avec les flux de droits activés, si vous avez précédemment appelé `EntitlementManager.initializeAccessEnabler`. Si vous n’effectuez pas le premier appel `EntitlementManager.initializeAccessEnabler`, puis la variable `ManagerFactory` renvoie une instance de `EntitlementManager`, avec les flux de droits désactivés. 1. Configurez l’identifiant du demandeur.

   L’implémentation de référence est préconfigurée avec l’identifiant du demandeur de test défini sur &quot;REF&quot;. Vous pouvez utiliser cet identifiant de demandeur pour tester votre application. Lorsque vous êtes prêt à utiliser l’identifiant du demandeur fourni par votre représentant d’authentification Primetime, mettez à jour le [!DNL res/values/strings.xml] avec votre ID de demandeur.

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

   De plus, vous devrez peut-être modifier les URL utilisées par votre application pour vous connecter aux services d’authentification Primetime. Il s’agit notamment des URL du serveur d’évaluation et de production d’authentification Primetime, ainsi que de l’URL d’un service de vérification des jetons. Pour plus d’informations, contactez votre représentant Adobe Primetime. 1. Signez l’identifiant du demandeur.

   Afin d’établir l’identité du programmeur dans le système d’authentification Primetime, l’identifiant du demandeur du programmetime est envoyé au système d’authentification Primetime. En tant que couche de sécurité supplémentaire, l’identifiant du demandeur doit être signé par le programmeur avant de l’envoyer à Adobe. Adobe recommande au programmeur de configurer un service pour signer l’identifiant du demandeur sur un réseau de confiance.

   La mise en oeuvre de référence Primetime montre comment signer l’identifiant du demandeur, mais ce n’est qu’à des fins de démonstration. Adobe recommande vivement que le certificat de signature et le code du générateur de signatures, sous `com.adobe.primetime.reference.crypto`, ne doit pas être inclus dans une application de production. Vous devez plutôt le déplacer vers un service réseau de confiance.

1. Configurez l’environnement du serveur.

   Le service d’authentification Primetime peut s’exécuter dans deux environnements distincts :

   * Évaluation : l’environnement d’évaluation est utilisé pour tester votre application.
   * Production : l’environnement de production est utilisé pour les déploiements en direct de votre application.

   Vous définissez les URI pour les environnements d’évaluation et de production à l’aide de l’application. Toutefois, vous devez définir ceux qui sont utilisés par l’application dans le code. Dans le `com.adobe.primetime.reference.manager.EntitlementManger` , définissez la variable `environmentUri` de `STAGING_URI` ou `PRODUCTION_URI` selon l’environnement du service d’authentification Primetime que vous utilisez.

   >[!NOTE]
   >
   >L’identifiant du demandeur fourni (&quot;REF&quot;) ne doit être utilisé qu’avec l’environnement d’évaluation.

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

1. Personnalisez la grille de sélection MVPD.

   La page de sélection du fournisseur de contenu affiche un tableau des neuf principaux distributeurs multicanaux de programmes de diffusion de contenu que l’utilisateur peut sélectionner. L’application extrait les neuf principaux MVPD d’une liste ordonnée au sein de l’application qui correspondent aux MVPD disponibles intégrés au programmeur dans le système d’authentification Primetime. La liste classée des MVPD principaux est indexée sur l’ID MVPD dans le système d’authentification Primetime, et non sur le nom d’affichage MVPD. Il est important de vérifier que les ID MVPD de la liste des MVPD principaux correspondent aux ID MVPD intégrés au compte du programmeur, car, dans certains cas, les ID peuvent être différents selon les intégrations. Vous trouverez ci-dessous la liste classée des MVPD principaux qui se trouvent dans la classe . `com.adobe.primetime.reference.ui.entitlement.MvpdPickerFragment`.

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

   Le tableau suivant fournit un exemple d’utilisation de la liste classée des MVPD principaux. La première colonne répertorie les MVPD intégrés au programmeur. La deuxième colonne est la liste (abrégée) des MVPD. La troisième colonne correspond à la liste de résultats utilisée pour afficher les six principaux MVPD pour l’utilisateur.

   Cet exemple utilise les six premiers MVPD au lieu des neuf réels simplement pour garder l’exemple simple. Notez comment la liste des résultats contient l’intersection des deux premières listes et a le même ordre que la deuxième liste. Notez également que AT&amp;T U-verse n’est pas dans la liste finale, car seuls les six premiers distributeurs MVPD correspondants sont pris.

| MVPD disponibles | MVPD de Principal | Affichage de 6 MVPD |
|--- |--- |--- |
| <ol><li>XFINITY Comcast</li><li>TWC</li><li>Mediacom</li><li>RCN</li><li>Disposition</li><li>AT&amp;T-verse</li><li>CableOne</li><li>Brighthouse</li><li>Haut débit atlantique</li><li>WOW !</li><li>MetroCast</li><li>DirectTV </li><li>Cox</li><li>Cablevision Optimum</li></ol> | <ol><li>XFINITY Comcast</li><li>DirectTV</li><li>Disposition</li><li> TWC</li><li>Cox</li><li>Charte</li><li>Verizon FiOS</li><li>Cablevision Optimum</li><li>AT&amp;T-verse</li></ol> | <ol><li>XFINITY Comcast</li><li>DirectTV</li><li>Disposition</li><li>TWC</li><li>Cox</li><li>Cablevision Optimum</li></ol> |
