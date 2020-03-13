---
seo-title: Droits de lecture
title: Droits de lecture
uuid: 90f2a7a6-6637-4d10-9afe-6d2e77fc4185
translation-type: tm+mt
source-git-commit: ed1430bdcb590a53fa69b324ef340ad636b2fa7c

---


# Droits de lecture {#play-rights}

Le tableau suivant décrit les préférences de droits de lecture :

| Préférence | Description |
|--- |--- |
| Fenêtre de lecture | durée de validité d’une licence (en minutes) après la première lecture du contenu protégé par l’utilisateur. |
| Protection Output | Contrôle si la sortie vers des périphériques de rendu externes doit être protégée. Les sorties analogiques et numériques peuvent être spécifiées indépendamment. |
| Restrictions | Liste noire des versions client non autorisées à lire le contenu. Toutes les colonnes sont facultatives. |
| DRM | Spécifie un de versions DRM qui ne sont pas autorisées à lire le contenu protégé. |
| Exécution | Spécifie un de versions d’exécution qui ne sont pas autorisées à lire le contenu protégé. |
| Niveau de sécurité minimal |  |
| DRM | Niveau minimum de sécurité DRM requis pour lire le contenu protégé. |
| Exécution | Niveau de sécurité minimal d’exécution requis pour lire le contenu protégé. |
| Applications autorisées | Liste blanche des applications clientes autorisées à lire le contenu. Si aucune application n’est spécifiée, tout fichier SWF ou toute application AIR est autorisé. |
| SWF |  d’URL SWF autorisées à lire le contenu protégé. |
| AIR |  des applications AIR autorisées à lire du contenu protégé. L’ID de l’éditeur est requis, les champs restants sont facultatifs. |

Flash Access Manager prend en charge les stratégies contenant plusieurs droits de lecture. Pour créer une stratégie avec plusieurs jeux de droite, utilisez le bouton &quot;Ajouter jeu supplémentaire de droite&quot; et renseignez les attributs souhaités pour chaque jeu de droite.

Lors de l’utilisation d’une licence, le client utilise le premier droit de lecture pour lequel il répond à toutes les exigences. Plusieurs droits de lecture peuvent être utilisés pour spécifier différentes restrictions pour différents systèmes d’exploitation. Par exemple, il est possible de spécifier un droit avec la protection Output requise pour Windows (en mettant les versions DRM sur liste noire sous Macintosh et Linux) et un second droit avec la protection Output Protection &quot;Use if available&quot; sur d&#39;autres plates-formes (en mettant les versions DRM sur liste noire sous Windows).
