---
seo-title: Règles de pare-feu
title: Règles de pare-feu
uuid: f1629ceb-22de-4bb5-b73f-9b874d97ea8b
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Règles de pare-feu{#firewall-rules}

Pour sécuriser l’accès au serveur d’individualisation, seuls certains chemins d’application doivent être exposés. Le serveur d’individualisation doit accepter les demandes des clients aux chemins suivants :

* [!DNL /flashaccess/i15n/*]
* [!DNL /flashaccess/status]
* [!DNL /crossdomain.xml]

Les chemins d’accès aux services, tels que [!DNL /flashaccess/admin/*] (p. ex., les pages d’état et d’administration) ne doivent être accessibles que depuis le pare-feu. Aucune partie du serveur de génération de clés ne doit être accessible en dehors du pare-feu.
