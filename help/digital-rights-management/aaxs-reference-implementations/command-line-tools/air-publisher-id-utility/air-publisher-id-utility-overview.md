---
title: Présentation de l’utilitaire d’identification de l’éditeur AIR
description: Présentation de l’utilitaire d’identification de l’éditeur AIR
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---


# Présentation de l’utilitaire d’identification de l’éditeur AIR {#air-publisher-id-utility-overview}

Dans le cadre du processus de création d’un fichier AIR, l’outil ADT (AIR Developer Tool) génère un identifiant d’éditeur. Il s’agit d’un identifiant unique au certificat utilisé pour créer le fichier AIR. Si vous réutilisez le même certificat pour plusieurs applications AIR, elles auront le même ID d&#39;éditeur. L&#39;utilitaire d&#39;identification de l&#39;éditeur AIR est utilisé pour calculer l&#39;ID d&#39;éditeur d&#39;une application AIR. Les versions d’AIR ultérieures à la version 1.5.2 n’écrivent pas l’ID d’éditeur généré dans un fichier. Il est donc nécessaire d’utiliser cet outil pour déterminer l’ID d’éditeur si vous utilisez une liste autorisée d’applications AIR.

>[!NOTE]
>
>L’ID d’éditeur, utilisé pour l’application de la liste autorisée AIR, n’est pas identique à l’ID d’éditeur spécifié par l’éditeur de l’application dans le fichier [!DNL application.xml] de l’application.
