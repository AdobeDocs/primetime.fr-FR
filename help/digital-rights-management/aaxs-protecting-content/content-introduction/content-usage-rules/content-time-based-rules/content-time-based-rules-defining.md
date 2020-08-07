---
seo-title: Définition de règles temporelles
title: Définition de règles temporelles
uuid: 17c69869-ac81-4561-9fb6-b1c5c9c4006d
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 0%

---


# Définition de règles temporelles {#defining-time-based-rules}

adobe Access utilise une &quot;application souple&quot; des restrictions de licence temporelles. Si un droit de lecture expire au cours de la lecture d’une vidéo, le comportement par défaut d’Accès Adobe consiste à ne pas restreindre la lecture jusqu’à la prochaine recréation du flux vidéo (en appelant `Netstream.stop()` et `Netstream.play()`).

Bien que l’application souple soit le comportement par défaut, vous pouvez également activer l’application stricte en exécutant l’une des tâches suivantes :

* Demandez à votre lecteur vidéo d’interroger régulièrement la licence afin de s’assurer qu’aucune des restrictions de temps n’a expiré. Pour ce faire, appelez `DRMManager.loadVoucher(LOCAL_ONLY).`un code d&#39;erreur indiquant que la licence stockée en local n&#39;est plus valide.
* Chaque fois que l’utilisateur clique sur le bouton Pause, vous pouvez enregistrer l’horodatage de la vidéo en cours, puis appeler `Netstream.stop().`Lorsque l’utilisateur clique sur le bouton Lecture, vous pouvez rechercher l’emplacement enregistré, puis appeler `Netstream.play()`.

## Date début {#start-date}

Indique la date à laquelle une licence est valide.

Exemple de cas d’utilisation : Utilisez une date absolue pour émettre des licences de contenu avant la date de disponibilité d&#39;un fichier ou pour imposer un &quot;embargo&quot;.

## Date de fin {#end-date}

Indique la date d’expiration des licences.

Exemple de cas d’utilisation : Utilisez une date d&#39;expiration absolue pour refléter la fin des droits de distribution.

## Date de fin relative {#relative-end-date}

Indique la date d’expiration de la licence, exprimée par rapport à la date de création du pack.

Exemple de cas d’utilisation : Dans un processus d’emballage automatisé, utilisez une seule stratégie avec cette option pour une série de vidéos afin de définir la date d’expiration sur 30 jours par rapport à la date d’emballage.

## Durée de mise en cache de la licence {#license-caching-duration}

Indique la durée pendant laquelle une licence peut être mise en cache sur le disque dans le magasin de licences local du client sans nécessiter de réacquisition à partir du serveur de licences. Vous pouvez également spécifier une date/heure absolue après laquelle une licence ne peut plus être mise en cache.

Une fois la date d’expiration du cache passée, la licence n’est plus valide et le client doit demander une nouvelle licence au serveur de licences.

Exemple de cas d’utilisation : Utilisez la durée de mise en cache de la licence pour spécifier une durée fixe valide pour une licence particulière, par exemple dans un cas d’utilisation de la location. Une location de 30 jours peut être spécifiée (avec mise en cache des licences) pour indiquer la durée totale de la licence pendant laquelle consommer le contenu.

## Fenêtre de lecture {#playback-window}

Indique la durée de validité d’une licence après sa première utilisation pour lire du contenu protégé.

Exemple de cas d’utilisation : Certains modèles d&#39;entreprise permettent une période de location de 30 jours mais, une fois la lecture commencée, elle doit être terminée en 48 heures. Cette longévité de 48 heures de la licence est définie comme la fenêtre de lecture.

## Conditions requises pour la synchronisation {#requirements-for-synchronization}

Indique la fréquence à laquelle le client synchronise son état avec le serveur. Si le client a reçu une licence hors bande (sans contact avec un serveur de licences), les règles d’utilisation peuvent spécifier que le client doit envoyer des messages de synchronisation au serveur afin de synchroniser l’heure sécurisée du client et de signaler l’état du client au serveur.

Le comportement de synchronisation est défini à l’aide des paramètres suivants :

* Intervalle de début : indique le délai d&#39;attente après la dernière synchronisation réussie pour début d&#39;une autre demande de synchronisation.
* Intervalle d’arrêt définitif — (facultatif). Interdire la lecture si une synchronisation réussie n’a pas eu lieu pendant la durée spécifiée.
* Forcer la probabilité de synchronisation — (facultatif). Probabilité avec laquelle le client doit envoyer un message de synchronisation avant l&#39;intervalle de début suivant.

>[!NOTE]
>
>Cette règle d&#39;utilisation est prise en charge par les clients Adobe Access version 3.0 et ultérieure. Le comportement des clients plus anciens dépend de la version minimale du client prise en charge par le serveur de licences. Voir Version [](../../../../aaxs-protecting-content/content-implementing-the-license-server/content-handling-license-reqs/content-minimum-client-version.md)minimale du client.