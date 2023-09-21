---
description: TVSDK peut lire des vidéos qui comportent plusieurs profils avec des débits différents, en passant d’un à l’autre pour fournir plusieurs niveaux de qualité en fonction de la bande passante disponible.
title: Débit binaire multiple
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '767'
ht-degree: 0%

---

# Débit binaire multiple {#multiple-bit-rates}

TVSDK peut lire des vidéos qui comportent plusieurs profils avec des débits différents, en passant d’un à l’autre pour fournir plusieurs niveaux de qualité en fonction de la bande passante disponible.

Vous pouvez définir des débits initiaux, minimaux et maximales, ainsi que la stratégie de commutation de débit adaptatif (ABR) pour un flux de débit multiple (MBR). TVSDK bascule automatiquement vers le débit qui offre la meilleure expérience de lecture dans la configuration spécifiée.

L’implémentation de référence configure les paramètres ABR suivants dans [IPlaybackConfig](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html).

| Paramètre | Description |
|--- |--- |
| Taux de bit initial : getABRInitialBitRate | Débit de lecture souhaité (en bits par seconde) pour le premier segment. Au démarrage de la lecture, le profil le plus proche (égal ou supérieur au débit initial) est utilisé pour le premier segment.  Si un débit minimal est défini et que le débit initial est inférieur au débit minimal, TVSDK sélectionne le profil dont le débit minimal est supérieur au débit minimal. De même, si le taux initial est supérieur au taux maximum, TVSDK sélectionne le taux le plus élevé en dessous du taux maximum. Si le débit initial est nul ou non défini, le débit initial est déterminé par la stratégie ABR.  Renvoie une valeur entière qui représente le profil byte par seconde. |
| Débit minimal : getABRMinBitRate | Le débit binaire le plus faible auquel l’ABR peut basculer. Le changement ABR ignore les profils dont le débit est inférieur à celui-ci. Renvoie une valeur entière qui représente le profil bits par seconde. |
| Taux de bit maximal : getABRMaxBitRate | Débit binaire autorisé le plus élevé auquel l’ABR peut basculer. Le changement d’ABR ignore les profils dont le débit est supérieur à celui-ci. Renvoie une valeur entière qui représente le profil bits par seconde. |
| Stratégie de changement ABR : getABRPolicy | Lorsque cela est possible, la lecture passe progressivement au profil de débit le plus élevé. Vous pouvez définir la stratégie de changement d’ABR, qui détermine la vitesse à laquelle TVSDK bascule entre les profils. La valeur par défaut est Modéré. <ul><li>*Conservatrice*: passe au profil avec le débit supérieur suivant lorsque la bande passante est 50 % supérieure au débit actuel. </li><li>*Modérer*: passe au profil de débit supérieur suivant lorsque la bande passante est de 20 % supérieure au débit actuel.</li><li>*Agressive*: bascule immédiatement vers le profil de débit le plus élevé lorsque la bande passante est supérieure à la vitesse actuelle</li></ul><br/>Si le débit initial est nul ou non spécifié et qu’une stratégie est spécifiée, la lecture commence par le profil de débit le plus faible pour Conservateur, le profil le plus proche du débit médian des profils disponibles pour Modéré et le profil de débit le plus élevé pour Agressif.<br/><br/>La stratégie fonctionne dans les limites des débits minimal et maximal, si ceux-ci sont spécifiés.  Renvoie le paramètre actuel de l’énumération ABRControlParameters : <ul><li>ABR_CONSERVATIVE</li><li>ABR_MODERATE </li><li>ABR_AGGRESSIVE</li></ul><br>Voir aussi [ABRPolicy](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/ABRControlParameters.ABRPolicy.html). |

>[!NOTE]
>
>* Le mécanisme de basculement TVSDK peut remplacer ces paramètres, car TVSDK favorise une expérience de lecture continue au lieu de respecter strictement les paramètres de contrôle.
>* Lorsque le débit binaire change, TVSDK distribue `onProfileChanged` événements dans `PlaybackEventListener`.

## Activation du contrôle ABR personnalisé dans l’implémentation de référence {#section_72A6E7263E1441DD8D7E0690285515E6}

Le débit adaptatif (ABR) est activé par défaut dans le TVSDK. Vous pouvez utiliser l’interface utilisateur Paramètres Primetime pour remplacer le comportement par défaut du TVSDK dans l’implémentation de référence en configurant un contrôle ABR personnalisé.

Pour activer la fonction ABR personnalisée via l’interface utilisateur de paramètres :

* Ouvrez la boîte de dialogue Paramètres Primetime .
* Sélectionner **[!UICONTROL ABR controls]**.

  ![](assets/abr-configuration.jpg)

* Appuyez sur le bouton [!UICONTROL Enable ON] contrôle afin qu’il s’affiche `OFF`.

La variable `PlaybackManager` définit uniquement les paramètres ABR si [isABRControlEnabled](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html) renvoie true (ON). S’il renvoie false (OFF), la variable `PlaybackManager` utilise la commande ABR par défaut, de sorte que les débits initial, minimum et maximum seront tous de 0 et que la stratégie ABR sera `ABR_MODERATE`.

## Configuration pour les faibles débits {#section_5451691CBBD24542AD54A474D222CD39}

Pour certains taux de lecture à faible débit, le TVSDK, par défaut, bascule vers la diffusion audio uniquement et la lecture apparaît figée. Vous pouvez configurer le lecteur de sorte qu’il ne rencontre jamais de situation où il passe au format audio uniquement.

* Mettez en oeuvre le [IPlaybackConfig](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html) interface :

* Assurez-vous que [getABRMinBitRate](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html#getABRMinBitRate()) est plus élevé que le débit audio uniquement (supérieur à 64 000).
* Assurez-vous que [isABRControlEnabled](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html#isABRControlEnabled()) est activé.
