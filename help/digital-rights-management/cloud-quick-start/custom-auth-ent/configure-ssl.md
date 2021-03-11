---
title: Configuration de SSL sur votre serveur BEES
description: Configuration de SSL sur votre serveur BEES
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
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
