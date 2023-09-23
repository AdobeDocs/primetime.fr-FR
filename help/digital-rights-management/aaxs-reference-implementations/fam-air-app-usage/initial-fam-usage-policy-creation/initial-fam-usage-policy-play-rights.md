---
title: Droits de lecture
description: Droits de lecture
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# Droits de lecture {#play-rights}

Le tableau suivant décrit les préférences de droits de lecture :

| Préférence | Description |
|--- |--- |
| Fenêtre de lecture | La durée de validité d’une licence (en minutes) après la première lecture du contenu protégé par l’utilisateur. |
| Protection de sortie | Contrôle si la sortie vers les périphériques de rendu externes doit être protégée. Les sorties analogique et numérique peuvent être spécifiées indépendamment. |
| Restrictions | Liste bloquée de versions du client non autorisées à lire le contenu. Toutes les colonnes sont facultatives. |
| DRM | Indique une liste des versions DRM qui ne sont pas autorisées à lire du contenu protégé. |
| Runtime | Indique une liste de versions d’exécution qui ne sont pas autorisées à lire du contenu protégé. |
| Niveau de sécurité minimal |  |
| DRM | Niveau de sécurité DRM minimal requis pour lire le contenu protégé. |
| Runtime | Niveau de sécurité d’exécution minimal requis pour lire le contenu protégé. |
| Applications autorisées | Liste autorisée des applications clientes autorisées à lire le contenu. Si aucune application n’est spécifiée, tout SWF ou application AIR est autorisé. |
| SWF | Liste des URL de SWF autorisées à lire du contenu protégé. |
| AIR | Liste des applications AIR autorisées à lire du contenu protégé. L’identifiant de l’éditeur est obligatoire, les champs restants sont facultatifs. |

Flash Access Manager prend en charge les stratégies contenant plusieurs droits de lecture. Pour créer une stratégie avec plusieurs droits de lecture, utilisez le bouton &quot;Ajouter un droit de lecture supplémentaire&quot;, puis renseignez les attributs souhaités pour chaque droit de lecture.

Lors de l’utilisation d’une licence, le client utilise le premier droit de lecture correspondant à toutes les exigences. Plusieurs droits de lecture peuvent être utilisés pour spécifier différentes restrictions pour différents systèmes d’exploitation. Par exemple, il est possible de spécifier un droit avec la protection Output requise pour Windows (par liste bloquée des versions DRM sous Macintosh et Linux) et un second droit avec la protection Output &quot;Use if available&quot; sur d’autres plateformes (par liste bloquée des versions DRM sous Windows).
