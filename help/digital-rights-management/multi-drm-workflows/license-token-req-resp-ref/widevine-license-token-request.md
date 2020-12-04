---
description: L'interface de jeton de licence Widevine fournit des services de production et de test.
seo-description: L'interface de jeton de licence Widevine fournit des services de production et de test.
seo-title: Demande/réponse de jeton de licence Widevine
title: Demande/réponse de jeton de licence Widevine
uuid: a3522422-7075-49a7-bc55-137ef84ee430
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c
workflow-type: tm+mt
source-wordcount: '873'
ht-degree: 5%

---


# Demande/réponse de jeton de licence Widevine {#widevine-license-token-request-response}

L&#39;interface de jeton de licence Widevine fournit des services de production et de test.

Cette requête HTTP renvoie un jeton qui peut être racheté pour une licence Widevine.

**Méthode : GET, POST**  (avec un corps codé www-url qui contient des paramètres pour les deux méthodes)

**URL :**

* **Production :** `https://wv-gen.{prod_domain}/hms/wv/token`

* **Test :** ` [https://wv-gen.test.expressplay.com/hms/wv/token](https://wv-gen.test.expressplay.com/hms/wv/token)`

* **Exemple de demande :**

   ```
   https://wv-gen.service.expressplay.com/hms/wv/token?customerAuthenticator= 
   <ExpressPlay customer authenticator identifier>
   ```

* **Exemple de réponse :**

   ```
   https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken=<base64-encoded ExpressPlay token>
   ```

<!--<a id="section_1E22012EE4B94BB2974D3B16DE8812D9"></a>-->

**Tableau 13 : Paramètres de Requête de jeton**

<table id="table_ww1_hcs_pv">  
 <thead> 
  <tr> 
   <th class="entry"> <b>Paramètre de requête</b> </th> 
   <th class="entry"> <b>Description</b> </th> 
   <th class="entry"> <b>Obligatoire ?</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td> <span class="codeph"> customerAuthenticator  </span> </td> 
   <td> <p>Il s’agit de votre clé d’API client, une clé pour chacun de vos environnements de production et de test. Vous pouvez le trouver dans l’onglet Tableau de bord d’administration ExpressPlay. </p> </td> 
   <td> Oui </td> 
  </tr> 
  <tr> 
   <td> <span class="codeph"> errorFormat  </span> </td> 
   <td> <span class="codeph"> html </span> ou <span class="codeph"> json </span>. <p>Si <span class="codeph"> html </span> (valeur par défaut), une représentation HTML de toute erreur est fournie dans le corps d’entité de la réponse. Si <span class="codeph"> json </span> est spécifié, une réponse structurée au format JSON est renvoyée. Voir <a href="https://www.expressplay.com/developer/restapi/#json-errors" format="html" scope="external"> Erreurs JSON </a> pour plus d’informations. </p> <p>Le type MIME de la réponse est soit <span class="codeph"> text/uri-liste </span> sur succès, <span class="codeph"> text/html </span> pour le format d'erreur <span class="codeph"> html </span>, soit <span class="codeph"> application/json </span> pour le format d'erreur </span> json &lt;a9/&gt;.<span class="codeph"> </span></p> </td> 
   <td> Non </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 14 : Paramètres de la Requête de licence**

| Paramètre de requête | Description | Obligatoire ? |
|--- |--- |--- |
| `generalFlags` | Chaîne hexadécimale de 4 octets représentant les indicateurs de licence. &quot;0000&quot; est la seule valeur autorisée | Non |
| `kek` | Clé de chiffrement de clé (KEK). Les clés sont stockées cryptées avec une clé à l’aide d’un algorithme d’encapsulation de clé (AES Key Wrap, RFC3394). | Non |
| `kid` | Représentation d’une chaîne hexadécimale de 16 octets de la clé de chiffrement de contenu ou d’une chaîne `^somestring'`. La longueur de la chaîne suivie de `^` ne peut pas être supérieure à 64 caractères. Consultez la note ci-dessous pour un exemple. | Oui |
| `ek` | Une chaîne hexadécimale représentant la clé de contenu chiffrée. | Non |
| `contentKey` | Représentation d’une chaîne hexadécimale de 16 octets de la clé de chiffrement du contenu | Oui, sauf si `kek` et `ek` ou `kid` sont fournis |
| `contentId` | ID de contenu | Non |
| `securityLevel` | Les valeurs autorisées sont comprises entre 1 et 5. <ul><li>1 = `SW_SECURE_CRYPTO`</li><li> 2 = `SW_SECURE_DECODE` </li><li> 3 = `HW_SECURE_CRYPTO` </li><li> 4 = `HW_SECURE_DECODE` </li><li> 5 = `HW_SECURE_ALL`</li></ul> | Oui |
| `hdcpOutputControl` | Les valeurs autorisées sont 0, 1, 2. <ul><li>0 = `HDCP_NONE` </li><li> 1 = `HDCP_V1` </li><li> 2 = `HDCP_V2`</li></ul> | Oui |
| `licenseDuration` * | Durée de la licence en secondes. Si elle n’est pas fournie, elle indique qu’il n’y a pas de limite à la durée. Veuillez consulter la note ci-dessous pour obtenir des informations détaillées. | Non |
| `wvExtension` | Un court formulaire encapsulant extensionType et extensionPayload, sous forme de chaîne séparée par des virgules. Voir le format ci-dessous. Exemple : `…&wvExtension=wudo,AAAAAA==&…` | Non, n’importe quel nombre peut être utilisé |

À propos de `licenseDuration` : <ol><li> La lecture s’arrête `licenseDuration` secondes après le début de la lecture. </li><li> Pour autoriser l’arrêt/la reprise de la lecture pendant une durée illimitée, omettez `licenseDuration` (il sera par défaut infini). Sinon, spécifiez la durée pendant laquelle les utilisateurs finaux doivent pouvoir profiter du flux. </li></ol>

**Tableau 15 : Paramètres de Requête de restriction de jeton**

| Paramètre de requête | Description | Obligatoire ? |
|--- |--- |--- |
| `expirationTime` | Heure d’expiration de ce jeton. Cette valeur DOIT être une chaîne au format de date/heure [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt) dans l&#39;indicateur de zone &quot;Z&quot; (&quot;heure Zulu&quot;), ou un entier précédé d&#39;un signe +. Un exemple de date/heure RFC 3339 est 2006-04-14T12:01:10Z. <br> Si la valeur est une chaîne au format  [RFC 339](https://www.ietf.org/rfc/rfc3339.txt) date/heure, elle représente une date/heure d’expiration absolue pour le jeton. Si la valeur est un entier précédé du signe +, le jeton est interprété comme un nombre relatif de secondes, à partir de l’émission, que le jeton est valide. Par exemple, `+60` spécifie une minute. <br> La durée de vie maximale et par défaut (si elle n’est pas spécifiée) du jeton est de 30 jours. | Non |

**Tableau 16 : Paramètres de Requête de corrélation**

| **Paramètre de requête** | **Description** | **Obligatoire ?** |
|---|---|---|
| `cookie` | Chaîne arbitraire pouvant contenir jusqu’à 32 caractères transportée dans le jeton et consignée par le serveur de remboursement du jeton. Peut être utilisé pour corréler les entrées de journal sur le serveur de remboursement et celles sur les serveurs du prestataire. | Non |

<!--<a id="section_6BFBD314C77C40C4B172ABBDD2D8D80E"></a>-->

**Tableau 17 : Réponse HTTP**

| **Code d’état HTTP** | **Description** | **Content-Type** | **Le corps d’entité contient** |
|---|---|---|---|
| `200 OK` | Aucune erreur. | `text/uri-list` | URL d’acquisition de licence + jeton |
| `400 Bad Request` | Arguments non valides | `text/html` ou  `application/json` | Description de l’erreur |
| `401 Unauthorized` | Échec de l&#39;authentification | `text/html` ou  `application/json` | Description de l’erreur |
| `404 Not found` | URL incorrecte | `text/html` ou  `application/json` | Description de l’erreur |
| `50x Server Error` | Erreur serveur | `text/html` ou  `application/json` | Description de l’erreur |

**Tableau 18 : Codes d&#39;erreur de événement**

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
   <td> Le jeton d'authentification doit être fourni </td> 
  </tr> 
  <tr> 
   <td> -2018 </td> 
   <td> Jeton d'authentification non valide : &lt;détails&gt; <p>Remarque :  Cela peut se produire si l’authentificateur est incorrect ou lors de l’accès à l’API de test sur *.test.expression.com à l’aide de l’authentificateur de production et vice versa. </p> <p importance="high">Remarque :  Le SDK de test et l'outil de test avancé (ATT) ne fonctionnent qu'avec <span class="filepath"> *.test.expression.com </span>, tandis que les périphériques de production doivent utiliser <span class="filepath"> *.service.expression.com </span> </p>. </td> 
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
   <td> Durée de lecture de location manquante </td> 
  </tr> 
  <tr> 
   <td> -2025 </td> 
   <td> Durée de lecture de location non valide </td> 
  </tr> 
  <tr> 
   <td> -2027 </td> 
   <td> La clé de chiffrement du contenu doit contenir 32 chiffres hexadécimaux. </td> 
  </tr> 
  <tr> 
   <td> -2030 </td> 
   <td> Erreur d’administration ExpressPlay : &lt;détails&gt; </td> 
  </tr> 
  <tr> 
   <td> -2031 </td> 
   <td> Compte désactivé de service </td> 
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
   <td> Le type d'extension doit comporter 4 caractères </td> 
  </tr> 
  <tr> 
   <td> -2037 </td> 
   <td> La charge utile de l’extension doit être encodée en Base64. </td> 
  </tr> 
  <tr> 
   <td> -2040 </td> 
   <td> <span class="codeph"> OutputControlFlag  </span> doit être codé 4 octets </td> 
  </tr> 
  <tr> 
   <td> -3004 </td> 
   <td> Format d'erreur non valide spécifié : &lt;format&gt; </td> 
  </tr> 
  <tr> 
   <td> -4001 </td> 
   <td> Le périphérique n'a pas pu être authentifié </td> 
  </tr> 
  <tr> 
   <td> -4010 </td> 
   <td> Jeton non valide </td> 
  </tr> 
  <tr> 
   <td> -4018 </td> 
   <td> Enfant <span class="filepath"> manquant </span> </td> 
  </tr> 
  <tr> 
   <td> -4019 </td> 
   <td> Impossible d'obtenir la clé de contenu à partir du service d'enregistrement clé </td> 
  </tr> 
  <tr> 
   <td> -4020 </td> 
   <td> <span class="codeph"> enfant  </span> doit comporter 32 caractères hexadécimaux </td> 
  </tr> 
  <tr> 
   <td> -4021 </td> 
   <td> <span class="codeph"> enfant  </span> doit comporter 64 caractères après le caractère '^' </td> 
  </tr> 
  <tr> 
   <td> -4022 </td> 
   <td> <span class="codeph"> enfant </span> non valide </td> 
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
   <td> -6005 </td> 
   <td> Données clés non valides spécifiées </td> 
  </tr> 
  <tr> 
   <td> -6007 </td> 
   <td> Durée de location spécifiée non valide </td> 
  </tr> 
  <tr> 
   <td> -7002 </td> 
   <td> La liaison d'ID de périphérique n'est pas prise en charge pour Widevine </td> 
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
   <td> Paramètres <span class="codeph"> WVExtension </span> non valides spécifiés </td> 
  </tr> 
  <tr> 
   <td> -7011 </td> 
   <td> Option Widevine désactivée </td> 
  </tr> 
 </tbody> 
</table>