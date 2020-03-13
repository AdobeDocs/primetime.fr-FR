---
description: Les fonctionnalités TVSDK sont pilotées par la configuration et implémentées via MediaPlayer.
seo-description: Les fonctionnalités TVSDK sont pilotées par la configuration et implémentées via MediaPlayer.
seo-title: Création de gestionnaires de fonctionnalités en transmettant les informations de configuration au lecteur multimédia
title: Création de gestionnaires de fonctionnalités en transmettant les informations de configuration au lecteur multimédia
uuid: 106ececd-a670-4360-b000-a31fec65233c
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Création de gestionnaires de fonctionnalités en transmettant les informations de configuration au lecteur multimédia {#creating-feature-managers-by-passing-configuration-information-to-the-mediaplayer}

Les fonctionnalités TVSDK sont pilotées par la configuration et implémentées via MediaPlayer.

* La configuration est le  de paramètres spécifiques pour la fonctionnalité, tels que le débit binaire initial du contrôle ABR et la visibilité par défaut du sous-titrage.

   Les gestionnaires de fonctionnalités doivent obtenir les configurations afin de déterminer le comportement des fonctionnalités.

   Dans l’implémentation de référence Primetime, la configuration est stockée dans les préférences partagées, mais vous pouvez stocker la configuration de toute manière qui convient à votre  .

* `MediaPlayer` est l’objet du lecteur multimédia TVSDK qui contient la ressource vidéo.

   Les gestionnaires de fonctionnalités enregistrent les auditeurs  TVSDK sur cet objet lecteur, récupèrent les données de la session de lecture et déclenchent les fonctionnalités TVSDK dans la session de lecture.

Chaque fonctionnalité possède une interface de configuration correspondante. Par exemple, `CCManager` utilise `ICCConfig` pour récupérer la configuration. `ICCConfig` contient les méthodes permettant d’obtenir les informations de configuration relatives au sous-titrage uniquement.

L’exemple suivant montre le [!DNL ICCConfig.java] fichier, configuré pour recevoir des informations sur la visibilité des sous-titres, le style et le bord de la police à partir du `MediaPlayer`:

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

Une application qui utilise une fonction TVSDK peut créer son gestionnaire de fonctionnalités avec un fournisseur de configuration et un `MediaPlayer` objet. Par exemple :

```java
// This application needs to use the advertising workflow feature 
AdsManager adsManager = new AdsManagerOn();
```

Documentation de l’API de configuration du gestionnaire de fonctionnalités : [Javadoc](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/package-summary.html)