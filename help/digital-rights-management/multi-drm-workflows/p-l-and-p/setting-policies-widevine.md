---
title: Utilisation des stratégies de protection de sortie
description: Utilisation des stratégies de protection de sortie
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# Utilisation des stratégies de protection de sortie{#using-output-protection-policies}

**Stratégies de protection des sorties étendues**

Widevine prend en charge de manière native les restrictions de protection des sorties analogique et numérique. Reportez-vous à la documentation de votre fournisseur de services Windows sur la manière de joindre ces stratégies aux licences générées.

Si vous utilisez Expressplay comme fournisseur de services Windows, joignez des stratégies de protection de sortie numérique au moment de la génération du jeton via l’indicateur hdcpOutputControl : les valeurs autorisées sont 0, 1, 2 où 0 = HDCP_NONE, 1 = HDCP_V1, 2 = HDCP_V2. HDCP_V1 et HDCP_V2 imposent respectivement les versions HDCP 1.X et 2.X.

Expressplay ne prend actuellement pas en charge l’ajout de restrictions de sortie analogique.

**Stratégies de protection de sortie PlayReady**

PlayReady prend également en charge de manière native les restrictions de protection des sorties analogique et numérique. Les valeurs de niveau de protection de sortie que vous pouvez définir. La page [Niveaux de protection de sortie](https://msdn.microsoft.com/en-us/library/dn468831.aspx) documente les valeurs que vous pouvez définir et leur comportement client attendu.

Si vous utilisez Expressplay, joignez des valeurs de niveau de protection de sortie au moment de la génération du jeton via l’indicateur compresséDigitalAudioOPL, uncompresséDigitalAudioOPL, compresséDigitalVideoOPL, uncompresséDigitalVideoOPL et unknownOutputBehavior . Ces informations sont documentées à l’adresse [Demande de jeton de licence PlayReady](https://www.expressplay.com/developer/restapi/#playready-license-token-request)
