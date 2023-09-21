---
title: Configuration des préférences - Aperçu
description: Configuration des préférences - Aperçu
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# Configuration des préférences - Aperçu {#setting-preferences-overview}

À l’exception de l’URL du serveur Packager, toutes les préférences spécifiées ci-dessous sont stockées dans la variable [!DNL flashaccess-refimpl-packager.properties] sur le serveur. Tous les paramètres peuvent être modifiés directement dans le fichier de propriétés ou via l’application AIR. Les mots de passe sont chiffrés lorsqu’ils sont stockés dans le fichier de propriétés du serveur. Saisissez le mot de passe non chiffré dans l’interface utilisateur. Il sera chiffré avant d’être stocké dans le fichier.

>[!NOTE]
>
>Tous les répertoires et chemins d’accès se rapportent aux répertoires du serveur de package, et non au client exécutant l’application AIR.

Toutes les modifications apportées ici prennent effet immédiatement une fois les préférences enregistrées. Il n’est pas nécessaire de redémarrer le serveur, sauf si le thread de Packager s’est arrêté en raison de problèmes de configuration.

Les descriptions de préférences utilisent les termes suivants :

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_tj5_hcz_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> Préférence </th> 
   <th colname="2" class="- topic/entry entry"> Description </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> URL du serveur de paquets </td> 
   <td colname="2" class="- topic/entry "> Emplacement du serveur en cours d’exécution <span class="filepath"> flashaccess-packager.war </span>; par exemple, <span class="filepath"> https://localhost:8080 </span> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> Répertoire de ressources </td> 
   <td colname="2" class="- topic/entry "> Répertoire contenant les stratégies, les certificats, les informations d’identification et toute autre ressource requise pour le serveur de package </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> URL du serveur de licences </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URL du serveur à partir duquel le client doit demander une licence ; par exemple, <span class="filepath"> https://mylicenseserver.com:8080 </span> </p> </td> 
  </tr> 
 </tbody> 
</table>
