---
title: Utilisation de l’ID Experience Cloud dans l’authentification Primetime
description: Utilisation de l’ID Experience Cloud dans l’authentification Primetime
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---


# Utilisation de l’ID Experience Cloud dans l’authentification Primetime

>[!NOTE]
>
>Le contenu de cette page est fourni à titre d’information uniquement. L’utilisation de cette API nécessite une licence actuelle de Adobe. Aucune utilisation non autorisée n’est autorisée.

## Qu’est-ce que l’identifiant Experience Cloud et comment l’obtenir ? {#what-exp-cloud-id-obtain}

L’identifiant Experience Cloud (ECID, abrégé) est un identifiant unique généré par Adobe Experience Cloud pour chaque utilisateur de votre application/site web. L’ECID est très utilisé dans tous les rapports Experience Cloud afin de lier des informations sur un utilisateur spécifique dans plusieurs applications/sites web.

Si vous disposez déjà d’un système qui fournit un identifiant visiteur, vous devez utiliser le même identifiant pour la portée de ce document.

Une méthode pour obtenir l’ECID consiste à utiliser le service d’ID Experience Cloud. Vous pouvez utiliser le type d’implémentation de votre choix, soit en fonction de TDM, de la bibliothèque JS, du côté serveur, de l’intégration directe ou des bibliothèques natives pour les plateformes mobiles. Pour obtenir une vue d’ensemble complète des services, bibliothèques, SDK et guides de mise en oeuvre disponibles, voir : https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-implementation-guides.html





## Quel est l’avantage de l’utilisation de l’ID Experience Cloud dans l’authentification Primetime ? {#benefit-ex-cloud-id}

Si vous configurez nos SDK et l’API REST sans client pour utiliser votre ECID, vous pourrez ensuite lier les données collectées par l’authentification Primetime à vos solutions Experience Cloud existantes. Vous pourrez ainsi mieux comprendre le parcours et l’expérience de vos clients dans toutes les solutions fournies par Adobe.

## Comment utiliser l’ID d’Experience Cloud dans l’authentification Primetime ? {#how-to-ex-cloud-id-authn}

Après avoir obtenu l’ECID (expliqué ci-dessus), vous devez transmettre ces informations à nos SDK et à notre API REST sans client. Ces informations seront ensuite transmises à nos serveurs à chaque appel réseau effectué par le SDK. Le processus de configuration est différent pour chaque SDK comme suit :

### SDK JS {#js-sdk}

Pour JavaScript, vous devez transmettre l’ECID dans une carte en tant que troisième paramètre à l’appel setRequestor .

**Exemple d’utilisation :**

```JavaScript
accessEnabler.setRequestor("REQUESTOR_ID", ["ENDPOINT_URL"],
    {
        "visitorID": "THE_ECID_VALUE"
    }
);
```

### SDK iOS/tvOS {#ios-sdk}

Pour le SDK iOS/tvOS, il existe une méthode dédiée appelée setOptions.

**Exemple d’utilisation :**

```JavaScript
accessEnabler.setOptions(
    [
        "visitorID": "THE_ECID_VALUE"
    ]
);
```

### SDK Android/fireTV {#android-sdk}

Pour le SDK Android/fireTV, le mécanisme est similaire à iOS. Seul le nom du paramètre est différent. L’API est décrite ici.

**Exemple d’utilisation :**

```JavaScript
String visitor_id = "THE_ECID_VALUE";

HashMap<String, String> options = new HashMap();
options.put("ap_vi",visitor_id);

accessEnabler.setOptions(options);
```

### API sans client {#clientless-api}

Lors de l’utilisation d’Adobe Primetime via son API REST, la variable **ECID** doit être envoyée. **sur toutes les API** comme paramètre nommé **&#39;ap_vi&#39;**.

**Exemple d’utilisation :**

`GET: https://api.auth.adobe.com/api/v1/authorize?...&ap_vi=THE_ECID_VALUE`