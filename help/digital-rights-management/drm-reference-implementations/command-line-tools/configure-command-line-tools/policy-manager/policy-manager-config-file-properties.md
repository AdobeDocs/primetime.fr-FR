---
description: 'null'
keywords: hard stop
seo-description: 'null'
seo-title: Propriétés de configuration
title: Propriétés de configuration
uuid: 216921d1-a9c1-4650-9dce-c025836986e5
translation-type: tm+mt
source-git-commit: 58bb3bedc5b0ac63afd96eb6101d9ad779e6deed
workflow-type: tm+mt
source-wordcount: '1218'
ht-degree: 0%

---


# Propriétés de configuration {#configuration-properties}

<!--<a id="section_20A96CDCC5C340DEAF455C6E300E5712"></a>-->

>[!NOTE]
>
>Pour les noms de propriété qui incluent `.n`, le `n` représente un entier qui s’début avec 1 et augmente pour chaque instance de la propriété. Par exemple: `policy.license.customProp.n`.

<table class="+ topic/table " id="table_p3x_54y_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> Option de ligne de commande/propriété </th> 
   <th colname="2" class="- topic/entry entry"> Description </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.name</span> <p class="- topic/p "><span class="codeph"> -n</span> nom <i class="+ topic/ph hi-d/i ">de stratégie</i> </p> </td> 
   <td colname="2" class="- topic/entry "> Nom de la stratégie DRM lisible par l'homme. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.requireKeyServer</span> <p class="- topic/p "><span class="codeph"> -keyServer</span> <i class="+ topic/ph hi-d/i ">boolean</i> </p> </td> 
   <td colname="2" class="- topic/entry ">Les conditions suivantes s'appliquent : 
    <ul id="ul_AF4EBD6C19DC4DFAAB4756EF24BAC57D"> 
     <li id="li_6CC48ABF78EC426E9FC51458BD946BC9">Si la valeur est true, un serveur de clés HTTPS est requis pour la diffusion de clés sur iOS. </li> 
     <li id="li_63046A4ED7354C1E9E823B475E4AEFF7">Si elle n’est pas spécifiée, la valeur par défaut est false. </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.applyJailbreak</span> <p class="- topic/p "><span class="codeph"> -applyJailbreak</span> <i class="+ topic/ph hi-d/i ">boolean</i> </p> </td> 
   <td colname="2" class="- topic/entry "> Pour les périphériques qui prennent en charge la détection de jailbreak, si la valeur est true, n’autorisez pas la lecture lorsque jailbreak est détecté. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.Critical</span> <p class="- topic/p "><span class="codeph"> -critique</span> <i class="+ topic/ph hi-d/i ">booléen</i> </p> </td> 
   <td colname="2" class="- topic/entry ">Définit le caractère critique de la politique de gestion des droits numériques : 
    <ul id="ul_63F1994798894233A67AC4F8220AB642"> 
     <li id="li_D05DD9AD70464D6B9DB9DFF95846E589">Si la valeur est true, le serveur doit comprendre toutes les parties de la stratégie DRM, ce qui représente le comportement par défaut. </li> 
     <li id="li_0211473DAF1F426787CC4A68F47643C6">Si elle est définie sur false, le serveur peut ignorer les attributs de stratégie DRM qu’il ne reconnaît pas. </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.chaîne.asymmetric.certfile</span> </td> 
   <td colname="2" class="- topic/entry ">Certificat du serveur de licences dont la clé publique est utilisée pour chiffrer la clé de chiffrement racine pour le chaînage <a href="https://help.adobe.com/en_US/primetime/drm/5.3/protecting_content/index.html#DRM-concept-Enhanced_License_Chaining" class="- topic/xref " format="http" scope="external"> de licences</a>amélioré. Cette propriété spécifie un fichier qui inclut uniquement le certificat. <p>Remarque :  Les deux formats PEM ou DER sont pris en charge. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.chaîne.rootKey</span> <p class="- topic/p "><span class="codeph"> -rootKey</span> <i class="+ topic/ph hi-d/i ">root-key</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p>Spécifie la clé de chiffrement racine pour le chaînage <a href="https://help.adobe.com/en_US/primetime/drm/5.3/protecting_content/index.html#DRM-concept-Enhanced_License_Chaining" class="- topic/xref " format="http" scope="external"> de licence</a>amélioré. Si aucune clé n’est spécifiée et que le chaînage de licences amélioré est activé, une clé aléatoire est automatiquement générée. </p> <p>La clé doit avoir une longueur de 16 octets et être spécifiée en tant que valeurs hexadécimales. L’espace entre les valeurs hexadécimales est facultatif. Pour les mises à jour, l’option de ligne de commande n’est pas disponible et la propriété est ignorée. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.url</span> <p class="- topic/p "><span class="codeph"> -domainURL</span> <i class="+ topic/ph hi-d/i ">url</i> </p> </td> 
   <td colname="2" class="- topic/entry ">Si l’enregistrement de domaine est requis, <i>url</i> indique l’URL d’un serveur de domaine. Pour les mises à jour, l’option de ligne de commande n’est pas disponible et la propriété est ignorée. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.anonymous</span> <p class="- topic/p "><span class="codeph"> -domainAnon</span> </p> </td> 
   <td colname="2" class="- topic/entry ">Indique si l’enregistrement de domaine anonyme est autorisé. Définit la propriété sur true ou inclut cette option de ligne de commande pour autoriser l’accès anonyme. <p>Remarque : Cette option ne peut pas être utilisée avec <span class="codeph"> -domainAuthNS</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.authNamespace</span> <p class="- topic/p "><span class="codeph"> -domainAuthNS</span> <i class="+ topic/ph hi-d/i ">espace de nommage</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p>espace de nommage d’authentification pour l’enregistrement de domaine. Si spécifié, le client doit s’authentifier avec un nom d’utilisateur et un mot de passe émis par l’autorité spécifiée. </p> <p>Pour les mises à jour, l’option de ligne de commande n’est pas disponible et la propriété est ignorée. </p> <p>Remarque : Cette option ne peut pas être utilisée avec <span class="codeph"> -domainAnon</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.analog</span> <p class="- topic/p "><span class="codeph"> -opAnalog</span> <i class="+ topic/ph hi-d/i ">AnalogOption</i> </p> </td> 
   <td colname="2" class="- topic/entry ">Les contraintes de protection de la sortie analogique et les valeurs suivantes sont prises en charge : 
    <ul class="- topic/ul " id="ul_h4x_54y_n4"> 
     <li class="- topic/li " id="li_F920EC01159C4231AFBE579D487C8770"><span class="+ topic/ph pr-d/codeph codeph"> NO_PROTECTION</span> </li> 
     <li class="- topic/li " id="li_2DE0494AF8C446EB9E4567915F5E97C3"><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE</span> </li> 
     <li class="- topic/li " id="li_207D2D6256D6423FBDABA7A8627A9B7D"><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE_ACP</span> </li> 
     <li class="- topic/li " id="li_E17D944BED5F403FAE94708EE6AE4BBE"><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE_CGMSA</span> </li> 
     <li class="- topic/li " id="li_66D5A0C8FE154445A522D91EFB05B7ED"><span class="+ topic/ph pr-d/codeph codeph"> OBLIGATOIRE</span> </li> 
     <li class="- topic/li " id="li_AF2024F212A249ED99AEECCF3E844A11"><span class="+ topic/ph pr-d/codeph codeph"> REQUIRED_ACP</span> </li> 
     <li class="- topic/li " id="li_FFF9B7DAE77740EE895EC35D1606A527"><span class="+ topic/ph pr-d/codeph codeph"> REQUIRED_CGMSA</span> </li> 
     <li class="- topic/li " id="li_52DED572F3AE495EB6A6450C611B440E"><span class="+ topic/ph pr-d/codeph codeph"> NO_PLAYBACK</span> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.drmVersionBlacklist.n</span> <p class="- topic/p "><span class="codeph"> -drmBlacklist</span> <i class="+ topic/ph hi-d/i ">nom/valeur-paires</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p>Clients DRM qui ne peuvent pas accéder au contenu protégé. Cette option spécifie une liste de versions des modules DRM qui ne peuvent pas être utilisées (liste bloquée). </p> <p>La valeur se compose de paires nom=valeur <span class="codeph"></span> séparées par des virgules au format suivant : </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> os|release|arch|model|vendor|env|screen=value</span> </p> <p class="- topic/p ">Les paires nom/valeur supplémentaires doivent être séparées par des virgules. Par exemple, <span class="codeph"> os=Win, release=2.0, arch=32</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.runtimeVersionBlacklist.n</span> <p class="- topic/p "><span class="codeph"> -runtimeBlacklist</span> <i class="+ topic/ph hi-d/i ">nom/valeur-paires</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p>Les runtimes d'application ne peuvent pas accéder au contenu protégé. Cette option spécifie une liste de versions des modules d’exécution qui ne peuvent pas être utilisées (liste bloquée). </p> <p>La valeur se compose de paires nom=valeur <span class="codeph"></span> séparées par des virgules au format suivant : </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> os|release|application|arche|model|vendor|env|screen=value</span> </p> <p class="- topic/p ">Les paires nom/valeur supplémentaires doivent être séparées par des virgules. Par exemple, <span class="codeph"> os=Win,application=AIR</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.v1DeviceCapabilities</span> <p class="- topic/p "><span class="codeph"> -devCapabilitiesV1</span> <i class="+ topic/ph hi-d/i ">nom/valeur-paires</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Spécifie les fonctionnalités de périphérique requises pour accéder au contenu protégé. La valeur se compose de paires nom=valeur <span class="codeph"></span> séparées par des virgules au format suivant : </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> nonUserAccessibleBus|hardwareRootOfTrust=true|false</span> </p> <p class="- topic/p ">Par exemple, <span class="codeph"> nonUserAccessibleBus=false,hardwareRootOfTrust=true</span>. </p> <p>Lors d'une mise à jour, vous devez appliquer <span class="codeph"> -devCapabilitiesV1</span> sans les arguments restants qui suppriment la restriction de capacités du périphérique. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.syncFrequency</span> <p class="- topic/p "><span class="codeph"> -sync</span> <i class="+ topic/ph hi-d/i ">name/value-paires</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique la fréquence à laquelle les clients doivent envoyer des messages de synchronisation au serveur. </p> <p>Si la propriété n’est pas définie, les clients n’envoient pas de messages de synchronisation lorsqu’ils lisent du contenu protégé par une stratégie DRM. La valeur se compose de paires nom=valeur <span class="codeph"></span> séparées par des virgules au format suivant : </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> début|force=numberValue</span> </p> <p class="- topic/p ">La liste suivante fournit des informations supplémentaires sur les options : 
     <ul id="ul_a5j_q4t_44"> 
      <li id="li_FD2C0C6DA19E455AA1917A56E09A7F84">(obligatoire) <span class="codeph"> début</span> spécifie que le client doit début de synchronisation avec le serveur dans les minutes spécifiées depuis la dernière synchronisation. </li> 
      <li id="li_9DEBC57385A442C3929AE3D0E3FA8992">(facultatif) <span class="codeph"> force</span> est la probabilité (0-100) avec laquelle le client doit forcer un message de synchronisation pendant la lecture. </li> 
     </ul>Pendant la mise à jour, utilisez <span class="codeph"> -sync</span> sans les arguments restants pour supprimer les exigences de synchronisation. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.useRootLicense</span> </td> 
   <td colname="2" class="- topic/entry ">Indique si cette stratégie DRM possède une licence racine. <p>Pour plus d’informations, voir <a href="https://help.adobe.com/en_US/primetime/drm/5.3/protecting_content/index.html#DRM-concept-Enhanced_License_Chaining" class="- topic/xref " format="http" scope="external"> Amélioration du chaînage</a>des licences. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.startDate</span> </td> 
   <td colname="2" class="- topic/entry ">Date à laquelle le contenu devient valide. Vous pouvez appliquer l’un des formats suivants : 
    <ul id="ul_6610B44D0C16485098F6F45DE3F151D7"> 
     <li id="li_986707D4C6164C44B3CCBE2EEB4C09B6"><span class="+ topic/ph pr-d/codeph codeph">aaaa-mm-jj</span> <p>Par exemple, <span class="codeph"> 2009-01-31</span> signifie le 31 janvier à 12h00. </p> </li> 
     <li id="li_E15B782716124F6EAEFB04D16E5280DB"><span class="+ topic/ph pr-d/codeph codeph">aaaa-mm-jj-h24:min:s</span> <p>Par exemple, <span class="codeph"> 2009-01-31-14:30:00</span> signifie le 31 janvier à 14:30. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.expiration.endDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">La date avant laquelle le contenu n'est plus valide. </p> <p>Remarque : Vous ne pouvez pas spécifier <span class="codeph"> .expiration.endDate</span> et <span class="codeph"> .expiration.duration</span> simultanément. </p> <p>Par exemple, 2009-01-31-14:30:00 signifie que le contenu expirera le 31 janvier à 14:30. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.expiration.duration</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Temps en minutes auquel le contenu devient non valide. débuts de mise en package du contenu. </p> <p>Remarque : Vous ne pouvez pas spécifier <span class="codeph"> .expiration.endDate</span> et <span class="codeph"> .expiration.duration</span> simultanément. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.licenseCaching.duration</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Durée en minutes pendant laquelle une licence peut être mise en cache sur le client. Vous pouvez définir cette propriété sur 0 pour empêcher la mise en cache des licences. La valeur doit être supérieure ou égale à 0. </p> <p>Remarque : Vous ne pouvez pas spécifier <span class="codeph"> .licenseCaching.duration</span> et <span class="codeph"> .licenseCaching.endDate</span> simultanément. </p> <p class="- topic/p ">Ce paramètre de stratégie DRM est appliqué uniquement à la mise en cache des licences sur le disque et ne contrôle pas la durée de la licence mise en cache par la mémoire. La licence peut être mise en cache en mémoire, même si vous ne spécifiez pas de stratégie DRM pour une durée nulle. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.licenseCaching.endDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Date à laquelle vous ne pouvez plus mettre en cache les licences. </p> <p>Remarque : Vous ne pouvez pas spécifier <span class="codeph"> .licenseCaching.duration</span> et <span class="codeph"> .licenseCaching.endDate</span> simultanément. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.anonyme</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique si l’acquisition de licence anonyme est autorisée. La valeur par défaut est définie sur <span class="codeph"> false</span>, ce qui signifie qu’un nom d’utilisateur et un mot de passe sont requis. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.authNamespace</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Si un nom d’utilisateur et un mot de passe sont requis, cette propriété spécifie un qualificateur de nom facultatif pour les noms d’utilisateur. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.customProp.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">paires nom/valeur personnalisées à utiliser par le serveur lors de l’acquisition de la licence. Vous pouvez appliquer le format suivant pour spécifier les propriétés : <span class="+ topic/ph pr-d/codeph codeph">policy.customProp.n</span>=<span class="+ topic/ph pr-d/codeph codeph">name</span>=<span class="+ topic/ph pr-d/codeph codeph">value</span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.playbackWindow </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique la fenêtre de lecture en minutes. Cette valeur représente la durée de validité de la licence après la première lecture du contenu protégé. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.digital</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Contraintes de protection de sortie, qui doivent être l’une des valeurs suivantes : 
     <ul id="ul_wsb_kfp_fs"> 
      <li id="li_FE012306F22F4F3FB981FE167C7A8B94"><span class="codeph"> NO_PROTECTION</span> </li> 
      <li id="li_A5591DC8983848FE9823C2A261BF7713"><span class="codeph"> USE_IF_AVAILABLE</span> </li> 
      <li id="li_74102C36ADE841C4B9ED71156E0A4C2C"><span class="codeph"> OBLIGATOIRE</span> </li> 
      <li id="li_769E15C85B4E4DD48213DBD019D60BA7"><span class="codeph"> NO_PLAYBACK</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.ota</span> </td> 
   <td colname="2" class="- topic/entry ">Spécifie les types de connexion OTA (over the air) qui doivent être autorisés dans la liste. Les types de connexion valides sont les suivants : 
    <ul id="ul_iz5_4fp_fs"> 
     <li id="li_FB07519EFEFE4B95B3B1F5BFD4DE6591"><span class="codeph"> MIRACATE</span> </li> 
     <li id="li_51E7DE83679F4630B01264407DAD0E84"><span class="codeph"> AIRPLAY</span> </li> 
     <li id="li_D499A0487AAC409CB2CEA6164265D3CF"><span class="codeph"> DLNA</span> </li> 
     <li id="li_4FCC0EC4A0FC48F99A13EC8A1B78D6A1"><span class="codeph"> WIDI</span> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.resolution</span> </td> 
   <td colname="2" class="- topic/entry "> Spécifie le fichier de configuration dans lequel les contraintes basées sur la résolution sont définies. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.drmMinSecurityLevel</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique le niveau de sécurité minimum permettant au module DRM d’accéder au contenu protégé. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.runtimeMinSecurityLevel</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Le module d'exécution d'application doit avoir au moins le niveau de sécurité minimum spécifié pour accéder au contenu protégé. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.allowedAIRApplication.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">liste autorisée d’applications non Flash (Adobe AIR, iOS, Android, etc.) qui sont autorisés à lire du contenu protégé. La propriété doit utiliser le format suivant : <span class="+ topic/ph pr-d/codeph codeph">pubId</span>[:<span class="+ topic/ph pr-d/codeph codeph">appId</span>[:[<span class="+ topic/ph pr-d/codeph codeph">min</span>]:[<span class="+ topic/ph pr-d/codeph codeph">max</span>]]] </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.allowedSWFApplication.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">liste autorisée d’applications SWF autorisées à lire du contenu protégé. La propriété doit utiliser le format suivant : </p> <p class="- topic/p "> 
     <ul id="ul_EC20F52AD95C4BE3B7F703048A43CDF0"> 
      <li id="li_3E4A47D925C24834A2C25BC5943279D4"><span class="+ topic/ph pr-d/codeph codeph">URL</span> </li> 
      <li id="li_9A7CAF081C5F488FB5CDA6D38C5552F6"><span class="+ topic/ph pr-d/codeph codeph">file=swf_file</span> </li> 
      <li id="li_E10EA4223137489CBE4015DE999F7154"><span class="codeph">time=max_time_to_verify</span> </li> 
     </ul> <i class="+ topic/ph hi-d/i ">swf_file</i> est le fichier SWF utilisé pour calculer le hachage et <i class="+ topic/ph hi-d/i ">max_time_to_verify</i> est le temps maximum en secondes autorisé pour télécharger et vérifier le SWF. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.license.customProp.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Des paires nom/valeur personnalisées que vous devez inclure dans les licences lorsque celles-ci sont délivrées aux utilisateurs. Vous devez spécifier le format suivant : </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph">policy.license.customProp.n=name</span> </p> <p class="- topic/p ">Vous pouvez définir cette option plusieurs fois pour plusieurs propriétés personnalisées. </p> </td> 
  </tr> 
 </tbody> 
</table>
