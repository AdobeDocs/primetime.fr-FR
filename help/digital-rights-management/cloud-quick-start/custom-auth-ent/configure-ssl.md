---
title: Configuration du protocole SSL sur votre serveur BEES
description: Configuration du protocole SSL sur votre serveur BEES
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 0%

---

# Configuration du protocole SSL sur votre serveur BEES {#configure-ssl-on-your-bees-server}

1. Fournissez le certificat SSL de votre serveur à votre contact d’Adobe qui a fourni ce logiciel.

   Le certificat sera ajouté en tant que certificat approuvé au Trust Store Primetime Cloud DRM.
1. Pour activer l’authentification du client pour la connexion SSL (désactivée dans cette version) :
   1. Ajoutez la variable `[!DNL clouddrm-transport.cer]` et `[!DNL AdobeFlashAccessIntermediateCA.cer]` certificats au trust store utilisé pour l’authentification du client.
   1. Activez l’authentification du client dans votre configuration SSL.
