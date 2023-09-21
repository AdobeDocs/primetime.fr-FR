---
title: Révocation des informations d’identification de l’ordinateur
description: Révocation des informations d’identification de l’ordinateur
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# Révocation des informations d’identification de l’ordinateur{#revoking-machine-credentials}

Adobe conserve une liste CRL pour la révocation des informations d’identification de la machine qui sont connues pour être compromises. Cette CRL est automatiquement appliquée par le SDK. S’il existe d’autres machines auxquelles vous ne souhaitez pas que votre serveur de licences octroie des licences, vous pouvez créer une liste de révocation de l’ordinateur et ajouter le nom de l’émetteur et le numéro de série des jetons de la machine à exclure (utilisez `MachineToken.getMachineTokenId()` pour récupérer le nom de l’émetteur et le numéro de série du certificat de la machine).

La révocation des informations d’identification de l’ordinateur implique l’utilisation d’un `RevocationListFactory` . Pour créer une liste de révocation, chargez une liste de révocation existante et vérifiez si un jeton de machine a été révoqué à l’aide de l’API Java, procédez comme suit :

1. Configurez votre environnement de développement et incluez tous les fichiers JAR mentionnés dans [Configuration de l’environnement de développement](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md) dans votre projet.
1. Créez un `ServerCredentialFactory` pour charger les informations d’identification nécessaires à la signature. Les informations d’identification du serveur de licences sont utilisées pour signer la liste de révocation.
1. Créez un `RevocationListFactory` instance.
1. Indiquez l’émetteur et le numéro de série du jeton de l’ordinateur à révoquer à l’aide d’une `IssuerAndSerialNumber` . Toutes les demandes d’accès aux Adobes contiennent un jeton d’ordinateur.
1. Créez un `RevocationList` en utilisant l’objet `IssuerAndSerialNumber` objet que vous venez de créer, et ajoutez-le à la liste de révocation en la transmettant `RevocationListFactory.addRevocationEntry()`. Générez la nouvelle liste de révocation en appelant `RevocationListFactory.generateRevocationList()`.
1. Pour enregistrer la liste de révocation, vous pouvez la sérialiser en appelant `RevocationList.getBytes()`. Pour charger la liste, appelez `RevocationListFactory.loadRevocationList()` et transmettez la liste sérialisée.
1. Vérifiez que la signature est valide et que la liste a été signée par le bon serveur de licences en appelant `RevocationList.verifySignature()`.
1. Pour vérifier si une entrée a été révoquée, transmettez la variable `IssuerAndSerialNumber` dans `RevocationList.isRevoked()`. La liste de révocation peut également être transmise à `HandlerConfiguration` pour que le SDK impose la liste de révocation pour toutes les demandes d’authentification et de licence.

Pour ajouter des entrées supplémentaires à une `RevocationList`, chargez une liste de révocation existante. Créer `RevocationListFactory` et veillez à incrémenter le numéro de CRL. Appeler `RevocationListFactioryEntries.addRevocationEntries` pour ajouter à la nouvelle liste toutes les entrées de l’ancienne liste. Appeler `RevocationListFactory.addRevocationEntry` pour ajouter de nouvelles entrées de révocation à RevocationList.

Pour obtenir un exemple de code montrant comment créer une liste de révocation, charger une liste de révocation existante et vérifier si un jeton de machine a été révoqué, voir `com.adobe.flashaccess.samples.revocation.CreateRevocationList` dans le répertoire &quot;Exemples&quot; des outils de ligne de commande de mise en oeuvre de référence.
