---
seo-title: Authentification Adobe Primetime (facultatif)
title: Authentification Adobe Primetime (facultatif)
uuid: fa6225d6-e0e5-4fcc-ac26-4ff54f9f334a
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5

---


# Authentification Adobe Primetime (facultatif) {#adobe-primetime-authentication-optional}

Si la stratégie DRM utilisée pour assembler le contenu est une stratégie anonyme, une licence sera délivrée à toutes les demandes de licence. Si vous le souhaitez, Primetime Cloud DRM prend également en charge l’authentification via l’authentification Adobe Primetime. Si cette fonction est activée, une licence ne sera pas émise, à moins que le périphérique client n’ait d’abord acquis un jeton d’authentification Primetime et l’ait défini localement via l’API client appropriée ( `setAuthenticationToken`) pour définir des jetons d’authentification personnalisés. Pour plus d&#39;informations sur l&#39;intégration de l&#39;authentification Primetime dans votre processus d&#39;authentification, consultez : [Authentification Adobe Primetime.](https://tve.helpdocsonline.com/home)

Lors de l’acquisition de la licence, si la stratégie DRM indique que l’authentification Pri metime est requise, le serveur de licences analysera et validera le jeton de support court de l’authentification Primetime. Si la stratégie DRM spécifie un ou `ResourceID``RequestorID`, le serveur de licences valide également le jeton par rapport à ces propriétés. S’ils ne sont pas définis, le serveur de licences indiquera la ou les propriétés comme &quot;null&quot; lors de la validation du jeton. Une licence sera délivrée uniquement si la validation du jeton est réussie ; sinon, un DRMErrorEvent 3328 avec un sous-code d&#39;erreur 305 (Utilisateur non autorisé) sera distribué par le client.

Les paramètres d’authentification Primetime doivent être spécifiés dans la stratégie utilisée pour assembler le contenu destiné à nécessiter l’authentification Primetime.

Les propriétés appropriées sont les suivantes :

```
#policy.customProp.1=adobePass.required=<TRUE or FALSE> 
#policy.customProp.1=adobePass.requestorID=<Requestor ID String> 
#policy.customProp.1=adobePass.resourceID=<Resource ID String>
```

>[!NOTE]
>
>Lors de l’utilisation de l’authentification Primetime en association avec la fonction de rotation de la licence (DRM), gardez à l’esprit que le jeton SMT (Primetime authentication Short Media Token) a une courte date de validité. Si votre application envisage d&#39;utiliser la rotation de la licence (par exemple, pour prendre en charge le cas d&#39;utilisation des *coupures* de courant), elle doit en être informée et actualiser son jeton média court d&#39;authentification Primetime avant de faire pivoter sa licence.