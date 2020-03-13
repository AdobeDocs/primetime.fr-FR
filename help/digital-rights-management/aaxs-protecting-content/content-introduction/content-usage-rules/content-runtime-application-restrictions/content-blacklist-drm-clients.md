---
seo-title: noir des clients DRM restreint l’accès au contenu protégé
title: noir des clients DRM restreint l’accès au contenu protégé
uuid: c05aa6f8-32d9-42aa-a9c5-0d0629d49778
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# noir des clients DRM restreint l’accès au contenu protégé {#black-list-of-drm-clients-restricted-from-accessing-protected-content}

**Les versions des modules DRM d’Adobe Access ne peuvent pas accéder au contenu protégé.**

Spécifie le client DRM qui ne peut pas accéder au contenu. Spécifié par la version et la plate-forme du client DRM.

Exemple de cas d’utilisation : Dans le  d’une faille de sécurité, une nouvelle version du client DRM peut être spécifiée comme version minimale requise pour l’acquisition de licence et la lecture de contenu. Le serveur de licences vérifie que le client DRM qui émet la demande de licence satisfait aux exigences de version avant de délivrer une licence. Le client DRM vérifie également la version DRM dans la licence avant de lire le contenu. Cette vérification du client est requise dans le cas des domaines où une licence peut être transférée vers un autre ordinateur.

Une version client DRM peut être identifiée par les attributs spécifiés dans le tableau suivant :

| **Attribut** | **Valeurs prises en charge** | **Critères de correspondance** | **Description** |
|---|---|---|---|
|   | &quot;PC&quot;, &quot;PortingKit&quot; | Correspondance exacte | Indique si le client est exécuté sur un ordinateur de bureau ou sur un autre périphérique. |
| OS | &quot;Win&quot;, &quot;Mac&quot;, &quot;Linux&quot;, &quot;Android&quot;, &quot;iOS&quot;, &quot;ChromeOS&quot; | Correspondance exacte | Plateforme |
| Architecture | “32”, “64” | Correspondance exacte | 32 bits ou 64 bits |
| Type d’écran | &quot;PC&quot;, &quot;Mobile&quot;, &quot;TV&quot; | Correspondance exacte |  |
| Version d’exécution | Numéro de version valide. Par exemple, &quot;2.0.0&quot;, &quot;3.0&quot;, &quot;4.0&quot;, &quot;11.0&quot;, etc. | Correspond si la version du client est inférieure ou égale à la version spécifiée. | Le numéro de version est spécifié sous la forme d’une combinaison de nombres et de points (&quot;.&quot;) de n&#39;importe quelle longueur. |
| Version de la bibliothèque DRM | Numéro de version valide. Par exemple, &quot;2.0.0&quot;. | Correspond si la version du client est inférieure ou égale à la version spécifiée. | Le numéro de version est spécifié sous la forme d’une combinaison de nombres et de points (&quot;.&quot;) de n&#39;importe quelle longueur. |
| Fournisseur OEM | Chaîne fournisseur OEM | Correspondance exacte | Chaîne d&#39;identification du fournisseur OEM pour le périphérique utilisant le kit de portage. |
| Modèle | Chaîne du modèle. Par exemple, &quot;iOS_Mobile&quot;, &quot;Android_Mobile&quot;, &quot;Chrome&quot;, &quot;ChromeOS_ARM&quot;, &quot;WindowsOnARM&quot;, &quot;AVE&quot; | Correspondance exacte | Chaîne d&#39;identification du modèle de périphérique pour le périphérique utilisant le kit de portage. |

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Lors de la spécification d’une entrée dans la liste noire, des valeurs peuvent être définies pour un ou plusieurs des attributs mentionnés dans le tableau précédent. Tout attribut non spécifié est traité comme un caractère générique. Si le client DRM correspond à toutes les valeurs spécifiées dans une entrée de liste noire, ce client ne peut pas accéder au contenu protégé.

