---
description: Pour empêcher les utilisateurs de sauvegarder et de restaurer des fichiers pour contourner le désenregistrement de domaine, vous devez mettre en oeuvre certaines méthodes de gestion de domaine.
seo-description: Pour empêcher les utilisateurs de sauvegarder et de restaurer des fichiers pour contourner le désenregistrement de domaine, vous devez mettre en oeuvre certaines méthodes de gestion de domaine.
seo-title: Gestion des domaines
title: Gestion des domaines
uuid: 30b73e38-d6ed-43c6-89ba-ae8616383779
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Gestion des domaines {#managing-domains}

Pour empêcher les utilisateurs de sauvegarder et de restaurer des fichiers pour contourner le désenregistrement de domaine, vous devez mettre en oeuvre certaines méthodes de gestion de domaine.

Voici quelques approches de gestion des domaines :

* Limitez la durée de validité des informations d’identification de domaine.

   Les clients doivent contacter le serveur de domaine pour récupérer les informations d’identification de domaine à l’expiration de ces informations. Le serveur de domaine peut alors vérifier que l’ordinateur est toujours autorisé à être membre du domaine.
* Passez la souris sur les clés de domaine chaque fois qu’un utilisateur se désinscrit.

   Le serveur de licences ne doit délivrer des licences qu’aux clients disposant de la dernière clé de domaine. Cette approche suppose que le serveur de licences peut coordonner son action avec le serveur de domaine pour savoir quelle clé est la plus récente. Le roulement sur les clés de domaine implique la génération d’une nouvelle paire de clés pour le domaine. Lorsque vous placez le pointeur de la souris sur les clés d’un domaine, incrémentez la version clé dans `generateDomainCredential`.
* Si le serveur de domaine est le même que le serveur de licences, le serveur peut utiliser le compteur de restauration pour détecter une sauvegarde et une restauration.

   Pour plus d’informations, voir [Traitement des demandes](../../protecting-content/implementing-the-license-server/processing-drm-requests.md)DRM Adobe Primetime.

