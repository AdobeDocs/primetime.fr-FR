---
seo-title: Contrôles de protection de sortie
title: Contrôles de protection de sortie
uuid: a0518392-cd33-4ef0-834c-f90145a9b421
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Contrôles de protection de sortie{#output-protection-controls}

Le paramètre de protection de sortie contrôle si la sortie sur des périphériques de rendu externes est protégée. Vous pouvez définir des restrictions pour les sorties analogiques et numériques indépendamment.

Contrôle si la sortie sur les périphériques de rendu externes doit être restreinte. Un périphérique externe est défini comme tout périphérique vidéo ou audio qui n’est pas incorporé à l’ordinateur. Les écrans intégrés, tels que ceux des ordinateurs portables, ne sont pas considérés comme externes dans le scénario des contrôles de protection de sortie.

Les types de connexion OTA (survol) sont tous blacklistés par défaut, mais peuvent être autorisés explicitement si nécessaire. Les connexions OTA prises en charge sont les suivantes : Miracast, AirPlay, DLNA et WIDI.

**Protection de la sortie basée sur la résolution : (Disponible à partir de la version 5.3.) ** Ceci offre une protection de sortie basée sur le nombre de pixels verticaux du contenu, ce qui permet de spécifier diverses exigences de protection en fonction du nombre de pixels verticaux.

Les options/niveaux d&#39;application suivants sont disponibles :

| Option | Pris en charge sur les périphériques analogiques | Pris en charge sur les périphériques numériques |
|---|---|---|
| **Obligatoire** — Protection de la copie analogique (ACP) ou Système de gestion de la génération de copies - La protection de sortie analogique (CGMS-A) doit être activée pour lire le contenu sur un périphérique externe. Les clients DRM Primetime doivent activer la protection de la sortie en utilisant les systèmes ACP ou CGMS-A. Sur les périphériques qui prennent en charge les deux, les clients DRM 3.0 de Primetime tentent d’activer les deux. Cependant, un seul doit être activé pour lire le contenu. | OUI | OUI |
| **PVA requis** — La protection de la sortie PVA est requise. La lecture n&#39;est pas autorisée sur CGMS-A. Les clients DRM 2.0 de Primetime ne prennent pas en charge cette option. S’il est défini, un client DRM 2.0 Primetime se comporte comme si l’option &quot;Aucune lecture&quot; avait été spécifiée. | OUI | - |
| **Utiliser si disponible** : tentez d&#39;activer la protection de sortie ACP et CGMS-A si disponible et d&#39;autoriser la lecture si elle n&#39;est pas disponible. Si possible, les clients de Primetime DRM 3.0 tentent d&#39;activer à la fois le ACP et le CGMS-A. Les clients DRM 2.0 de Primetime tentent uniquement d&#39;activer le ACP ou le CGMS-A. Par exemple, le client DRM de Primetime tente d&#39;activer le protocole ACP ou CGMS-A. Si la tentative réussit, l&#39;autre option ne peut pas être activée. Si la tentative échoue, une seconde tentative est alors effectuée pour activer l’autre option. Même si les deux tentatives échouent, le contenu est alors lu de toute façon. | OUI | OUI |
| **Utiliser ACP si disponible** : tentez d&#39;activer la protection de sortie ACP si disponible, mais autorisez la lecture si elle n&#39;est pas disponible. La protection n&#39;est pas disponible sur CGMS-A. Les clients DRM 2.0 de Primetime ne prennent pas en charge cette option. S’il est défini, un client DRM 2.0 de Primetime se comporte comme si l’option &quot;Aucune protection&quot; avait été spécifiée. | OUI | - |
| **Utilisez CGMS-A si disponible **— Tentez d&#39;activer la protection de sortie CGMS-A si disponible, mais autorisez la lecture si elle n&#39;est pas disponible. La protection n&#39;est pas disponible sur ACP. Les clients DRM 2.0 de Primetime ne prennent pas en charge cette option. S’il est défini, un client DRM 2.0 de Primetime se comporte comme si l’option &quot;Aucune protection&quot; avait été spécifiée. | OUI | - |
| **Aucune protection** : aucune activation de la protection de sortie n’est appliquée pour les sorties analogiques et numériques. | OUI | OUI |
| **Aucune lecture** : n’autorisez pas la lecture sur un périphérique externe pour les sorties analogiques et numériques. | OUI | OUI |

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Bien que ces règles soient appliquées de manière cohérente sur toutes les plates-formes, vous ne pouvez activer la protection de sortie en toute sécurité que sur les plates-formes Windows. Sur d’autres plates-formes, telles que Macintosh et Linux, aucune fonction de système d’exploitation compatible n’est disponible pour les applications tierces.

Exemple de cas d’utilisation : Certains contenus peuvent imposer des contrôles de protection de sortie et, par conséquent, le distributeur de contenu peut définir le niveau de protection. Si &quot;Obligatoire&quot; est spécifié et que la lecture est tentée sur un Macintosh, le client ne lit pas le contenu sur des périphériques externes. Le contenu peut être lu sur des moniteurs internes.

Si &quot;Obligatoire&quot; est spécifié et que la lecture est tentée sous Linux, le client ne lit pas le contenu sur aucun périphérique, car il ne peut pas faire de distinction entre les périphériques internes et externes.

Si vous spécifiez &quot;Utiliser si disponible&quot;, la protection de sortie est activée lorsque cela est possible. Par exemple, sur les systèmes Windows qui prennent en charge le protocole COPP (Certified Output Protection Protocol), le contenu est transmis avec protection de sortie à un affichage externe. Cet exemple est parfois appelé *`selectable output control`*.
