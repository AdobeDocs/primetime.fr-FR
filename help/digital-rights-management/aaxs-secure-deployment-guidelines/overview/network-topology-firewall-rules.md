---
seo-title: Règles de pare-feu
title: Règles de pare-feu
uuid: a5667030-c4d0-42e3-b56e-20a12c903954
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---


# Règles de pare-feu {#firewall-rules}

## URL entrantes {#section-F111526A9DB844CBBF21A3CAE5F50880}

Configurez votre pare-feu externe de sorte qu’il n’expose que les URL des fonctionnalités d’application que vous souhaitez fournir aux utilisateurs finaux. Autoriser les utilisateurs externes à accéder par le pare-feu externe uniquement aux URL répertoriées dans le tableau suivant :

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table-bqs-whz-n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">URL racine </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Objectif </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="filepath"> /flashaccess/getServerVersion/v3</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URL permettant de déterminer la version du serveur. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul-xr4-hdn-44"> 
     <li id="li-05925A4DE4114F7786FF93A66AB8A117"><span class="filepath"> /flashaccess/authn/v1/*</span> </li> 
     <li id="li-E76E9BA0160F4E7F9EBB64428C2D9F31"><span class="filepath"> /flashaccess/authn/v3/*</span> </li> 
     <li id="li-ED3C15EB4D194FFE99954BDB7D5C1E41"><span class="filepath"> /flashaccess/authn/v4/*</span> </li> 
     <li id="li-4DD6CBBE939F4E6EABA474E3DCCBD893"><span class="filepath"> /flashaccess/authn/v5/*</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URL d’authentification des utilisateurs. Cette URL ne doit être accessible que si vous utilisez les API du client d'accès à l'Adobe pour effectuer l'authentification de l'utilisateur. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul-yxs-rdn-44"> 
     <li id="li-49B9987ED6E14FADA66727448F923F84"><span class="filepath"> /flashaccess/license/v1/*</span> </li> 
     <li id="li-BF4A415E573C4C728E24D548F53D923C"><span class="filepath"> /flashaccess/license/v3/*</span> </li> 
     <li id="li-E6C551DDA030429B9D0073D2685B778A"><span class="filepath"> /flashaccess/license/v4/*</span> </li> 
     <li id="li-57811F4CD7304DBDAFADD65244AED0D9"><span class="filepath"> /flashaccess/license/v5/*</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URL d’octroi de licences aux utilisateurs finaux. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul-ibl-5dn-44"> 
     <li id="li-189BE370CD5044F988A42335C3BFE420"><span class="filepath"> /flashaccess/sync/v3</span> </li> 
     <li id="li-B333B85FFE8A46DD884595B0A620B4EE"><span class="filepath"> /flashaccess/sync/v4</span> </li> 
     <li id="li-E4771D3C5AA5454CA1EDCFAA3E027CC1"><span class="filepath"> /flashaccess/sync/v5</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URL des demandes de synchronisation. Cette URL ne doit être accessible que si vous spécifiez les conditions de synchronisation requises dans vos licences. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul-plq-ydn-44"> 
     <li id="li-81C96F93BA904C8C95B907F1A77E6494"><span class="filepath"> /flashaccess/domain/v3</span> </li> 
     <li id="li-40F0952F09674CA3B9AAFB5A62F9D02E"><span class="filepath"> /flashaccess/domain/v4</span> </li> 
     <li id="li-3ADE44B959B548F8A31A6FF08537AF46"><span class="filepath"> /flashaccess/domain/v5</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URL d’enregistrement de domaine. Cette URL ne doit être accessible que si vous mettez en oeuvre la prise en charge des domaines. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul-btm-c2n-44"> 
     <li id="li-3535EDF7C644406FAC471D4234C4AF98"><span class="filepath"> /flashaccess/dereg/v3</span> </li> 
     <li id="li-AB33657BC7E140E695767710DF7AEC72"><span class="filepath"> /flashaccess/dereg/v4</span> </li> 
     <li id="li-D15B32BCD4674269A3A2644DD5204707"><span class="filepath"> /flashaccess/dereg/v5</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URL de désenregistrement de domaine. Cette URL ne doit être accessible que si vous mettez en oeuvre la prise en charge des domaines. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="filepath"> /flashaccess/headerconversion/v1/*</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URL à utiliser par le client pour convertir les métadonnées DRM FMRMS 1.x en métadonnées DRM d’accès à l’Adobe. </p> <p class="- topic/p ">Remarque : <i class="+ topic/ph hi-d/i ">Cette URL doit utiliser SSL (HTTPS)</i>. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="filepath"> /edcws/services/urn:EDCLicenseService/*</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URL du service Web LiveCycle Rights Management ES. Si le contenu a été publié à l’aide d’une version antérieure de FMRMS, cette URL permet aux anciens clients de se connecter au serveur et d’être invités à effectuer la mise à niveau vers Adobe Access. </p> <p class="- topic/p ">Remarque : <i class="+ topic/ph hi-d/i ">Cette URL doit utiliser SSL (HTTPS)</i>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "><span class="filepath"> /flashaccess/lreturn/v5</span> </td> 
   <td colname="2" class="- topic/entry "> <p>URL de retour de licence. L’URL ne doit être accessible que si vous mettez en oeuvre la prise en charge du retour de licence. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Le pare-feu interne ne doit autoriser que les connexions au serveur de licences d&#39;accès à l&#39;Adobe par le proxy inverse et uniquement aux URL répertoriées ci-dessus. Pour améliorer l’évolutivité, les connexions entre le proxy inverse et l’accès à l’Adobe seront effectuées via HTTP.

## URL sortantes {#section-FFF9F7BB353149F4A27F8788E9934A48}

Le serveur de licences nécessite un accès via le pare-feu pour télécharger les listes de révocation des certificats suivantes à partir de l’Adobe :

* <span></span>https://crl2.adobe.com/Adobe/FlashAccessRootCA.crl
* <span></span>https://crl2.adobe.com/Adobe/FlashAccessIntermediateCA.crl
* <span></span>https://crl3.adobe.com/AdobeSystemsIncorporatedFlashAccessRuntime/LatestCRL.crl
* <span></span>https://crl2.adobe.com/Adobe/FlashAccessIndividualizationCA.crl