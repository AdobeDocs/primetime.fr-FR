---
seo-title: Présentation des règles temporelles
title: Présentation des règles temporelles
uuid: 10b7766e-3b1a-4d8a-ba15-46976aa0847d
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc

---


# Règles temporelles {#time-based-rules}

Primetime DRM utilise l’application logicielle des restrictions de licence temporelles. Si un droit temporel expire pendant la lecture d’une vidéo, le comportement par défaut de Primetime DRM est de ne pas restreindre la lecture jusqu’à la prochaine recréation du flux vidéo (en appelant `Netstream.stop()` et `Netstream.play()`).

Bien que l’application souple soit le comportement par défaut, vous pouvez également l’activer en effectuant l’une des  suivantes :

* Demandez à votre lecteur vidéo d’interroger régulièrement la licence afin de vous assurer qu’aucune des restrictions de temps n’a expiré. Pour ce faire, appelez `DRMManager.loadVoucher(LOCAL_ONLY).` un code d’erreur indiquant que la licence stockée localement n’est plus valide.
* Chaque fois que l’utilisateur clique **[!UICONTROL Pause]**, vous pouvez enregistrer l’horodatage de la vidéo actuelle, puis appeler `Netstream.stop()`. Lorsque l’utilisateur clique sur le bouton Lecture, vous pouvez rechercher l’emplacement enregistré, puis appeler `Netstream.play()`.