---
title: Licences pré-générées
description: Licences pré-générées
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 0%

---


# Licences prégénérées{#pre-generating-licenses}

Si vous générez des licences qui contiennent des règles d’utilisation temporelles, il est vivement recommandé que la licence inclut des exigences de synchronisation (voir *Utilisation du SDK Adobe Access pour la protection du contenu* guide), afin que l’expiration de la licence puisse être appliquée en toute sécurité. Il est fortement recommandé de mettre en oeuvre un mécanisme de &quot;battement cardiaque&quot; entre le client et le serveur si la licence comporte des restrictions temporelles, car la battement cardiaque synchronise le temps du client avec celui du serveur.
