---
description: Lorsque vous configurez une architecture réseau sécurisée, des protocoles réseau sont requis pour l’interaction entre Adobe Primetime DRM et d’autres systèmes du réseau de votre entreprise.
seo-description: Lorsque vous configurez une architecture réseau sécurisée, des protocoles réseau sont requis pour l’interaction entre Adobe Primetime DRM et d’autres systèmes du réseau de votre entreprise.
seo-title: Protocoles réseau DRM Adobe Primetime
title: Protocoles réseau DRM Adobe Primetime
uuid: 8954e33c-83ac-4b40-9e45-005d4954b44e
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---


# Protocoles réseau DRM Adobe Primetime {#adobe-primetime-drm-network-protocols}

Lorsque vous configurez une architecture réseau sécurisée, des protocoles réseau sont requis pour l’interaction entre Adobe Primetime DRM et d’autres systèmes du réseau de votre entreprise.

Lorsque vous configurez une architecture réseau sécurisée, les protocoles réseau suivants sont requis pour cette interaction :

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_itc_33z_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Protocole </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Utiliser </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">HTTP </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Les clients Flash Player, Adobe AIR® et Adobe Primetime communiquent avec Primetime DRM via HTTP. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">HTTPS (facultatif) </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Les clients Flash Player, Adobe AIR et Adobe Primetime peuvent utiliser HTTPS pour communiquer avec Primetime DRM ; HTTPS (SSL) n’est pas requis à moins que vous ne preniez en charge les clients FMRMS 1.x. Pour plus d’informations, voir <a href="../../secure-deployment-guidelines/overview/network-topology-firewall-rules.md" format="dita" scope="local"> URL entrantes </a> et Configuration de SSL. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Ports des serveurs d’applications {#ports-for-application-servers}

Vous pouvez configurer le serveur de licences DRM Adobe Primetime pour utiliser n’importe quel port réseau.

Ces ports doivent être activés ou désactivés sur le pare-feu interne, selon la fonctionnalité réseau que vous souhaitez autoriser pour les clients qui se connectent au serveur d’applications qui exécute Primetime DRM.

## Configuration de SSL {#configuring-ssl}

Le protocole SSL (Secure Sockets Layer) n’est nécessaire que si vous avez besoin de la prise en charge des clients Flash Media Rights Management Server 1.x.

SSL avec authentification du client est requis pour le serveur de clés DRM Adobe Primetime. Pour plus d’informations, voir [Utilisation du serveur de clés DRM Adobe Primetime](../../using-the-drm-key-server/requirements.md).