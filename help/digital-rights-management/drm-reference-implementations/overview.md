---
title: À propos des implémentations de référence
description: À propos des implémentations de référence
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---

# À propos des implémentations de référence{#about-the-reference-implementations}

Ce guide décrit l’installation, la configuration et le fonctionnement des mises en oeuvre de référence DRM Adobe Primetime.

>[!NOTE]
>
>Primetime DRM s&#39;appelait auparavant Accès aux Adobes, et avant cela, Flash Access.

Les implémentations de référence DRM Primetime incluent les composants suivants :

* **Outils de ligne de commande** - Ces outils sont basés sur le même code SDK DRM Primetime utilisé dans le serveur de licences DRM Primetime. Vous pouvez effectuer des tâches de package, de licences et autres tâches DRM à partir de la ligne de commande, et alterner facilement entre l’utilisation des outils de ligne de commande et le serveur de licences.
* **Serveur de licences** - Un serveur de licences entièrement fonctionnel et personnalisable (décrit ci-dessous comme l’une des options de votre serveur de licences).

**Options du serveur de licences :**

* **Mises en oeuvre de référence DRM Primetime** - Objet de ce guide, cette mise en oeuvre de référence comprend un serveur de licences DRM robuste qui présente toutes les fonctionnalités fournies par le SDK DRM Primetime. Cette implémentation est fournie avec le code source et des instructions pour la création du code. Cette implémentation n’est pas destinée à être utilisée telle quelle (bien qu’une [!DNL .war] est inclus et vous pouvez le déployer rapidement). Il s’agit principalement d’une référence que vous pouvez utiliser pour créer votre propre serveur de licences personnalisées.

  Fonctionnalités du serveur de licences :

   * Gère les demandes d’authentification à l’aide d’une base de données pour valider le nom d’utilisateur/mot de passe.
   * Gère les demandes de licence et détermine le type de licence qui est émis lorsque le chaînage de licence est appliqué.
   * Envoie des licences pour le contenu qui comprend plusieurs stratégies DRM Primetime.
   * Envoie des licences qui prennent en charge la diffusion de clé à distance aux clients iOS, ce qui nécessite Primetime DRM.
   * Envoie des licences qui nécessitent une recherche et une récupération externes de la clé de chiffrement de contenu (CEK).
   * Recherche une base de données afin de déterminer si un utilisateur est autorisé à afficher le contenu.
   * Recherche les listes de mise à jour de stratégie DRM Primetime.
   * Recherche les listes de révocation des ordinateurs.
   * Utilise un fichier HSM ou PKCS12 pour stocker les informations d’identification.
   * Chiffre les mots de passe que vous avez spécifiés dans un fichier de propriétés.
   * Indique plusieurs informations d’identification de serveur de licences ou de transport une fois les informations d’identification renouvelées.

     Les anciennes informations d’identification sont conservées sur le serveur afin que les utilisateurs puissent continuer à afficher le contenu existant sans avoir à effectuer un nouveau package.
   * Limite les versions DRM/Runtime autorisées à envoyer des requêtes à un serveur de licences.
   * Définit les préférences de la fenêtre rétroactive de l’horloge client.
   * Limite la différence de temps autorisée entre l’heure de la requête et l’heure du serveur pour empêcher les attaques de relecture.
   * Gère les demandes des clients FMRMS 1.x

     Par exemple, le client FMRMS 1.x est déclenché pour effectuer la mise à niveau vers Primetime DRM 2.0 ou version ultérieure.
   * Convertit les métadonnées FMRMS 1.x en métadonnées DRM Primetime à la demande à l’aide des informations de licence FMRMS 1.x stockées dans une base de données.
   * Convertit les stratégies FMRMS 1.x en stratégies Primetime DRM pour l’exemple de code.
   * Importe les informations de licence FMRMS 1.x d’une base de données existante pour les exemples de scripts.
   * Obtient la version du serveur
   * Enregistrement de domaine
   * Désinscription de domaine
   * Demandes de synchronisation
   * Retour sur licence

* **Le serveur DRM Primetime pour la diffusion en continu protégée** - Il s’agit d’un binaire prêt à l’emploi que vous pouvez mettre en oeuvre rapidement avec un effort minimal. Il s’agit d’une bonne option pour les clients qui souhaitent afficher rapidement un Bon à tirer du concept, ou *can* être une option de production si vos besoins DRM personnalisés sont minimes. Pour plus d’informations, voir Informations connexes ci-dessous.

* **Le service DRM Primetime Cloud** - Il s’agit d’un serveur de licences hébergé par Adobe que vous pouvez utiliser pour le service de licences. (Vous devez être un concessionnaire Primetime pour utiliser ce service.) Ce service cloud Adobe vous soulage des dépenses, de la maintenance et de l’ingénierie nécessaires à la création de votre propre service. Pour plus d’informations, voir Informations connexes ci-dessous.
