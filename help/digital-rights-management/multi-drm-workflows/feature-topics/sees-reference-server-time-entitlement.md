---
description: Consultez le site SEES pour savoir comment activer un service de droits basé sur le temps à l’aide d’ExpressPlay.
seo-description: Consultez le site SEES pour savoir comment activer un service de droits basé sur le temps à l’aide d’ExpressPlay.
seo-title: Droits basés sur le temps du service de référence
title: Droits basés sur le temps du service de référence
uuid: dd937299-a271-49a9-9b26-eec16f1484df
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c

---


# Service de référence : Droits basés sur le temps {#reference-service-time-based-entitlement}

Consultez le site SEES pour savoir comment activer un service de droits basé sur le temps à l’aide d’ExpressPlay.

Le SEES reçoit une demande de droits (voir la section API publique) du client. Le serveur SEES recherche le CEK et le IV en fonction du `contentID`, ajoute le `expirationTime`et transfère la requête au serveur ExpressPlay. Le jeton ExpressPlay final est lié au temps. Voir le diagramme de séquence des droits temporels ci-dessous. ![](assets/fees-time-based.png)

**Tableau 1 : Paramètres de licence envoyés par le client**

| Paramètre  | Description | Obligatoire |
|---|---|---|
| `contentKey` | Une chaîne hexadécimale de 16 octets représentant la clé de chiffrement du contenu | Oui |
| `iv` | Une chaîne hexadécimale de 16 octets représentant le chiffrement de contenu IV | Oui |
| `rentalDuration` | Durée de la location en secondes (par défaut = 0) | Non |

**Tableau 2 : Paramètres de restriction de jeton ajoutés par le serveur SEES**

<table id="table_E979FAD7A61A4832A46667301939FAEB">  
 <thead> 
  <tr> 
   <th class="entry"> Paramètre  </th> 
   <th class="entry"> Description </th> 
   <th class="entry"> Obligatoire ? </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td><span class="codeph"> expirationTime</span> </td> 
   <td>Heure d’expiration de ce jeton. Cette valeur doit être une chaîne au format <a href="https://www.ietf.org/rfc/rfc3339.txt" format="html" type="external"> RFC 3339</a> date/heure dans l’indicateur de zone 'Z' ("heure Zulu"), ou un entier précédé d’un signe "+". Un exemple de date/heure RFC 3339 est le <span class="codeph"> 2006-04-14T12:01:10Z</span>. <p>Si la valeur est une chaîne au format date/heure RFC 3339, elle représente une date/heure d’expiration absolue pour le jeton. Si la valeur est un nombre entier précédé d’un signe "+", le nombre de secondes écoulées depuis l’émission indique que le jeton est valide. Par exemple, <span class="codeph"> +60</span> indique une minute. La durée de vie maximale (et par défaut, si elle n’est pas spécifiée) du jeton est de 30 jours. Utilisez le formulaire codé "%2B" lors de la spécification du signe "+". </p> </td> 
   <td> Non </td> 
  </tr> 
 </tbody> 
</table>

