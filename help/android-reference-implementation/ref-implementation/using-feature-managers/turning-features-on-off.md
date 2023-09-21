---
description: Vous pouvez activer ou désactiver des fonctionnalités sans passer par le code en utilisant la fabrique de gestion.
title: Activation ou désactivation des fonctionnalités à l’aide de ManagerFactory
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%

---

# Activation ou désactivation des fonctionnalités à l’aide de ManagerFactory{#turning-features-on-or-off-using-managerfactory}

Vous pouvez activer ou désactiver des fonctionnalités sans passer par le code en utilisant la fabrique de gestion.

L’argument d’activation de l’exemple ci-dessous détermine si la fonction est utilisée ou non. S’il est défini sur false, le gestionnaire de fonctionnalités est créé, mais il fournit uniquement la fonctionnalité par défaut au lecteur, comme si le gestionnaire de fonctionnalités n’avait pas été créé. Si la valeur est true, le gestionnaire de fonctionnalités est créé, la fonction est activée et le lecteur multimédia accepte les entrées du fichier de configuration.

Par exemple, dans la variable `com.adobe.primetime.reference.ui.player.PlayerFragment.java` fichier :

```java
adsManager = ManagerFactory.getAdsManager( 
<b>true</b>, config, mediaPlayer);
```

**Documentation de l’API**: [ManagerFactory](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/ManagerFactory.html)
