---
description: Vous pouvez choisir d’utiliser les comportements publicitaires par défaut.
seo-description: Vous pouvez choisir d’utiliser les comportements publicitaires par défaut.
seo-title: Utiliser le comportement de lecture par défaut
title: Utiliser le comportement de lecture par défaut
uuid: 7139384c-167a-4cab-816a-c02fb723a5cb
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Utiliser le comportement de lecture par défaut{#use-the-default-playback-behavior}

Vous pouvez choisir d’utiliser les comportements publicitaires par défaut.

Pour utiliser des comportements par défaut :

    * Si vous implémentez votre propre classe &quot;ContentFactory&quot;, renvoyez une nouvelle instance de &quot;DefaultAdPolicySelector&quot; dans votre implémentation de &quot;doRetrieveAdPolicySelector&quot;.
    
    &quot;
    public class CustomContentFactory étend ContentFactory {
    
    //...
    // votre code personnalisé pour les classes
    de publicité//...
    
    /**
    * @inheritDoc
    */
    override protected
    function doRetrieveAdPolicySelector(item:MediaPlayerItem):AdPolicySelector {
    renvoie un nouveau DefaultAdPolicySelector(item);
    
    }&quot;* Si vous n&#39;avez pas d&#39;implémentation personnalisée pour la classe &quot;ContentFactory&quot;, utilise &quot;DefaultAdPolicySelector&quot;.
    
    
    