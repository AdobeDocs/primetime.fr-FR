---
description: Le Gestionnaire de droits est le gestionnaire de fonctionnalités qui prend en charge la mise en oeuvre de l’authentification Primetime.
title: Présentation du Gestionnaire de droits
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# Présentation du Gestionnaire de droits {#entitlement-manager-overview}

Le Gestionnaire de droits est le gestionnaire de fonctionnalités qui prend en charge la mise en oeuvre de l’authentification Primetime.

## Présentation des fonctionnalités

L’intégration de l’authentification Primetime à l’implémentation de référence du SDK Primetime Android ajoute un nouveau gestionnaire de fonctionnalités à l’application. Cependant, contrairement à la plupart des autres gestionnaires de fonctionnalités, *EntitlementManager est utilisé à plusieurs endroits dans l’application.*. Vous trouverez ci-dessous un aperçu des modifications et des ajouts apportés à la mise en oeuvre de référence pour prendre en charge l’authentification Primetime :

### Classe EntitlementManager

La variable `EntitlementManager` gère toutes les communications avec le SDK d’authentification Primetime, ainsi que la logique d’application requise pour les processus de droits. La variable `EntitlementManager`L’API publique de est utilisée par l’application pour lancer des processus de droits, tandis que la variable `EntitlementMangerListener` L’interface fournit un mécanisme de rappel que l’application doit gérer. `EntitlementManger` événements .

### Rappels EntitlementManager

L’activité principale Mise en oeuvre de référence, la `CatalogActivity`, crée une instance de `EntitlementManagerListener` et l’enregistre auprès de la fonction `EntitlementManager`. Ainsi, la variable `EntitlementManager` peut signaler les mises à jour nécessaires de l’interface utilisateur au reste de l’application. Les rappels incluent l’affichage/le masquage d’une boîte de dialogue de chargement, l’affichage de boîtes de dialogue d’état, la mise à jour des icônes d’autorisation et d’authentification, ainsi que le démarrage de la lecture vidéo lors d’une autorisation réussie.

### Boîtes de dialogue de droits

La variable `EntitlementDialogFragment` génère des messages de boîte de dialogue en fonction de l’état des droits transmis au constructeur de classe. Cette classe est utilisée pour les messages de succès d’authentification, ainsi que pour tous les messages d’erreur. La variable `CatalogActivity` affiche les boîtes de dialogue des droits lorsqu’il reçoit des événements spécifiques de la `EntitlementManager`. En outre, la variable `CatalogActivity` met en oeuvre `EntitlementDialogListener` qui inclut des méthodes de rappel pour signaler qu’une boîte de dialogue est fermée ou que l’utilisateur se déconnecte du service d’authentification Primetime.

### Sélection et connexion du fournisseur de contenu

Lors de l’authentification avec l’authentification Primetime, deux nouvelles activités, `MvpdPickerActivity` et `MvpdLoginActivity`, permettent à l’utilisateur de sélectionner son fournisseur de contenu et de se connecter. Ces deux activités sont lancées à partir du `CatalogActivity` via le `EntitlementManager`. En outre, les deux `MvpdPickerActivity` et `MvpdLoginActivity` renvoyer les résultats à la variable `CatalogActivity` et par conséquent, `CatalogActivity` doit remplacer la variable `Activity.onActivityResult` .

### Bouton Se connecter

L’activité principale Mise en oeuvre de référence, la `CatalogActivity`, inclut un nouveau bouton &quot;Se connecter&quot; dans sa barre d’actions. Le bouton Se connecter permet à l’utilisateur de lancer l’authentification avec l’authentification Primetime. En outre, l’utilisateur peut lancer l’authentification en sélectionnant une vidéo protégée pour la lecture. L’icône et le texte du bouton Se connecter changent en fonction de l’état d’authentification de l’utilisateur et du `CatalogActivity` contient le code permettant de mettre à jour l’icône et le texte du bouton lors de l’actualisation de la page. Pour ce faire, lorsque la variable `CatalogActivity` démarre, appelle `EntitlementManager.checkAuthentication()` pour mettre à jour l’état d’authentification de l’utilisateur.

### Droit relatif au contenu

Dans le `CatalogView`, de nouvelles icônes s’affichent au-dessus de l’icône du contenu pour signaler l’état d’autorisation de l’utilisateur pour ce contenu. Par exemple, si l’utilisateur est préautorisé à visionner une vidéo, une icône en forme de cercle vert s’affiche au-dessus du contenu. Cependant, si l’utilisateur n’est pas autorisé à visionner la vidéo, une icône de clé s’affiche. L’affichage de ces icônes est géré dans la section `ContentTileAdapter`, toutefois, la mise à jour de leur état est lancée à partir de la fonction `CatalogActivity` lorsqu’un rappel dans la variable `EntitlementManagerListener` est appelée.

### Lecture du contenu

La lecture vidéo nécessite désormais une vérification d’autorisation de la part de `EntitlementManager`. L’appel à `EntitlementManager.getAuthorization()` se produit dans `CatalogView`. Si la vidéo nécessite une autorisation et que l’utilisateur est autorisé, la variable `PlayerActivity` est démarré à partir de la fonction `CatalogActivity`.
