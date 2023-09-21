---
title: Présentation des environnements Adobe
description: Présentation des environnements Adobe
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 0%

---

# Présentation des environnements Adobe {#understanding-the-adobe-environments}

>[!NOTE]
>
>Le contenu de cette page est fourni à titre d’information uniquement. L’utilisation de cette API nécessite une licence actuelle de Adobe. Aucune utilisation non autorisée n’est autorisée.

La documentation officielle décrivant les environnements d’Adobe est disponible. [Configuration de votre environnement et test dans Pre-Qual](/help/authentication/setting-up-your-environment-and-testing-in-prequal.md):

Les environnements d&#39;Adobe, résumés en quelques mots :

Adobe comporte deux environnements : **Préqualification** et **Version**.

* Dans l&#39;environnement de préqualification, nous préparons le nouveau build à sortir.

* La version actuelle repose sur l’environnement Version .

Chaque environnement comporte deux profils : **staging** et **production**.

* Le profil d’évaluation se connecte au serveur d’évaluation MVPD
* Le profil de production se connecte au profil de production des MVPD.

La raison d’avoir les deux profils est que, sur le profil d’évaluation, nous préparons de nouveaux partenaires à entrer en ligne, et ils aimeraient tester le système avec le prochain build (pré-qualification) ou avec la version (plus stable).

Si un partenaire souhaite tester la nouvelle version, quelques étapes supplémentaires doivent être effectuées. Voir [Configuration de votre environnement et test dans Pre-Qual](/help/authentication/setting-up-your-environment-and-testing-in-prequal.md).

En suivant les étapes ci-dessus, il est certain que la prochaine version sera testée dans l’environnement Pré-qualification .
