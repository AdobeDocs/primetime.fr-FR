---
title: Définition de règles temporelles
description: Définition de règles temporelles
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 0%

---

# Définition de règles temporelles {#defining-time-based-rules}

Adobe Access applique une &quot;application souple&quot; des restrictions de licence basées sur le temps. Si un droit temporel expire pendant la lecture d’une vidéo, le comportement par défaut de l’accès par Adobe est de ne pas restreindre la lecture jusqu’à la prochaine recréation de la diffusion vidéo (en appelant `Netstream.stop()` et `Netstream.play()`).

Bien que l’application en douceur soit le comportement par défaut, vous pouvez également activer l’application en dur en effectuant l’une des tâches suivantes :

* Demandez à votre lecteur vidéo d’interroger régulièrement la licence pour s’assurer qu’aucune des restrictions de temps n’a expiré. Pour ce faire, appelez `DRMManager.loadVoucher(LOCAL_ONLY).`Un code d’erreur indique que la licence stockée localement n’est plus valide.
* Chaque fois que l’utilisateur clique sur le bouton Pause , vous pouvez enregistrer l’horodatage actuel de la vidéo, puis appeler `Netstream.stop().`Lorsque l’utilisateur clique sur le bouton Lecture , vous pouvez rechercher l’emplacement enregistré, puis appeler `Netstream.play()`.

## Date de début {#start-date}

Indique la date à laquelle une licence est valide.

Exemple de cas d’utilisation : utilisez une date absolue pour émettre des licences de contenu avant la date de disponibilité d’une ressource, ou pour appliquer un &quot;embargo&quot;.

## Date de fin {#end-date}

Indique la date d’expiration d’une licence.

Exemple de cas d’utilisation : utilisez une date d’expiration absolue pour refléter la fin des droits de distribution.

## Date de fin relative {#relative-end-date}

Indique la date d’expiration de la licence, exprimée par rapport à la date du package.

Exemple de cas d’utilisation : dans un processus de conditionnement automatisé, utilisez une seule stratégie avec cette option pour une série de vidéos afin de définir la date d’expiration sur 30 jours par rapport à la date de conditionnement.

## Durée de mise en cache de la licence {#license-caching-duration}

Spécifie la durée pendant laquelle une licence peut être mise en cache sur le disque dans le magasin de licences local du client sans nécessiter de nouvelle acquisition de la part du serveur de licences. Vous pouvez également spécifier une date/heure absolue au-delà de laquelle une licence ne peut plus être mise en cache.

Une fois la date d’expiration du cache passée, la licence n’est plus valide et le client doit demander une nouvelle licence au serveur de licences.

Exemple de cas d’utilisation : utilisez la durée de mise en cache d’une licence pour spécifier une durée de validité fixe pour une licence spécifique, comme dans un cas d’utilisation de location. Vous pouvez spécifier une location de 30 jours (avec mise en cache de licence) pour indiquer la durée totale de la licence pendant laquelle le contenu doit être consommé.

## Fenêtre de lecture {#playback-window}

Indique la durée de validité d’une licence après sa première utilisation pour lire du contenu protégé.

Exemple de cas d’utilisation : certains modèles d’entreprise autorisent une période de location de 30 jours, mais une fois la lecture commencée, elle doit être terminée dans 48 heures. Cette longévité de 48 heures de la licence est définie comme la fenêtre de lecture.

## Conditions requises pour la synchronisation {#requirements-for-synchronization}

Indique la fréquence à laquelle le client synchronise son état avec le serveur. Si le client a reçu une licence hors-bande (sans contact avec un serveur de licences), les règles d’utilisation peuvent spécifier que le client doit envoyer des messages de synchronisation au serveur afin de synchroniser l’heure sécurisée du client et de signaler l’état du client au serveur.

Le comportement de synchronisation est défini à l&#39;aide des paramètres suivants :

* Intervalle de début : indique la durée d’attente après la dernière synchronisation réussie pour démarrer une autre requête de synchronisation.
* Intervalle d’arrêt hard (facultatif). Interdire la lecture si une synchronisation réussie ne s’est pas produite pendant la durée spécifiée.
* Forcer la probabilité de synchronisation — (facultatif). Probabilité avec laquelle le client doit envoyer un message de synchronisation avant l’intervalle de démarrage suivant.

>[!NOTE]
>
>Cette règle d’utilisation est prise en charge par les clients Adobe Access versions 3.0 et ultérieures. Le comportement sur les clients plus anciens dépend de la version client minimale prise en charge par le serveur de licences. Voir [Version minimale du client](../../../../aaxs-protecting-content/content-implementing-the-license-server/content-handling-license-reqs/content-minimum-client-version.md).
