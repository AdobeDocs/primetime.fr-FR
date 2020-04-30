---
seo-title: Licences pré-générées
title: Licences pré-générées
uuid: 0207abdf-52bb-4bd0-a4f2-fe740b89fa83
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Licences pré-générées{#pre-generating-licenses}

Si vous générez automatiquement des licences qui contiennent des règles d’utilisation temporelles, il est vivement recommandé que la licence comprenne des exigences de synchronisation (voir *Utilisation du guide Adobe Access SDK for Protecting Content* Guide), afin que l’expiration de la licence puisse être appliquée en toute sécurité. Il est fortement recommandé de mettre en oeuvre un mécanisme de &quot;battement cardiaque&quot; entre le client et le serveur si la licence comporte des restrictions temporelles, car la battement cardiaque synchronise le temps du client avec celui du serveur.
