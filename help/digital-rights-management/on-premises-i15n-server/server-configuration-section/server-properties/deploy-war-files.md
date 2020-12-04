---
seo-title: Déploiement des fichiers WAR
title: Déploiement des fichiers WAR
uuid: 435a6a6e-c981-46fb-bca9-7f5f34eecd6a
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
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

