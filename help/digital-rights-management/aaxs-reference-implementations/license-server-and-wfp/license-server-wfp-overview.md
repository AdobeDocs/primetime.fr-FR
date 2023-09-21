---
title: Présentation du serveur de licences et du module de dossiers de contrôle
description: Présentation du serveur de licences et du module de dossiers de contrôle
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# Présentation du serveur de licences et du module de dossiers de contrôle {#license-server-and-watched-folder-packager-overview}

Le serveur de mise en oeuvre de référence peut vous aider à créer un serveur de licences à l’aide du SDK Adobe Access. Dans cette implémentation, les utilisateurs sont authentifiés en fonction des entrées d’utilisateurs dans une base de données. Le serveur comprend une logique commerciale de démonstration pour l’émission de licences. Il met également en oeuvre la prise en charge de la compatibilité pour Flash Media Rights Management Server 1.0 et 1.5.

Le serveur d’implémentation de référence comprend également une implémentation du dossier de contrôle du service de package. Ce composant peut être déployé avec le serveur de licences ou sur un ordinateur distinct. Avec cette mise en oeuvre de packager, plusieurs dossiers de contrôle peuvent être créés. Lorsque du contenu est déposé dans le dossier de contrôle, le programme de package le regroupe automatiquement.

Le serveur de licences et le gestionnaire de packages sont déployés sous la forme de fichiers WAR distincts. Vous pouvez donc choisir de les exécuter sur des serveurs distincts ou dans une seule instance Apache Tomcat®. Le serveur de licences se trouve dans la variable [!DNL flashaccess.war] et que le module est dans [!DNL flashaccess-packager.war]. Le paramètre facultatif [!DNL edcws.war] prend en charge les demandes de licence des clients FMRMS 1.x.

L’exemple de code de mise en oeuvre de référence présente les fonctionnalités suivantes :

* Serveur de licences :

   * Gestion des demandes d’authentification à l’aide d’une base de données pour valider le nom d’utilisateur/mot de passe
   * Traitement des demandes de licence et détermination du type de licence à émettre lors de l’utilisation du chaînage de licence.
   * Émission de licences pour le contenu contenant plusieurs stratégies
   * Émettez des licences qui prennent en charge la diffusion de clé à distance aux clients iOS (nécessite Adobe Primetime)
   * Émission de licences nécessitant une recherche/récupération externe de la clé de chiffrement de contenu (CEK)
   * Utilisation de la base de données pour déterminer si l’utilisateur est autorisé à afficher le contenu
   * Utilisation des listes de mise à jour de stratégie
   * Utilisation de listes de révocation automatique
   * Utilisation d’un fichier HSM ou PKCS12 pour stocker des informations d’identification
   * Chiffrement des mots de passe spécifiés dans le fichier de propriétés
   * Spécification de plusieurs informations d’identification de serveur de licences ou de transport (une fois les informations d’identification renouvelées, les anciennes informations d’identification sont conservées sur le serveur afin que le contenu existant puisse être consommé sans avoir à recompresser)
   * Limitation des versions DRM/Runtime autorisées à envoyer des requêtes au serveur de licences
   * Définition des préférences d’actualisation de l’horloge client
   * Limitation de l’écart de temps autorisé entre l’heure de la requête et l’heure du serveur (pour éviter les attaques de relecture)
   * Gestion des demandes des clients FMRMS 1.x (déclenche la mise à niveau du client FMRMS 1.x vers Adobe Access 2.0 ou version ultérieure)
   * Conversion des métadonnées FMRMS 1.x en métadonnées Adobe Accéder aux métadonnées à la volée, à l’aide des informations de licence FMRMS 1.x stockées dans une base de données
   * Exemple de code pour la conversion de stratégies FMRMS 1.x en stratégies d’accès Adobe
   * Exemples de scripts pour importer des informations de licence FMRMS 1.x depuis une base de données existante
   * Obtenir la version du serveur
   * Enregistrement de domaine
   * Désinscription de domaine
   * Demandes de synchronisation
   * Retour sur licence

* Packager Server :

   * Mise en oeuvre d’un module qui regroupe automatiquement le contenu ajouté à un dossier de contrôle
   * Utilisation d’un fichier HSM ou PKCS12 pour stocker des informations d’identification
   * Chiffrement des mots de passe spécifiés dans le fichier de propriétés
   * Configuration du service de package, création de stratégies et création de listes de mise à jour de stratégie à l’aide d’une application AIR
