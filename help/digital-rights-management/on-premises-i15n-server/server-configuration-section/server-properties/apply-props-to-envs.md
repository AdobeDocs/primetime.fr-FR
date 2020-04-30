---
description: 'Vous devez configurer les propriétés du serveur pour refléter votre environnement. Pour ce faire, utilisez l’une des méthodes suivantes : '
seo-description: 'Vous devez configurer les propriétés du serveur pour refléter votre environnement. Pour ce faire, utilisez l’une des méthodes suivantes : '
seo-title: Appliquer les propriétés aux environnements de serveur
title: Appliquer les propriétés aux environnements de serveur
uuid: a1ee0d6c-b5e7-4689-b7c8-b155176faf1c
translation-type: tm+mt
source-git-commit: d8e4c39c297d69b154baf0b4d67cf09b5cf0a9d4

---


# Appliquer les propriétés aux environnements de serveur{#apply-properties-to-server-environments}

Vous devez configurer les propriétés du serveur pour refléter votre environnement. Pour ce faire, utilisez l’une des méthodes suivantes :

* [!DNL flashaccess-i15n.properties] - Exemples inclus dans chacun des [!DNL .war] fichiers

* [!DNL AdobeInitial.properties] - Exemple situé dans le [!DNL /shared] dossier du DVD

   Vous pouvez utiliser ce fichier pour remplacer les propriétés définies dans le fichier WAR comme suit :

   1. Définissez les valeurs de propriété de remplacement dans [!DNL AdobeInitial.properties]
   1. Placez [!DNL AdobeInitial.properties] le chemin de classe.
   >[!NOTE]
   >
   >Adobe vous recommande d’utiliser le [!DNL AdobeInitial.properties] fichier, car cela vous permet de mettre à jour vos fichiers WAR d’application sans risquer de perdre toute configuration de propriété antérieure que vous avez peut-être effectuée dans le [!DNL flashaccess-i15n.properties] fichier.

* Mécanisme de propriétés Java System.

Vous pouvez appliquer des propriétés individuelles à ces environnements de serveur spécifiques :

* *Développement*
* *Évaluation*
* *Production*

Grâce à cette fonctionnalité, vous pouvez utiliser le même fichier WAR pour tous les environnements de serveur. Pour appliquer des propriétés à des environnements spécifiques, ajoutez deux caractères de soulignement (&#39; `__`&#39;) plus l’un des codes d’environnement suivants au *nom* de la propriété :

    * `DEV`
    * `STAGE`
    * `PROD`

<!--<a id="example_A7A58E3EE8DA4114B4F7A9EEB69D50CA"></a>-->

Par exemple, pour définir le niveau de journal sur `INFO` pour vos serveurs de production et d’évaluation et sur `DEBUG` pour votre serveur de développement :

```
log.Level=INFO  
log.Level__DEV=DEBUG 
```

Le serveur utilise cet ordre de recherche pour les propriétés :

1. `propertyname_environment` in [!DNL AdobeInitial.properties]

1. `propertyname_environment` in [!DNL flashaccess-15n.properties]

1. `propertyname_environment` dans les propriétés système Java
1. `propertyname` in [!DNL AdobeInitial.properties]

1. `propertyname` in [!DNL flashaccess-15n.properties]

1. `propertyname` dans les propriétés système Java

>[!NOTE]
>
>Vous devez spécifier le nom de l’environnement du serveur en tant que propriété système Java lors du démarrage du serveur. Par exemple, lorsque vous démarrez Tomcat avec [!DNL catalina.bat], définissez la variable `CATALINA_OPTS` environnement comme suit :
>-DENVIRONMENT_NAME=[ DEV | ETAPE | PROD ]
