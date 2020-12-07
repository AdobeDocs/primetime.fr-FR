---
description: L’interface de jeton de licence PlayReady fournit des services de production et de test.
seo-description: L’interface de jeton de licence PlayReady fournit des services de production et de test.
seo-title: Demande/réponse de jeton de licence PlayReady
title: Demande/réponse de jeton de licence PlayReady
uuid: 20ebd582-ebb9-4716-8c1e-df3e58d6ec14
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c
workflow-type: tm+mt
source-wordcount: '913'
ht-degree: 3%

---


# Demande de jeton de licence PlayReady / réponse {#playready-license-token-request-response}

L’interface de jeton de licence PlayReady fournit des services de production et de test.

Cette requête HTTP renvoie un jeton qui peut être utilisé pour une licence PlayReady.

**Méthode : GET, POST**  (avec un corps codé www-url qui contient des paramètres pour les deux méthodes)

**URL :**

* **Production :** `https://pr-gen.{prod_domain}/hms/pr/token`

* **Test :** ` [https://pr-gen.test.expressplay.com/hms/pr/token](https://pr-gen.test.expressplay.com/hms/pr/token)`

* **Exemple de demande :**

   ```
   <xref href="https: pr-gen.test.expressplay.com="" hms="" pr="" token?customerAuthenticator="201722,1ad8eed133edf43cbcc185f0236828ae&kid=b366360da82e9c6e0b0984002a362cf2&contentKey=b366360da82e9c6e0b0984002a362cf2&rightsType=BuyToOwn&analogVideoOPL=0&compressedDigitalAudioOPL=0&compressedDigitalVideoOPL=0&uncompressedDigitalAudioOPL=0&uncompressedDigitalVideoOPL=0&quot; format=&quot;html&quot; scope=&quot;external&quot;">
   https://pr-gen.test.expressplay.com/hms/pr/token?customerAuthenticator=
    <ExpressPlay customer authenticator identifier>
    &kid=<CEKSID>
    &contentKey=<CEK>
    &rightsType=BuyToOwn
    &analogVideoOPL=0
    &compressedDigitalAudioOPL=0
    &compressedDigitalVideoOPL=0
    &uncompressedDigitalAudioOPL=0
    &uncompressedDigitalVideoOPL=0
   </xref href="https:>
   ```

* **Exemple de réponse :**

   ```
   {"licenseAcquisitionUrl":"https://expressplay-licensing.axprod.net/LicensingService.ashx",
               "token":"<base64-encoded ExpressPlay token>"}
   ```

## Paramètres de la Requête de requêtes {#section_26F8856641A64A46A3290DBE61ACFAD2}

**Tableau 9 : Paramètres de Requête de jeton**

<table id="table_zxg_dyr_pv">  
 <thead> 
  <tr> 
   <th class="entry"><b>Paramètre de requête</b> </th> 
   <th class="entry"><b>Description</b> </th> 
   <th class="entry"><b>Obligatoire ?</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td><span class="codeph"> customerAuthenticator</span> </td> 
   <td> <p>Il s’agit de votre clé d’API client, une clé pour chacun de vos environnements de production et de test. Vous pouvez le trouver dans l’onglet Tableau de bord d’administration ExpressPlay. </p> </td> 
   <td> Oui </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> errorFormat</span> </td> 
   <td><span class="codeph"> html</span> ou <span class="codeph"> json</span>. Si <span class="codeph"> html</span> (valeur par défaut), une représentation HTML de toute erreur est fournie dans le corps d’entité de la réponse. <p>Si <span class="codeph"> json</span> est spécifié, une réponse structurée au format JSON est renvoyée. Voir <a href="https://www.expressplay.com/developer/restapi/#json-errors" format="html" scope="external"> Erreurs JSON</a> pour plus d’informations. </p> <p>Le type MIME de la réponse est soit <span class="codeph"> text/uri-liste</span> en cas de succès, <span class="codeph"> text/html</span> pour le format d’erreur HTML, soit <span class="codeph"> application/json</span> pour le format d’erreur JSON. </p> </td> 
   <td> Non </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 10 : Paramètres de la Requête de licence**

<table id="table_f1l_fyr_pv">  
 <thead> 
  <tr> 
   <th class="entry"><b>Paramètre de requête</b> </th> 
   <th class="entry"><b>Description</b> </th> 
   <th class="entry"><b>Obligatoire ?</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td><span class="codeph"> generalFlags</span> </td> 
   <td>Chaîne hexadécimale de 4 octets représentant les indicateurs de licence. Il doit être défini sur 00000001 pour une licence permanente. <p>Remarque : Les licences de location (<span class="codeph"> rightsType=Rental</span>) DOIVENT être persistantes. </p> </td> 
   <td> Non </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> kek</span> </td> 
   <td> Clé de chiffrement de clé (KEK). Les clés sont stockées cryptées avec une clé à l’aide d’un algorithme d’encapsulation de clé (AES Key Wrap, RFC3394). </td> 
   <td> Non </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> enfant</span> </td> 
   <td>Représentation d’une chaîne hexadécimale de 16 octets de la clé de chiffrement de contenu ou d’une chaîne <span class="codeph"> ^somestring'</span>. La longueur de la chaîne suivie du caractère "^" ne peut pas dépasser 64 caractères. </td> 
   <td> Oui </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> ek</span> </td> 
   <td> Une chaîne hexadécimale représentant la clé de contenu chiffrée. </td> 
   <td> Non </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> contentKey</span> </td> 
   <td> Représentation d’une chaîne hexadécimale de 16 octets de la clé de chiffrement du contenu </td> 
   <td>Oui, sauf si <span class="codeph"> kek</span> et <span class="codeph"> ek</span> ou <span class="codeph"> gamin</span> sont fournis </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> rightsType</span> </td> 
   <td>Indique le type de droits. Doit être <span class="codeph"> BuyToOwn</span> ou <span class="codeph"> Location</span>. </td> 
   <td> Oui </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> location.periodEndTime</span> </td> 
   <td>Date de fin de la location. Cette valeur DOIT être au format RFC 3339 _ date/heure au format de l'indicateur de zone Z ("heure Zulu"), ou un entier précédé d'un signe "+". <p>Si la valeur est un format de date/heure <a href="https://www.ietf.org/rfc/rfc3339.txt" format="html" scope="external"> RFC 3339</a>, elle représente une date/heure d’expiration absolue pour la licence. Un exemple de date/heure RFC 3339 est 2006-04-14T12:01:10Z. </p> <p> Si la valeur est un entier précédé d’un signe "+", elle est prise en tant que nombre relatif de secondes à partir du moment où le jeton est émis. Le contenu ne peut plus être lu après cette date. Uniquement valide si <span class="codeph"> rightsType</span> est <span class="codeph"> Location</span>. </p> </td> 
   <td>Oui, lorsque <span class="codeph"> rightsType</span> est <span class="codeph"> Location</span>. </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> location.playDuration</span> </td> 
   <td>Temps, en secondes, pendant lequel le contenu peut être lu une fois que la lecture a commencé. Uniquement valide si <span class="codeph"> rightsType</span> est loué. </td> 
   <td> Non </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> analogVideoOPL</span> </td> 
   <td> Entier pour indiquer le niveau de protection de sortie pour la vidéo analogique. Plage valide 0-999. </td> 
   <td> Oui </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> compresséDigitalAudioOPL</span> </td> 
   <td> Entier pour indiquer le niveau de protection de sortie pour l’audio numérique compressé. Plage valide 0-999. </td> 
   <td> Oui </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> compresséDigitalVideoOPL</span> </td> 
   <td> Entier pour indiquer le niveau de protection de sortie pour la vidéo numérique compressée. Plage valide 0-999. </td> 
   <td> Oui </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> uncompresséDigitalAudioOPL</span> </td> 
   <td> Entier pour indiquer le niveau de protection de sortie pour les fichiers audio numériques non compressés. Plage valide 0-999. </td> 
   <td> Oui </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> uncompresséDigitalVideoOPL</span> </td> 
   <td> Entier pour indiquer le niveau de protection de sortie pour la vidéo numérique non compressée. Plage valide 0-999. </td> 
   <td> Oui </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> unknownOutputBehavior</span> </td> 
   <td>Comportement requis lorsque la sortie est inconnue. Valeurs autorisées : <span class="codeph"> Autoriser </span>, <span class="codeph"> Interdire</span> ou <span class="codeph"> SDOnly</span> </td> 
   <td> Non </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> outputControlFlags</span> </td> 
   <td> Valeur hexadécimale de 4 octets pour indiquer les indicateurs des autres options de contrôle de sortie </td> 
   <td> Non </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> extensionType</span> </td> 
   <td>Mot arbitraire de 4 lettres représentant un identifiant 32 bits pour une extension. Le code ASCII 8 bits de chaque lettre correspond à la portion d’octet 8 bits de l’identifiant. Par exemple, la valeur d'identificateur 0x61626364 (hexadécimal) serait écrite "<span class="codeph"> abcd</span>", car le code ASCII pour "a" est 0x61, etc. </td> 
   <td> Non </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> extensionPayload</span> </td> 
   <td> Chaîne codée en base 64 de l’extension. </td> 
   <td>Oui, lorsque <span class="codeph"> extensionType</span> est spécifié. </td> 
  </tr> 
 </tbody> 
</table>

## Réponses {#section_0079C31B4AF14DBBB6277CF251FB90E3}

**Tableau 11 : Réponses HTTP**

| **Code d’état HTTP** | **Description** | **Content-Type** | **Le corps d’entité contient** |
|---|---|---|---|
| `200 OK` | Aucune erreur. | `text/uri-list` | URL et jeton d’acquisition de licence |
| `400 Bad Request` | Arguments non valides | `text/html` ou  `application/json` | Description de l’erreur |
| `401 Unauthorized` | Échec de l&#39;authentification | `text/html` ou  `application/json` | Description de l’erreur |
| `404 Not found` | URL incorrecte | `text/html` ou  `application/json` | Description de l’erreur |
| `50x Server Error` | Erreur serveur | `text/html` ou  `application/json` | Description de l’erreur |

**Tableau 12 : Codes d&#39;erreur de événement**

<table id="table_lqb_ycs_pv">  
 <thead> 
  <tr> 
   <th class="entry"><b>Code</b> </th> 
   <th class="entry"><b>Description</b> </th> 
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
   <td>Jeton d'authentification non valide : &lt;détails&gt; <p>Remarque :  Cela peut se produire si l’authentificateur est incorrect ou lors de l’accès à l’API de test sur *.test.expression.com à l’aide de l’authentificateur de production et vice versa. </p> <p importance="high">Remarque : Le SDK de test et l’outil de test avancé (ATT) ne fonctionnent qu’avec <span class="filepath"> *.test.expression.com</span>, tandis que les périphériques de production doivent utiliser <span class="filepath"> *.service.expression.com</span>. </p> </td> 
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
   <td> Type de droits non valide </td> 
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
   <td><span class="codeph"> </span> OutputControlFlagmust doit être codé 4 octets </td> 
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
   <td> -4018 </td> 
   <td>Enfant <span class="codeph"> manquant</span> </td> 
  </tr> 
  <tr> 
   <td> -4019 </td> 
   <td> Impossible d'obtenir la clé de contenu à partir du service d'enregistrement clé </td> 
  </tr> 
  <tr> 
   <td> -4020 </td> 
   <td><span class="codeph"> </span> kidmust be 32 caractères hexadécimaux long </td> 
  </tr> 
  <tr> 
   <td> -4021 </td> 
   <td><span class="codeph"> </span> kidmust doit comporter 64 caractères après le ^ </td> 
  </tr> 
  <tr> 
   <td> -4022 </td> 
   <td><span class="codeph"> enfant </span> non valide </td> 
  </tr> 
  <tr> 
   <td> -4024 </td> 
   <td>Clé <span class="codeph"> chiffrée </span> ou clé non valide </td> 
  </tr> 
  <tr> 
   <td> -5001 </td> 
   <td> Erreur de type de sortie inconnue non valide </td> 
  </tr> 
  <tr> 
   <td> -5002 </td> 
   <td> L'option PlayReady est désactivée pour ce service </td> 
  </tr> 
  <tr> 
   <td> -5003 </td> 
   <td> Indicateurs généraux non valides </td> 
  </tr> 
  <tr> 
   <td> -5004 </td> 
   <td> L'ID de périphérique doit comporter 32 caractères hexadécimaux. </td> 
  </tr> 
  <tr> 
   <td> -5005 </td> 
   <td> ID de périphérique non valide </td> 
  </tr> 
  <tr> 
   <td> -5006 </td> 
   <td> Valeur OPL manquante </td> 
  </tr> 
  <tr> 
   <td> -5007 </td> 
   <td>Seul l'un des <span class="codeph"> kek</span> ou <span class="codeph"> contentKey</span> peut être spécifié </td> 
  </tr> 
 </tbody> 
</table>
