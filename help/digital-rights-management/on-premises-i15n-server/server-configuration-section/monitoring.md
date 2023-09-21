---
title: Surveillance
description: Surveillance
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---

# Surveillance{#monitoring}

Les serveurs Individualization et Key Generation disposent chacun d’une page d’état que vous pouvez utiliser pour déterminer l’intégrité des serveurs.

* **Page d’état de l’individualisation :** [!DNL https://SERVER:PORT/flashaccess/status]

   * Signale &quot;Actif&quot; si le serveur d’applications est en cours d’exécution et que l’application peut envoyer une demande de GET au serveur de génération de clés.
   * La page indique soit &quot;Vivant&quot;, soit rien. Aucune information sur l’application n’est affichée. Cette page peut donc être utilisée pour la surveillance depuis l’extérieur du pare-feu.

* **Page d’état Génération de clés :** [!DNL https://SERVER:PORT/flashaccess-kgs/status]

   * Signale &quot;Actif&quot; si le serveur d’applications est en cours d’exécution
   * Toutes les URL de génération de clés ne doivent être accessibles qu’en interne.

* **Page Statistiques d’individualisation :** [!DNL https://SERVER:PORT/flashaccess/admin/appstats]

   * Inclut des statistiques sur le serveur d’individualisation, telles que le nombre de requêtes servies et le nombre de clés disponibles dans le cache.
   * Cette page doit uniquement être accessible en interne.

* **Page Statistiques de génération de clés :** [!DNL https://SERVER:PORT/flashaccess-kgs/appstats]

   * Inclut des statistiques sur le serveur de génération de clés, telles que le nombre de demandes traitées et le nombre de fichiers clés disponibles sur le disque.
   * Toutes les URL de génération de clés ne doivent être accessibles qu’en interne.
