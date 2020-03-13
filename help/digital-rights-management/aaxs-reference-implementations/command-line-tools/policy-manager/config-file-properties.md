---
seo-title: Propriétés du fichier de configuration
title: Propriétés du fichier de configuration
uuid: aec5fee7-4d77-4299-8d85-3e9042b2bbd1
translation-type: tm+mt
source-git-commit: 99d7eea63b18a97d2b99d0bb7aab5cdc50ae5ffc

---


# Propriétés du fichier de configuration {#configuration-file-properties}

Le fichier de configuration spécifie les propriétés suivantes. Pour les noms de propriété qui incluent `n`, `n` représente un entier commençant par 1 et augmentant pour chaque instance de la propriété.

<table class="+ topic/table " id="table_p3x_54y_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> Option Propriété/Ligne de commande </th> 
   <th colname="2" class="- topic/entry entry"> Description </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.name</span> <p class="- topic/p "><span class="codeph"> -n</span> nom <i class="+ topic/ph hi-d/i ">de la stratégie</i> </p> </td> 
   <td colname="2" class="- topic/entry "> Nom de la stratégie lisible par l’homme. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.requireKeyServer</span> <p class="- topic/p "><span class="codeph"> -keyServer</span><i class="+ topic/ph hi-d/i ">boolean</i> </p> </td> 
   <td colname="2" class="- topic/entry "> Si la valeur est true, un serveur de clés HTTPS est requis pour les  de clés vers iOS. La valeur par défaut est false, si elle n’est pas spécifiée. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.applyJailbreak</span> <p class="- topic/p "><span class="codeph"> -applyJailbreak</span><i class="+ topic/ph hi-d/i ">boolean</i> </p> </td> 
   <td colname="2" class="- topic/entry "> Si la valeur est true, pour les périphériques prenant en charge la détection de jailbreak, n’autorisez pas la lecture si jailbreak a été détecté. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.Critical</span> <p class="- topic/p "><span class="codeph"> -Critical</span> <i class="+ topic/ph hi-d/i ">boolean</i> </p> </td> 
   <td colname="2" class="- topic/entry "> Fixer l'importance de la politique. Si la valeur est true, le serveur doit comprendre toutes les parties de la stratégie (il s’agit du comportement par défaut). Si la valeur est false, le serveur peut ignorer les attributs de stratégie qu’il ne comprend pas. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.chain.asymmetric.certfile</span> </td> 
   <td colname="2" class="- topic/entry ">Certificat du serveur de licences dont la clé publique est utilisée pour chiffrer la clé de chiffrement racine pour le chaînage de licences <a href="../../../aaxs-protecting-content/content-introduction/content-usage-rules/content-other-policy-options/content-enhanced-license-chaining.md" format="dita" scope="local"> amélioré </a>Cette propriété spécifie un fichier contenant uniquement le certificat (le format PEM ou DER est acceptable). </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.chaîne.rootKey</span> <p class="- topic/p "><span class="codeph"> -rootKey</span><i class="+ topic/ph hi-d/i ">root-key</i> </p> </td> 
   <td colname="2" class="- topic/entry "> Spécifiez la clé de chiffrement racine pour le chaînage de licence amélioré. Si aucune clé n’est spécifiée et que le chaînage de licence amélioré est activé, une clé aléatoire est générée. La clé doit avoir une longueur de 16 octets et être spécifiée en tant que valeurs hexadécimales. L’espace entre les valeurs hexadécimales est facultatif. Pour les mises à jour, l’option de ligne de commande n’est pas autorisée et la propriété est ignorée. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.url</span> <p class="- topic/p "><span class="codeph"> -domainURL</span><i class="+ topic/ph hi-d/i ">url</i> </p> </td> 
   <td colname="2" class="- topic/entry "> URL du serveur de domaine, si l’enregistrement du domaine est requis. Pour les mises à jour, l’option de ligne de commande n’est pas autorisée et la propriété est ignorée. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.anonymous</span> <p class="- topic/p "><span class="codeph"> -domainAnon</span> </p> </td> 
   <td colname="2" class="- topic/entry "> Indique si l’enregistrement de domaine anonyme est autorisé. Définissez la propriété sur true ou incluez cette option de ligne de commande pour autoriser l’accès anonyme. Cette option ne peut pas être utilisée avec -domainAuthNS. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.authNamespace</span> <p class="- topic/p "><span class="codeph"> -domainAuthNS</span><i class="+ topic/ph hi-d/i "></i> </p> </td> 
   <td colname="2" class="- topic/entry "> Le d’authentification   pour l’enregistrement de domaine. Le cas échéant, le client doit s’authentifier avec un nom d’utilisateur et un mot de passe émis par l’autorité spécifiée. Pour les mises à jour, l’option de ligne de commande n’est pas autorisée et la propriété est ignorée. Cette option ne peut pas être utilisée avec -domainAnon. </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.analog</span> <p class="- topic/p "><span class="codeph"> -opAnalog</span> <i class="+ topic/ph hi-d/i ">AnalogOption</i> </p> </td> 
   <td colname="2" class="- topic/entry ">Contraintes de protection de sortie analogique. Les valeurs suivantes sont prises en charge : 
    <ul class="- topic/ul " id="ul_h4x_54y_n4"> 
     <li class="- topic/li " id="li_5BC8F39B61894E83A7B27570FF848F09"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> NO_PROTECTION</span> </p> </li> 
     <li class="- topic/li " id="li_FF14594A0714480496793A82C3FA1610"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE</span> </p> </li> 
     <li class="- topic/li " id="li_721FCC4DC1F34AE398EFAE4C0D3F50F5"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE_ACP</span> </p> </li> 
     <li class="- topic/li " id="li_D588BB278BEE4CEAB034BD48550EBCDC"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE_CGMSA</span> </p> </li> 
     <li class="- topic/li " id="li_7E5F006D2F114502BA6D0A9C4173004E"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> REQUIS</span> </p> </li> 
     <li class="- topic/li " id="li_9EBFAA4AACF249C2A94432D88E12C3B9"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> REQUIRED_ACP</span> </p> </li> 
     <li class="- topic/li " id="li_6720C6A085864BEB957C0BF2C38551C9"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> REQUIRED_CGMSA</span> </p> </li> 
     <li class="- topic/li " id="li_6FD98473ECDB4A66AC4B506FB9B3B360"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> NO_PLAYBACK</span> </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.drmVersionBlacklist.n</span> <p class="- topic/p "><span class="codeph"> -drmBlacklist</span> <i class="+ topic/ph hi-d/i ">nom/valeur-paires</i> </p> </td> 
   <td colname="2" class="- topic/entry ">Les clients DRM ne peuvent pas accéder au contenu protégé. Cette option spécifie un  de versions des modules DRM qui ne peuvent pas être utilisées (noir ). La valeur se compose de paires nom=valeur séparées par des virgules avec le format suivant : <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> os|release|arch|model|vendor|env|screen=value</span> </p> <p class="- topic/p ">Les paires nom/valeur supplémentaires doivent être séparées par des virgules. Par exemple : <span class="codeph"> os=Win,release=2.0,arch=32</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.runtimeVersionBlacklist.n</span> <p class="- topic/p "><span class="codeph"> -runtimeBlacklist</span> <i class="+ topic/ph hi-d/i ">nom/valeur-paires</i> </p> </td> 
   <td colname="2" class="- topic/entry ">Les moteurs d’exécution d’application n’ont pas accès au contenu protégé. Cette option spécifie un  de versions des modules d’exécution qui ne peuvent pas être utilisées (noir ). La valeur se compose de paires nom=valeur séparées par des virgules avec le format suivant : <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> os|release|application|arch|modèle|fournisseur|env|écran=valeur</span> </p> <p class="- topic/p ">Les paires nom/valeur supplémentaires doivent être séparées par des virgules. Par exemple, <span class="codeph"> os=Win,application=AIR</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.v1DeviceCapabilities</span> <p class="- topic/p "><span class="codeph"> -devCapabilitiesV1</span> <i class="+ topic/ph hi-d/i ">nom/valeur-paires</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Spécifie les fonctionnalités du périphérique requises pour accéder au contenu protégé. La valeur se compose de paires nom=valeur séparées par des virgules avec le format suivant : </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> nonUserAccessibleBus|hardwareRootOfTrust=true|false</span> </p> <p class="- topic/p ">Par exemple, <span class="codeph"> nonUserAccessibleBus=false,hardwareRootOfTrust=true</span>. Lors de la mise à jour, utilisez <span class="codeph"> -devCapabilitiesV1</span> sans les arguments restants pour supprimer la restriction de capacités du périphérique. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.syncFrequency</span> <p class="- topic/p "><span class="codeph"> -sync</span><i class="+ topic/ph hi-d/i ">nom/valeur-paires</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Spécifiez la fréquence à laquelle les clients doivent envoyer des messages de synchronisation au serveur. Si elle n’est pas définie, les clients n’envoient pas de messages de synchronisation lors de la lecture du contenu protégé par cette stratégie. La valeur se compose de paires nom=valeur <span class="codeph"></span> séparées par des virgules avec le format suivant : </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> |force|hardStop=numberValue</span> </p> <p class="- topic/p "> 
     <ul id="ul_a5j_q4t_44"> 
      <li id="li_25CAF96C27F34848A95B2E3693847C71"><span class="codeph"></span> (obligatoire) : l'intervalle de  indique que le client doit s'de se synchroniser avec le serveur pendant ces nombreuses minutes depuis la dernière synchronisation. </li> 
      <li id="li_CC9068CFE75645029C947C9E1B53351F"><span class="codeph"> force</span> (facultatif) - Forcer la probabilité de synchronisation est la probabilité (0-100) avec laquelle le client doit forcer un message de synchronisation pendant la lecture. </li> 
      <li id="li_C31A6250F19348FBB8B7569D00C6314E"><span class="codeph"> hardStop</span> (facultatif) - Intervalle d'arrêt définitif est le temps en minutes après lequel le client échoue à la lecture s'il ne parvient pas à se synchroniser. Si elle est définie, elle doit être supérieure à l’intervalle  du. </li> 
     </ul>Lors de la mise à jour, utilisez <span class="codeph"> -sync</span> sans les arguments restants pour supprimer les conditions de synchronisation. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.useRootLicense</span> </td> 
   <td colname="2" class="- topic/entry ">Indique si cette stratégie comporte une licence racine (voir Chaîne <i class="+ topic/ph hi-d/i ">de licence</i> améliorée dans <i class="+ topic/ph hi-d/i ">Utilisation d’Adobe Access pour la protection du contenu</i>). </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.startDate</span> </td> 
   <td colname="2" class="- topic/entry ">Date à laquelle le contenu est valide. Utilisez le format <span class="+ topic/ph pr-d/codeph codeph">aaaa-mm-jj</span> (par exemple, <span class="codeph"> 2009-01-31</span> représente le 31 janvier à 12:00) ou <span class="+ topic/ph pr-d/codeph codeph">aaaa-mm-jj-h24:min:sec</span> (par exemple, <span class="codeph"> 2009-01-31-1 4:30:00 représente le 31 janvier à 14h30).</span> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.expiration.endDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Date avant laquelle le contenu est valide. Il est possible que <span class="codeph"> .expiration.endDate</span> et policy.expiration.length ne soient pas spécifiés simultanément. Utilisez le format <span class="+ topic/ph pr-d/codeph codeph">aaaa-mm-jj</span> ou <span class="+ topic/ph pr-d/codeph codeph">aaaa-mm-jj-h24:min:sec</span> (par exemple, 2009-01-31-14:30:00 représente le 31 janvier à 14h30). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.expiration.length</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">durée de validité (en minutes) du contenu, à partir du moment où il est compressé. Il est possible que <span class="codeph"> .expiration.endDate</span> et <span class="codeph"> .expiration.length</span> ne soient pas spécifiés simultanément. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.licenseCaching.length</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Durée pendant laquelle une licence peut être mise en cache sur le client (en minutes). Définissez cette propriété sur 0 pour désactiver la mise en cache des licences. La valeur doit être supérieure ou égale à 0. Il est impossible d’utiliser <span class="codeph"> .licenseCaching.length</span> et <span class="codeph"> .licenseCaching.endDate</span> simultanément. </p> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">Remarque</b>: Ce paramètre de stratégie s’applique uniquement à la mise en cache des licences sur le disque. Il ne contrôle pas la durée de la licence en mémoire cache. La licence peut être mise en cache en mémoire, même si la durée spécifiée par la stratégie est égale à zéro. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.licenseCaching.endDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Date à laquelle les licences ne peuvent pas être mises en cache. Il est impossible d’utiliser <span class="codeph"> .licenseCaching.length</span> et <span class="codeph"> .licenseCaching.endDate</span> simultanément. </p> </td> 
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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Des paires nom/valeur personnalisées à utiliser par le serveur lors de l’acquisition de la licence. Utilisez le format suivant pour spécifier des propriétés : <span class="+ topic/ph pr-d/codeph codeph">policy.customProp.n</span>=<span class="+ topic/ph pr-d/codeph codeph">name</span>=<span class="+ topic/ph pr-d/codeph codeph">value</span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.playbackWindow</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique la fenêtre de lecture (en minutes), qui correspond à la durée de validité de la licence après sa première utilisation pour lire du contenu protégé. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.digital</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Contraintes de protection de sortie. Les valeurs doivent être l’une des suivantes : </p> <p class="- topic/p "><i class="+ topic/ph hi-d/i ">NO_PROTECTION, USE_IF_AVAILABLE, REQUIS, NO_PLAYBACK</i> </p> </td> 
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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Un blanc d’applications Adobe AIR ou iOS permet de lire du contenu protégé. La propriété doit utiliser le format suivant : <span class="+ topic/ph pr-d/codeph codeph">pubId</span>[:<span class="+ topic/ph pr-d/codeph codeph">appId</span>[:[<span class="+ topic/ph pr-d/codeph codeph">min</span>]:[<span class="+ topic/ph pr-d/codeph codeph">max]]]</span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.allowedSWFApplication.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Un blanc d’applications SWF permet de lire du contenu protégé. Utilisez le format suivant : </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph">URL</span> ou file=<span class="+ topic/ph pr-d/codeph codeph">swf_file</span>,time=<i class="+ topic/ph hi-d/i ">max_time_to_verify</i> swf_file <i class="+ topic/ph hi-d/i "></i> est le fichier SWF pour lequel le calcul du hachage et max_time_to_verify est le temps maximal pour permettre le téléchargement et la vérification du SWF à terminer (en secondes).<i class="+ topic/ph hi-d/i "></i> </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.license.customProp.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Des paires nom/valeur personnalisées à inclure dans les licences délivrées aux utilisateurs. Utilisez le format suivant : </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph">policy.license.customProp.n</span>=<span class="+ topic/ph pr-d/codeph codeph">name</span>=<span class="+ topic/ph pr-d/codeph codeph">value</span> </p> <p class="- topic/p ">Cette option peut être définie plusieurs fois pour plusieurs propriétés personnalisées. </p> </td> 
  </tr> 
 </tbody> 
</table>

