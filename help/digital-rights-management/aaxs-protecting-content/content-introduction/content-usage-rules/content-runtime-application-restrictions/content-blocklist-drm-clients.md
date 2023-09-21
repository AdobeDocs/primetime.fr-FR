---
title: Liste bloquée des clients DRM limitée à l’accès au contenu protégé
description: Liste bloquée des clients DRM limitée à l’accès au contenu protégé
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Liste bloquée des clients DRM limitée à l’accès au contenu protégé {#blocklist-of-drm-clients-restricted-from-accessing-protected-content}

**Adobe Accès aux versions du module DRM restreint l’accès au contenu protégé.**

Indique le client DRM qui ne peut pas accéder au contenu. Spécifié par la version du client DRM et la plateforme.

Exemple de cas d’utilisation : en cas de violation de sécurité, une version plus récente du client DRM peut être spécifiée comme version minimale requise pour l’acquisition de licence et la lecture de contenu. Le serveur de licences vérifie que le client DRM qui émet la demande de licence satisfait aux exigences de version avant de délivrer une licence. Le client DRM vérifie également la version DRM dans la licence avant de lire le contenu. Ce contrôle client est requis dans le cas de domaines où une licence peut être transférée à un autre ordinateur.

Une version client DRM peut être identifiée par les attributs spécifiés dans le tableau suivant :

| **Attribut** | **Valeurs prises en charge** | **Critères de correspondance** | **Description** |
|---|---|---|---|
| Environnement | &quot;PC&quot;, &quot;PortingKit&quot; | Correspondance exacte | Indique si le client s’exécute sur un bureau ou sur un autre appareil. |
| SE | &quot;Win&quot;, &quot;Mac&quot;, &quot;Linux&quot;, &quot;Android&quot;, &quot;iOS&quot;, &quot;ChromeOS&quot; | Correspondance exacte | Plateforme |
| Architecture | “32”, “64” | Correspondance exacte | 32 bits ou 64 bits |
| Type d’écran | &quot;PC&quot;, &quot;Mobile&quot;, &quot;TV&quot; | Correspondance exacte | |
| Version d’exécution | Numéro de version valide. Par exemple, &quot;2.0.0&quot;, &quot;3.0&quot;, &quot;4.0&quot;, &quot;11.0&quot;, etc. | Correspond si la version du client est inférieure ou égale à la version spécifiée. | Le numéro de version est spécifié sous la forme d’une combinaison de nombres et de points (&quot;.&quot;) de n’importe quelle longueur. |
| Version de la bibliothèque DRM | Numéro de version valide. Par exemple, &quot;2.0.0&quot;. | Correspond si la version du client est inférieure ou égale à la version spécifiée. | Le numéro de version est spécifié sous la forme d’une combinaison de nombres et de points (&quot;.&quot;) de n’importe quelle longueur. |
| Fournisseur OEM | Chaîne du fournisseur OEM | Correspondance exacte | Chaîne d’identification du fournisseur OEM pour l’appareil à l’aide du kit de portage. |
| Modèle | Chaîne de modèle. Par exemple, &quot;iOS_Mobile&quot;, &quot;Android_Mobile&quot;, &quot;Chrome&quot;, &quot;Chrome&quot;, &quot;Chrome OS_ARM&quot;, &quot;WindowsOnARM&quot;, &quot;AVE&quot;. | Correspondance exacte | Chaîne d’identification du modèle de périphérique pour l’appareil à l’aide du kit de portage. |

>[!NOTE]
>
>Lors de la spécification d’une entrée dans la liste bloquée, des valeurs peuvent être définies pour un ou plusieurs des attributs mentionnés dans le tableau précédent. Tout attribut non spécifié est traité comme un caractère générique. Si le client DRM correspond à toutes les valeurs spécifiées dans une entrée de liste bloquée, ce client ne peut pas accéder au contenu protégé.
