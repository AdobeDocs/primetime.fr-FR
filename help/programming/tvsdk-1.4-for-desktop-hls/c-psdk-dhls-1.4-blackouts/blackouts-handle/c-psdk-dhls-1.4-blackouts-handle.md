---
description: Vous pouvez gérer les pannes de courant dans les diffusions vidéo en direct et fournir un contenu alternatif lors d’une panne.
title: Gestion des pannes de courant dans les flux en direct
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 0%

---

# Gestion des pannes de courant dans les flux en direct{#handle-blackouts-in-live-streams}

Vous pouvez gérer les pannes de courant dans les diffusions vidéo en direct et fournir un contenu alternatif lors d’une panne.

Lorsqu’un blackout se produit dans un flux en direct, votre lecteur utilise des gestionnaires d’événements pour détecter le blackout et fournir un contenu alternatif à ces utilisateurs qui ne sont pas éligibles pour regarder le flux principal. Votre lecteur détecte le début et la fin de la période d’interruption, bascule la lecture de la diffusion principale vers une diffusion alternative et revient à la diffusion principale lorsque la période d’interruption se termine.

Dans votre application cliente, vous vous abonnez aux balises de blackout dans TVSDK. Lors de la notification de la nouvelle *métadonnées minutées* , vous analysez les données de l’objet de métadonnées minutées afin d’identifier si l’objet indique une entrée ou une sortie blackout. Pour les pannes identifiées, vous appelez les éléments TVSDK pertinents pour passer au contenu alternatif au début de la pannes, puis de nouveau pour revenir au contenu principal lorsque la pannes est terminée.

>[!TIP]
>
>Les clés sont toujours téléchargées à partir du manifeste avant la lecture du contenu.

Lorsqu’un utilisateur se connecte à un flux actif une fois la période de blackout terminée et qu’il fait défiler à nouveau dans le temps jusqu’à la période de blocage, le contenu est lu.

>[!IMPORTANT]
>
>Si toutes les demandes clés échouent, une erreur est générée lors de l’analyse du manifeste. Si certaines requêtes échouent et que d’autres réussissent, TVSDK tente de lire le contenu. Si TVSDK tente de lire une section du contenu, mais qu’il n’existe pas de clé valide pour déchiffrer ce contenu, il renvoie une erreur.

Pour gérer les pannes de courant dans les flux en direct :

1. Configurez votre application pour détecter les balises de blackout en vous abonnant aux balises de blackout dans un manifeste de diffusion en direct.

   TVSDK ne détecte pas les balises de blackout par lui-même ; vous devez vous abonner aux balises de blackout pour recevoir une notification lorsque les balises sont rencontrées lors de l’analyse du fichier manifeste.
1. Créez des écouteurs d’événement pour les balises auxquelles votre lecteur est abonné.

   Lorsqu’une balise se produit à laquelle votre lecteur s’est abonné (par exemple, une balise d’interruption) dans les manifestes de diffusion de premier plan (contenu principal) ou en arrière-plan (contenu alternatif), TVSDK envoie une `TimedMetadataEvent` et crée une `TimedMetadataObject` pour le `TimedMetadataEvent`.
1. Mettez en oeuvre des gestionnaires pour les événements de métadonnées minutés pour les flux de premier plan et d’arrière-plan.

   Dans ces gestionnaires, obtenez les heures de début et de fin de la période d’interruption à partir des objets d’événement de métadonnées minutés.
1. Préparez le `MediaPlayer` pour les coupures d&#39;électricité.

   Lorsque la variable `MediaPlayer` entre à l’état PRÉPARÉ, vous calculez et préparez les plages d’blackout et les définissez sur l’événement `MediaPlayer` objet.

1. Pour chaque mise à jour de la position du curseur de lecture, vérifiez la liste des `TimedMetadataObjects`.

   C’est là que votre lecteur détecte le début et la fin de la coupure et suit l’heure de la coupure au fur et à mesure.

1. Créez des méthodes pour changer de contenu au début et à la fin de la période de blackout.

   Au début de la période d’interruption, basculez le contenu principal en arrière-plan et changez le contenu alternatif pour devenir la diffusion principale. Continuez à récupérer et à analyser le manifeste d’origine en arrière-plan et à rechercher la balise &quot;blackout end&quot;, de sorte que le lecteur puisse rejoindre le flux d’origine à la fin du blackout.
