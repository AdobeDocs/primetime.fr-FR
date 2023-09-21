---
description: TVSDK gère les erreurs de période en fonction du problème spécifique en fusionnant ou en réorganisant les périodes mal définies.
title: Gestion des erreurs de suppression et de remplacement des publicités
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# Gestion des erreurs de suppression et de remplacement des publicités  {#ad-deletion-and-replacement-error-handling}

TVSDK gère les erreurs de période en fonction du problème spécifique en fusionnant ou en réorganisant les périodes mal définies.

Gestion de TVSDK `timeRanges` erreurs via les processus de fusion et de réorganisation par défaut. Tout d’abord, le lecteur trie les périodes définies par le client en fonction de la variable *begin* temps. En fonction de cet ordre de tri, s’il existe des sous-ensembles et des intersections entre les plages, TVSDK fusionne les plages adjacentes et les relie.

TVSDK gère les erreurs de période avec les options suivantes :

* **En panne** TVSDK réorganise les périodes.

* **Sous-ensemble** TVSDK fusionne les sous-ensembles de périodes.

* **Intersection** TVSDK fusionne les plages intersections.

* **Conflit de plages de remplacement** TVSDK sélectionne la durée de remplacement à partir du plus ancien `timeRange` qui apparaît dans le groupe en conflit.

TVSDK gère les conflits en mode de signalisation avec les métadonnées publicitaires des manières suivantes :

* Si le mode de signalisation de la publicité est en conflit avec les métadonnées de période, les métadonnées de période ont toujours la priorité.

  Par exemple, si le mode de signalisation de la publicité est défini comme carte du serveur ou comme indicateurs de manifeste, et qu’il existe également des plages horaires MARK dans les métadonnées de publicité, le comportement résultant est que les plages sont marquées et qu’aucune publicité n’est insérée.
* Pour les plages REPLACE, si le mode de signalisation est défini comme carte du serveur ou comme indices manifestes, les plages sont remplacées comme spécifié dans les plages REPLACE et il n’y a pas d’insertion de publicités par le biais de la carte du serveur ou des indices manifestes.

  Pour plus d’informations, voir *Mode de signature/Comportements de combinaison des métadonnées* dans [Effet sur l’insertion et la suppression des publicités depuis le mode de signalisation publicitaire](../../../../../tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/delete-replace-content-vod/android-3x-signaling-mode-android.md).

Gardez à l’esprit les éléments suivants :

* Lorsque le serveur ne retourne pas valide `AdBreaks`, TVSDK génère et traite un `NOPTimelineOperation` pour l’AdBreak vide, et aucune publicité n’est lue.

* Bien que la suppression et le remplacement des publicités C3 soient prévus pour être pris en charge uniquement pour VOD, si spécifié dans les métadonnées de publicité, les plages de temps sont également traitées pour les diffusions en direct.
