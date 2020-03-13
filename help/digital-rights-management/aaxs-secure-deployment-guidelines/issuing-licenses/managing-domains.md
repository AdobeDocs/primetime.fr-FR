---
seo-title: Gestion des domaines
title: Gestion des domaines
uuid: aee02196-8704-46ee-add9-82b371722f0f
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Gestion des domaines{#managing-domains}

Pour empêcher les utilisateurs de sauvegarder et de restaurer leurs fichiers afin de contourner le désenregistrement des domaines, il est recommandé d’appliquer l’une des méthodes suivantes pour la gestion des domaines :

* Limitez la durée de validité des informations d’identification de domaine. Les clients devront contacter le serveur de domaine pour acquérir à nouveau les informations d’identification de domaine à leur expiration. Le serveur de domaine peut alors s’assurer que l’ordinateur est toujours autorisé à être membre du domaine.
* Survolez les clés de domaine chaque fois qu’un utilisateur se désenregistre. Le serveur de licences ne doit délivrer des licences qu’aux clients disposant de la dernière clé de domaine. Cela suppose que le serveur de licences peut coordonner son action avec le serveur de domaine pour savoir quelle clé est la plus récente. Le roulement sur les clés de domaine implique la génération d’une nouvelle paire de clés pour le domaine. Lorsque vous placez le pointeur de la souris sur les clés d’un domaine particulier, veillez à incrémenter la version clé dans `generateDomainCredential`. Pour plus d’informations sur l’implémentation d’un roulement de clé, voir *RefImplDomainReqHandler* dans l’implémentation des références.
* Si le serveur de domaine est le même que le serveur de licences, le serveur peut utiliser le compteur de restauration pour détecter la sauvegarde et la restauration. Voir *Traitement des demandes Adobe Access *dans *Utilisation du SDK Adobe Access pour la protection du contenu.*

