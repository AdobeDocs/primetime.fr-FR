---
description: Lorsque la prise de décision publicitaire Primetime rencontre une publicité VAST (créative) vide ou ayant un type de média non valide pour HLS, elle évalue les publicités de secours pour déterminer ce qui doit être renvoyé.
title: Comportement de secours des publicités pour VAST et VMAP
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Comportement de secours des publicités pour VAST et VMAP {#ad-fallback-behavior-for-vast-and-vmap}

Lorsque la prise de décision publicitaire Primetime rencontre une publicité VAST (créative) vide ou ayant un type de média non valide pour HLS, elle évalue les publicités de secours pour déterminer ce qui doit être renvoyé.

<!--<a id="section_9F60AF00CE9645848EAAF8C06A9E426B"></a>-->

Dans TVSDK, le seul type de média valide est `application/x-mpegURL` (M3U8).

Lorsqu’il existe des publicités de secours autonomes, le plug-in de prise de décision publicitaire Primetime examine ces publicités dans l’ordre suivant et renvoie la première publicité avec un type de média valide :

1. Si le reconditionnement est activé, la première occurrence d’une publicité avec un type de média non valide est traitée comme d’autres types de média non valides.

   Si le reconditionnement échoue, ce processus s’applique aux occurrences supplémentaires de la publicité.
1. Si TVSDK ne trouve aucune publicité de secours valide, il renvoie la publicité d’origine avec le type de média non valide.
1. Si une publicité de secours avec un type MIME valide est renvoyée au lieu de la publicité d’origine, la prise de décision de publicité Primetime envoie le code d’erreur 403 à l’URL d’erreur VAST, le cas échéant.
1. Si une publicité de secours est un wrapper qui renvoie plusieurs publicités, seules les publicités avec le type de média approprié sont renvoyées.

>[!IMPORTANT]
>
>Ce comportement est toujours activé pour les publicités dans les wrappers VAST. Pour les publicités VAST intégrées dans un VMAP, le comportement est désactivé par défaut, mais votre application peut l’activer.
