---
title: Présentation de l’utilitaire AIR Publisher ID
description: Présentation de l’utilitaire AIR Publisher ID
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---

# Présentation de l’utilitaire AIR Publisher ID {#air-publisher-id-utility-overview}

Dans le cadre du processus de création d’un fichier AIR, l’outil de développement AIR (ADT) génère un identifiant d’éditeur. Il s’agit d’un identifiant unique au certificat utilisé pour créer le fichier AIR. Si vous réutilisez le même certificat pour plusieurs applications AIR, elles auront le même identifiant d’éditeur. L’utilitaire AIR Publisher ID est utilisé pour calculer l’identifiant d’éditeur d’une application AIR. Les versions d’AIR ultérieures à la version 1.5.2 n’écrivent pas l’identifiant d’éditeur généré dans un fichier. Il est donc nécessaire d’utiliser cet outil pour déterminer l’identifiant d’éditeur si vous utilisez une liste autorisée d’application AIR.

>[!NOTE]
>
>L’identifiant de l’éditeur, utilisé pour l’application des listes autorisées AIR, n’est pas identique à l’identifiant de l’éditeur spécifié par l’éditeur de l’application dans le [!DNL application.xml] fichier .
