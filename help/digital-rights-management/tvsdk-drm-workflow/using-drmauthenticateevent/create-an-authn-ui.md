---
title: Création d’une interface utilisateur d’authentification
description: Création d’une interface utilisateur d’authentification
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# Création d’une interface utilisateur d’authentification {#create-an-authentication-ui}

1. Créez une interface utilisateur pour récupérer les informations d’authentification de l’utilisateur.

   Vous trouverez ci-dessous un exemple Flex d’interface utilisateur simple pour récupérer les informations d’identification de l’utilisateur. Il se compose d’un objet de panneau contenant deux `TextInput` , un pour chaque nom d’utilisateur et mot de passe. Le panneau contient également un bouton qui lance la fonction `credentials()` .

   ```xml
   <mx:Panel x="236.5"  
             y="113"  
             width="325"  
             height="204"  
             layout="absolute"  
             title="Login">  
       <mx:TextInput x="110"  
                     y="46"  
                     id="uName"/>  
       <mx:TextInput x="110"  
                     y="76"  
                     id="pWord"  
                     displayAsPassword="true"/>  
       <mx:Text x="35"  
                y="48"  
                text="Username:"/>  
       <mx:Text x="35"  
                y="78"  
                text="Password:"/>  
       <mx:Button x="120"  
                  y="115"  
                  label="Login"  
                  click="credentials()"/>  
   </mx:Panel>  
   ```

1. Écrivez le `credentials()` pour traiter les valeurs d’authentification fournies par l’utilisateur.

   La variable `credentials()` est une méthode définie par l’utilisateur qui transmet les valeurs de nom d’utilisateur et de mot de passe au `setDRMAuthenticationCredentials()` . Une fois les valeurs transmises, la variable `credentials()` réinitialise les valeurs de la méthode `TextInput` objets.

   ```
   <mx:Script> 
       <![CDATA[ 
         public function credentials():void { 
             videoStream.setDRMAuthenticationCredentials(uName, pWord, "drm"); 
             uName.text = ""; 
             pWord.text = ""; 
   } ]]> 
   </mx:Script> 
   ```

   Une méthode pour implémenter ce type d’interface simple consiste à inclure le panneau dans un nouvel état. Le nouvel état provient de l’état de base lorsque la variable `DRMAuthenticateEvent` est généré. L’exemple suivant contient une `VideoDisplay` avec un attribut source pointant vers un fichier vidéo protégé. Dans ce cas, la variable `credentials()` est modifiée afin qu’elle renvoie également l’application à l’état de base. Cette méthode le fait après avoir transmis les informations d’identification de l’utilisateur et réinitialisé les valeurs de l’objet TextInput.

   ```xml
   <?xml version="1.0" encoding="utf-8"?> 
   <mx:WindowedApplication xmlns:mx="https://www.adobe.com/2006/mxml" 
       layout="absolute" 
       width="800" 
       height="500" 
       title="DRM FLV Player" 
       creationComplete="initApp()" > 
       <mx:states> 
           <mx:State name="LOGIN"> 
               <mx:AddChild position="lastChild"> 
                       <mx:Panel x="236.5"  
                                 y="113"  
                                 width="325"  
                                 height="204"  
                                 layout="absolute"  
                                 title="Login"> 
                       <mx:TextInput x="110"  
                                     y="46"  
                                     id="uName"/> 
                       <mx:TextInput x="110"  
                                     y="76"  
                                     id="pWord"  
                                     displayAsPassword="true"/> 
                       <mx:Text x="35"  
                                y="48"  
                                text="Username:"/> 
                       <mx:Text x="35"  
                                y="78"  
                                text="Password:"/> 
                       <mx:Button x="120"  
                                  y="115"  
                                  label="Login"  
                                  click="credentials()"/> 
                       <mx:Button x="193"  
                                  y="115"  
                                  label="Reset"  
                                  click="uName.text=''; 
               </mx:Panel> 
           </mx:AddChild> 
       </mx:State> 
   </mx:states> 
   pWord.text='';"/> 
   
   <mx:Script> 
       <![CDATA[ 
           import flash.events.DRMAuthenticateEvent; 
           private function initApp():void { 
               videoStream.addEventListener(DRMAuthenticateEvent.DRM_AUTHENTICATE, 
                                            drmAuthenticateEventHandler); 
           } 
           public function credentials():void { 
               videoStream.setDRMAuthenticationCredentials(uName, pWord, "drm"); 
               uName.text = ""; 
               pWord.text = ""; 
               currentState=''; 
           } 
           private function drmAuthenticateEventHandler(event:DRMAuthenticateEvent):void { 
               currentState='LOGIN'; 
           } 
       ]]> 
   </mx:Script> 
   <mx:VideoDisplay id="video"  
                    x="50"  
                    y="25"  
                    width="700"  
                    height="350" 
                    autoPlay="true" 
                    bufferTime="10.0" 
                    source="https://www.example.com/flv/Video.flv" /> 
   </mx:WindowedApplication> 
   ```
