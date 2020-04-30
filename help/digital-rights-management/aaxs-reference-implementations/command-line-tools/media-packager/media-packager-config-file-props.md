---
seo-title: Propriétés du fichier de configuration
title: Propriétés du fichier de configuration
uuid: f0d36240-e5fa-4bf9-9a82-7e963d03cdd0
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Propriétés du fichier de configuration {#configuration-file-properties}

Avant d’exécuter Media Packager, spécifiez des valeurs pour les propriétés de Media Packager. Le fichier de configuration spécifie les propriétés suivantes. Pour les noms de propriété qui incluent* n*, *n* représente un entier commençant par 1 et augmentant pour chaque instance de la propriété.

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_dx4_mpy_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Propriété </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Description </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.video</span> </td> 
   <td colname="2" class="- topic/entry "> Indique si le contenu vidéo doit être chiffré. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.audio</span> </td> 
   <td colname="2" class="- topic/entry "> Indique s’il faut chiffrer l’audio. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.script</span> </td> 
   <td colname="2" class="- topic/entry ">Indique si les données de script doivent être chiffrées dans les fichiers FLV. <i class="+ topic/ph hi-d/i ">Les balises de données de script onMetaData</i> et <i class="+ topic/ph hi-d/i ">onXMP</i> ne sont jamais chiffrées, même si cette option est activée. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.video.level</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique le niveau de chiffrement vidéo. Une valeur élevée est utilisée pour chiffrer tout le contenu vidéo, tandis que des valeurs moyennes et faibles sont utilisées pour chiffrer des portions du contenu vidéo pour les fichiers F4V contenant du contenu H.264. </p> <p class="- topic/p ">value = <span class="codeph"> high | medium | low</span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.secondsUnencrypted</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Si la valeur est supérieure à 0, le nombre spécifié de secondes de contenu au début du fichier ne sera pas chiffré. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.asymmetric.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Fichier de certificat du serveur de licences utilisé pour chiffrer la clé. La propriété <span class="codeph"> encrypt.keys.asymmetric.certfile</span> spécifie un fichier qui contient le certificat uniquement (le format PEM ou DER est acceptable). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">encrypt.keys.policyFile.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Cette propriété est utilisée à plusieurs reprises pour créer une liste de stratégies à appliquer au contenu. <span class="codeph"> n</span> est un entier dont la valeur est supérieure ou égale à 1. Le client utilisera la première instance par défaut. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.serverurl</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URL du serveur de licences. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.servercert</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Certificat de transport pour le serveur de licences. Cette propriété spécifie un fichier <span class="filepath"> .cer</span> contenant uniquement le certificat (le format PEM ou DER est acceptable). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Fichier PKCS12 contenant les informations d’identification du gestionnaire de package pour la signature de contenu. Le <span class="codeph"> fichier encrypt.sign.certfile</span> doit faire référence à un fichier <span class="filepath"> .pfx</span> contenant un certificat et une clé privée. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certpass</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">mot de passe utilisé pour protéger le fichier spécifié par <span class="codeph"> encrypt.sign.certfile</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.minServerVersion</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Définit la version minimale du serveur requise pour émettre des licences pour le contenu en cours de création de package. Spécifiez x (Adobe Access x.0) où x = le numéro de la version principale. Les serveurs antérieurs à Adobe Access 3.0 ne prennent pas en charge ce paramètre. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.policyFile.n.domain.transportcert</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Si une stratégie <span class="+ topic/ph pr-d/codeph codeph"> encrypt.keys.policyFile.n</span> requiert l’enregistrement de domaine auprès d’un serveur qui utilise un certificat de transport différent de celui spécifié dans <span class="+ topic/ph pr-d/codeph codeph"> encrypt.license.servercert</span>, le certificat de transport de domaine doit être fourni. </p> <p class="- topic/p ">Cette propriété spécifie un fichier contenant uniquement le certificat (le format PEM ou DER est acceptable). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.licenseKey</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Spécifiez la clé de licence. Si aucune clé n’est spécifiée, la clé est générée de manière aléatoire. Lorsque la rotation des clés n’est pas activée, il s’agit de la clé utilisée pour chiffrer le contenu. </p> <p class="- topic/p ">Lorsque la rotation des clés est activée, cette clé est utilisée pour protéger les clés de rotation. La clé doit avoir une longueur de 16 octets et être spécifiée en tant que valeurs hexadécimales. L’espace entre les valeurs hexadécimales est facultatif. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.rotation.enable</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique si la rotation des clés est activée. Si la valeur est définie sur false (par défaut), la rotation des clés est désactivée et le CEK maître est utilisé pour chiffrer tous les échantillons du contenu. </p> <p class="- topic/p ">Si ce paramètre est défini sur true, la rotation des clés est activée et différentes clés peuvent être utilisées pour chiffrer des parties du contenu. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.rotation.key.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Séquence de clés pivotées utilisées pour chiffrer le contenu lorsque la rotation des clés est activée. Si aucune clé n’est spécifiée, les clés sont générées de manière aléatoire. Les clés doivent avoir une longueur de 16 octets et être spécifiées en tant que valeurs hexadécimales. </p> <p class="- topic/p ">L’espace entre les valeurs hexadécimales est facultatif. <i class="+ topic/ph hi-d/i ">n</i> doit augmenter monotoniquement, en commençant par 1. Lorsque plusieurs clés sont spécifiées, les clés sont parcourues dans l'ordre indiqué. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.rotation.interval</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique l’intervalle (en secondes) au cours duquel une clé de rotation sera utilisée pour chiffrer des échantillons de contenu. </p> <p class="- topic/p ">Une fois que cette durée du contenu a été chiffrée, la clé de rotation suivante sera utilisée. Si la rotation des clés est activée et qu’aucun intervalle n’est spécifié, les clés sont pivotées toutes les 15 minutes. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.serverless</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Si la valeur est true, il n’existe aucun serveur de licences à partir duquel les licences peuvent être obtenues. Les licences doivent être incorporées ou obtenues hors bande. La valeur par défaut est false si elle n’est pas spécifiée. Uniquement pris en charge dans Adobe Access Professional. </p> </td> 
  </tr> 
 </tbody> 
</table>

