---
title: Propriétés du fichier de configuration
description: Propriétés du fichier de configuration
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---


# Propriétés du fichier de configuration {#configuration-file-properties}

Avant d’exécuter le générateur de licences, spécifiez des valeurs pour les propriétés du générateur de licences. Le fichier de configuration spécifie les propriétés suivantes. Pour les noms de propriété qui incluent *n*, *n* représente un entier commençant par 1 et augmentant pour chaque instance de la propriété.

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_qk1_rry_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> Propriété </th> 
   <th colname="2" class="- topic/entry entry"> Description </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> preneur de licence segen.minClientVersion</span> </td> 
   <td colname="2" class="- topic/entry "> Définissez la version minimale du client prise en charge. Si elle n’est pas définie, toutes les versions sont prises en charge par défaut. Définissez cette valeur pour contrôler comment les clients plus âgés répondent aux exigences de licence qu’ils ne prennent pas en charge. Indiquez x (pour Accès aux Adobes x.0) où x est le numéro de version principal. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> prenesegen.keyServerCert</span> </td> 
   <td colname="2" class="- topic/entry "> Certificat de serveur de clés (certificat de serveur de licences émis par un Adobe et utilisé par le serveur de clés). Ce certificat est utilisé uniquement si les métadonnées/stratégies indiquent qu’un serveur de clés est requis pour la diffusion de clés sur les périphériques iOS. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> preneur de licence segen.sign.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> Fichier PKCS12 contenant les informations d’identification du serveur de licences pour la signature des licences. Cette propriété doit faire référence à un fichier .pfx contenant un certificat et une clé privée. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> preneur de licence segen.sign.certpass</span> </td> 
   <td colname="2" class="- topic/entry ">Mot de passe utilisé pour protéger le fichier spécifié par <span class="+ topic/ph pr-d/codeph codeph"> prensegen.sign.certfile.</span> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">licencisegen.domainca.n</span> </td> 
   <td colname="2" class="- topic/entry "> Si vous générez des licences liées à un domaine, un ou plusieurs certificats d’autorité de certification de domaine doivent être spécifiés pour indiquer les autorités de domaine approuvées par cet émetteur de licences. Si le destinataire de licence est un certificat de domaine, qui n’a pas été émis par l’une des autorités de certification de domaine spécifiées, une licence ne peut pas être générée. Cette propriété spécifie un fichier .cer contenant uniquement le certificat (le format PEM ou DER est acceptable). n doit augmenter monotoniquement, en commençant par 1. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">preneur de licence segen.keys.asymmetric.licenseServerCredential.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Fichier PKCS12 facultatif contenant des informations d’identification supplémentaires du serveur de licences pour le déchiffrement du CEK dans les métadonnées et la stratégie. D’autres informations d’identification peuvent être configurées si le contenu a été précédemment inclus avec un certificat du serveur de licences autre que celui spécifié par <span class="codeph"> prensegen.sign.certfile</span>. Cette propriété doit faire référence à un fichier <span class="filepath"> .pfx</span> contenant un certificat et une clé privée. n doit augmenter monotoniquement, en commençant par 1. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">preneur de licence segen.keys.asymmetric.licenseServerCredential.n.password</span> </td> 
   <td colname="2" class="- topic/entry ">Mot de passe utilisé pour protéger le fichier spécifié par : <p><span class="+ topic/ph pr-d/codeph codeph"> preneur de licence segen.keys.asymmetric.licenseServerCredential.n</span> </p> </td> 
  </tr> 
 </tbody> 
</table>

