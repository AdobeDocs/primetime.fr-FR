---
seo-title: Gestion des domaines
title: Gestion des domaines
uuid: aee02196-8704-46ee-add9-82b371722f0f
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---


# Gestion des domaines{#managing-domains}

Pour empêcher les utilisateurs de sauvegarder et de restaurer leurs fichiers afin de contourner le désenregistrement des domaines, il est recommandé de mettre en oeuvre l’une des méthodes suivantes pour la gestion des domaines :

* Limitez la durée de validité des informations d’identification de domaine. Les clients devront contacter le serveur de domaine pour réacquérir les informations d’identification de domaine à leur expiration. Le serveur de domaine peut alors s&#39;assurer que l&#39;ordinateur est toujours autorisé à être membre du domaine.
* Survolez les clés de domaine chaque fois qu’un utilisateur désenregistre. Le serveur de licences ne doit délivrer que des licences aux clients disposant de la dernière clé de domaine. Cela suppose que le serveur de licences peut coordonner ses activités avec le serveur de domaines pour savoir quelle clé est la plus récente. Le roulement des clés de domaine implique la création d’une nouvelle paire de clés pour le domaine. Lorsque vous placez le pointeur de la souris sur les clés d&#39;un domaine particulier, veillez à incrémenter la version de clé dans `generateDomainCredential`. Pour plus d&#39;informations sur l&#39;implémentation d&#39;un roulement de clés, voir *RefImplDomainReqHandler* dans la section Mise en oeuvre des références.
* Si le serveur de domaine est identique au serveur de licences, le serveur peut utiliser le compteur de restauration pour détecter la sauvegarde et la restauration. Voir *Traitement des demandes d’accès aux Adobes *dans *Utilisation du SDK d’accès aux Adobes pour la protection du contenu.*

