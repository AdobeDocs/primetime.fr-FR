---
seo-title: Configuration de SSL sur votre serveur BEES
title: Configuration de SSL sur votre serveur BEES
uuid: 041a106e-8b21-4018-815d-b7ea48c3de03
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 0%

---


# Configurer SSL sur votre serveur BEES {#configure-ssl-on-your-bees-server}

1. Fournissez le certificat SSL de votre serveur à votre contact d’Adobe qui a fourni ce logiciel.

   Le certificat sera ajouté en tant que certificat approuvé au Trust Store de Primetime Cloud DRM.
1. Pour activer l’authentification du client pour la connexion SSL (désactivée dans cette version) :
   1. Ajoutez les certificats `[!DNL clouddrm-transport.cer]` et `[!DNL AdobeFlashAccessIntermediateCA.cer]` au Trust Store utilisé pour l’authentification du client.
   1. Activez l’authentification du client dans votre configuration SSL.
