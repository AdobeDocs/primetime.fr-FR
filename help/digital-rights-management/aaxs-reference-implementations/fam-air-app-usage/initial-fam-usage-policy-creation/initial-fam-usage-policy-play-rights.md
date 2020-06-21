---
seo-title: Droits de lecture
title: Droits de lecture
uuid: 90f2a7a6-6637-4d10-9afe-6d2e77fc4185
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---


# Droits de lecture {#play-rights}

Le tableau suivant décrit les préférences de droits de lecture :

| Préférence | Description |
|--- |--- |
| Fenêtre de lecture | Durée de validité d’une licence (en minutes) après la première lecture du contenu protégé par l’utilisateur. |
| Protection Output | Contrôle si la sortie sur des périphériques de rendu externes doit être protégée. Les sorties analogiques et numériques peuvent être spécifiées indépendamment. |
| Restrictions | La Liste bloquée des versions client n’est pas autorisée à lire le contenu. Toutes les colonnes sont facultatives. |
| DRM | Spécifie une liste de versions DRM qui ne sont pas autorisées à lire du contenu protégé. |
| Exécution | Indique une liste de versions d’exécution qui ne sont pas autorisées à lire du contenu protégé. |
| Niveau de sécurité minimal |  |
| DRM | Niveau minimum de sécurité DRM requis pour lire le contenu protégé. |
| Exécution | Niveau de sécurité minimal d’exécution requis pour lire le contenu protégé. |
| Applications autorisées | Liste autorisée des applications clientes autorisées à lire du contenu. Si aucune application n’est spécifiée, toute application SWF ou AIR est autorisée. |
| SWF | Liste des URL SWF autorisées à lire du contenu protégé. |
| AIR | Liste des applications AIR autorisées à lire du contenu protégé. L’identifiant de l’éditeur est requis, les champs restants sont facultatifs. |

Flash Access Manager prend en charge les stratégies contenant plusieurs droits de lecture. Pour créer une stratégie avec plusieurs jeux de droite, utilisez le bouton &quot;Ajouter la lecture à droite supplémentaire&quot; et remplissez les attributs souhaités pour chaque jeu de droite.

Lors de l’utilisation d’une licence, le client utilise le premier logiciel Play Right pour lequel il répond à toutes les exigences. Plusieurs droits de lecture peuvent être utilisés pour spécifier différentes restrictions pour différents systèmes d&#39;exploitation. Par exemple, il est possible de spécifier un droit avec la protection Output requise pour Windows (en listant par bloc les versions DRM sur Macintosh et Linux) et un second droit avec la protection Output &quot;Utiliser si disponible&quot; sur d&#39;autres plates-formes (en listant par bloc les versions DRM sur Windows).
