---
description: Les fonctionnalités TVSDK sont pilotées par la configuration et mises en oeuvre via MediaPlayer.
title: Création de gestionnaires de fonctionnalités en transmettant des informations de configuration au lecteur multimédia
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---

# Création de gestionnaires de fonctionnalités en transmettant des informations de configuration au lecteur multimédia {#creating-feature-managers-by-passing-configuration-information-to-the-mediaplayer}

Les fonctionnalités TVSDK sont pilotées par la configuration et mises en oeuvre via MediaPlayer.

* La configuration est la liste des paramètres spécifiques de la fonctionnalité, tels que le débit initial du contrôle ABR et la visibilité par défaut du sous-titrage.

  Les gestionnaires de fonctionnalités doivent obtenir les configurations afin de déterminer le comportement de la fonctionnalité.

  Dans l’implémentation de référence Primetime, la configuration est stockée dans les préférences partagées, mais vous pouvez stocker la configuration de la manière qui convient le mieux à votre environnement.

* `MediaPlayer` est l’objet du lecteur multimédia TVSDK qui contient la ressource vidéo.

  Les gestionnaires de fonctionnalités enregistrent les écouteurs d’événement TVSDK sur cet objet de lecteur, récupèrent les données de la session de lecture et déclenchent les fonctionnalités TVSDK dans la session de lecture.

Chaque fonction possède une interface de configuration correspondante. Par exemple : `CCManager` uses `ICCConfig` pour récupérer la configuration. `ICCConfig` contient des méthodes pour obtenir les informations de configuration relatives au sous-titrage codé uniquement.

L’exemple suivant illustre la variable [!DNL ICCConfig.java] fichier, configuré pour recevoir des informations sur la visibilité de la légende fermée, le style et le bord de la police à partir de `MediaPlayer`:

```java
// Constructor of CCManager 
 
<b>public CCManager(ICCConfig ccConfig, MediaPlayer mediaPlayer) {...}</b> 
  
// ICCConfig methods 
 
<b>public interface ICCConfig {</b> 
  
    /** 
     * Get the closed captioning visibility config 
     * 
     * @return true if visibility is set to true, false otherwise 
     */ 
    
<b> public boolean getCCVisibility();</b> 
  
    /** 
     * Get the closed captioning font style 
     * 
     * @return TextFormat.Font object represents font style 
     */ 
     
<b>public TextFormat.Font getCCFont();</b>

    /** 
     * Get the closed captioning font edge 
     * 
     * @return TextFormat.FontEdge represents of font edge 
     */ 
     
<b>public TextFormat.FontEdge getCCFontEdge();</b> 
... 
}
```

Une application qui utilise une fonctionnalité TVSDK peut créer son gestionnaire de fonctionnalités avec un fournisseur de configuration et un `MediaPlayer` . Par exemple :

```java
// This application needs to use the advertising workflow feature 
AdsManager adsManager = new AdsManagerOn();
```

Documentation de l’API de configuration du gestionnaire de fonctionnalités : [Javadoc](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/package-summary.html)
