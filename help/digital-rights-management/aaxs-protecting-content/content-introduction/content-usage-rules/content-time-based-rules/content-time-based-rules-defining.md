---
seo-title: Définition de règles temporelles
title: Définition de règles temporelles
uuid: 17c69869-ac81-4561-9fb6-b1c5c9c4006d
translation-type: tm+mt
source-git-commit: 53654b740b03c6a79394d30704a41186d4655237

---


# Définition de règles temporelles {#defining-time-based-rules}

Adobe Access applique une &quot;application souple&quot; des restrictions de licence temporelles. Si un droit temporel expire pendant la lecture d’une vidéo, le comportement par défaut d’Adobe Access consiste à ne pas restreindre la lecture jusqu’à la prochaine recréation du flux vidéo (en appelant `Netstream.stop()` et `Netstream.play()`).

Bien que l’application souple soit le comportement par défaut, vous pouvez également l’activer en effectuant l’une des  suivantes :

* Demandez à votre lecteur vidéo d’interroger régulièrement la licence afin de vous assurer qu’aucune des restrictions de temps n’a expiré. Pour ce faire, appelez `DRMManager.loadVoucher(LOCAL_ONLY).`un code d’erreur indiquant que la licence stockée localement n’est plus valide.
* Chaque fois que l’utilisateur clique sur le bouton Pause, vous pouvez enregistrer l’horodatage de la vidéo actuelle, puis appeler `Netstream.stop().`Lorsque l’utilisateur clique sur le bouton Lecture, vous pouvez rechercher l’emplacement enregistré, puis appeler `Netstream.play()`.

## Date {#start-date}

Indique la date de validité d’une licence.

Exemple de cas d’utilisation : Utilisez une date absolue pour émettre des licences de contenu avant la date de disponibilité d’un fichier ou pour imposer une période d’embargo.

## Date de fin {#end-date}

Indique la date d’expiration d’une licence.

Exemple de cas d’utilisation : Utilisez une date d’expiration absolue pour refléter la fin des droits de distribution.

## Date de fin relative {#relative-end-date}

Indique la date d’expiration de la licence, exprimée par rapport à la date de création du pack.

Exemple de cas d’utilisation : Dans un processus d’assemblage automatisé, utilisez une stratégie unique avec cette option pour une série de vidéos afin de définir la date d’expiration sur 30 jours par rapport à la date d’assemblage.

## Durée de mise en cache de la licence {#license-caching-duration}

Indique la durée pendant laquelle une licence peut être mise en cache sur le disque dans le magasin de licences local du client sans nécessiter une nouvelle acquisition à partir du serveur de licences. Vous pouvez également spécifier une date/heure absolue après laquelle une licence ne peut plus être mise en cache.

Une fois la date d’expiration du cache passée, la licence n’est plus valide et le client doit demander une nouvelle licence au serveur de licences.

Exemple de cas d’utilisation : Utilisez la durée de mise en cache de la licence pour spécifier une durée fixe valide pour une licence particulière, par exemple dans un cas d’utilisation locative. Une location de 30 jours peut être spécifiée (avec mise en cache des licences) pour indiquer la durée totale de la licence pour la consommation du contenu.

## Fenêtre de lecture {#playback-window}

Indique la durée de validité d’une licence après sa première utilisation pour lire le contenu protégé.

Exemple de cas d’utilisation : Certains modèles d&#39;entreprise permettent une période de location de 30 jours, mais une fois la lecture commencée, elle doit être terminée dans 48 heures. Cette durée de vie de 48 heures de la licence est définie comme la fenêtre de lecture.

## Conditions requises pour la synchronisation {#requirements-for-synchronization}

Indique la fréquence à laquelle le client synchronise son état avec le serveur. Si le client a reçu une licence hors bande (sans contact avec un serveur de licences), les règles d’utilisation peuvent spécifier que le client doit envoyer des messages de synchronisation au serveur afin de synchroniser l’heure sécurisée du client et de signaler l’état du client au serveur.

Le comportement de synchronisation est défini à l’aide des paramètres suivants :

* Intervalle  — Indique le délai d’attente après la dernière synchronisation réussie pour d’une autre requête de synchronisation.
* Intervalle d&#39;arrêt fixe — (Facultatif). Interdire la lecture si une synchronisation réussie ne s’est pas produite pendant la durée spécifiée.
* Forcer la probabilité de synchronisation — (Facultatif). Probabilité avec laquelle le client doit envoyer un message de synchronisation avant l’intervalle de  suivant.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Cette règle d’utilisation est prise en charge par les clients Adobe Access versions 3.0 et ultérieures. Le comportement sur les anciens clients dépend de la version minimale du client prise en charge par le serveur de licences. Voir Version [](../../../../aaxs-protecting-content/content-implementing-the-license-server/content-handling-license-reqs/content-minimum-client-version.md)minimale du client.