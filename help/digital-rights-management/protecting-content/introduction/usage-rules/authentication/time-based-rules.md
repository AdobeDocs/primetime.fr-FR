---
title: Règles temporelles
description: Règles temporelles
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# Règles temporelles {#time-based-rules}

Primetime DRM applique une &quot;application souple&quot; des restrictions de licence basées sur le temps. Si un droit temporel expire lors de la lecture d’une vidéo, le comportement par défaut de Primetime DRM est de ne pas restreindre la lecture jusqu’à la prochaine recréation du flux vidéo (en appelant `Netstream.stop()` et `Netstream.play()`).

Bien que l’application en douceur soit le comportement par défaut, vous pouvez également activer l’application en dur en effectuant l’une des tâches suivantes :

* Demandez à votre lecteur vidéo d’interroger régulièrement la licence pour s’assurer qu’aucune des restrictions de temps n’a expiré. Pour ce faire, appelez `DRMManager.loadVoucher(LOCAL_ONLY).` Un code d’erreur indique que la licence stockée localement n’est plus valide.
* Lorsque l’utilisateur clique **[!UICONTROL Pause]**, vous pouvez enregistrer l’horodatage vidéo actuel, puis appeler `Netstream.stop()`. Lorsque l’utilisateur clique sur le bouton Lecture , vous pouvez rechercher l’emplacement enregistré, puis appeler `Netstream.play()`.

## Date de début {#start-date}

La date de début indique la date de validité d’une licence.

Exemple de cas d’utilisation : utilisez une date absolue pour émettre des licences de contenu avant la date de disponibilité d’une ressource, ou pour appliquer un &quot;embargo&quot;.

## Date de fin {#end-date}

La date de fin indique la date à laquelle une licence expire.

Exemple de cas d’utilisation : utilisez une date d’expiration absolue pour refléter la fin des droits de distribution.

## Date de fin relative {#relative-end-date}

La date de fin relative spécifie la date d’expiration de la licence, exprimée par rapport à la date de l’emballage, et non par rapport à la date à laquelle la licence a été émise.

Exemple de cas d’utilisation : dans un processus de conditionnement automatisé, utilisez une seule stratégie DRM Primetime avec cette option pour une série de vidéos, afin de définir la date d’expiration sur 30 jours par rapport à la date de conditionnement.

## Durée de mise en cache de la licence{#license-caching-duration}

La durée de mise en cache des licences indique la durée pendant laquelle une licence peut être mise en cache sur le disque dans le magasin de licences local du client sans nécessiter de nouvelle acquisition de la part du serveur de licences. Vous pouvez également spécifier une date et une heure absolues au-delà desquelles une licence ne peut plus être mise en cache.

Une fois la date d’expiration du cache passée, la licence n’est plus valide et le client doit demander une nouvelle licence au serveur de licences.

Exemple de cas d’utilisation : utilisez la durée de mise en cache d’une licence pour spécifier une durée de validité fixe pour une licence spécifique, comme dans un cas d’utilisation de location. Vous pouvez indiquer une location de 30 jours (avec mise en cache de licence) pour indiquer la durée totale de la licence pendant laquelle le contenu doit être consommé.

## Fenêtre de lecture {#playback-window}

La fenêtre de lecture spécifie la durée de validité d’une licence après sa première utilisation pour lire du contenu protégé.

Exemple de cas d’utilisation : certains modèles d’entreprise autorisent une période de location de 30 jours, mais une fois la lecture commencée, celle-ci doit être terminée dans 48 heures. Dans ce cas, la durée de 48 heures de la licence correspond à la fenêtre de lecture.

**À partir de la version 5.3** - La fenêtre de lecture prend également en charge l’option d’activation ou de désactivation de l’arrêt en dur, qui indique si le contexte de déchiffrement de la lecture doit s’arrêter à l’expiration de la fenêtre de lecture (activée) ou continuer malgré l’expiration (désactivée).

>[!NOTE]
>
>L’option de blocage ne fonctionne pas correctement avec la fenêtre de lecture si elle est utilisée conjointement (la fenêtre de lecture ne sera pas respectée). La lecture du contenu avec la fenêtre de lecture sans arrêt sécurisé respecte la restriction de la fenêtre de lecture.
