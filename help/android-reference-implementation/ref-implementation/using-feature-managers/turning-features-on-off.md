---
description: Vous pouvez activer ou désactiver les fonctionnalités sans passer par le code à l’aide de la fabrique de gestionnaires.
seo-description: Vous pouvez activer ou désactiver les fonctionnalités sans passer par le code à l’aide de la fabrique de gestionnaires.
seo-title: Activation ou désactivation des fonctionnalités à l’aide de ManagerFactory
title: Activation ou désactivation des fonctionnalités à l’aide de ManagerFactory
uuid: 385c2707-95f7-4628-8d25-67731151cb6a
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Activation ou désactivation des fonctionnalités à l’aide de ManagerFactory{#turning-features-on-or-off-using-managerfactory}

Vous pouvez activer ou désactiver les fonctionnalités sans passer par le code à l’aide de la fabrique de gestionnaires.

L’argument d’activation de l’exemple ci-dessous détermine si la fonction est utilisée ou non. S’il est défini sur false, le gestionnaire de fonctionnalités est créé mais fournit uniquement la fonctionnalité par défaut au lecteur, comme si le gestionnaire de fonctionnalités n’avait pas été créé. S’il est vrai, le gestionnaire de fonctionnalités est créé, la fonction est activée et le lecteur de médias accepte les entrées du fichier de configuration.

Par exemple, dans le `com.adobe.primetime.reference.ui.player.PlayerFragment.java` fichier :

```java
adsManager = ManagerFactory.getAdsManager( 
<b>true</b>, config, mediaPlayer);
```

**Documentation** API : [ManagerFactory](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/ManagerFactory.html)