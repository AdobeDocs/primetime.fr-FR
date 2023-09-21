---
title: Règles de pare-feu
description: Règles de pare-feu
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '63'
ht-degree: 0%

---

# Règles de pare-feu{#firewall-rules}

Pour sécuriser l’accès au serveur d’individualisation, seuls certains chemins d’application doivent être exposés. Le serveur d’individualisation doit accepter les demandes des clients concernant ces chemins :

* [!DNL /flashaccess/i15n/*]
* [!DNL /flashaccess/status]
* [!DNL /crossdomain.xml]

Les chemins d’accès aux services, tels que [!DNL /flashaccess/admin/*] (c’est-à-dire, les pages d’état et d’administration) ne doivent être accessibles que depuis le pare-feu. Aucune partie du serveur de génération de clés ne doit être accessible en dehors du pare-feu.
