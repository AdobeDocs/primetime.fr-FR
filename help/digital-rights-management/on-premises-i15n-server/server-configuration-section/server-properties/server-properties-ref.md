---
seo-title: Référence des propriétés du serveur
title: Référence des propriétés du serveur
uuid: 24a187fe-9b7d-411f-a358-d10c70a5dd0e
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Référence des propriétés du serveur{#server-properties-reference}

<!--<a id="section_EC8810492A454BDBA6013FE376360F4E"></a>-->

## Serveur d’individualisation

<table id="table_ats_tk2_jr">  
 <thead> 
  <tr> 
   <th class="entry"> Configuration </th> 
   <th class="entry"> Description </th> 
   <th class="entry"> Exemple </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td> Informations d'identification de transport </td> 
   <td>Les informations d’identification de transport sont utilisées pour déchiffrer les demandes reçues du client et signer les réponses renvoyées. Veillez à configurer le fichier <span class="filepath"> AdobeInitial.properties</span> de manière appropriée avec le chemin d’accès au fichier d’informations d’identification de transport et le mot de passe PKCS12 chiffré. </td> 
   <td> 
    <ul id="ul_itx_fl2_jr"> 
     <li id="li_A2E65253F37245268A41E6B9C958C8DF"><span class="codeph"> cert.i15n.transport.file = </span> [fichier PKCS12 contenant le certificat et la clé de transport d’individualisation] </li> 
     <li id="li_28CDFC0B3D684795AF4708B6D26DF83F"><span class="codeph"> cert.i15n.transport.password =</span> [mot de passe chiffré pour le fichier PKCS12] </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Informations d’identification de l’autorité de certification d’individualisation </td> 
   <td>Le serveur d’individualisation utilise les informations d’identification de l’autorité de certification d’individualisation pour signer les certificats de la machine qu’il émet. Veillez à configurer le fichier <span class="filepath"> AdobeInitial.properties</span> de manière appropriée avec le chemin d’accès au fichier d’informations d’identification de l’autorité de certification I15N, ainsi que le mot de passe PKCS12 chiffré. </td> 
   <td> 
    <ul id="ul_xsj_nl2_jr"> 
     <li id="li_5A770D8A482F41A4A9AB63CA52C2EB90"><span class="codeph"> cert.i15n.ica.file =</span> [fichier PKCS12 contenant le certificat et la clé d’autorité de certification d’individualisation] </li> 
     <li id="li_C3C4A2D9AA2A4F86B6DDCFFD9CB55CBB"><span class="codeph"> cert.i15n.ica.password =</span> [mot de passe chiffré pour le fichier PKCS12] </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Informations d’identification du chiffrement de l’individualisation </td> 
   <td> Le serveur d’individualisation utilise les informations d’identification Encryption pour chiffrer les fichiers sensibles qui doivent être transmis aux serveurs d’individualisation. Par exemple, ce certificat prend en charge la migration des licences et sert également à chiffrer les clés privées DRM pour les serveurs d’individualisation. </td> 
   <td> 
    <ul id="ul_nbr_kpd_w5"> 
     <li id="li_4226AD6CC85740669DAF467EFD00BBBE"><span class="codeph"> cert.i15n.decryption.file=i15n_transport.pfx</span> </li> 
     <li id="li_F51BDD94F4724FA58CEF9470B6FEE33B"><span class="codeph"> cert.i15n.decryption.password=password</span> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Cache de contenu </td> 
   <td>Ces paramètres contrôlent l’emplacement à partir duquel le serveur d’individualisation télécharge le contenu et l’emplacement de mise en cache du contenu sur le disque. Le serveur d’individualisation recherche le nouveau contenu une fois au démarrage, puis à la fréquence/heure spécifiée par ces propriétés. <p>Pour le serveur d’individualisation sur site, nous avons inclus un jeu initial de données de cache de contenu. Veillez à copier le <i>CONTENU</i> du dossier du cache (et non le dossier du cache lui-même) vers l’emplacement configuré <span class="filepath"> AdobeInitial.properties</span><span class="codeph"> contentServer.localDirectory</span> . </p> </td> 
   <td> 
    <ul id="ul_r4n_1r2_jr"> 
     <li id="li_CA5F562577B04B4A9966EF46E039A137"><span class="codeph"> contentServer.localDirectory =</span> [Répertoire dans lequel stocker le contenu local (normalement tomcat/temp)] </li> 
     <li id="li_9A78FBD6C54D47708226378340B46E8E"><span class="codeph"> contentServer.server =</span> [serveur Web à contacter pour les informations ECI (<i>non pris en charge dans cette version</i>)] </li> 
     <li id="li_4E7D7F76085D411688B5003E855F860B"><span class="codeph"> contentServer.timeout =</span> [Délai d’expiration de la connexion, en secondes] </li> 
     <li id="li_4B751F238A1643A7AC730CD9354887B6"><span class="codeph"> contentServer.pollFrequency =</span> [fréquence d’interrogation du serveur, en jours (minimum : 1 jour)] </li> 
     <li id="li_8E23C3C6E7EF46B0AFDD7993DE79F142"><span class="codeph"> contentServer.pollTime =</span> [Heure du jour pour interroger le serveur, en minutes depuis minuit] </li> 
    </ul> <p>Veuillez lire la section <i>CRL et les fichiers ECI</i> sur la mise à jour du cache. </p> </td> 
  </tr> 
  <tr> 
   <td> CRL d'autorité de certification d'individualisation </td> 
   <td> <p>Ce point de distribution CRL (Certificate Revocation) est inclus dans chaque certificat d’ordinateur émis par le serveur d’individualisation. Lors de la validation du certificat de l’ordinateur sur le serveur de licences, la liste CRL est téléchargée à partir du point de distribution indiqué dans le certificat (ou lue à partir du cache si le certificat a déjà été téléchargé) et vérifiée pour vérifier que le certificat n’a pas été révoqué. Il est recommandé d’effectuer ce changement de configuration du serveur après avoir suivi le processus de création et de déploiement de la liste CRL d’autorité de certification d’individualisation. Redémarrez le serveur d’individualisation après toute modification de la configuration. </p> <p>Pour définir l’URL du point de distribution CRL, vous devez définir le champ <span class="filepath"> AdobeInitial.properties</span> cert.machine.crldp <span class="codeph"></span> . </p> </td> 
   <td> 
    <ul id="ul_eq3_lv2_jr"> 
     <li id="li_5E37A9E318D742B6A5E1035120888819"><span class="codeph"> cert.machine.crldp =</span> [point de distribution CRL] </li> 
    </ul> <p>Par exemple : </p>
    <p> <code>
      cert.machine.crldp__DEV=<span>tps://onprem-individualization.com</span>CRL/onprem-individualization-ca.crl
     </code></p>
     <p>Le serveur de licences doit télécharger automatiquement cette liste CRL, une fois qu’une demande de licence est traitée. </p> <p importance="high">Remarque : Ce point de distribution <i>n’est pas</i> vérifié par Primetime DRM pour vérifier sa validité. Vous devez vérifier que cette URL est valide. Les erreurs résultant d’une URL non valide n’apparaîtront pas tant que les erreurs de validation n’auront pas été détectées par le serveur de licences. </p> </td> 
  </tr> 
  <tr> 
   <td> Journalisation </td> 
   <td>Configurez le fichier <span class="filepath"> AdobeInitial.properties</span> pour la journalisation, le cas échéant. </td> 
   <td> 
    <ul id="ul_j1v_kw2_jr"> 
     <li id="li_B60002B33A3042FCBE1F694454966469"><span class="codeph"> adobe.weblogs.loc =</span> [répertoire de création des fichiers journaux] </li> 
     <li id="li_2DD4406FBBF047589BAAAE1C9082D8B3"><span class="codeph"> log.Level =</span> [Le niveau le plus bas des messages du journal qui peuvent apparaître dans les journaux <span class="codeph"> [DEBUG]| INFO]</span> ] </li> 
     <li id="li_610FAF239A554CE59DAC455174F0CF0A"><span class="codeph"> log.FileName =</span> [Préfixe pour les fichiers journaux. L’extension Date/Heure et ".log" sera ajoutée au nom de fichier] </li> 
     <li id="li_1F2913B209BE4A0E8207FAAD052D1764"><span class="codeph"> log.RollInterval =</span> [Indique la fréquence d’exécution des journaux.] </li> 
     <li id="li_3F46C15488114BB5B41035F710E7A19F"><span class="codeph"> log.RollSize =</span> [Faire rouler les journaux lorsqu'ils atteignent cette taille (Les journaux s'affichent lorsque l'on atteint l' <span class="codeph"> Intervalle</span> de roulage ou la <span class="codeph"> Taille</span> de roulage, selon le premier critère)] </li> 
     <li id="li_DA32E862F7B0413885DA20633B682484"><span class="codeph"> log.ReportLogging.Enabled =</span>[ [true]| false ] Indique si un fichier distinct doit être généré, qui contient les données utilisées par Adobe pour générer des rapports d’individualisation.] </li> 
     <li id="li_465CC6D81B8A484CBF4E7A39F7AF86AA"><span class="codeph"> log.ReportLogging.FileName =</span> [Préfixe pour les fichiers journaux des rapports. Les extensions Date/Heure et <span class="filepath"> .log</span> seront ajoutées au nom du fichier. La propriété l<span class="codeph"> og.Level</span> ne s’applique pas à ce fichier journal, mais <span class="codeph"> log.RollInterval</span> et <span class="codeph"> log.RollSize</span> .] </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Autre </td> 
   <td></td> 
   <td> 
    <ul id="ul_b3b_g1f_jr"> 
     <li id="li_FACF07CB332D416E91FD34DE48152FAA"><span class="codeph"> deviceinfo.key =</span> [Clé codée Base64 chiffrée utilisée pour les informations de périphérique HMAC avant de l’inclure dans le jeton de l’ordinateur. La clé peut être différente pour l’ de développement/test/ de production, mais doit être la même pour tous les serveurs d’un  particulier. ] </li> 
     <li id="li_B19C77FD6F91496294DBF836A1922EE1"><span class="codeph"> keys.kgs.server =</span> [Emplacement du serveur Key Gen (un hôte/port unique, représentant un pool de serveurs clés) ] </li> 
     <li id="li_5DA3C89770804B148EF6FAF01A5AD958"><span class="codeph"> keys.MinQueueSize =</span> [Récupère un autre lot de clés du KGS lorsqu'il reste autant de clés dans la file d'attente] </li> 
     <li id="li_0C2E5F2FDB824182A6BE418B041D2F28"><span class="codeph"> status.Timeout =</span> [La page d'état effectuera un test ping sur le KGS pour déterminer s'il peut atteindre le serveur. Il expirera si une réponse n’est pas reçue dans le délai spécifié.] </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Serveur de génération de clés {#section_37FA8EEBA258461F8CFA3ADF37714577}

<table id="table_ats_tk2_js"> 
 <thead> 
  <tr> 
   <th class="entry"> Configuration </th> 
   <th class="entry"> Description </th> 
   <th class="entry"> Exemple </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td> Génération de clés </td> 
   <td></td> 
   <td> 
    <ul id="ul_nlj_ydf_jr"> 
     <li id="li_E4347D572F004BF0B237A662BFE7F3ED"><span class="codeph"> kgs.Threads =</span> [Nombre de threads à utiliser pour générer des clés (doit être égal au nombre de processeurs disponibles sur l'ordinateur)] </li> 
     <li id="li_EDBC2535D48E4A66AEB240DB337187FC"><span class="codeph"> kgs.BatchSize =</span> [Nombre de clés à générer par lot] </li> 
     <li id="li_07B41546D94F42349103BF8AF4605E14"><span class="codeph"> kgs.KeyDirectory =</span> [Répertoire dans lequel stocker les fichiers de commandes clés] </li> 
     <li id="li_F4962C97DC3D491DA7FAC826E38A4459"><span class="codeph"> kgs.MaxQueueSize =</span> [Nombre maximal de fichiers de lot de clés à générer] </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Journalisation </td> 
   <td></td> 
   <td> 
    <ul id="ul_kwq_12f_jr"> 
     <li id="li_5E5D34FE5EB44BB898090494C7DDEBD8"><span class="codeph"> adobe.weblogs.loc =</span> [répertoire de création des fichiers journaux] </li> 
     <li id="li_0E34CD32CD5E47729B69B50414F93678"><span class="codeph"> log.FileName =</span> [Préfixe pour les fichiers journaux. Date/Heure et <span class="filepath"> extension .log</span> seront ajoutées au nom du fichier] </li> 
     <li id="li_8AB15ACEC39041A2A04C7301154C6EDB"><span class="codeph"> log.Level =</span> [Le niveau le plus bas des messages du journal qui peuvent apparaître dans les journaux] </li> 
     <li id="li_A17E84DA3ED243F381FF3A6184A3CAA0"><span class="codeph"> log.RollInterval =</span> [Indique la fréquence d’exécution des journaux.] </li> 
     <li id="li_C2B3D111608945DA9D1428BE98D61664"><span class="codeph"> log.RollSize =</span> [Faire rouler les journaux lorsqu'ils atteignent cette taille (Les journaux s'affichent lorsque l'on atteint l' <span class="codeph"> Intervalle</span> de roulage ou la <span class="codeph"> Taille</span> de roulage, selon le premier critère)] </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
