---
seo-title: Contrôles de protection de sortie
title: Contrôles de protection de sortie
uuid: a0518392-cd33-4ef0-834c-f90145a9b421
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Contrôles de protection de sortie{#output-protection-controls}

Le paramètre de protection de sortie contrôle si la sortie vers des périphériques de rendu externes est protégée. Vous pouvez spécifier des restrictions pour les sorties analogiques et numériques indépendamment.

Contrôle si la sortie vers des périphériques de rendu externes doit être restreinte. Un périphérique externe est défini comme tout périphérique vidéo ou audio qui n’est pas incorporé à l’ordinateur. Les écrans intégrés, comme ceux des ordinateurs portables, ne sont pas considérés comme externes dans le scénario des contrôles de protection de sortie.

Les types de connexion OTA (survol) sont tous par défaut, mais peuvent être placés sur liste blanche explicitement si nécessaire. Les connexions OTA prises en charge sont les suivantes : Miracast, AirPlay, DLNA et WIDI.

**Protection de sortie basée sur la résolution : (Disponible à partir de la version 5.3.) ** Ceci offre une protection de sortie basée sur le nombre de pixels verticaux du contenu, ce qui permet de spécifier diverses exigences de protection en fonction du nombre de pixels verticaux.

Les options/niveaux d’application suivants sont disponibles :

| Option | Pris en charge sur les périphériques analogiques | Pris en charge sur les périphériques numériques |
|---|---|---|
| **Obligatoire** — La protection de sortie analogique (ACP) ou Copier le système de gestion de génération - La protection de sortie analogique (CGMS-A) doit être activée pour que le contenu soit lu sur un périphérique externe. Les clients DRM Primetime doivent activer la protection de la sortie à l&#39;aide de ACP ou de CGMS-A. Sur les périphériques prenant en charge les deux, les clients DRM 3.0 de Primetime tentent d’activer les deux. Cependant, un seul doit être activé pour lire le contenu. | OUI | OUI |
| **ACP requis** — Une protection de sortie ACP est requise. La lecture n’est pas autorisée sur CGMS-A. Les clients de Primetime DRM 2.0 ne prennent pas en charge cette option. S’il est défini, un client DRM 2.0 Primetime se comporte comme si l’option &quot;Aucune lecture&quot; avait été spécifiée. | OUI | - |
| **Utiliser si disponible** — Tentez d’activer la protection de sortie ACP et CGMS-A si disponible et autorisez la lecture si elle n’est pas disponible. Les clients de Primetime DRM 3.0 essaient d&#39;activer le ACP et le CGMS-A, si possible. Les clients de Primetime DRM 2.0 essaient seulement d&#39;activer ACP ou CGMS-A. Par exemple, le client DRM de Primetime tente d&#39;activer ACP ou CGMS-A. Si la tentative réussit, l’autre option ne peut pas être activée. Si la tentative échoue, une seconde tentative est alors effectuée pour activer l’autre option. Même si les deux tentatives échouent, le contenu est alors lu de toute façon. | OUI | OUI |
| **Utiliser le PVA si disponible** — Tentez d’activer la protection de sortie ACP si elle est disponible, mais autorisez la lecture si elle n’est pas disponible. La protection n&#39;est pas disponible sur CGMS-A. Les clients de Primetime DRM 2.0 ne prennent pas en charge cette option. S’il est défini, un client DRM 2.0 Primetime se comporte comme si l’option &quot;Aucune protection&quot; avait été spécifiée. | OUI | - |
| **Utiliser CGMS-A si disponible **— Tentez d’activer la protection de sortie CGMS-A si disponible, mais autorisez la lecture si elle n’est pas disponible. La protection n&#39;est pas disponible sur ACP. Les clients de Primetime DRM 2.0 ne prennent pas en charge cette option. S’il est défini, un client DRM 2.0 Primetime se comporte comme si l’option &quot;Aucune protection&quot; avait été spécifiée. | OUI | - |
| **Aucune protection** — Aucune activation de la protection de sortie n’est appliquée pour les sorties analogiques et numériques. | OUI | OUI |
| **Aucune lecture** — N’autorisez pas la lecture sur un périphérique externe pour les sorties analogiques et numériques. | OUI | OUI |

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Bien que ces règles soient appliquées de manière cohérente sur toutes les plates-formes, vous ne pouvez activer la protection de sortie en toute sécurité que sur les plates-formes Windows. Sur d’autres plateformes, telles que Macintosh et Linux, aucune fonction de système d’exploitation n’est disponible pour les applications tierces.

Exemple de cas d’utilisation : Certains contenus peuvent imposer des contrôles de protection de sortie et, par conséquent, le distributeur de contenu peut définir le niveau de protection. Si l’option &quot;Obligatoire&quot; est spécifiée et que la lecture est tentée sur un Macintosh, le client ne lit pas le contenu sur des périphériques externes. Le contenu peut être lu sur des moniteurs internes.

Si l’option &quot;Obligatoire&quot; est spécifiée et que la lecture est tentée sous Linux, le client ne lit aucun contenu sur aucun périphérique, car il ne peut pas faire de distinction entre les périphériques internes et externes.

Si vous spécifiez &quot;Utiliser si disponible&quot;, la protection de sortie est activée lorsque cela est possible. Par exemple, sur les systèmes Windows qui prennent en charge le protocole COPP (Certified Output Protection Protocol), le contenu est transmis avec protection de sortie à un affichage externe. Cet exemple est parfois appelé *`selectable output control`*.
