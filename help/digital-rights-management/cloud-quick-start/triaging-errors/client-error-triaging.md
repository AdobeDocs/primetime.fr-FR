---
description: Il arrive parfois que le contenu ne puisse pas être lu. Un certain nombre de situations peuvent en être à l’origine, notamment des erreurs dans la pile réseau du navigateur, la couche de transport, le système d’exploitation, l’exécution du Flash Player ou le système DRM Primetime.
seo-description: Il arrive parfois que le contenu ne puisse pas être lu. Un certain nombre de situations peuvent en être à l’origine, notamment des erreurs dans la pile réseau du navigateur, la couche de transport, le système d’exploitation, l’exécution du Flash Player ou le système DRM Primetime.
seo-title: Présentation des erreurs de tri
title: Présentation des erreurs de tri
uuid: 44b4ab0e-5f08-44b0-bcb5-a869f6add69b
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---


# Erreurs de déclenchement {#triaging-errors}

Il arrive parfois que le contenu ne puisse pas être lu. Un certain nombre de situations peuvent en être à l’origine, notamment des erreurs dans la pile réseau du navigateur, la couche de transport, le système d’exploitation, l’exécution du Flash Player ou le système DRM Primetime.

La première étape du diagnostic consiste à déterminer si le problème se manifeste sans le chiffrement DRM introduit dans l&#39;équation. Tentez d’assembler le contenu, mais demandez à l’outil de création de package de ne pas chiffrer le contenu. Si le problème existe toujours, il s&#39;agit probablement d&#39;un problème de codage ou d&#39;empaquetage du contenu, ou quelque part dans l&#39;infrastructure réseau. Si le problème disparaît lorsque le contenu est compressé sans chiffrement, l’échec de la lecture est probablement dû à un problème de gestion des droits numériques et vous devriez procéder à un triage client/serveur.

Primetime DRM (en dehors de Primetime Cloud DRM) est sur le marché depuis plusieurs années. Par conséquent, il existe une mine d’informations provenant de la communauté sur le dépannage et la configuration de Primetime DRM. L&#39;Adobe a fourni un forum aux utilisateurs de Primetime DRM (anciennement appelé Adobe Access) pour les agrégats et partager les problèmes et les résolutions. Pour déterminer si votre problème a déjà été abordé, veuillez vérifier : [https://forums.adobe.com/community/adobe_access](https://forums.adobe.com/community/adobe_access)

## Triage des erreurs client {#section_D0EBAEB0C27F4B01BD44124DEE62F6BA}

Si le contenu n’est pas lu, examinez le panneau de droite des exemples de lecteurs vidéo, qui consigne tout élément `DRMErrorEvent` qui se produit. Si un événement d&#39;erreur se produit, il est corrélé à l&#39;une des erreurs d&#39;exécution du Flash Player :

* [Référence](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages) du message d’erreur du client DRM ; ou
* [Erreurs](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/runtimeErrors.html)  d’exécution de Flash AS3 (DRM génère un début à 3300)

