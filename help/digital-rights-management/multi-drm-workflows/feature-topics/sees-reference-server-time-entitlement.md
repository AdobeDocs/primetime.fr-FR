---
description: Travaillez avec le SEES pour voir comment activer un service de droits basé sur le temps à l’aide d’ExpressPlay.
title: Droit basé sur le temps du service de référence
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Service de référence : droit basé sur le temps {#reference-service-time-based-entitlement}

Travaillez avec le SEES pour voir comment activer un service de droits basé sur le temps à l’aide d’ExpressPlay.

Le SEES reçoit une demande de droit (voir la section API publique ) du client. Le serveur SEES recherche le CEK et l’ID en fonction de la variable `contentID`, ajoute la variable `expirationTime`et transfère la demande au serveur ExpressPlay. Le jeton ExpressPlay final est lié au temps. Consultez le diagramme de séquence de droits en fonction du temps ci-dessous. ![](assets/fees-time-based.png)

**Tableau 1 : Paramètres de licence envoyés par le client**

| Paramètre de requête | Description | Obligatoire |
|---|---|---|
| `contentKey` | Une représentation sous forme de chaîne hexadécimale de 16 octets de la clé de chiffrement du contenu | Oui |
| `iv` | Une représentation sous forme de chaîne hexadécimale de 16 octets du chiffrement de contenu IV | Oui |
| `rentalDuration` | Durée de la location en secondes (par défaut = 0) | Non |

**Tableau 2 : Paramètres de restriction des jetons ajoutés par le serveur SEES**

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
   <td>Expiration de ce jeton. Cette valeur doit être une chaîne dans <a href="https://www.ietf.org/rfc/rfc3339.txt" format="html" type="external"> RFC 3339</a> format de date/heure dans l’indicateur de zone "Z" ("heure zoulou"), ou un entier précédé d’un signe "+". Exemple de date/heure RFC 3339 : <span class="codeph"> 2006-04-14T12:01:10Z</span>. <p>Si la valeur est une chaîne au format date/heure RFC 3339, elle représente une date/heure d’expiration absolue pour le jeton. Si la valeur est un entier précédé d’un signe "+", il est interprété comme un nombre relatif de secondes à partir de l’émission, indiquant que le jeton est valide. Par exemple : <span class="codeph"> +60</span> spécifie une minute. La durée de vie maximale du jeton (et par défaut, si elle n’est pas spécifiée) est de 30 jours. Utilisez le formulaire codé "%2B" lors de la spécification du signe "+". </p> </td> 
   <td> Non </td> 
  </tr> 
 </tbody> 
</table>
