---
title: Annexe B "Conseils de débogage"
description: Annexe B "Conseils de débogage"
exl-id: ea024797-315e-47c0-99ea-1ac49c8c9697
source-git-commit: 1bc2f6c230c262babf2958c32fee31afcad04c2f
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

---

# Annexe B : Conseils de débogage {#appendix-b-debugging-tips}

>[!NOTE]
>
>Le contenu de cette page est fourni à titre d’information uniquement. L’utilisation de cette API nécessite une licence actuelle de Adobe. Aucune utilisation non autorisée n’est autorisée.


## Effacement des données temporaires {#clearing-temporary-data}

L’authentification Adobe Primetime stocke des données temporaires telles que le cache du navigateur, le cache des LSO et les cookies. L’effacement des données temporaires est important, afin de vous assurer que vous obtenez une page nette lors du test.

- [Effacement du cache du navigateur et des cookies](#clearing-the-browser-cache-and-cookies)
- [Effacement du cache des LSOs](#clearing-lsos-cache)\
   

## Effacement du cache du navigateur et des cookies {#clearing-the-browser-cache-and-cookies}

Il est fiable pour le navigateur, mais dans Firefox : &quot;Outils&quot; -\> &quot;Effacer l’historique récent...&quot; -\> Sur &quot;Période à effacer&quot; : sélectionnez &quot;Tout&quot; ; et sur &quot;Détails&quot; : cochez les cases &quot;Cookies&quot; et &quot;Cache&quot; -\> cliquez sur &quot;Effacer maintenant&quot;.\
 

## Effacement du cache des LSOs {#clearing-lsos-cache}

Accédez au [Aide sur les Flashs Player](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html).

Sélectionnez la ```entitlement.\*``` (en fonction des tests) et cliquez sur &quot;Supprimer le site web&quot;.\
 

## Outils de débogage {#tools}

Les ingénieurs d’authentification Adobe Primetime utilisent les outils de débogage suivants :

- Firebug - <http://www.getfirebug.com/>
- Flashbug (fonctionne avec la version de débogage du lecteur Flash)
- Fiddler - <http://www.fiddler2.com/fiddler2/>
- Charles - <http://www.charlesproxy.com/>
- Wireshark - <http://www.wireshark.org/>


<!--
## Related Information

- [Programmer Integration Guide](/help/authentication/programmer-integration-guide-overview.md)

- [Using Charles Proxy (Tech Note)](https://tve.zendesk.com/hc/en-us/articles/204962849-Using-Charles-Proxy)
-->
