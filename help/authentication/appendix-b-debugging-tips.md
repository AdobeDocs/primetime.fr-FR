---
title: Annexe B "Conseils de débogage"
description: Annexe B "Conseils de débogage"
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
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
- [Effacement du cache des LSOs](#clearing-lsos-cache)


## Effacement du cache du navigateur et des cookies {#clearing-the-browser-cache-and-cookies}

Il est fiable pour le navigateur, mais dans Firefox : &quot;Outils&quot; -\> &quot;Effacer l’historique récent...&quot; -\> Dans &quot;Période à effacer&quot; : sélectionnez &quot;Tout&quot; ; et dans &quot;Détails&quot; : cochez les &quot;Cookies&quot; et &quot;Cache&quot; -\> Cliquez sur &quot;Effacer maintenant&quot;.


## Effacement du cache des LSOs {#clearing-lsos-cache}

Accédez au [Aide de Flash Player](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html).

Sélectionnez la variable ```entitlement.\*``` (en fonction des tests) et cliquez sur &quot;Supprimer le site web&quot;.


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
