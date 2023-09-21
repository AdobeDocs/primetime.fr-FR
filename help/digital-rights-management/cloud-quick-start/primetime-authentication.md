---
title: Authentification Adobe Primetime (facultatif)
description: Authentification Adobe Primetime (facultatif)
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Authentification Adobe Primetime (facultatif) {#adobe-primetime-authentication-optional}

Si la stratégie DRM utilisée pour empaqueter le contenu est une stratégie anonyme, une licence sera émise à toutes les demandes de licence. En option, Primetime Cloud DRM prend également en charge l’authentification par le biais de l’authentification Adobe Primetime. Si cette fonctionnalité est activée, une licence ne sera pas émise, sauf si le périphérique client a acquis au préalable un jeton d’authentification Primetime et l’a défini localement via l’API client appropriée ( `setAuthenticationToken`) pour définir des jetons d’authentification personnalisés. Pour plus d’informations sur l’intégration de l’authentification Primetime à votre workflow d’authentification, consultez : [Authentification Adobe Primetime.](https://tve.helpdocsonline.com/home)

Lors de l’acquisition d’une licence, si la stratégie DRM indique que l’authentification Pri-time est requise, le serveur de licences analyse et valide le jeton de média court de l’authentification Primetime. Si la stratégie DRM spécifie une `ResourceID` ou `RequestorID`, le serveur de licences valide également le jeton en fonction de ces propriétés. S’ils ne sont pas définis, le serveur de licences définit la ou les propriétés comme &quot;null&quot; lors de la validation du jeton. Ce n’est que si la validation du jeton est réussie qu’une licence sera émise. Dans le cas contraire, un DRMErrorEvent 3328 avec un sous-code d’erreur 305 (User Not Authorized) sera distribué par le client.

Les paramètres d’authentification Primetime doivent être spécifiés dans la stratégie utilisée pour regrouper le contenu destiné à nécessiter une authentification Primetime.

Les propriétés pertinentes sont les suivantes :

```
#policy.customProp.1=adobePass.required=<TRUE or FALSE> 
#policy.customProp.1=adobePass.requestorID=<Requestor ID String> 
#policy.customProp.1=adobePass.resourceID=<Resource ID String>
```

>[!NOTE]
>
>Lors de l’utilisation de l’authentification Primetime en association avec la fonction de rotation de la licence (DRM), sachez que le jeton de média court (SMT) d’authentification Primetime a une courte date de validité. Si votre application prévoit d’utiliser la rotation de licence (par exemple, pour prendre en charge la fonction *Noires* (cas d’utilisation), l’application doit en être consciente et actualiser son jeton média court d’authentification Primetime avant de faire pivoter sa licence.
