---
description: Pour empêcher les utilisateurs de sauvegarder et de restaurer des fichiers pour contourner le désenregistrement de domaine, vous devez mettre en oeuvre certaines méthodes de gestion de domaine.
seo-description: Pour empêcher les utilisateurs de sauvegarder et de restaurer des fichiers pour contourner le désenregistrement de domaine, vous devez mettre en oeuvre certaines méthodes de gestion de domaine.
seo-title: Gestion des domaines
title: Gestion des domaines
uuid: 30b73e38-d6ed-43c6-89ba-ae8616383779
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---


# Gestion des domaines {#managing-domains}

Pour empêcher les utilisateurs de sauvegarder et de restaurer des fichiers pour contourner le désenregistrement de domaine, vous devez mettre en oeuvre certaines méthodes de gestion de domaine.

Voici quelques approches de gestion des domaines :

* Limitez la durée de validité des informations d’identification de domaine.

   Les clients doivent contacter le serveur de domaine pour réacquérir les informations d’identification de domaine à l’expiration de ces dernières. Le serveur de domaine peut alors vérifier que l&#39;ordinateur est toujours autorisé à être membre du domaine.
* Placez le pointeur de la souris sur les clés de domaine chaque fois qu’un utilisateur se désinscrit.

   Le serveur de licences ne doit délivrer que des licences aux clients disposant de la dernière clé de domaine. Cette approche suppose que le serveur de licences peut coordonner ses activités avec le serveur de domaines pour déterminer la clé la plus récente. Le roulement des clés de domaine implique la création d’une nouvelle paire de clés pour le domaine. Lorsque vous placez le pointeur de la souris sur les clés d&#39;un domaine, incrémentez la version de clé dans `generateDomainCredential`.
* Si le serveur de domaine est identique au serveur de licences, le serveur peut utiliser le compteur de restauration pour détecter une sauvegarde et une restauration.

   Pour plus d’informations, voir [Traitement des demandes Adobe Primetime DRM](../../protecting-content/implementing-the-license-server/processing-drm-requests.md).

