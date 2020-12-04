---
description: Pour utiliser TVSDK de manière efficace, vous devez prendre en compte certains détails de son fonctionnement et suivre certaines bonnes pratiques.
seo-description: Pour utiliser TVSDK de manière efficace, vous devez prendre en compte certains détails de son fonctionnement et suivre certaines bonnes pratiques.
seo-title: Considérations et bonnes pratiques
title: Considérations et bonnes pratiques
uuid: a65c9739-ed83-4519-8ae5-7ba4c8f1ca49
translation-type: tm+mt
source-git-commit: 23a48208ac1d3625ae7d925ab6bfba8f2a980766
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---


# Considérations et bonnes pratiques {#considerations-and-best-practices}

Pour utiliser TVSDK de manière efficace, vous devez prendre en compte certains détails de son fonctionnement et suivre certaines bonnes pratiques.

## Considérations {#section_tvsdk_considerations}

Rappelez-vous des informations suivantes lorsque vous utilisez TVSDK :

* Adobe Primetime ne fonctionne pas sur les simulateurs iOS.

   Vous devez utiliser des périphériques réels pour les tests.

* La lecture n’est prise en charge que pour le contenu HLS (HTTP Live Streaming).

* Le contenu vidéo principal peut être multiplexé, où les flux vidéo et audio se trouvent dans le même rendu, ou non multiplexé, où les flux vidéo et audio se trouvent dans des rendus distincts.

* L’API TVSDK est implémentée dans Objective-C.

* La lecture vidéo nécessite la structure native d’Apple AV Foundation. Cela a une incidence sur la manière et le moment où les ressources multimédia, y compris les sous-titres et les calendriers fermés, peuvent être consultées :

   * Les réglages de la chronologie ne peuvent pas être modifiés après la configuration initiale.

      Par exemple, une publicité ne peut pas être supprimée du plan de montage chronologique après sa lecture. Si l’utilisateur effectue de nouveau une recherche dans la présentation, la même publicité est lue à nouveau, même si la stratégie consistait à la supprimer.

   * Selon la précision de l’encodeur, la durée réelle du support codé peut différer des durées enregistrées dans le manifeste de ressources de diffusion en continu.

      Il n&#39;existe aucun moyen fiable de resynchroniser entre la chronologie virtuelle idéale et la chronologie de la lecture réelle. Le suivi de la progression de la lecture du flux pour la gestion des publicités et les analyses vidéo doit utiliser le temps de lecture réel. Par conséquent, le comportement des rapports et de l’interface utilisateur peut ne pas suivre précisément le contenu multimédia et publicitaire.

   * L’agent utilisateur entrant pour toutes les requêtes HTTP de TVSDK sur cette plate-forme est déterminé par le périphérique et la version iOS qui s’exécute sur le périphérique.

      La valeur de la chaîne de l’agent utilisateur correspond par défaut à ce que le système d’exploitation attribue.

## Meilleures pratiques {#section_tvsdk_best_practices}

Voici les pratiques recommandées pour TVSDK :

* Utilisez HLS version 3.0 ou ultérieure pour le contenu du programme.

* Utilisez l’outil mediastreamvalidator d’Apple pour valider les flux VOD.

* La classe PTSDKConfig fournit des méthodes pour appliquer SSL sur les requêtes effectuées sur les serveurs Primetime de prise de décision et de gestion des droits numériques et d’analyses vidéo.

Pour plus d&#39;informations, voir les méthodes forceHTTPS et isForcingHTTPS dans cette classe.

>[!IMPORTANT]
>
>Les requêtes envoyées à des domaines tiers tels que les pixels de suivi des publicités, les URL de contenu et de publicité et les requêtes similaires ne sont pas modifiées. Il incombe aux fournisseurs de contenu et aux serveurs d’annonces de fournir des URL prises en charge par HTTPS.
