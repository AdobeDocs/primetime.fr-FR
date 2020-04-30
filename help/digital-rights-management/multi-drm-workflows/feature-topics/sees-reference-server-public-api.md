---
description: La demande de droits et la réponse sont transmises via une connexion SSL mutuellement authentifiée entre le serveur de licences et le service de droits du client.
seo-description: La demande de droits et la réponse sont transmises via une connexion SSL mutuellement authentifiée entre le serveur de licences et le service de droits du client.
seo-title: VOIR API publique
title: VOIR API publique
uuid: f3a17d61-04ee-4bdb-9d64-a98066c6d1c8
translation-type: tm+mt
source-git-commit: 15403abbd53486e1faa2146cda83f41bd8116632

---


# VOIR API publique {#sees-public-api}

La demande de droits et la réponse sont transmises via une connexion SSL mutuellement authentifiée entre le serveur de licences et le service de droits du client.

Le schéma URI HTTPS ( [https://tools.ietf.org/html/rfc7230#section-2.7.2](https://tools.ietf.org/html/rfc7230#section-2.7.2)) est utilisé pour définir le point de terminaison des droits et la méthode de requête HTTP POST ( [https://tools.ietf.org/html/rfc7231#section-4.3.3](https://tools.ietf.org/html/rfc7231#section-4.3.3)) est utilisée pour la requête. Le point de terminaison des droits, ainsi qu’un indicateur indiquant les droits dorsaux, sont obligatoires et doivent être inclus dans la stratégie au moment de l’assemblage.

## Demande de droits {#section_BFBFEF0795CA46D6842C479256B95F95}

Le corps de la demande de droits est un objet JSON défini comme illustré ci-dessous.

**Définition de l&#39;objet de demande de droits JSON**

```
{ 
 "title" : "Entitlement Request", 
 "type" : "object", 
 "properties" : { 
  "messageID" : { 
   "type" : "string", 
   "description" : "Unique ID for this message (GUID).  Used to confirm that the subsequent response is actually for this request." 
  }, 
  "version" : { 
   "type" : "integer", 
   "description" : "Version number of the protocol, currently 1." 
  }, 
  "requestType" : { 
   "type" : "integer", 
   "description" : "Request type. 1 - time based entitlement request, 2 - device registration entitlement request 3 - device bound entitlement request." 
  }, 
  "contentID" : { 
   "type" : "string", 
   "description" : "Content ID (GUID) that was given to the content during packaging time." 
  }, 
  "customerCookie" : { 
   "type" : "string", 
   "description" : "Customer cookie. Cookie is just arbitrary string up to 32 characters long." 
  } 
    }, 
 "required" : ["messageID", "version", "contentID"] 
}
```

## Réponse aux droits {#section_F15A9FD6BAD946B3B4C5C14612F90154}

Le corps de la réponse de droits est un objet JSON.

**Définition de l’objet de réponse de droits JSON**

```
{ 
  "title" : "Entitlement Response", 
  "type" : "object", 
  "properties" : { 
    "messageID" : { 
    "type" : "string", 
    "description" : "Unique ID from the Entitlement Request message.   
      Must match, or entitlement will be denied." 
  }, 
  "version" : { 
    "type" : "integer", 
    "description" : "Version number of the protocol; must be <= the version number  
      from the Entitlement Request message." 
  }, 
  "isAllowed" : { 
    "type" : "boolean", 
    "description" : "Grant the license or not." 
  }, 
  "epTokenURL" : { 
    "type" : "string", 
    "description" : "ExpressPlay Token URL" 
  }, 
  "error" : { 
    "type" : "integer", 
    "description" : "An error number produced by the entitlement server.  
      Will be passed to the client as the 'code' field of the server error response." 
  }, 
  "errorText" : { 
    "type" : "string", 
    "description" : "Additional error information produced by the entitlement server.  
      Will be passed to the client as the 'text' field of the server error response." 
  }, 
  "required" : ["messageID", "version", "isAllowed", "epTokenURL"] 
}
```
