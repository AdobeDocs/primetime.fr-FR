---
seo-title: Mise à jour de la base de données d’implémentation de référence
title: Mise à jour de la base de données d’implémentation de référence
uuid: 2883045e-ad62-466d-94a2-fc45ded2a4f5
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Mise à jour de la base de données d’implémentation de référence{#update-the-reference-implementation-db}

Pour contrôler les modèles d’utilisation sous lesquels une licence est délivrée à un utilisateur désigné, ajoutez des entrées à la base de données de mise en oeuvre de référence.

1. Ajouter les entrées dans la `Customer` table.

   Le `Customer` tableau comprend les noms d’utilisateur et les mots de passe pour authentifier les utilisateurs. Il indique également si un utilisateur dispose d’un   (une licence délivrée selon le modèle d’utilisation du ** ).

1. Accordez à un utilisateur l’accès sous les modèles d’utilisation Téléchargement à la propriété ou Vidéo à la demande.

       Ajouter les entrées de la table &quot;CustomerAuthorization&quot; pour spécifier:
   
   * Le modèle d’utilisation
   * Chaque segment de contenu auquel un utilisateur peut accéder

Pour plus d’informations sur la façon de remplir chaque tableau, voir le [!DNL PopulateSampleDB.sql] script (inclus dans votre DVD DRM Primetime dans le [!DNL Reference Implementation/Server/Reference Implementation Server/dbscript/] répertoire).
