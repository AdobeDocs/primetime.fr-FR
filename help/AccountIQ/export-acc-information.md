---
title: Exporter des informations pour les comptes avec un score de partage élevé
description: Exportez des informations pour les comptes ayant un score de partage élevé.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 1%

---

# Exporter des informations pour les comptes avec un score de partage élevé {#export-account-info-high-score}

Account IQ vous offre la possibilité d’exporter les détails de partage de compte pour les 1 000 premiers comptes abonnés en fonction de leurs [probabilités de partage](/help/AccountIQ/product-concepts.md#account-sharing-probability-def). Les données du fichier CSV exporté sont triées dans l’ordre décroissant des probabilités de partage des comptes d’abonnés, des MVPD sélectionnés dans la variable [segment](/help/AccountIQ/product-concepts.md#segment-def), pour un [période spécifiée](/help/AccountIQ/product-concepts.md#time-frame-def).

L’option permettant d’exporter les informations de partage de compte est disponible sur [Rapports d’utilisation générale](/help/AccountIQ/general-usage-reports.md) et [Rapports sur les comptes partagés](/help/AccountIQ/shared-acc-reports.md) pages.

>[!NOTE]
>
>Les chiffres du fichier CSV téléchargé sont différents pour les pages de rapports Utilisation générale et Comptes partagés . En effet, la page Rapports d’utilisation généraux comporte des filtres supplémentaires permettant aux programmeurs de sélectionner Seuil pour le nombre d’appareils, d’adresses IP et de codes postaux. Les données exportées à partir des rapports d’utilisation générale sont donc basées sur le filtre de seuil supplémentaire appliqué.

![Option d’exportation dans Utilisation générale](assets/export.png)

Pour exporter les informations de partage de compte des abonnés :

1. Définissez un segment de votre choix en suivant les étapes de la section [Comment définir un segment et sélectionner une période](/help/AccountIQ/howto-select-segment-timeframe.md) pour l’évaluation à partir de [segment et période](/help/AccountIQ/segments-timeframe.md) du panneau.

1. Sélectionnez la variable **Exporter les 1 000 premiers comptes** pour exporter les informations du compte de 1 000 abonnés avec la probabilité de partage la plus élevée.

Lorsque vous utilisez l’option d’exportation, les statistiques de 1 000 comptes présentant les plus fortes probabilités de partage (pour une période définie) sont téléchargées dans le dossier Téléchargements de votre ordinateur local.

>[!NOTE]
>
>Le fichier CSV téléchargé peut être ouvert à l’aide de toute application qui lit un fichier CSV, par exemple Microsoft Excel.

![données exportées au format csv](assets/exported-csv.png)

*Figure : Exportation des données de compte partagé au format CSV*

## Colonnes du rapport exporté {#columns-in-export}

**Semaine/Mois**

La semaine ou le mois que vous avez sélectionné sur la page **Granularité et période** dans le sélecteur de segments, pour lequel les statistiques de partage sont recherchées.

**MVPD**

Si vous êtes un utilisateur programmeur, la colonne indique à quel MVPD appartient le compte abonné.

**ID d’abonné**

Compte spécifique dont nous parlons d&#39;affilée.

**Nombre minimal d’appareils**

Le nombre réel d’appareils (ce contenu de diffusion en continu) est presque certainement supérieur au nombre minimal d’appareils spécifié pour un compte particulier.

>[!NOTE]
>
>Le nombre réel d’appareils (ce contenu de diffusion en continu) est certainement supérieur au nombre minimum d’appareils spécifié pour un compte particulier.

**Nombre minimum de personnes**

Nombre minimum absolu de personnes qui étaient actives dans le contenu en continu à l’aide de ces appareils.

>[!NOTE]
>
>Le nombre réel de personnes (le contenu de ce flux) est presque certainement beaucoup plus élevé que le Nombre minimum de personnes, défini pour un compte particulier.

**# IP**

Nombre d’adresses IP à partir desquelles le contenu est diffusé en continu.

**# Emplacements**

Nombre d’emplacements (en fonction du code postal) à partir desquels le contenu est diffusé en continu.

**# Villes**

Nombre de villes où la diffusion en continu a eu lieu.

**Nombre d’états**

Nombre d’états où la diffusion en continu a eu lieu.

**# Clusters**

Le nombre de variables distinctes [grappes](/help/AccountIQ/product-concepts.md#cluster-def) où la diffusion en continu a eu lieu.

**span géographique (miles)**

Distance maximale entre les emplacements de diffusion en continu associés au compte.

**# AuthN OK**

Nombre de fois où les utilisateurs se sont connectés au cours de la période, à l’aide de ce compte.

**# AuthZ OK**

Nombre de fois où un MVPD a autorisé un flux, ou accordé l’accès (au contenu), à ce compte.

>[!NOTE]
>
>La variable **# AuthZ OK** est lié à la variable **# Lecture de requêtes**; il est plus petit que le **# Lecture de requêtes** car Adobe met en cache les autorisations qui sont envoyées pour les distributeurs multicanaux de programmes audiovisuels pendant 24 heures.

**# Lecture de requêtes**

Le nombre réel de diffusions pendant la période.

**# Canaux**

Nombre total de canaux différents que le compte a visionnés au cours de la période.

>[!NOTE]
>
>**# Canaux** inclut les canaux qui n’appartenaient pas nécessairement au programmeur connecté.
>
>Ce numéro du compte s’affichait, car le compte avait visionné votre canal, mais il avait également accédé à d’autres canaux pendant cette période.

**Modèle d’utilisation**

Les nombres de cette colonne sont des identifiants qui correspondent à l’un des 14 modèles que nous identifions comme tous les comptes d’utilisateurs.

*Tableau : Identifiants des modèles d’utilisation dans le mappage CSV exporté avec les modèles d’utilisation*

| ID | 1 | 2 | 3 | 4 | 5 et 8 | 6 | 7 | 9 | 10 et 11 | 12 | 13 | 14 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Modèles d’utilisation | Utilisateur régulier | Voyageur ou navetteur | Grande famille | Famille proche et amis | Partage de groupes sociaux | Grand groupe d&#39;amis | Diffusion en continu simultanée | Partage de communautés | Comportement incertain | Petite famille | Second home | Utilisation anormale |

{style="table-layout:auto"}

**Probabilité de partage**

La probabilité de partage est la probabilité que le compte spécifique partage ses informations d’identification.

>[!NOTE]
>
> La moyenne de la probabilité de partage de tous les comptes (dans le segment sélectionné) est utilisée pour calculer la valeur [niveau de partage](/help/AccountIQ/dashboard.md#sharing-level) de [Score de partage agrégé](/help/AccountIQ/dashboard.md#aggregated-sharing).
