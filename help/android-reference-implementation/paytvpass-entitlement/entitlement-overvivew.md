---
description: Le Gestionnaire de droits est le gestionnaire de fonctionnalités qui prend en charge l’implémentation de l’authentification Primetime.
seo-description: Le Gestionnaire de droits est le gestionnaire de fonctionnalités qui prend en charge l’implémentation de l’authentification Primetime.
seo-title: Présentation du Gestionnaire des droits
title: Présentation du Gestionnaire des droits
uuid: b33dfae3-a132-4215-9992-80cbf4c87a61
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Présentation du Gestionnaire des droits {#entitlement-manager-overview}

Le Gestionnaire de droits est le gestionnaire de fonctionnalités qui prend en charge l’implémentation de l’authentification Primetime.

## Présentation des fonctionnalités

L’intégration de l’authentification Primetime à l’implémentation de référence du SDK Primetime Android ajoute un nouveau gestionnaire de fonctionnalités à l’application. Cependant, contrairement à la plupart des autres gestionnaires de fonctionnalités, *le gestionnaire de droits est utilisé à plusieurs endroits dans l’application*. Vous trouverez ci-dessous un aperçu des modifications et des ajouts apportés à l’implémentation de référence pour la prise en charge de l’authentification Primetime :

### Classe EntitlementManager

La `EntitlementManager` classe gère toutes les communications avec le SDK d’authentification Primetime, plus encapsule la logique d’application requise pour le  de droits. L’API publique `EntitlementManager`de l’application est utilisée par celle-ci pour lancer des  de droits, tandis que l’ `EntitlementMangerListener` interface fournit un mécanisme de rappel pour que l’application gère les  `EntitlementManger` .

### Rappels EntitlementManager

Le principal  de l’implémentation de référence, le `CatalogActivity`, crée une instance de `EntitlementManagerListener` et l’enregistre dans le `EntitlementManager`. De cette manière, le `EntitlementManager` peut signaler les mises à jour nécessaires de l’interface utilisateur au reste de l’application. Les rappels comprennent l’affichage/le masquage d’une boîte de dialogue de chargement, l’affichage de boîtes de dialogue d’état, la mise à jour des icônes d’autorisation et d’authentification et le démarrage de la lecture vidéo après une autorisation réussie.

### Boîte de dialogue Droits

La `EntitlementDialogFragment` classe génère des messages de dialogue en fonction de l&#39;état des droits transmis au constructeur de classe. Cette classe est utilisée pour les messages de réussite d’authentification ainsi que pour tous les messages d’erreur. La `CatalogActivity` fenêtre affiche les boîtes de dialogue de droits lorsqu’elle reçoit des  spécifiques de la `EntitlementManager`. En outre, l’ `CatalogActivity` interface `EntitlementDialogListener` est implémentée, ce qui inclut des méthodes de rappel pour signaler la fermeture d’une boîte de dialogue ou la déconnexion du service d’authentification Primetime par l’utilisateur.

### Sélection et connexion du fournisseur de contenu

Lors de l’authentification avec l’authentification Primetime, deux nouveaux , `MvpdPickerActivity` et `MvpdLoginActivity`, permettent à l’utilisateur de sélectionner son fournisseur de contenu et de se connecter. Ces deux   sont démarrés à partir de la `CatalogActivity` via le `EntitlementManager`. De plus, les résultats `MvpdPickerActivity` et `MvpdLoginActivity` renvoient au `CatalogActivity` et, par conséquent, `CatalogActivity` doivent remplacer la `Activity.onActivityResult` méthode.

### Bouton Se connecter

Le principal  de l’implémentation de référence, le `CatalogActivity`, inclut un nouveau bouton &quot;Se connecter&quot; dans sa barre d’actions. Le bouton Se connecter permet à l’utilisateur de lancer l’authentification avec l’authentification Primetime. De plus, l’utilisateur peut lancer l’authentification en sélectionnant une vidéo protégée pour la lecture. L’icône et le texte du bouton Se connecter changent en fonction de l’état d’authentification de l’utilisateur et le `CatalogActivity` contient le code permettant de mettre à jour l’icône et le texte du bouton lors de l’actualisation de la page. Pour ce faire, lorsque le `CatalogActivity` , il appelle `EntitlementManager.checkAuthentication()` pour mettre à jour l’état d’authentification de l’utilisateur.

### Droits du contenu

Au sein de la `CatalogView`, de nouvelles icônes s’affichent au-dessus de l’icône du contenu pour signaler l’état d’autorisation de l’utilisateur pour ce contenu. Si, par exemple, l’utilisateur est préautorisé à d’une vidéo, une icône en forme de cercle vert s’affiche sur le contenu. Toutefois, si l’utilisateur n’est pas préautorisé à  la vidéo, une icône de clé s’affiche. L’affichage de ces icônes est géré dans `ContentTileAdapter`, mais la mise à jour de leur état est initiée à partir du `CatalogActivity` moment où un rappel dans le `EntitlementManagerListener` est appelé.

### Lecture de contenu

La lecture vidéo nécessite désormais une vérification d’autorisation de la part du `EntitlementManager`lecteur. L’appel à `EntitlementManager.getAuthorization()` se produit dans `CatalogView`. Si la vidéo nécessite une autorisation et que l’utilisateur est autorisé, la vidéo `PlayerActivity` est démarrée à partir de la `CatalogActivity`.

