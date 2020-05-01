---
seo-title: Utilisation de la ligne de commande
title: Utilisation de la ligne de commande
uuid: e549a98e-b027-4472-8860-6aa1d56d4a8b
translation-type: tm+mt
source-git-commit: ''

---


# Utilisation de la ligne de commande {#command-line-usage}

Avant d’utiliser Policy Manager, assurez-vous de respecter les exigences répertoriées dans la section Conditions requises.

Policy Manager se trouve dans le [!DNL \Reference Implementation\Command Line Tools] répertoire du DVD. Pour exécuter l’outil, utilisez la syntaxe suivante :

```
java -jar AdobePolicyManager.jar  
<i class="+ topic ph hi-d="" i "="">
  command filename [options] 
</i class="+ topic>
```

Le tableau suivant contient la description des actions de ligne de commande indiquées dans la syntaxe ci-dessus :

| Action de ligne de commande | Description |
|---|---|
| `new` | Crée une nouvelle stratégie. |
| `detail` | Décrit une stratégie existante. |
| `update` | Met à jour une stratégie existante. |

Le tableau suivant décrit les options de ligne de commande qui peuvent être spécifiées avec la syntaxe ci-dessus :

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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique l’emplacement du fichier de configuration. Si cette option n'est pas utilisée, le gestionnaire de stratégies recherche <span class="filepath"> flashaccesstools.properties </span> dans le répertoire de travail. Les options spécifiées sur la ligne de commande sont prioritaires sur celles du fichier de configuration. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Si le fichier de destination existe déjà, remplacez-le sans invite. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -noprompt </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Ne demandez pas si le fichier de destination doit être remplacé. Si le fichier de destination existe déjà et que <span class="codeph"> -o </span> n'est pas défini, une erreur est renvoyée. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -root </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique que la stratégie possède une licence racine. Non autorisé pour les mises à jour. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -e date </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Date avant laquelle les licences seront valides. Indiquez comme <span class="+ topic/ph pr-d/codeph codeph"> aaaa-mm-jj </span> ou <span class="+ topic/ph pr-d/codeph codeph"> aaaa-mm-jj-h24:min:sec </span>. Par exemple, 2008-12-1 ou 2008-12-1-00:00:00 pour minuit le 1er décembre 2008. La valeur doit être supérieure à la valeur de <span class="codeph"> -s </span>, le cas échéant. Cette option ne peut pas être utilisée avec <span class="codeph"> -r </span>. Pour supprimer la date de fin lors de la mise à jour d’une stratégie, utilisez <span class="codeph"> -e </span> sans spécifier de date. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -r minutes </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">La durée (en minutes) pendant laquelle le contenu protégé par cette stratégie est valide, à partir du moment où le contenu est protégé par l’outil de création de package. La valeur doit être non négative. Cette option ne peut pas être utilisée avec <span class="codeph"> -e </span>. Pour supprimer la durée lors de la mise à jour d’une stratégie, utilisez <span class="codeph"> -r </span> sans spécifier un nombre de minutes. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -s date </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Date à laquelle les licences seront valides. Indiquez comme <span class="+ topic/ph pr-d/codeph codeph"> aaaa-mm-jj </span> ou <span class="+ topic/ph pr-d/codeph codeph"> aaaa-mm-jj-h24:min:sec </span>. Par exemple, 2008-12-1 ou 2008-12-1-00:00:00 pour minuit le 1er décembre 2008. La valeur doit être inférieure à la valeur de <span class="codeph"> -e </span>, le cas échéant. Cette option ne peut pas être utilisée avec <span class="codeph"> -r </span>. Pour supprimer la date du début lors de la mise à jour d’une stratégie, utilisez <span class="codeph"> -s </span> sans spécifier de date. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -w minutes </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">La fenêtre de lecture (nombre de minutes pendant lesquelles le contenu peut être affiché, à partir de la première lecture). Si cette option n’est pas spécifiée ou si <span class="codeph"> -w </span> est utilisé sans indiquer le nombre de minutes, la fenêtre de lecture n’est pas limitée. La valeur doit être non négative. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -l minutes </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Durée de mise en cache de la licence en minutes, c’est-à-dire le moment où une licence est autorisée à être mise en cache dans le magasin de licences du client une fois la licence émise par le serveur. La valeur doit être non négative. Spécifiez <span class="codeph"> -l 0 </span> pour indiquer que la mise en cache des licences n’est pas autorisée. Utilisez <span class="codeph"> -l </span> sans spécifier un nombre de minutes pour la mise en cache illimitée des licences. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -date de mise à jour </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Date de fin de mise en cache de la licence (date à laquelle les licences ne peuvent pas être mises en cache dans le magasin de licences du client, une fois la licence émise par le serveur). Indiquez comme <span class="+ topic/ph pr-d/codeph codeph"> aaaa-mm-jj </span><i class="+ topic/ph hi-d/i "> ou </i><i class="+ topic/ph hi-d/i "> </i> aaaa-mm-jj-h24:min:sec <span class="+ topic/ph pr-d/codeph codeph"> </span>. Par exemple, 2008-12-1 ou 2008-12-1-00:00:00 pour minuit le 1er décembre 2008. Utilisez <span class="codeph"> -l </span> sans spécifier un nombre de minutes pour la mise en cache illimitée des licences. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -authNS </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">espace de nommage d'authentification. Si spécifié, le client doit s’authentifier avec un nom d’utilisateur et un mot de passe émis par l’autorité spécifiée. Cette option ne peut pas être utilisée avec <span class="codeph"> -x </span>. Il n’est pas autorisé pour les mises à jour. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -x </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Autoriser l’accès anonyme. Cette option ne peut pas être utilisée avec <span class="codeph"> -authNS </span>. Il n’est pas autorisé pour les mises à jour. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -air pubId </span>[ : <span class="+ topic/ph pr-d/codeph codeph"> appId </span>[:[ <span class="+ topic/ph pr-d/codeph codeph"> min </span>]:[ <span class="+ topic/ph pr-d/codeph codeph"> max </span>]]] </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Liste blanche des applications AIR autorisées à lire du contenu protégé. Utilisez cette option pour restreindre les éditeurs, les applications et les versions qui peuvent accéder au contenu protégé par cette stratégie. </p> <p class="- topic/p ">Si <i class="+ topic/ph hi-d/i ">appId</i> n’est pas spécifié, toutes les applications pour publisher <i class="+ topic/ph hi-d/i ">pubId</i> sont autorisées. </p> <p class="- topic/p "><i class="+ topic/ph hi-d/i ">les numéros de version min</i> et <i class="+ topic/ph hi-d/i ">max</i> sont facultatifs. </p> <p class="- topic/p ">Plusieurs <span class="codeph"> options </span> -air peuvent être spécifiées pour autoriser plusieurs applications. Si aucune application AIR ou SWF n’est spécifiée, toutes les applications peuvent accéder à ce contenu. Lors d’une mise à jour, utilisez -air sans les arguments restants pour supprimer toutes les entrées de la liste. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -drmChaîne de liste noire nom </span><i class="+ topic/ph hi-d/i ">/</i> valeur <span class="+ topic/ph pr-d/codeph codeph"></span> paires <i class="+ topic/ph hi-d/i "> </i> <span class="+ topic/ph pr-d/codeph codeph"></span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Les clients DRM ne peuvent pas accéder au contenu protégé. La valeur est composée de paires nom:valeur séparées par des virgules avec le format suivant : </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> os | release= stringValue </span> </p> <p class="- topic/p ">Par exemple, <span class="codeph"> os=Win,release=2.0.1 </span>. Lors d’une mise à jour, utilisez <span class="codeph"> -drmBlacklist </span> sans les arguments restants pour supprimer toutes les entrées de la liste. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -drmLevel int </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique que les clients DRM doivent avoir le niveau de sécurité minimum spécifié pour accéder au contenu protégé. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opAnalog NO_PROTECTION | USE_IF_AVAILABLE | OBLIGATOIRE | NO_PLAYBACK | ACP_REQUIRED | CGMS-A_REQUIRED | USE_ACP_IF_AVAILABLE | USE_CGMS-A_IF_AVAILABLE </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Contraintes de protection de la sortie analogique. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opDigital NO_PROTECTION | USE_IF_AVAILABLE | OBLIGATOIRE | NO_PLAYBACK </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Contraintes de protection de la sortie numérique. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -runtimeChaîne de liste noire nom </span><i class="+ topic/ph hi-d/i ">/</i> <span class="+ topic/ph pr-d/codeph codeph"> valeur </span> <i class="+ topic/ph hi-d/i "> </i> de paires <span class="+ topic/ph pr-d/codeph codeph"></span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Les runtimes de l'application empêchaient l'accès au contenu protégé. La valeur est composée de paires nom:valeur séparées par des virgules avec le format suivant : </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> os | application | release= stringValue </span> </p> <p class="- topic/p ">Par exemple, <span class="codeph"> os=Win,release=2.0.1,application=AIR </span>. Lors d’une mise à jour, utilisez <span class="codeph"> -runtimeBlacklist </span> sans les arguments restants pour supprimer toutes les entrées de la liste. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -runtimeLevel int </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Indique que les exécutions d’application doivent avoir le niveau de sécurité minimum spécifié pour accéder au contenu protégé. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -swf url </span> </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -swf file= fichier_swf </span>, <span class="+ topic/ph pr-d/codeph codeph"> time= max_time_to_verify </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Liste blanche des applications SWF autorisées à lire du contenu protégé. Plusieurs options -swf peuvent être spécifiées pour autoriser plusieurs applications. Si aucune application AIR ou SWF n’est spécifiée, toutes les applications peuvent accéder à ce contenu. Lors d’une mise à jour, utilisez -swf sans les arguments restants pour supprimer toutes les entrées de la liste. Pour identifier un fichier SWF par sa valeur de hachage, spécifiez le fichier SWF pour lequel calculer le hachage et la durée maximale pour permettre l’exécution de la vérification du fichier SWF (en secondes). </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -k name= valeur </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Spécifie les clés/valeurs personnalisées à ajouter à la stratégie. Plusieurs options <span class="codeph"> -k </span> peuvent être spécifiées. Lors de la mise à jour, utilisez <span class="codeph"> -k </span> sans les arguments restants pour supprimer toutes les propriétés. L’interprétation ou le traitement de ces données dépend entièrement de la mise en oeuvre du serveur de licences Adobe Access. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -p name= valeur </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Ajoute une propriété personnalisée qui apparaîtra dans la licence générée pour chaque client. Plusieurs options <span class="codeph"> -p </span> peuvent être spécifiées pour ajouter plusieurs propriétés. Lors d’une mise à jour, utilisez <span class="codeph"> -p </span> sans les arguments restants pour supprimer toutes les propriétés. L'interprétation ou le traitement de ces données dépend entièrement de la mise en oeuvre de l'application cliente. </p> </td> 
  </tr> 
 </tbody> 
</table>

