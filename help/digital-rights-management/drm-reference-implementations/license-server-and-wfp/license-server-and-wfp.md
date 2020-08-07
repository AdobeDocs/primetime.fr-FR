---
description: Le serveur d’implémentation de référence peut vous aider à créer un serveur de licences entièrement fonctionnel qui utilise toutes les fonctionnalités du SDK Java DRM Adobe Primetime.
seo-description: Le serveur d’implémentation de référence peut vous aider à créer un serveur de licences entièrement fonctionnel qui utilise toutes les fonctionnalités du SDK Java DRM Adobe Primetime.
seo-title: Serveur de licences
title: Serveur de licences
uuid: 39cb0d0f-f3dc-48e9-b6fd-6960a9ade291
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---


# Serveur de licences {#license-server}

Le serveur d’implémentation de référence peut vous aider à créer un serveur de licences entièrement fonctionnel qui utilise toutes les fonctionnalités du SDK Java DRM Adobe Primetime.

Dans cette implémentation, les utilisateurs sont authentifiés en fonction des entrées d’utilisateur dans une base de données. Le serveur comprend une logique commerciale de démonstration pour l’octroi de licences et fournit une prise en charge de compatibilité pour Flash Media Rights Management Server 1.0 et 1.5.

## Exigences du serveur de licences {#license-server-requirements}

Exigences du serveur de licences :

* Installation de Tomcat 6.0 ou version ultérieure
* Installez une base de données, par exemple MySQL (disponible sur le DVD, dans [!DNL Third Party\MySQL]).
* Vérifiez que Java 1.6 ou version ultérieure est installé
* Pour exécuter les exemples de scripts de génération, assurez-vous d’avoir Ant 1.8 ou version ultérieure.

Après avoir installé Tomcat et MySQL, contactez l’Adobe pour obtenir les informations d’identification DRM requises.

## Création du serveur de licences {#build-the-license-server}

>[!NOTE]
>
>La création du serveur de licences n’est nécessaire que si vous avez l’intention de modifier le code source. À des fins d&#39;évaluation, vous pouvez simplement utiliser les fichiers WAR tels qu&#39;expédiés.

Le serveur de licences d’implémentation de référence comprend l’ensemble du code source du serveur de licences ( `([DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\src/`), ainsi qu’un script de version Ant ( `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl/build-refimpl.xml`) avec lequel vous pouvez personnaliser le serveur de licences en fonction de vos besoins professionnels.

1. Modifiez le script de génération Ant pour spécifier les emplacements de votre SDK DRM Primetime, Tomcat, MySQL et Log4J.

   Ouvrez le [!DNL build-refimpl.xml] fichier dans un éditeur de texte et définissez les valeurs de propriété suivantes :

   * `sdkdir`
   * `tomcatdir`
   * `mysqldir`
   * `log4jdir`

1. Exécutez le script de génération Ant avec la `all` propriété, dans le répertoire où se trouve le script de génération Ant.

   ```
   ant -f build-refimpl.xml all
   ```

   Le script de génération Ant crée un [!DNL refimpl-build/wars] répertoire qui inclut les fichiers WAR du serveur.
