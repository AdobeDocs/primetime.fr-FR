---
description: Le SDK TVSDK peut lire des vidéos qui comportent plusieurs profils avec des débits différents, en basculant entre eux pour fournir plusieurs niveaux de qualité en fonction de la bande passante disponible.
seo-description: Le SDK TVSDK peut lire des vidéos qui comportent plusieurs profils avec des débits différents, en basculant entre eux pour fournir plusieurs niveaux de qualité en fonction de la bande passante disponible.
seo-title: Débit multiple
title: Débit multiple
uuid: 46eac41e-0b2a-42e3-8a88-54ad9fe34212
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 0%

---


# Débit multiple {#multiple-bit-rates}

Le SDK TVSDK peut lire des vidéos qui comportent plusieurs profils avec des débits différents, en basculant entre eux pour fournir plusieurs niveaux de qualité en fonction de la bande passante disponible.

Vous pouvez définir des débits initiaux, minimaux et maximaux, ainsi que la stratégie de commutation de débit binaire adaptatif (ABR) pour un flux de débit binaire multiple (MBR). Le SDK TVSDK bascule automatiquement sur le débit binaire qui offre la meilleure expérience de lecture dans la configuration spécifiée.

L’implémentation de référence configure les paramètres ABR suivants dans [IPlaybackConfig](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html).

| Paramètre | Description |
|--- |--- |
| Débit initial :  getABRInitialBitRate | Débit de lecture souhaité (en bits par seconde) pour le premier segment. Lors des débuts de lecture, le profil le plus proche (égal ou supérieur au débit initial) est utilisé pour le premier segment.  Si un débit minimal est défini et que le débit initial est inférieur au débit minimal, TVSDK sélectionne le profil dont le débit minimal est supérieur au débit minimal. De même, si le taux initial est supérieur au taux maximum, TVSDK sélectionne le taux le plus élevé inférieur au taux maximum. Si le débit initial est nul ou non défini, le débit initial est déterminé par la stratégie ABR.  Renvoie une valeur entière qui représente l’octet par seconde. |
| Débit minimum :  getABRMinBitRate | Le débit binaire le plus bas autorisé auquel l&#39;ABR peut basculer. Le changement ABR ignore les profils dont le débit est inférieur à celui-ci. Renvoie une valeur entière qui représente le profil bits par seconde. |
| Débit maximal :  getABRMaxBitRate | Débit maximal autorisé auquel l&#39;ABR peut basculer. Le changement d&#39;ABR ignore les profils dont le débit binaire est supérieur à celui-ci. Renvoie une valeur entière qui représente le profil bits par seconde. |
| Stratégie de commutation ABR :  getABRPolicy | Lorsque cela est possible, la lecture passe progressivement au profil de débit le plus élevé. Vous pouvez définir la stratégie de commutation ABR, qui détermine la vitesse à laquelle TVSDK bascule entre les profils. La valeur par défaut est Modéré. <ul><li>*Conservatrice* : Bascule vers le profil avec le débit binaire suivant plus élevé lorsque la bande passante est supérieure de 50 % à celle du débit binaire actuel. </li><li>*Modéré* : Passe au profil de débit supérieur suivant lorsque la bande passante est supérieure de 20 % à celle du débit actuel.</li><li>*Agressive* : Bascule immédiatement au profil de débit le plus élevé lorsque la bande passante est supérieure au débit binaire actuel.</li></ul><br/>Si le débit initial est nul ou non spécifié et qu’une stratégie est spécifiée, les débuts de lecture avec le profil de débit le plus faible pour Conservateur, le profil le plus proche du débit médian des profils disponibles pour Modéré et le profil de débit le plus élevé pour Agressive.<br/><br/>La stratégie fonctionne dans les limites des débits minimum et maximum, si elles sont spécifiées.  Renvoie le paramètre actuel de l&#39;énumération ABRControlParameters : <ul><li>ABR_CONSERVATIVE</li><li>ABR_MODERATE </li><li>ABR_AGGRESSIVE</li></ul><br>Voir aussi  [ABRPolicy](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/ABRControlParameters.ABRPolicy.html). |

>[!NOTE]
>
>* Le mécanisme de basculement TVSDK peut remplacer ces paramètres, car TVSDK favorise une lecture continue plutôt que le strict respect des paramètres de contrôle.
>* Lorsque le débit binaire change, TVSDK distribue des événements `onProfileChanged` dans `PlaybackEventListener`.


## Activation du contrôle ABR personnalisé dans l&#39;implémentation de référence {#section_72A6E7263E1441DD8D7E0690285515E6}

Le débit binaire adaptatif (ABR) est activé par défaut dans le SDK TVSDK. Vous pouvez utiliser l’interface utilisateur Paramètres Primetime pour remplacer le comportement par défaut de TVSDK dans l’implémentation de référence en configurant un contrôle ABR personnalisé.

Pour activer l’ABR personnalisé via l’interface utilisateur des paramètres :

* Ouvrez la boîte de dialogue Paramètres Primetime.
* Sélectionnez **[!UICONTROL ABR controls]**.

   ![](assets/abr-configuration.jpg)

* Appuyez sur le contrôle [!UICONTROL Enable ON] pour afficher `OFF`.

`PlaybackManager` ne définit les paramètres ABR que si [isABRControlEnabled](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html) renvoie true (ON). Si elle renvoie false (OFF), `PlaybackManager` utilise le contrôle ABR par défaut, de sorte que les débits initial, minimal et maximal seront tous 0 et que la stratégie ABR sera `ABR_MODERATE`.

## Configurer pour les faibles débits {#section_5451691CBBD24542AD54A474D222CD39}

Pour certains taux de lecture à faible débit, TVSDK bascule par défaut sur le flux audio uniquement et la lecture apparaît figée. Vous pouvez configurer le lecteur de sorte qu’il ne rencontre jamais de situation où il passe à l’audio uniquement.

* Implémentez l&#39;interface [IPlaybackConfig](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html) :

* Assurez-vous que [getABRMinBitRate](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html#getABRMinBitRate()) est supérieur au débit binaire audio uniquement (supérieur à 64000).
* Vérifiez que [isABRControlEnabled](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html#isABRControlEnabled()) est activé.