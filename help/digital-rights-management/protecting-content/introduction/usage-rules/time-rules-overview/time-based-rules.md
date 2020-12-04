---
seo-title: Présentation des règles temporelles
title: Présentation des règles temporelles
uuid: 10b7766e-3b1a-4d8a-ba15-46976aa0847d
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# Règles temporelles {#time-based-rules}

Primetime DRM utilise une &quot;application souple&quot; des restrictions de licence temporelles. Si un droit temporel expire pendant la lecture d’une vidéo, le comportement par défaut de Primetime DRM est de ne pas restreindre la lecture jusqu’à la prochaine recréation du flux vidéo (en appelant `Netstream.stop()` et `Netstream.play()`).

Bien que l’application souple soit le comportement par défaut, vous pouvez également activer l’application stricte en exécutant l’une des tâches suivantes :

* Demandez à votre lecteur vidéo d’interroger régulièrement la licence afin de s’assurer qu’aucune des restrictions de temps n’a expiré. Pour ce faire, appelez `DRMManager.loadVoucher(LOCAL_ONLY).`. Un code d&#39;erreur indique que la licence stockée localement n&#39;est plus valide.
* Chaque fois que l’utilisateur clique sur **[!UICONTROL Pause]**, vous pouvez enregistrer l’horodatage de la vidéo actuelle, puis appeler `Netstream.stop()`. Lorsque l’utilisateur clique sur le bouton Lecture, vous pouvez rechercher l’emplacement enregistré, puis appeler `Netstream.play()`.