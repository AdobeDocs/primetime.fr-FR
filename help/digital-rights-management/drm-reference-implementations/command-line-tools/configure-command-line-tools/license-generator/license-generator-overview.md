---
seo-title: Présentation
title: Présentation
uuid: 857390be-dd14-46c0-b8f7-2bc661c515d4
translation-type: tm+mt
source-git-commit: d2b8cb67c54fadb8e0e7d2bdc15e393fdce8550e
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---


# Générateur de licences DRM {#license-generator}

Permet [!DNL AdobeLicenseGenerator.jar] de générer des licences sans demander au client d’envoyer une demande de licence à un serveur. Vous pouvez ensuite incorporer une licence prégénérée dans le contenu ou fournir la licence au client par le biais d’autres mécanismes, tels qu’un serveur Web HTTP simple.

## Utilisation de la ligne de commande du générateur de licences {#license-generator-command-line-usage}

**Générer une licence :**

```
java -jar AdobeLicenseGenerator.jar -m 
<i class="+ topic ph hi-d="" i "="">
 metadata 
 <i class="+ topic ph hi-d="" i "="">
   [options]
 </i class="+ topic>
</i class="+ topic>
```

* `metadata` - Inclut les métadonnées Adobe Primetime DRM.

   Vous pouvez récupérer ce fichier à partir d’un contenu protégé à l’aide des `-d -m` options de Media Packager.

**Affichez une licence générée précédemment :**

```
java -jar AdobeLicenseGenerator.jar -d 
<i class="+ topic ph hi-d="" i "="">
  license
</i class="+ topic>
```

* `license` - Contient une licence DRM Adobe Primetime générée par le générateur de licences.

**Tableau 6 : Options**

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_skr_vry_n4">  
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Option de ligne de commande </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Description </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-c configfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique le nom et l’emplacement du fichier de configuration. </p> <p class="- topic/p ">Si vous ne spécifiez ni nom ni emplacement, le générateur de licences DRM recherche <span class="filepath"> flashaccesstools.properties</span> dans le répertoire de travail actuel. </p> <p>Remarque :  Les options que vous spécifiez sur la ligne de commande sont prioritaires sur les options que vous spécifiez dans le fichier de configuration. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-d <i class="+ topic/ph hi-d/i "><span class="+ topic/ph pr-d/codeph codeph"> fichier de licence</span></i> </p> </td> 
   <td colname="2" class="- topic/entry "> Affiche des informations sur une licence qui a déjà été générée. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-leaf-filename</span> </td> 
   <td colname="2" class="- topic/entry "> Génère une licence feuille et enregistre la sortie dans un fichier spécifié. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-m nom_fichier_métadonnées</span> </td> 
   <td colname="2" class="- topic/entry "> Indique les métadonnées de contenu pour lesquelles vous devez générer une licence. Cette option est requise pour générer une licence. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -noprompt</span> </td> 
   <td colname="2" class="- topic/entry ">Ne demandez pas si le fichier de destination doit être remplacé. Si le fichier de destination existe déjà et que l'option <span class="codeph"> -o</span> n'a pas été définie, une erreur se produit. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -o</span> </td> 
   <td colname="2" class="- topic/entry "> Si le fichier de destination existe déjà, vous pouvez le remplacer sans recevoir d’invite. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-policy-num</span> </td> 
   <td colname="2" class="- topic/entry "> <p>Si les métadonnées comportent plusieurs stratégies DRM, vous pouvez spécifier le nombre de stratégies DRM que vous pouvez utiliser pour générer une licence. </p> <p>Si vous ne spécifiez pas le nombre de stratégies DRM, la première stratégie DRM est automatiquement appliquée. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-r destinataire-cert</span> </td> 
   <td colname="2" class="- topic/entry ">Génère une licence pour un destinataire spécifié. Vous pouvez utiliser un certificat de périphérique ou de domaine et spécifier plusieurs <span class="+ topic/ph pr-d/codeph codeph"> options -r </span>pour créer une licence pour plusieurs destinataires. </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-root-root-filename</span> </td> 
   <td colname="2" class="- topic/entry "> Génère une licence racine et enregistre la sortie dans un fichier que vous spécifiez. </td> 
  </tr> 
 </tbody> 
</table>

## Propriétés du fichier de configuration {#configuration-file-properties}

Avant d’exécuter License Generator, vous devez spécifier des valeurs pour les propriétés License Generator dans le fichier de configuration.

>[!NOTE]
>
>Pour les noms de propriété qui incluent *n*, *n* représente un entier qui s’début avec 1 et augmente pour chaque instance de la propriété.

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
   <td colname="2" class="- topic/entry "> <p>Définit la version minimale du client actuellement prise en charge. Si vous ne définissez pas cette propriété, toutes les versions sont automatiquement prises en charge par défaut. </p> <p>Vous pouvez définir cette valeur pour contrôler comment les clients plus âgés répondent aux exigences de licence qu’ils ne prennent pas en charge. Spécifiez <span class="codeph"> x</span> (pour Adobe Primetime DRM x.0) où <span class="codeph"> x</span> représente un numéro de version majeur. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> prenesegen.keyServerCert</span> </td> 
   <td colname="2" class="- topic/entry "> Certificat de serveur de clés, qui est un certificat de serveur de licences émis par un Adobe et utilisé par le serveur de clés. Ce certificat est appliqué uniquement si la stratégie de métadonnées/DRM indique qu’un serveur de clés est requis pour la diffusion de clés sur les périphériques iOS. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> preneur de licence segen.sign.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> Fichier PKCS12 qui contient les informations d’identification du serveur de licences pour la signature des licences. Cette propriété doit faire référence à un fichier .pfx contenant un certificat et une clé privée. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> preneur de licence segen.sign.certpass</span> </td> 
   <td colname="2" class="- topic/entry ">Mot de passe protégeant le fichier que vous avez spécifié avec l’option <span class="+ topic/ph pr-d/codeph codeph"> prenessegen.sign.certfile</span> . </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">licencisegen.domainca.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p>Si vous générez des licences liées à un domaine, vous devez spécifier un ou plusieurs certificats d’autorité de certification de domaine pour indiquer les autorités de domaine auxquelles l’émetteur de licences peut faire confiance. </p> <p>Si le destinataire de licence est un certificat de domaine, qui n’a pas été émis par l’une des autorités de certification de domaine spécifiées, une licence ne peut pas être générée. Cette propriété spécifie un fichier <span class="filepath"> .cer</span> qui inclut le certificat au format PEM ou DER. <span class="codeph">n</span> doit augmenter monotoniquement, en commençant par 1. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <code>licensegen.keys.asymmetric. licenseServerCredential.n</code>
   </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Fichier PKCS12 facultatif qui comprend des informations d’identification supplémentaires du serveur License Server pour le déchiffrement du CEK dans les métadonnées et la stratégie DRM. Vous pouvez configurer d’autres informations d’identification si du contenu a déjà été inclus avec un certificat du serveur de licences autre que celles qui ont été spécifiées avec <span class="codeph"> prensegen.sign.certfile</span>. Cette propriété doit faire référence à un fichier <span class="filepath"> .pfx</span> qui inclut un certificat et une clé privée. <span class="codeph">n</span> doit augmenter monotoniquement, en commençant par 1. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <code>licensegen.keys.asymmetric. licenseServerCredential.n.password</code>
   </td> 
   <td colname="2" class="- topic/entry "> <p>Le mot de passe est appliqué pour protéger le fichier que vous avez spécifié avec la<span class="+ topic/ph pr-d/codeph codeph"> propriété prensegen.keys.asymmetric.licenseServerCredential.n</span> . </p> </td> 
  </tr> 
 </tbody> 
</table>