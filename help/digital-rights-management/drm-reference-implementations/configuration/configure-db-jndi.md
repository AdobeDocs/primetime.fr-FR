---
title: Configuration de la base de données du serveur de licences
description: Configuration de la base de données du serveur de licences
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Configuration de la base de données du serveur de licences{#configure-the-license-server-database}

Pour configurer l’exemple de base de données en configurant le schéma de base de données et en renseignant la base avec des données d’exemple :

1. Permet d’afficher la ligne de commande MySQL.

   **Sous Windows -** Cliquez sur  **[!UICONTROL Window's Start Menu]** > **[!UICONTROL MySQL]** > **[!UICONTROL MySQL Server 5.1]** > **[!UICONTROL MySQL Command Line Client]**

   **Sous Linux, etc.** - Type `MySQL`.

1. Exécutez le script SQL suivant :

   mysql> source &quot; `"[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\dbscript\createsampledb.sql" dbscript\createsampledb.sql`&quot;

   Ce script ajoute le compte utilisateur `dbuser`, établit une connexion via une application web et crée un schéma de base de données.

   >[!NOTE]
   >
   >Assurez-vous qu’il n’y a pas de point-virgule ( `;`) à la fin du script.

1. Modifiez la variable `PopulateSampleDB.sql` qui renseigne des données d’exemple dans les tableaux afin d’inclure des données pour vos tests.

   Ce script se trouve dans la variable `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\dbscript\ dbscript\` dossier.
1. Exécutez le [!DNL PopulateSampleDB] pour renseigner les données comme vous l’avez fait à l’étape 2.

   >[!NOTE]
   >
   >La première fois que vous exécutez le [!DNL CreateSampleDB.sql] L’erreur suivante se produit dans le script :

   Vous pouvez ignorer cette erreur en toute sécurité. Cela ne se produit que la première fois que vous exécutez ce script.

Vous devez configurer le pool de connexions à la base de données (DBCP), qui utilise le pool de connexions à la base de données Jakarta-Commons. Une source de données JNDI TestDB est configurée pour tirer parti de ce pool de connexions au serveur d’applications. Pour modifier la connexion à la base de données afin qu’elle pointe vers un serveur MySQL qui ne se trouve pas sur localhost, modifiez l’un des fichiers suivants :

* La variable [!DNL META-INF\context.xml] qui spécifie l’emplacement, le nom d’utilisateur et le mot de passe de la base de données du serveur de licences qui se trouve dans le fichier [!DNL flashaccess.war] fichier .

* La variable `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl\WebContent/META-INF\context.xml` fichier .

et recréez le fichier WAR à l’aide des fichiers mis à jour.

Pour modifier l’un de ces paramètres, modifiez la variable [!DNL context.xml] dans le fichier [!DNL WebContent] et utilisez le script Ant pour recréer le fichier WAR. Pour régler la base de données, modifiez les paramètres de source de données JNDI dans ce fichier.

Si vous déboguez le projet d’implémentation de référence dans Eclipse, ajoutez `$CATALINA_HOME\lib\tomcat-dbcp.jar` à votre configuration d’exécution/de débogage.

>[!NOTE]
>
>Si vous exécutez le [!DNL flashaccess.war] sur un serveur Tomcat 6.0 autonome, cette étape n’est pas requise.
