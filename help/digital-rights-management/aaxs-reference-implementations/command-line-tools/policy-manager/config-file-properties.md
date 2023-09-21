---
title: Propriétés du fichier de configuration
description: Propriétés du fichier de configuration
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1119'
ht-degree: 0%

---

# Propriétés du fichier de configuration {#configuration-file-properties}

Le fichier de configuration spécifie les propriétés suivantes. Pour les noms de propriété qui incluent `n`, `n` représente un entier commençant par 1 et augmentant pour chaque instance de la propriété.

<table class="+ topic/table " id="table_p3x_54y_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> Propriété/Option de ligne de commande </th> 
   <th colname="2" class="- topic/entry entry"> Description </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.name</span> <p class="- topic/p "><span class="codeph"> -n</span> <i class="+ topic/ph hi-d/i ">policy name</i> </p> </td> 
   <td colname="2" class="- topic/entry "> Nom lisible de la stratégie. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.requireKeyServer</span> <p class="- topic/p "><span class="codeph"> -keyServer</span> <i class="+ topic/ph hi-d/i ">boolean</i> </p> </td> 
   <td colname="2" class="- topic/entry "> Si la valeur est true, un serveur de clés HTTPS est requis pour la diffusion de clés vers iOS. La valeur par défaut est false, si elle n’est pas spécifiée. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.enforceJailbreak</span> <p class="- topic/p "><span class="codeph"> -enforceJailbreak</span> <i class="+ topic/ph hi-d/i ">boolean</i> </p> </td> 
   <td colname="2" class="- topic/entry "> Si la valeur est true, pour les appareils qui prennent en charge la détection de saut de jailbreak, n’autorisez pas la lecture si le saut de jailbreak a été détecté. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.critical</span> <p class="- topic/p "><span class="codeph"> -critical</span> <i class="+ topic/ph hi-d/i ">boolean</i> </p> </td> 
   <td colname="2" class="- topic/entry "> Définissez la critique politique. Si la valeur est true, le serveur doit comprendre toutes les parties de la stratégie (il s’agit du comportement par défaut). Si la valeur est false, le serveur peut ignorer les attributs de stratégie qu’il ne comprend pas. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.chaining.asymmetric.certfile</span> </td> 
   <td colname="2" class="- topic/entry ">Certificat du serveur de licences dont la clé publique est utilisée pour chiffrer la clé de chiffrement racine pour la variable <a href="../../../aaxs-protecting-content/content-introduction/content-usage-rules/content-other-policy-options/content-enhanced-license-chaining.md" format="dita" scope="local"> Chaîne de licence améliorée </a>
   Cette propriété spécifie un fichier contenant uniquement le certificat (le format PEM ou DER est acceptable). </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.chaining.rootKey</span> <p class="- topic/p "><span class="codeph"> -rootKey</span> <i class="+ topic/ph hi-d/i ">root-key</i> </p> </td> 
   <td colname="2" class="- topic/entry "> Spécifiez la clé de chiffrement racine pour le chaînage de licence amélioré. Si aucune clé n’est spécifiée et que le chaînage de licence amélioré est activé, une clé aléatoire est générée. La clé doit avoir une longueur de 16 octets et être spécifiée sous la forme de valeurs hexadécimales. Un espace blanc entre les valeurs hexadécimales est facultatif. Pour les mises à jour, l’option de ligne de commande n’est pas autorisée et la propriété est ignorée. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.url</span> <p class="- topic/p "><span class="codeph"> -domainURL</span> <i class="+ topic/ph hi-d/i ">url</i> </p> </td> 
   <td colname="2" class="- topic/entry "> URL du serveur de domaine, si un enregistrement de domaine est requis. Pour les mises à jour, l’option de ligne de commande n’est pas autorisée et la propriété est ignorée. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.anonymous</span> <p class="- topic/p "><span class="codeph"> -domainAnon</span> </p> </td> 
   <td colname="2" class="- topic/entry "> Indique si l’enregistrement de domaine anonyme est autorisé. Définissez la propriété sur true ou incluez cette option de ligne de commande pour autoriser l’accès anonyme. Cette option ne peut pas être utilisée avec -domainAuthNS. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.authNamespace</span> <p class="- topic/p "><span class="codeph"> -domainAuthNS</span> <i class="+ topic/ph hi-d/i ">namespace</i> </p> </td> 
   <td colname="2" class="- topic/entry "> Espace de noms d’authentification pour l’enregistrement du domaine. Si spécifié, le client doit s’authentifier avec un nom d’utilisateur et un mot de passe émis par l’autorité spécifiée. Pour les mises à jour, l’option de ligne de commande n’est pas autorisée et la propriété est ignorée. Cette option ne peut pas être utilisée avec -domainAnon. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.analog</span> <p class="- topic/p "><span class="codeph"> -opAnalog</span> <i class="+ topic/ph hi-d/i ">AnalogOption</i> </p> </td> 
   <td colname="2" class="- topic/entry ">Contraintes de protection de sortie analogique. Les valeurs suivantes sont prises en charge : 
    <ul class="- topic/ul " id="ul_h4x_54y_n4"> 
     <li class="- topic/li " id="li_5BC8F39B61894E83A7B27570FF848F09"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> NO_PROTECTION</span> </p> </li> 
     <li class="- topic/li " id="li_FF14594A0714480496793A82C3FA1610"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE</span> </p> </li> 
     <li class="- topic/li " id="li_721FCC4DC1F34AE398EFAE4C0D3F50F5"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE_ACP</span> </p> </li> 
     <li class="- topic/li " id="li_D588BB278BEE4CEAB034BD48550EBCDC"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE_CGMSA</span> </p> </li> 
     <li class="- topic/li " id="li_7E5F006D2F114502BA6D0A9C4173004E"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> OBLIGATOIRE</span> </p> </li> 
     <li class="- topic/li " id="li_9EBFAA4AACF249C2A94432D88E12C3B9"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> REQUIRED_ACP</span> </p> </li> 
     <li class="- topic/li " id="li_6720C6A085864BEB957C0BF2C38551C9"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> REQUIRED_CGMSA</span> </p> </li> 
     <li class="- topic/li " id="li_6FD98473ECDB4A66AC4B506FB9B3B360"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> NO_PLAYBACK</span> </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.drmVersionBlacklist.n</span> <p class="- topic/p "><span class="codeph"> -drmBlacklist</span> <i class="+ topic/ph hi-d/i ">nom/valeur-paires</i> </p> </td> 
   <td colname="2" class="- topic/entry ">Les clients DRM ne peuvent pas accéder au contenu protégé. Cette option spécifie une liste de versions des modules DRM qui ne peuvent pas être utilisés (liste bloquée). La valeur se compose de paires nom=valeur séparées par des virgules au format suivant : <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> os|release|arch|model|vendor|env|screen=value</span> </p> <p class="- topic/p ">Les paires nom/valeur supplémentaires doivent être séparées par des virgules. Par exemple : <span class="codeph"> os=Win,release=2.0,arch=32</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.runtimeVersionBlacklist.n</span> <p class="- topic/p "><span class="codeph"> -runtimeBlacklist</span> <i class="+ topic/ph hi-d/i ">nom/valeur-paires</i> </p> </td> 
   <td colname="2" class="- topic/entry ">Les exécutions d’application ne peuvent pas accéder au contenu protégé. Cette option spécifie une liste des versions des modules d’exécution qui ne peuvent pas être utilisées (liste bloquée). La valeur se compose de paires nom=valeur séparées par des virgules au format suivant : <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> os|release|application|arch|model|vendor|env|screen=value</span> </p> <p class="- topic/p ">Les paires nom/valeur supplémentaires doivent être séparées par des virgules. Par exemple : <span class="codeph"> os=Win,application=AIR</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.v1DeviceCapabilities</span> <p class="- topic/p "><span class="codeph"> -devCapabilitiesV1</span> <i class="+ topic/ph hi-d/i ">nom/valeur-paires</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Spécifie les fonctionnalités de périphérique requises pour accéder au contenu protégé. La valeur se compose de paires nom=valeur séparées par des virgules au format suivant : </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> nonUserAccessibleBus|hardwareRootOfTrust=true|false</span> </p> <p class="- topic/p ">Par exemple : <span class="codeph"> nonUserAccessibleBus=false,hardwareRootOfTrust=true</span>. Lors de la mise à jour, utilisez <span class="codeph"> -devCapabilitiesV1</span> sans les arguments restants pour supprimer la restriction des fonctionnalités de l’appareil. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.syncFrequency</span> <p class="- topic/p "><span class="codeph"> -sync</span> <i class="+ topic/ph hi-d/i ">nom/valeur-paires</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indiquez la fréquence à laquelle les clients doivent envoyer des messages de synchronisation au serveur. Si elle n’est pas définie, les clients n’envoient pas de messages de synchronisation lors de la lecture de contenu protégé par cette stratégie. La valeur est composée de virgules séparées. <span class="codeph"> name=value</span> paires au format suivant : </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> start|force|hardStop=numberValue</span> </p> <p class="- topic/p "> 
     <ul id="ul_a5j_q4t_44"> 
      <li id="li_25CAF96C27F34848A95B2E3693847C71"><span class="codeph"> start</span> (obligatoire) : l’intervalle de démarrage indique que le client doit commencer la synchronisation avec le serveur pendant plusieurs minutes depuis la dernière synchronisation. </li> 
      <li id="li_CC9068CFE75645029C947C9E1B53351F"><span class="codeph"> force</span> (facultatif) - Forcer la probabilité de synchronisation est la probabilité (0 à 100) avec laquelle le client doit forcer un message de synchronisation pendant la lecture. </li> 
      <li id="li_C31A6250F19348FBB8B7569D00C6314E"><span class="codeph"> hardStop</span> (facultatif) - L’intervalle d’arrêt en dur correspond à la durée en minutes après laquelle le client échoue à la lecture s’il ne parvient pas à se synchroniser. S’il est défini, doit être supérieur à l’intervalle de début. </li> 
     </ul>Lors de la mise à jour, utilisez <span class="codeph"> -sync</span> sans les arguments restants pour supprimer les exigences de synchronisation. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.useRootLicense</span> </td> 
   <td colname="2" class="- topic/entry ">Indique si cette stratégie possède une licence racine (voir <i class="+ topic/ph hi-d/i ">Chaîne de licence améliorée</i> in <i class="+ topic/ph hi-d/i ">Utilisation de l’accès aux Adobes pour la protection du contenu</i>). </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.startDate</span> </td> 
   <td colname="2" class="- topic/entry ">Date à laquelle le contenu est valide. Utiliser le format <span class="+ topic/ph pr-d/codeph codeph">aaaa-mm-jj</span> (par exemple, <span class="codeph"> 2009-01-31</span> représente le 31 janvier à 12h00) ou <span class="+ topic/ph pr-d/codeph codeph">aaaa-mm-jj-h24:min:sec</span> (par exemple, <span class="codeph"> 2009-01-31-14:30:00</span> représente le 31 janvier à 14 h 30). </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.expiration.endDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Date avant laquelle le contenu est valide. Les deux <span class="codeph"> policy.expiration.endDate</span> et policy.expiration.duration ne peut pas être spécifié simultanément. Utiliser le format <span class="+ topic/ph pr-d/codeph codeph">aaaa-mm-jj</span> ou <span class="+ topic/ph pr-d/codeph codeph">aaaa-mm-jj-h24:min:sec</span> (par exemple, 2009-01-31-14:30:00 représente le 31 janvier à 14 h 30). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.expiration.duration</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Durée de validité du contenu (en minutes), à partir du moment où il est compressé. Les deux <span class="codeph"> policy.expiration.endDate</span> et <span class="codeph"> policy.expiration.duration</span> ne peuvent pas être spécifiées en même temps. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.licenseCaching.duration</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Durée pendant laquelle une licence peut être mise en cache sur le client (en minutes). Définissez cette propriété sur 0 pour interdire la mise en cache de licence. La valeur doit être 0 ou supérieure. Les deux <span class="codeph"> policy.licenseCaching.duration</span> et <span class="codeph"> policy.licenseCaching.endDate</span> ne peuvent pas être utilisés simultanément. </p> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Remarque</b>: ce paramètre de stratégie est appliqué uniquement à la mise en cache de licence sur le disque. Il ne contrôle pas la durée de licence de la mémoire mise en cache. La licence peut être mise en cache en mémoire même si la durée spécifiée par la stratégie est zéro. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.licenseCaching.endDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Date à laquelle les licences ne peuvent pas être mises en cache. Les deux <span class="codeph"> policy.licenseCaching.duration</span> et <span class="codeph"> policy.licenseCaching.endDate</span> ne peuvent pas être utilisés simultanément. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.anonymous</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique si l’acquisition de licence anonyme est autorisée. La valeur par défaut est "false" (l’authentification du nom d’utilisateur/mot de passe est requise) si elle n’est pas spécifiée. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.authNamespace</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Si l’authentification par nom d’utilisateur/mot de passe est requise, cette propriété spécifie un qualificateur de nom facultatif pour les noms d’utilisateur. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.customProp.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Paires nom/valeur personnalisées à utiliser par le serveur lors de l’acquisition de la licence. Utilisez le format suivant pour spécifier les propriétés : <span class="+ topic/ph pr-d/codeph codeph">policy.customProp.n</span>=<span class="+ topic/ph pr-d/codeph codeph">name</span>=<span class="+ topic/ph pr-d/codeph codeph">value</span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.playbackWindow</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique la fenêtre de lecture (en minutes), durée pendant laquelle la licence est valide après la première utilisation de celle-ci pour lire du contenu protégé. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.digital</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Contraintes de protection de sortie. Les valeurs doivent être parmi les suivantes : </p> <p class="- topic/p "><i class="+ topic/ph hi-d/i ">NO_PROTECTION, USE_IF_AVAILABLE, REQUIS, NO_PLAYBACK</i> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.drmMinSecurityLevel</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Le module DRM doit avoir le niveau de sécurité minimum spécifié, ou supérieur, pour accéder au contenu protégé. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.runtimeMinSecurityLevel</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Le module d’exécution de l’application doit avoir le niveau de sécurité minimum spécifié, ou supérieur, pour accéder au contenu protégé. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.allowedAIRApplication.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Liste autorisée des applications Adobe AIR ou iOS permettant de lire du contenu protégé. La propriété doit utiliser le format suivant : <span class="+ topic/ph pr-d/codeph codeph">pubId</span>[:<span class="+ topic/ph pr-d/codeph codeph">appId</span>[:[<span class="+ topic/ph pr-d/codeph codeph">min</span>]:[<span class="+ topic/ph pr-d/codeph codeph">max</span>]] </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.allowedSWFApplication.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Liste autorisée d’applications SWF autorisées à lire du contenu protégé. Utilisez le format suivant : </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph">URL</span> ou file=<span class="+ topic/ph pr-d/codeph codeph">swf_file</span>,time=<i class="+ topic/ph hi-d/i ">max_time_to_verify</i> <i class="+ topic/ph hi-d/i ">swf_file</i> est le fichier du SWF pour lequel calculer le hachage et <i class="+ topic/ph hi-d/i ">max_time_to_verify</i> est la durée maximale autorisée pour le téléchargement et la vérification du SWF à terminer (en secondes). </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.license.customProp.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Paires nom/valeur personnalisées à inclure dans les licences délivrées aux utilisateurs. Utilisez le format suivant : </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph">policy.license.customProp.n</span>=<span class="+ topic/ph pr-d/codeph codeph">name</span>=<span class="+ topic/ph pr-d/codeph codeph">value</span> </p> <p class="- topic/p ">Cette option peut être définie plusieurs fois pour plusieurs propriétés personnalisées. </p> </td> 
  </tr> 
 </tbody> 
</table>
