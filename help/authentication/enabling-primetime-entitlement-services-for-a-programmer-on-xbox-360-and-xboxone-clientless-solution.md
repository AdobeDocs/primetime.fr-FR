---
title: Activation des Services de droits Primetime pour un programmeur sur Xbox 360 et XboxOne sans client
description: Activation des Services de droits Primetime pour un programmeur sur Xbox 360 et XboxOne sans client
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# Activation des Services de droits Primetime pour un programmeur sur Xbox 360 et XboxOne sans client {#enabling-primetime-entitlement-services-for-a-programer-on-xbox-360-and-xboxone-clientless}

>[!NOTE]
>
>Le contenu de cette page est fourni à titre d’information uniquement. L’utilisation de cette API nécessite une licence actuelle de Adobe. Aucune utilisation non autorisée n’est autorisée.




1. Le programmeur crée un ticket Zendesk pour activer la solution sans client d&#39;authentification Xbox 360/One pour Primetime en fournissant les informations suivantes :

   1. Plate-forme : ex. Xbox 360, Xbox One

   1. Identifiant du demandeur : netgeo, CNN, etc.

1. Adobe va créer des certificats X509 et configurer la clé privée et le mot de passe à sa fin.

1. Adobe fournira le certificat public (du certificat X509) au programmeur dans le ticket ou par email.

1. Le programmeur devra ensuite installer ce certificat public sur le portail GDNP pour l’application enregistrée sur Microsoft.

1. Le programmeur demandera alors le JWT (Java Web Token) ou le Jeton STS pour XboxOne ou 360 respectivement auprès du service Microsoft Xbox Live, qui serait crypté à l&#39;aide du certificat public X509 fourni à l&#39;étape 3.

1. Il s’agit des jetons qui contiennent l’deviceId unique pour les périphériques Xbox. Incluez le jeton (JWT ou STS) dans l’en-tête d’autorisation à l’aide d’un paramètre &#39;x&#39; comme ci-dessous :

   1. Pour Xbox 360, le jeton XSTS doit être encodé en Base64 avant d&#39;être envoyé vers l&#39;authentification Primetime Pay-TV.
   1. Pour Xbox One, le JWT est déjà correctement encodé. Aucun encodage supplémentaire ne doit donc avoir lieu.

1. Tous les appels API du périphérique Xbox doivent contenir l’en-tête d’autorisation avec le jeton mentionné ci-dessus dans le paramètre x.



>[!NOTE]
>
>La Xbox en particulier a des exigences uniques liées à la signature numérique. L’identifiant de périphérique de la console XBox est inclus dans le jeton XSTS.  Pour Xbox 360, il s&#39;agit d&#39;une assertion SAML chiffrée ; pour Xbox One, il s&#39;agit d&#39;un JWT chiffré. L’application de console XBox envoie l’intégralité du jeton XSTS à l’authentification payante Primetime. L’authentification payante Primetime décrypte le jeton à l’aide de sa clé publique, analyse le jeton et extrait le deviceId de celui-ci.

>[!NOTE]
>
>En raison de la longueur importante du jeton XSTS, la console XBox présente une limitation technique : elle ne peut pas envoyer le jeton en tant que paramètre de GET HTTP aux API d’authentification de télévision payante Primetime. Pour ce faire, l’authentification payante Primetime permet d’envoyer le jeton XSTS dans le cadre de l’en-tête HTTP &quot;Authorization&quot; lors de l’appel des API. Le jeton XSTS doit être chiffré à l’aide de la clé publique du certificat X.509 émis au programmeur à partir de l’authentification payante Primetime. L’authentification payante Primetime stocke la clé privée associée et l’utilise pour déchiffrer le jeton XSTS et en extraire l’deviceId.
