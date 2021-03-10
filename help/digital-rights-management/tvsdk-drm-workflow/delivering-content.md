---
title: Diffusion de contenu
description: Diffusion de contenu
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---


# Diffusion de contenu {#delivering-content}

Primetime DRM ignore le mécanisme de diffusion du contenu, car le runtime extrait la couche réseau et fournit simplement le contenu protégé au sous-système DRM Primetime. Par conséquent, le contenu peut être diffusé via HTTP, HTTP Dynamic Streaming, RTMP, RTMPE, HLS, etc.

Cependant, selon le protocole, la récupération des métadonnées du contenu protégé peut se révéler complexe ( `DRMContentData` - généralement sous la forme d&#39;un fichier &lt; a1/> chargé en parallèle). [!DNL .metadata] Ces métadonnées DRM sont requises pour appeler toute API `DRMManager`, telle que la prérécupération de la licence, l’authentification DRM ou l’accès à un domaine de périphérique. Par exemple, avec le protocole RTMP/RTMPE, seules les données FLV et F4V peuvent être diffusées au client via le Flash Media Server (FMS). C’est pourquoi le client doit récupérer l’objet blob de métadonnées de différentes manières. Une option permettant de résoudre ce problème consiste à héberger les métadonnées sur un serveur Web HTTP et à mettre en oeuvre le lecteur vidéo client pour récupérer les métadonnées appropriées, en fonction du contenu lu.

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

