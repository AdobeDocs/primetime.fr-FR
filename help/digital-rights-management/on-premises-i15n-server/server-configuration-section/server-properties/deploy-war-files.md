---
title: Déploiement des fichiers WAR
description: Déploiement des fichiers WAR
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Déploiement des fichiers WAR{#deploy-the-war-files}

1. Copiez le fichier WAR dans le fichier Tomcat [!DNL webapps] répertoire .

   * Individualization Server : [!DNL flashaccess.war]
   * Serveur de génération de clés : [!DNL flashaccess-kgs.war]

1. Copiez le [!DNL ROOT] du package fourni par Adobe au [!DNL webapps] répertoire .

   Le serveur d’individualisation doit également héberger la variable [!DNL crossdomain.xml] fichier . (La variable [!DNL ROOT] contient le dossier [!DNL crossdomain.xml] fichier; [!DNL ROOT] doit être en majuscules.) Le serveur de génération de clés ne nécessite pas ce fichier.
