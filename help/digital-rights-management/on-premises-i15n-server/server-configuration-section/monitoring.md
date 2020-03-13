---
seo-title: Surveillance
title: Surveillance
uuid: ee62c55f-0d44-40f4-a2c7-39456f4d3d99
translation-type: tm+mt
source-git-commit: 1547eb3dd220fafc08df923f40504736c16a866c

---


# Surveillance{#monitoring}

Le serveur d’individualisation et le serveur de génération de clés disposent chacun d’une page d’état, que vous pouvez utiliser pour déterminer l’état des serveurs.

* **Page d’état de l’individualisation :** [!DNL https://SERVER:PORT/flashaccess/status]

   * Signale &quot;Alive&quot; si le serveur d’applications est en cours d’exécution et que l’application peut envoyer une requête GET au serveur de génération de clés.
   * La page signale soit &quot;Vivant&quot;, soit rien. Aucune information sur l&#39;application n&#39;est révélée. Cette page peut donc être utilisée pour la surveillance depuis l&#39;extérieur du pare-feu.

* **Page d&#39;état Génération de clé :** [!DNL https://SERVER:PORT/flashaccess-kgs/status]

   * Signale &quot;En direct&quot; si le serveur d’applications est en cours d’exécution
   * Toutes les URL de génération de clés ne doivent être accessibles qu’en interne.

* **Page Statistiques d’individualisation :** [!DNL https://SERVER:PORT/flashaccess/admin/appstats]

   * Inclut des statistiques sur le serveur d’individualisation, telles que le nombre de requêtes servies et le nombre de clés disponibles dans le cache.
   * Cette page ne doit être accessible qu&#39;en interne

* **Page Statistiques de génération de clés :** [!DNL https://SERVER:PORT/flashaccess-kgs/appstats]

   * Comprend des statistiques sur le serveur de génération de clés, telles que le nombre de demandes servies et le nombre de fichiers clés disponibles sur le disque.
   * Toutes les URL de génération de clés ne doivent être accessibles qu’en interne.

