---
title: Contrôles de protection de sortie
description: Contrôles de protection de sortie
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---

# Contrôles de protection de sortie {#output-protection-controls}

**Permet de contrôler si la sortie vers les périphériques de rendu externes est protégée. Spécifiez indépendamment les sorties analogique et numérique.**

Contrôle si la sortie vers les périphériques de rendu externes doit être limitée. Un appareil externe est défini comme tout appareil vidéo ou audio qui n’est pas incorporé à l’ordinateur. La liste des périphériques externes exclut les affichages intégrés, tels que dans les ordinateurs portables. Les restrictions de sortie analogique et numérique peuvent être spécifiées indépendamment.

Les options/niveaux d’application suivants sont disponibles :

<table frame="all" colsep="0" rowsep="1" id="adobetable_fvw_5fx_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Option </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Pris en charge dans les appareils analogiques </p> </th> 
   <th colname="3" class="- topic/entry entry"> <p class="- topic/p ">Pris en charge dans les appareils numériques </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Obligatoire</b> — Analog Copy Protection (ACP) ou Copy Generation Management System - La protection de sortie Analog (CGMS-A) doit être activée afin de lire le contenu sur un appareil externe. Les clients Adobe Access doivent activer la protection de sortie à l'aide d'ACP ou de CGMS-A. Sur les appareils qui prennent en charge les deux, les clients Adobe Access 3.0 tenteront d’activer les deux. Toutefois, un seul doit être activé pour lire le contenu. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">ACP requis</b> — Une protection de sortie ACP est requise. La lecture n’est pas autorisée sur CGMS-A. Les clients Adobe Access 2.0 ne prennent pas en charge cette option. S’il est défini, un client Adobe Access 2.0 se comporte comme si l’option "No Playback" (Pas de lecture) était spécifiée. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">CGMS-A requis</b> — La protection de sortie CGMS-A est requise. La lecture n’est pas autorisée sur les pays ACP. Les clients Adobe Access 2.0 ne prennent pas en charge cette option. S’il est défini, un client Adobe Access 2.0 se comporte comme si l’option "No Playback" (Pas de lecture) était spécifiée. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Utilisation si disponible</b> — Essayez d’activer la protection de sortie ACP et CGMS-A si elle est disponible et autorisez la lecture si elle n’est pas disponible. Si possible, les clients Adobe Access 3.0 tenteront d’activer les composants ACP et CGMS-A. Les clients Adobe Access 2.0 ne tenteront que d'activer les composants ACP ou CGMS-A. Par exemple, le client Adobe Access tentera d'activer les fonctions ACP ou CGMS-A. Si la tentative réussit, l’autre option ne sera pas activée. Si la tentative échoue, une deuxième tentative est effectuée pour activer l’autre option. Même si les deux tentatives échouent, le contenu est lu de toute façon. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Utiliser le ACP si disponible</b> — Essayez d’activer la protection de sortie ACP si elle est disponible, mais autorisez la lecture si elle n’est pas disponible. La protection n’est pas disponible sur le CGMS-A. Les clients Adobe Access 2.0 ne prennent pas en charge cette option. S’il est défini, un client Adobe Access 2.0 se comporte comme si l’option "No Protection" (Pas de protection) était spécifiée. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Utilisez CGMS-A si disponible </b>— Essayez d’activer la protection de sortie CGMS-A si elle est disponible, mais autorisez la lecture si elle n’est pas disponible. La protection n'est pas disponible sur ACP. Les clients Adobe Access 2.0 ne prennent pas en charge cette option. S’il est défini, un client Adobe Access 2.0 se comporte comme si l’option "No Protection" (Pas de protection) était spécifiée. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Pas de protection</b> — Aucune activation de la protection de sortie n’est appliquée pour les sorties analogique et numérique. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Pas de lecture</b> : n’autorisez pas la lecture sur un appareil externe pour les sorties analogique et numérique. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Bien que ces règles soient appliquées de manière cohérente sur toutes les plateformes, il est actuellement possible d’activer la protection de sortie en toute sécurité sur les plateformes Windows. Sur d’autres plateformes (telles que Macintosh et Linux), aucune fonction de système d’exploitation compatible n’est disponible pour les applications tierces.

Exemple de cas d’utilisation : un contenu peut imposer des contrôles de protection de sortie, et le niveau de protection peut être défini par le distributeur de contenu. Si &quot;Obligatoire&quot; est spécifié et que la lecture est tentée sur un Macintosh, le client ne lit pas le contenu sur des appareils externes. Le contenu sera toutefois relu sur les moniteurs internes.

Si &quot;Obligatoire&quot; est spécifié et que la lecture est tentée sous Linux, le client ne lit le contenu sur aucun appareil, car il n’est pas possible de différencier les appareils internes et externes.

Si vous indiquez &quot;Utiliser si disponible&quot;, la protection de sortie est activée lorsque cela est possible. Par exemple, sur les ordinateurs Windows qui prennent en charge le protocole COPP (Certified Output Protection Protocol), le contenu est transmis avec protection de sortie à un affichage externe. Cet exemple est parfois appelé &quot;contrôle de sortie sélectionnable&quot;.
