---
seo-title: Contrôles de protection de sortie
title: Contrôles de protection de sortie
uuid: 1f4cc617-7f14-4952-8e61-6acbdf01d10e
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c

---


# Contrôles de protection de sortie {#output-protection-controls}

**Contrôle si la sortie vers des périphériques de rendu externes est protégée. Spécifiez des sorties analogiques et numériques indépendamment.**

Contrôle si la sortie vers des périphériques de rendu externes doit être restreinte. Un périphérique externe est défini comme tout périphérique vidéo ou audio qui n’est pas incorporé à l’ordinateur. Le  des périphériques externes exclut les écrans intégrés, tels que les ordinateurs portables. Les restrictions de sortie analogique et numérique peuvent être spécifiées indépendamment.

Les options/niveaux d’application suivants sont disponibles :

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
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Obligatoire</b> — La protection de sortie analogique (ACP) ou Copier le système de gestion de génération - La protection de sortie analogique (CGMS-A) doit être activée pour que le contenu soit lu sur un périphérique externe. Les clients Adobe Access doivent activer la protection de sortie à l’aide d’ACP ou de CGMS-A. Sur les périphériques prenant en charge les deux, les clients Adobe Access 3.0 tentent d'activer les deux. Cependant, un seul doit être activé pour lire le contenu. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">ACP requis</b> — Une protection de sortie ACP est requise. La lecture n’est pas autorisée sur CGMS-A. Les clients Adobe Access 2.0 ne prennent pas en charge cette option. S’il est défini, un client Adobe Access 2.0 se comporte comme si l’option "Aucune lecture" était spécifiée. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">CGMS-A Obligatoire</b> — La protection de sortie CGMS-A est requise. La lecture n’est pas autorisée sur ACP. Les clients Adobe Access 2.0 ne prennent pas en charge cette option. S’il est défini, un client Adobe Access 2.0 se comporte comme si l’option "Aucune lecture" était spécifiée. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Utiliser si disponible</b> — Tentez d’activer la protection de sortie ACP et CGMS-A si disponible et autorisez la lecture si elle n’est pas disponible. Si possible, les clients Adobe Access 3.0 tenteront d'activer à la fois ACP et CGMS-A. Les clients Adobe Access 2.0 tenteront uniquement d'activer ACP ou CGMS-A. Par exemple, le client Adobe Access tentera d’activer ACP ou CGMS-A. Si la tentative réussit, l’autre option ne sera pas activée. Si la tentative échoue, une seconde tentative est effectuée pour activer l’autre option. Même si les deux tentatives échouent, le contenu sera tout de même lu. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Utiliser le PVA si disponible</b> — Tentez d’activer la protection de sortie ACP si elle est disponible, mais autorisez la lecture si elle n’est pas disponible. La protection n'est pas disponible sur CGMS-A. Les clients Adobe Access 2.0 ne prennent pas en charge cette option. S’il est défini, un client Adobe Access 2.0 se comporte comme si l’option "Aucune protection" était spécifiée. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Utiliser CGMS-A si disponible </b>— Tentez d’activer la protection de sortie CGMS-A si disponible, mais autorisez la lecture si elle n’est pas disponible. La protection n'est pas disponible sur ACP. Les clients Adobe Access 2.0 ne prennent pas en charge cette option. S’il est défini, un client Adobe Access 2.0 se comporte comme si l’option "Aucune protection" était spécifiée. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">OUI </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Aucune protection</b> — Aucune activation de la protection de sortie n’est appliquée pour les sorties analogiques et numériques. </p> </td> 
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

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Bien que ces règles soient appliquées de manière cohérente sur toutes les plates-formes, il n’est actuellement possible d’activer la protection de sortie en toute sécurité que sur les plates-formes Windows. Sur d’autres plateformes (telles que Macintosh et Linux), aucune fonction de système d’exploitation n’est disponible pour les applications tierces.

Exemple de cas d’utilisation : Certains contenus peuvent imposer des contrôles de protection de sortie et le niveau de protection peut être défini par le distributeur de contenu. Si l’option &quot;Obligatoire&quot; est spécifiée et que la lecture est tentée sur un Macintosh, le client ne lit pas le contenu sur des périphériques externes. Le contenu sera toutefois lu sur les moniteurs internes.

Si l’option &quot;Obligatoire&quot; est spécifiée et que la lecture est tentée sous Linux, le client ne lit aucun contenu sur aucun périphérique, car il n’est pas possible de différencier les périphériques internes et externes.

Si vous spécifiez &quot;Utiliser si disponible&quot;, la protection de sortie est activée lorsque cela est possible. Par exemple, sur les ordinateurs Windows qui prennent en charge le protocole COPP (Certified Output Protection Protocol), le contenu est transmis avec protection de sortie à un affichage externe. Cet exemple est parfois appelé &quot;contrôle de sortie sélectionnable&quot;.
