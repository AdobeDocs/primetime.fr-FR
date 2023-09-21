---
description: Pour empêcher les utilisateurs de sauvegarder et de restaurer des fichiers afin de contourner la désinscription de domaine, vous devez mettre en oeuvre certaines approches de gestion des domaines.
title: Gestion des domaines
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Gestion des domaines {#managing-domains}

Pour empêcher les utilisateurs de sauvegarder et de restaurer des fichiers afin de contourner la désinscription de domaine, vous devez mettre en oeuvre certaines approches de gestion des domaines.

Voici quelques approches de gestion des domaines :

* Limitez la durée de validité des informations d’identification de domaine.

  Les clients doivent contacter le serveur de domaine pour réacquérir les informations d’identification de domaine à l’expiration des informations d’identification. Le serveur de domaine peut alors vérifier que la machine est toujours autorisée à être membre du domaine.
* Faites défiler les clés de domaine chaque fois qu’un utilisateur se désinscrit.

  Le serveur de licences ne doit émettre que des licences pour les clients disposant de la dernière clé de domaine. Cette approche suppose que le serveur de licences peut se coordonner avec le serveur de domaine pour savoir quelle clé est la plus récente. Le fait de survoler les clés de domaine implique de générer une nouvelle paire de clés pour le domaine. Lorsque vous effectuez un roulement des clés d’un domaine, incrémentez la version clé dans `generateDomainCredential`.
* Si le serveur de domaine est le même que le serveur de licences, le serveur peut utiliser le compteur de restauration pour détecter une sauvegarde et restaurer.

  Pour plus d’informations, voir [Traitement des demandes Adobe Primetime DRM](../../protecting-content/implementing-the-license-server/processing-drm-requests.md).
