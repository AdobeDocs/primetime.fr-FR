---
description: Le TVSDK d’exécution du Flash a besoin d’un jeton signé pour vérifier que vous avez le droit d’appeler l’API TVSDK sur le domaine où réside votre application.
title: Charger votre jeton signé
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---


# Chargez votre jeton signé {#load-your-signed-token}

Le TVSDK d’exécution du Flash a besoin d’un jeton signé pour vérifier que vous avez le droit d’appeler l’API TVSDK sur le domaine où réside votre application.

1. Récupérez un jeton signé auprès de votre représentant d’Adobe pour chacun de vos domaines (où chaque domaine peut être un domaine spécifique ou un domaine générique).

       Pour obtenir un jeton, fournissez à l’Adobe soit le domaine dans lequel votre application sera stockée ou chargée, soit, de préférence, le domaine en tant que hachage SHA256. En retour, l’Adobe vous fournit un jeton signé pour chaque domaine. Ces jetons prennent l’une des formes suivantes :
   
   * Un fichier [!DNL .xml] agissant comme jeton pour un seul domaine ou domaine générique.

      >[!NOTE]
      >
      >Un jeton pour un domaine générique couvre ce domaine et tous ses sous-domaines. Par exemple, un jeton générique pour le domaine [!DNL mycompany.com] couvrirait également [!DNL vids.mycompany.com] et [!DNL private.vids.mycompany.com]; un jeton générique pour [!DNL vids.mycompany.com] couvrirait également [!DNL private.vids.mycompany.com]. *Les jetons de domaine génériques ne sont pris en charge que pour certaines versions de Flash Player.*

   * Fichier [!DNL .swf] contenant des informations de jeton pour plusieurs domaines (sans inclure les caractères génériques) (unique ou générique), que votre application peut charger dynamiquement.

1. Stockez le fichier de jeton au même emplacement ou domaine que votre application.

   Par défaut, TVSDK recherche le jeton à cet emplacement. Vous pouvez également spécifier le nom et l’emplacement du jeton dans `flash_vars` votre fichier HTML.
1. Si votre fichier de jeton est un fichier XML unique :
   1. Utilisez `utils.AuthorizedFeaturesHelper.loadFrom` pour télécharger les données stockées à l’URL spécifiée (le fichier de jeton) et en extraire les informations `authorizedFeatures`.

      Cette étape peut varier. Par exemple, vous pouvez effectuer une authentification avant de démarrer l’application ou recevoir directement le jeton de votre système de gestion de contenu (CMS).

   1. TVSDK distribue un événement `COMPLETED` si le chargement réussit ou un événement `FAILED` dans le cas contraire. Prenez les mesures appropriées lorsque vous détectez l’un ou l’autre des événements.

      Pour que votre application puisse fournir les objets `authorizedFeatures` requis à TVSDK sous la forme d&#39;un `MediaPlayerContext`, cette opération doit réussir.
   Cet exemple montre comment utiliser un fichier à jeton unique [!DNL .xml].

   ```
   private function loadDirectTokenURL():void { 
       var url:String = constructAuthorizedFeatureTokenURL(); 
       _logger.debug("#onApplicationComplete Loading token from [{0}].", url); 
       _authorizedFeatureHelper = new AuthorizedFeaturesHelper(); 
       _authorizedFeatureHelper.addEventListener(Event.COMPLETE,  
           onFeatureComplete); 
       _authorizedFeatureHelper.addEventListener(ErrorEvent.ERROR,  
           onFeatureError); 
        _authorizedFeatureHelper.loadFrom(url); 
    }
   ```

1. Si votre jeton est un fichier [!DNL .swf] :
   1. Définissez une classe `Loader` pour charger dynamiquement le fichier [!DNL .swf].
   1. Définissez `LoaderContext` pour spécifier le chargement dans le domaine d’application actuel, ce qui permet à TVSDK de choisir le jeton approprié dans le fichier [!DNL .swf]. Si `LoaderContext` n&#39;est pas spécifié, l&#39;action par défaut de `Loader.load` consiste à charger le fichier .swf dans le domaine enfant du domaine actif.
   1. Prêtez attention au événement COMPLETE, que TVSDK distribue si le chargement réussit.

      Écoutez également le événement ERROR et prenez les mesures appropriées.
   1. Si le chargement réussit, utilisez `AuthorizedFeaturesHelper` pour obtenir un `ByteArray` contenant les données de sécurité codées PCKS-7.

      Ces données sont utilisées par l’API AVE V11 pour obtenir un accusé de réception d’autorisation de la part du lecteur d’exécution Flash. Si le tableau d’octets ne contient aucun contenu, utilisez plutôt la procédure pour rechercher un fichier de jeton d’un seul domaine.
   1. Utilisez `AuthorizedFeatureHelper.loadFeatureFromData` pour obtenir les données requises à partir du tableau d’octets.
   1. Déchargez le fichier [!DNL .swf].

   Les exemples suivants montrent comment utiliser un fichier à jetons multiples [!DNL .swf].

   **Exemple 1 à jetons multiples :**

   ```
   private function onApplicationComplete(event:FlexEvent):void { 
       var url:String = constructAuthorizedFeatureTokenURLFromSwf();   
       _loader = new Loader(); 
       var swfUrl:URLRequest = new URLRequest(url); 
       var loaderContext:LoaderContext =  
           new LoaderContext(false, ApplicationDomain.currentDomain, null); 
       _loader.contentLoaderInfo.addEventListener(Event.COMPLETE,  
           modEventHandler); 
       _loader.contentLoaderInfo.addEventListener(IOErrorEvent.IO_ERROR,  
           errEventHandler); 
       _loader.contentLoaderInfo.addEventListener(ProgressEvent.PROGRESS,  
           onProgressHandler); 
       _loader.uncaughtErrorEvents.addEventListener(UncaughtErrorEvent. 
           UNCAUGHT_ERROR, uncaughtEventHandler); 
       _logger.debug("# Loading token swf with context from [{0}].", url); 
       _loader.load(swfUrl, loaderContext); 
   } 
   
   private function modEventHandler(e:Event):void { 
       _logger.debug("loadSWF with domainID {0}",  
       SecurityDomain.currentDomain.domainID); 
       var loader : Loader = e.currentTarget.loader as Loader; 
       var myAuthorizedTokensLoaderClass:Class =  
           loader.contentLoaderInfo.applicationDomain. 
           getDefinition("AuthorizedTokensLoader") as Class; 
       var myTokens:Object = new myAuthorizedTokensLoaderClass(); 
       _authorizedFeatureHelper = new AuthorizedFeaturesHelper(); 
       _authorizedFeatureHelper.addEventListener(Event.COMPLETE, onFeatureComplete); 
       _authorizedFeatureHelper.addEventListener(ErrorEvent.ERROR, onFeatureError); 
       var byteArray:ByteArray = myTokens. 
           FetchToken(SecurityDomain.currentDomain.domainID); 
       if (myTokens == null || byteArray == null || byteArray.length == 0) 
           loadDirectTokenURL(); 
       else { 
           _logger.debug("token bytearry size {0}", byteArray.length); 
           _authorizedFeatureHelper.loadFeatureFromData(byteArray); 
       } 
       _loader.unload(); 
   } 
   ```

   **Exemple 2 à jetons multiples :**

   ```
   private function tokenSwfLoadedHandler(e:Event):void { 
       trace("loadSWF with domainID {0}", SecurityDomain.currentDomain.domainID); 
       var loader : Loader = e.currentTarget.loader as Loader; 
       var myAuthorizedTokensLoaderClass:Class =  
         loader.contentLoaderInfo.applicationDomain. 
         getDefinition("AuthorizedTokensLoader") as Class; 
       var myTokens:Object = new myAuthorizedTokensLoaderClass(); 
       authorizedFeatureHelper = new AuthorizedFeaturesHelper(); 
       authorizedFeatureHelper.addEventListener(Event.COMPLETE, onFeatureComplete); 
       authorizedFeatureHelper.addEventListener(ErrorEvent.ERROR, onFeatureError); 
       var byteArray:ByteArray =  
           myTokens.FetchToken(SecurityDomain.currentDomain.domainID); 
       var myDomains:Array = ["domain.com"]; 
       if (byteArray == null || byteArray.length == 0) { 
           // check for wildcard tokens 
           if (myTokens.hasOwnProperty("FetchWildCardToken") == true) { 
               // contains wildcard domains 
               for each (var domain:String in myDomains) { 
                   byteArray = myTokens.FetchWildCardToken(domain); 
                   if (byteArray != null && byteArray.length != 0) { 
                       break; 
                   } 
               }; 
           } 
       } 
   
       if (myTokens == null || byteArray == null || byteArray.length == 0) 
           loadDirectTokenURL(); 
       else { 
           trace("token bytearry size {0}", byteArray.length); 
           authorizedFeatureHelper.loadFeatureFromData(byteArray); 
       } 
       _loader.unload(); 
   } 
   
   private function loadDirectTokenURL():void { 
       trace("#onApplicationComplete Loading token from [{0}].", tokenUrl); 
       authorizedFeatureHelper = new AuthorizedFeaturesHelper(); 
       authorizedFeatureHelper.addEventListener(Event.COMPLETE, onFeatureComplete); 
       authorizedFeatureHelper.addEventListener(ErrorEvent.ERROR, onFeatureError); 
       authorizedFeatureHelper.loadFrom(tokenUrl); 
   }
   ```

