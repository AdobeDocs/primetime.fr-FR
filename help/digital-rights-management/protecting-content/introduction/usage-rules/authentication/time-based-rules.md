---
seo-title: Règles temporelles
title: Règles temporelles
uuid: 19a6ee7e-9580-48bb-a3a6-ff2cedcc796a
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Règles temporelles {#time-based-rules}

Primetime DRM utilise l’application logicielle des restrictions de licence temporelles. Si un droit temporel expire pendant la lecture d’une vidéo, le comportement par défaut de Primetime DRM est de ne pas restreindre la lecture jusqu’à la prochaine recréation du flux vidéo (en appelant `Netstream.stop()` et `Netstream.play()`).

Bien que l’application souple soit le comportement par défaut, vous pouvez également l’activer en effectuant l’une des  suivantes :

* Demandez à votre lecteur vidéo d’interroger régulièrement la licence afin de vous assurer qu’aucune des restrictions de temps n’a expiré. Pour ce faire, appelez `DRMManager.loadVoucher(LOCAL_ONLY).` un code d’erreur indiquant que la licence stockée localement n’est plus valide.
* Chaque fois que l’utilisateur clique **[!UICONTROL Pause]**, vous pouvez enregistrer l’horodatage de la vidéo actuelle, puis appeler `Netstream.stop()`. Lorsque l’utilisateur clique sur le bouton Lecture, vous pouvez rechercher l’emplacement enregistré, puis appeler `Netstream.play()`.

## Date {#start-date}

La date de  du indique la date à laquelle une licence est valide.

Exemple de cas d’utilisation : Utilisez une date absolue pour émettre des licences de contenu avant la date de disponibilité d’un fichier ou pour imposer une période d’embargo.

## Date de fin {#end-date}

La date de fin indique la date d’expiration de la licence.

Exemple de cas d’utilisation : Utilisez une date d’expiration absolue pour refléter la fin des droits de distribution.

## Date de fin relative {#relative-end-date}

La date de fin relative indique la date d’expiration de la licence, exprimée par rapport à la date d’emballage, et non par rapport à la date d’émission de la licence.

Exemple de cas d’utilisation : Dans un processus d’assemblage automatisé, utilisez une seule stratégie DRM Primetime avec cette option pour une série de vidéos, afin de définir la date d’expiration sur 30 jours par rapport à la date d’emballage.

## Durée de mise en cache de la licence{#license-caching-duration}

La durée de mise en cache de la licence indique la durée pendant laquelle une licence peut être mise en cache sur le disque dans le magasin de licences local du client sans nécessiter une nouvelle acquisition à partir du serveur de licences. Vous pouvez également spécifier une date et une heure absolues après lesquelles une licence ne peut plus être mise en cache.

Une fois la date d’expiration du cache passée, la licence n’est plus valide et le client doit demander une nouvelle licence au serveur de licences.

Exemple de cas d’utilisation : Utilisez la durée de mise en cache de la licence pour spécifier une durée fixe valide pour une licence particulière, par exemple dans un cas d’utilisation locative. Vous pouvez spécifier une location de 30 jours (avec mise en cache des licences) pour indiquer la durée totale de la licence pour la consommation du contenu.

## Fenêtre de lecture {#playback-window}

La fenêtre de lecture indique la durée de validité d’une licence après sa première utilisation pour lire du contenu protégé.

Exemple de cas d’utilisation : Certains modèles d’entreprise prévoient une période de location de 30 jours, mais une fois la lecture commencée, la lecture doit être terminée dans 48 heures. Dans ce cas, la durée de 48 heures de la licence correspond à la fenêtre de lecture.

**A partir de la version 5.3 vers** l’avant - La fenêtre de lecture prend également en charge l’option d’activation ou de désactivation de l’arrêt en mode réel, qui indique si le contexte de déchiffrement pour la lecture doit s’arrêter à l’expiration de la fenêtre de lecture (activée) ou se poursuivre malgré l’expiration (désactivée).

>[!NOTE]
>
>L’option d’arrêt définitif ne fonctionne pas correctement avec la fenêtre de lecture si elle est utilisée conjointement (la fenêtre de lecture n’est pas respectée). La lecture de contenu avec la fenêtre de lecture sans arrêt sécurisé ne respecte pas la restriction de la fenêtre de lecture.