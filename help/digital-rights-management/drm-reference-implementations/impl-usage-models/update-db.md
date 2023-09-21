---
title: Mise à jour de la base de données d’implémentation de référence
description: Mise à jour de la base de données d’implémentation de référence
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Mise à jour de la base de données d’implémentation de référence{#update-the-reference-implementation-db}

Pour contrôler les modèles d’utilisation sous lesquels une licence est émise à un utilisateur désigné, ajoutez des entrées à la base de données de mise en oeuvre de référence.

1. Ajoutez des entrées au `Customer` table.

   La variable `Customer` comprend les noms d’utilisateur et les mots de passe pour authentifier les utilisateurs. Elle indique également si un utilisateur a un abonnement (une licence émise sous la propriété *Abonnement* modèle d’utilisation).

1. Accordez à un utilisateur l’accès sous les modèles d’utilisation Téléchargement vers soi ou Vidéo à la demande.

       Ajoutez des entrées à la table &quot;CustomerAuthorization&quot; pour spécifier :
   
   * Le modèle d’utilisation
   * Chaque segment de contenu auquel un utilisateur peut accéder

Pour plus d’informations sur la façon de renseigner chaque tableau, voir la section [!DNL PopulateSampleDB.sql] script (inclus dans votre DVD DRM Primetime dans la variable [!DNL Reference Implementation/Server/Reference Implementation Server/dbscript/] ).
