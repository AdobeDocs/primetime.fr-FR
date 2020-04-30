---
description: Le Gestionnaire de droits est le gestionnaire de fonctionnalités qui prend en charge l’implémentation de l’authentification Primetime.
seo-description: Le Gestionnaire de droits est le gestionnaire de fonctionnalités qui prend en charge l’implémentation de l’authentification Primetime.
seo-title: Présentation du Gestionnaire de droits
title: Présentation du Gestionnaire de droits
uuid: b33dfae3-a132-4215-9992-80cbf4c87a61
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Présentation du Gestionnaire de droits {#entitlement-manager-overview}

Le Gestionnaire de droits est le gestionnaire de fonctionnalités qui prend en charge l’implémentation de l’authentification Primetime.

## Présentation des fonctionnalités

L’intégration de l’authentification Primetime à l’implémentation de référence du SDK Primetime Android ajoute un nouveau gestionnaire de fonctionnalités à l’application. Cependant, contrairement à la plupart des autres gestionnaires de fonctionnalités, *le gestionnaire de droits est utilisé à plusieurs endroits dans l’application*. Vous trouverez ci-dessous un aperçu des modifications et ajouts apportés à l’implémentation de référence pour la prise en charge de l’authentification Primetime :

### EntitlementManager, classe

La `EntitlementManager` classe gère toutes les communications avec le SDK d&#39;authentification Primetime, plus encapsule la logique d&#39;application requise pour les workflows de droits. L&#39;API publique `EntitlementManager`de l&#39;application est utilisée par celle-ci pour lancer des workflows de droits, tandis que l&#39; `EntitlementMangerListener` interface fournit un mécanisme de rappel pour que l&#39;application puisse gérer `EntitlementManger` les événements.

### Rappels EntitlementManager

L’activité principale de l’implémentation de référence, la `CatalogActivity`, crée une instance de `EntitlementManagerListener` et l’enregistre dans le `EntitlementManager`. De cette façon, l’interface utilisateur `EntitlementManager` peut signaler les mises à jour nécessaires au reste de l’application. Les rappels incluent l’affichage/le masquage d’une boîte de dialogue de chargement, l’affichage de boîtes de dialogue d’état, la mise à jour des icônes d’autorisation et d’authentification et le démarrage de la lecture vidéo après une autorisation réussie.

### Boîte de dialogue Droits

La `EntitlementDialogFragment` classe génère des messages de dialogue en fonction de l&#39;état des droits transmis au constructeur de classe. Cette classe est utilisée pour les messages de réussite d&#39;authentification ainsi que pour tous les messages d&#39;erreur. La `CatalogActivity` boîte de dialogue des droits s&#39;affiche lorsqu&#39;elle reçoit des événements spécifiques du `EntitlementManager`. En outre, le `CatalogActivity` programme implémente l’ `EntitlementDialogListener` interface, qui comprend des méthodes de rappel pour signaler qu’une boîte de dialogue est fermée ou que l’utilisateur se déconnecte du service d’authentification Primetime.

### Sélection et connexion du fournisseur de contenu

Lors de l’authentification avec l’authentification Primetime, deux nouvelles activités, `MvpdPickerActivity` et `MvpdLoginActivity`permettent à l’utilisateur de sélectionner son fournisseur de contenu et de se connecter. Ces deux activités sont lancées depuis la `CatalogActivity` via le `EntitlementManager`. De plus, les résultats `MvpdPickerActivity` et `MvpdLoginActivity` retournés à la `CatalogActivity` méthode et donc à la `CatalogActivity` méthode doivent remplacer la `Activity.onActivityResult` .

### Bouton Se connecter

L’activité principale de l’implémentation de référence, la `CatalogActivity`, comprend un nouveau bouton &quot;Se connecter&quot; dans sa barre d’actions. Le bouton Se connecter permet à l’utilisateur de lancer une authentification avec l’authentification Primetime. De plus, l’utilisateur peut lancer l’authentification en sélectionnant une vidéo protégée pour la lecture. L’icône et le texte du bouton Se connecter changent en fonction de l’état d’authentification de l’utilisateur et le `CatalogActivity` contient le code permettant de mettre à jour l’icône et le texte du bouton lors de l’actualisation de la page. Pour ce faire, lorsque le `CatalogActivity` début se produit, il appelle `EntitlementManager.checkAuthentication()` pour mettre à jour l’état d’authentification de l’utilisateur.

### Droits du contenu

Au sein de la `CatalogView`, de nouvelles icônes s’affichent au-dessus de l’icône du contenu pour signaler l’état d’autorisation de l’utilisateur pour ce contenu. Par exemple, si l’utilisateur est préautorisé à vue d’une vidéo, une icône en forme de cercle vert s’affiche sur le contenu. Cependant, si l’utilisateur n’est pas préautorisé à vue de la vidéo, une icône de clé s’affiche. L’affichage de ces icônes est géré dans `ContentTileAdapter`, mais la mise à jour de leur état est initiée à partir du `CatalogActivity` moment où un rappel dans la `EntitlementManagerListener` est appelé.

### Lecture du contenu

La lecture vidéo nécessite désormais une vérification d’autorisation de la `EntitlementManager`part de l’utilisateur. L&#39;appel à `EntitlementManager.getAuthorization()` survient dans `CatalogView`. Si la vidéo nécessite une autorisation et que l’utilisateur est autorisé, la vidéo `PlayerActivity` est démarrée à partir de la `CatalogActivity`.

