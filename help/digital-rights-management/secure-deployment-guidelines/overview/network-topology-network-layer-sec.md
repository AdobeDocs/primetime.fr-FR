---
description: Les vulnérabilités de sécurité réseau sont parmi les premières menaces à l'encontre des serveurs d'applications orientés Internet ou intranet, et vous devez protéger les hôtes du réseau contre ces vulnérabilités.
seo-description: Les vulnérabilités de sécurité réseau sont parmi les premières menaces à l'encontre des serveurs d'applications orientés Internet ou intranet, et vous devez protéger les hôtes du réseau contre ces vulnérabilités.
seo-title: Sécurité de la couche réseau
title: Sécurité de la couche réseau
uuid: c750c595-a784-47ce-be0b-17b8d60c5753
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Sécurité de la couche réseau{#network-layer-security}

Les vulnérabilités de sécurité réseau sont parmi les premières menaces à l&#39;encontre des serveurs d&#39;applications orientés Internet ou intranet, et vous devez protéger les hôtes du réseau contre ces vulnérabilités.

Voici quelques techniques courantes qui réduisent les vulnérabilités de sécurité réseau :

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_djf_lhz_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Technique </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Description </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Zones démilitarisées </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">La segmentation doit exister à au moins deux niveaux avec le serveur d’applications utilisé pour exécuter Adobe Primetime DRM lorsque Primetime DRM se trouve derrière le pare-feu interne. Vous devez séparer le réseau externe de la zone démilitarisée qui comprend les serveurs Web et les serveurs Web du réseau interne. Vous pouvez utiliser des pare-feu pour implémenter ces couches de séparation. </p> <p>Vous pouvez classer et contrôler le trafic qui passe par chaque couche réseau pour vous assurer que seul le minimum absolu de données requises est autorisé. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Adresses IP privées </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Utilisez le NAT (Network Address Translation) avec des adresses IP privées RFC 1918 sur les serveurs d’applications DRM Primetime. Vous pouvez attribuer des adresses IP privées (10.0.0.0/8, 172.16.0.0/12 et 192.168.0.0/16) pour rendre plus difficile pour un attaquant d’acheminer le trafic vers et depuis un hôte interne NAT via Internet. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Pare-feu </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Voici quelques critères à prendre en compte lors de la sélection d’une solution de pare-feu : </p> <p class="- topic/p "> 
     <ul class="- topic/ul " id="ul_wjf_lhz_n4"> 
      <li class="- topic/li " id="li_A620D0B635384590BA7804F9720D04D0">Mettez en oeuvre des pare-feu qui prennent en charge les serveurs proxy et/ou l’inspection avec état, au lieu de solutions simples de filtrage de paquets. </li> 
      <li class="- topic/li " id="li_3E4F814A30C047539185C23F4F57C282">Utilisez un pare-feu qui prend en charge un paradigme de sécurité dans lequel vous pouvez refuser tous les services, à l’exception des services explicitement autorisés. </li> 
      <li class="- topic/li " id="li_96160B3F14C4425397F017AF93FABE32">Implémentez une solution de pare-feu à double hébergement ou à plusieurs hébergements. Cette architecture offre un niveau de sécurité optimal et empêche les utilisateurs non autorisés de contourner la sécurité du pare-feu. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

