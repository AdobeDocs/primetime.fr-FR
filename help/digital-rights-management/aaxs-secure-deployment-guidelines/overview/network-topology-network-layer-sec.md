---
seo-title: Sécurité de la couche réseau
title: Sécurité de la couche réseau
uuid: bd53bccf-1130-4189-97ec-4259bd25762f
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Sécurité de la couche réseau{#network-layer-security}

Les vulnérabilités de sécurité réseau sont parmi les premières menaces à l’encontre de tout serveur d’applications orienté Internet ou intranet. Cette section décrit le processus de renforcement des hôtes sur le réseau contre ces vulnérabilités. Il traite de la segmentation du réseau, du renforcement de la pile TCP/IP (Transmission Control Protocol/Internet Protocol) et de l’utilisation de pare-feu pour la protection de l’hôte.

Ce tableau décrit les techniques courantes qui réduisent les vulnérabilités de sécurité réseau.

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table-djf-lhz-n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Technique </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Description </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Zones démilitarisées </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">La segmentation doit exister à au moins deux niveaux avec le serveur d’applications utilisé pour exécuter Adobe Access placé derrière le pare-feu interne. Séparez le réseau externe de la zone démilitarisée qui contient les serveurs Web, lesquels doivent à leur tour être séparés du réseau interne. Utilisez des pare-feu pour implémenter les couches de séparation. Classez et contrôlez le trafic qui passe par chaque couche réseau pour vous assurer que seul le minimum absolu de données requises est autorisé. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Adresses IP privées </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Utilisez la traduction d’adresses réseau (NAT) avec des adresses IP privées RFC 1918 sur les serveurs d’applications Adobe Access. Attribuez des adresses IP privées (10.0.0.0/8, 172.16.0.0/12 et 192.168.0.0/16) pour rendre plus difficile l’acheminement du trafic vers et depuis un hôte interne NAT via Internet. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Pare-feu </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Utilisez les critères suivants pour sélectionner une solution de pare-feu : </p> <p class="- topic/p "> 
     <ul class="- topic/ul " id="ul-wjf-lhz-n4"> 
      <li class="- topic/li " id="li-8031632160F44037B092988183139202"> <p class="- topic/p ">Mettez en oeuvre des pare-feu qui prennent en charge les serveurs proxy et/ou l’inspection avec état au lieu de solutions simples de filtrage de paquets. </p> </li> 
      <li class="- topic/li " id="li-B65CBB92113E4503B79EB194C34FCA50"> <p class="- topic/p ">Utilisez un pare-feu qui prend en charge un paradigme de sécurité dans lequel vous pouvez refuser tous les services sauf ceux explicitement autorisés. </p> </li> 
      <li class="- topic/li " id="li-5CE4C7B65D84410DB4BE966FD8922993"> <p class="- topic/p ">Implémentez une solution de pare-feu à double hébergement ou à plusieurs hébergements. Cette architecture offre un niveau de sécurité optimal et permet d'empêcher les utilisateurs non autorisés de contourner la sécurité du pare-feu. </p> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

