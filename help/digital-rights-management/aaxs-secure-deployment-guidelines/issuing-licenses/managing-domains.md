---
title: Gestion des domaines
description: Gestion des domaines
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# Gestion des domaines{#managing-domains}

Pour empêcher les utilisateurs de sauvegarder et de restaurer leurs fichiers afin de contourner le désenregistrement de domaine, il est recommandé de mettre en oeuvre l’une des approches suivantes pour la gestion des domaines :

* Limitez la durée de validité des informations d’identification de domaine. Les clients devront contacter le serveur de domaine pour acquérir à nouveau les informations d’identification de domaine lorsqu’elles arrivent à expiration. Le serveur de domaine peut alors s’assurer que la machine est toujours autorisée à être membre du domaine.
* Survolez les clés de domaine chaque fois qu’un utilisateur se désinscrit. Le serveur de licences ne doit émettre que des licences pour les clients disposant de la dernière clé de domaine. Cela suppose que le serveur de licences puisse se coordonner avec le serveur de domaine pour savoir quelle clé est la plus récente. Le fait de survoler les clés de domaine implique de générer une nouvelle paire de clés pour le domaine. Lorsque vous passez le curseur sur les clés d’un domaine particulier, veillez à incrémenter la version clé dans `generateDomainCredential`. Pour plus d’informations sur l’implémentation d’un roulement de clés, voir *RefImplDomainReqHandler* dans la mise en oeuvre de référence.
* Si le serveur de domaine est le même que le serveur de licences, le serveur peut utiliser le compteur de restauration pour détecter la sauvegarde et la restauration. Voir *Traitement des demandes d’accès aux Adobes *dans *Utilisation du SDK Adobe Access pour la protection du contenu.*
