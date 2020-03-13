---
seo-title: Présentation des préférences
title: Présentation des préférences
uuid: d1c067b1-6c2b-460e-8d00-5a5bfee0789c
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Présentation des préférences {#setting-preferences-overview}

À l’exception de l’URL du serveur Packager, toutes les préférences spécifiées ci-dessous sont stockées dans le [!DNL flashaccess-refimpl-packager.properties] fichier sur le serveur. Tous les paramètres peuvent être modifiés soit directement dans le fichier de propriétés, soit par le biais de l’application AIR. Les mots de passe sont chiffrés lorsqu’ils sont stockés dans le fichier de propriétés du serveur. Entrez le mot de passe non chiffré dans l’interface utilisateur et il sera chiffré avant d’être stocké dans le fichier.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Tous les répertoires et chemins d’accès se rapportent aux répertoires sur le serveur packager, et non sur le client exécutant l’application AIR.

Les modifications apportées ici prennent effet immédiatement une fois les préférences enregistrées. Il n’est pas nécessaire de redémarrer le serveur à moins que le thread de Packager ne se soit arrêté en raison de problèmes de configuration.

Les descriptions de préférences utilisent les termes suivants :

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_tj5_hcz_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> Préférence </th> 
   <th colname="2" class="- topic/entry entry"> Description </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> URL du serveur Packager </td> 
   <td colname="2" class="- topic/entry "> Emplacement du serveur exécutant <span class="filepath"> flashaccess-packager.war </span>; par exemple, <span class="filepath"> https://localhost:8080 </span> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> Répertoire de ressources </td> 
   <td colname="2" class="- topic/entry "> Répertoire contenant les stratégies, les certificats, les informations d’identification et toute autre ressource requise pour le serveur Packager </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> URL du serveur de licences </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URL du serveur à partir duquel le client doit demander une licence ; par exemple, <span class="filepath"> https://mylicenseserver.com:8080 </span> </p> </td> 
  </tr> 
 </tbody> 
</table>

