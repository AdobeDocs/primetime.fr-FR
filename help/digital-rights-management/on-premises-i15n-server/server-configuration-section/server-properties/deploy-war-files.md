---
seo-title: Déploiement des fichiers WAR
title: Déploiement des fichiers WAR
uuid: 435a6a6e-c981-46fb-bca9-7f5f34eecd6a
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Déploiement des fichiers WAR{#deploy-the-war-files}

1. Copiez le fichier WAR dans le [!DNL webapps] répertoire de Tomcat.

   * Serveur d’individualisation : [!DNL flashaccess.war]
   * Serveur de génération de clés : [!DNL flashaccess-kgs.war]

1. Copiez le [!DNL ROOT] dossier du package fourni par Adobe dans le [!DNL webapps] répertoire.

   Le serveur d’individualisation doit également héberger le [!DNL crossdomain.xml] fichier. (Le [!DNL ROOT] dossier contient le [!DNL crossdomain.xml] fichier ; doit [!DNL ROOT] être en majuscules.) Le serveur de génération de clés ne nécessite pas ce fichier.

