---
title: Débogage du SDK AccessEnabler iOS/tvOS à l’aide des journaux d’application de la console
description: Débogage du SDK AccessEnabler iOS/tvOS à l’aide des journaux d’application de la console
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---


# Débogage du SDK AccessEnabler iOS/tvOS à l’aide des journaux d’application de la console {#debugging-the-accessenabler-iostvos-sdk-using-console-app-logs}

>[!NOTE]
>
>Le contenu de cette page est fourni à titre d’information uniquement. L’utilisation de cette API nécessite une licence actuelle de Adobe. Aucune utilisation non autorisée n’est autorisée.


## Présentation

Ce document a pour but de capturer et de présenter l’évolution du mécanisme de journalisation du SDK iOS/tvOS d’AccessEnabler, ainsi que quelques détails utiles pour déboguer la structure AccessEnabler à l’aide des journaux d’application de la console.

## État du mécanisme de journalisation

Le mécanisme de journalisation d’AccessEnabler iOS/tvOS a pour objectif d’émettre des messages utiles pour résoudre les problèmes éventuels qu’une application utilisant la structure AccessEnabler pourrait rencontrer en raison de ce problème.

### AccessEnabler iOS/tvOS 3.5.0 et versions ultérieures

À partir de la version iOS/tvOS 3.5.0 d’AccessEnabler, le mécanisme de journalisation introduit les améliorations suivantes lors des modifications :

* La structure AccessEnabler utilise Apple recommandé [OSLog](https://developer.apple.com/documentation/os/oslog) implémentation.

* La structure AccessEnabler introduit la possibilité de filtrer les journaux d’application de la console en fonction du sous-système : **com.adobe.pass.AccessEnabler**. Tous les messages émis par le SDK font partie de com.adobe.pass.AccessEnabler.

* La structure AccessEnabler introduit la possibilité de filtrer les journaux d’application de la console en fonction de n’importe quel (préfixe) : **[AccessEnabler]**. Tous les messages émis par le SDK sont précédés du préfixe [AccessEnabler].

* La structure AccessEnabler introduit la possibilité de filtrer les journaux d’application de la console en fonction de la catégorie : **debug**, **error** en association avec l’un des deux critères ci-dessus : Subsystem ou Any (préfixe).

## Débogage à l’aide des journaux de l’application Console

En fonction des problèmes qui font l’objet d’une enquête, vous pouvez inclure ou exclure les messages de journalisation émis par l’infrastructure AccessEnabler. Vous trouverez donc ci-dessous des détails utiles qui peuvent vous aider lors des enquêtes et lors de l’utilisation des journaux d’application de la console.


### AccessEnabler iOS/tvOS 3.5.0 et versions ultérieures

#### Inclusion {#including}

Tout d’abord, afin de pouvoir voir tous les messages de journalisation émis par la structure AccessEnabler que vous avez **must** sélectionnez les options &quot;Inclure les messages d’informations&quot; et &quot;Inclure les messages de débogage&quot; dans la section Action de l’application Console, comme présenté dans l’image ci-dessous.

![](assets/include-info-debug-msg.png)


Pour pouvoir déboguer les fonctionnalités du SDK AccessEnabler iOS/tvOS et **see** Les journaux de la structure AccessEnabler vous permettent :

* Recherche dans l’application Console à l’aide de **Subsystem** qui Correspond à la valeur com.adobe.pass.AccessEnabler comme dans l’image ci-dessous.

![](assets/subsys-console-app.png)

* Recherche dans l’application Console à l’aide de **Quelconque** qui contient la variable
   [AccessEnabler] comme dans l’image ci-dessous.

![](assets/any-optn-console-app.png)

Outre les deux critères ci-dessus, vous pouvez également utiliser la variable **Catégorie** en conjonction avec **Subsystem** ou **Any (préfixe)** pour rechercher explicitement **debug** ou **error** messages de niveau émis par le SDK AccessEnabler iOS/tvOS.

#### Exclusion

Afin de pouvoir mieux déboguer les fonctionnalités d’autres composants et **exclude** Les journaux de la structure AccessEnabler vous permettent :

* Recherche dans l’application Console à l’aide de **Subsystem** qui n’est pas égale à la valeur com.adobe.pass.AccessEnabler .
* Recherche dans l’application Console à l’aide de **Quelconque** qui ne contient pas l’option [AccessEnabler] .

## Signalement d’un problème

Lorsque vous signalez un problème à l’authentification Adobe Primetime, veuillez tenir compte des suggestions suivantes :

* veuillez essayer de fournir les étapes de reproduction.
* essayez de fournir la ou les versions du système d’exploitation et le ou les modèles de périphérique sur lesquels le problème se produit.
* essayez de fournir la version du SDK AccessEnabler iOS/tvOS qui rencontre le problème.
* essayez de capturer et de joindre tous les messages de journalisation du SDK AccessEnabler iOS/tvOS à l’aide de l’une des deux options présentées dans la section [Inclusion](#including) .
