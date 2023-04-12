---
title: Chemin de mise à niveau d’AccessEnabler iOS/tvOS 3.7.0
description: Chemin de mise à niveau d’AccessEnabler iOS/tvOS 3.7.0
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---


# Chemin de mise à niveau d’AccessEnabler iOS/tvOS 3.7.0 {#accessenabler-iostvos-370-upgrade-path}

>[!NOTE]
>
>Le contenu de cette page est fourni à titre d’information uniquement. L’utilisation de cette API nécessite une licence actuelle de Adobe. Aucune utilisation non autorisée n’est autorisée.

</br>

Modifications du stockage du trousseau à partir de [new AccessEnabler version 3.7.0](/help/authentication/authn-rn-ios-tvos-370.md) sont incompatibles avec l’implémentation du stockage Keychain de la version d’AccessEnabler inférieure à 3.7.0.

Le chemin de mise à niveau d’une application adoptant la nouvelle version 3.7.0 d’AccessEnabler migre tous les jetons de la ou des versions précédentes de l’espace de stockage Keychain. Par conséquent, les utilisateurs finaux **ne doit pas entraîner de perte des sessions d’authentification/d’autorisation** lors du processus de mise à jour de la structure AccessEnabler.

## Limites connues

Certaines limitations, décrites ci-dessous, peuvent être rencontrées par les implémenteurs.


1. L’authentification unique régulière (par Adobe) ne fonctionnera pas entre une application utilisant AccessEnabler version 3.7.0 et une application utilisant AccessEnabler version(s) inférieure(s) à 3.7.0, même pour les applications développées par le même fournisseur.

   - **Important :**
      - La connexion unique au niveau du système (Apple) ne sera pas affectée.
      - La connexion unique régulière (par Adobe) continuera à fonctionner si les deux applications sont développées par le même fournisseur et utilisent la ou les versions d’AccessEnabler antérieures à la version 3.7.0 !
      - La connexion unique (par Adobe) régulière fonctionnera si les deux applications sont développées par le même fournisseur et utilisent AccessEnabler version 3.7.0 !

1. Dans le cas de la mise à niveau d&#39;une application utilisant la version 3.7.0 d&#39;AccessEnabler vers une version inférieure d&#39;AccessEnabler, les nouveaux jetons générés ne seront pas migrés. Par conséquent, les utilisateurs finaux risquent de subir la perte des sessions d’authentification/d’autorisation, sans s’y attendre.

   - **Important :**
      - Les utilisateurs finaux authentifiés par le biais de la connexion unique au niveau du système (Apple) ne seront pas affectés.
      - Les utilisateurs finaux qui étaient déjà authentifiés avant la mise à jour vers la nouvelle application à l’aide de la version 3.7.0 d’AccessEnabler ne seront pas affectés.

1. Dans le cas de la mise à niveau d&#39;une application utilisant la version 3.7.0 d&#39;AccessEnabler vers une version inférieure d&#39;AccessEnabler, les jetons supprimés ne seront pas reconnus. Par conséquent, les utilisateurs finaux peuvent rencontrer la présence de sessions d’authentification/d’autorisation, sans s’y attendre.
