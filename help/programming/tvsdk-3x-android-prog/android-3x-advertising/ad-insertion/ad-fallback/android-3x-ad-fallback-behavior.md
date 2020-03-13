---
description: Lorsque la décision publicitaire Primetime rencontre une publicité VAST (créative) vide ou dont le type de média n’est pas valide pour HLS, elle évalue les publicités de secours afin de déterminer le contenu à renvoyer.
seo-description: Lorsque la décision publicitaire Primetime rencontre une publicité VAST (créative) vide ou dont le type de média n’est pas valide pour HLS, elle évalue les publicités de secours afin de déterminer le contenu à renvoyer.
seo-title: Comportement de secours de publicité pour VAST et VMAP
title: Comportement de secours de publicité pour VAST et VMAP
uuid: 612416b9-d070-42e2-b68b-74ba52023345
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Comportement de secours de publicité pour VAST et VMAP {#ad-fallback-behavior-for-vast-and-vmap}

Lorsque la décision publicitaire Primetime rencontre une publicité VAST (créative) vide ou dont le type de média n’est pas valide pour HLS, elle évalue les publicités de secours afin de déterminer le contenu à renvoyer.

<!--<a id="section_9F60AF00CE9645848EAAF8C06A9E426B"></a>-->

Dans TVSDK, le seul type de support valide est `application/x-mpegURL` (M3U8).

Lorsqu’il existe des publicités de secours autonomes, le module de prise de décision publicitaire Primetime examine ces publicités dans l’ordre suivant et renvoie la première publicité avec un type de média valide :

1. Si le reconditionnement est activé, la première occurrence d’une publicité avec un type de média non valide est traitée comme d’autres types de média non valides.

   Si le reconditionnement échoue, ce processus s’applique aux occurrences supplémentaires de la publicité.
1. Si TVSDK ne trouve aucune publicité de secours valide, il renvoie la publicité d’origine avec le type de média non valide.
1. Si une publicité de secours avec un type MIME valide est renvoyée au lieu de la publicité d’origine, Primetime et la décision d’une publicité envoie le code d’erreur 403 à l’URL d’erreur VAST, le cas échéant.
1. Si une publicité de secours est un wrapper et renvoie plusieurs publicités, seules les publicités avec le type de média approprié sont renvoyées.

>[!IMPORTANT]
>
>Ce comportement est toujours activé pour les annonces dans les wrappers VAST. Pour les publicités VAST intégrées dans un VMAP, le comportement est désactivé par défaut, mais votre application peut l’activer.