---
seo-title: Création d’une interface utilisateur d’authentification
title: Création d’une interface utilisateur d’authentification
uuid: 4744bac0-c36e-4b0a-b3fb-d81c7f2e7617
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Création d’une interface utilisateur d’authentification {#create-an-authentication-ui}

1. Créez une interface utilisateur pour récupérer les informations d’identification d’authentification de l’utilisateur.

   Voici un exemple Flex d’interface utilisateur simple pour récupérer les informations d’identification de l’utilisateur. Il se compose d’un objet de panneau contenant deux `TextInput` objets, un pour chaque nom d’utilisateur et mot de passe. Le panneau contient également un bouton qui lance la `credentials()` méthode.

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

1. Ecrivez la `credentials()` méthode pour traiter les valeurs d’authentification fournies par l’utilisateur.

   La `credentials()` méthode est définie par l’utilisateur et transmet les valeurs de nom d’utilisateur et de mot de passe à la `setDRMAuthenticationCredentials()` méthode. Une fois les valeurs transmises, la `credentials()` méthode réinitialise les valeurs des `TextInput` objets.

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

   Une méthode pour implémenter ce type d’interface simple consiste à inclure le panneau dans un nouvel état. Le nouvel état provient de l’état de base lorsque l’ `DRMAuthenticateEvent` objet est lancé. L’exemple suivant contient un `VideoDisplay` objet avec un attribut source qui pointe vers un fichier vidéo protégé. Dans ce cas, la `credentials()` méthode est modifiée de sorte qu’elle renvoie également l’application à l’état de base. Cette méthode le fait après avoir transmis les informations d’identification de l’utilisateur et réinitialisé les valeurs de l’objet TextInput.

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

