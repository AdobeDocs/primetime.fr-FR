---
seo-title: Importance des politiques
title: Importance des politiques
uuid: 076f386e-ba58-4507-92a3-a190126c881e
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---


# Critique de la politique{#policy-criticality}

Si de nouvelles règles d’utilisation sont utilisées dans les stratégies et que celles-ci sont utilisées dans le contenu conditionné pour les anciens serveurs de licences (qui ne comprennent pas les nouvelles règles d’utilisation), vous pouvez indiquer comment les anciens serveurs de licences doivent se comporter. Par défaut, la criticité de la stratégie est &quot;true&quot;, ce qui signifie que le serveur de licences doit comprendre toutes les parties de la stratégie pour générer une licence à l’aide de la stratégie. Si la criticité de la stratégie est définie sur &quot;false&quot;, un ancien serveur de licences peut ignorer certaines parties de la stratégie qu’il ne comprend pas et les licences générées par le serveur ne contiendront pas les nouvelles règles d’utilisation.

Les serveurs d’accès aux Adobes utilisant la version 2.0.2 du SDK et les versions ultérieures respecteront le paramètre de criticité des stratégies.
