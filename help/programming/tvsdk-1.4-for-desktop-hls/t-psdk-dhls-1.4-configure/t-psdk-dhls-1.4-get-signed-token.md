---
description: Le TVSDK Flash Runtime nécessite un jeton signé pour vérifier que vous avez le droit d’appeler l’API TVSDK sur le domaine où réside votre application.
title: Chargement de votre jeton signé
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# Chargement de votre jeton signé {#load-your-signed-token}

Le TVSDK Flash Runtime nécessite un jeton signé pour vérifier que vous avez le droit d’appeler l’API TVSDK sur le domaine où réside votre application.

1. Obtenez un jeton signé auprès de votre représentant d’Adobe pour chacun de vos domaines (où chaque domaine peut être un domaine spécifique ou un domaine générique).

       Pour obtenir un jeton, fournissez l’Adobe du domaine dans lequel votre application sera stockée ou chargée, ou, de préférence, du domaine sous la forme d’un hachage SHA256. En retour, Adobe vous fournit un jeton signé pour chaque domaine. Ces jetons prennent l’une des formes suivantes :
   
   * Un [!DNL .xml] agissant comme le jeton d’un domaine unique ou d’un domaine générique.

     >[!NOTE]
     >
     >Un jeton pour un domaine de caractères génériques couvre ce domaine et tous ses sous-domaines. Par exemple, un jeton générique pour le domaine [!DNL mycompany.com] couvrirait également [!DNL vids.mycompany.com] et [!DNL private.vids.mycompany.com]; un jeton de caractère générique pour [!DNL vids.mycompany.com] couvrirait également [!DNL private.vids.mycompany.com]. *Les jetons de domaine génériques ne sont pris en charge que pour certaines versions de Flash Player.*

   * A [!DNL .swf] fichier contenant des informations sur les jetons pour plusieurs domaines (sans inclure les caractères génériques) (un seul ou un caractère générique), que votre application peut charger dynamiquement.

1. Stockez le fichier de jeton au même emplacement ou dans le même domaine que votre application.

   Par défaut, TVSDK recherche le jeton à cet emplacement. Vous pouvez également spécifier le nom et l’emplacement du jeton dans `flash_vars` dans votre fichier de HTML.
1. Si votre fichier de jeton est un fichier XML unique :
   1. Utilisation `utils.AuthorizedFeaturesHelper.loadFrom` pour télécharger les données stockées à l’URL spécifiée (le fichier de jeton) et extraire la variable `authorizedFeatures` des informations.

      Cette étape peut varier. Par exemple, vous pouvez effectuer une authentification avant de démarrer l’application ou vous pouvez recevoir le jeton directement de votre système de gestion de contenu (CMS).

   1. TVSDK distribue une `COMPLETED` si le chargement a réussi ou si un événement `FAILED` dans le cas contraire. Prenez les mesures appropriées lorsque vous détectez l’un des événements.

      Cela doit réussir pour que votre application fournisse les `authorizedFeatures` objets au TVSDK sous la forme d’un objet `MediaPlayerContext`.

   Cet exemple montre comment utiliser un jeton unique [!DNL .xml] fichier .

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

1. Si votre jeton est un [!DNL .swf] fichier :
   1. Définition d’une `Loader` pour charger dynamiquement la classe [!DNL .swf] fichier .
   1. Définissez la variable `LoaderContext` pour spécifier le chargement à inclure dans le domaine d’application actuel, ce qui permet à TVSDK de choisir le jeton correct dans le [!DNL .swf] fichier . If `LoaderContext` n’est pas spécifié, l’action par défaut de `Loader.load` est de charger le fichier .swf dans le domaine enfant du domaine actif.
   1. Prêtez attention à l’événement COMPLETE, que TVSDK distribue si le chargement réussit.

      Recherchez également l’événement ERROR et prenez les mesures appropriées.
   1. Si la charge est réussie, utilisez la méthode `AuthorizedFeaturesHelper` pour obtenir un `ByteArray` qui contient les données de sécurité codées PCKS-7.

      Ces données sont utilisées par le biais de l’API AVE V11 pour obtenir l’accusé de réception des autorisations du lecteur Runtime Flash. Si le tableau d’octets ne comporte aucun contenu, utilisez plutôt la procédure pour rechercher un fichier de jeton à un seul domaine.
   1. Utilisation `AuthorizedFeatureHelper.loadFeatureFromData` pour obtenir les données requises du tableau d’octets.
   1. Déchargez le fichier [!DNL .swf] fichier .

   Les exemples suivants montrent comment utiliser un jeton multiple. [!DNL .swf] fichier .

   **Exemple 1 avec jeton multiple :**

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

   **Exemple 2 avec jeton multiple :**

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
