---
seo-title: Déploiement de l’implémentation de référence BEES
title: Déploiement de l’implémentation de référence BEES
uuid: 5ee7b066-8ae8-48ba-a3f0-8cc14b19d5c5
translation-type: tm+mt
source-git-commit: 4f196bbd079edeb1a423afee6b4b7e249d380f40
workflow-type: tm+mt
source-wordcount: '53'
ht-degree: 0%

---


# Déployer l&#39;implémentation de référence BEES {#deploy-the-bees-reference-implementation}

1. Configurez votre serveur d’applications Tomcat. (Consultez votre documentation Tomcat.)
1. Copiez le fichier `[!DNL bees.war]` dans le dossier [!DNL webapps/] de Tomcat.
1. Envoyez une demande à `https://localhost:8080/bees`.

   Si le message &quot;BEES is Operational&quot; s’affiche, le déploiement est terminé.
1. Activez SSL sur votre serveur.
