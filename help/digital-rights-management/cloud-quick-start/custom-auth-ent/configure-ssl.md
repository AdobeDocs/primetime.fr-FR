---
seo-title: Configuration de SSL sur votre serveur BEES
title: Configuration de SSL sur votre serveur BEES
uuid: 041a106e-8b21-4018-815d-b7ea48c3de03
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5

---


# Configuration de SSL sur votre serveur BEES {#configure-ssl-on-your-bees-server}

1. Fournissez le certificat SSL de votre serveur à votre contact Adobe qui a fourni ce logiciel.

   Le certificat sera ajouté en tant que certificat approuvé au magasin d’approbation DRM de Primetime Cloud.
1. Pour activer l’authentification du client pour la connexion SSL (désactivée dans cette version) :
   1. Ajouter les `[!DNL clouddrm-transport.cer]` certificats et les `[!DNL AdobeFlashAccessIntermediateCA.cer]` certificats au Trust Store utilisé pour l’authentification du client.
   1. Activez l’authentification du client dans votre configuration SSL.
