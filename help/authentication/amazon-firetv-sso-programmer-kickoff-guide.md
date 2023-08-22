---
title: Amazon fireTV SSO - Guide de démarrage du programmeur
description: Amazon fireTV SSO - Guide de démarrage du programmeur
exl-id: cf9ba614-57ad-46c3-b154-34204b38742d
source-git-commit: 84a16ce775a0aab96ad954997c008b5265e69283
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 0%

---

# Amazon fireTV SSO - Guide de démarrage du programmeur {#amazon-firetv-sso---programmer-kick-off-guide}

>[!NOTE]
>
>Le contenu de cette page est fourni à titre d’information uniquement. L’utilisation de cette API nécessite une licence actuelle de Adobe. Aucune utilisation non autorisée n’est autorisée.

</br>

## Introduction {#intro}

Ce document décrit les informations nécessaires à l’intégration de la nouvelle **SDK FireTV de l’authentification Adobe Primetime** dans votre application fireTV. Ce nouveau SDK tire parti de l’intégration au niveau du système d’exploitation sur la plateforme Amazon FireTV pour offrir **Authentification unique** la prise en charge. Pour bénéficier de l’authentification unique, votre côté doit faire quelques efforts afin de migrer votre application de l’API sans client vers le nouveau SDK FireTV. Des modifications seront apportées aux flux d’authentification, qui seront présentés ci-dessous.

## Intégration de haut niveau à l’architecture et au niveau du système d’exploitation {#high}

Afin d’atteindre l’authentification unique entre les applications TV Everywhere sur la plateforme Amazon FireTV et d’améliorer l’expérience globale sur cette plateforme, nous avons décidé d’intégrer notre SDK principal au niveau du système d’exploitation FireTV. Les programmeurs devront compiler par rapport à une bibliothèque stub fournie par Adobe. La fonctionnalité réelle sera fournie par la bibliothèque d’Adobes présente dans Amazon FireTV OS.

Tant qu’Amazon ne fournit pas de simulateur FireTV qui intègre notre bibliothèque au niveau du système d’exploitation, le développement ne sera possible qu’à l’aide de véritables appareils FireTV.

## Avantages {#bene}

* Authentification unique entre toutes les applications TV partout alimentées par Adobe sur la plateforme Amazon FireTV avec tous les MVPD intégrés.
* Possibilité de bénéficier de l’adaptateur de bus hôte (avec les MVPD pris en charge).
* Possibilité d’utiliser le dernier SDK FireTV sans avoir à mettre à jour vos applications chaque fois qu’une nouvelle version du SDK est publiée.
* Toutes les applications TVE bénéficient de l’utilisation de la bibliothèque système partagée en supprimant la nécessité d’avoir une copie locale de la bibliothèque AccessEnabler. Cela permet également de s’assurer que toutes les applications utilisent la même version du SDK.
* Authentification à un seul écran : pas besoin de code d’enregistrement et de workflows à deuxième écran.

## Migration d’une application basée sur une API sans client vers une application basée sur le SDK FireTV {#migra1}

Pour migrer de l’API sans client vers le SDK FireTV, vous devez supprimer le code base associé à l’API sans client et intégrer le nouveau SDK FireTV.

Par rapport à l’application sans API cliente, avec le nouveau SDK FireTV, l’authentification passe au premier écran, il n’est plus nécessaire d’effectuer une deuxième authentification d’écran.

Pour ce faire, les programmeurs doivent ajouter un sélecteur MVPD dans leurs applications afin que les utilisateurs puissent choisir leur fournisseur de télévision directement sur le périphérique FireTV. Lors de la sélection de MVPD, l’utilisateur voit apparaître la page de connexion MVPD sur l’appareil FireTV.

Vous trouverez des maquettes des flux d’utilisateurs qui décrivent les scénarios standard, d’adaptateur et d’authentification unique sur fireTV à l’adresse [Amazon Fire TV - Flux d’utilisateur de connexion MVPD](https://xd.adobe.com/view/9058288e-4b67-43a1-9d5b-5f76ede6c51e/).

## Migration de l’application basée sur le SDK Android vers l’application basée sur le SDK FireTV {#migra2}

Ce nouveau SDK FireTV est très similaire à notre SDK Android existant et à la documentation actuelle que nous avons pour **intégration de notre SDK Android** <!--http://tve.helpdocsonline.com/android-technical-overview-->peut être utilisé jusqu’à ce que les documents du SDK FireTV soient prêts. Si vous disposez déjà d’applications Android qui utilisent notre SDK Android, l’intégration du SDK FireTV dans votre application FireTV doit être simple.

Par rapport au SDK Android existant, le processus d’authentification sera plus simple à développer sur le SDK FireTV, car les tâches de gestion/présentation de la page de connexion MVPD et de récupération du jeton AuthN seront effectuées en interne par la bibliothèque AccessEnabler.

## Questions fréquentes {#faq}

1. Comment la variable **SSO** travail ?

   * SSO fonctionnera dans toutes les applications de programmeur optimisées par l’authentification Adobe Primetime qui utilisent le nouveau SDK FireTV sur le même appareil FireTV Amazon.
   * SSO entre les applications de programmation implémentées sur l’API REST sans client et les applications implémentées sur le SDK FireTV **ne sera PAS pris en charge**

1. Quelle est la couverture MVPD de fireTV SSO ?

   * **Tous les MVPD** l’authentification Adobe Primetime sera techniquement prise en charge par SSO sur le SDK fireTV.

1. Outre l’utilisation du nouveau SDK, et d’autres **modifications de workflow** Les programmeurs devraient-ils être conscients ?

   * Les programmeurs doivent mettre en oeuvre un sélecteur MVPD pour la plateforme fireTV.

1. L’authentification sera-t-elle modifiée ? **TTL**?

   * Il n’y a aucun changement de comportement concernant les TTL d’authentification.
   * Le premier jeton d’authentification valide sera utilisé pour effectuer l’authentification unique. Dans ce cas, toutes les autres applications qui seront authentifiées via l’authentification unique utiliseront le même TTL jusqu’à son expiration. Ainsi, lorsque vous naviguez d’une application à l’autre, la deuxième application partage la durée de vie de la première application qui s’authentifie.

1. Comment **API de dégradation** travail ?

   * Aucune modification n’est nécessaire pour l’API de dégradation. L’expérience utilisateur sera la même que sur les appareils Android.

1. Comment **TempPass** les flux sont affectés ?

   * Les flux TempPass sont un seul écran et se comportent comme sur tout autre appareil natif.

1. Les autres fonctionnalités d’Adobe fonctionneront-elles comme auparavant ?

   * Toutes les fonctionnalités d’authentification Primetime fonctionneront sur fireTV comme sur les appareils Android.
