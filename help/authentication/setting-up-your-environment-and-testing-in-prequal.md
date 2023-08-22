---
title: Configuration de votre environnement et test dans un environnement de préqualification
description: Configuration de votre environnement et test dans un environnement de préqualification
exl-id: f822c0a1-045a-401f-a44f-742ed25bfcdc
source-git-commit: 84a16ce775a0aab96ad954997c008b5265e69283
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# Configuration de votre environnement et test dans les versions préliminaires{#setting-up-your-environment-and-testing-in-prequal}

>[!NOTE]
>
>Le contenu de cette page est fourni à titre d’information uniquement. L’utilisation de cette API nécessite une licence en cours de Adobe. Aucune utilisation non autorisée n’est autorisée.

L’objectif de cette note technique est d’aider nos partenaires à configurer leur environnement et à tester une nouvelle version déployée sur le Adobe l’environnement de pré-qualification.

Étant donné qu’il y a deux versions de build : ***production*** et ***mise en œuvre*** , dans ce document, nous nous concentrons sur la configuration de la production en mentionnant que toutes les étapes sont identiques pour l’évaluation, seules les URL sont différentes.

Les étapes 1 et 2 configurent l’environnement de test sur l’une des machines de test, l’étape 3 est une vérification du flux de base et les étapes 4 &amp; 5 composent certaines directives de test.

>[!IMPORTANT]
>
> Il est très important d’exécuter les étapes 1 et 2 chaque fois que vous souhaitez modifier votre environnement de test (passage de l’évaluation à l’état de production ou l’inverse)


## ÉTAPE 1. Résolution d’un problème de transfert de domaine vers une adresse IP {#resolving-pass-domain-to-an-ip}

* Pour trouver une adresse IP de l&#39;équilibreur de charge utilisable pour l&#39;usurpation, exécutez la commande suivante :

* **Sous Windows**

  ```cmd
  C:\>nslookup sp-prequal.auth.adobe.com
  ...
  Addresses:  52.13.71.11
              54.184.208.150
  ```

```Choose any IP from **addresses** section (e.g. `52.13.71.11)```

* **Sous Linux/Mac**

```sh
    $ dig sp-prequal.auth.adobe.com
    
    ;; ANSWER SECTION:
    ...
    ............ 60 IN A      52.13.71.11
    ............ 60 IN A      54.184.208.150
```

```Choose any IP from **A records (**e.g `52.13.71.11)```

>[!NOTE]
>
>Les domaines exclus de la réponse, car ils ne sont pas pertinents et peuvent différer d’un utilisateur à l’autres.

>[!IMPORTANT]
>
> Ces adresses IP peuvent changer à l’avenir et elles peuvent ne pas être les mêmes pour les utilisateurs de différentes régions géographiques.


## ÉTAPE 2.  Usurpation de l’environnement de pré-qualification en production {#spoofing-the-prequalification-environment}

* Modifiez le *fichier c:\\windows\\System32\\drivers\\etc\\hosts* (dans Windows) ou *le fichier/etc/hosts* (sous Macintosh/Linux/Android) et ajoutez ce qui suit :

* Usurpation de profil de production
   * 52.13.71.11 http://entitlement.auth.adobe.com, http://sp.auth.adobe.com, http://api.auth.adobe.com

**Spoofing sur Android :** Pour réaliser une mise en forme sur Android, vous devez utiliser un émulateur Android.

* Une fois l’usurpation, vous pouvez simplement utiliser les URL standard pour les profils de production et d’évaluation : (c’est-à-dire, `http://sp.auth-staging.adobe.com` et `http://entitlement.auth-staging.adobe.com` et vous atteindrez le *environnement de préqualification/production* du* nouveau build.


## ÉTAPE 3.  Vérifiez que vous pointez vers l’environnement approprié. {#Verify-you-are-pointing-to-the-right-environment}

**Il s’agit d’une étape facile :**

* Chargez [ l’environnement ](https://entitlement-prequal.auth.adobe.com/environment.html) et l’habilitation ](https://entitlement.auth.adobe.com/environment.html) préqualys de [ l’habilitation. Elles doivent renvoyer la même réponse.


## ÉTAPE 4.  Exécution d’un flux d’authentification/d’autorisation simple à l’aide du site Web du programmeur {#peform-a-simple-auth-flow}

* Cette étape nécessite l’adresse du programmeur du programmeur et certaines informations d’identification MVPD valides (utilisateur authentifié et autorisé).

## ETAPE 5.  Effectuer des tests de scénario à l’aide des sites Web du programmeur {#perform-scenario-testing-using-programmer-website}

* Une fois que vous avez terminé la configuration de l’environnement et que le flux d’autorisation de l’authentification de base fonctionne, vous pouvez procéder au test des scénarios plus complexes.


## ÉTAPE 6.  Effectuer des tests à l’aide du site de test d’API {#perform-testing-using-api-testing-site}

* Si vous souhaitez approfondir le test de l’authentification Adobe Primetime, nous vous recommandons d’utiliser la variable [Site de test d’API](http://entitlement-prequal.auth.adobe.com/apitest/api.html).

Pour plus d’informations sur le site de test d’API, voir [Comment tester les flux d’authentification et d’autorisation à l’aide du site de test de l’API d’Adobe](/help/authentication/test-authn-authz-flows-using-adobes-api-test-site.md).
