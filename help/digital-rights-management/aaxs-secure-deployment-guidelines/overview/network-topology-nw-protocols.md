---
title: Protocoles réseau utilisés par Adobe Access
description: Protocoles réseau utilisés par Adobe Access
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---


# Protocoles réseau utilisés par Adobe Access {#network-protocols-used-by-adobe-access}

Lorsque vous configurez une architecture réseau sécurisée, les protocoles réseau du tableau suivant sont requis pour l&#39;interaction entre Adobe Access et d&#39;autres systèmes du réseau de votre entreprise.

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table-itc-33z-n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Protocole </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Utiliser </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">HTTP </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Les clients Flash Player, Adobe AIR® et Adobe Primetime communiquent avec Adobe Access via HTTP. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">HTTPS (facultatif) </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Les clients Flash Player, Adobe AIR et Adobe Primetime peuvent utiliser le protocole HTTPS pour communiquer avec Adobe Access. Cependant, le protocole HTTPS (SSL) n’est pas requis, sauf si vous avez besoin de prise en charge des clients FMRMS 1.x. Consultez les notes du tableau <a href="network-topology-firewall-rules.md" format="dita" scope="local"> URL entrantes</a> et <a href="network-topology-nw-protocols.md"> Configuration de SSL</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>