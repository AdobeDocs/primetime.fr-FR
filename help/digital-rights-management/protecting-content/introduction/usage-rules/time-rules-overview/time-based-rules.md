---
title: Présentation des règles temporelles
description: Présentation des règles temporelles
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# Règles temporelles {#time-based-rules}

Primetime DRM utilise une &quot;application souple&quot; des restrictions de licence temporelles. Si un droit temporel expire pendant la lecture d’une vidéo, le comportement par défaut de Primetime DRM est de ne pas restreindre la lecture jusqu’à la prochaine recréation du flux vidéo (en appelant `Netstream.stop()` et `Netstream.play()`).

Bien que l’application souple soit le comportement par défaut, vous pouvez également activer l’application stricte en exécutant l’une des tâches suivantes :

* Demandez à votre lecteur vidéo d’interroger régulièrement la licence afin de s’assurer qu’aucune des restrictions de temps n’a expiré. Pour ce faire, appelez `DRMManager.loadVoucher(LOCAL_ONLY).`. Un code d&#39;erreur indique que la licence stockée localement n&#39;est plus valide.
* Chaque fois que l’utilisateur clique sur **[!UICONTROL Pause]**, vous pouvez enregistrer l’horodatage de la vidéo actuelle, puis appeler `Netstream.stop()`. Lorsque l’utilisateur clique sur le bouton Lecture, vous pouvez rechercher l’emplacement enregistré, puis appeler `Netstream.play()`.