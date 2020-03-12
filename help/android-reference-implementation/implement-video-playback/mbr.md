---
description: Le SDK TVSDK peut lire des vidéos qui ont plusieurs  avec des débits de bits différents, passant d’un mode à l’autre pour fournir plus d’un niveau de qualité en fonction de la bande passante disponible.
seo-description: Le SDK TVSDK peut lire des vidéos qui ont plusieurs  avec des débits de bits différents, passant d’un mode à l’autre pour fournir plus d’un niveau de qualité en fonction de la bande passante disponible.
seo-title: Débit multiple
title: Débit multiple
uuid: 46eac41e-0b2a-42e3-8a88-54ad9fe34212
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Débit multiple {#multiple-bit-rates}

Le SDK TVSDK peut lire des vidéos qui ont plusieurs  avec des débits de bits différents, passant d’un mode à l’autre pour fournir plus d’un niveau de qualité en fonction de la bande passante disponible.

Vous pouvez définir des débits initiaux, minimaux et maximaux, ainsi que la stratégie de commutation de débit binaire adaptatif (ABR) pour un flux à débit binaire multiple (MBR). Le SDK TVSDK bascule automatiquement sur le débit binaire qui offre la meilleure expérience de lecture dans la configuration spécifiée.

L’implémentation de référence configure les paramètres ABR suivants dans [IPlaybackConfig](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html).

| Paramètre | Description |
|--- |--- |
| Débit initial :  getABRInitialBitRate | Débit de lecture souhaité (en bits par seconde) pour le premier segment. Lorsque le de lecture est , le  le plus proche (égal ou supérieur au débit initial) est utilisé pour le premier segment.  Si un débit minimal est défini et que le débit initial est inférieur au débit minimal, le SDK TVSDK sélectionne le dont le débit minimal est supérieur au débit minimal. De même, si le taux initial est supérieur au taux maximum, le SDK TVSDK sélectionne le taux le plus élevé inférieur au taux maximum. Si le débit initial est nul ou non défini, le débit initial est déterminé par la stratégie ABR.  Renvoie une valeur entière qui représente le  d’octet par seconde. |
| Débit minimum :  getABRMinBitRate | Le débit binaire le plus faible auquel l’ABR peut basculer. Le basculement ABR ignore les  dont le débit est inférieur à celui-ci. Renvoie une valeur entière qui représente le  de bits par seconde. |
| Débit maximal :  getABRMaxBitRate | débit maximal autorisé auquel l’ABR peut basculer. Le basculement ABR ignore les  avec un débit binaire supérieur à celui-ci. Renvoie une valeur entière qui représente le  de bits par seconde. |
| Stratégie de commutation ABR :  getABRPolicy | Lorsque cela est possible, la lecture passe progressivement au  de débit le plus élevé. Vous pouvez définir la stratégie de commutation ABR, qui détermine la vitesse à laquelle TVSDK bascule entre les  du. La valeur par défaut est Modéré. <ul><li>*Conservateur*: Passe au  avec le débit supérieur suivant lorsque la bande passante est supérieure de 50 % à celle du débit actuel. </li><li>*Modéré*: Passe au prochain de débit supérieur lorsque la bande passante est supérieure de 20 % à la vitesse de transmission actuelle.</li><li>*Agressive*: Bascule immédiatement vers le à débit binaire le plus élevé  lorsque la bande passante est supérieure au débit binaire actuel</li></ul><br/>Si le débit initial est nul ou non spécifié et qu’une stratégie est spécifiée, le de lecture  avec le de débit le plus faible pour Conservateur, le plus proche du débit médian du disponible pour Modéré et le plus élevé pour Agressive.<br/><br/>La stratégie fonctionne dans les limites des débits minimum et maximum, si elles sont spécifiées.  Renvoie le paramètre actuel de l’énumération ABRControlParameters : <ul><li>ABR_CONSERVATIVE</li><li>ABR_MODERATE </li><li>ABR_AGGRESSIVE</li></ul><br>Voir aussi [ABRPolicy](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/ABRControlParameters.ABRPolicy.html). |

>[!NOTE]
>
>* Le mécanisme de basculement TVSDK peut remplacer ces paramètres, car TVSDK favorise une lecture continue plutôt que le strict respect des paramètres de contrôle.
>* Lorsque le débit change, le kit TVSDK envoie `onProfileChanged` des  dans `PlaybackEventListener`.


## Activation du contrôle ABR personnalisé dans l’implémentation de référence {#section_72A6E7263E1441DD8D7E0690285515E6}

Le débit binaire adaptatif (ABR) est activé par défaut dans le SDK TVSDK. Vous pouvez utiliser l’interface utilisateur des paramètres Primetime pour remplacer le comportement par défaut de TVSDK dans l’implémentation de référence en configurant le contrôle ABR personnalisé.

Pour activer l’ABR personnalisé via l’interface utilisateur des paramètres :

* Ouvrez la boîte de dialogue Paramètres Primetime.
* Sélectionnez **[!UICONTROL ABR controls]**.

   ![](assets/abr-configuration.jpg)

* Appuyez sur le [!UICONTROL Enable ON] contrôle pour qu’il s’affiche `OFF`.

Le `PlaybackManager` paramètre ABR est défini uniquement si [isABRControlEnabled](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html) renvoie true (ON). S’il renvoie false (OFF), le `PlaybackManager` contrôle ABR par défaut est utilisé de sorte que les débits initial, minimal et maximal soient tous de 0 et que la stratégie ABR soit `ABR_MODERATE`définie.

## Configuration pour les faibles débits {#section_5451691CBBD24542AD54A474D222CD39}

Pour certains taux de lecture faibles, le TVSDK bascule par défaut vers le flux audio uniquement et la lecture semble figée. Vous pouvez configurer le lecteur de sorte qu’il ne rencontre jamais de situation où il bascule sur le paramètre audio uniquement.

* Implémentez l’interface [IPlaybackConfig](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html) :

* Assurez-vous que [getABRMinBitRate](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html#getABRMinBitRate()) est supérieur au débit audio uniquement (supérieur à 64 000).
* Vérifiez que [isABRControlEnabled](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html#isABRControlEnabled()) est activé.