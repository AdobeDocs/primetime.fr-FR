---
title: Mise en oeuvre de l’API sans client - Codes d’erreur/messages avec une raison/cause probable
description: Mise en oeuvre de l’API sans client - Codes d’erreur/messages avec une raison/cause probable
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---


# Mise en oeuvre de l’API sans client - Codes d’erreur/messages avec une raison/cause probable {#clientless-api-implementation--error-codes-messages-with-probable-reason-cause}

>[!NOTE]
>
>Le contenu de cette page est fourni à titre d’information uniquement. L’utilisation de cette API nécessite une licence actuelle de Adobe. Aucune utilisation non autorisée n’est autorisée.

</br>


## Erreur : Non autorisé

### Causes :

1. En-tête d’autorisation manquant dans le POST
1. Problème avec l’en-tête d’autorisation : vérifiez si le temps de requête est en millisecondes.

## Erreur : SC 400 lors de l’authentification

### Causes :

1. Le serveur n’a pas trouvé le code d’enregistrement, qui a été créé pour un demandeur et un environnement spécifiques.
1. Vous pouvez rencontrer des problèmes de script interdomaines.
1. Ajout d’un usurpation correct au fichier /etc/hosts

## Erreur : 400 Bad Request

### Causes :

1. URL incorrecte pour POST/GET
1. SAMLAsertionParserException - L’assertion SAML chiffrée n’a pas pu être décryptée à la fin de l’Adobe.

## Erreur : 403 interdit

### Causes :

1. Trop de demandes rapides : une fonctionnalité de gestion des API pour empêcher les attaques par déni de service (DoS).
2. Si vous utilisez un environnement précédent, ajoutez une mise en file d’attente, sinon assurez-vous que la mise en file d’attente a été supprimée du fichier /etc/hosts.

## Erreur : Impossible de se connecter à la page MVPD

### Causes :

1. Le nom d’utilisateur et le mot de passe ne correspondent pas. 
2. La connexion a peut-être été désactivée
3. Vérifiez si la connexion est destinée à la production ou à l’évaluation.


<!--

## Related Information

- [Clientless API Reference](/help/authentication/rest-api-reference.md)

-->