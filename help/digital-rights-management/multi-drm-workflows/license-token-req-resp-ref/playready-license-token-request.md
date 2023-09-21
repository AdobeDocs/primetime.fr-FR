---
description: L’interface de jeton de licence PlayReady fournit des services de production et de test.
title: Demande/réponse de jeton de licence PlayReady
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 4%

---

# Demande/réponse de jeton de licence PlayReady {#playready-license-token-request-response}

L’interface de jeton de licence PlayReady fournit des services de production et de test.

Cette requête HTTP renvoie un jeton qui peut être consommé pour une licence PlayReady .

**Méthode : GET, POST** (avec un corps codé www-url qui contient des paramètres pour les deux méthodes)

**URL :**

* **Production :** `https://pr-gen.{prod_domain}/hms/pr/token`

* **Test :** ` [https://pr-gen.test.expressplay.com/hms/pr/token](https://pr-gen.test.expressplay.com/hms/pr/token)`

* **Exemple de requête :**

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

## Paramètres de requête de requête {#section_26F8856641A64A46A3290DBE61ACFAD2}

**Tableau 9 : Paramètres de requête de jeton**

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
   <td> <p>Il s’agit de votre clé d’API client, une pour vos environnements de production et de test. Vous pouvez le trouver dans l’onglet Tableau de bord administrateur ExpressPlay . </p> </td> 
   <td> Oui </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> errorFormat</span> </td> 
   <td>Soit <span class="codeph"> html</span> ou <span class="codeph"> json</span>. If <span class="codeph"> html</span> (valeur par défaut) une représentation par HTML des erreurs est fournie dans le corps de l’entité de la réponse. <p>If <span class="codeph"> json</span> est spécifiée, une réponse structurée au format JSON est renvoyée. Voir <a href="https://www.expressplay.com/developer/restapi/#json-errors" format="html" scope="external"> Erreurs JSON</a> pour plus d’informations. </p> <p>Le type MIME de la réponse est : <span class="codeph"> text/uri-list</span> en cas de succès, <span class="codeph"> text/html</span> pour le format d’erreur de HTML, ou <span class="codeph"> application/json</span> pour le format d’erreur JSON. </p> </td> 
   <td> Non </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 10 : Paramètres de requête de licence**

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
   <td>Chaîne hexadécimale de 4 octets représentant les indicateurs de licence. Il doit être défini sur "00000001" pour une licence persistante. <p>Remarque : Licences de location (<span class="codeph"> rightsType=Rental</span>) DOIT être persistant. </p> </td> 
   <td> Non </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> kek</span> </td> 
   <td> Clé de chiffrement de clé (KEK). Les clés sont stockées cryptées avec une clé à l’aide d’un algorithme d’encapsulage de clé (AES Key Wrap, RFC3394). </td> 
   <td> Non </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> gamin</span> </td> 
   <td>Représentation sous forme de chaîne hexadécimale de 16 octets de la clé de chiffrement du contenu ou d’une chaîne <span class="codeph"> ^somestring'</span>. La longueur de la chaîne suivie du caractère "^" ne peut pas être supérieure à 64 caractères. </td> 
   <td> Oui </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> ek</span> </td> 
   <td> Représentation sous forme de chaîne hexadécimale de la clé de contenu chiffrée. </td> 
   <td> Non </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> contentKey</span> </td> 
   <td> Une représentation sous forme de chaîne hexadécimale de 16 octets de la clé de chiffrement du contenu </td> 
   <td>Oui, sauf si <span class="codeph"> kek</span> et <span class="codeph"> ek</span> ou <span class="codeph"> gamin</span> sont fournies ; </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> rightsType</span> </td> 
   <td>Indique le type de droits. Doit être <span class="codeph"> BuyToOwn</span> ou <span class="codeph"> location</span>. </td> 
   <td> Oui </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> location.periodEndTime</span> </td> 
   <td>Date de fin de la location. Cette valeur DOIT être au format "RFC 3339" _ date/heure au format "Z" zone designator ("Zulu time") , ou un entier précédé d'un signe "+". <p>Si la valeur est une <a href="https://www.ietf.org/rfc/rfc3339.txt" format="html" scope="external"> RFC 3339</a> format date/heure, puis représente une date/heure d’expiration absolue pour la licence. Exemple de date/heure RFC 3339 : 2006-04-14T12:01:10Z. </p> <p> Si la valeur est un entier précédé d’un signe "+", il s’agit d’un nombre relatif de secondes à partir du moment où le jeton est émis. Le contenu ne peut plus être lu après cette période. Valide uniquement si <span class="codeph"> rightsType</span> is <span class="codeph"> location</span>. </p> </td> 
   <td>Oui, lorsque <span class="codeph"> rightsType</span> is <span class="codeph"> location</span>. </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> location.playDuration</span> </td> 
   <td>Temps, en secondes, pendant lequel le contenu peut être lu une fois la lecture démarrée. Valide uniquement si <span class="codeph"> rightsType</span> est louée. </td> 
   <td> Non </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> analogVideoOPL</span> </td> 
   <td> Valeur entière pour indiquer le niveau de protection de sortie pour la vidéo analogique. Plage valide 0-999. </td> 
   <td> Oui </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> compresséDigitalAudioOPL</span> </td> 
   <td> Valeur entière pour indiquer le niveau de protection de sortie pour l’audio numérique compressé. Plage valide 0-999. </td> 
   <td> Oui </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> compresséDigitalVideoOPL</span> </td> 
   <td> Valeur entière pour indiquer le niveau de protection de sortie pour la vidéo numérique compressée. Plage valide 0-999. </td> 
   <td> Oui </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> uncompresséDigitalAudioOPL</span> </td> 
   <td> Valeur entière pour indiquer le niveau de protection de sortie pour le contenu audio numérique non compressé. Plage valide 0-999. </td> 
   <td> Oui </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> uncompresséDigitalVideoOPL</span> </td> 
   <td> Valeur entière pour indiquer le niveau de protection de sortie pour la vidéo numérique non compressée. Plage valide 0-999. </td> 
   <td> Oui </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> unknownOutputBehavior</span> </td> 
   <td>Comportement requis lorsque la sortie est inconnue. Valeurs autorisées : <span class="codeph"> Autoriser</span>, <span class="codeph"> Ne pas autoriser</span> ou <span class="codeph"> SDOnly</span> </td> 
   <td> Non </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> outputControlFlags</span> </td> 
   <td> Valeur hexadécimale de 4 octets pour indiquer les indicateurs des autres options de contrôle de sortie </td> 
   <td> Non </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> extensionType</span> </td> 
   <td>Un mot arbitraire de 4 lettres représentant un identifiant 32 bits pour une extension. Le code ASCII 8 bits de chaque lettre est la partie 8 bits correspondante de l’identifiant. Par exemple, la valeur de l’identifiant 0x61626364 (hexadécimal) serait "<span class="codeph"> abcd</span>", car le code ASCII pour "a" est 0x61, etc. </td> 
   <td> Non </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> extensionPayload</span> </td> 
   <td> Chaîne codée en base64 de l’extension. </td> 
   <td>Oui, lorsque <span class="codeph"> extensionType</span> est spécifié. </td> 
  </tr> 
 </tbody> 
</table>

## Réponses {#section_0079C31B4AF14DBBB6277CF251FB90E3}

**Tableau 11 : Réponses HTTP**

| **Code d’état HTTP** | **Description** | **Content-Type** | **Le corps d’entité contient** |
|---|---|---|---|
| `200 OK` | Aucune erreur. | `text/uri-list` | URL et jeton d’acquisition de licence |
| `400 Bad Request` | Arguments non valides | `text/html` ou `application/json` | Description de l’erreur |
| `401 Unauthorized` | Échec de l’authentification | `text/html` ou `application/json` | Description de l’erreur |
| `404 Not found` | URL incorrecte | `text/html` ou `application/json` | Description de l’erreur |
| `50x Server Error` | Erreur du serveur | `text/html` ou `application/json` | Description de l’erreur |

**Tableau 12 : Codes d’erreur des événements**

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
   <td>Jeton d’authentification non valide : &lt;details&gt; <p>Remarque : Cela peut se produire si l’authentificateur est incorrect ou lors de l’accès à l’API de test à l’adresse *.test.expressplay.com à l’aide de l’authentificateur de production et vice versa. </p> <p importance="high">Remarque : Le SDK Test et l’outil de test avancé fonctionnent uniquement avec <span class="filepath"> *.test.expressplay.com</span>, tandis que les appareils de production doivent utiliser <span class="filepath"> *.service.expressplay.com</span>. </p> </td> 
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
   <td><span class="codeph"> OutputControlFlag</span> doit être encodé 4 octets </td> 
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
   <td> -4018 </td> 
   <td>Absente <span class="codeph"> gamin</span> </td> 
  </tr> 
  <tr> 
   <td> -4019 </td> 
   <td> Échec de l’obtention de la clé de contenu à partir du service de stockage clé </td> 
  </tr> 
  <tr> 
   <td> -4020 </td> 
   <td><span class="codeph"> gamin</span> doit comporter 32 caractères hexadécimaux </td> 
  </tr> 
  <tr> 
   <td> -4021 </td> 
   <td><span class="codeph"> gamin</span> doit comporter 64 caractères après le ^ </td> 
  </tr> 
  <tr> 
   <td> -4022 </td> 
   <td>Non valide <span class="codeph"> gamin</span> </td> 
  </tr> 
  <tr> 
   <td> -4024 </td> 
   <td>Chiffrement non valide <span class="codeph"> key</span> ou kek </td> 
  </tr> 
  <tr> 
   <td> -5001 </td> 
   <td> Erreur de type de sortie inconnu non valide </td> 
  </tr> 
  <tr> 
   <td> -5002 </td> 
   <td> L’option PlayReady est désactivée pour ce service. </td> 
  </tr> 
  <tr> 
   <td> -5003 </td> 
   <td> Indicateurs généraux non valides </td> 
  </tr> 
  <tr> 
   <td> -5004 </td> 
   <td> L’identifiant de l’appareil doit comporter 32 caractères hexadécimaux. </td> 
  </tr> 
  <tr> 
   <td> -5005 </td> 
   <td> ID d’appareil non valide </td> 
  </tr> 
  <tr> 
   <td> -5006 </td> 
   <td> Valeur OPL manquante </td> 
  </tr> 
  <tr> 
   <td> -5007 </td> 
   <td>Un seul de <span class="codeph"> kek</span> ou <span class="codeph"> contentKey</span> peut être spécifié </td> 
  </tr> 
 </tbody> 
</table>
