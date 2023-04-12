---
title: Configuration de votre environnement et test dans un environnement de préqualification
description: Configuration de votre environnement et test dans un environnement de préqualification
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---


# Configuration de votre environnement et test dans un environnement de préqualification{#setting-up-your-environment-and-testing-in-prequal}

>[!NOTE]
>
>Le contenu de cette page est fourni à titre d’information uniquement. L’utilisation de cette API nécessite une licence actuelle de Adobe. Aucune utilisation non autorisée n’est autorisée.

Cette note technique a pour but d’aider nos partenaires à configurer leur environnement et à commencer à tester une nouvelle version déployée dans l’environnement de préqualification de l’Adobe.

Comme il existe deux versions : ***production*** et ***staging***, dans ce document, nous allons nous concentrer sur la configuration de production en mentionnant que toutes les étapes sont les mêmes pour l’évaluation. Seules les URL sont différentes.

Les étapes 1 et 2 mettent en place l’environnement de test sur l’une des machines de test, l’étape 3 est une vérification du flux de base et les étapes 4 et 5 présentent quelques instructions de test.

>[!IMPORTANT]
>
> Il est très important d’exécuter les étapes 1 et 2 chaque fois que vous souhaitez modifier votre environnement de test (passer de l’évaluation au profil de production ou inversement).
 

## ÉTAPE 1. Résolution d’un domaine Pass sur une IP {#resolving-pass-domain-to-an-ip}

* Pour trouver une adresse IP de l&#39;équilibreur de charge utilisable pour l&#39;usurpation, exécutez la commande suivante :

* **Sous Windows**

   ```cmd
   C:\>nslookup sp-prequal.auth.adobe.com
   ...
   Addresses:  52.13.71.11
               54.184.208.150
   ```

```Choose any IP from **addresses** section (e.g. `52.13.71.11)```

* **Sous Linux/Mac**

```sh
    $ dig sp-prequal.auth.adobe.com
    
    ;; ANSWER SECTION:
    ...
    ............ 60 IN A      52.13.71.11
    ............ 60 IN A      54.184.208.150
```

```Choose any IP from **A records (**e.g `52.13.71.11)```

>[!NOTE]
>
>Les domaines exclus de la réponse car ils ne sont pas pertinents peuvent différer d’un utilisateur à l’autre.

>[!IMPORTANT]
>
> Ces adresses IP peuvent changer à l’avenir et elles peuvent ne pas être identiques pour les utilisateurs de différentes régions géographiques.


## ÉTAPE 2.  Présentation de l’environnement de préqualification en production {#spoofing-the-prequalification-environment}

* Modifiez la variable *c:\\windows\\System32\\drivers\\etc\\hosts* fichier (sous Windows) ou */etc/hosts* (sous Macintosh/Linux/Android) et ajoutez les éléments suivants :

* Profil de production nul
   * 52.13.71.11 http://entitlement.auth.adobe.com, http://sp.auth.adobe.com, http://api.auth.adobe.com

**Spoofing sur Android :** Pour réaliser une mise en forme sur Android, vous devez utiliser un émulateur Android.

* Une fois l’usurpation, vous pouvez simplement utiliser les URL régulières pour les profils de production et d’évaluation : (c&#39;est-à-dire : `http://sp.auth-staging.adobe.com` et `http://entitlement.auth-staging.adobe.com` et vous atteindrez le *environnement de préqualification/production* du* nouveau build.


## ÉTAPE 3.  Vérifiez que vous pointez vers l’environnement approprié. {#Verify-you-are-pointing-to-the-right-environment}

**C&#39;est une étape facile :**

* load [environnement précédent des droits](https://entitlement-prequal.auth.adobe.com/environment.html) et [droits](https://entitlement.auth.adobe.com/environment.html). Ils doivent renvoyer la même réponse.


## ÉTAPE 4.  Effectuez un flux d’authentification/d’autorisation simple à l’aide du site web du programmeur {#peform-a-simple-auth-flow}

* Cette étape nécessite l’adresse du site web du programmeur et quelques informations d’identification MVPD valides (un utilisateur authentifié et autorisé).

## ÉTAPE 5.  Effectuer des tests de scénario à l’aide des sites web du programmeur {#perform-scenario-testing-using-programmer-website}

* Après avoir terminé la configuration de l’environnement et vous être assuré que le flux d’authentification-autorisation de base fonctionne, vous pouvez passer aux tests de scénarios plus complexes.


## ÉTAPE 6.  Effectuer des tests à l’aide du site de test d’API {#perform-testing-using-api-testing-site}

* Si vous souhaitez approfondir le test de l’authentification Adobe Primetime, nous vous recommandons d’utiliser la variable [Site de test d’API](http://entitlement-prequal.auth.adobe.com/apitest/api.html).

Vous trouverez plus d’informations sur le site de test de l’API à l’adresse [Comment tester les flux d’authentification et d’autorisation à l’aide du site de test de l’API d’Adobe](/help/authentication/test-authn-authz-flows-using-adobes-api-test-site.md).

