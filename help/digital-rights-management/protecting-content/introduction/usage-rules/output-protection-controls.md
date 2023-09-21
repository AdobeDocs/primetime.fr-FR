---
title: Contrôles de protection de sortie
description: Contrôles de protection de sortie
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 0%

---

# Contrôles de protection de sortie{#output-protection-controls}

Le paramètre de protection de sortie contrôle si la sortie vers des périphériques de rendu externes est protégée. Vous pouvez spécifier des restrictions pour les sorties analogique et numérique indépendamment.

Contrôle si la sortie vers les périphériques de rendu externes doit être limitée. Un appareil externe est défini comme tout appareil vidéo ou audio qui n’est pas incorporé à l’ordinateur. Les écrans intégrés, tels que ceux des ordinateurs portables, ne sont pas considérés comme externes dans le scénario des contrôles de protection de sortie.

Les types de connexion en direct (OTA) sont tous des blocs répertoriés par défaut, mais peuvent être autorisés explicitement s’il y a lieu. Les connexions OTA prises en charge incluent : Miracast, AirPlay, DLNA et WIDI.

**Protection des sorties basée sur la résolution : (disponible à partir de la version 5.3.) ** Vous bénéficiez ainsi d’une protection de sortie basée sur le nombre de pixels verticaux du contenu, ce qui vous permet de définir diverses exigences de protection en fonction du nombre de pixels verticaux.

Les options/niveaux d’application suivants sont disponibles :

| Option | Pris en charge dans les appareils analogiques | Pris en charge dans les appareils numériques |
|---|---|---|
| **Obligatoire** — Analog Copy Protection (ACP) ou Copy Generation Management System - La protection de sortie Analog (CGMS-A) doit être activée afin de lire le contenu sur un appareil externe. Les clients DRM Primetime doivent activer la protection de sortie à l’aide de ACP ou CGMS-A. Sur les appareils qui prennent en charge les deux, les clients Primetime DRM 3.0 tentent d’activer les deux. Toutefois, un seul doit être activé pour lire le contenu. | OUI | OUI |
| **ACP requis** — Une protection de sortie ACP est requise. La lecture n’est pas autorisée sur CGMS-A. Les clients Primetime DRM 2.0 ne prennent pas en charge cette option. S’il est défini, un client DRM 2.0 Primetime se comporte comme si l’option &quot;No Playback&quot; (Pas de lecture) avait été spécifiée. | OUI | - |
| **Utilisation si disponible** — Essayez d’activer la protection de sortie ACP et CGMS-A si elle est disponible et autorisez la lecture si elle n’est pas disponible. Si possible, les clients Primetime DRM 3.0 tentent d’activer à la fois le ACP et le CGMS-A. Les clients Primetime DRM 2.0 tentent uniquement d’activer les composants ACP ou CGMS-A. Par exemple, le client DRM Primetime tente d’activer les fonctions ACP ou CGMS-A. Si la tentative réussit, l’autre option ne peut pas être activée. Si la tentative échoue, une seconde tentative est alors effectuée pour activer l’autre option. Même si les deux tentatives échouent, le contenu est alors lu de toute façon. | OUI | OUI |
| **Utiliser le ACP si disponible** — Essayez d’activer la protection de sortie ACP si elle est disponible, mais autorisez la lecture si elle n’est pas disponible. La protection n’est pas disponible sur le CGMS-A. Les clients Primetime DRM 2.0 ne prennent pas en charge cette option. S’il est défini, un client DRM 2.0 Primetime se comporte comme si l’option &quot;Aucune protection&quot; avait été spécifiée. | OUI | - |
| **Utilisez CGMS-A s’il est disponible **— Tentez d’activer la protection de sortie CGMS-A si elle est disponible, mais autorisez la lecture si elle n’est pas disponible. La protection n&#39;est pas disponible sur ACP. Les clients Primetime DRM 2.0 ne prennent pas en charge cette option. S’il est défini, un client DRM 2.0 Primetime se comporte comme si l’option &quot;Aucune protection&quot; avait été spécifiée. | OUI | - |
| **Pas de protection** — Aucune activation de la protection de sortie n’est appliquée pour les sorties analogique et numérique. | OUI | OUI |
| **Pas de lecture** — Ne pas autoriser la lecture sur un appareil externe pour les sorties analogique et numérique. | OUI | OUI |

>[!NOTE]
>
>Bien que ces règles soient appliquées de manière cohérente sur toutes les plateformes, vous ne pouvez activer la protection de sortie que de manière sécurisée sur les plateformes Windows. Sur d’autres plateformes, telles que Macintosh et Linux, aucune fonction de système d’exploitation compatible n’est disponible pour les applications tierces.

Exemple de cas d’utilisation : un contenu peut imposer des contrôles de protection de sortie et, par conséquent, le distributeur de contenu peut définir le niveau de protection. Si &quot;Obligatoire&quot; est spécifié et que la lecture est tentée sur un Macintosh, le client ne lit pas le contenu sur des appareils externes. Le contenu peut être lu sur des moniteurs internes.

Si &quot;Obligatoire&quot; est spécifié et que la lecture est tentée sous Linux, le client ne lit le contenu sur aucun appareil, car il ne peut pas différencier les appareils internes et externes.

Si vous indiquez &quot;Utiliser si disponible&quot;, la protection de sortie est activée lorsque cela est possible. Par exemple, sur les systèmes Windows qui prennent en charge le protocole COPP (Certified Output Protection Protocol), le contenu est transmis avec protection de sortie à un affichage externe. Cet exemple est parfois appelé *`selectable output control`*.
