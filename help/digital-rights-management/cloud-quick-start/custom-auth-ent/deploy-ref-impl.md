---
title: Déploiement de l’implémentation de référence BEES
description: Déploiement de l’implémentation de référence BEES
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '53'
ht-degree: 0%

---

# Déploiement de l’implémentation de référence BEES {#deploy-the-bees-reference-implementation}

1. Configurez votre serveur d’applications Tomcat. (Voir votre documentation Tomcat.)
1. Copiez le `[!DNL bees.war]` dans le fichier Tomcat [!DNL webapps/] dossier.
1. Envoi d’une requête à `https://localhost:8080/bees`.

   Si un message &quot;BEES est opérationnel&quot; s’affiche, le déploiement est terminé.
1. Activez SSL sur votre serveur.
