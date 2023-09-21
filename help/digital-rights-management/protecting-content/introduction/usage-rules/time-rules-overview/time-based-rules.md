---
title: Règles temporelles - Aperçu
description: Règles temporelles - Aperçu
copied-description: true
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# Règles temporelles {#time-based-rules}

Primetime DRM applique une &quot;application souple&quot; des restrictions de licence basées sur le temps. Si un droit temporel expire lors de la lecture d’une vidéo, le comportement par défaut de Primetime DRM est de ne pas restreindre la lecture jusqu’à la prochaine recréation du flux vidéo (en appelant `Netstream.stop()` et `Netstream.play()`).

Bien que l’application en douceur soit le comportement par défaut, vous pouvez également activer l’application en dur en effectuant l’une des tâches suivantes :

* Demandez à votre lecteur vidéo d’interroger régulièrement la licence pour s’assurer qu’aucune des restrictions de temps n’a expiré. Pour ce faire, appelez `DRMManager.loadVoucher(LOCAL_ONLY).` Un code d’erreur indique que la licence stockée localement n’est plus valide.
* Lorsque l’utilisateur clique **[!UICONTROL Pause]**, vous pouvez enregistrer l’horodatage vidéo actuel, puis appeler `Netstream.stop()`. Lorsque l’utilisateur clique sur le bouton Lecture , vous pouvez rechercher l’emplacement enregistré, puis appeler `Netstream.play()`.