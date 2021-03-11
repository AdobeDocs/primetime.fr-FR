---
description: Les fonctionnalités TVSDK sont pilotées par la configuration et implémentées via MediaPlayer.
title: Création de gestionnaires de fonctionnalités en transmettant les informations de configuration au lecteur Media
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---


# Création de gestionnaires de fonctionnalités en transmettant les informations de configuration au MediaPlayer {#creating-feature-managers-by-passing-configuration-information-to-the-mediaplayer}

Les fonctionnalités TVSDK sont pilotées par la configuration et implémentées via MediaPlayer.

* La configuration est la liste de paramètres spécifiques pour la fonction, tels que le débit binaire initial du contrôle ABR et la visibilité par défaut du sous-titrage.

   Les gestionnaires de fonctionnalités doivent obtenir les configurations afin de déterminer le comportement des fonctionnalités.

   Dans l’implémentation de la référence Primetime, la configuration est stockée dans des préférences partagées, mais vous pouvez stocker la configuration de n’importe quelle façon qui convient à votre environnement.

* `MediaPlayer` est l’objet du lecteur multimédia TVSDK qui contient la ressource vidéo.

   Les gestionnaires de fonctionnalités enregistrent les écouteurs de événement TVSDK sur cet objet lecteur, récupèrent les données de la session de lecture et déclenchent les fonctionnalités TVSDK à la session de lecture.

Chaque fonction possède une interface de configuration correspondante. Par exemple, `CCManager` utilise `ICCConfig` pour récupérer la configuration. `ICCConfig` contient les méthodes permettant d’obtenir les informations de configuration relatives au sous-titrage uniquement.

L’exemple suivant montre le fichier [!DNL ICCConfig.java], configuré pour recevoir des informations sur la visibilité de la légende fermée, le style et le bord de la police à partir de `MediaPlayer` :

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

Une application qui utilise une fonction TVSDK peut créer son gestionnaire de fonctionnalités avec un fournisseur de configuration et un objet `MediaPlayer`. Par exemple :

```java
// This application needs to use the advertising workflow feature 
AdsManager adsManager = new AdsManagerOn();
```

Documentation de l’API de configuration de Feature Manager : [Javadoc](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/package-summary.html)