---
title: Mise en œuvre d’une API sans client-codes/messages d’erreur avec raison probable/cause
description: Mise en œuvre d’une API sans client-codes/messages d’erreur avec raison probable/cause
exl-id: 616e35fc-9b72-422b-9a05-e6248bd52490
source-git-commit: 84a16ce775a0aab96ad954997c008b5265e69283
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# Mise en œuvre d’une API sans client-codes/messages d’erreur avec raison probable/cause {#clientless-api-implementation--error-codes-messages-with-probable-reason-cause}

>[!NOTE]
>
>Le contenu de cette page est fourni à titre d’information uniquement. L’utilisation de cette API nécessite une licence en cours de Adobe. Aucune utilisation non autorisée n’est autorisée.

</br>


## Erreur : non autorisé

### Causes:

1. En-tête d’autorisation manquant dans la POST
1. Problème avec l’en-tête d’autorisation-Vérifiez si la durée de la demande est exprimée en millisecondes.

## Erreur : SC 400 pendant l’authentification

### Causes:

1. Le serveur n’a pas trouvé le code d’enregistrement, qui a été créé pour un demandeur et un environnement spécifiques.
1. Vous pourriez être en cours d’exécution dans des problèmes de script inter-domaines.
1. Un spoof correct doit être ajouté au fichier/etc/hosts.

## Erreur : requête incorrecte 400

### Causes :

1. URL incorrecte pour POST/GET
1. SAMLAssertionParserException – l’assertion SAML cryptée n’a pas pu être décryptée à la fin de Adobe

## Erreur : 403 interdite

### Causes:

1. Un trop grand nombre de requêtes rapides, une fonctionnalité de la gestion des API permet d’empêcher les attaques par déni de service.
2. En cas d’utilisation de l’environnement prequalys, ajoutez l’usurpation, sinon Assurez-vous que l’usurpation a été supprimée du fichier/etc/hosts.

## Erreur : impossible de se connecter à la page MVPD

### Causes:

1. Le nom d’utilisateur et le mot de passe ne correspondent pas.
2. La connexion a peut-être été désactivée.
3. Vérifiez si la connexion est destinée à la production ou à l’évaluation


<!--

## Related Information

- [Clientless API Reference](/help/authentication/rest-api-reference.md)

-->
