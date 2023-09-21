---
title: Licences pré-générées
description: Licences pré-générées
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 0%

---

# Licences pré-générées{#pre-generating-licenses}

Si vous prégénérez des licences qui contiennent des règles d’utilisation basées sur le temps, il est vivement recommandé que la licence inclut des exigences de synchronisation (voir *Utilisation du SDK Adobe Access pour la protection du contenu* ), afin que l’expiration de licence puisse être appliquée en toute sécurité. La mise en oeuvre d’un mécanisme de &quot;pulsation&quot; entre le client et le serveur est vivement recommandée si la licence contient des restrictions temporelles, car la pulsation synchronise l’heure du client avec l’heure du serveur.
