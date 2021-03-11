---
description: 'Vous devez configurer les propriétés du serveur pour refléter votre environnement. Pour ce faire, utilisez l’une des méthodes suivantes : '
title: Appliquer les propriétés aux environnements de serveur
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---


# Appliquer les propriétés aux environnements de serveur{#apply-properties-to-server-environments}

Vous devez configurer les propriétés du serveur pour refléter votre environnement. Pour ce faire, utilisez l’une des méthodes suivantes :

* [!DNL flashaccess-i15n.properties] - Exemples inclus dans chacun des  [!DNL .war] fichiers

* [!DNL AdobeInitial.properties] - Exemple situé dans le  [!DNL /shared] dossier du DVD

   Vous pouvez utiliser ce fichier pour remplacer les propriétés définies dans le fichier WAR comme suit :

   1. Définissez les valeurs de propriété de remplacement dans [!DNL AdobeInitial.properties]
   1. Placez [!DNL AdobeInitial.properties] sur le chemin de classe.

   >[!NOTE]
   >
   >L&#39;Adobe vous recommande d&#39;utiliser le fichier [!DNL AdobeInitial.properties], car cela vous permet de mettre à jour vos fichiers WAR d&#39;application sans risquer de perdre la configuration de propriété précédente que vous avez peut-être effectuée dans le fichier [!DNL flashaccess-i15n.properties].

* Mécanisme de propriétés Java System.

Vous pouvez appliquer des propriétés individuelles à ces environnements de serveur spécifiques :

* *Développement*
* *Évaluation*
* *Production*

Grâce à cette fonctionnalité, vous pouvez utiliser le même fichier WAR pour tous les environnements de serveur. Pour appliquer des propriétés à des environnements spécifiques, ajoutez deux caractères de soulignement (&#39; `__`&#39;) plus l&#39;un des codes d&#39;environnement suivants à la propriété *name* :

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

1. `propertyname_environment` in  [!DNL AdobeInitial.properties]

1. `propertyname_environment` in  [!DNL flashaccess-15n.properties]

1. `propertyname_environment` dans les propriétés système Java
1. `propertyname` in  [!DNL AdobeInitial.properties]

1. `propertyname` in  [!DNL flashaccess-15n.properties]

1. `propertyname` dans les propriétés système Java

>[!NOTE]
>
>Vous devez spécifier le nom de l’environnement du serveur en tant que propriété système Java lors du démarrage du serveur. Par exemple, lorsque vous démarrez Tomcat avec [!DNL catalina.bat], définissez la variable d’environnement `CATALINA_OPTS` comme suit :
>-DENVIRONMENT_NAME=[ DEV | ETAPE | PROD ]
