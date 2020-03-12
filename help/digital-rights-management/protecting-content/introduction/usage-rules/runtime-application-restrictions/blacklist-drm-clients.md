---
description: 'null'
seo-description: 'null'
seo-title: Liste noire des clients DRM interdits d’accès au contenu protégé
title: Liste noire des clients DRM interdits d’accès au contenu protégé
uuid: 38bc024e-0c5b-4c1c-8d4b-94b9e0fec67e
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Liste noire des clients DRM interdits d’accès au contenu protégé {#blacklist-of-drm-clients-restricted-from-accessing-protected-content}

Cette liste noire indique les clients DRM Primetime qui ne peuvent pas accéder au contenu protégé. Vous faites une liste noire des clients par version et plateforme client.

Exemple de cas d’utilisation : Dans le  d’une violation de sécurité, une nouvelle version du client DRM Primetime peut être spécifiée comme version minimale requise pour l’acquisition de licence et la lecture de contenu. Le serveur de licences vérifie que le client DRM Primetime qui effectue la demande de licence satisfait aux exigences de version avant de délivrer une licence. Le client DRM Primetime vérifie également la version de la licence avant de lire le contenu. Cette vérification du client est requise dans le cas des domaines où une licence peut être transférée vers un autre ordinateur.

Une version client DRM Primetime peut être identifiée par les attributs spécifiés dans le tableau suivant :

| **Attribut** | **Valeurs prises en charge** | **Critères de correspondance** | **Description** |
|---|---|---|---|
|   | `“PC”, “PortingKit”` | Correspondance exacte | Indique si le client est exécuté sur un ordinateur de bureau ou sur un autre périphérique. |
| OS | `“Win”, “Mac”, “Linux”, “Android”, “iOS”, "ChromeOS"` | Correspondance exacte | Plateforme |
| Architecture | `“32”, “64”` | Correspondance exacte | 32 bits ou 64 bits |
| Type d’écran | `“PC”, “Mobile”, “TV”` | Correspondance exacte |  |
| Version d’exécution | Numéro de version valide. Par exemple, `“2.0.0”, "3.0", "4.0", "11.0"`, etc. | Correspond si la version du client est inférieure ou égale à la version spécifiée. | Le numéro de version est spécifié sous la forme d’une combinaison de nombres et de points (&quot;.&quot;) de n&#39;importe quelle longueur. |
| Version de la bibliothèque DRM Primetime | Numéro de version valide. Par exemple, `“2.0.0”`. | Correspond si la version du client est inférieure ou égale à la version spécifiée. | Le numéro de version est spécifié sous la forme d’une combinaison de nombres et de points (&quot;.&quot;) de n&#39;importe quelle longueur. |
| Fournisseur OEM | Chaîne du fournisseur OEM pouvant être située dans le certificat d’exécution délivré à un client qui transportait le DRM Primetime sur un périphérique. | Correspondance exacte | Chaîne d&#39;identification du fournisseur OEM pour le périphérique utilisant le kit de portage. |
| Modèle | Chaîne de modèle qui peut être située dans le certificat d’exécution délivré à un client qui a transféré le DRM Primetime sur un périphérique. Par exemple, `"iOS_Mobile", "Android_Mobile", "Chrome", "ChromeOS_ARM", "WindowsOnARM", "AVE"` | Correspondance exacte | Chaîne d&#39;identification du modèle de périphérique pour le périphérique utilisant le kit de portage. |

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Lors de la spécification d’une entrée dans la liste noire, vous pouvez définir des valeurs pour un ou plusieurs des attributs mentionnés dans le tableau précédent. Tout attribut non spécifié est traité comme un caractère générique. Si le client DRM Primetime correspond à toutes les valeurs spécifiées dans une entrée de liste noire, ce client ne peut pas accéder au contenu protégé.

