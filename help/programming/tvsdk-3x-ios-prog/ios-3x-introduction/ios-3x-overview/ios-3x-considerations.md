---
description: Pour utiliser TVSDK de manière efficace, vous devez prendre en compte certains détails de son fonctionnement et suivre certaines bonnes pratiques.
title: Considérations et bonnes pratiques
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Considérations et bonnes pratiques {#considerations-and-best-practices}

Pour utiliser TVSDK de manière efficace, vous devez prendre en compte certains détails de son fonctionnement et suivre certaines bonnes pratiques.

## Considérations {#section_tvsdk_considerations}

Gardez à l’esprit les informations suivantes lorsque vous utilisez TVSDK :

* Adobe Primetime ne fonctionne pas sur les simulateurs iOS.

  Vous devez utiliser des appareils réels pour les tests.

* La lecture est prise en charge uniquement pour le contenu HTTP Live Streaming (HLS).

* Le contenu vidéo principal peut être multiplexé, où les flux vidéo et audio se trouvent dans le même rendu, ou non multiplexé, où les flux vidéo et audio se trouvent dans des rendus distincts.

* L’API TVSDK est mise en oeuvre dans Objective-C.

* La lecture vidéo nécessite la structure native d’Apple AV Foundation. Cela a une incidence sur la manière et le moment où les ressources multimédia, y compris les sous-titres et les chronologies fermés, sont accessibles :

   * Les réglages de la chronologie ne peuvent pas être modifiés après la configuration initiale.

     Par exemple, une publicité ne peut pas être supprimée de la chronologie après sa lecture. Si l’utilisateur effectue une recherche de retour dans la présentation, la même publicité est relue même si la stratégie aurait été de supprimer la publicité.

   * Selon la précision de l’encodeur, la durée réelle du média codé peut différer des durées enregistrées dans le manifeste de ressource de flux.

     Il n’existe aucun moyen fiable de resynchroniser entre la chronologie virtuelle idéale et la chronologie réelle de lecture. Le suivi de la progression de la lecture de la diffusion pour la gestion des publicités et les analyses vidéo doit utiliser le temps de lecture réel. Par conséquent, le comportement de la création de rapports et de l’interface utilisateur peut ne pas suivre précisément le contenu multimédia et publicitaire.

   * L’agent utilisateur entrant pour toutes les requêtes HTTP issues de TVSDK sur cette plate-forme est déterminé par l’appareil et la version iOS qui s’exécute sur l’appareil.

     La valeur de la chaîne de l’agent utilisateur correspond par défaut à ce que le système d’exploitation attribue.

## Bonnes pratiques {#section_tvsdk_best_practices}

Voici les pratiques recommandées pour TVSDK :

* Utilisez HLS version 3.0 ou ultérieure pour le contenu du programme.

* Utilisez l’outil Apple mediastreamvalidator pour valider les flux VOD.

* La classe PTSDKConfig fournit des méthodes pour appliquer SSL sur les demandes effectuées aux serveurs Primetime ad Decisioning, DRM et Video Analytics.

Pour plus d’informations, voir les méthodes forceHTTPS et isForcingHTTPS de cette classe.

>[!IMPORTANT]
>
>Les requêtes envoyées à des domaines tiers tels que les pixels de suivi des publicités, les URL de contenu et de publicité, ainsi que les requêtes similaires ne sont pas modifiées. Il est de la responsabilité des fournisseurs de contenu et des serveurs de publicités de fournir les URL prises en charge par HTTPS.
