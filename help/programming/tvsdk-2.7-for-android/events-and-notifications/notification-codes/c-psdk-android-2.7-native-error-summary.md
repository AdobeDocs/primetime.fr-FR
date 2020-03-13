---
seo-title: Détails de la notification NATIVE_ERROR
title: Détails de la notification NATIVE_ERROR
uuid: 750ee0e2-15d4-4602-9574-94015a6e1b57
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40

---


# Détails de la notification NATIVE_ERROR {#details-for-the-native-error-notification}

Lorsque TVSDK traite une erreur native, il renvoie certaines ou toutes les valeurs de clé de métadonnées suivantes sous forme de chaînes.

<table id="table_7F713B7A56024D8DA3C84E449D09CC91"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Nom de la clé de métadonnées </th> 
   <th colname="col2" class="entry"> Valeur des métadonnées </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> NATIVE_ERROR_CODE</span> </td> 
   <td colname="col2"> <p>Code d’erreur natif provenant d’AVE. </p> <p>Ces codes représentent les éléments suivants : 
     <ul id="ul_1F33D523DDFE4CE8B4F0DC279FF7E4F8"> 
      <li id="li_07A2D9BEE6364935A61EF3BD4AB6DE27">Erreurs DRM (codes 3300 à 3367). Ces codes sont identiques aux codes d’erreur équivalents de Flash Player. </li> 
      <li id="li_433BA22DE3504AEEB623598BB4F939FA">Erreurs de lecture vidéo (-1 à 89) </li> 
      <li id="li_B347CB151DB94DE0A1DDEB1B33D2DABA">Erreurs de chiffrement (300 à 307) </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> NATIVE_ERROR</span> </td> 
   <td colname="col2">Brève description de la notification (par exemple, <span class="codeph"> AAXS_InvalidVoucher</span> ou <span class="codeph"> DECODER_FAILED</span>). </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DESCRIPTION</span> </td> 
   <td colname="col2"> Description longue de la notification (par exemple, l’opération de résolution de publicité a échoué). </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> PSDK_ERROR_CODE</span> </td> 
   <td colname="col2"><span class="codeph"> com.adobe.mediacore.PSDKErrorCode</span> valeur numérique sous forme de chaîne (par exemple, "13"). </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> PSDK_ERROR</span> </td> 
   <td colname="col2"><span class="codeph"> com.adobe.mediacore.PSDKErrorCode</span> sous forme de chaîne (par exemple, <span class="codeph"> kECNetworkError</span>). </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AVERTISSEMENT</span> </td> 
   <td colname="col2"> Description de l’avertissement. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ERREUR</span> </td> 
   <td colname="col2"> Description de l’erreur. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>DRM</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> NATIVE_SUBERROR_CODE</span> </td> 
   <td colname="col2"> Erreur mineure du module DRM. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DRM_ERROR_STRING</span> </td> 
   <td colname="col2"> Description de l’erreur. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DRM_ERROR_SERVER_URL</span> </td> 
   <td colname="col2"> URL du serveur DRM auquel TVSDK a tenté de parler. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Échec du chargement du manifeste publicitaire</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AD_URL</span> </td> 
   <td colname="col2"> URL du contenu dont le chargement a échoué. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AD_TYPE</span> </td> 
   <td colname="col2">Type de publicité (constante de l’énumération <span class="codeph"> MediaResource.Type</span> ). </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AD_DURATION</span> </td> 
   <td colname="col2"> Durée de la publicité en millisecondes. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AD_ID</span> </td> 
   <td colname="col2"> ID affecté à la publicité. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Erreurs de fichier</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DOWNLOAD_ERROR</span> </td> 
   <td colname="col2"> Description de l’erreur lors du téléchargement du fichier multimédia. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> URL</span> </td> 
   <td colname="col2"> URL du fichier en cours de téléchargement. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> MANIFEST_ERROR</span> </td> 
   <td colname="col2"> Description de l’erreur lors du téléchargement du fichier manifeste. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> CONTENT_ERROR</span> </td> 
   <td colname="col2">Description de l’erreur pendant le téléchargement du fragment (par exemple, <span class="codeph"> ts</span>). </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Erreurs de suivi audio</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AUDIO_TRACK_NAME</span> </td> 
   <td colname="col2"> Nom de la piste audio dont le chargement a échoué, tel que spécifié dans le manifeste. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AUDIO_TRACK_LANGUAGE</span> </td> 
   <td colname="col2"> Langue de la piste audio, comme spécifié dans le manifeste. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Rechercher des erreurs</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DESIRED_SEEK_PERIOD</span> </td> 
   <td colname="col2"> ID de la période (entier). </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DESIRED_SEEK_POSITION</span> </td> 
   <td colname="col2"> <p>Position (en millisecondes) recherchée (). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Divers</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AUDITUDE_ERROR_CODE</span> </td> 
   <td colname="col2"> Code d’erreur Auditude (nombre). </td> 
  </tr> 
 </tbody> 
</table>

## NATIVE_ERROR : Valeurs DRM {#section_D240082B93D34902A18C3923C1C717B3}

L’interface Video Encoder du moteur vidéo Adobe renvoie ces notifications DRM dans l’objet `NATIVE_ERROR` de métadonnées.

Lorsque vous  des erreurs DRM à Adobe, veillez à inclure l’aide `NATIVE_SUBERROR_CODE` et `DRM_ERROR_STRING` pour le dépannage.

>[!TIP]
>
>Ce fournit des informations spécifiques à TVSDK sur les erreurs. Pour obtenir des descriptions complètes, voir Référence ActionScript sur les erreurs d’exécution [ActionScript pour la plate-forme](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/runtimeErrors.html#3300)Adobe Flash.

<table id="table_CD59A859865F4FFDBAA249C89C74770A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Valeur de la clé de métadonnées NATIVE_- ERROR_CODE </th> 
   <th colname="col2" class="entry"> Valeur de la clé de métadonnées NATIVE_ERROR_NAME </th> 
   <th colname="col3" class="entry"> Signification </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> 3300 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InvalidVoucher</span> </td> 
   <td colname="col3"> 
    <ul id="ul_516E4CB32D624B22892DDB9266CB04CA"> 
     <li id="li_348FC0F38B11417994119B61C9244076">Ce que le logiciel du distributeur doit faire: 
      <ul id="ul_7AFD45CF92454BA4927783FAA628FBC4"> 
       <li id="li_0D9CCE61612643648C12DCDDD252E52A">Si vous utilisez Google Chrome et que vous êtes en mode Incognito et que votre version de Flash Player est inférieure à 11.6, cette erreur peut se produire. <p>Nous recommandons au lecteur de vérifier le numéro de version du navigateur et de recommander à l'utilisateur de quitter le mode Incognito. </p> </li> 
       <li id="li_1DC6B755BD0840D48BEC92568FD330BA">Demandez à nouveau la licence. <p>Si la requête aboutit, vous n’avez pas besoin de vous connecter ou de réaffecter. Si la requête échoue, consignez le contenu à l’origine de l’erreur. <span class="codeph"> subErrorId</span> contient une erreur de ligne, le cas échéant. </p> </li> 
      </ul> </li> 
     <li id="li_060B5D60C9BB419CBFA7B062FBCF2632">Ce que le distributeur doit faire : 
      <ul id="ul_FADB29DBF0DA4A0E8E54134AEB7DCD8A"> 
       <li id="li_FC5B1C04D21E4AECB0EBD9ADD3198504">Si les  échouent sur des configurations autres que Chrome avec Flash version 11.6, il se peut qu’une erreur se soit produite dans le pack. </li> 
       <li id="li_A720ECE591254021879B335B81B1F76D">Vérifiez si le problème est spécifique à certains contenus et reconditionnez-les. </li> 
      </ul> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3301 </td> 
   <td colname="col2"><span class="codeph"> AAXS_AuthenticationFailed</span> </td> 
   <td colname="col3"> <p>Le serveur n'a pas pu authentifier ou autoriser le client. </p> 
    <ul id="ul_BE77AC1848FB4C09B6318359ACF1B8EE"> 
     <li id="li_6FB37D317D174E8488C5070D20CD241C">Le logiciel du distributeur doit prendre toutes les mesures nécessaires pour rétablir les informations d'identification de l'utilisateur ou guider l'utilisateur pour obtenir l'accès au contenu. </li> 
     <li id="li_BE071D59805B42D38E3E7650BC936417">Le distributeur doit confirmer que le mécanisme d'autorisation et d'authentification du distributeur fonctionne correctement. <p>Si les distributeurs n’envisagent pas d’utiliser les fonctionnalités d’authentification ou d’autorisation, ils doivent vérifier si la stratégie du contenu offensant nécessite une authentification et voir Diagnostic des écarts entre les stratégies et les licences. </p> </li> 
    </ul> <p>Pour plus d’informations sur ce code d’erreur, voir <a href="https://forums.adobe.com/thread/1277149" format="https" scope="external"> Causes et résolution</a>de l’erreur DRM 3301. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3302 </td> 
   <td colname="col2"><span class="codeph"> AAXS_RequireSSL</span> </td> 
   <td colname="col3"> <p>Sur Access 4.0 et versions ultérieures, cette erreur est générée sur iOS lorsque l’URL de clé distante n’utilise pas HTTPS comme schéma. HTTPS est obligatoire. </p> 
    <ul id="ul_3D47777BBCA14B67B107FBBE3E37E40C"> 
     <li id="li_7F7BBB27AE754CC39ABAAF9269739C49">Si le distributeur utilise une version antérieure à Access v4 ou une version d’au moins 4 mais que la plate-forme n’est pas iOS, le logiciel du distributeur doit enregistrer l’erreur. <p>L’erreur est générée uniquement sur iOS. </p> </li> 
     <li id="li_D83C427D2A0D47408F723EF7195070B6">Si le logiciel du distributeur est au moins Adobe Access version 4 et que la plate-forme est iOS, les distributeurs doivent modifier l’URL du serveur de clés distantes qu’ils utilisent en HTTPS. <p>S’ils utilisaient uniquement HTTP, les distributeurs pourraient avoir à configurer un serveur HTTPS. Dans le cas contraire, les distributeurs doivent envoyer les informations enregistrées à Adobe et réaffecter le problème. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3303 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ContentExpired</span> </td> 
   <td colname="col3"> <p>Le contenu que vous affichez a expiré conformément aux règles définies par le fournisseur de contenu. subErrorId contient une erreur spécifique au client ou une erreur de ligne. </p> <p> 
     <ul id="ul_1E4B3B8AE87A4E79997553BB2A0E52B9"> 
      <li id="li_EE3F2EEBF73743B9A38E4FCB7531E275">Le logiciel du distributeur doit tenter de récupérer une fois la licence du serveur afin de déterminer si une nouvelle licence non expirée est disponible. <p>Si aucune licence n’est disponible ou si la licence a expiré, autorisez l’utilisateur à acquérir une nouvelle licence ou informez l’utilisateur que le contenu ne peut pas être regardé.Si le contenu a été inclus dans un pack avec une stratégie dont la date d’expiration/de fin est dépassée, les journaux du serveur de licences signalent une <span class="codeph"> exception PolicyEvaluation</span> et indiquent que la date de fin de la stratégie est dépassée (code d’erreur du serveur 3303333330333).). Vérifiez les fichiers journaux du serveur. </p> <p>Dans la mesure du possible, les clients doivent vérifier la stratégie qu’ils ont utilisée lors de l’assemblage pour vérifier si elle a expiré. L’outil de ligne de commande Java est : 
        <code>
         java&nbsp;-jar&nbsp;libs/AdobePolicyManager.jar&nbsp;&nbsp;&nbsp;detail&nbsp;demo.pol
        </code> </p> </li> 
      <li id="li_50DBE680D8F04E7DA3E29C65A93188E7">Le distributeur doit vérifier si les dates d’expiration des licences sont configurées comme prévu. </li> 
     </ul> </p> <p>Pour plus d’informations sur ce code d’erreur, voir <a href="https://forums.adobe.com/thread/1300813" format="https" scope="external"> 3303 (Content Expired) with AMS/FMS using a Live Stream?</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3304 </td> 
   <td colname="col2"><span class="codeph"> AAXS_AuthorizationFailed</span> </td> 
   <td colname="col3">Pour plus d’informations sur ce code d’erreur, voir <a href="https://forums.adobe.com/thread/1277149" format="https" scope="external"> Causes et résolution</a>de l’erreur DRM 3301. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3305 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ServerConnectionFailed</span> </td> 
   <td colname="col3"> <p>La connexion aux serveurs de domaine ou de licence a expiré, soit en raison d’un retard du réseau, soit en raison de la mise hors ligne du client. Normalement, subErrorId contient le code de retour HTTP. </p> 
    <ul id="ul_938C7D8F07F64B4FA71A09DDF37E2E64"> 
     <li id="li_6648EA0049094E369BD9AE9CCA6B148D">Le logiciel du distributeur doit tenter une connexion réseau à un bon serveur connu. <p>Si la tentative échoue, invitez l’utilisateur à se reconnecter au réseau. Si la tentative est réussie, connectez-la. </p> </li> 
     <li id="li_2ECA2C04BA08449DA3AD79A52EFAA229">Le distributeur doit vérifier que les licences et les serveurs de domaine utilisés sont en ligne et visibles depuis le réseau du client. </li> 
    </ul> <p>Pour plus d’informations sur ce code d’erreur, voir les causes et la résolution <a href="https://forums.adobe.com/thread/1284947" format="https" scope="external"> de</a>DRM 3305 [ServerConnectionFailed]. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3306 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ClientUpdateRequire</span> </td> 
   <td colname="col3"> Utilisez une version plus récente de TVSDK pour Android. <p>Le client actuel ne peut pas terminer l’action demandée, mais un client mis à jour peut être en mesure de terminer la requête. </p> <p>Cela peut avoir plusieurs causes : 
     <ul id="ul_2EC4D42D5273439FA1AFDA1A2578B3D6"> 
      <li id="li_FCA926F5FAED4E7190BE855545AB6ACF">Un domaine partagé non disponible sur ce client a été utilisé. C’est probablement le cas lorsque la lecture fonctionne sur Chrome, mais pas dans tout autre navigateur et inversement. <p> <p>Conseil : Chrome utilise une clé PHDS/PHLS différente de celle utilisée par les autres navigateurs. Pour plus d’informations, voir <a href="https://adobeprimetime.zendesk.com/agent/tickets/2891" format="https" scope="external"> https://adobeprimetime.zendesk.com/agent/tickets/2891</a>. </p> </p> </li> 
      <li id="li_3B633FB699234DCEA136E9BE3CC3386D">L’application tente d’ajouter plusieurs sessions DRMSession lors de l’exécution sur une version iOS antérieure à la version 5.0. </li> 
      <li id="li_F7ED993AF0B941A7A27216B4D587A999">Les métadonnées ont une version 3 ou supérieure lorsque seule la version 2 est prise en charge. </li> 
     </ul> </p> 
    <ul id="ul_EE4AE6AD4F1745A5B5623E53B599DB62"> 
     <li id="li_7A83869D4262443DA35FA1DF8D3097DD">Le logiciel du distributeur doit avertir l'utilisateur et abandonner l'opération. <p>Si le logiciel permet de déterminer si une mise à niveau est disponible, dirigez l’utilisateur vers cette mise à niveau de la manière appropriée pour la plateforme. </p> </li> 
     <li id="li_AF9C2711FDE54DA196EB9D2864632000">Si le problème survient en raison d’un domaine partagé, le distributeur devra vérifier auprès d’Adobe si le runtime ou la bibliothèque a été mis à jour. <p>Pour le runtime Flash, le distributeur peut forcer la mise à niveau directement dans son application. Dans le cas d'une bibliothèque, le distributeur devra obtenir une bibliothèque mise à jour, recréer son application et la déployer sur ses utilisateurs. </p> <p>Si le problème survient en raison de plusieurs sessions DRMS, le distributeur devra mettre à jour son application pour vérifier le numéro de version iOS avant d’ajouter plusieurs sessions DRMS. Ils peuvent également limiter la distribution de leur application à iOS v5 et versions ultérieures. </p> <p>si le problème survient parce que la version des métadonnées est supérieure à la version 2, il s’agit probablement de métadonnées endommagées. Ils peuvent essayer de recréer les métadonnées et d'examiner les résultats. S’ils continuent de voir le problème, consignez-le et réaffectez-le à Adobe. </p> </li> 
    </ul> <p>Pour plus d’informations sur ce code d’erreur, voir <a href="https://forums.adobe.com/thread/1266675" format="https" scope="external"> Comment corriger un code d’erreur DRMErrorEvent 3306</a> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3307 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InternalFailure</span> </td> 
   <td colname="col3"> <p>Ceci représente généralement un bogue dans le code Adobe Access et est inattendu, sauf s’il existe un bogue connu, comme ci-dessous. subErrorId contient une erreur spécifique au client ou une erreur de ligne. </p> 
    <ul id="ul_79F4A9655A2148519B1E9509C41F78C3"> 
     <li id="li_0E093AB4D6BD489B852279E6C1525A15">Si le navigateur est Chrome sous Windows et que la version Flash est 11.6 (SWF version 19 ou supérieure), le logiciel du distributeur doit supposer que l’utilisateur a appuyé sur <span class="uicontrol"> Deny</span> sur l’infobar et traité de la même façon qu’un 3368. </li> 
     <li id="li_0215D1089B344861A2C0A73E1067CFEF">Si la version 3307 se produit lorsque le navigateur n’est pas Chrome ou que la version Flash n’est pas 11.6, le distributeur doit réaffecter à Adobe. </li> 
    </ul> <p>Important : <span class="codeph"> 3307:1107296344 (FailedToGetBrokerHandle)</span> peut survenir avec les versions 24 à 28 du navigateur Chrome. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3308 </td> 
   <td colname="col2"><span class="codeph"> AAXS_WrongLicenseKey</span> </td> 
   <td colname="col3"> <p>Cette erreur est renvoyée lorsque la licence utilisée contient la mauvaise clé pour déchiffrer le contenu. subErrorId contient une erreur spécifique au client ou une erreur de ligne. </p> <p>Il ne semble y avoir que deux manières de générer ce bogue : 
     <ul id="ul_1C955BD74C7843809D1B5A0CDCA5ED7B"> 
      <li id="li_18F0A7FDA6584887AD9DB3EDE54080D8">Le client a modifié l’outil Adobe standard pour générer des licences (par exemple, la structure Java du serveur de licence). <p>Dans ce cas, la licence contient une mauvaise clé qui peut ne correspondre à aucun contenu. </p> </li> 
      <li id="li_21D04ED1F1FA464785BC297D385766FF">Le client a émis plusieurs licences avec le même ID de licence. <p>Dans ce cas, plusieurs licences sont disponibles sur le client qui correspondent aux métadonnées de contenu et le code d’accès a sélectionné la mauvaise licence à utiliser. </p> </li> 
     </ul> </p> 
    <ul id="ul_64AEE62BE36946F290067CF475A36ECA"> 
     <li id="li_9EEB2B11A4DA41E78C5840D8FAA81F0D">Le logiciel du distributeur doit tenter de récupérer la licence du serveur. 
      <ul id="ul_ACADC5518B054D0A853AEED2B675DB23"> 
       <li id="li_394835C8731048A5BF7D9370AC12448C">Si aucune licence n’est disponible ou si la licence est expirée, fournissez un flux de travail à l’utilisateur pour acquérir une nouvelle licence ou informez-lui que le contenu ne peut pas être regardé et consignez la publication. </li> 
       <li id="li_3FE50518BE53405F9563FA620F7EAD5F">S’il s’agissait d’un contenu lié au domaine (pour AIR), offrez à l’utilisateur un moyen de le rejoindre. </li> 
      </ul> </li> 
     <li id="li_C80B353C1AEA4E9398241420CB491E84">Le distributeur doit : 
      <ul id="ul_B5C50009374C4EED9B2B050B48F5F0F6"> 
       <li id="li_D5E6B760E0BC4B5C949ED1544B398838">Vérifiez qu’ils n’ont pas personnalisé les portions de délivrance des licences du serveur de licences d’accès. </li> 
       <li id="li_AA8F4E4B6DDD40BA8807C0920A92186B">Vérifiez qu’ils émettent des ID de licence uniques pour toutes les licences. </li> 
       <li id="li_A2C53FE779AC4FDDB65E00A2C4F43EC4">Réaffectez le problème à Adobe. </li> 
      </ul> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3309 </td> 
   <td colname="col2"><span class="codeph"> AAXS_CorruptedAdditionalHeader </span> </td> 
   <td colname="col3"> <p>Cela se produit si l’en-tête est supérieur à 6 536 octets. </p> 
    <ul id="ul_82C0F688519B4F43A764D59A891F1903"> 
     <li id="li_E66AC9149A0649E88A79C5289C12C395">Le logiciel du distributeur doit consigner le contenu qui a provoqué l'erreur. </li> 
     <li id="li_1C5916A33E7B4DC9968105B9BD20A727">Le distributeur doit confirmer que l'erreur est reproductible avec des éléments de contenu spécifiques. Réparez le contenu endommagé. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3310 </td> 
   <td colname="col2"><span class="codeph"> AAXS_AppIDMismatch </span> </td> 
   <td colname="col3">L'application Android ne correspond pas à celle utilisée. <p>L’application AIR ou le fichier SWF Flash approprié n’est pas utilisé. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3311 </td> 
   <td colname="col2"><span class="codeph"> AAXS_AppVersionMismatch </span> </td> 
   <td colname="col3"> Non utilisé. Ce problème peut toujours être généré par la pile de la version 1.x dans AIR. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3312 </td> 
   <td colname="col2"><span class="codeph"> AAXS_LicenseIntegrity </span> </td> 
   <td colname="col3"> Pour résoudre ce problème, téléchargez à nouveau la licence à partir du serveur. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3313 </td> 
   <td colname="col2"><span class="codeph"> AAXS_WriteMicrosafeFailed </span> </td> 
   <td colname="col3"> <p>Ce problème survient lorsque le système ne peut pas écrire dans le système de fichiers. <span class="codeph"> subErrorId</span> contient une erreur spécifique au client ou une erreur de ligne. </p> <p>Sous Microsoft Windows, l’erreur 3313 peut être générée par le lecteur Flash Active X ou NPAPI lorsque le contenu chiffré comporte un ID de licence ou un ID de stratégie trop long. Cela est dû à la longueur maximale du chemin dans Windows. (Le plug-in Pepper n’a pas ce problème.) </p> <p>Voir watson 3549660 </p> 
    <ul id="ul_DFD527D1E1224A439766DF7BED878E3B"> 
     <li id="li_FAF8FD98A4E8478CA7A92F770676ADFC">Le logiciel du distributeur doit demander à l'utilisateur de confirmer que son répertoire d'utilisateurs n'est pas verrouillé, ni sur un volume plein ou verrouillé. </li> 
     <li id="li_6D1136EA750A459BBECEEE5F73F527BB">Si le distributeur utilise AIR, plutôt que Flash, le problème peut être causé par une limitation de longueur de chemin. <p>Les distributeurs doivent raccourcir le nom de leur application AIR pour qu'il soit raisonnable. Publiez également le contenu avec un <span class="codeph"> ID</span> de licence <span class="codeph"> plus court et un</span>ID de stratégie. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3314 </td> 
   <td colname="col2"><span class="codeph"> AAXS_CorruptedDRMMetadata </span> </td> 
   <td colname="col3"> <p>Cette erreur indique souvent que le contenu a été compressé avec des certificats PKI de test et que le lecteur est créé avec l’ICP de production ou vice versa. subErrorId contient une erreur spécifique au client ou une erreur de ligne. </p> 
    <ul id="ul_A122EF304CAF48A8B4DA1E3F4413E29B"> 
     <li id="li_A9A1A5B23E884C22A71E2DE7535FEB3B">Le logiciel du distributeur doit consigner le contenu qui a provoqué l'erreur. </li> 
     <li id="li_7AD7F13A4B1B4998A7E49664E7645815">Le distributeur doit confirmer que l'erreur est reproductible avec des éléments de contenu spécifiques. <p>Vous devrez peut-être recompresser le contenu rompu. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3315 </td> 
   <td colname="col2"><span class="codeph"> AAXS_PermissionDenied </span> </td> 
   <td colname="col3"> <p>Il existe des bogues connus dans lesquels ce code d’erreur est généré lorsqu’un 3305 est prévu. Pour plus d’informations, voir les causes et la résolution <a href="https://forums.adobe.com/thread/1284947" format="https" scope="external"> de</a>DRM 3305 [ServerConnectionFailed]. </p> <p>Le fichier SWF distant chargé par AIR n’est pas autorisé à accéder à la fonctionnalité Flash Access. Ce code d'erreur peut également être généré si une erreur de sécurité survient pendant l'accès au réseau. Par exemple, le serveur de destination ne permet pas au client de se connecter en utilisant crossdomain.xml, ou le fichier crossdomain.xml n’est pas accessible. </p> <p>Pour plus d’informations, voir <a href="https://forums.adobe.com/thread/1266592" format="https" scope="external"> Erreur DRM 3315, cause et résolution</a>possibles de la racine. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3316 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NOTUSED_MOVED </span> </td> 
   <td colname="col3"> Était ADOBECPSHIM_MinorErr_MissingAdobeCPModule <span class="codeph"></span>. Déplacé vers 3344 en raison d’un conflit avec le code d’erreur Flash. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3317 </td> 
   <td colname="col2"><span class="codeph"> AAXS_LoadAdobeCPFailing </span> </td> 
   <td colname="col3"> <p>Important :  Il s’agit d’une erreur rare qui ne se produit généralement pas dans un  de production . </p> <p>Si l’erreur se produit, vous pouvez effectuer l’une des opérations suivantes : 
     <ul id="ul_BC435E61623444BB98A86216531DC892"> 
      <li id="li_FA433D0758B642D2AFDCF04906B3FE18">Si vous utilisez AIR, réinstallez-le. </li> 
      <li id="li_F08D9AAFF46244F8842DEE5FD9CBBE0A">Si vous utilisez Flash Player, téléchargez à nouveau les modules <span class="codeph"> AdobeCP</span> . </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3318 </td> 
   <td colname="col2"><span class="codeph"> AAXS_IncompatibleAdobeCPVersion </span> </td> 
   <td colname="col3"> Non applicable pour Android. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3319 </td> 
   <td colname="col2"><span class="codeph"> AAXS_MissingAdobeCPGetAPI </span> </td> 
   <td colname="col3"> Non applicable pour Android. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3320 </td> 
   <td colname="col2"><span class="codeph"> AAXS_HostAuthenticateFailed </span> </td> 
   <td colname="col3"> Non applicable pour Android. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3321 </td> 
   <td colname="col2"><span class="codeph"> AAXS_I15nÉchec </span> </td> 
   <td colname="col3"> <p>Le processus de mise en service du client avec des clés a échoué. subErrorId contient une erreur spécifique au client, au serveur ou à la ligne. </p> 
    <ul id="ul_98D919B9060A441AACB6106F6D8E8DA7"> 
     <li id="li_DCAB00A8AC4A426CBBD377374B3F71AE">Le logiciel du distributeur doit recommencer l'opération au moins une fois. <p>Si vous utilisez Google Chrome sous Windows, fournissez une explication sur la manière d’autoriser l’accès aux modules externes qui ne se trouve pas dans un sandbox. Pour plus d’informations, voir Accès non sandbox de <a href="https://helpx.adobe.com/adobe-access/kb/error-3321.html" format="html" scope="external"> Google Chrome refusé</a>. </p> </li> 
     <li id="li_7FB7681FE32D444BB1BDBA3E5953A2C3">Le distributeur doit remplir l'un des  suivants : 
      <ul id="ul_486B64F187C44AE3B4775953A6142836"> 
       <li id="li_095B1D4CD051427CB2BFA7082B454056">Si l’erreur est cohérente sur toutes les plateformes, vous devez réaffecter le problème à Adobe. </li> 
       <li id="li_0C6EB7B912FA41E59657216498DA3515">Si l’erreur est limitée à Chrome sous Windows, demandez à l’utilisateur d’autoriser l’accès au module externe non sandbox. </li> 
      </ul> <p>Les distributeurs doivent mettre à jour leur fichier SWF vers la version 19 ou ultérieure, et l’erreur 3321 spécifique à Chrome renvoie une erreur 3368. L'erreur 3368 peut être traitée plus spécifiquement par le logiciel du distributeur. Cette modification a été introduite dans Chrome Stable  version 26.0.1410.43. </p> <p>Conseil : L’erreur <span class="codeph"> 3321:1090519056</span> peut se produire avec les versions 11.1 à 11.6 de Flash Player. Nous vous recommandons d’effectuer la mise à niveau vers la dernière version de Flash Player. </p> </li> 
    </ul> <p>Pour plus d’informations, voir <a href="https://forums.adobe.com/thread/1277138" format="https" scope="external"> Erreur DRM 3321 Causes &amp; Resolution</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Erreurs de corruption du magasin global</b> </td> 
   <td colname="col2"> </td>
   <td colname="col3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"> 3322 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DeviceBindingFailed </span> </td> 
   <td colname="col3"> <p>Le périphérique ne semble pas correspondre à la configuration qui était présente lors de l’initialisation. subErrorId contient une erreur de ligne ou spécifique au client. </p> <p>Le logiciel du distributeur doit compléter l'un des  suivants: 
     <ul id="ul_444401051A2E407B95BC44491E9BB71C"> 
      <li id="li_93493EA05DB44CB1AEC368663F1ABA8D"> <p>Si le périphérique n’utilise pas Flash Player et qu’il utilise AIR, iOS, etc., appelez <span class="codeph"> DRMManager.resetDRMVouchers()</span>. </p> <p>Si le problème survient sur iOS dans une phase de développement, demandez au développeur de confirmer si le problème est observé lors du basculement entre des versions téléchargées à partir de systèmes de distribution tiers préversion (par exemple, HockeyApp) et une version locale de Xcode. Les attributs d’une installation précédente ne sont pas entièrement remplacés lors du passage d’une version distribuée à partir de HockeyApp à une version de Xcode. Cette situation peut déclencher l’erreur 3322. </p> <p>Pour résoudre ce problème, le développeur doit supprimer l’ancienne version du périphérique avant d’installer la nouvelle version. </p> </li> 
      <li id="li_A5C9633F11584C788A2D9A23CC18FA6D">Si le périphérique utilise Flash Player et qu’il est inutilisable à partir d’un code d’erreur 3322 ou 3346, reportez-vous aux instructions d’Adobe sur la manière de réinitialiser par programmation votre magasin de licences DRM lors de l’erreur <a href="https://forums.adobe.com/message/5535907#5535907" format="https" scope="external"> DRM 3322/3346/3368 dans Chrome (problèmes de barre d’informations)</a>. </li> 
     </ul> </p> <p>Cette erreur ne devrait pas se produire fréquemment. Dans les  d’entreprise  qui utilisent un en itinérance, si un utilisateur visualisait un contenu protégé par DRM, le risque d’erreur 3322 se générait plus élevé lorsque l’utilisateur se connectait à partir de différentes machines. Dans la mesure du possible, le distributeur devrait essayer d'obtenir ces informations auprès de l'utilisateur. </p> <p>Si l’erreur se produit fréquemment, réaffectez-vous à Adobe. Vous devez indiquer à Adobe si la réinitialisation du magasin de licences a résolu (ou non) le problème et indiquer à Adobe sur quels navigateurs l’erreur s’est produite. </p> <p>Pour plus d’informations, reportez-vous aux articles suivants : 
     <ul id="ul_C468409D1EA046178CA7F54DCDCB84EA"> 
      <li id="li_20C8CA3853574CE486F21E7A3667DAB9"><a href="https://forums.adobe.com/message/5520902" format="https" scope="external"> https://forums.adobe.com/message/5520902</a> </li> 
      <li id="li_6E6F1BD6FE7843449B3E2F06F342EFF7"><a href="https://forums.adobe.com/message/5535911" format="https" scope="external"> https://forums.adobe.com/message/5535911</a> </li> 
      <li id="li_2BE40E513A0C4BAD900C7B69FEF5D690"><a href="https://forums.adobe.com/message/5748618" format="https" scope="external"> https://forums.adobe.com/message/5748618</a> </li> 
      <li id="li_9C2BD122E3874E2893DD43E082A877E0"><a href="https://forums.adobe.com/message/6061165" format="https" scope="external"> https://forums.adobe.com/message/6061165</a> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3323 </td> 
   <td colname="col2"><span class="codeph"> AAXS_CorruptGlobalStateStore </span> </td> 
   <td colname="col3"> <p>Les fichiers utilisés par le client DRM ont été modifiés de manière inattendue. subErrorId contient une erreur de ligne ou spécifique au client. </p> 
    <ul id="ul_96EA771046CA4B2B9FAE24D493F43FF2"> 
     <li id="li_D2693CD8EFEF46108828BA17E3F54FF6">Le logiciel du distributeur doit guider l'utilisateur à se réinitialiser de la même manière que pour 3322. </li> 
     <li id="li_0149B82436B64E28AC2B8C9B0EB09898">Si le GlobalStore échoue à un rythme supérieur au taux d’échec attendu des disques durs de votre base d’utilisateurs, réaffectez le problème à Adobe. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3324 </td> 
   <td colname="col2"><span class="codeph"> AAXS_MachineTokenInvalid </span> </td> 
   <td colname="col3"> Réinitialisez le  local DRM  pour cette application. Appelez DRMManager.resetDRM. <p>Le serveur de licences peut ne pas être en mesure de se connecter au serveur CRL (Certificate Revocation) pour actualiser ses fichiers CRL, ou l’ordinateur client demande une licence/authentification révoquée par le serveur de licences. </p> <p>Dans les journaux du serveur, un code d'erreur 111 est MachineTokenInvalid. Toutefois, au niveau du client, le code d’erreur 111 est traduit en code d’erreur 3324. </p> <p>L’administrateur du serveur de licences DRM doit vérifier si le serveur de licences du client a jamais pu récupérer les fichiers CRL Adobe. Si le client utilise Tomcat, il peut vérifier le répertoire<span class="filepath"> tomcat/temp/</span> pour savoir s’il existe 4 fichiers CRL. </p> 
    <ul id="ul_23B7F1A104AF49E79EA87DB8E15E337E"> 
     <li id="li_855D87F251184FE688A8D5FA0F6C9EF5">Si les fichiers se trouvent dans ce répertoire, cliquez  sur les fichiers dans l’Explorateur Windows et dans l’application du lecteur CRL, déterminez si l’un des fichiers a expiré. </li> 
     <li id="li_58EC4EDA2B5146188A0FF7B33C91E2FD">S’il n’y a aucun fichier dans tomcat/temp/, on peut supposer que ce serveur de licences n’a jamais pu accéder au serveur Adobe CRL en raison d’un problème de pare-feu/de . </li> 
    </ul> <p>Pour plus d’informations, voir Règles <a href="https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_secure_deployment_guidelines.pdf" format="http" scope="external"></a>de pare-feu. </p> <p>Si les fichiers CRL ne sont pas disponibles ou ont expiré, vous devez vérifier si le serveur de licences est accessible. Ouvrez un renifleur réseau sur le serveur de licences du client, redémarrez le serveur et demandez une licence au client. Vous pouvez observer le trafic réseau pour voir si les appels aux points de fin d’URL suivants sont réussis : <p>Conseil :  Vous pouvez également entrer les URL de liste CRL suivantes dans un navigateur pour savoir si vous pouvez télécharger manuellement chaque fichier. </p> 
     <ul id="ul_9B65C7ABBDEC4AC9BF3755FFD3587971"> 
      <li id="li_6867A9050E8D421C9138AC853D1784C9"><a href="https://crl2.adobe.com/Adobe/FlashAccessIndividualizationCA.crl" format="http" scope="external"> crl2.adobe.com/Adobe/FlashAccessIndividualizationCA.crl</a> </li> 
      <li id="li_6431689260554EAFAFDA2EC31798DCB5"><a href="https://crl2.adobe.com/Adobe/FlashAccessIntermediateCA.crl" format="http" scope="external"> crl2.adobe.com/Adobe/FlashAccessIntermediateCA.crl</a> </li> 
      <li id="li_2939674D0F854ADEB67E45FD216288A2"><a href="https://crl2.adobe.com/Adobe/FlashAccessRootCA.crl" format="http" scope="external"> crl2.adobe.com/Adobe/FlashAccessRootCA.crl</a> </li> 
      <li id="li_96386E00BE9D4CB99D100057A5F7C6DD">crl3.adobe.com/AdobeSystemsIncorporated FlashAccessRuntime/LatestCRL.crl</li> 
     </ul> </p> <p>Si les règles de pare-feu sont ouvertes et qu’il n’y a pas d’erreurs 3324 actuelles, il se peut qu’il y ait eu un problème de réseau temporaire. Vérifiez les journaux du serveur du client, qui se trouvent probablement dans le répertoire <span class="codeph"> /tomcat/logs/</span> , pour déterminer si une erreur s’est produite lorsque le serveur de licences a tenté de récupérer le de révocation des certificats. <p>Important :  Une erreur peut se produire lorsqu’un grand nombre (ou une explosion) de clients signalent une erreur 3324 à un problème réseau temporaire lors du renouvellement d’un fichier CRL. Lorsque le problème réseau a été résolu, les problèmes 3324 ont également été résolus. </p> </p> <p>Si les 4 fichiers CRL existent dans le répertoire <span class="filepath"> tomcat/temp/</span> et que les clients obtiennent toujours des codes d’erreur 3324, il se peut que des problèmes d’accès aux fichiers CRL se produisent. Pour résoudre ce problème, vous pouvez consulter les journaux et purger les fichiers CRL existants. </p> <p>S’il n’y a aucun problème de serveur, invitez l’utilisateur à se réinitialiser comme décrit dans la section 3322. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Erreurs de corruption de la banque de serveurs</b> </td> 
   <td colname="col2"> </td>
   <td colname="col3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"> 3325 </td> 
   <td colname="col2"><span class="codeph"> AAXS_CorruptServerStateStore </span> </td> 
   <td colname="col3"> <p>Les fichiers utilisés par le client DRM ont été modifiés de manière inattendue. <span class="codeph"> subErrorId</span> contient une erreur de ligne ou spécifique au client. </p> 
    <ul id="ul_860D2402DA61460AB0D938F1116F6D64"> 
     <li id="li_CF368C43452B4265B62ADA3E223894BA">Le logiciel du distributeur doit recommencer l’opération, car AdobeCP a supprimé le magasin du serveur concerné en interne et une nouvelle tentative doit réussir. Si une nouvelle tentative échoue, consignez le problème dans le journal. </li> 
     <li id="li_51A5803A1F754970BB4EBD6494F5DC96">Si le  échoue à un rythme supérieur au taux d’échec attendu des disques durs de votre base d’utilisateurs, réaffectez le problème à Adobe. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3326 </td> 
   <td colname="col2"><span class="codeph"> AAXS_StoreTamperingDetected </span> </td> 
   <td colname="col3"> Appelez <span class="codeph"> DRMManager.resetDRM</span>. <p>Le magasin de licences a été altéré/corrompu et ne peut plus être utilisé. </p> <p>Le logiciel du distributeur doit guider l'utilisateur à se réinitialiser de la même manière que décrit à la section 3322. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3327 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ClockTamperingDetected </span> </td> 
   <td colname="col3"> Corrigez l’horloge ou rachetez la licence <span class="codeph"> /Lic/Domain</span> . </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>Erreurs d’authentification/de licence/serveur de domaine</b> </td> 
   <td colname="col2"> </td>
   <td colname="col3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"> 3328 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ServerErrorTryagain </span> </td> 
   <td colname="col3"> <p>Il s’agit d’une erreur côté serveur où le serveur n’a pas pu terminer la requête du client. Cette erreur peut se produire lorsque, par exemple, le serveur est occupé, HTTP/500, que le serveur ne dispose pas de la clé nécessaire pour déchiffrer la requête, etc. </p> <p>Sur le client, il n'y a aucun moyen de déterminer ce qui a mal tourné. Le client doit consulter les journaux du serveur Adobe Access, généralement appelés <span class="codeph"> AdobeFlashAccess.log</span>, pour déterminer ce qui s’est mal passé. Il existe toujours une trace de pile descriptive dans le journal pour indiquer le problème. <span class="codeph"> subErrorId</span> contient une erreur de ligne ou spécifique au serveur. </p> <p>Le distributeur doit consulter les journaux du serveur pour identifier le serveur qui envoie cette erreur. Pour les erreurs 3328 comportant un code de sous-erreur 101, le serveur ne peut pas déchiffrer la requête. Le client doit vérifier que les certificats de licence/serveur de transport installés sur le serveur de licences correspondent aux certificats utilisés lors de l’assemblage. </p> <p>En outre, si les clients utilisent l’implémentation des références, ils doivent s’assurer qu’il n’y a pas de fautes de frappe dans le fichier <span class="codeph"> flashaccess-refimpl.properties</span> où les certificats principal et supplémentaire sont spécifiés. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3329 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ApplicationSpecificError </span> </td> 
   <td colname="col3"> <p>Le code de sous-erreur spécifique à l'application n'est pas connu de Flash Access. <span class="codeph"> subErrorId</span> contient une erreur spécifique au serveur provenant du serveur de licences personnalisé des éditeurs. Le serveur a renvoyé une erreur dans le  de  spécifique à l’application. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3330 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NeedAuthentication </span> </td> 
   <td colname="col3"> <p>Cette erreur se produit lorsque le contenu est configuré pour demander aux clients de s’authentifier avant d’obtenir les licences. </p> 
    <ul id="ul_712D29B8B5A6401FB014C4A283918E32"> 
     <li id="li_2D56905EB50D4FDEAD69CA8EAE38AD1A">Le logiciel du distributeur doit authentifier l'utilisateur, puis acquérir à nouveau la licence. <p>Si votre service n’a pas l’intention d’utiliser l’authentification, consignez l’identification du contenu à l’origine de cette erreur. </p> </li> 
     <li id="li_B3BCF899B8BE41C7A4F7CF84B0503483">Cette erreur ne doit pas nécessiter une réaffectation, sauf si le contenu n’est pas censé être configuré pour exiger une authentification. <p>Dans ce cas, reconditionnez le contenu offensant avec une stratégie appropriée. Si le contenu est correctement compressé, voir Diagnostic des divergences entre les stratégies et les licences. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <b>Erreurs d'application de la licence non couvertes ci-dessus</b> </td> 
   <td colname="col2"> </td>
   <td colname="col3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"> 3331 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ContentNotyetValid </span> </td> 
   <td colname="col3"> <p>La licence acquise n'est pas encore valide. Pour résoudre ce problème, vérifiez si l’horloge du client n’est pas correctement définie. Pour définir l’horloge du client, recompressez le contenu ou modifiez la configuration du serveur de licences. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3332 </td> 
   <td colname="col2"><span class="codeph"> AAXS_CachedLicenseExpired </span> </td> 
   <td colname="col3"> Récupérez la licence à partir du serveur. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3333 </td> 
   <td colname="col2"><span class="codeph"> AAXS_PlaybackWindowExpired </span> </td> 
   <td colname="col3"> <p>Vous devez informer les utilisateurs qu’ils ne peuvent pas lire ce contenu avant l’expiration de la stratégie. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3334 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InvalidDRMPlatform </span> </td> 
   <td colname="col3"> <p>Cette plate-forme n’est pas autorisée à lire le contenu, car, par exemple, le fournisseur de contenu a configuré Adobe Access pour qu’il refuse le contenu à Adobe Access sur une plateforme ou une licence liée à un domaine partagé est liée à un jeton de domaine partagé destiné à une partition différente. </p> <p>Le MDP peut renvoyer cette erreur si le contenu n'a pas été emballé en utilisant une certification appropriée (par défaut) d'emballeur. </p> <p>Si le contenu est compressé avec un certificat PHDS/PHLS incorrect, il se peut que le contenu fonctionne dans Chrome mais pas dans d’autres navigateurs (ou vice versa). <p>Conseil :  En effet, Chrome utilise différents certificats PHDS/PHLS. </p>Pour confirmer quel certificat est utilisé, videz les détails des métadonnées de contenu et recherchez les certificats <i>du</i>. Pour plus d’informations, voir <a href="https://adobeprimetime.zendesk.com/agent/tickets/2891" format="https" scope="external"> https://adobeprimetime.zendesk.com/agent/tickets/2891</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3335 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InvalidDRMVersion </span> </td> 
   <td colname="col3"> Mettez à niveau vers la dernière version de TVSDK pour Android. <p>Pour résoudre ce problème, effectuez l’une des  suivantes : 
     <ul id="ul_BF1742948BC9461CB8686DE70124D3CD"> 
      <li id="li_690D440C94CC45A0AE55EC319B1C4C23">Mise à niveau d’AIR </li> 
      <li id="li_CDD20251C881466E88BE7BBB53D61EBC">Pour Flash Player, mettez à niveau le module AdobeCP et réessayez la lecture. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3336 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InvalidRuntimePlatform </span> </td> 
   <td colname="col3"> <p>Cette plate-forme n’est pas autorisée à lire le contenu car, par exemple, le fournisseur de contenu a configuré Access pour refuser le contenu à FP/AIR sur une plateforme. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3337 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InvalidRuntimeVersion </span> </td> 
   <td colname="col3"> Mettez à niveau vers la dernière version de TVSDK pour Android. <p>Cela se produit si le contenu ou le serveur est configuré pour refuser la lecture à une version particulière des moteurs d’exécution Flash ou AIR. </p> 
    <ul id="ul_B0732D941256483CABBDD30C9BF43249"> 
     <li id="li_72782B1D638F48C0B87084689FB9C798">Si l’utilisateur se trouve sur un système d’exploitation sur lequel Flash peut être mis à niveau, le logiciel du distributeur doit demander à l’utilisateur de mettre à niveau Flash et de réessayer. Sinon, conseillez à l’utilisateur d’utiliser un autre ordinateur. </li> 
     <li id="li_1E3FD93CE39E43F2B7D961299B1211DA">Si l’erreur 3337s est suspectée, indiquez si elle se produit pour un contenu spécifique et reconditionnez-le. Si le contenu est correctement compressé, reportez-vous à la page Diagnostic des écarts entre les stratégies et les licences </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3338 </td> 
   <td colname="col2"><span class="codeph"> AAXS_UnknownConnectionType </span> </td> 
   <td colname="col3"> <p>Impossible de détecter le type de connexion et la stratégie requiert que vous activiez Output Protection. Ce problème est attendu uniquement si le contenu est compressé pour exiger une protection de sortie numérique ou analogique. </p> <p>Un problème dans les versions de Flash Player antérieures à la version 11.8.800.168 provoquait parfois l’erreur 3338 sur le contenu pour lequel la stratégie indiquait que la protection du contenu était <span class="codeph"> UTILISÉE SI DISPONIBLE</span>. Ce problème est corrigé dans les versions 11.8.800.168 et ultérieures. </p> 
    <ul id="ul_4B6CA26A53F84838B5B95400925464D4"> 
     <li id="li_CBD890F467E449EBB5116E1561252058">Le logiciel du distributeur sélectionne une variante du contenu qui ne nécessite pas de protection de sortie (par exemple, une variante SD d’un flux HD). <p>Si l’erreur 3338 se produit sur le <span class="codeph"> contenu USE_IF_AVAILABLE </span> , recherchez le numéro de version du lecteur. Si la version du lecteur est inférieure à 11.8.800.168, conseillez à l’utilisateur de mettre à niveau Flash Player. Si l’erreur 3338 se produit sur les versions supérieures à 11.8.800.168, consignez le contenu à l’origine de l’erreur. </p> </li> 
     <li id="li_62886C1D96264B129928A7E29E6C70E1">Le distributeur doit vérifier quel contenu est à l’origine de cette erreur et vérifier que la stratégie du contenu définit <span class="codeph"> NO_PROTECTION</span> ou <span class="codeph"> USE_IF_AVAILABLE</span> pour les sorties analogiques et numériques. <p>Si le contenu est inclus par inadvertance dans un package avec <span class="codeph"> NO_OUTPUT</span> ou <span class="codeph"> REQUIRED</span>, recompressez le contenu. Si le contenu est correctement compressé, reportez-vous à la page Diagnostic des différences entre les stratégies et les licences. Sinon, réaffectez-vous à Adobe. </p> </li> 
    </ul> <p>Pour plus d’informations, voir <a href="https://forums.adobe.com/message/5518688" format="https" scope="external"> Obtention d’erreurs 3338 inattendues lorsque votre stratégie DRM est définie sur USE_IF_AVAILABLE ?</a> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3339 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoAnalogPlaybackAllowed </span> </td> 
   <td colname="col3"> Lecture impossible sur un périphérique analogique. Pour résoudre ce problème, connectez un périphérique numérique. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3340 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoAnalogProtectionAvail </span> </td> 
   <td colname="col3"> Impossible de lire le contenu, car le périphérique d’affichage externe analogique (moniteur/TV) connecté n’a pas les fonctionnalités appropriées (par exemple, le périphérique n’a pas de Macrovision ou ACP). </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3341 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoDigitalPlaybackAllowed </span> </td> 
   <td colname="col3"> Impossible de lire le contenu sur un périphérique numérique. <p>Important :  Ce problème ne doit pas se produire dans un  de production , car les éditeurs de contenu ne doivent pas interdire la lecture numérique. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3342 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoDigitalProtectionAvail </span> </td> 
   <td colname="col3"> Le périphérique d’affichage numérique externe (moniteur/TV) connecté ne dispose pas des fonctionnalités appropriées. Par exemple, le périphérique ne dispose pas de HDCP. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3343 </td> 
   <td colname="col2"><span class="codeph"> AAXS_IntegrityVerifyFailed </span> </td> 
   <td colname="col3"> <p>Non applicable pour Android. </p> <p>Cette erreur est connue pour se produire initialement après la publication d’une nouvelle version de Flash. Cela se produit car Flash a été mis à niveau pendant l’ouverture de Flash, ce qui met Flash dans un état incorrect jusqu’au redémarrage du navigateur. </p> 
    <ul id="ul_A0AC4A77550E40409A04BD33748EA987"> 
     <li id="li_F41C1ABD838D41ABB0DF65093E664A29">Le logiciel du distributeur doit remplir le  suivant : 
      <ul id="ul_79B2AB1372074D448F129851AA24F985"> 
       <li id="li_B93EDD263D78434FAF198A01938D3508">Recommandez à l’utilisateur de fermer ou de quitter tous les navigateurs, puis de rouvrir. </li> 
       <li id="li_ADFBCFA66AD849E18DB390455458528E">Vérifiez si la version de Flash est actuelle. <p>Si la version n’est pas actuelle, conseillez au client de mettre à niveau, de fermer tous les onglets de son navigateur, puis de rouvrir. </p> </li> 
      </ul> </li> 
     <li id="li_281B54582B5949AEA7D166246917EE41">Si une erreur semble se produire après un redémarrage réussi du navigateur, réaffectez-vous à Adobe. <p>Lorsqu’une nouvelle version est publiée, nous vous recommandons de contacter l’assistance technique d’Adobe pour savoir si le problème des mises à jour en arrière-plan a été résolu. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3344 </td> 
   <td colname="col2"><span class="codeph"> AAXS_MissingAdobeCPModule </span> </td> 
   <td colname="col3"> Non applicable pour Android. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3345 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DRMNoAccessError </span> </td> 
   <td colname="col3"> <p>Non applicable pour Android. </p> <p>Cette erreur se produit lorsqu’une partie de Flash ou AIR n’a pas été correctement installée. </p> <p>Le logiciel du distributeur doit effectuer l'une des opérations suivantes: 
     <ul id="ul_D1188E2D4FDF4BD89A04F5629D75D981"> 
      <li id="li_B33FBCA5D4534D668B86A5E93DB3A809">Demandez à l’utilisateur de désinstaller et de réinstaller AIR. </li> 
      <li id="li_B7D2388E9FA84C26AF1C87B48AF9EF16">Pour Flash Player, appelez <span class="codeph"> System.update</span>. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3346 </td> 
   <td colname="col2"><span class="codeph"> AAXS_MigrationFailed </span> </td> 
   <td colname="col3"> 
    <ul id="ul_518AD4931CC64EB3A962DD451E6C5067"> 
     <li id="li_3C44F0740B08490E9C62D89C40B57DC2">Le logiciel du distributeur doit effectuer l'une des opérations suivantes: 
      <ul id="ul_7D90526684BF4EB2BBADCF598AA13086"> 
       <li id="li_D15B4BEDAF7340F6B9BC886DF6E346EC">Si AIR, appelez <span class="codeph"> DRMManager.resetDRMVouchers()</span> </li> 
       <li id="li_40A51D35408249CFA28DBC49FDA3408B">Si le code d’erreur 3322 ou 3346 de Flash est inutilisable, les utilisateurs doivent se rendre sur <a href="https://forums.adobe.com/message/5535907#5535907" format="http" scope="external"> https://forums.adobe.com/message/5535907#5535907</a> et suivre les instructions de l’article Adobe pour réinitialiser par programmation leur magasin de licences DRM. </li> 
      </ul> </li> 
     <li id="li_0464471E4A094C80BF2986694341921A">Si cette erreur se produit fréquemment, le distributeur doit fournir à Adobe les détails concernant la version du lecteur de fréquence et la version du navigateur. </li> 
    </ul> <p>Pour plus d’informations, reportez-vous aux articles suivants du forum : 
     <ul id="ul_44E0077FEAA749CC9549BF3846065304"> 
      <li id="li_2BE3B2443380415DA73B7AA3B6547B31"><a href="https://forums.adobe.com/message/5520902" format="https" scope="external"> Erreur DRM 3322/3346/3368 dans Chrome (Problèmes de barre d’informations)</a> </li> 
      <li id="li_4E5C7414756644E1AB78BE7B8112228C"><a href="https://forums.adobe.com/message/5535911" format="https" scope="external"> Erreur 3322 ou 3346 après modification matérielle</a> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3347 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InsuffisammentDeviceCapabilites </span> </td> 
   <td colname="col3"> <p>La principale signification de cette erreur est que la licence a une contrainte que le certificat DRM du client indique qu’elle ne peut pas satisfaire. Les "fonctionnalités matérielles" suivantes sont définies lors de l’émission du certificat DRM du client : 
     <ul id="ul_1EB6F1469C244CF0BA52C212495C053D"> 
      <li id="li_646043CE045C4DE2BBC939E1F4963DFE"><b>Bus</b>accessible aux non-utilisateurs. Si c’est <b>vrai</b>, le média déchiffré ne traverse jamais un bus ou dans la mémoire principale où une application peut y accéder. <p>Si la valeur est <b>false</b>, le contenu peut être accessible à l’application après le déchiffrement. </p> </li> 
      <li id="li_02AAECAF4D35447BA10554541B46DE67"><b>La racine matérielle de la confiance</b>. Si la valeur est <b>true</b>, tous les logiciels chargés au démarrage sur le périphérique ont été validés par rapport à une clé ou à un condensé disponible uniquement sur le matériel. <p>Ces deux contraintes sont vérifiées côté client lorsque la licence est ouverte par rapport au certificat DRM du client et que l’échec est immédiat. Ces contraintes peuvent également être vérifiées côté serveur avant la délivrance de la licence. </p> </li> 
     </ul> </p> <p>La signification secondaire de cette erreur est que la licence a le jeu de stratégies "Application de Jailbreak" et qu’une interruption de prison a été détectée sur l’appareil. Cette vérification est effectuée régulièrement du côté client et ne peut pas être vérifiée du côté serveur. </p> <p>Les distributeurs peuvent mettre à jour les politiques et supprimer les restrictions. Pour les stratégies de capacité de périphérique, exécutez la commande de mise à jour de stratégie avec l’indicateur <span class="codeph"> -devCapabilitiesV1</span> et aucun argument. Pour l’application de l’arrêt de prison, définissez <span class="codeph"> .applyJailbreak=false</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3348 </td> 
   <td colname="col2"><span class="codeph"> AAXS_HardStopIntervalExpired </span> </td> 
   <td colname="col3"> Intervalle d'arrêt fixe expiré. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3349 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ServerVersionTooHigh </span> </td> 
   <td colname="col3"> Le serveur s’exécute dans une version supérieure à la version la plus élevée prise en charge par le client. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3350 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ServerVersionTooLow </span> </td> 
   <td colname="col3"> Le serveur s’exécute dans une version inférieure à la version minimale prise en charge par le client. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3351 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DomainTokenInvalid </span> </td> 
   <td colname="col3"> Jeton de domaine non valide. Pour résoudre ce problème, inscrivez-vous à nouveau avec le domaine. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3352 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DomainTokenTooOld </span> </td> 
   <td colname="col3"> Le jeton de domaine est plus ancien que le jeton requis par la licence. Pour résoudre ce problème, enregistrez-vous de nouveau auprès du domaine. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3353 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DomainTokenTooNew </span> </td> 
   <td colname="col3"> Le jeton de domaine est plus récent que le jeton requis par la licence. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3354 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DomainTokenExpired </span> </td> 
   <td colname="col3"> Le jeton de domaine a expiré. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3355 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DomainJoinFailed </span> </td> 
   <td colname="col3"> Échec de la jonction de domaine. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3356 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoCorrespondantRoot </span> </td> 
   <td colname="col3"> Licence racine introuvable pour une licence feuille V3. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3357 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoValidEmbeddedLicense </span> </td> 
   <td colname="col3"> Aucune licence incorporée valide n'a été trouvée. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3358 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoACPProprotectionAvail </span> </td> 
   <td colname="col3"> Impossible de lire, car le périphérique analogique connecté ne dispose pas de la protection ACP. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3359 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoCGMSAPprotectionAvail </span> </td> 
   <td colname="col3"> Impossible de lire, car le périphérique analogique connecté ne dispose pas de la protection CGMS-A. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3360 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DomainRegistrationRequired </span> </td> 
   <td colname="col3"> Le contenu nécessite l’enregistrement du domaine. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3361 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NotRegisteredToDomain </span> </td> 
   <td colname="col3"> L'ordinateur n'est pas enregistré dans le domaine pour les métadonnées spécifiées. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3362 </td> 
   <td colname="col2"><span class="codeph"> AAXS_OperationTimeoutError </span> </td> 
   <td colname="col3"> L’opération asynchrone a pris plus de temps que <span class="codeph"> maxOperationTimeout</span>. Uniquement renvoyé par iOS DRMNative Framework. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3363 </td> 
   <td colname="col2"><span class="codeph"> AAXS_UnsupportedIOSPlaylistError </span> </td> 
   <td colname="col3"> La liste de lecture M3U8 transmise contenait du contenu non pris en charge. Uniquement renvoyé par iOS DRMNative Framework. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3364 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoDeviceId </span> </td> 
   <td colname="col3"> <p>La structure a demandé l’ID du périphérique, mais la valeur renvoyée était vide. </p> <p>L’utilisateur ne doit pas cocher la case <span class="uicontrol"> Autoriser les identifiants pour le contenu</span> protégé dans les paramètres Chrome. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3365 </td> 
   <td colname="col2"><span class="codeph"> AAXS_IncognitoModeNotAllowed </span> </td> 
   <td colname="col3"> <p>Cette combinaison navigateur/plate-forme n’autorise pas la lecture protégée par DRM en mode Incognito. </p> <p>Le logiciel du distributeur doit conseiller à l'utilisateur de quitter le mode Incognito ou d'utiliser un autre navigateur. Pour plus d’informations, voir <a href="https://forums.adobe.com/thread/1266622" format="https" scope="external"> Cause et résolution</a>de l’erreur DRM 3365. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3366 </td> 
   <td colname="col2"><span class="codeph"> AAXS_BadParameter </span> </td> 
   <td colname="col3"> <p>Le runtime hôte a appelé la bibliothèque Access avec un paramètre incorrect. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3367 </td> 
   <td colname="col2"><span class="codeph"> AAXS_BadSignature </span> </td> 
   <td colname="col3"> Échec de la signature du manifeste m3u8. Uniquement renvoyé par iOS DRMNative Framework ou AVE. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3368 </td> 
   <td colname="col2"><span class="codeph"> AAXS_UserSettingsNoAccess</span> </td> 
   <td colname="col3"> <p>L’utilisateur a annulé l’opération ou a saisi des paramètres qui interdisent l’accès au système. </p> <p>Cette erreur n’est générée que lorsque la version SWF est 19 ou une version ultérieure. Pour une compatibilité descendante, la valeur 3321 est générée lorsque le fichier SWF est de la version 18 ou antérieure. </p> <p>Le logiciel du distributeur doit guider l'utilisateur vers une explication de la façon d'autoriser l'accès au module externe non sandbox. Pour plus d’informations, reportez-vous à la section Accès non sandbox de <a href="https://helpx.adobe.com/adobe-access/kb/error-3321.html" format="html" scope="external"> Google Chrome refusé</a> et Erreur <a href="https://forums.adobe.com/message/5520902" format="https" scope="external"> DRM 3322/3346/3368 dans Chrome (Problèmes de barre d’informations)</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3369 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InterfaceNotAvailable</span> </td> 
   <td colname="col3"> <p>Aucune interface de navigateur requise n’est disponible. Ce problème survient uniquement sur Pepper. Il peut y avoir une incohérence entre le module externe Flash et la version du navigateur. </p> <p>Le logiciel du distributeur doit guider l'utilisateur pour qu'il dispose de la dernière version du navigateur. </p> <p> Si les incidents de cette erreur augmentent et correspondent à une mise à jour du navigateur en cours de publication, réaffectez-vous à Adobe. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3370 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ContentIdSettingsNoAccess</span> </td> 
   <td colname="col3"> <p>L’utilisateur a désactivé les identifiants <span class="uicontrol"> Autoriser pour le paramètre de contenu</span> protégé. </p> <p>Conseil :  Cette erreur s’affichait avec les versions 13.0.0.x ou ultérieures de Pepper. </p> <p>Le logiciel du distributeur doit guider l’utilisateur pour activer les identifiants <span class="uicontrol"> Allow pour le paramètre de contenu</span> protégé. </p> <p>L’équipe d’exploitation du distributeur doit guider l’utilisateur pour activer les identifiants <span class="uicontrol"> Autoriser pour le paramètre de contenu</span> protégé. </p> <p>Pour plus d’informations, voir <a href="https://forums.adobe.com/message/6518323#6518323" format="https" scope="external"> https://forums.adobe.com/message/6518323#6518323</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3371 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoOPConstraintInPixel</span><span class="codeph"> Constraints</span> </td> 
   <td colname="col3"> <p>Résolution incorrecte basée sur les contraintes de protection de sortie dans la licence. </p> <p>Le logiciel du distributeur doit afficher un message d’erreur. Demandez à l’utilisateur de signaler le problème au distributeur avec un titre de contenu. </p> <p>Le distributeur doit recompresser le contenu avec une stratégie valide. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3372 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ResolutionLargerThanMaxResolution</span> </td> 
   <td colname="col3"> <p>La résolution du contenu est supérieure à la résolution maximale spécifiée dans la contrainte de protection de sortie. </p> <p>Si l’équipe d’exploitation du distributeur détecte cette erreur dans ses journaux, il doit revoir la politique de protection de la sortie basée sur la résolution et, si nécessaire, reconditionner le contenu. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3373 </td> 
   <td colname="col2"><span class="codeph"> AAXS_MinorErr_DisplayResolutionLargerThanConserver</span> </td> 
   <td colname="col3"> <p>La résolution du contenu est supérieure à la résolution spécifiée par la contrainte active de protection de sortie. </p> <p>Si l’équipe d’exploitation du distributeur détecte cette erreur dans ses journaux, il doit revoir la politique de protection de la sortie basée sur la résolution et, si nécessaire, reconditionner le contenu. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3374 </td> 
   <td colname="col2"><span class="codeph"> AAXS_MinorErr_ClientCommProcessFailed</span> </td> 
   <td colname="col3"> <p>Échec lors du traitement de la communication côté client, par exemple, génération de requêtes, traitement de réponse, jeton d’authentification incorrect, etc. </p> <p>Si l’équipe d’exploitation du distributeur détecte cette erreur dans ses journaux, il doit vérifier la politique de protection de la sortie basée sur la résolution et, si nécessaire, reconditionner le contenu. </p> </td> 
  </tr> 
 </tbody> 
</table>

## NATIVE_ERROR : Valeurs de lecture vidéo {#section_7079501250C2487499639F92EC774525}

L’interface Video Encoder de l’AVE renvoie ces notifications de lecture vidéo dans l’objet `NATIVE_ERROR` de métadonnées.

<table id="table_5EEB1F60E5854452A8B0BABBE9B32651"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Valeur de la clé de métadonnées NATIVE_ERROR_CODE </th> 
   <th colname="col2" class="entry"> Valeur de la clé de métadonnées NATIVE_ERROR_NAME </th> 
   <th colname="col3" class="entry"> Description </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> -1 </td> 
   <td colname="col2"><span class="codeph"> END_OF_PERIOD</span> </td> 
   <td colname="col3"> Fin de période. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 0 </td> 
   <td colname="col2"><span class="codeph"> SUCCÈS</span> </td> 
   <td colname="col3"> Opération réussie. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 1 </td> 
   <td colname="col2"> <span class="codeph"> ASYNC_OPERATION_IN_PROGRESS</span> </td> 
   <td colname="col3"> Opération asynchrone. La demande d'opération a été effectuée. Les informations de réussite/échec seront disponibles ultérieurement. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 2 </td> 
   <td colname="col2"><span class="codeph"> EOF</span> </td> 
   <td colname="col3"> Opération impossible en raison de la condition de fin de fichier (EOF). </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3 </td> 
   <td colname="col2"><span class="codeph"> DECODER_FAILED</span> </td> 
   <td colname="col3"> Échec du décodeur au moment de l’exécution. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 4 </td> 
   <td colname="col2"><span class="codeph"> DEVICE_OPEN_ERROR</span> </td> 
   <td colname="col3"> Échec de l'ouverture du décodeur matériel. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 5 </td> 
   <td colname="col2"><span class="codeph"> FILE_NOT_FOUND </span> </td> 
   <td colname="col3"> Impossible de localiser la ressource. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 6 </td> 
   <td colname="col2"><span class="codeph"> GENERIC_ERROR </span> </td> 
   <td colname="col3"> Erreur générique. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 7 </td> 
   <td colname="col2"><span class="codeph"> IRRECOVERABLE_ERROR </span> </td> 
   <td colname="col3"> Condition d’erreur à laquelle le moteur vidéo ne peut pas récupérer. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 8 </td> 
   <td colname="col2"><span class="codeph"> LOST_CONNECTION_RECOVERABLE </span> </td> 
   <td colname="col3"> Erreur réseau, tentative de récupération. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 9 </td> 
   <td colname="col2"><span class="codeph"> NO_FIXED_SIZE </span> </td> 
   <td colname="col3"> Impossible de déterminer la taille de la ressource. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 10 </td> 
   <td colname="col2"><span class="codeph"> NOT_IMPLEMENTED </span> </td> 
   <td colname="col3"> Fonction non implémentée. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 11 </td> 
   <td colname="col2"><span class="codeph"> OUT_OF_MEMORY </span> </td> 
   <td colname="col3"> Mémoire insuffisante. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 12 </td> 
   <td colname="col2"><span class="codeph"> PARSE_ERROR </span> </td> 
   <td colname="col3"> Erreur lors de l'analyse du fichier multimédia. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 13 </td> 
   <td colname="col2"><span class="codeph"> TAILLE_INCONNUE </span> </td> 
   <td colname="col3"> La ressource a une taille, mais elle est inconnue. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 14 </td> 
   <td colname="col2"><span class="codeph"> UNDER_FLOW </span> </td> 
   <td colname="col3"> Condition de débordement. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 15 </td> 
   <td colname="col2"><span class="codeph"> UNSUPPORTED_CONFIG </span> </td> 
   <td colname="col3"> La configuration n’est pas prise en charge. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 16 </td> 
   <td colname="col2"><span class="codeph"> UNSUPPORTED_OPERATION </span> </td> 
   <td colname="col3"> Opération non prise en charge. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 17 </td> 
   <td colname="col2"><span class="codeph"> WAITING_FOR_INIT </span> </td> 
   <td colname="col3"> Pas encore initialisé. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 18 </td> 
   <td colname="col2"><span class="codeph"> INVALID_PARAMETER </span> </td> 
   <td colname="col3"> Paramètre non valide. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 19 </td> 
   <td colname="col2"><span class="codeph"> INVALID_OPERATION</span> </td> 
   <td colname="col3"> Opération non autorisée. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 20 </td> 
   <td colname="col2"><span class="codeph"> OP_ONLY_ALLOWED_IN_PAUSED_STATE</span> </td> 
   <td colname="col3"> L’opération n’est autorisée que lorsqu’elle est en pause. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 21 </td> 
   <td colname="col2"><span class="codeph"> OP_INVALID_WITH_AUDIO_ONLY_FILE</span> </td> 
   <td colname="col3"> Cette opération ne peut pas être utilisée sur des fichiers audio uniquement. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 22 </td> 
   <td colname="col2"><span class="codeph"> PREVIOUS_STEP_SEEK_IN_PROGRESS</span> </td> 
   <td colname="col3"> L'opération de recherche précédente est toujours en cours. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 23 </td> 
   <td colname="col2"><span class="codeph"> SOURCE_NOT_SPECIFIED </span> </td> 
   <td colname="col3"> Ressource non spécifiée. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 24 </td> 
   <td colname="col2"><span class="codeph"> RANGE_ERROR</span> </td> 
   <td colname="col3"> La valeur spécifiée est hors limites. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 25 </td> 
   <td colname="col2"><span class="codeph"> INVALID_SEEK_TIME</span> </td> 
   <td colname="col3"> Heure de recherche non valide. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 26 </td> 
   <td colname="col2"><span class="codeph"> FILE_STRUCTURE_INVALID</span> </td> 
   <td colname="col3"> Le fichier spécifié n’est pas conforme à la syntaxe attendue. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 27 </td> 
   <td colname="col2"><span class="codeph"> COMPONENT_CREATION_FAILURE</span> </td> 
   <td colname="col3"> Impossible de créer un composant essentiel. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 28 </td> 
   <td colname="col2"><span class="codeph"> DRM_INIT_ERROR</span> </td> 
   <td colname="col3"> Impossible de créer le contexte DRM. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 29 </td> 
   <td colname="col2"><span class="codeph"> _NOT_SUPPORTED </span> </td> 
   <td colname="col3"> Le type de  n’est pas pris en charge. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 30 </td> 
   <td colname="col2"><span class="codeph"> SEEK_FAILED</span> </td> 
   <td colname="col3"> Échec de la recherche. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 31 </td> 
   <td colname="col2"><span class="codeph"> CODEC_NOT_SUPPORTED</span> </td> 
   <td colname="col3"> Codec non pris en charge. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 32 </td> 
   <td colname="col2"><span class="codeph"> NETWORK_UNAVAILABLE</span> </td> 
   <td colname="col3"> Le réseau n'est pas disponible. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 33 </td> 
   <td colname="col2"><span class="codeph"> NETWORK_ERROR</span> </td> 
   <td colname="col3"> Erreur lors de l'obtention des données du réseau. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 34 </td> 
   <td colname="col2"><span class="codeph"> DÉBORDEMENT</span> </td> 
   <td colname="col3"> Débordement. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 35 </td> 
   <td colname="col2"><span class="codeph"> VIDEO___NOT_SUPPORTED</span> </td> 
   <td colname="col3">  vidéo non pris en charge. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 36 </td> 
   <td colname="col2"><span class="codeph"> PERIOD_NOT_LOADED</span> </td> 
   <td colname="col3"> Une opération a été tentée sur une période HOLD ou une période qui n'a pas encore été chargée. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 37 </td> 
   <td colname="col2"><span class="codeph"> INVALID_REPLACE_DURATION</span> </td> 
   <td colname="col3"> La durée de remplacement spécifiée n’est pas valide ou s’étend au-delà de la fin du flux. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 38 </td> 
   <td colname="col2"><span class="codeph"> APPELLED_FROM_WRONG_THREAD</span> </td> 
   <td colname="col3"> L'API ne peut pas être appelée à partir du mauvais thread. Surtout pour les éléments d’API qui doivent être appelés à partir du thread principal uniquement. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 39 </td> 
   <td colname="col2"><span class="codeph"> FRAGMENT_READ_ERROR</span> </td> 
   <td colname="col3"> Erreur de lecture du fragment. Aucun basculement n'est présent. Le moteur essaiera de lire le fragment suivant. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 40 </td> 
   <td colname="col2"><span class="codeph"> ABORDÉ</span> </td> 
   <td colname="col3"> L’opération a été abandonnée par un appel explicite Abandonner ou Détruire. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 41 </td> 
   <td colname="col2"><span class="codeph"> UNSUPPORTED_HLS_VERSION</span> </td> 
   <td colname="col3"> Impossible de lire cette version du média HLS. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 42 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_FAIL_OVER</span> </td> 
   <td colname="col3"> Impossible d'échouer. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 43 </td> 
   <td colname="col2"><span class="codeph"> HTTP_TIME_OUT</span> </td> 
   <td colname="col3"> Le téléchargement HTTP a expiré. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 44 </td> 
   <td colname="col2"><span class="codeph"> NETWORK_DOWN </span> </td> 
   <td colname="col3"> La connexion réseau de l’utilisateur est hors service. La lecture peut s’arrêter à tout moment et reprendra lorsque la connexion sera disponible. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 45 </td> 
   <td colname="col2"><span class="codeph"> NO_USABLE_BITRATE_</span> </td> 
   <td colname="col3"> Aucun de débit binaire utilisable  trouvé dans le flux. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 46 </td> 
   <td colname="col2"><span class="codeph"> BAD_MANIFEST_SIGNATURE</span> </td> 
   <td colname="col3"> Le manifeste a une mauvaise signature. Le test de signature du manifeste a échoué. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 47 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_LOAD_PLAYLIST</span> </td> 
   <td colname="col3"> Impossible de charger une liste de lecture. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 48 </td> 
   <td colname="col2"><span class="codeph"> REPLACEMENT_FAILED</span> </td> 
   <td colname="col3"> Le remplacement spécifié dans une API d'insertion n'a pas pu réussir. Cela signifie que l’insertion a réussi mais que le remplacement n’a pas eu lieu. Le remplacement peut échouer si le manifeste à remplacer a été supprimé du plan de montage chronologique. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 49 </td> 
   <td colname="col2"><span class="codeph"> SWITCH_TO_ASYMMETRIC_</span> </td> 
   <td colname="col3"> DRM passe à un  asymétrique. Tous les  du doivent être alignés dans la durée. Si ce n’est pas le cas, cet avertissement est généré et il se peut qu’il y ait des sauts dans la lecture. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 50 </td> 
   <td colname="col2"><span class="codeph"> LIVE_WINDOW_MOVED_BACKWARD</span> </td> 
   <td colname="col3"> La fenêtre dynamique ne doit avancer que vers l’avant. Si ce n'est pas le cas, cet avertissement sera lancé et la fenêtre ne sera pas lue. Pour cette raison, il peut y avoir des sauts (ou une longue pause/arrêt) dans la lecture. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 51 </td> 
   <td colname="col2"><span class="codeph"> CURRENT_PERIOD_EXPIRED</span> </td> 
   <td colname="col3"> La fenêtre dynamique a dépassé la période actuelle. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 52 </td> 
   <td colname="col2"><span class="codeph"> CONTENT_LENGTH_MISMATCH</span> </td> 
   <td colname="col3"> La longueur de contenu signalée par le serveur HTTP ne correspondait pas à la taille réelle du média. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 53 </td> 
   <td colname="col2"><span class="codeph"> PERIOD_HOLD</span> </td> 
   <td colname="col3"> Le lecteur de médias ne peut pas lire davantage, car il a atteint l’heure définie par l’API setHoldAt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 54 </td> 
   <td colname="col2"><span class="codeph"> LIVE_HOLD </span> </td> 
   <td colname="col3">Le lecteur de médias ne peut pas charger les segments, car il a atteint la fin de la fenêtre active. Le chargement des segments reprend lorsque le serveur ajoute de nouveaux médias à la fenêtre active. Cet état est généralement atteint si : 
    <ul id="ul_FCFF658EDA4144E59970B317D6DEB624"> 
     <li id="li_2F6EEEB782D54CD999BC7CC7C0B78B48">La valeur <span class="codeph"> bufferTime</span> est trop élevée (égale ou supérieure à la durée de la fenêtre active). </li> 
     <li id="li_25CE97115ED64E44AA89977FB5F0DCF7">Une combinaison d’une ou de plusieurs API d’insertion/effacement a remplacé plus de supports qu’elle n’en a ajouté. </li> 
     <li id="li_1B14716B2157492AB1859306D1250523">La période suivante est une période de production avec un remplacement de média en attente (en raison de l'appel de l'API InsertBy) </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 55 </td> 
   <td colname="col2"><span class="codeph"> BAD_MEDIA_INTERLEAVING </span> </td> 
   <td colname="col3"> L’interlettrage audio et vidéo dans le média n’est pas effectué correctement. Il s’agit d’une erreur de création de package. L’avertissement est envoyé lorsque la différence dépasse deux secondes. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 56 </td> 
   <td colname="col2"><span class="codeph"> DRM_NOT_AVAILABLE</span> </td> 
   <td colname="col3"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 57 </td> 
   <td colname="col2"><span class="codeph"> PLAYBACK_NOT_AUTHORIZED</span> </td> 
   <td colname="col3"> La lecture HLS n’a pas été activée dans le lecteur Flash. Voir AuthorizedFeatures.enableHLSPlayback. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 58 </td> 
   <td colname="col2"><span class="codeph"> BAD_MEDIA_SAMPLE_FOUND</span> </td> 
   <td colname="col3"> Le décodeur a reçu un échantillon incorrect qui ne peut pas être décodé. Il ne s’agit généralement pas d’une erreur fatale, mais cela indique qu’il peut y avoir des problèmes dans l’audio/la vidéo. Trop d'instances de cette erreur indiquent un mauvais codage ou un fichier incorrect. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 59 </td> 
   <td colname="col2"><span class="codeph"> RANGE_SPANS_READ_HEAD</span> </td> 
   <td colname="col3"> Une fois la lecture commencée, la plage Insérer/Remplacer ne doit pas contenir le titre de lecture. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 60 </td> 
   <td colname="col2"><span class="codeph"> POSTROLL_WITH_LIVE_NOT_ALLOWED</span> </td> 
   <td colname="col3"> Les insertions postroulantes ne sont pas autorisées sur un support en direct. Elles sont toutefois autorisées une fois que le serveur a marqué le média comme terminé. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 61 </td> 
   <td colname="col2"><span class="codeph"> INTERNAL_ERROR</span> </td> 
   <td colname="col3"> Une question très rare qui ne devrait jamais se produire. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 62 </td> 
   <td colname="col2"><span class="codeph"> SPS_PPS_FOUND_OUTSIDE_AVCC</span> </td> 
   <td colname="col3"> Le flux ne suit pas la recommandation de création de package de toujours placer H264 SPS/PPS dans un AVCC. Des problèmes de recherche/lecture peuvent être affichés. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 63 </td> 
   <td colname="col2"><span class="codeph"> PARTIAL_REPLACEMENT</span> </td> 
   <td colname="col3"> Le remplacement spécifié dans une API d'insertion n'a été que partiellement effectué. Cela se produit lorsque replaceDuration s’étend sur la durée du plan de montage chronologique. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 64 </td> 
   <td colname="col2"><span class="codeph"> RENDITION_M3U8_ERROR</span> </td> 
   <td colname="col3"> Une erreur de chargement s’est produite dans la liste de lecture du rendu. Il s’agit uniquement d’AVE, et non de FlashPlayer. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 65 </td> 
   <td colname="col2"><span class="codeph"> NULL_OPERATION</span> </td> 
   <td colname="col3"> L'opération ne fait rien. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 66 </td> 
   <td colname="col2"><span class="codeph"> SEGMENT_SKIPPED_ON_FAILURE</span> </td> 
   <td colname="col3"> Impossible de lire le segment et est ignoré en cas d’échec. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 67 </td> 
   <td colname="col2"><span class="codeph"> INCOMPATIBLE_RENDER_MODE</span> </td> 
   <td colname="col3"> Mode de rendu incompatible. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 68 </td> 
   <td colname="col2"><span class="codeph"> PROTOCOL_NOT_SUPPORTED </span> </td> 
   <td colname="col3"> Le protocole Web utilisé dans l’URL n’est pas pris en charge. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 69 </td> 
   <td colname="col2"><span class="codeph"> PARSE_ERROR_INCOMPATIBLE_VERSION</span> </td> 
   <td colname="col3"> Erreur lors de l'analyse du fichier multimédia. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 70 </td> 
   <td colname="col2"><span class="codeph"> MANIFEST_FILE_UNEXPECTEDLY_CHANGED</span> </td> 
   <td colname="col3"> Le fichier manifeste a été modifié de manière inattendue. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 71 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_SPLIT_TIMELINE</span> </td> 
   <td colname="col3"> Impossible d'effectuer une opération de division sur un plan de montage chronologique. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 72 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_ERASE_TIMELINE</span> </td> 
   <td colname="col3"> Impossible d'effectuer une opération d'effacement sur un plan de montage chronologique. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 73 </td> 
   <td colname="col2"><span class="codeph"> DID_NOT_GET_NEXT_FRAGMENT</span> </td> 
   <td colname="col3"> N’a pas obtenu le fragment suivant. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 74 </td> 
   <td colname="col2"><span class="codeph"> NO_TIMELINE</span> </td> 
   <td colname="col3"> Aucune chronologie n’est présente dans une structure de données interne. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 75 </td> 
   <td colname="col2"><span class="codeph"> LISTENER_NOT_FOUND</span> </td> 
   <td colname="col3"> Aucun écouteur n’a été trouvé dans une structure de données interne. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 76 </td> 
   <td colname="col2"><span class="codeph"> AUDIO__ERROR</span> </td> 
   <td colname="col3"> Impossible de  audio. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 77 </td> 
   <td colname="col2"><span class="codeph"> NO_AUDIO_SINK</span> </td> 
   <td colname="col3"> Aucun récepteur audio n’est présent dans une structure de données interne. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 78 </td> 
   <td colname="col2"><span class="codeph"> FILE_OPEN_ERROR</span> </td> 
   <td colname="col3"> Impossible d'ouvrir le fichier. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 79 </td> 
   <td colname="col2"><span class="codeph"> FILE_WRITE_ERROR</span> </td> 
   <td colname="col3"> Impossible d'écrire dans un fichier. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 80 </td> 
   <td colname="col2"><span class="codeph"> FILE_READ_ERROR</span> </td> 
   <td colname="col3"> Impossible de lire à partir d'un fichier. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 81 </td> 
   <td colname="col2"><span class="codeph"> ID3PARSE_ERROR</span> </td> 
   <td colname="col3"> Une erreur s'est produite lors de l'analyse des données ID3. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 82 </td> 
   <td colname="col2"><span class="codeph"> SECURITY_ERROR </span> </td> 
   <td colname="col3"> Le chargement du contenu a échoué en raison de restrictions de sécurité. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 83 </td> 
   <td colname="col2"><span class="codeph"> TIMELINE_TOO_SHORT</span> </td> 
   <td colname="col3"> La durée du plan de montage chronologique est trop courte. S’il s’agit d’un flux en direct, une mise en mémoire tampon fréquente peut survenir. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 84 </td> 
   <td colname="col2"><span class="codeph"> AUDIO_ONLY_STREAM_</span> </td> 
   <td colname="col3"> Le flux est passé à un flux audio uniquement. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 85 </td> 
   <td colname="col2"><span class="codeph"> AUDIO_ONLY_STREAM_END</span> </td> 
   <td colname="col3"> Le flux est passé de l’audio uniquement à un flux vidéo. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 87 </td> 
   <td colname="col2"><span class="codeph"> KEY_NOT_FOUND </span> </td> 
   <td colname="col3"> Clé introuvable. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 88 </td> 
   <td colname="col2"><span class="codeph"> INVALID_KEY</span> </td> 
   <td colname="col3"> La clé n'est pas valide. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 89 </td> 
   <td colname="col2"> <span class="codeph"> KEY_SERVER_NOT_FOUND</span> </td> 
   <td colname="col3"> Le serveur de clés ne renvoie pas de clé. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 90 </td> 
   <td colname="col2"> <span class="codeph"> MAIN_MANIFEST_UPDATE_TO_BE_HANDLED</span> </td> 
   <td colname="col3"> Impossible de gérer la mise à jour du manifeste principal. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 91 </td> 
   <td colname="col2"> <span class="codeph"> UNREPORTED_TIME_DISCONTINUITY_FOUND</span> </td> 
   <td colname="col3"> Discontinuité de temps non rapporté (PTS) détectée. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 92 </td> 
   <td colname="col2"> <span class="codeph"> UNMATCHED_AV_DISCONTINUITY_FOUND</span> </td> 
   <td colname="col3"> Discontinuité audio et vidéo inégale trouvée. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 93 </td> 
   <td colname="col2"><span class="codeph"> TRICKPLAY_ENDED_DUE_TO_ERROR</span> </td> 
   <td colname="col3">Une erreur s'est produite lors de la lecture du média en mode <i>de lecture</i> . Le mode de lecture de la vidéo est terminé et le flux est en pause. Appelez <span class="codeph"> Play()</span> pour lire le média en mode normal. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 95 </td> 
   <td colname="col2"><span class="codeph"> LIVE_WINDOW_MOVED_AHEAD</span> </td> 
   <td colname="col3"> Le joueur est sorti de la fenêtre en direct et doit chercher à rattraper. </td> 
  </tr> 
 </tbody> 
</table>

## NATIVE_ERROR : Valeurs Crypto {#section_39365E545CAC49B9A4D4678657BB2155}

Le module de chiffrement du moteur vidéo Adobe renvoie ces notifications dans l’objet `NATIVE_ERROR` de métadonnées.

| Valeur de la clé de métadonnées NATIVE_ERROR_CODE | Valeur de la clé de métadonnées NATIVE_ERROR_NAME | Signification |
|---|---|---|
| 300 | `CRYPTO_ALGORITHM_NOT_SUPPORTED` | L’algorithme utilisé n’est pas pris en charge. |
| 301 | `CRYPTO_ERROR_CORRUPTED_DATA` | Les données sont corrompues. |
| 302 | `CRYPTO_ERROR_BUFFER_TOO_SMALL` | Mémoire tampon trop petite. |
| 303 | `CRYPTO_ERROR_BAD_CERTIFICATE` | Certificat incorrect. |
| 304 | `CRYPTO_ERROR_DIGEST_UPDATE` | Mise à jour du résumé. |
| 305 | `CRYPTO_ERROR_DIGEST_FINISH` | Finition Digest. |
| 306 | `CRYPTO_ERROR_BAD_PARAMETER` | Paramètre incorrect. |
