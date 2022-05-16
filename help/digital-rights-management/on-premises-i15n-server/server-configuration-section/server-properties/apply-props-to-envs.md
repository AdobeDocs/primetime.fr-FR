---
description: 'Vous devez configurer les propriétés du serveur pour qu’elles reflètent votre environnement. Pour ce faire, utilisez l’une des méthodes suivantes : '
title: Application des propriétés aux environnements de serveur
exl-id: 0c78011a-e8c8-43a8-8c2d-a5c4ed54a8d7
source-git-commit: 0019a95fa9ca6d21249533d559ce844897ab67cf
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# Application des propriétés aux environnements de serveur{#apply-properties-to-server-environments}

Vous devez configurer les propriétés du serveur pour qu’elles reflètent votre environnement. Pour ce faire, utilisez l’une des méthodes suivantes :

* [!DNL flashaccess-i15n.properties] - Exemples inclus dans chacun des [!DNL .war] files

* [!DNL AdobeInitial.properties] - Exemple situé dans le [!DNL /shared] dossier sur le DVD

   Vous pouvez utiliser ce fichier pour remplacer les propriétés définies dans le fichier WAR comme suit :

   1. Définissez les valeurs de propriété de remplacement dans [!DNL AdobeInitial.properties]
   1. Placer [!DNL AdobeInitial.properties] sur le chemin d’accès aux classes.

   >[!NOTE]
   >
   >Adobe vous recommande d’utiliser la variable [!DNL AdobeInitial.properties] , car cela vous permet de mettre à jour vos fichiers WAR d’application sans risquer de perdre toute configuration de propriété précédente que vous avez effectuée dans la variable [!DNL flashaccess-i15n.properties] fichier .

* Mécanisme des propriétés système Java.

Vous pouvez appliquer des propriétés individuelles à ces environnements de serveur spécifiques :

* *Développement*
* *Évaluation*
* *Production*

Grâce à cette fonctionnalité, vous pouvez utiliser le même fichier WAR pour tous les environnements de serveur. Pour appliquer des propriétés à des environnements spécifiques, ajoutez deux caractères de soulignement (&#39; `__`&quot;) plus l’un des codes d’environnement suivants à la propriété *name*:

* `DEV`
* `STAGE`
* `PROD`

<!--<a id="example_A7A58E3EE8DA4114B4F7A9EEB69D50CA"></a>-->

Par exemple, pour définir le niveau de journal sur `INFO` pour vos serveurs de production et d’évaluation, et à `DEBUG` pour votre serveur de développement :

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
>Vous devez spécifier le nom d’environnement du serveur en tant que propriété système Java lors du démarrage du serveur. Par exemple, lors du démarrage de Tomcat avec [!DNL catalina.bat], définissez la variable `CATALINA_OPTS` Variable d’environnement comme suit :
>-DENVIRONMENT_NAME=[ DEV | ÉTAPE | PROD ]
