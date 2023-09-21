---
title: Critique politique
description: Critique politique
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---

# Critique politique{#policy-criticality}

Si de nouvelles règles d’utilisation sont utilisées dans les stratégies et que celles-ci sont utilisées dans le contenu mis en package pour les serveurs de licences plus anciens (qui ne comprennent pas les nouvelles règles d’utilisation), vous pouvez spécifier le comportement des serveurs de licences plus anciens. Par défaut, la critique de la politique est &quot;true&quot;, ce qui signifie que le serveur de licences doit comprendre toutes les parties de la politique pour générer une licence à l’aide de la stratégie. Si la criticité de la stratégie est définie sur &quot;false&quot;, un ancien serveur de licences peut ignorer certaines parties de la stratégie qu’il ne comprend pas et les licences générées par le serveur ne contiendront pas les nouvelles règles d’utilisation.

Les serveurs Adobe Access utilisant la version 2.0.2 du SDK et les versions ultérieures respecteront le paramètre de criticité des politiques.
