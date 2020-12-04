---
seo-title: Mettre à jour la base de données d'implémentation de référence
title: Mettre à jour la base de données d'implémentation de référence
uuid: 2883045e-ad62-466d-94a2-fc45ded2a4f5
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---


# Mettre à jour la base de données d’implémentation de référence {#update-the-reference-implementation-db}

Pour contrôler les modèles d’utilisation sous lesquels une licence est délivrée à un utilisateur désigné, ajoutez des entrées à la base de données de mise en oeuvre de référence.

1. Ajoutez les entrées à la table `Customer`.

   Le tableau `Customer` contient les noms d’utilisateur et les mots de passe d’authentification des utilisateurs. Il indique également si un utilisateur dispose d’un abonnement (licence délivrée en vertu du modèle d’utilisation *Abonnement*).

1. Accordez à un utilisateur l’accès sous les modèles d’utilisation Téléchargement à soi ou Vidéo à la demande.

       Ajoutez les entrées de la table &quot;CustomerAuthorization&quot; pour spécifier :
   
   * Le modèle d’utilisation
   * Chaque segment de contenu auquel un utilisateur peut accéder

Pour plus d&#39;informations sur la façon de remplir chaque tableau, consultez le script [!DNL PopulateSampleDB.sql] (inclus dans votre DVD DRM Primetime dans le répertoire [!DNL Reference Implementation/Server/Reference Implementation Server/dbscript/]).
