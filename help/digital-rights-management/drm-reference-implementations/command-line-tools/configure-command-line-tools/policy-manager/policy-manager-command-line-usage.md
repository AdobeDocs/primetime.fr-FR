---
title: Utilisation de la ligne de commande de Policy Manager
description: Utilisation de la ligne de commande de Policy Manager
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1223'
ht-degree: 0%

---

# Utilisation de la ligne de commande de Policy Manager {#policy-manager-command-line-usage}

```
java -jar AdobePolicyManager.jar  
<i class="+ topic ph hi-d="" i "="">
  command filename [options] 
</i class="+ topic>
```

**Tableau 1 : Commandes**

| Commande | Description |
|---|---|
| `new` | Création d’une stratégie DRM |
| `detail` | Décrit une stratégie DRM existante. |
| `update` | Met à jour une stratégie DRM existante |

**Tableau 2 : Options**

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_q5h_cpy_n4">  
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Option de ligne de commande </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Description </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -c configfile </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique le nom et l’emplacement du fichier de configuration. </p> <p class="- topic/p ">Si vous ne spécifiez aucun nom ou emplacement, le Gestionnaire de stratégies DRM recherche <span class="filepath"> flashaccesstools.properties </span> dans le répertoire de travail actuel. </p> <p>Remarque : les options que vous spécifiez sur la ligne de commande sont prioritaires sur celles que vous spécifiez dans le fichier de configuration. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Si le fichier de destination existe, vous pouvez le remplacer sans y être invité. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -noprompt </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Ne demandez pas si le fichier de destination doit être remplacé. Si le fichier de destination existe et <span class="codeph"> -o </span> n’est pas définie, une erreur se produit. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -root </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique que la stratégie DRM possède une licence racine. </p> <p class="- topic/p ">Cette option n’est pas disponible pour les mises à jour. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -e date </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">La date de validité des licences. </p> <p>Vous pouvez spécifier la date dans la section <span class="+ topic/ph pr-d/codeph codeph"> aaaa-mm-jj </span> ou <span class="+ topic/ph pr-d/codeph codeph"> aaaa-mm-jj-h24:min:sec </span> format. Par exemple, 2008-12-1 ou 2008-12-1-00:00:00 pour minuit le 1er décembre 2008. </p> <p> 
     <ul id="ul_D5DB5044756D4BD6A734813971598425"> 
      <li id="li_B6BD62A524384060A9DDA14FF50936FA">La valeur doit être supérieure à la valeur de <span class="codeph"> -s </span> s’il est présent. </li> 
      <li id="li_C3C5AD0231A240EC9AC57685B9206E8D">Vous ne pouvez pas appliquer cette option avec <span class="codeph"> -r </span>. </li> 
      <li id="li_3790E2F829A149979BF44E0914CFF431">Pour supprimer la date de fin lors de la mise à jour d’une stratégie DRM, appliquez <span class="codeph"> -e </span> sans spécifier de date. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -r minutes </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Durée en minutes de validité du contenu protégé. </p> <p class="- topic/p ">La stratégie DRM devient valide lorsque le contenu est protégé par le programme de package. </p> <p> 
     <ul id="ul_4690A0E4677A4DF6A006B7FCBD46F1BE"> 
      <li id="li_D1F098D44B494EE7A8647C0B62D5ACFA">La valeur doit être non négative. </li> 
      <li id="li_ADFDCB01EEE04B37AFA42886AAEF47EB">Vous ne pouvez pas appliquer cette option avec la variable <span class="codeph"> -e </span>. </li> 
      <li id="li_E80563E68BEB43FC9E29A694594CAE01">Pour supprimer ou supprimer la durée lors de la mise à jour d’une stratégie DRM, appliquez <span class="codeph"> -r </span> sans préciser de minutes. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -s date </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Date de validité des licences. </p> <p>Vous pouvez spécifier la date dans la variable <span class="+ topic/ph pr-d/codeph codeph"> aaaa-mm-jj </span> ou <span class="+ topic/ph pr-d/codeph codeph"> aaaa-mm-jj-h24:min:sec </span> format. Par exemple : <span class="codeph"> 2008-12-1 </span> ou <span class="codeph"> 2008-12-1-00:00:00 </span> pour minuit le 1er décembre 2008. </p> <p> 
     <ul id="ul_D52B337F547F4E7AB87FE025236CA930"> 
      <li id="li_DBAE380972434DB1A4EF20D399038AB8">La valeur doit être inférieure à la valeur de <span class="codeph"> -e </span>, le cas échéant. </li> 
      <li id="li_2899EC5559CF44319A4AC4ECD90A5B9A">Vous ne pouvez pas appliquer cette option avec la variable <span class="codeph"> -r </span>. </li> 
      <li id="li_19861B1A64E44B95B649948EAB3E4085">Pour supprimer ou supprimer la date de début lors de la mise à jour d’une stratégie DRM, utilisez <span class="codeph"> -s </span> sans spécifier de date. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -w [&lt;minutes&gt;[,enableHS|disableHS]] </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Fenêtre de lecture, qui correspond au nombre de minutes pendant lesquelles le contenu peut être affiché lors de la première lecture. </p> <p>Si non spécifié, ou si <span class="codeph"> -w </span> est utilisé sans spécifier de nombre de minutes, il n’y a aucune limitation de fenêtre de lecture. La valeur doit être non négative. </p> <p>Le paramètre facultatif <span class="codeph"> enableHS </span> ou <span class="codeph"> disableHS </span> Le drapeau indique s’il faut activer ou désactiver l’arrêt hard. L’indicateur indique si le contexte de décryptage est détruit à la fin de la fenêtre de lecture (activé) ou non (désactivé). </p> <p>Par exemple, pour indiquer que le contenu ne peut être affiché que pendant 60 minutes et nécessite un arrêt hard : 
     <codeblock>
       -w&amp;nbsp;60,enableHS 
     </codeblock> </p> <p>Remarque :  <i>Arrêt Hard</i> n’est actuellement pas pris en charge dans Flash Player, Android et iOS. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -l minutes </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">La durée de mise en cache d’une licence correspond au temps en minutes qu’une licence peut être mise en cache dans le magasin de licences du client une fois la licence émise par le serveur. La valeur doit être non négative. </p> <p>Vous pouvez indiquer <span class="codeph"> -l 0 </span> pour indiquer que la mise en cache de licence n’est pas autorisée. Pour une mise en cache illimitée des licences, spécifiez <span class="codeph"> -l </span> sans minutes. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -date de mise à jour </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Date de fin de la mise en cache de la licence. </p> <p class="- topic/p ">Cela indique la date finale à laquelle le client peut mettre en cache les licences dans le magasin de licences du client après que le serveur Primetime DRM a émis la licence. </p> <p>Vous pouvez spécifier la date dans les formats suivants : 
     <ul id="ul_112DE7248A9C48B19520A3AA9E5D1F03"> 
      <li id="li_01C5400E78B84A3B8955972FBA875AAC"> <span class="+ topic/ph pr-d/codeph codeph"> aaaa-mm-jj </span> </li> 
      <li id="li_AA13B1EFA07A4542A3DB41FA3320B143"> <span class="+ topic/ph pr-d/codeph codeph"> aaaa-mm-jj-h24:min:sec </span> </li> 
     </ul>Par exemple : <span class="codeph"> 2008-12-1 </span> ou <span class="codeph"> 2008-12-1-00:00:00 </span> pour minuit le 1er décembre 2008. Vous devez demander <span class="codeph"> -l </span> sans spécifier de minutes pour la mise en cache illimitée de la licence. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -authNS </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Espace de noms d’authentification. </p> <p class="- topic/p ">Si vous appliquez cette option, le client doit saisir un nom d’utilisateur et un mot de passe émis par l’autorité spécifiée. </p> <p>Vous ne pouvez pas appliquer cette option avec la variable <span class="codeph"> -x </span>. </p> <p>Cette option n’est pas autorisée pour les mises à jour. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -x </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Autoriser l'accès anonyme </p> <p class="- topic/p ">Vous ne pouvez pas appliquer cette option avec la variable <span class="codeph"> -authNS </span>. </p> <p class="- topic/p ">Cette option n’est pas autorisée pour les mises à jour. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -air pubId </span>[: <span class="+ topic/ph pr-d/codeph codeph"> appId </span>[:[ <span class="+ topic/ph pr-d/codeph codeph"> min </span>]:[ <span class="+ topic/ph pr-d/codeph codeph"> max </span>]] </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Liste autorisée d’applications AIR pouvant lire du contenu protégé. </p> <p class="- topic/p ">Vous pouvez appliquer cette option pour restreindre les éditeurs, les applications et les versions qui peuvent accéder au contenu protégé par cette stratégie DRM. </p> <p class="- topic/p ">Si vous ne spécifiez pas <i class="+ topic/ph hi-d/i ">appId</i>, toutes les applications pour éditeur <i class="+ topic/ph hi-d/i ">pubId</i> sont autorisées. </p> <p>Remarque :  <i class="+ topic/ph hi-d/i ">min</i> et <i class="+ topic/ph hi-d/i ">max</i> les numéros de version sont facultatifs. </p> <p class="- topic/p ">Vous pouvez spécifier plusieurs <span class="codeph"> -air </span> pour autoriser plusieurs applications. Si vous ne spécifiez aucune application AIR ou SWF, toutes les applications peuvent accéder à ce contenu. Lors d’une mise à jour, pour supprimer toutes les entrées de la liste, appliquez <span class="codeph"> -air </span> sans les arguments restants. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -drmBlacklist name </span> <i class="+ topic/ph hi-d/i ">/</i> <span class="+ topic/ph pr-d/codeph codeph"> value </span> <i class="+ topic/ph hi-d/i "> </i> <span class="+ topic/ph pr-d/codeph codeph"> paires </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Les clients DRM qui ne peuvent pas accéder au contenu protégé. </p> <p class="- topic/p ">La valeur prend en charge les paires nom:valeur séparées par des virgules au format suivant : </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> os | release= stringValue </span> </p> <p class="- topic/p ">Par exemple : <span class="codeph"> os=Win,release=2.0.1 </span>. Lors d’une mise à jour, pour supprimer toutes les entrées de la liste, appliquez <span class="codeph"> -drmBlacklist </span> sans les arguments restants. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -drmLevel int </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique que le niveau de sécurité minimal doit être attribué aux clients DRM pour accéder au contenu protégé. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opAnalog NO_PROTECTION | USE_IF_AVAILABLE | OBLIGATOIRE | NO_PLAYBACK | REQUIRED_ACP | REQUIRED_CGMSA | USE_IF_AVAILABLE_ACP | USE_IF_AVAILABLE_CGMSA </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Contraintes de protection de sortie Analog </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opDigital NO_PROTECTION | USE_IF_AVAILABLE | OBLIGATOIRE | NO_PLAYBACK </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Contraintes de protection de la production numérique </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -runtimeBlacklist name </span> <i class="+ topic/ph hi-d/i ">/</i> <span class="+ topic/ph pr-d/codeph codeph"> value </span> <i class="+ topic/ph hi-d/i "> </i> <span class="+ topic/ph pr-d/codeph codeph"> paires </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Les environnements d’exécution de l’application qui ne peuvent pas accéder au contenu protégé. </p> <p class="- topic/p ">La valeur prend en charge les paires nom:valeur séparées par des virgules au format suivant : </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> os | application | release= stringValue </span> </p> <p class="- topic/p ">Par exemple : <span class="codeph"> os=Win,release=2.0.1,application=AIR </span>. Lors d’une mise à jour, pour supprimer toutes les entrées de la liste, appliquez <span class="codeph"> -runtimeBlacklist </span> sans les arguments restants. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -runtimeLevel int </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique que les environnements d’exécution de l’application doivent avoir un niveau de sécurité minimal spécifié pour accéder au contenu protégé. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -swf url </span> </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -swf file= swf_file </span>, <span class="+ topic/ph pr-d/codeph codeph"> time= max_time_to_verify </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Liste autorisée d’applications SWF autorisées à lire du contenu protégé. </p> <p class="- topic/p ">Vous pouvez spécifier plusieurs <span class="codeph"> -swf </span> pour autoriser plusieurs applications. Si vous ne spécifiez aucune application AIR ou SWF, toutes les applications peuvent accéder à ce contenu. </p> <p>Lors d’une mise à jour, pour supprimer toutes les entrées de la liste, appliquez <span class="codeph"> -swf </span> sans les arguments restants. Si vous souhaitez identifier un SWF par sa valeur de hachage, vous devez spécifier le fichier de SWF pour lequel le hachage doit être calculé et la durée maximale pour permettre la vérification du SWF (en secondes). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -k name= value </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Spécifie la ou les clé(s) personnalisée(s) que vous souhaitez ajouter à une stratégie DRM. </p> <p class="- topic/p ">Vous pouvez spécifier plusieurs <span class="codeph"> -k </span> options. Lors de la mise à jour, vous pouvez appliquer des <span class="codeph"> -k </span> sans les arguments restants si vous souhaitez supprimer toutes les propriétés. L’interprétation ou le traitement des données est géré par le serveur de licences Primetime DRM. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -p name= value </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Ajoute une propriété personnalisée qui apparaît dans la licence générée pour chaque client. </p> <p class="- topic/p ">Vous pouvez spécifier plusieurs <span class="codeph"> -p </span> pour ajouter plusieurs propriétés. Lors d’une mise à jour, vous devez appliquer des <span class="codeph"> -p </span> sans les arguments restants si vous souhaitez supprimer toutes les propriétés. L’interprétation ou le traitement de ces données est géré par l’implémentation de l’application cliente. </p> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> <span class="codeph"> -opOTA whitelist=&lt;connection types=""&gt; </span> </span> </td> 
   <td colname="2" class="- topic/entry "> Contraintes de protection de la production dans l'air (OTA). La variable <span class="codeph"> whitelist </span> indique les types de connexion à liste autorisée et le format de &lt;connection types=""&gt; is <span class="codeph"> [type(,type)*] </span>, où le type peut être l’un des suivants : MIRACAST, AIRPLAY, WIDI, DLNA </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opResolution &lt;filename&gt; </span> </td> 
   <td colname="2" class="- topic/entry "> <p>Contraintes de protection de sortie basées sur une résolution, telles que définies dans le fichier spécifié. </p> <p>Le codage de ce fichier est JSON. La grammaire de la mise en forme se trouve dans la section <i>À propos de la protection des sorties basée sur la résolution</i>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Exemples**

Pour créer une stratégie permettant l’accès anonyme à votre contenu, à l’aide de votre propre fichier de propriétés de configuration :

```
java -jar libs\AdobePolicyManager.jar new policy_test.pol -x -c my_configuration.properties
```
