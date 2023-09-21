---
description: Le serveur de mise en oeuvre de référence peut vous aider à créer un serveur de licences entièrement fonctionnel qui utilise toutes les fonctionnalités du SDK Java DRM d’Adobe Primetime.
title: Serveur de licences
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Serveur de licences {#license-server}

Le serveur de mise en oeuvre de référence peut vous aider à créer un serveur de licences entièrement fonctionnel qui utilise toutes les fonctionnalités du SDK Java DRM d’Adobe Primetime.

Dans cette implémentation, les utilisateurs sont authentifiés en fonction des entrées d’utilisateurs dans une base de données. Le serveur comprend une logique commerciale de démonstration pour l’octroi de licences et fournit une prise en charge de compatibilité pour les serveurs Flash Media Rights Management 1.0 et 1.5.

## Exigences du serveur de licences {#license-server-requirements}

Exigences du serveur de licences :

* Installation de Tomcat 6.0 ou version ultérieure
* Installez une base de données, par exemple MySQL (disponible sur le DVD, dans [!DNL Third Party\MySQL])
* Vérifiez que Java 1.6 ou version ultérieure est installé.
* Pour exécuter les exemples de scripts de génération, vérifiez que vous disposez d’Ant 1.8 ou d’une version ultérieure.

Après avoir installé Tomcat et MySQL, contactez l’Adobe de votre jeu d’informations d’identification DRM requises.

## Création du serveur de licences {#build-the-license-server}

>[!NOTE]
>
>La création du serveur de licences n’est nécessaire que si vous avez l’intention de modifier le code source. À des fins d’évaluation, vous pouvez simplement utiliser les fichiers WAR tels qu’expédiés.

Le serveur de licence de mise en oeuvre de référence comprend tout le code source du serveur de licences ( `([DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\src/`), avec un script de génération Ant ( `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl/build-refimpl.xml`) avec lequel vous pouvez personnaliser le serveur de licences en fonction des besoins de votre entreprise.

1. Modifiez le script de génération Ant pour spécifier les emplacements de vos SDK DRM Primetime, Tomcat, MySQL et Log4J.

   Ouvrez le [!DNL build-refimpl.xml] dans un éditeur de texte, puis définissez les valeurs de propriété suivantes :

   * `sdkdir`
   * `tomcatdir`
   * `mysqldir`
   * `log4jdir`

1. Exécutez le script de création Ant avec la méthode `all` , dans le répertoire où se trouve le script de génération Ant.

   ```
   ant -f build-refimpl.xml all
   ```

   Le script de génération Ant crée une [!DNL refimpl-build/wars] qui comprend les fichiers WAR du serveur.
