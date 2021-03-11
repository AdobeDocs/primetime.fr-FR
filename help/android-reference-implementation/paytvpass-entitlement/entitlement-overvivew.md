---
description: Le Gestionnaire de droits est le gestionnaire de fonctionnalités qui prend en charge l’implémentation de l’authentification Primetime.
title: Présentation du Gestionnaire de droits
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---


# Présentation du Gestionnaire de droits {#entitlement-manager-overview}

Le Gestionnaire de droits est le gestionnaire de fonctionnalités qui prend en charge l’implémentation de l’authentification Primetime.

## Présentation des fonctionnalités

L’intégration de l’authentification Primetime à l’implémentation de référence du SDK Primetime Android ajoute un nouveau gestionnaire de fonctionnalités à l’application. Cependant, contrairement à la plupart des autres gestionnaires de fonctionnalités, *EntitlementManager est utilisé à plusieurs endroits dans l&#39;application*. Vous trouverez ci-dessous un aperçu des modifications et ajouts apportés à l’implémentation de référence pour la prise en charge de l’authentification Primetime :

### EntitlementManager, classe

La classe `EntitlementManager` gère toutes les communications avec le SDK d&#39;authentification Primetime, plus encapsule la logique d&#39;application requise pour les workflows de droits. L&#39;API publique de `EntitlementManager` est utilisée par l&#39;application pour lancer des workflows de droits, tandis que l&#39;interface `EntitlementMangerListener` fournit un mécanisme de rappel pour que l&#39;application puisse gérer les événements `EntitlementManger`.

### Rappels EntitlementManager

L&#39;activité principale de l&#39;implémentation de référence, la `CatalogActivity`, crée une instance de `EntitlementManagerListener` et l&#39;enregistre avec la `EntitlementManager`. De cette façon, `EntitlementManager` peut signaler les mises à jour nécessaires de l&#39;interface utilisateur au reste de l&#39;application. Les rappels incluent l’affichage/le masquage d’une boîte de dialogue de chargement, l’affichage de boîtes de dialogue d’état, la mise à jour des icônes d’autorisation et d’authentification et le démarrage de la lecture vidéo après une autorisation réussie.

### Boîte de dialogue Droits

La classe `EntitlementDialogFragment` génère des messages de boîte de dialogue en fonction de l&#39;état des droits transmis au constructeur de classe. Cette classe est utilisée pour les messages de réussite d&#39;authentification ainsi que pour tous les messages d&#39;erreur. `CatalogActivity` affiche les boîtes de dialogue de droits lorsqu&#39;il reçoit des événements spécifiques de `EntitlementManager`. En outre, `CatalogActivity` implémente l&#39;interface `EntitlementDialogListener`, qui inclut des méthodes de rappel pour signaler lorsqu&#39;une boîte de dialogue est fermée ou lorsque l&#39;utilisateur se déconnecte du service d&#39;authentification Primetime.

### Sélection et connexion du fournisseur de contenu

Lors de l’authentification avec l’authentification Primetime, deux nouvelles activités, `MvpdPickerActivity` et `MvpdLoginActivity`, permettent à l’utilisateur de sélectionner son fournisseur de contenu et de se connecter. Ces deux activités sont démarrées à partir de `CatalogActivity` par l&#39;intermédiaire de `EntitlementManager`. De plus, les résultats `MvpdPickerActivity` et `MvpdLoginActivity` renvoyés à `CatalogActivity` et, par conséquent, à `CatalogActivity` doivent remplacer la méthode `Activity.onActivityResult`.

### Bouton Se connecter

L&#39;activité principale de l&#39;implémentation de référence, `CatalogActivity`, comprend un nouveau bouton &quot;Se connecter&quot; dans sa barre d&#39;actions. Le bouton Se connecter permet à l’utilisateur de lancer une authentification avec l’authentification Primetime. De plus, l’utilisateur peut lancer l’authentification en sélectionnant une vidéo protégée pour la lecture. L’icône et le texte du bouton Se connecter changent en fonction de l’état d’authentification de l’utilisateur et `CatalogActivity` contient le code permettant de mettre à jour l’icône et le texte du bouton lors de l’actualisation de la page. Pour ce faire, lorsque le `CatalogActivity` début, il appelle `EntitlementManager.checkAuthentication()` pour mettre à jour l&#39;état d&#39;authentification de l&#39;utilisateur.

### Droits du contenu

Dans `CatalogView`, de nouvelles icônes s’affichent au-dessus de l’icône du contenu pour signaler l’état d’autorisation de l’utilisateur pour ce contenu. Par exemple, si l’utilisateur est préautorisé à vue d’une vidéo, une icône en forme de cercle vert s’affiche sur le contenu. Cependant, si l’utilisateur n’est pas préautorisé à vue de la vidéo, une icône de clé s’affiche. L&#39;affichage de ces icônes est géré dans `ContentTileAdapter`, mais la mise à jour de leur état est initiée à partir de `CatalogActivity` lorsqu&#39;un rappel dans `EntitlementManagerListener` est appelé.

### Lecture du contenu

La lecture vidéo nécessite désormais une vérification d’autorisation de la part de `EntitlementManager`. L&#39;appel à `EntitlementManager.getAuthorization()` se produit dans `CatalogView`. Si la vidéo nécessite une autorisation et que l&#39;utilisateur est autorisé, `PlayerActivity` est démarré à partir de `CatalogActivity`.

