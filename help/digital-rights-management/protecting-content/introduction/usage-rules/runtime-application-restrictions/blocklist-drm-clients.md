---
description: 'null'
seo-description: 'null'
seo-title: Liste bloquée des clients DRM limitée à l'accès au contenu protégé
title: Liste bloquée des clients DRM limitée à l'accès au contenu protégé
uuid: 38bc024e-0c5b-4c1c-8d4b-94b9e0fec67e
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---


# Liste bloquée des clients DRM limitée à l&#39;accès au contenu protégé {#blocklist-of-drm-clients-restricted-from-accessing-protected-content}

Cette liste bloquée spécifie les clients DRM Primetime qui ne peuvent pas accéder au contenu protégé. Vous liste bloquée les clients par version et plateforme client.

Exemple de cas d’utilisation : Dans le événement d’une brèche de sécurité, une nouvelle version du client DRM Primetime peut être spécifiée comme version minimale requise pour l’acquisition de licence et la lecture de contenu. Le serveur de licences vérifie que le client DRM Primetime qui effectue la demande de licence satisfait aux exigences de version avant de délivrer une licence. Le client DRM Primetime vérifie également la version de la licence avant de lire le contenu. Ce contrôle client est requis dans le cas des domaines où une licence peut être transférée à un autre ordinateur.

Une version client DRM Primetime peut être identifiée par les attributs spécifiés dans le tableau suivant :

| **Attribut** | **Valeurs prises en charge** | **Critères de correspondance** | **Description** |
|---|---|---|---|
| Environnement | `“PC”, “PortingKit”` | Correspondance exacte | Indique si le client s’exécute sur un bureau ou sur un autre périphérique. |
| SE | `“Win”, “Mac”, “Linux”, “Android”, “iOS”, "ChromeOS"` | Correspondance exacte | Platform |
| Architecture | `“32”, “64”` | Correspondance exacte | 32 bits ou 64 bits |
| Type d’écran | `“PC”, “Mobile”, “TV”` | Correspondance exacte |  |
| Version d’exécution | Numéro de version valide. Par exemple, `“2.0.0”, "3.0", "4.0", "11.0"`, etc. | Correspond si la version du client est inférieure ou égale à la version spécifiée. | Le numéro de version est spécifié sous la forme d’une combinaison de nombres et de points (&quot;.&quot;) de toute longueur. |
| Version de la bibliothèque DRM Primetime | Numéro de version valide. Par exemple, `“2.0.0”`. | Correspond si la version du client est inférieure ou égale à la version spécifiée. | Le numéro de version est spécifié sous la forme d’une combinaison de nombres et de points (&quot;.&quot;) de toute longueur. |
| Fournisseur OEM | Chaîne fournisseur OEM pouvant être située dans le certificat d’exécution émis à un client qui a transporté le DRM Primetime sur un périphérique. | Correspondance exacte | Chaîne d&#39;identification du fournisseur OEM pour le périphérique utilisant le kit de portage. |
| Modèle | Chaîne de modèle qui peut se trouver dans le certificat d’exécution émis à un client qui a transporté le DRM Primetime sur un périphérique. Par exemple, `"iOS_Mobile", "Android_Mobile", "Chrome", "ChromeOS_ARM", "WindowsOnARM", "AVE"` | Correspondance exacte | Chaîne d&#39;identification du modèle de périphérique pour le périphérique utilisant le kit de portage. |

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Lorsque vous spécifiez une entrée dans la liste bloquée, vous pouvez définir des valeurs pour un ou plusieurs des attributs mentionnés dans le tableau précédent. Tout attribut non spécifié est traité comme un caractère générique. Si le client DRM Primetime correspond à toutes les valeurs spécifiées dans une entrée de liste bloquée, ce client peut ne pas accéder au contenu protégé.

