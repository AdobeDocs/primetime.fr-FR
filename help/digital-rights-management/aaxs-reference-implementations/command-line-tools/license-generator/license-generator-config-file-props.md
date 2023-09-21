---
title: Propriétés du fichier de configuration
description: Propriétés du fichier de configuration
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
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
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensesegen.minClientVersion</span> </td> 
   <td colname="2" class="- topic/entry "> Définissez la version cliente minimale prise en charge. Si elle n’est pas définie, toutes les versions sont prises en charge par défaut. Définissez cette valeur pour contrôler la manière dont les clients plus âgés répondent aux exigences de licence qu’ils ne prennent pas en charge. Spécifiez x (pour Accès par Adobe x.0) où x est le numéro de version principal. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> license segen.keyServerCert</span> </td> 
   <td colname="2" class="- topic/entry "> Certificat de serveur clé (certificat de serveur de licences émis par un Adobe et utilisé par le serveur de clés). Ce certificat n’est utilisé que si les métadonnées/la stratégie indiquent qu’un serveur de clés est requis pour la diffusion de clés sur les appareils iOS. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licencisegen.sign.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> Fichier PKCS12 contenant les informations d’identification du serveur de licences pour la signature des licences. Cette propriété doit faire référence à un fichier .pfx contenant un certificat et une clé privée. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> license segen.sign.certpass</span> </td> 
   <td colname="2" class="- topic/entry ">mot de passe utilisé pour protéger le fichier spécifié par <span class="+ topic/ph pr-d/codeph codeph"> license segen.sign.certfile.</span> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">licencisegen.domainca.n</span> </td> 
   <td colname="2" class="- topic/entry "> Si vous générez des licences liées à des domaines, un ou plusieurs certificats d’autorité de certification de domaine doivent être spécifiés pour indiquer les autorités de domaine approuvées par cet émetteur de licences. Si le destinataire de la licence est un certificat de domaine, qui n’a pas été émis par l’une des autorités de certification de domaine spécifiées, une licence ne peut pas être générée. Cette propriété spécifie un fichier .cer contenant uniquement le certificat (le format PEM ou DER est acceptable). n doit augmenter de manière monotone, en commençant par 1. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">license segen.keys.asymmetric.licenseServerCredential.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Fichier PKCS12 facultatif contenant des informations d’identification supplémentaires du serveur de licences pour le décryptage du CEK dans les métadonnées et la stratégie. Des informations d’identification supplémentaires peuvent être configurées si du contenu a été précédemment conditionné avec un certificat de serveur de licences autre que celui spécifié par <span class="codeph"> licencisegen.sign.certfile</span>. Cette propriété doit faire référence à une propriété <span class="filepath"> .pfx</span> contenant un certificat et une clé privée. n doit augmenter de manière monotone, en commençant par 1. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">license segen.keys.asymmetric.licenseServerCredential.n.password</span> </td> 
   <td colname="2" class="- topic/entry ">mot de passe utilisé pour protéger le fichier spécifié par : <p><span class="+ topic/ph pr-d/codeph codeph"> license segen.keys.asymmetric.licenseServerCredential.n</span> </p> </td> 
  </tr> 
 </tbody> 
</table>
