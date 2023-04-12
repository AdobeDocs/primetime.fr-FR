---
title: Configuration système minimale
description: Configuration système minimale
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---


# Configuration système minimale {#minimum-system-requirements}

>[!NOTE]
>
>Le contenu de cette page est fourni à titre d’information uniquement. L’utilisation de cette API nécessite une licence actuelle de Adobe. Aucune utilisation non autorisée n’est autorisée.


## Présentation {#overview}

Ce document présente les exigences logicielles et matérielles actuelles pour la mise en oeuvre des intégrations d’authentification Adobe Primetime sur les plateformes prises en charge. Tous les navigateurs web/mobiles et systèmes d’exploitation pris en charge répertoriés ci-dessous bénéficieront de la prise en charge complète de l’équipe d’authentification Adobe Primetime, liée aux contrats de niveau de service (SLA) convenus.

En tant qu’équipe d’authentification Adobe Primetime, nous encourageons l’utilisation des dernières versions stables des navigateurs et des systèmes d’exploitation ; nous reconnaissons également l’existence de plateformes et de navigateurs non conformes/plus anciens qui sont actuellement en cours d’utilisation. Ces appareils obsolètes peuvent toujours fonctionner sans problème, mais ils seront plus sujets aux erreurs.

L’approche initiale pour atténuer les problèmes qui apparaissent sur ces plateformes obsolètes doit être mise à niveau vers les versions les plus récentes ; il peut s’agir de la version du système d’exploitation, de la version du navigateur ou de la version de l’application installée.

Tous les problèmes apparaissant sur ces plateformes seront traités au mieux par l’équipe d’authentification Adobe Primetime. 

Adobe Primetime encourage ses clients et ses partenaires à envisager une mise à niveau vers les versions les plus récentes afin de bénéficier de l’assistance complète d’Adobe en cas de problèmes potentiels, en plus des améliorations de performances, d’efficacité et de sécurité. 


## Configuration requise du navigateur et du système d’exploitation {#browser-OS-system-requirements}


| Navigateur web/mobile (†) | Versions prises en charge |
|---|---|
| Google Chrome | **70** ou ultérieure |
| Mozilla Firefox | **57** ou ultérieure |
| Apple Safari | **14** ou ultérieure |
| Microsoft Edge | **100** ou ultérieure |

(†) Adobe déconseille d’utiliser le mode privé ou incognito.

| Système d’exploitation | Versions prises en charge |
|---|---|
| *Android* | **7,0** (Nougat) ou version ultérieure |
| *iOS* | **14** ou ultérieure |
| *iPadOS* | **14** ou ultérieure |
| *tvOS* | **14** ou ultérieure |
| *SE Fire* | **5 (Android 5.1)** ou ultérieure |
| *Mac OS* | **10,13** ou ultérieure |
| *Microsoft Windows* | **10** ou ultérieure |




>[!NOTE]
>
>Cookies tiers : les flux de droits d’authentification Adobe Primetime peuvent échouer lorsque les cookies tiers sont désactivés.  Ce problème se produit uniquement lorsque les paramètres du navigateur sont modifiés. Pour tous les navigateurs pris en charge, l’authentification Primetime doit être fonctionnelle avec les paramètres par défaut.\
 

## Configuration requise pour les mises en oeuvre sans client (REST) {#general_clientless_reqs}

 
Tout appareil qui consommera des services d’authentification Adobe Primetime par le biais d’implémentations sans client **doit être en mesure de**:

* Fournissez un identifiant d’appareil haché unique. Si l’appareil ne fournit pas d’identifiant d’appareil haché unique, il doit pouvoir conserver un identifiant unique fourni par l’authentification Adobe Primetime. L’appareil doit pouvoir conserver l’identifiant unique de manière permanente dans son stockage local et fournir l’identifiant unique en tant qu’identifiant de périphérique lors d’appels aux API d’authentification Adobe Primetime.
* Générer des signatures numériques à l’aide de l’algorithme HMAC-SHA1
* Définition d’en-têtes HTTP arbitraires
* Utilisation des services web RESTful
* Analyse des formats de données XML et JSON
* Envoyer le trafic en utilisant HTTPS
* Gestion des codes d’erreur HTTP
