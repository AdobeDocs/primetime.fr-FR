---
title: Point d’informations sur la stratégie
description: Point d’informations sur la stratégie
source-git-commit: ac0c15b951f305e29bb8fa0bd45aa2c53de6ad15
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---



# Point d’informations sur la stratégie {#pip}

>[!NOTE]
>
>Cette page est obsolète car elle s’applique à la version précédente de l’API qui n’est plus recommandée pour les nouvelles intégrations.

Le diagramme suivant montre le flux au cas où le client opterait pour la variable **Point d’informations sur la stratégie**, auquel cas CM est simplement utilisé pour interroger l’activité et toute la logique d’accès est incorporée dans l’application cliente) :

![](assets/pip-workflow.png)



Le diagramme ci-dessous illustre le fonctionnement du comptage de flux pour un utilisateur qui regarde le contenu de 2 appareils.

![](assets/pip-sequence.png)

En bref, le flux de message habituel est le suivant :

1. Au départ, pour un utilisateur qui n’a jamais utilisé le service, une page web est chargée/une application est ouverte, où une application instrumentée du service de surveillance de simultanéité effectue un appel d’initialisation de session.
1. Le service de surveillance de la simultanéité renvoie la nouvelle ressource de diffusion pour les pulsations, ainsi que l’activité de l’utilisateur actuelle.
1. Pendant la lecture vidéo, l’application instrumentée effectue des appels de pulsation au service de surveillance de la simultanéité, indiquant que l’utilisateur consomme actuellement une vidéo.
1. À tout autre moment, d’autres applications instrumentées peuvent effectuer des appels de requête d’état au service de surveillance de la simultanéité, qui renverra l’activité de l’utilisateur actuel.
1. Au niveau de la lecture vidéo, l’application instrumentée peut effectuer un appel de pulsation avec &quot;event=stop&quot;, ce qui signifie que la vidéo a été arrêtée et que la diffusion actuelle ne doit plus être comptée comme principale diffusion.

