---
description: 'null'
seo-description: 'null'
seo-title: A propos des implémentations de référence
title: A propos des implémentations de référence
uuid: f08fdb4b-aaa8-4871-bb62-1a21d5abdd8d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# A propos des implémentations de référence{#about-the-reference-implementations}

Ce guide décrit l’installation, la configuration et le fonctionnement des implémentations de référence DRM d’Adobe Primetime.

>[!NOTE]
>
>Primetime DRM s&#39;appelait auparavant Adobe Access et auparavant Flash Access.

Les implémentations de référence DRM Primetime comprennent les composants suivants :

* **Outils** de ligne de commande : ces outils sont basés sur le même code SDK DRM Primetime utilisé dans le serveur de licences DRM Primetime. Vous pouvez créer des packs, des licences et d’autres  DRM à partir de la ligne de commande et alterner facilement entre l’utilisation des outils de ligne de commande et le serveur de licences.
* **Serveur** de licences : serveur de licences entièrement fonctionnel et personnalisable (décrit ci-dessous comme l’une des options de votre serveur de licences).

**Options du serveur de licences :**

* **Implémentations** de référence DRM Primetime - L’objet de ce guide, cette implémentation de référence, est dotée d’un serveur de licences DRM robuste qui présente toutes les fonctionnalités fournies par le SDK DRM Primetime. Cette implémentation est fournie avec le code source et des instructions pour la création du code. Cette implémentation n’est pas destinée à être utilisée en l’état (bien qu’un [!DNL .war] fichier soit inclus que vous puissiez déployer rapidement). Il s’agit principalement d’une référence que vous pouvez utiliser pour créer votre propre serveur de licences personnalisé.

   Fonctionnalités du serveur de licences :

   * Gère les demandes d’authentification en utilisant une base de données pour valider le nom d’utilisateur/mot de passe.
   * Gère les demandes de licence et détermine le type de licence qui est émis lors de l’application du chaînage de licence.
   * Délivre des licences pour le contenu qui inclut plusieurs stratégies DRM Primetime.
   * Délivre des licences qui prennent en charge le de clés distantes pour les clients iOS, ce qui nécessite la gestion des droits numériques Primetime.
   * Délivre des licences qui nécessitent une recherche et une récupération externes de la clé de chiffrement de contenu (CEK).
   * Recherche une base de données afin de déterminer si un utilisateur est autorisé à  du contenu.
   * Recherche les  de mise à jour de la stratégie DRM Primetime.
   * Recherche le de révocation de l’ordinateur.
   * utilise un fichier HSM ou PKCS12 pour stocker les informations d’identification.
   * Chiffre les mots de passe que vous avez spécifiés dans un fichier de propriétés.
   * Spécifie plusieurs informations d’identification de serveur de licences ou de transport après le renouvellement des informations d’identification.

      Les anciennes informations d’identification sont conservées sur le serveur afin que les utilisateurs puissent continuer à du contenu existant sans avoir à recompresser.
   * Limite les versions DRM/Runtime autorisées à envoyer des requêtes à un serveur de licences.
   * Définit les préférences d’inversion de l’horloge client.
   * Limite la différence de temps autorisée entre le temps de requête et le temps du serveur pour empêcher les attaques de relecture.
   * Gère les requêtes des clients FMRMS 1.x

      Par exemple, le client FMRMS 1.x est déclenché pour effectuer la mise à niveau vers Primetime DRM 2.0 ou version ultérieure.
   * Convertit les métadonnées FMRMS 1.x en métadonnées DRM Primetime à la demande en utilisant les informations de licence FMRMS 1.x stockées dans une base de données.
   * permet de convertir des stratégies FMRMS 1.x en stratégies DRM Primetime pour un exemple de code.
   * Importe les informations de licence FMRMS 1.x d’une base de données existante pour les exemples de scripts.
   * Obtient la version du serveur
   * Enregistrement de domaine
   * Désenregistrement de domaine
   * Demandes de synchronisation
   * Retour de licence

* **Le serveur DRM Primetime pour la diffusion en flux continu** protégé - Il s’agit d’un binaire prêt à l’emploi que vous pouvez implémenter rapidement avec le moins d’efforts possible. Il s’agit d’une bonne option pour les clients qui souhaitent afficher rapidement le de Concept, ou *peut* être une option de production si vos besoins DRM personnalisés sont minimes. Pour plus d’informations, voir Informations connexes ci-dessous.

* **Service** DRM de Primetime Cloud - Il s’agit d’un serveur de licences hébergé par Adobe que vous pouvez utiliser pour la diffusion de licences. (Vous devez être titulaire de licence Primetime pour pouvoir utiliser ce service.) Ce service Adobe Cloud vous soulage des dépenses, de la maintenance et de l’ingénierie nécessaires à la création de votre propre service. Pour plus d’informations, voir Informations connexes ci-dessous.

