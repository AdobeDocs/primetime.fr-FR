---
description: Parfois, il arrive que le contenu ne puisse pas être lu. Cela peut être dû à un certain nombre de situations, notamment des erreurs dans la pile réseau du navigateur, la couche de transport, le système d’exploitation, l’exécution de Flash Player ou le système DRM Primetime.
title: Présentation des erreurs de déclenchement
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Déclenchement des erreurs {#triaging-errors}

Parfois, il arrive que le contenu ne puisse pas être lu. Cela peut être dû à un certain nombre de situations, notamment des erreurs dans la pile réseau du navigateur, la couche de transport, le système d’exploitation, l’exécution de Flash Player ou le système DRM Primetime.

La première étape de diagnostic consiste à déterminer si le problème se manifeste sans cryptage DRM introduit dans l’équation. Essayez de regrouper le contenu, mais demandez au programme de chiffrement de ne pas le chiffrer. Si le problème existe toujours, il s’agit probablement d’un problème de codage ou de conditionnement du contenu, ou quelque part dans l’infrastructure réseau. Si le problème disparaît lorsque le contenu est conditionné sans chiffrement, l’échec de la lecture est probablement dû à un problème DRM et vous devez vous engager dans le triage client/serveur.

Primetime DRM (en dehors de Primetime Cloud DRM) est sur le marché depuis plusieurs années. Par conséquent, il existe une mine d’informations provenant de la communauté sur le dépannage et la configuration de Primetime DRM. Adobe a fourni un forum aux utilisateurs de Primetime DRM (anciennement appelé Accès Adobe) pour rassembler et partager les problèmes et les résolutions. Pour déterminer si votre problème a déjà été discuté, veuillez vérifier : [https://forums.adobe.com/community/adobe_access](https://forums.adobe.com/community/adobe_access)

## Test des erreurs client {#section_D0EBAEB0C27F4B01BD44124DEE62F6BA}

Si le contenu n’est pas lu, examinez le panneau de droite des exemples de lecteurs vidéo, qui consigne les `DRMErrorEvent` cela se produit. Si un événement d’erreur se produit, il est corrélé à l’une des erreurs d’exécution de Flash Player :

* [Référence de message d’erreur du client DRM](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages); ou
* [Erreurs d’exécution du Flash AS3](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/runtimeErrors.html) (Les problèmes DRM démarrent à 3300)
