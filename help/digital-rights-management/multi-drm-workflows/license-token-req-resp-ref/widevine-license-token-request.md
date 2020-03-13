---
description: L'interface du jeton de licence Widevine fournit des services de production et de test.
seo-description: L'interface du jeton de licence Widevine fournit des services de production et de test.
seo-title: Demande/réponse de jeton de licence Widevine
title: Demande/réponse de jeton de licence Widevine
uuid: a3522422-7075-49a7-bc55-137ef84ee430
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c

---


# Demande/réponse de jeton de licence Widevine {#widevine-license-token-request-response}

L&#39;interface du jeton de licence Widevine fournit des services de production et de test.

Cette requête HTTP renvoie un jeton qui peut être utilisé pour une licence Widevine.

**Méthode : GET, POST** (avec un corps codé www-url qui contient des paramètres pour les deux méthodes)

**URL :**

* **Production :** `https://wv-gen.{prod_domain}/hms/wv/token`

* **Test :** ` [https://wv-gen.test.expressplay.com/hms/wv/token](https://wv-gen.test.expressplay.com/hms/wv/token)`

* **Exemple de requête :**

   ```
   https://wv-gen.service.expressplay.com/hms/wv/token?customerAuthenticator= 
   <ExpressPlay customer authenticator identifier>
   ```

* **Exemple de réponse :**

   ```
   https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken=<base64-encoded ExpressPlay token>
   ```

<!--<a id="section_1E22012EE4B94BB2974D3B16DE8812D9"></a>-->

**Tableau 13 : Paramètres de  de jeton**

<table id="table_ww1_hcs_pv">  
 <thead> 
  <tr> 
   <th class="entry"> <b>Paramètre</b> </th> 
   <th class="entry"> <b>Description</b> </th> 
   <th class="entry"> <b>Obligatoire ?</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td> <span class="codeph"> customerAuthenticator </span> </td> 
   <td> <p>Il s’agit de votre clé d’API client, une clé pour votre production et testez  . Vous pouvez le trouver sur l’onglet  d’administration ExpressPlay. </p> </td> 
   <td> Oui </td> 
  </tr> 
  <tr> 
   <td> <span class="codeph"> errorFormat </span> </td> 
   <td> HTML <span class="codeph"> ou </span> json <span class="codeph"> </span>. <p>Si <span class="codeph"> html </span> (valeur par défaut), une représentation HTML de toute erreur est fournie dans le corps d’entité de la réponse. Si <span class="codeph"> json </span> est spécifié, une réponse structurée au format JSON est renvoyée. Voir Erreurs <a href="https://www.expressplay.com/developer/restapi/#json-errors" format="html" scope="external"> JSON </a> pour plus d’informations. </p> <p>Le type MIME de la réponse est <span class="codeph"> text/uri-- </span> en cas de succès, <span class="codeph"> text/html </span> pour le format d’erreur <span class="codeph"> html, ou </span> <span class="codeph"> application/json  pour le format d’erreur de  Json.</span><span class="codeph"></span> </p> </td> 
   <td> Non </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 14 : Paramètres  du de licence**

| Paramètre  | Description | Obligatoire ? |
|--- |--- |--- |
| `generalFlags` | Chaîne hexadécimale de 4 octets représentant les indicateurs de licence. &quot;0000&quot; est la seule valeur autorisée | Non |
| `kek` | Clé de chiffrement de clé (KEK). Les clés sont stockées chiffrées à l’aide d’une clé KEK à l’aide d’un algorithme d’encapsulation de clé (AES Key Wrap, RFC3394). | Non |
| `kid` | Une chaîne hexadécimale de 16 octets représentant la clé de chiffrement du contenu ou une chaîne `^somestring'`. La longueur de la chaîne suivie par le `^` ne peut pas être supérieure à 64 caractères. Consultez la note ci-dessous pour un exemple. | Oui |
| `ek` | Une chaîne hexadécimale représentant la clé de contenu chiffrée. | Non |
| `contentKey` | Une chaîne hexadécimale de 16 octets représentant la clé de chiffrement du contenu | Oui, sauf si `kek` et `ek` ou `kid` si |
| `contentId` | ID de contenu | Non |
| `securityLevel` | Les valeurs autorisées sont comprises entre 1 et 5. <ul><li>1 = `SW_SECURE_CRYPTO`</li><li> 2 = `SW_SECURE_DECODE` </li><li> 3 = `HW_SECURE_CRYPTO` </li><li> 4 = `HW_SECURE_DECODE` </li><li> 5 = `HW_SECURE_ALL`</li></ul> | Oui |
| `hdcpOutputControl` | Les valeurs autorisées sont 0, 1, 2. <ul><li>0 = `HDCP_NONE` </li><li> 1 = `HDCP_V1` </li><li> 2 = `HDCP_V2`</li></ul> | Oui |
| `licenseDuration` * | Durée de la licence en secondes. S’il n’est pas fourni, il indique qu’il n’existe aucune limite à la durée. Veuillez consulter la note ci-dessous pour obtenir des informations détaillées. | Non |
| `wvExtension` | court-formulaire encapsulant extensionType et extensionPayload, sous forme de chaîne séparée par des virgules. Voir le format ci-dessous. Exemple : `…&wvExtension=wudo,AAAAAA==&…` | Non, n’importe quel nombre peut être utilisé |

A propos `licenseDuration`: <ol><li> La lecture s’arrête `licenseDuration` quelques secondes après le début de la lecture. </li><li> Pour autoriser l’arrêt/la reprise de la lecture pendant une durée illimitée, omettez `licenseDuration` (l’option infinie est définie par défaut). Sinon, spécifiez la durée pendant laquelle les utilisateurs finaux doivent pouvoir profiter du flux. </li></ol>

**Tableau 15 : Paramètres  de restriction de jeton**

| Paramètre  | Description | Obligatoire ? |
|--- |--- |--- |
| `expirationTime` | Heure d’expiration de ce jeton. Cette valeur DOIT être une chaîne au format [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt) date/heure dans l’indicateur de zone &quot;Z&quot; (&quot;heure Zulu&quot;), ou un entier précédé du signe +. Un exemple de date/heure RFC 3339 est 2006-04-14T12:01:10Z. <br> Si la valeur est une chaîne au format date/heure [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt) , elle représente une date/heure d’expiration absolue pour le jeton. Si la valeur est un nombre entier précédé du signe +, le nombre de secondes, à partir de l’émission, pendant lequel le jeton est valide est interprété comme un nombre relatif de secondes. Par exemple, `+60` indique une minute. <br> La durée de vie maximale et par défaut du jeton (si elle n’est pas spécifiée) est de 30 jours. | Non |

**Tableau 16 : Paramètres de  de corrélation**

| **Paramètre** | **Description** | **Obligatoire ?** |
|---|---|---|
| `cookie` | Chaîne arbitraire de 32 caractères maximum transportée dans le jeton et consignée par le serveur d’échange de jeton. Peut être utilisé pour corréler les entrées de journal sur le serveur de remboursement et celles sur les serveurs de  du. | Non |

<!--<a id="section_6BFBD314C77C40C4B172ABBDD2D8D80E"></a>-->

**Tableau 17 : Réponse HTTP**

| **Code d’état HTTP** | **Description** | **Content-Type** | **Le corps d’entité contient** |
|---|---|---|---|
| `200 OK` | Aucune erreur. | `text/uri-list` | URL d’acquisition de licence + jeton |
| `400 Bad Request` | Arguments non valides | `text/html` ou `application/json` | Description de l’erreur |
| `401 Unauthorized` | Échec de l&#39;authentification | `text/html` ou `application/json` | Description de l’erreur |
| `404 Not found` | URL incorrecte | `text/html` ou `application/json` | Description de l’erreur |
| `50x Server Error` | Erreur du serveur | `text/html` ou `application/json` | Description de l’erreur |

**Tableau 18 : Codes d’erreur**

<table id="table_agj_gqx_pv">  
 <thead> 
  <tr> 
   <th class="entry"> Code </th> 
   <th class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td> -2002 </td> 
   <td> Délai d'expiration de jeton non valide : &lt;détails&gt; </td> 
  </tr> 
  <tr> 
   <td> -2003 </td> 
   <td> Adresse IP non valide </td> 
  </tr> 
  <tr> 
   <td> -2005 </td> 
   <td> Clé de chiffrement de contenu non valide : &lt;détails&gt; </td> 
  </tr> 
  <tr> 
   <td> -2008 </td> 
   <td> Indicateurs de contrôle de sortie non valides spécifiés : &lt;détails&gt; </td> 
  </tr> 
  <tr> 
   <td> -2017 </td> 
   <td> Le jeton d’authentification doit être fourni </td> 
  </tr> 
  <tr> 
   <td> -2018 </td> 
   <td> Jeton d'authentification non valide : &lt;détails&gt; <p>Remarque :  Cela peut se produire si l’authentificateur est incorrect ou lors de l’accès à l’API de test sur *.test.expression.com à l’aide de l’authentificateur de production et vice versa. </p> <p importance="high">Remarque :  Le SDK de test et l’outil de test avancé (ATT) fonctionnent uniquement avec <span class="filepath"> *.test.expression.com </span>, tandis que les périphériques de production doivent utiliser <span class="filepath"> *.service.expression.com. </span> </p>. </td> 
  </tr> 
  <tr> 
   <td> -2019 </td> 
   <td> Jetons insuffisants disponibles </td> 
  </tr> 
  <tr> 
   <td> -2022 </td> 
   <td> Heure de fin de la période de location manquante </td> 
  </tr> 
  <tr> 
   <td> -2023 </td> 
   <td> Durée de jeu de location manquante </td> 
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
   <td> Erreur d’administration ExpressPlay : &lt;détails&gt; </td> 
  </tr> 
  <tr> 
   <td> -2031 </td> 
   <td>  du service </td> 
  </tr> 
  <tr> 
   <td> -2033 </td> 
   <td> Cookie non valide </td> 
  </tr> 
  <tr> 
   <td> -2034 </td> 
   <td> Contrôle de sortie non valide, valeurs hors de la plage spécifiée </td> 
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
   <td> Format d'erreur spécifié non valide : &lt;format&gt; </td> 
  </tr> 
  <tr> 
   <td> -4001 </td> 
   <td> Impossible d'authentifier le périphérique </td> 
  </tr> 
  <tr> 
   <td> -4010 </td> 
   <td> Jeton non valide </td> 
  </tr> 
  <tr> 
   <td> -4018 </td> 
   <td> Enfant <span class="filepath"> disparu </span> </td> 
  </tr> 
  <tr> 
   <td> -4019 </td> 
   <td> Impossible d'obtenir la clé de contenu à partir de la clé  service  de </td> 
  </tr> 
  <tr> 
   <td> -4020 </td> 
   <td> <span class="codeph"> enfant </span> doit comporter 32 caractères hexadécimaux </td> 
  </tr> 
  <tr> 
   <td> -4021 </td> 
   <td> <span class="codeph"> enfant </span> doit comporter 64 caractères après le caractère "^" </td> 
  </tr> 
  <tr> 
   <td> -4022 </td> 
   <td> Enfant <span class="codeph"> non valide </span> </td> 
  </tr> 
  <tr> 
   <td> -4024 </td> 
   <td> Clé ou <span class="codeph"> clé chiffrée non valide </span> </td> 
  </tr> 
  <tr> 
   <td> -5003 </td> 
   <td> Indicateurs généraux non valides </td> 
  </tr> 
  <tr> 
   <td> -6005 </td> 
   <td> Données de clé non valides spécifiées </td> 
  </tr> 
  <tr> 
   <td> -6007 </td> 
   <td> Durée de location spécifiée non valide </td> 
  </tr> 
  <tr> 
   <td> -7002 </td> 
   <td> La liaison d'ID de périphérique n'est pas prise en charge pour Windows </td> 
  </tr> 
  <tr> 
   <td> -7003 </td> 
   <td> Valeur de niveau de sécurité manquante </td> 
  </tr> 
  <tr> 
   <td> -7004 </td> 
   <td> Valeur de niveau de sécurité non valide </td> 
  </tr> 
  <tr> 
   <td> -7006 </td> 
   <td> Valeur de contrôle de sortie HDCP manquante </td> 
  </tr> 
  <tr> 
   <td> -7007 </td> 
   <td> Durée de licence spécifiée non valide </td> 
  </tr> 
  <tr> 
   <td> -7008 </td> 
   <td> Impossible de générer la licence Widevine </td> 
  </tr> 
  <tr> 
   <td> -7009 </td> 
   <td> Paramètres WVExtension <span class="codeph"> </span> spécifiés non valides </td> 
  </tr> 
  <tr> 
   <td> -7011 </td> 
   <td> Option Widevine désactivée </td> 
  </tr> 
 </tbody> 
</table>