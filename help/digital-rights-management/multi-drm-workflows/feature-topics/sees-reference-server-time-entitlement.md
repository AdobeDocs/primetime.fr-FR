---
description: Consultez le site SEES pour savoir comment activer un service de droits temporels à l'aide d'ExpressPlay.
title: Droits basés sur le temps du service de référence
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---


# Service de référence : Droit fondé sur le temps {#reference-service-time-based-entitlement}

Consultez le site SEES pour savoir comment activer un service de droits temporels à l&#39;aide d&#39;ExpressPlay.

Le SEES reçoit une demande de droits (voir la section API publique) du client. Le serveur SEES recherche le CEK et IV en fonction de `contentID`, ajoute le `expirationTime` et transfère la requête au serveur ExpressPlay. Le jeton final ExpressPlay est lié au temps. Voir le diagramme de séquence de droits temporels ci-dessous. ![](assets/fees-time-based.png)

**Tableau 1 : Paramètres de licence envoyés par le client**

| Paramètre de requête | Description | Obligatoire |
|---|---|---|
| `contentKey` | Représentation d’une chaîne hexadécimale de 16 octets de la clé de chiffrement du contenu | Oui |
| `iv` | Une représentation de chaîne hexadécimale de 16 octets du chiffrement de contenu IV | Oui |
| `rentalDuration` | Durée de la location en secondes (par défaut = 0) | Non |

**Tableau 2 : Paramètres de restriction de jeton ajoutés par le serveur SEES**

<table id="table_E979FAD7A61A4832A46667301939FAEB">  
 <thead> 
  <tr> 
   <th class="entry"> Paramètre de requête </th> 
   <th class="entry"> Description </th> 
   <th class="entry"> Obligatoire ? </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td><span class="codeph"> expirationTime</span> </td> 
   <td>Heure d’expiration de ce jeton. Cette valeur doit être une chaîne au format de date/heure <a href="https://www.ietf.org/rfc/rfc3339.txt" format="html" type="external"> RFC 3339</a> dans l'indicateur de zone 'Z' ("heure Zulu"), ou un entier précédé d'un signe '+'. Un exemple de date/heure RFC 3339 est <span class="codeph"> 2006-04-14T12:01:10Z</span>. <p>Si la valeur est une chaîne au format date/heure RFC 3339, elle représente une date/heure d’expiration absolue pour le jeton. Si la valeur est un entier précédé d’un signe "+", le jeton est interprété comme un nombre relatif de secondes après l’émission. Par exemple, <span class="codeph"> +60</span> spécifie une minute. La durée de vie maximale (et par défaut, si elle n’est pas spécifiée) du jeton est de 30 jours. Utilisez le formulaire codé "%2B" lors de la spécification du signe "+". </p> </td> 
   <td> Non </td> 
  </tr> 
 </tbody> 
</table>

