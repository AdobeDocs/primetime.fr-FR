---
description: L’interface de jeton de licence FairPlay fournit des services de production et de test.
title: Demande/réponse de jeton de licence FairPlay
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 4%

---

# Demande et réponse de jeton de licence FairPlay {#fairplay-license-token-request-response}

L’interface de jeton de licence FairPlay fournit des services de production et de test. Cette requête renvoie un jeton qui peut être consommé pour une licence FairPlay.

**Méthode : GET, POST** (avec un corps codé www-url qui contient des paramètres pour les deux méthodes)

**URL :**

* **Production :** `https://fp-gen.{prod_domain}/hms/fp/token`

* **Test :** `https://fp-gen.test.expressplay.com/hms/fp/token`

* **Exemple de requête :**

```<xref href="https: pr-gen.test.expressplay.com="" hms="" pr="" token?customerAuthenticator="201722,1ad8eed133edf43cbcc185f0236828ae&kid=b366360da82e9c6e0b0984002a362cf2&contentKey=b366360da82e9c6e0b0984002a362cf2&rightsType=BuyToOwn&analogVideoOPL=0&compressedDigitalAudioOPL=0&compressedDigitalVideoOPL=0&uncompressedDigitalAudioOPL=0&uncompressedDigitalVideoOPL=0&quot; format=&quot;html&quot; scope=&quot;external&quot;">
  https://fp-gen.test.expressplay.com/hms/fp/token?customerAuthenticator= 
   <ExpressPlay customer authenticator identifier> 
   &kid=<CEKSID> 
   &contentKey=<CEK> 
   &rightsType=BuyToOwn 
   &analogVideoOPL=0 
   &compressedDigitalAudioOPL=0 
   &compressedDigitalVideoOPL=0 
   &uncompressedDigitalAudioOPL=0 
   &uncompressedDigitalVideoOPL=0
```

* **Exemple de réponse :**

  ```
  https://fp.service.expressplay.com:80/hms/fp/rights/?ExpressPlayToken=<base64-encoded ExpressPlay token>
  ```

**Paramètres de requête de requête**

**Tableau 3 : Paramètres de requête de jeton**

| Paramètre de requête | Description | Obligatoire ? |
|--- |--- |--- |
| customerAuthenticator Authator du client en tant que paramètre de requête customerAuthenticator FairPlay | Il s’agit de votre clé d’API client, une pour vos environnements de production et de test. Vous pouvez le trouver dans l’onglet Tableau de bord administrateur ExpressPlay . | Oui |
| errorFormat | HTML ou json. Si html (valeur par défaut), une représentation par HTML des erreurs est fournie dans le corps de l’entité de la réponse. Si json est spécifié, une réponse structurée au format JSON est renvoyée. Voir [Erreurs JSON](https://www.expressplay.com/developer/restapi/#json-errors) pour plus d’informations. Le type MIME de la réponse est text/uri-list en cas de succès, text/html pour le format d’erreur de HTML ou application/json pour le format d’erreur JSON. | Non |

**Tableau 4 : Paramètres de requête de licence**

| **Paramètre de requête** | **Description** | **Obligatoire ?** |
|---|---|---|
| `generalFlags` | Chaîne hexadécimale de 4 octets représentant les indicateurs de licence. &quot;0000&quot; est la seule valeur autorisée. | Non |
| `kek` | Clé de chiffrement de clé (KEK). Les clés sont stockées cryptées avec une clé à l’aide d’un algorithme d’encapsulage de clé (AES Key Wrap, RFC3394). If `kek` est fourni, l’un des `kid` ou le `ek` les paramètres doivent être fournis, *mais pas les deux*. | Non |
| `kid` | Représentation sous forme de chaîne hexadécimale de 16 octets de la clé de chiffrement du contenu ou d’une chaîne `'^somestring'`. Longueur de la chaîne suivie de la valeur `'^'` ne peut pas dépasser 64 caractères. | Non |
| `ek` | Représentation sous forme de chaîne hexadécimale de la clé de contenu chiffrée. | Non |
| `contentKey` | Une représentation sous forme de chaîne hexadécimale de 16 octets de la clé de chiffrement du contenu | Oui, sauf si la variable `kek` et `ek` ou `kid` sont fournies. |
| `iv` | Une représentation sous forme de chaîne hexadécimale de 16 octets du chiffrement de contenu IV | Oui |
| `rentalDuration` | Durée de la location en secondes (par défaut - 0) | Non |
| `fpExtension` | Encapsulage de formulaire court `extensionType` et `extensionPayload`, sous la forme d’une chaîne séparée par des virgules. Par exemple : [..] `&fpExtension=wudo,AAAAAA==&`[..] | Non, n’importe quel nombre peut être utilisé |

**Tableau 5 : Paramètres de requête de restriction de jeton**

<table id="table_ar3_lsx_pv">  
 <thead> 
  <tr> 
   <th class="entry"> <b>Paramètre de requête</b> </th> 
   <th class="entry"> <b>Description</b> </th> 
   <th class="entry"> <b>Obligatoire ?</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td> <span class="codeph"> expirationTime </span> </td> 
   <td> Expiration de ce jeton. Cette valeur DOIT être une chaîne dans <a href="https://www.ietf.org/rfc/rfc3339.txt" format="html" scope="external"> RFC 3339 </a> format de date/heure dans l’indicateur de zone "Z" ("heure zoulou"), ou un entier précédé d’un signe "+". Exemple de date/heure RFC 3339 : <span class="codeph"> 2006-04-14T12:01:10Z </span>. <p>Si la valeur est une chaîne dans <a href="https://www.ietf.org/rfc/rfc3339.txt" format="html" scope="external"> RFC 3339 </a> format date/heure, puis représente une date/heure d’expiration absolue pour le jeton. Si la valeur est un entier précédé d’un signe "+", le jeton est interprété comme un nombre relatif de secondes, à partir de l’émission, qu’il est valide. </p> Par exemple : <span class="codeph"> +60 </span> spécifie une minute. La durée de vie maximale et par défaut du jeton (si elle n’est pas spécifiée) est de 30 jours. </td> 
   <td> Non </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 6 : Paramètres de requête de corrélation**

| **Paramètre de requête** | **Description** | **Obligatoire ?** |
|---|---|---|
| `cookie` | Chaîne arbitraire pouvant contenir jusqu’à 32 caractères, transportée dans le jeton et consignée par le serveur de rédemption du jeton. Vous pouvez l’utiliser pour mettre en corrélation les entrées de journal sur le serveur de rédemption et sur les serveurs du fournisseur de services. | Non |

**Réponse**

**Tableau 7 : Réponses HTTP**

| **Code d’état HTTP** | **Description** | **Content-Type** | **Le corps d’entité contient** |
|---|---|---|---|
| `200 OK` | Aucune erreur. | `text/uri-list` | URL d’acquisition de licence + jeton |
| `400 Bad Request` | Arguments non valides | `text/html` ou `application/json` | Description de l’erreur |
| `401 Unauthorized` | Échec de l’authentification | `text/html` ou `application/json` | Description de l’erreur |
| `404 Not found` | URL incorrecte | `text/html` ou `application/json` | Description de l’erreur |
| `50x Server Error` | Erreur du serveur | `text/html` ou `application/json` | Description de l’erreur |

**Tableau 8 : Codes d’erreur des événements**

<table id="table_i2c_zsx_pv">  
 <thead> 
  <tr> 
   <th class="entry"> <b>Code</b> </th> 
   <th class="entry"> <b>Description</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td> -2002 </td> 
   <td> Délai d’expiration du jeton non valide : &lt;details&gt; </td> 
  </tr> 
  <tr> 
   <td> -2003 </td> 
   <td> Adresse IP non valide </td> 
  </tr> 
  <tr> 
   <td> -2005 </td> 
   <td> Clé de chiffrement du contenu non valide : &lt;details&gt; </td> 
  </tr> 
  <tr> 
   <td> -2008 </td> 
   <td> Indicateurs de contrôle de sortie non valides spécifiés : &lt;details&gt; </td> 
  </tr> 
  <tr> 
   <td> -2017 </td> 
   <td> Le jeton d’authentification doit être fourni </td> 
  </tr> 
  <tr> 
   <td> -2018 </td> 
   <td> Jeton d’authentification non valide : &lt;details&gt; <p>Remarque : Cela peut se produire si l’authentificateur est incorrect ou lors de l’accès à l’API de test à l’adresse <span class="filepath"> *.test.expressplay.com </span> à l’aide de l’authentificateur de production et vice versa. </p> <p importance="high">Remarque : Le SDK Test et l’outil de test avancé fonctionnent uniquement avec <span class="filepath"> *.test.expressplay.com </span>, tandis que les appareils de production doivent utiliser <span class="filepath"> *.service.expressplay.com </span>. </p> </td> 
  </tr> 
  <tr> 
   <td> -2019 </td> 
   <td> Jetons insuffisants disponibles </td> 
  </tr> 
  <tr> 
   <td> -2020 </td> 
   <td> Type de droits manquants </td> 
  </tr> 
  <tr> 
   <td> -2021 </td> 
   <td> Type de droits non valides </td> 
  </tr> 
  <tr> 
   <td> -2022 </td> 
   <td> Heure de fin de la période de location manquante </td> 
  </tr> 
  <tr> 
   <td> -2023 </td> 
   <td> Durée de lecture de location manquante </td> 
  </tr> 
  <tr> 
   <td> -2025 </td> 
   <td> Durée de lecture de location non valide </td> 
  </tr> 
  <tr> 
   <td> -2027 </td> 
   <td> La clé de chiffrement du contenu doit comporter 32 chiffres hexadécimaux. </td> 
  </tr> 
  <tr> 
   <td> -2030 </td> 
   <td> Erreur d’administration ExpressPlay : &lt;details&gt; </td> 
  </tr> 
  <tr> 
   <td> -2031 </td> 
   <td> Compte de service désactivé </td> 
  </tr> 
  <tr> 
   <td> -2033 </td> 
   <td> Cookie non valide </td> 
  </tr> 
  <tr> 
   <td> -2034 </td> 
   <td> Contrôle de sortie non valide, valeurs en dehors de la plage spécifiée </td> 
  </tr> 
  <tr> 
   <td> -2035 </td> 
   <td> Aucune valeur correspondante spécifiée </td> 
  </tr> 
  <tr> 
   <td> -2036 </td> 
   <td> Le type d’extension doit comporter 4 caractères. </td> 
  </tr> 
  <tr> 
   <td> -2037 </td> 
   <td> La charge utile de l’extension doit être encodée en Base64. </td> 
  </tr> 
  <tr> 
   <td> -2040 </td> 
   <td> <span class="codeph"> OutputControlFlag </span> doit être encodé 4 octets </td> 
  </tr> 
  <tr> 
   <td> -3004 </td> 
   <td> Format d’erreur non valide spécifié : &lt;format&gt; </td> 
  </tr> 
  <tr> 
   <td> -4001 </td> 
   <td> L’appareil n’a pas pu être authentifié. </td> 
  </tr> 
  <tr> 
   <td> -4010 </td> 
   <td> Jeton non valide </td> 
  </tr> 
  <tr> 
   <td> -4018 </td> 
   <td> Enfant manquant </td> 
  </tr> 
  <tr> 
   <td> -4019 </td> 
   <td> Échec de l’obtention de la clé de contenu à partir du service de stockage clé </td> 
  </tr> 
  <tr> 
   <td> -4020 </td> 
   <td> <span class="codeph"> gamin </span> doit comporter 32 caractères hexadécimaux </td> 
  </tr> 
  <tr> 
   <td> -4021 </td> 
   <td> <span class="codeph"> gamin </span> doit comporter 64 caractères après le ^ </td> 
  </tr> 
  <tr> 
   <td> -4022 </td> 
   <td> Non valide <span class="codeph"> gamin </span> </td> 
  </tr> 
  <tr> 
   <td> -4024 </td> 
   <td> Clé chiffrée non valide ou <span class="codeph"> kek </span> </td> 
  </tr> 
  <tr> 
   <td> -5003 </td> 
   <td> Indicateurs généraux non valides </td> 
  </tr> 
  <tr> 
   <td> -6001 </td> 
   <td> Non valide <span class="codeph"> FPExtension </span> paramètres spécifiés </td> 
  </tr> 
  <tr> 
   <td> -6002 </td> 
   <td> Type de jeton FP non valide </td> 
  </tr> 
  <tr> 
   <td> -6003 </td> 
   <td> Non valide <span class="codeph"> iv </span> parameter specified </td> 
  </tr> 
  <tr> 
   <td> -6004 </td> 
   <td> Échec de la génération de CKC pour FP </td> 
  </tr> 
  <tr> 
   <td> -6005 </td> 
   <td> Données de clé non valides spécifiées </td> 
  </tr> 
  <tr> 
   <td> -6006 </td> 
   <td> Service non autorisé pour la prise en charge de FairPlay </td> 
  </tr> 
  <tr> 
   <td> -6007 </td> 
   <td> Durée de location non valide spécifiée </td> 
  </tr> 
  <tr> 
   <td> -6008 </td> 
   <td> La liaison d’ID de périphérique n’est pas prise en charge pour FairPlay. </td> 
  </tr> 
  <tr> 
   <td> -6009 </td> 
   <td> Option FairPlay désactivée </td> 
  </tr> 
 </tbody> 
</table>
