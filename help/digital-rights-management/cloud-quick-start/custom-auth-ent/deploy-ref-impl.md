---
title: Déploiement de l’implémentation de référence BEES
description: Déploiement de l’implémentation de référence BEES
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
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
