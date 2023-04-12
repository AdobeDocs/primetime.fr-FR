---
title: Préautoriser
description: Préautoriser JavaScript
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '1499'
ht-degree: 0%

---


# Préautoriser {#js-preauthorize}

>[!NOTE]
>
>Le contenu de cette page est fourni à titre d’information uniquement. L’utilisation de cette API nécessite une licence actuelle de Adobe. Aucune utilisation non autorisée n’est autorisée.

## Présentation {#preauth-overview}

La méthode API de préautorisation doit être utilisée par les applications pour obtenir des décisions de préautorisation pour une ou plusieurs ressources. La demande de préautorisation d’API doit être utilisée pour les conseils d’interface utilisateur et/ou le filtrage de contenu. Une demande d’API d’autorisation réelle doit être effectuée avant d’autoriser l’accès de l’utilisateur aux ressources spécifiées.

Si une erreur inattendue (par exemple, un problème de réseau et un point de terminaison d’autorisation MVPD non disponible) se produit lorsqu’une demande d’API de préautorisation est traitée par les services d’authentification Adobe Primetime, alors une ou plusieurs informations d’erreur distinctes seront incluses pour les ressources affectées dans le cadre du résultat de la réponse de l’API de préautorisation.

### public preauthorized(request: PreauthorizedRequest, callback: AccessEnablerCallback&lt;any>) : void {#preauth-method}

**Description :** Cette méthode doit être utilisée par les applications pour obtenir des décisions de préautorisation (informatives) de l’utilisateur authentifié du service d’authentification Adobe Primetime afin d’afficher des ressources protégées spécifiques, dans le Principal but de décorer l’interface utilisateur de l’application (par exemple, en indiquant l’état d’accès avec les icônes de verrouillage et de déverrouillage).

**Disponibilité :** v4.4.0+

**Paramètres :**

* `PreauthorizeRequest`: Objet du créateur utilisé pour définir la requête
* `AccessEnablerCallback`: rappel utilisé pour renvoyer la réponse de l’API
* `PreauthorizeResponse`: Objet utilisé pour renvoyer le contenu de réponse de l’API

### class PreauthorizedRequestBuilder {#preath-req-builder-class}

#### setResources(resources: string[]) : PreallowRequestBuilder {#set-res-preath-req-buildr}

* Définit la Liste des ressources pour lesquelles vous souhaitez obtenir des décisions de préautorisation.
* Il est obligatoire de le définir pour l’utilisation de l’API de préautorisation.
* Chaque élément de la liste doit être une chaîne représentant soit la valeur de l’ID de ressource, soit le fragment RSS du média qui doit être accepté avec le MVPD.
* Cette méthode définit les informations uniquement dans le contexte de la variable active `PreauthorizeRequestBuilder` instance d’objet, qui est le récepteur de cet appel de méthode.

* Pour créer un réel `PreauthorizeRequest` vous pouvez y jeter un oeil. `PreauthorizeRequestBuilder`Méthode de &quot;s&quot; :

```JavaScript
  build(): PreauthorizeRequest
```

* `@param {string[]}` ressources. Liste des ressources pour lesquelles vous souhaitez obtenir des décisions de préautorisation.
* `@returns {PreauthorizeRequestBuilder}` Référence à la même `PreauthorizeRequestBuilder` instance d’objet, qui est le récepteur de l’appel de méthode.
* Cela permet de créer un chaînage de méthodes.

#### disableFeatures(..fonctionnalités : string[]) : PreallowRequestBuilder {#disabl-featres-preauth-req-buildr}

* Définit les fonctionnalités dont vous souhaitez qu’elles soient désactivées lors de l’obtention des décisions de préautorisation.
* Cette fonction définit les informations uniquement dans le contexte de la fonction active `PreauthorizeRequestBuilder` instance d’objet, qui est le récepteur de cet appel de fonction.
* Pour créer un réel `PreauthorizeRequest` vous pouvez y jeter un oeil. `PreauthorizeRequestBuilder`Fonction &#39;s&#39; :

```JavaScript
public func build() -> PreauthorizeRequest
```

* `@param {string[]}` fonctions. Ensemble de fonctionnalités que vous souhaitez désactiver.
* `@returns` Référence à la même `PreauthorizeRequestBuilder` instance d’objet, qui est le récepteur de l’appel de fonction.
* Il effectue cette opération afin de permettre la création d’un chaînage de fonctions.

#### build() : PreauthorizedRequest {#preauth-req}

* Crée et récupère la référence d’une nouvelle `PreauthorizeRequest` instance d’objet.
* Cette méthode instancie une nouvelle `PreauthorizeRequest` chaque fois qu’il est appelé.
* Cette méthode utilise les valeurs définies à l’avance dans le contexte de la variable active `PreauthorizeRequestBuilder` instance d’objet, qui est le récepteur de cet appel de méthode.
* Gardez à l&#39;esprit que cette méthode ne produit aucun effet secondaire,
* par conséquent, cela ne modifie pas l’état du SDK ni celui de la variable `PreauthorizeRequestBuilder` instance d’objet, qui est le récepteur de cet appel de méthode.
* Cela signifie que les appels successifs de cette méthode pour le même récepteur créeront une nouvelle `PreauthorizeRequest` , mais avec les mêmes informations, au cas où les valeurs définies sur la variable `PreauthorizeRequestBuilder` lorsqu’elles ne sont pas modifiées entre les appels.
* Si vous n’avez pas besoin de mettre à jour les informations fournies (ressources et mise en cache), vous pouvez réutiliser l’instance PreallowRequest pour plusieurs utilisations de l’API de préautorisation.
* `@returns {PreauthorizeRequest}`

### interface AccessEnablerCallback&lt;t> {#interface-access-enablr-callback}

#### onResponse(result: T); {#on-response-result}

* Rappel de réponse appelé par le SDK lorsque la demande d’API de préautorisation a été satisfaite.
* Le résultat obtenu est un résultat réussi ou une erreur contenant un état.
* `@param {T} result`

#### onFailure(result: T); {#on-failure-result}

* Rappel d’échec appelé par le SDK lorsque la demande d’API de préautorisation n’a pas pu être traitée.
* Le résultat est un résultat d’échec contenant un état.
* `@param {T} result`

### class PreauthorizedResponse {#preauth-response-class}

#### statut public : État; {#public-status}

* Renvoie : Informations supplémentaires sur l’état en cas d’échec.
* Peut contenir un `null` .

#### décisions publiques : Décision[]; {#public-decisions}

* Renvoie : Liste des décisions de préautorisation. Une décision pour chaque ressource.
* La liste peut être vide en cas d’échec.

### class Status {#class-status}

#### statut public : nombre; {#public-status-numbr}

* Le code d’état de réponse HTTP, comme indiqué dans la norme RFC 7231.
* Peut être égal à 0 au cas où la variable `Status` provient du SDK au lieu des services d’authentification Adobe Primetime.

#### code public : nombre; {#public-code-numbr}

* Code d’erreur des services d’authentification Adobe Primetime standard.
* peut contenir une chaîne vide ou un `null` .

#### message public : string; {#public-msg-string}

* Message détaillé qui dans certains cas est fourni par les points d’entrée d’autorisation MVPD ou par les règles de dégradation des programmeurs.
* peut contenir une chaîne vide ou un `null` .

#### informations publiques : string; {#public-details-strng}

* Contient un message détaillé qui dans certains cas est fourni par les points d’entrée d’autorisation MVPD ou par les règles de dégradation des programmeurs.
* peut contenir une chaîne vide ou un `null` .


#### public helpUrl : string; {#public-help-url-string}

* URL qui renvoie à des informations supplémentaires sur la raison de cet état/erreur et les solutions possibles.
* peut contenir une chaîne vide ou un `null` .

#### trace publique : string; {#public-trace-string}

* L’identifiant unique de cette réponse, qui peut être utilisé pour contacter l’assistance afin d’identifier des problèmes spécifiques dans des scénarios plus complexes.
* peut contenir une chaîne vide ou un `null` .

#### action publique : string; {#public-action-string}

* L’action recommandée pour remédier à la situation.
   * **none**: Malheureusement, il n&#39;y a pas d&#39;action prédéfinie pour résoudre ce problème. Cela peut indiquer un appel incorrect de l’API publique
   * **configuration**: Un changement de configuration est nécessaire par le biais du tableau de bord TVE ou en contactant l’assistance.
   * **application-registration**: La demande doit à nouveau s&#39;enregistrer.
   * **authentication**: L’utilisateur doit s’authentifier ou se reconnecter.
   * **authorization**: L’utilisateur doit obtenir l’autorisation de la ressource spécifique.
   * **dégradation**: Une forme de dégradation doit être appliquée.
   * **retry**: Une nouvelle tentative de requête peut résoudre le problème.
   * **retry-after**: Une nouvelle tentative après la période indiquée peut résoudre le problème.
* peut contenir une chaîne vide ou un `null` .

### Classe Decision {#class-decision}

#### public id : string; {#public-id-string}

* ID de ressource pour lequel la décision a été obtenue.

#### public autorisé : boolean; {#public-auth-boolean}

* La valeur de l’indicateur indiquant si la décision a réussi ou non.

#### erreur publique : État; {#public-error-status}

* Informations supplémentaires sur l’état en cas d’erreur. Peut contenir un `null` .

## Exemple de mise en oeuvre client {#client-imp-example}

```JavaScript
let accessEnablerApi = new window.AccessEnabler.AccessEnabler("software statement");
let accessEnablerModels = window.AccessEnabler.models;



// Build request
let requestBuilder = new accessEnablerModels.PreauthorizeRequest.getBuilder();
let request = requestBuilder
    .setResources(["RES01", "RES02", "RES03"])
    .disableFeatures("LOCAL_CACHE")
    .build();



// Create callback
let callback = {
    onResponse(response) {
        // Handle onResponse
    },
    onFailure(response) {
        // Handle onFailure
    }
};

// Invoke call
accessEnablerApi.preauthorize(request, callback);
```


## Exemples de scénarios {#scenario-examples}

### Scénario 1 : Toutes les ressources demandées ont été autorisées {#all-req-res-auth}

<table>
<thead>
  <tr>
    <th>Indicateur de code d’erreur amélioré</th>
    <th>Réponse</th>
  </tr>
</thead>
<tbody>
<tr>
    <td>Désactivé</td>
    <td>

```JavaScript
        {
    "decisions": [
        {
        "id": "RES01",
        "authorized": true
        },
        {
        "id": "RES02",
        "authorized": true
        },
        {
        "id": "RES03",
        "authorized": true
        }
    ]
    }    
```

</td>
  </tr>
</tbody>


### Scénario 2 : Certaines ressources demandées ont été autorisées. {#sm-req-res-auth}

<table>
<thead>
  <tr>
    <th>Indicateur de code d’erreur amélioré</th>
    <th>Réponse</th>
  </tr>
</thead>
<tbody>
<tr>
    <td>Désactivé</td>
    <td>

    &quot;JavaScript
    
    {
    &quot;décisions&quot; : [
    {
    &quot;id&quot;: &quot;RES01&quot;,
    &quot;authorized&quot; : true
    },
    {
    &quot;id&quot;: &quot;RES02&quot;,
    &quot;authorized&quot; : false
    },
    {
    &quot;id&quot;: &quot;RES03&quot;,
    &quot;authorized&quot; : true
    }
    ]
    }
    
    &quot;

</td>
  </tr>

<tr>
    <td>Activé</td>
    <td>

    &quot;JavaScript
    {
    &quot;décisions&quot; : [
    {
    &quot;id&quot;: &quot;RES01&quot;,
    &quot;authorized&quot; : true
    },
    {
    &quot;id&quot;: &quot;RES02&quot;,
    &quot;authorized&quot; : false,
    &quot;error&quot; : {
    &quot;status&quot;: 403,
    &quot;code&quot;: &quot;preauthorization_denied_by_mvpd&quot;,
    &quot;message&quot;: &quot;Le MVPD a renvoyé une décision \&quot;Refuser\&quot; lors de la demande de pré-autorisation pour la ressource spécifiée.&quot;,
    &quot;helpUrl&quot;: &quot;https://experienceleague.adobe.com/docs/primetime/authentication/home.html&quot;,
    &quot;action&quot; : &quot;none&quot;
    }
    },
    {
    &quot;id&quot;: &quot;RES03&quot;,
    &quot;authorized&quot; : true
    },
    ]
    }
    
    &quot;

</td>
  </tr>
</tbody>


### Scénario 3 : Aucune des ressources demandées n&#39;a été autorisée. {#none-req-res-auth}

<table>
<thead>
  <tr>
    <th>Indicateur de code d’erreur amélioré</th>
    <th>Réponse</th>
  </tr>
</thead>
<tbody>
<tr>
    <td>Désactivé</td>
    <td>

    &quot;JavaScript
    
    {
    &quot;décisions&quot; : [
    {
    &quot;id&quot;: &quot;RES01&quot;,
    &quot;authorized&quot; : false
    },
    {
    &quot;id&quot;: &quot;RES02&quot;,
    &quot;authorized&quot; : false
    },
    {
    &quot;id&quot;: &quot;RES03&quot;,
    &quot;authorized&quot; : false
    }
    ]
    }
    
    &quot;

</td>
  </tr>

<tr>
    <td>Activé</td>
    <td>

    &quot;JavaScript
    
    {
    &quot;décisions&quot; : [
    {
    &quot;id&quot;: &quot;RES01&quot;,
    &quot;authorized&quot; : false,
    &quot;error&quot; : {
    &quot;status&quot;: 403,
    &quot;code&quot;: &quot;preauthorization_denied_by_mvpd&quot;,
    &quot;message&quot;: &quot;Le MVPD a renvoyé une décision \&quot;Refuser\&quot; lors de la demande de pré-autorisation pour la ressource spécifiée.&quot;,
    &quot;helpUrl&quot;: &quot;https://experienceleague.adobe.com/docs/primetime/authentication/home.html&quot;,
    &quot;action&quot; : &quot;none&quot;
    }
    },
    {
    &quot;id&quot;: &quot;RES02&quot;,
    &quot;authorized&quot; : false,
    &quot;error&quot; : {
    &quot;status&quot;: 403,
    &quot;code&quot;: &quot;preauthorization_denied_by_mvpd&quot;,
    &quot;message&quot;: &quot;Le MVPD a renvoyé une décision \&quot;Refuser\&quot; lors de la demande de pré-autorisation pour la ressource spécifiée.&quot;,
    &quot;helpUrl&quot;: &quot;https://experienceleague.adobe.com/docs/primetime/authentication/home.html&quot;,
    &quot;action&quot; : &quot;none&quot;
    }
    },
    {
    &quot;id&quot;: &quot;RES03&quot;,
    &quot;authorized&quot; : false,
    &quot;error&quot; : {
    &quot;status&quot;: 403,
    &quot;code&quot;: &quot;maximum_execution_time_exceeded&quot;,
    &quot;message&quot;: &quot;La demande n’a pas été effectuée dans le délai maximal autorisé. Une nouvelle tentative de la requête peut résoudre le problème.&quot;,
    &quot;helpUrl&quot;: &quot;https://experienceleague.adobe.com/docs/primetime/authentication/home.html&quot;,
    &quot;action&quot; : &quot;retry&quot;
    }
    }
    ]
    }
    
    &quot;

</td>
  </tr>
</tbody>


### Scénario 4 : Requête client incorrecte - aucune ressource spécifiée. {#bad-cl-req-no-res-sp}

<table>
<thead>
  <tr>
    <th>Indicateur de code d’erreur amélioré</th>
    <th>Réponse</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Désactivé/activé</td>
    <td>

    &quot;JavaScript
    {
    &quot;status&quot;: {
    &quot;status&quot;: 400,
    &quot;code&quot;: &quot;internal_error&quot;,
    &quot;message&quot;: &quot;La requête a échoué en raison d’une erreur interne.&quot;,
    &quot;details&quot;: &quot;Le paramètre &quot;chaîne obligatoire[] &quot;ressource&quot; n’est pas présent&quot;,
    &quot;helpUrl&quot;: &quot;https://experienceleague.adobe.com/docs/primetime/authentication/home.html&quot;,
    &quot;action&quot; : &quot;none&quot;
    },
    &quot;décisions&quot; : []
    }
    &quot;

</td>
  </tr>
</tbody>
</table>

### Scénario 5 : Requête client incorrecte - ressources vides spécifiées. {#bad-cl-req-empt-res-sp}

<table>
<thead>
  <tr>
    <th>Indicateur de code d’erreur amélioré</th>
    <th>Réponse</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Désactivé/activé</td>
    <td>

    &quot;JavaScript
    {
    &quot;status&quot;: {
    &quot;status&quot;: 412,
    &quot;code&quot;: &quot;missing_resource&quot;,
    &quot;message&quot;: &quot;Le paramètre de ressource est manquant&quot;,
    &quot;helpUrl&quot;: &quot;https://experienceleague.adobe.com/docs/primetime/authentication/home.html&quot;,
    &quot;action&quot; : &quot;none&quot;
    },
    &quot;décisions&quot; : []
    }
    &quot;

</td>
  </tr>
</tbody>
</table>

### Scénario 6 : Erreur réseau. {#ntwrk-error}

<table>
<thead>
  <tr>
    <th>Indicateur de code d’erreur amélioré</th>
    <th>Réponse</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Activé</td>
    <td>

    &quot;JavaScript
    {
    &quot;décisions&quot; : [
    {
    &quot;id&quot;: &quot;RES01&quot;,
    &quot;authorized&quot; : false,
    &quot;error&quot; : {
    &quot;status&quot;: 403,
    &quot;code&quot;: &quot;network_received_error&quot;,
    &quot;message&quot;: &quot;Une erreur de lecture s’est produite lors de la récupération de la réponse du service partenaire associé. Une nouvelle tentative de la requête peut résoudre le problème.&quot;,
    &quot;helpUrl&quot;: &quot;https://experienceleague.adobe.com/docs/primetime/authentication/home.html&quot;,
    &quot;action&quot; : &quot;retry&quot;
    }
    },
    {
    &quot;id&quot;: &quot;RES02&quot;,
    &quot;authorized&quot; : false,
    &quot;error&quot; : {
    &quot;status&quot;: 403,
    &quot;code&quot;: &quot;network_received_error&quot;,
    &quot;message&quot;: &quot;Une erreur de lecture s’est produite lors de la récupération de la réponse du service partenaire associé. Une nouvelle tentative de la requête peut résoudre le problème.&quot;,
    &quot;helpUrl&quot;: &quot;https://experienceleague.adobe.com/docs/primetime/authentication/home.html&quot;,
    &quot;action&quot; : &quot;retry&quot;
    }
    }
    ]
    }
    &quot;

</td>
  </tr>
</tbody>
</table>

### Scénario 7 : Le flux de préautorisation a été appelé sans session AuthN valide.

<table>
<thead>
  <tr>
    <th>Indicateur de code d’erreur amélioré</th>
    <th>Réponse</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Désactivé/activé</td>
    <td>

    &quot;JavaScript
    {
    &quot;status&quot;: {
    &quot;status&quot;: 0,
    &quot;code&quot;: &quot;authentication_session_missing&quot;,
    &quot;message&quot;: &quot;La session d’authentification associée à cette requête n’a pas pu être récupérée. L’utilisateur doit se reconnecter avec un MVPD pris en charge pour pouvoir continuer.&quot;,
    &quot;action&quot; : &quot;authentication&quot;
    },
    &quot;décisions&quot; : []
    }
    
    &quot;

</td>
  </tr>
</tbody>
</table>



### Scénario 8 : Le flux de préautorisation a été appelé avant que l’appel setRequestor ne soit terminé.

<table>
<thead>
  <tr>
    <th>Indicateur de code d’erreur amélioré</th>
    <th>Réponse</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Désactivé/activé</td>
    <td>

    &quot;JavaScript
    {
    &quot;status&quot;: {
    &quot;status&quot;: 0,
    &quot;code&quot;: &quot;requestor_not_configured&quot;,
    &quot;message&quot;: &quot;Le demandeur n’est pas encore configuré, ce qui est une condition préalable à l’utilisation d’une API autre que l’API setRequestor.&quot;,
    &quot;action&quot; : &quot;retry&quot;
    },
    &quot;décisions&quot; : []
    }
    &quot;

</td>
  </tr>
</tbody>
</table>

