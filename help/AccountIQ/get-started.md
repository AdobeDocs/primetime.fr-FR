---
title: Prise en main du compte IQ, des conditions préalables et de l’intégration
description: 'Intégration, conditions préalables et prise en main du compte IQ. '
source-git-commit: 258ce10297aa15086a3ed1c1a825af2a30d34d24
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Prise en main de Account IQ {#onboarding}

Lisez la suite pour connaître les conditions préalables à l’utilisation du compte IQ et comment votre entreprise peut-elle intégrer pour commencer à consulter le compte qui partage les scores d’abonnés.

## Conditions préalables {#prerequisites}

* L’organisation doit être enregistrée dans [!DNL Adobe Marketing Cloud] organisations.

* Les utilisateurs de cette organisation doivent être affectés à TVE Dashboard en lecture-écriture ou à TVE Dashboard en lecture seule.

### Conditions préalables du navigateur {#browser-prerequisites}

Account IQ est un service Web hébergé. Il est compatible avec la version la plus récente des navigateurs suivants :

* Google Chrome
* Mozilla Firefox
* Version de Safari

### Comment embarquer les organisations sur le compte IQ ? {#steps-to-onboard}


C&#39;est ce que nous avons en ce moment. L’objectif est de se débarrasser de la vérification dma_primetime et d’avoir un profil dédié pour AIQ. Les utilisateurs qui doivent avoir accès à la console auront besoin de ce profil utilisateur. Cela n&#39;est cependant pas mis en oeuvre pour le moment.

1. Votre organisation est intégrée dans Adobe Marketing Cloud @Eric ou @Peter, pouvez-vous prendre ceci en compte.  Je pense que c&#39;est maintenant appelé &quot;Experience Cloud&quot;, mais c&#39;est mineur.  Y a-t-il plus de détails à cela ? Est-ce géré par un autre groupe ? Si tel est le cas, pouvons-nous fournir un lien, un contact, etc. ? Cela doit également contenir une mise en garde concernant la vérification si leur organisation fait déjà partie de l’Experience Cloud.

2. Les profils &quot;Lecture-écriture du tableau de bord TVE&quot; ou &quot;Lecture seule du tableau de bord TVE&quot; sont attribués à leurs utilisateurs dans http://adminconsole.adobe.com/.
@Eric, savez-vous comment faire ?  Y a-t-il des étapes secondaires ?  Pouvons-nous expliquer aux clients pourquoi ils ont choisi Lecture-Écriture ou Lecture seule ?
@Cristina, pouvez-vous fournir une brève explication selon laquelle il s&#39;agit d&#39;une approche temporaire et peut-être comment cela fonctionnera dans la prochaine version ?

3. Si leur ID d&#39;organisation est placé sur la liste autorisée côté AIQ @Cristina, y a-t-il un processus que nous pouvons mettre en place pour gérer cela ?  Par exemple, envoyez un email à &quot;DL-AdobePass-Eng AdobePass-Eng@adobe.com&quot; avec l’ID d’organisation de l’organisation, etc.

<!-- these user groups set dma_primetime product context for the user accounts. In AIQ code we’re checking for this product context when providing access. Internally, in the code we have an additional condition: the org id should be whitelisted in order for the users to get access to their data. -->

Lors de l’accès à Adobe Enterprise Dashboard, les deux nouveaux groupes d’utilisateurs s’affichent dans votre organisation Adobe Marketing Cloud :

Tableau de bord TVE Lecture-écriture : les membres de ce groupe ont des droits complets sur toutes les sections modifiables du tableau de bord TVE Dashboard Lecture seule - les membres de ce groupe n’ont des droits d’affichage que sur l’ensemble du tableau de bord. Ajoutez votre compte au groupe d’utilisateurs Lecture-Écriture du tableau de bord TVE Dashboard dans Adobe Enterprise Dashboard, puis connectez-vous au tableau de bord Adobe Primetime TVE.  Par la suite, vous pourrez gérer les autorisations utilisateur dans Adobe Enterprise Dashboard en ajoutant et en supprimant des utilisateurs dans les deux groupes d’utilisateurs répertoriés ci-dessus.

..........

Dans la documentation que vous avez fournie, vous trouverez cette partie appelée &quot;Prise en main de l’approvisionnement des utilisateurs du tableau de bord Primetime TVE&quot; qui s’applique à la console Adobe Pass, mais qui doit également être similaire pour AIQ.
http://tve.helpdocsonline.com/primetime-tve-dashboard-user-guide L’organisation qui s’intéresse à AIQ doit être une organisation enregistrée dans les organisations Adobe Marketing Cloud. Les utilisateurs de cette organisation doivent être affectés à TVE Dashboard en lecture-écriture ou à TVE Dashboard en lecture seule.
À votre connaissance seulement, ces groupes d’utilisateurs définissent le contexte du produit dma_primetime pour les comptes d’utilisateurs. Dans le code AIQ, nous vérifions ce contexte de produit lors de la fourniture de l’accès. En interne, dans le code, une condition supplémentaire s’affiche : l’ID d’organisation doit être placé sur la liste autorisée pour que les utilisateurs puissent accéder à leurs données.
C&#39;est ce que nous avons en ce moment. L’objectif est de se débarrasser de la vérification dma_primetime et d’avoir un profil dédié pour AIQ. Les utilisateurs qui doivent avoir accès à la console auront besoin de ce profil utilisateur. Cela n&#39;est cependant pas mis en oeuvre pour le moment.

.........................

1. Intégration de leur organisation dans Adobe Marketing Cloud
2. Les profils &quot;Lecture-écriture du tableau de bord TVE&quot; ou &quot;Lecture seule du tableau de bord TVE&quot; sont attribués à leurs utilisateurs dans http://adminconsole.adobe.com/.
3. Avoir leur ID d’organisation placé sur la liste autorisée côté AIQ
