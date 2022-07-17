---
title: Opérations sur le compte IQ
description: Les opérations dans le compte IQ impliquent des actions pour effectuer des automatisations et des opérations en bloc sur les comptes d’abonnés et suivre leurs effets.
source-git-commit: e61cca77bad4f01de871e300dc99d7368c283f2a
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---


# Opérations {#operations-tab-next-steps}

Une fois que vous avez compris les schémas d’utilisation de vos abonnés et identifié le partage de mot de passe pour le segment sélectionné (à l’aide des rapports et analyses dans le compte IQ), vous pouvez prendre des mesures ciblées pour réduire le partage de mot de passe.

La fonctionnalité Opérations du compte IQ vous aide à gérer et à gérer efficacement le partage des informations d’identification par le biais de procédures ciblées appelées opérations. Il vous offre des options pour concevoir un objectif, personnaliser les actions ciblées (en fonction de l’objectif) pour un groupe spécifique de comptes d’abonnés et automatiser leur exécution pendant une durée ultérieure. Grâce à la fonctionnalité Opérations, vous pouvez non seulement créer et exécuter des opérations, mais également en mesurer l’impact. Ainsi, en évaluant les impacts, vous pouvez ajuster votre stratégie pour optimiser l’effet, que ce soit en convertissant les emprunteurs ou en atténuant le partage des informations d’identification.

Pour afficher **Opérations** page select **Opérations** option sous **Actions** dans le volet de navigation de gauche de l’application Account IQ. La page Opérations répertorie toutes les opérations qui existent déjà sur le système Account IQ, ainsi que leurs détails.

![](assets/operations-page.png)

*Figure : Liste et détails des opérations existantes dans le compte IQ*

Sur la page Opérations, vous pouvez :

* Afficher une liste des opérations déjà existantes dans le compte IQ

* Afficher les détails de l’opération, tels que :

   * État (planifié, en cours d’exécution, terminé, erreur ou arrêté)

   * progression (en pourcentage d&#39;achèvement)

   * audience cible (segment sur lequel exécuter l’opération)

   * planning (date de début et de fin de l’opération)

   * création et date de fin de l’opération

* [Créer une opération](/help/AccountIQ/operation-affecting-user-segment.md)

* [Affichage des rapports d’opération](#operation-reports)

<!--* Search from the list of operations using Search field

* Stop an operation.

* Create a duplicate operation.

* [Configure columns of Operations details page](#configure-columns)-->

## Affichage des rapports d’opération {#operation-reports}

Vous pouvez analyser les impacts d’une opération en consultant son rapport. Pour afficher le rapport d’une opération :

1. Sélectionnez le nom de l’opération sur la page Opérations principale.

   Le rapport s’affiche sous la forme d’un graphique à barres empilé.

   ![](assets/operation-impact-report.png)

   *Figure : Rapport des opérations pour visualiser les impacts des opérations*

   L’axe X trace la période d’évaluation et l’axe Y trace une variable pour évaluer l’impact du fonctionnement.

   Par exemple, dans l’image ci-dessus, la variable sur l’axe Y est le nombre de comptes. Le graphique vous permet de comparer le nombre de comptes qui se trouvent dans le segment des opérations par rapport au nombre de comptes qui se trouvent en dehors du segment des opérations à un moment donné (par exemple, la semaine 2 de la période d’évaluation des opérations). Par conséquent, vous pouvez analyser la manière dont le nombre de comptes varie au cours de la période d’évaluation dans le segment d’opération et en dehors du segment.

   Ainsi, si votre opération devait envoyer des emails d’avertissement à des comptes suspects, et que les comptes dans le segment des opérations étaient ceux avec une probabilité de partage supérieure à 90 et utilisant plus de 5 appareils pour diffuser du contenu, alors au début de la période d’évaluation, les comptes dans le segment sont plus de 7 millions. Ce nombre change au cours de la période d’évaluation, comme le montre le graphique, indiquant ainsi l’impact du fonctionnement. Sur la base de l’évaluation, vous pouvez prendre des mesures correctives concernant la suspension de comptes, ou poursuivre l’opération, ou ajuster votre stratégie pour de meilleurs résultats afin de limiter le partage des informations d’identification.

2. Pour fermer le rapport et revenir à la page Opérations principale, sélectionnez **Opérations** option sous **Actions** dans le volet de navigation de gauche.

<!--

![](assets/operations-details.png)

*Figure: Operation details*
## Configure columns {#configure-columns}

You can select the icon to **Configure columns** on the top of the operations table.

![](assets/config-columns.png)

*Figure: Configure columns of Operations details page*-->