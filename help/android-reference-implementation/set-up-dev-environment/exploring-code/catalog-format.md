---
description: L’implémentation de référence Primetime utilise un format de flux basé sur JSON pour les réponses. Ce format est analysé à l’aide d’une implémentation de l’interface IFeedItemAdapter .
title: Format du catalogue
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 0%

---

# Format du catalogue {#catalog-format}

L’implémentation de référence Primetime utilise un format de flux basé sur JSON pour les réponses. Ce format est analysé à l’aide d’une implémentation de l’interface IFeedItemAdapter .

>[!NOTE]
>
>Ce format de flux est l’exemple de format utilisé par l’implémentation de référence et sert d’exemple de la manière dont le format peut être analysé et mappé à l’interface du flux. Vous pouvez utiliser votre propre format de flux d’entrée avec vos propres mises en oeuvre de l’interface de flux.

À un niveau élevé, le format est constitué d’un tableau d’entrées de contenu. Chaque entrée représente un contenu vidéo publié en direct ou VOD :

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

Chaque entrée de flux est un objet JSON avec un ensemble donné d’attributs :

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
| `id` | Identifiant/guide unique du contenu tel que défini par le système de publication de flux. |
| `title` | Titre du contenu. |
| `description` | Description du contenu. |
| `categories` | Liste des catégories balisées pour le contenu pouvant être utilisé par l’application pour améliorer l’expérience de l’utilisateur. Lisez les propriétés du contenu. |
| `keywords` | L’application peut utiliser une liste de mots-clés séparés par des virgules pour améliorer l’expérience de l’utilisateur. Lisez les propriétés du contenu. |
| `isLive` | true ou false, indiquant s’il s’agit d’un flux Live ou VOD. |
| `content` | Tableau d’objets JSON avec des formats alternatifs pour le contenu, ainsi que les URL correspondantes. Par exemple, il peut y avoir des url pour les formats f4m et m3u8. Les attributs d’objet JSON sont décrits plus loin ci-dessous. |
| `thumbnails` | Tableau d’objets JSON avec des URL pour différentes tailles de miniatures. Les attributs d’objet JSON sont définis ci-dessous. |
| `metadata` | Objet JSON définissant des métadonnées pour le contenu, ces métadonnées sont actuellement limitées aux métadonnées associées aux publicités. L’objet de métadonnées est défini ci-dessous. |

Le bloc de code suivant définit les objets JSON qui forment le tableau de **objet de contenu**:

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

Le bloc de code suivant définit les objets JSON qui forment le tableau de **objet miniature**:

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
| format | Une chaîne indiquant le format du fichier miniature, par exemple, JPEG, PNG, etc. |
| height | Hauteur de la miniature. Dans l’application de référence, la miniature dont la hauteur et la largeur sont les plus petites est renvoyée sous la forme d’une petite miniature, tandis que celle dont la largeur et la hauteur sont les plus grandes est renvoyée sous la forme d’une grande miniature. |
| width | Largeur de la miniature. Dans l’application de référence, la miniature dont la hauteur et la largeur sont les plus petites est renvoyée sous la forme d’une petite miniature, tandis que celle dont la largeur et la hauteur sont les plus grandes est renvoyée sous la forme d’une grande miniature. |
| url | URL du fichier de miniature. |

Le bloc de code suivant définit la variable **objet metadata**:

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
| ad | Métadonnées liées aux publicités. |
| type | Il peut s’agir de publicités Primetime, de coupures publicitaires directes ou de marqueurs publicitaires personnalisés. <br/><br/>Le PSDK fournit une prise en charge intégrée pour les types de métadonnées suivants : métadonnées liées à l’Auditude pour la fonction AdServing Primetime (publicités Primetime), coupures publicitaires directes avec URL de publicité (coupures publicitaires directes) et marqueurs publicitaires personnalisés qui fournissent la période pour chaque marqueur de publicité (marqueurs de publicité personnalisés). Chaque type dispose d’un AdProvider intégré dans le PSDK qui traite les métadonnées.  <br/><br/>Le format JSON de chacun d’eux a été défini ci-dessous. |
| détails | Inclut les attributs de métadonnées de publicité. Les deux types de métadonnées publicitaires disposent de leur propre jeu d’attributs défini ci-dessous. Pour les types intégrés, les attributs inclus définissent les données attendues par le PSDK pour ce type. |
| droits | Métadonnées liées au droit |
| id | Identifiant de ressource multimédia utilisé pour les demandes d’autorisation par rapport au service de laissez-passer de télévision payante Adobe Primetime. L’ID peut être une chaîne de texte ou une chaîne mRSS codée en HTML. Tout contenu multimédia nécessitant une autorisation doit contenir un identifiant de ressource valide. |
