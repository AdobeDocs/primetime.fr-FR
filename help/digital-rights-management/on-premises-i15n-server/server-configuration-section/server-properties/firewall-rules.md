---
title: Règles de pare-feu
description: Règles de pare-feu
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '63'
ht-degree: 0%

---


# Règles de pare-feu{#firewall-rules}

Pour sécuriser l’accès au serveur d’individualisation, seuls certains chemins d’application doivent être exposés. Le serveur d’individualisation doit accepter les demandes des clients aux chemins suivants :

* [!DNL /flashaccess/i15n/*]
* [!DNL /flashaccess/status]
* [!DNL /crossdomain.xml]

Les chemins d&#39;accès aux services, tels que [!DNL /flashaccess/admin/*] (c&#39;est-à-dire les pages d&#39;état et d&#39;administration) ne doivent être accessibles que depuis le pare-feu. Aucune partie du serveur de génération de clés ne doit être accessible en dehors du pare-feu.
