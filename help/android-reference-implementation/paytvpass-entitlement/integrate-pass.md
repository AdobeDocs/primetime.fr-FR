---
description: Personnalisez votre implémentation de référence pour intégrer l’authentification Adobe Primetime à votre environnement de production.
seo-description: Personnalisez votre implémentation de référence pour intégrer l’authentification Adobe Primetime à votre environnement de production.
seo-title: Intégration de l’authentification Primetime
title: Intégration de l’authentification Primetime
uuid: 34cdf1da-261e-462c-a194-4fcb439e5dfb
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Intégration de l’authentification Primetime {#integrate-primetime-authentication}

Personnalisez votre implémentation de référence pour intégrer l’authentification Adobe Primetime à votre environnement de production.

L’intégration de l’implémentation de référence du service d’authentification Primetime fonctionne de manière standard comme une démonstration. Cependant, pour utiliser l’intégration dans un lecteur prêt à l’emploi, vous devez implémenter les personnalisations suivantes :

1. Activez ou désactivez les flux de droits.

   Le `EntitlementManager` client doit d’abord initialiser et obtenir une instance du SDK d’authentification Primetime pour être activé. Si la bibliothèque `EntitlementManager` n’est pas initialisée, le gestionnaire est désactivé.
1. Activez le `EntitlementManger`, à partir de votre classe d&#39;applications principale :

   ```java
   // initialize the AccessEnabler library, required for Primetime PayTV Pass entitlement workflows 
   EntitlementManager.initializeAccessEnabler(this); // comment out this line to disable entitlement workflows
   ```

1. Utilisez la `ManagerFactory` classe pour obtenir une instance du `EntitlementManager`.

   Vous devez toujours utiliser la `ManagerFactory` pour obtenir une instance de la `EntitlementManager`, car la classe `ManagerFactory` gère une instance unique de EntitlementManager pour votre application. N&#39;instanciez jamais les `EntitlementManager` ou `EntitlementManagerOn` les classes en utilisant leurs constructeurs.

   ```java
   EntitlementManager entitlementManager =  
   ManagerFactory.getEntitlementManager();
   ```

   Le `ManagerFactory` renvoie une instance de `EntitlementManagerOn`, avec les flux de droits activés, si vous avez précédemment appelé `EntitlementManager.initializeAccessEnabler`. Si vous n&#39;appelez pas `EntitlementManager.initializeAccessEnabler`au préalable, alors l&#39; `ManagerFactory` instance renvoie une instance de `EntitlementManager`, avec les flux de droits désactivés. 1. Configurez l&#39;ID du demandeur.

   L&#39;implémentation de référence est préconfigurée avec l&#39;ID de demandeur de test défini sur : &quot;REF&quot;. Vous pouvez utiliser cet ID de demandeur pour tester votre application. Lorsque vous êtes prêt à utiliser l&#39;ID du demandeur fourni par votre représentant d&#39;authentification Primetime, mettez à jour le [!DNL res/values/strings.xml] fichier de l&#39;application avec votre ID de demandeur.

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

   De plus, vous devrez peut-être modifier les URL utilisées par votre application pour vous connecter aux services d’authentification Primetime. Il s’agit notamment des URL d’évaluation et de serveur de production d’authentification Primetime, ainsi que d’une URL vers un service de vérification des jetons. Pour plus d’informations, contactez votre représentant Adobe Primetime. 1. Signez l&#39;identifiant du demandeur.

   Afin d&#39;établir l&#39;identité du Programmetime dans le système d&#39;authentification Primetime, l&#39;ID du Demandeur du Programmetime est envoyé au système d&#39;authentification Primetime. En tant que couche supplémentaire de sécurité, l’ID du demandeur doit être signé par le programmeur avant de l’envoyer à Adobe. Adobe recommande au programmeur de configurer un service pour signer l’identifiant du demandeur sur un réseau approuvé.

   L’implémentation de référence Primetime montre comment signer l’identifiant du demandeur, mais ceci est uniquement à des fins de démonstration. Adobe recommande vivement de ne pas inclure le certificat de signature et le code du générateur de signatures dans `com.adobe.primetime.reference.crypto`une application de production. Vous devez plutôt le déplacer vers un service réseau approuvé.

1. Configurez l&#39;Environnement de serveur.

   Le service d’authentification Primetime peut s’exécuter dans deux environnements distincts :

   * Évaluation : l’environnement intermédiaire est utilisé pour tester votre application.
   * Production : l&#39;environnement de production est utilisé pour les déploiements en direct de votre application.
   Vous définissez les URI pour les environnements d’évaluation et de production à l’aide de l’application ; toutefois, vous devez définir ceux qui sont utilisés par l’application dans le code. Dans la `com.adobe.primetime.reference.manager.EntitlementManger` classe, définissez la `environmentUri` variable sur `STAGING_URI` ou `PRODUCTION_URI` selon l’environnement du service d’authentification Primetime que vous utilisez.

   >[!NOTE]
   >
   >L&#39;ID de demandeur fourni (&quot;REF&quot;) ne doit être utilisé qu&#39;avec l&#39;environnement d&#39;évaluation.

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

1. Personnaliser la grille de sélection de la MVPD.

   La page de sélection du fournisseur de contenu affiche un tableau des neuf principaux DPSC que l’utilisateur peut sélectionner. L&#39;application extrait les neuf principaux DVM d&#39;une liste ordonnée dans l&#39;application qui correspond aux DVM disponibles intégrés au Programmeer dans le système d&#39;authentification Primetime. La liste ordonnée des principaux descripteurs de programme de test multivarié est indiquée sur l&#39;ID de la DPSC dans le système d&#39;authentification Primetime, et non sur le nom d&#39;affichage de la DPSC. Il est important de vérifier que les identifiants de la MVPD figurant dans la liste principale des descripteurs correspondent aux identifiants de la MVPD intégrés au compte du programmeur, car, dans certains cas, les identifiants peuvent être différents d&#39;une intégration à l&#39;autre. Ci-dessous, vous trouverez la liste ordonnée des MVPD primaires qui se trouve dans la classe `com.adobe.primetime.reference.ui.entitlement.MvpdPickerFragment`.

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

   Le tableau suivant fournit un exemple d&#39;utilisation de la liste ordonnée des MVPD primaires. La première colonne liste les DPSC intégrés au programmeur. La deuxième colonne est la liste ordonnée (abrégée) des DPSC. La troisième colonne correspond à la liste de résultats utilisée pour afficher les six principaux descripteurs de projet multivarié à l&#39;utilisateur.

   Cet exemple utilise les six premiers PVM plutôt que les neuf derniers pour simplifier l&#39;exemple. Notez comment la liste de résultats contient l’intersection des deux premières listes et a le même ordre que la seconde liste. De plus, notez qu&#39;AT&amp;T U-verse n&#39;est pas dans la liste finale, car seuls les six premiers MVPD correspondants sont pris.

| MVPD disponibles | MVPD principaux | Affichage de 6 MVPD |
|--- |--- |--- |
| <ol><li>XFINITÉ Comcast</li><li>TWC</li><li>Mediacom</li><li>RCN</li><li>Disque</li><li>A&amp;T - Inverse</li><li>CableOne</li><li>Brighthouse</li><li>Haut débit atlantique</li><li>WOW !</li><li>MetroCast</li><li>DirectTV </li><li>Cox</li><li>Cablevision Optimum</li></ol> | <ol><li>XFINITÉ Comcast</li><li>DirectTV</li><li>Disque</li><li> TWC</li><li>Cox</li><li>Charte</li><li>Verizon FiOS</li><li>Cablevision Optimum</li><li>A&amp;T - Inverse</li></ol> | <ol><li>XFINITÉ Comcast</li><li>DirectTV</li><li>Disque</li><li>TWC</li><li>Cox</li><li>Cablevision Optimum</li></ol> |
