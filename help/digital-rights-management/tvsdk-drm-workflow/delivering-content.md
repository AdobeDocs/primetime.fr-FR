---
title: Diffuser du contenu
description: Diffuser du contenu
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---

# Diffuser du contenu {#delivering-content}

Primetime DRM ne s’intéresse pas au mécanisme de diffusion du contenu, car l’exécution extrait la couche réseau et fournit simplement le contenu protégé au sous-système DRM Primetime. Par conséquent, le contenu peut être diffusé par HTTP, HTTP Dynamic Streaming, RTMP, RTMPE, HLS, etc.

Cependant, selon le protocole, la récupération des métadonnées du contenu protégé peut être complexe ( `DRMContentData` - généralement sous la forme d’un fichier codé [!DNL .metadata] ). Ces métadonnées DRM sont requises pour appeler toute `DRMManager` API, comme la prérécupération de la licence, l’authentification DRM ou la jonction d’un domaine d’appareil. Par exemple, avec le protocole RTMP/RTMPE, seules les données FLV et F4V peuvent être diffusées au client par le biais du Flash Media Server (FMS). C’est pourquoi le client doit récupérer l’objet blob de métadonnées par d’autres moyens. Une option permettant de résoudre ce problème consiste à héberger les métadonnées sur un serveur web HTTP et à mettre en oeuvre le lecteur vidéo client pour récupérer les métadonnées appropriées, en fonction du contenu lu.

```
private function getMetadata():void { 
    extrapolated-path-to-metadata = "https://metadatas.mywebserver.com/" + videoname; 
     var urlRequest : URLRequest =  
      new URLRequest(extrapolated-path-to-the-metadata + ".metadata");  
    var urlStream : URLStream = new URLStream();  
    urlStream.addEventListener(Event.COMPLETE, handleMetadata);  
    urlStream.addEventListener(IOErrorEvent.NETWORK_ERROR, handleIOError);  
    urlStream.addEventListener(IOErrorEvent.IO_ERROR, handleIOError);  
    urlStream.addEventListener(IOErrorEvent.VERIFY_ERROR, handleIOError);  
 
    try { 
        urlStream.load(urlRequest);  
    } catch(se:SecurityError) { 
        videoLog.text += se.toString() + "\n";  
    } catch(e:Error) { 
        videoLog.text += e.toString() + "\n";  
    } 
} 
```
