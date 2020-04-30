---
description: Vous pouvez gérer les coupures de courant dans les flux vidéo en direct et fournir un autre contenu pendant une coupure de courant.
seo-description: Vous pouvez gérer les coupures de courant dans les flux vidéo en direct et fournir un autre contenu pendant une coupure de courant.
seo-title: Gestion des pannes de courant en direct
title: Gestion des pannes de courant en direct
uuid: df933087-c8a8-49eb-a016-6dfd971c219c
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Gestion des pannes de courant en direct{#handle-blackouts-in-live-streams}

Vous pouvez gérer les coupures de courant dans les flux vidéo en direct et fournir un autre contenu pendant une coupure de courant.

Lorsqu’une panne survient dans un flux en direct, votre lecteur utilise des gestionnaires de événement pour détecter la panne et fournir un autre contenu aux utilisateurs qui ne sont pas admissibles pour regarder le flux principal. Votre lecteur détecte le début et la fin de la période d’interruption, bascule la lecture du flux principal vers un flux alternatif et revient au flux principal à la fin de la période d’interruption.

Dans votre application cliente, vous vous abonnez aux balises blackout dans TVSDK. Lorsque vous êtes informé de nouveaux objets de métadonnées ** minutés, vous analysez les données de l’objet de métadonnées minutées afin de déterminer si l’objet indique une entrée ou une sortie de panne. Pour les pannes identifiées, vous appelez les éléments TVSDK pertinents pour passer à un autre contenu au début de la panne, puis de nouveau pour revenir au contenu principal lorsque la panne est terminée.

>[!TIP]
>
>Les clés sont toujours téléchargées à partir du manifeste avant la lecture du contenu.

Lorsqu’un utilisateur se connecte à un flux en direct après la fin de la période d’interruption et revient dans le temps à la période de blocage, le contenu est lu.

>[!IMPORTANT]
>
>Si toutes les requêtes clés échouent, une erreur est générée lors de l’analyse du manifeste. Si certaines requêtes échouent et que d’autres réussissent, TVSDK tente de lire le contenu. Si TVSDK tente de lire une section du contenu, mais qu’il n’existe aucune clé valide pour déchiffrer ce contenu, une erreur est renvoyée.

Pour gérer les pannes de courant en direct :

1. Configurez votre application pour détecter les balises d’arrêt en vous abonnant aux balises d’arrêt dans un manifeste de diffusion en direct.

   TVSDK ne détecte pas de balises d’interruption de service par ses propres moyens ; vous devez vous abonner à des balises d&#39;arrêt pour recevoir une notification lorsque les balises sont rencontrées lors de l&#39;analyse du fichier manifeste.
1. Créez des écouteurs de événement pour les balises auxquelles votre lecteur est abonné.

   Lorsqu’une balise se produit à laquelle votre lecteur s’est abonné (par exemple, une balise d’arrêt) dans le flux de premier plan (contenu principal) ou d’arrière-plan (contenu alternatif), TVSDK distribue une balise `TimedMetadataEvent` et crée une balise `TimedMetadataObject` pour le `TimedMetadataEvent`.
1. Mettez en oeuvre des gestionnaires pour les événements de métadonnées temporisés pour les flux de premier plan et d’arrière-plan.

   Dans ces gestionnaires, récupérez les heures de début et de fin de la période d’arrêt à partir des objets de événement de métadonnées minutés.
1. Préparez-les `MediaPlayer` aux pannes d&#39;électricité.

   Lorsque le `MediaPlayer` paramètre entre dans l’état PRÉPARÉ, vous calculez et préparez les plages d’interruptions et les définissez sur l’ `MediaPlayer` objet.

1. Pour chaque mise à jour de la position du curseur de lecture, vérifiez la liste de `TimedMetadataObjects`.

   C&#39;est là que votre lecteur détecte le début et la fin de la coupure et suit le moment de la coupure au fur et à mesure.

1. Créez des méthodes pour changer de contenu le début et la fin de la période d’interruption.

   Lorsque la période d’interruption début, basculez le contenu principal en arrière-plan et basculez le contenu alternatif pour en faire le flux principal. Continuez à récupérer et à analyser le manifeste d’origine en arrière-plan et continuez à rechercher la balise &quot;blackout end&quot;, de sorte que le lecteur puisse rejoindre le flux d’origine lorsque la coupure se termine.

