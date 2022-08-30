---
title: Tableau de bord du compte IQ
description: Le tableau de bord permet d’identifier les instances de partage de mot de passe en analysant un large éventail de données d’abonnés.
exl-id: 616da2a5-c9fe-40ea-90cf-f565bc13e764
source-git-commit: 5b34fbe26078ae761d61179975366505c5628c9c
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---

# Le tableau de bord {#dashboard}

Le tableau de bord résume et agrège les données dans une collection de graphiques et de rapports, conçue pour donner un aperçu général de la portée et de l’impact du partage de compte. Il fournit une page unique contenant les principaux rapports et mesures du compte IQ.

![Tableau de bord du compte IQ](assets/dashboard-capture.png)


*Figure : Le tableau de bord*

## Score de partage moyen - agrégé pour le segment actuel {#aggregated-sharing}

Le panneau Score de partage agrégé fournit un résumé de première ligne résumant la quantité et l’impact du partage en termes de comptes et de volume de diffusion.

Les valeurs vous aident à comprendre l’ampleur du partage des informations d’identification par vos abonnés, ce qui vous permet de mesurer la nécessité d’agir sur celle-ci.

![](assets/aggregate-sharing-score.png)


*Figure : Panneau Note de partage moyenne - agrégé pour le segment actuel*

Les trois mesures suivantes sont des composants de la note de partage moyenne.

### Niveau de partage {#sharing-level}

La jauge du niveau de partage indique le pourcentage de tous vos comptes d’abonnés (dans le segment défini) qui sont partagés, pendant la période sélectionnée.

Une valeur calculée à partir d’une moyenne de la probabilité de partage calculée pour chaque compte dans l’ensemble des distributeurs multicanaux sélectionnés qui a diffusé en continu depuis l’un des canaux de programmeurs sélectionnés pendant la période sélectionnée.

![](assets/sharing-level.png)


*Figure : Niveau de partage*

L’indicateur de tendance affiche le pourcentage de changement de la valeur de la mesure dans par rapport à la période précédente.

### Utilisation de comptes partagés {#usage-from-shared-accounts}

Cette jauge indique le pourcentage d’utilisation de tous les comptes d’abonnés provenant des comptes partagés pour le segment défini et la période. La jauge marque les plages d’utilisation (des comptes partagés) sur l’échelle de 0 à 100 %. Ces plages (nommées Faible, Moyen, Élevé et Abnormal) sont basées sur la moyenne du secteur.

Vous pouvez également voir l’indicateur de tendance, qui illustre une augmentation ou une baisse de l’utilisation des comptes partagés par rapport à la période précédente.

![](assets/usage-4mshared-accounts.png)


*Figure : Utilisation de comptes partagés*

### Score de partage global {#overall-sharing-score}

Le score de partage global est un composite des scores de partage, y compris &quot;Niveau de partage&quot; et &quot;Utilisation z des comptes partagés&quot;.

Il fournit une valeur destinée à refléter l’impact relatif du partage par rapport à l’industrie. Son objectif est similaire à celui d’un score de crédit, résumant la situation par un seul chiffre. Mais dans ce cas, plus le nombre est élevé, plus le danger potentiel est grand.

![](assets/overall-sharing-score.png)


*Figure : Score de partage global*

<!--### MVPDs in segment {#mvpd-in-segment}

It is a table of risk indices and accounts totals for the top MVPDs ranked by overall usage or account sharing.

![](assets/mvpds-in-segment.png)-->

### Scores de partage globaux à l’échelle du secteur pour les distributeurs multicanaux de programmes audiovisuels {#top-mvpds}

Ce tableau fournit une vue comparative des différents scores de partage agrégés pour les MVPD dans le segment.

>[!NOTE]
>
>Ce tableau utilise les données globales de l’industrie à des fins de comparaison, et non les données représentées par ces distributeurs multicanaux dans le segment.

![](assets/top-mvpds.png)


*Figure : Meilleurs MVPD dans le segment par score global*

### Score de partage par canaux et MVPD {#sharin-score-by-channels-and-mvpds}

Ce tableau fournit une vue comparative du partage des scores des canaux sélectionnés pour les MVPD dans le segment actuel.

![](assets/sharing-scores-by-channels-mvpds.png)


*Figure : Partage de scores par canaux et MVPD*

### Probabilité de partage des comptes {#accounts-sharing-probability}

Ce graphique partitionne les comptes en plages de quintiles de probabilité de partage allant de très bas (0-20 %) à très élevés (80=100 %).

>[!NOTE]
>
>Le graphique à barres utilise une échelle logarithmique.


![](assets/dashboard-ac-sharing-prob.png)


*Figure : Nombres et pourcentages de comptes abonnés dans différentes plages de probabilités de partage*

### Nombre de comptes et d’utilisations en partageant le niveau de probabilité {#number-of-accounts-usage-sharing-probability}

Ce panneau fournit une vue tabulaire des comptes partitionnés en plages de quintiles de probabilité de partage allant de très bas (0 à 20 %) à très élevé (80 à 100 %) avec l’utilisation associée de chaque quintile à partir de comptes partagés.

![](assets/no-acc-usage-prob-level.png)


*Figure : Nombre de comptes, de tendances et d’utilisations appartenant à différentes périodes de probabilité*



<!--
+++Dashboard for programmers

![dashboard of account IQ](assets/dashboard-capture.png)


*Figure: The dashboard*

## Average sharing score - aggregated for the current segment {#aggregated-sharing}

The Aggregated Sharing Score panel provides a top line readout summarizing the quantity and impact of sharing in terms of accounts and streaming volume.

The values help you understand the magnitude of credential sharing by your subscribers, hence providing a measure of the need to act upon it.

![](assets/aggregate-sharing-score.png)


*Figure: Average sharing score panel - aggregated for the current segment*

The following three metrics are components of the Average Sharing Score.

### Sharing level {#sharing-level}

The sharing level gauge shows the percentage of all your subscriber accounts (in the defined segment) that are shared, during the selected time frame.  

A value calculated based on an average of the sharing probability computed for every account in the set of selected MVPDs that has streamed from a one of the selected programmer channels during the selected time frame.

![](assets/sharing-level.png)


*Figure: Sharing level*

The Trend indicator shows the percentage change in the value of the metric in from the previous time frame.

### Usage from shared accounts {#usage-from-shared-accounts}

This gauge indicates what percent of the usage of all the subscriber accounts is from the shared accounts for the defined segment and time period. The gauge marks the ranges of usage (from shared accounts) on the scale of 0 to 100%. These ranges—named Low, Medium, High, and Abnormal—are based on the industry average.

You can also see the Trend indicator, which depicts a rise or fall in the usage from shared accounts as compared to the previous time frame.

![](assets/usage-4mshared-accounts.png)


*Figure: Usage from shared accounts*

### Overall sharing score {#overall-sharing-score}

Overall sharing score is composite of sharing scores including “Sharing level” and “z Usage from shared accounts”.

It provides a value meant to reflect the relative impact of sharing when compared to the industry. It’s purpose is similar to that of a credit score, summarizing the situation with a single number. But in this case, the higher the number the greater the potential harm.

![](assets/overall-sharing-score.png)


*Figure: Overall sharing score*

<!--### MVPDs in segment {#mvpd-in-segment}

It is a table of risk indices and accounts totals for the top MVPDs ranked by overall usage or account sharing.

![](assets/mvpds-in-segment.png)

### Industrywide overall sharing scores for MVPDs {#top-mvpds}

This table provides a comparative view of the different Aggregated Sharing Scores for the MVPDs in the segment.

>[!NOTE]
>
>This table uses overall industry data for comparative purposes, not the data represented by those MVPDs in the segment.

![](assets/top-mvpds.png)


*Figure: Top MVPDs in segment by overall score*

### Sharing score by channels and MVPDs {#sharin-score-by-channels-and-mvpds}

This table provides a comparative view of sharing scores of the selected channels for the MVPDs in the current segment.

![](assets/sharing-scores-by-channels-mvpds.png)


*Figure: Sharing scores by channels and MVPDs*

### Accounts sharing probability {#accounts-sharing-probability}

This chart partitions accounts into ranges of sharing probability quintiles from very low (0-20%) to very high (80=100%).

>[!NOTE]
>
>The bar graph uses a logarithmic scale.


![](assets/dashboard-ac-sharing-prob.png)


*Figure: Numbers and percentages of subscriber accounts in different sharing probability ranges*

### Number of accounts and usage by sharing probability level {#number-of-accounts-usage-sharing-probability}

This panel provides tabular view of  accounts partitioned into ranges of sharing probability quintiles from very low (0-20%) to very high (80-100%) with each quintile’s associated usage from shared accounts.

![](assets/no-acc-usage-prob-level.png)


*Figure: Number of accounts, trends, and usages falling in various probability ranges*

+++


+++Dashboard for MVPDs
The dashboard for MVPD users is slightly different from those of the programmer users.

![](assets/dashboard-mvpd.png)


*Figure: MVPD's Dashboard*

## Top programmers in segment by overall sharing score {#}

![](assets/top-programmers-panel.png)


*Figure: Panel showing top programmers in a segment*
+++


+++Dashboard for MVPDs
The dashboard for MVPD users is slightly different from those of the programmer users.

![](assets/dashboard-mvpd.png)


*Figure: MVPD's Dashboard*

## Top programmers in segment by overall sharing score {#}


![](assets/top-programmers-panel.png)


*Figure: Panel showing top programmers in a segment*
+++
-->