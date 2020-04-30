---
seo-title: Utilisation des stratégies de protection d’Output
title: Utilisation des stratégies de protection d’Output
uuid: f00d2a97-0036-41a6-ab44-391cc40b146e
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Utilisation des stratégies de protection d’Output{#using-output-protection-policies}

**Politiques de protection de la production à large bande**

Widevine prend en charge en mode natif les restrictions de protection de sortie analogique et numérique. Reportez-vous à la documentation de votre prestataire Widevine sur la façon de joindre ces stratégies aux licences générées.

Si vous utilisez Expressplay en tant que prestataire Widevine, associez des stratégies de protection de sortie numérique au moment de la génération de jetons via l’indicateur hdcpOutputControl :
Les valeurs autorisées sont 0, 1, 2 où 0 = HDCP_NONE, 1 = HDCP_V1, 2 = HDCP_V2. HDCP_V1 et HDCP_V2 appliquent respectivement les versions 1.X et 2.X du HDCP.

Expressplay ne prend actuellement pas en charge l’attachement de restrictions de sortie analogique

**Stratégies de protection de sortie PlayReady**

PlayReady prend également en charge de manière native les restrictions de protection de sortie analogique et numérique. Valeurs de niveau de protection de sortie que vous pouvez définir. La page Niveaux [de protection](https://msdn.microsoft.com/en-us/library/dn468831.aspx) de sortie documents les valeurs que vous pouvez définir et le comportement attendu du client.

Si vous utilisez Expressplay, associez des valeurs de niveau de protection de sortie au moment de la génération du jeton par le biais de l’indicateur compresséDigitalAudioOPL, uncompresséDigitalAudioOPL, compresséDigitalVideoOPL, uncompresséDigitalVideoOPL et de l’indicateur unknownOutputBehavior. Ces informations figurent dans la demande de jeton de licence [PlayReady.](https://www.expressplay.com/developer/restapi/#playready-license-token-request)
