---
seo-title: Contrôles de protection de sortie
title: Contrôles de protection de sortie
uuid: 1f4cc617-7f14-4952-8e61-6acbdf01d10e
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---


# Contrôles de protection de sortie {#output-protection-controls}

**Contrôle si la sortie sur les périphériques de rendu externes est protégée. Spécifiez des sorties analogiques et numériques indépendamment.**

Contrôle si la sortie sur les périphériques de rendu externes doit être restreinte. Un périphérique externe est défini comme tout périphérique vidéo ou audio qui n’est pas incorporé à l’ordinateur. La liste des périphériques externes exclut les écrans intégrés, tels que ceux des ordinateurs portables. Les restrictions de sortie analogique et numérique peuvent être spécifiées indépendamment.

Les options/niveaux d&#39;application suivants sont disponibles :

<table frame="all" colsep="0" rowsep="1" id="adobetable_fvw_5fx_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Option </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Pris en charge sur les périphériques analogiques </p> </th> 
   <th colname="3" class="- topic/entry entry"> <p class="- topic/p ">Pris en charge sur les périphériques numériques </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Obligatoire</b> — Protection de la copie analogique (ACP) ou Système de gestion de la génération de copies - La protection de sortie analogique (CGMS-A) doit être activée pour lire le contenu sur un périphérique externe. Les clients d'Accès à l'Adobe doivent activer la protection de la sortie en utilisant le PVA ou le CGMS-A. Sur les périphériques qui prennent en charge les deux, les clients Adobe Access 3.0 tentent d'activer les deux. Cependant, un seul doit être activé pour lire le contenu. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">PVA requis</b> — La protection de la sortie PVA est requise. La lecture n'est pas autorisée sur CGMS-A. Les clients Adobe Access 2.0 ne prennent pas en charge cette option. Si elle est définie, un client Adobe Access 2.0 se comporte comme si l'option "Aucune lecture" était spécifiée. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">CGMS-A Obligatoire</b> — CGMS-A La protection de sortie est requise. La lecture n'est pas autorisée sur ACP. Les clients Adobe Access 2.0 ne prennent pas en charge cette option. Si elle est définie, un client Adobe Access 2.0 se comporte comme si l'option "Aucune lecture" était spécifiée. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Utiliser si disponible</b> : tentez d'activer la protection de sortie ACP et CGMS-A si disponible et d'autoriser la lecture si elle n'est pas disponible. Si possible, les clients d'Adobe Access 3.0 tenteront d'activer à la fois le PVA et le CGMS-A. Les clients d'Adobe Access 2.0 ne feront qu'essayer d'activer le PVA ou le CGMS-A. Par exemple, le client Adobe Access tentera d'activer le PVA ou le CGMS-A. Si la tentative réussit, l’autre option ne sera pas activée. Si la tentative échoue, une deuxième tentative est effectuée pour activer l’autre option. Même si les deux tentatives échouent, le contenu sera de toute façon lu. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Utiliser ACP si disponible</b> : tentez d'activer la protection de sortie ACP si disponible, mais autorisez la lecture si elle n'est pas disponible. La protection n'est pas disponible sur CGMS-A. Les clients Adobe Access 2.0 ne prennent pas en charge cette option. S'il est défini, un client Adobe Access 2.0 se comporte comme si l'option "Aucune protection" était spécifiée. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Utilisez CGMS-A si disponible </b>— Tentez d'activer la protection de sortie CGMS-A si disponible, mais autorisez la lecture si elle n'est pas disponible. La protection n'est pas disponible sur ACP. Les clients Adobe Access 2.0 ne prennent pas en charge cette option. S'il est défini, un client Adobe Access 2.0 se comporte comme si l'option "Aucune protection" était spécifiée. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Aucune protection</b> : aucune activation de la protection de sortie n’est appliquée pour les sorties analogiques et numériques. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Aucune lecture</b> : n’autorisez pas la lecture sur un périphérique externe pour les sorties analogiques et numériques. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Bien que ces règles soient appliquées de manière cohérente sur toutes les plates-formes, il n’est actuellement possible d’activer la protection de sortie en toute sécurité que sur les plates-formes Windows. Sur d’autres plates-formes (telles que Macintosh et Linux), aucune fonction de système d’exploitation compatible n’est disponible pour les applications tierces.

Exemple de cas d’utilisation : Certains contenus peuvent imposer des contrôles de protection de sortie et le niveau de protection peut être défini par le distributeur de contenu. Si &quot;Obligatoire&quot; est spécifié et que la lecture est tentée sur un Macintosh, le client ne lit pas le contenu sur des périphériques externes. Le contenu sera toutefois lu sur les moniteurs internes.

Si &quot;Obligatoire&quot; est spécifié et que la lecture est tentée sous Linux, le client ne lit pas le contenu sur aucun périphérique, car il n’est pas possible de différencier les périphériques internes et externes.

Si vous spécifiez &quot;Utiliser si disponible&quot;, la protection de sortie est activée lorsque cela est possible. Par exemple, sur les ordinateurs Windows qui prennent en charge le protocole COPP (Certified Output Protection Protocol), le contenu est transmis avec protection de sortie à un affichage externe. Cet exemple est parfois appelé &quot;contrôle de sortie sélectionnable&quot;.
