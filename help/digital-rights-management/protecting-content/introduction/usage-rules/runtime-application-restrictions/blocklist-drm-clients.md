---
title: Liste bloquée des clients DRM limitée à l’accès au contenu protégé
description: Liste bloquée des clients DRM limitée à l’accès au contenu protégé
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Liste bloquée des clients DRM limitée à l’accès au contenu protégé {#blocklist-of-drm-clients-restricted-from-accessing-protected-content}

Cette liste bloquée spécifie les clients DRM Primetime qui ne peuvent pas accéder au contenu protégé. Vous liste bloquée des clients par version client et plateforme.

Exemple de cas d’utilisation : en cas de violation de sécurité, une version plus récente du client DRM Primetime peut être spécifiée comme version minimale requise pour l’acquisition de licence et la lecture de contenu. Le serveur de licences vérifie que le client DRM Primetime qui émet la demande de licence satisfait aux exigences de version avant de délivrer une licence. Le client DRM Primetime vérifie également la version de la licence avant de lire le contenu. Ce contrôle client est requis dans le cas de domaines où une licence peut être transférée à un autre ordinateur.

Une version client DRM Primetime peut être identifiée par les attributs spécifiés dans le tableau suivant :

| **Attribut** | **Valeurs prises en charge** | **Critères de correspondance** | **Description** |
|---|---|---|---|
| Environnement | `“PC”, “PortingKit”` | Correspondance exacte | Indique si le client s’exécute sur un bureau ou sur un autre appareil. |
| SE | `“Win”, “Mac”, “Linux”, “Android”, “iOS”, "ChromeOS"` | Correspondance exacte | Plateforme |
| Architecture | `“32”, “64”` | Correspondance exacte | 32 bits ou 64 bits |
| Type d’écran | `“PC”, “Mobile”, “TV”` | Correspondance exacte | |
| Version d’exécution | Numéro de version valide. Par exemple, `“2.0.0”, "3.0", "4.0", "11.0"`, etc. | Correspond si la version du client est inférieure ou égale à la version spécifiée. | Le numéro de version est spécifié sous la forme d’une combinaison de nombres et de points (&quot;.&quot;) de n’importe quelle longueur. |
| Version de la bibliothèque DRM Primetime | Numéro de version valide. Par exemple, `“2.0.0”`. | Correspond si la version du client est inférieure ou égale à la version spécifiée. | Le numéro de version est spécifié sous la forme d’une combinaison de nombres et de points (&quot;.&quot;) de n’importe quelle longueur. |
| Fournisseur OEM | Chaîne du fournisseur OEM qui peut se trouver dans le certificat d’exécution émis à un client qui transportait le DRM Primetime sur un appareil. | Correspondance exacte | Chaîne d’identification du fournisseur OEM pour l’appareil à l’aide du kit de portage. |
| Modèle | Chaîne de modèle pouvant se trouver dans le certificat d’exécution émis à un client qui transportait Primetime DRM sur un appareil. Par exemple : `"iOS_Mobile", "Android_Mobile", "Chrome", "ChromeOS_ARM", "WindowsOnARM", "AVE"` | Correspondance exacte | Chaîne d’identification du modèle de périphérique pour l’appareil à l’aide du kit de portage. |

>[!NOTE]
>
>Lors de la spécification d’une entrée dans la liste bloquée, vous pouvez définir des valeurs pour un ou plusieurs des attributs mentionnés dans le tableau précédent. Tout attribut non spécifié est traité comme un caractère générique. Si le client DRM Primetime correspond à toutes les valeurs spécifiées dans une entrée de liste bloquée, ce client peut ne pas accéder au contenu protégé.
