---
description: L’implémentation de la référence Primetime utilise un format de flux JSON pour les réponses. Ce format est analysé à l'aide d'une implémentation de l'interface IFeedItemAdapter.
seo-description: L’implémentation de la référence Primetime utilise un format de flux JSON pour les réponses. Ce format est analysé à l'aide d'une implémentation de l'interface IFeedItemAdapter.
seo-title: Format du catalogue
title: Format du catalogue
uuid: 6e1a526f-c0bb-403d-a792-666caf5479a5
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%

---


# Format de catalogue {#catalog-format}

L’implémentation de la référence Primetime utilise un format de flux JSON pour les réponses. Ce format est analysé à l&#39;aide d&#39;une implémentation de l&#39;interface IFeedItemAdapter.

>[!NOTE]
>
>Ce format de flux est l’exemple de format utilisé par l’implémentation de référence et sert d’exemple de la façon dont le format peut être analysé et mappé à l’interface de flux. Vous pouvez utiliser votre propre format de flux d’entrée avec vos propres implémentations d’interface de flux.

A un niveau élevé, le format est constitué d’un tableau d’entrées de contenu. Chaque entrée représente un contenu vidéo publié en direct ou VOD :

```
{
    "entries": [
        {
        },
        {
        },
        ...
    ]
}
```

Chaque entrée de flux est un objet JSON doté d’un ensemble donné d’attributs :

```
{
    "entries": [
        
            "id": "episode1",
            "title": "My episode1",
            "description": "This is an episode.",
            "categories": "documentary, educational, children",
            "keywords": "List, of, comma, separated, keywords",
            "isLive": false,
            "content":  [
                
                },
                
                },
            ],
            "thumbnails": [
                
                },
                
                }
            ]
            "metadata": 
            } 
        }
    ]
}
```

| Propriété | Description |
|---|---|
| `id` | Identificateur/guide unique pour le contenu tel que défini par le système de publication de flux. |
| `title` | Titre du contenu. |
| `description` | Description du contenu. |
| `categories` | Liste de catégories balisées pour le contenu qui peut être utilisé par l’application pour améliorer l’expérience de l’utilisateur. Lisez les propriétés du contenu. |
| `keywords` | L’application peut utiliser une liste de mots-clés séparés par des virgules pour améliorer l’expérience de l’utilisateur. Lisez les propriétés du contenu. |
| `isLive` | true ou false, indiquant s’il s’agit d’un flux en direct ou VOD. |
| `content` | Tableau d’objets JSON avec des formats de substitution pour le contenu, ainsi que les URL correspondantes. Par exemple, il peut y avoir des url pour les formats f4m et m3u8. Les attributs d’objet JSON sont décrits plus loin ci-dessous. |
| `thumbnails` | Tableau d’objets JSON avec des URL pour différentes tailles de miniatures. Les attributs d’objet JSON sont définis ci-dessous. |
| `metadata` | Un objet JSON définissant des métadonnées pour le contenu ; actuellement, ces métadonnées sont limitées aux métadonnées associées à la publicité. L’objet metadata est défini ci-dessous. |

Le bloc de code suivant définit les objets JSON qui forment le tableau des **objets de contenu** :

```
"content":  [
    {
        "format": "M3U8",
        "url": "https://adobeprimetime-f.akamaihd.net/i/
<i>longstringofcharacters</i>/
                 Episode_,640x360_1000,640x360_700,_b.mp4.csmil/master.m3u8",
        "language": "en"
    }  
],
```

| Propriété | Description |
|--- |--- |
| format | Doit être au format m3u8 pour Android. |
| url | URL du flux vidéo pour le format donné. |

Le bloc de code suivant définit les objets JSON qui forment le tableau des **objets miniatures** :

```
"thumbnails": [
    {
        "format": "JPEG",
        "height":  "90",
        "width": "160",
        "url": "https://example.com/small.jpg"
    },
    {
        "format": "JPEG",
        "height": "450",
        "width": "800",
        "url": "https://example.com/large.jpg"
    }
],
```

| Propriété | Description |
|---|---|
| format | Chaîne indiquant le format du fichier miniature, par exemple, JPEG, PNG, etc. |
| hauteur | Hauteur de la miniature. Dans l’application de référence, la miniature dont la hauteur et la largeur sont les plus faibles est renvoyée sous forme de petite miniature et celle dont la largeur et la hauteur sont les plus élevées est renvoyée sous forme de grande miniature. |
| width | Largeur de la miniature. Dans l’application de référence, la miniature dont la hauteur et la largeur sont les plus faibles est renvoyée sous forme de petite miniature et celle dont la largeur et la hauteur sont les plus élevées est renvoyée sous forme de grande miniature. |
| url | URL du fichier miniature. |

Le bloc de code suivant définit l&#39;objet de métadonnées **** :

```
"metadata" : {
    "ad" : {
        "type" : "",
        "details" : {
        }
    }
    "entitlement" : {
        "id" : ""
    }
}
```

| Propriété | Description |
|--- |--- |
| publicité | Métadonnées liées à la publicité. |
| type | Il peut s’agir de publicités Primetime, de coupures publicitaires directes ou de marqueurs publicitaires personnalisés. <br/><br/>Le PSDK offre une prise en charge intégrée des types de métadonnées suivants : Métadonnées liées à l’Auditude pour la fonction AdServing Primetime (publicités Primetime), les coupures publicitaires directes avec des url publicitaires (sauts d’annonce directs) et les marqueurs publicitaires personnalisés qui fournissent la période pour chaque marqueur d’annonce (marqueurs d’annonce personnalisés). Chaque type dispose d’un AdProvider intégré dans le PSDK qui traite les métadonnées.  <br/><br/>Le format JSON de chacun de ces fichiers a été défini ci-dessous. |
| détails | Inclut les attributs de métadonnées publicitaires. Les deux types de métadonnées publicitaires possèdent leur propre jeu d’attributs défini ci-dessous. Pour les types intégrés, les attributs inclus définissent les données attendues par le PSDK pour ce type. |
| droits | Métadonnées liées aux droits |
| id | ID de ressource média utilisé pour les demandes d&#39;autorisation par rapport au service de laissez-passer de télévision payante en Adobe Primetime. L’ID peut être une chaîne de texte ou une chaîne mRSS codée au format HTML. Tout contenu multimédia nécessitant une autorisation doit contenir un ID de ressource valide. |

