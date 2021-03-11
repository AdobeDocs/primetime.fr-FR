---
title: Déploiement des fichiers WAR
description: Déploiement des fichiers WAR
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 0%

---


# Déploiement des fichiers WAR{#deploy-the-war-files}

1. Copiez le fichier WAR dans le répertoire [!DNL webapps] de Tomcat.

   * Serveur d’individualisation : [!DNL flashaccess.war]
   * Serveur de génération de clés : [!DNL flashaccess-kgs.war]

1. Copiez le dossier [!DNL ROOT] du package fourni par Adobe dans le répertoire [!DNL webapps].

   Le serveur d’individualisation doit également héberger le fichier [!DNL crossdomain.xml]. (Le dossier [!DNL ROOT] contient le fichier [!DNL crossdomain.xml]; [!DNL ROOT] doit être dans tous les capitales.) Le serveur de génération de clés ne nécessite pas ce fichier.

