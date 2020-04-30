---
seo-title: Présentation du serveur de licences et du gestionnaire de dossiers de contrôle
title: Présentation du serveur de licences et du gestionnaire de dossiers de contrôle
uuid: 3dd6f699-a5c0-44c4-897a-34e06abe3d71
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Présentation du serveur de licences et du gestionnaire de dossiers de contrôle {#license-server-and-watched-folder-packager-overview}

Le serveur d’implémentation de référence peut vous aider à créer un serveur de licences à l’aide du SDK Adobe Access. Dans cette implémentation, les utilisateurs sont authentifiés en fonction des entrées d’utilisateur dans une base de données. Le serveur comprend une logique commerciale de démonstration pour l’octroi de licences. Il met également en oeuvre la prise en charge de la compatibilité pour Flash Media Rights Management Server 1.0 et 1.5.

Le serveur d’implémentation de référence inclut également une implémentation du dossier de contrôle du gestionnaire de packages. Ce composant peut être déployé avec le serveur de licences ou sur un ordinateur distinct. Avec cette mise en oeuvre de Packager, plusieurs dossiers de contrôle peuvent être créés. Lorsque du contenu est déposé dans le dossier de contrôle, l’outil de création de package empaquette automatiquement le contenu.

Le serveur de licences et le gestionnaire de package sont déployés en tant que fichiers WAR distincts, ce qui vous permet de choisir de les exécuter sur des serveurs distincts ou dans une seule instance Apache Tomcat®. Le serveur de licences se trouve dans le [!DNL flashaccess.war] et le gestionnaire de package est dans [!DNL flashaccess-packager.war]. L’option [!DNL edcws.war] contient la prise en charge des demandes de licence des clients FMRMS 1.x.

L’exemple de code de mise en oeuvre de référence présente les fonctionnalités suivantes :

* License Server :

   * Gestion des demandes d’authentification, utilisation d’une base de données pour valider le nom d’utilisateur/le mot de passe
   * Traitement des demandes de licence et détermination du type de licence à émettre lors de l’utilisation du chaînage de licence.
   * Délivrance de licences pour le contenu contenant plusieurs stratégies
   * Délivrer des licences prenant en charge la diffusion des clés distantes aux clients iOS (nécessite Adobe Primetime)
   * Délivrance de licences nécessitant une recherche/récupération externe de la clé de chiffrement de contenu (CEK)
   * Utilisation de la base de données pour déterminer si l’utilisateur est autorisé à vue du contenu
   * Utilisation des listes de mise à jour de stratégie
   * Utilisation de listes de révocation d’ordinateurs
   * Utilisation d’un fichier HSM ou PKCS12 pour stocker des informations d’identification
   * Chiffrement des mots de passe spécifiés dans le fichier de propriétés
   * Spécification de plusieurs informations d’identification de serveur de licences ou de transport (une fois les informations d’identification renouvelées, les anciennes informations d’identification sont conservées sur le serveur afin que le contenu existant puisse être consommé sans qu’il faille procéder à un reconditionnement)
   * Limitation des versions DRM/Runtime autorisées à envoyer des requêtes au serveur de licences
   * Définition des préférences d&#39;actualisation de l&#39;horloge client
   * Limitation de la différence de temps autorisée entre le temps de requête et le temps du serveur (pour éviter les attaques de relecture)
   * Gestion des requêtes des clients FMRMS 1.x (déclenche la mise à niveau du client FMRMS 1.x vers Adobe Access 2.0 ou version ultérieure)
   * Conversion instantanée des métadonnées FMRMS 1.x en métadonnées Adobe Access à l’aide des informations de licence FMRMS 1.x stockées dans une base de données
   * Exemple de code pour la conversion de stratégies FMRMS 1.x en stratégies Adobe Access
   * Exemples de scripts pour l’importation d’informations de licence FMRMS 1.x à partir d’une base de données existante
   * Obtenir la version du serveur
   * Enregistrement de domaine
   * Désinscription de domaine
   * Demandes de synchronisation
   * Retour de licence

* Serveur Packager :

   * Implémentation d’une implémentation de packager qui regroupe automatiquement le contenu ajouté à un dossier de contrôle
   * Utilisation d’un fichier HSM ou PKCS12 pour stocker des informations d’identification
   * Chiffrement des mots de passe spécifiés dans le fichier de propriétés
   * Configuration de Packager, création de stratégies et création de listes de mise à jour de stratégies à l’aide d’une application AIR

