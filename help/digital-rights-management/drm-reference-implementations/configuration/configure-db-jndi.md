---
title: Configuration de la base de données du serveur de licences
description: Configuration de la base de données du serveur de licences
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---


# Configuration de la base de données du serveur de licences{#configure-the-license-server-database}

Pour configurer la base de données exemple en configurant le schéma de base de données et en renseignant la base de données avec des données d’exemple :

1. Montez la ligne de commande MySQL.

   **Sous Windows -** Cliquez   **[!UICONTROL Window's Start Menu]** >  **[!UICONTROL MySQL]** >  **[!UICONTROL MySQL Server 5.1]** >  **[!UICONTROL MySQL Command Line Client]**

   **Sous Linux, etc.** - Type  `MySQL`.

1. Exécutez le script SQL suivant :

   mysql> source &quot;`"[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\dbscript\createsampledb.sql" dbscript\createsampledb.sql`&quot;

   Ce script ajoute le compte utilisateur `dbuser`, établit une connexion via une application Web et crée un schéma de base de données.

   >[!NOTE]
   >
   >Assurez-vous qu’il n’y a pas de point-virgule ( `;`) à la fin du script.

1. Modifiez le script `PopulateSampleDB.sql` qui renseigne des données d’exemple dans les tableaux pour inclure des données à des fins de test.

   Ce script se trouve dans le dossier `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\dbscript\ dbscript\`.
1. Exécutez le script [!DNL PopulateSampleDB] pour renseigner les données comme vous l’avez fait à l’étape 2.

   >[!NOTE]
   >
   >La première fois que vous exécutez le script [!DNL CreateSampleDB.sql], l&#39;erreur suivante se produit :

   Vous pouvez ignorer cette erreur en toute sécurité. Elle se produit uniquement lors de la première exécution de ce script.

Vous devez configurer le pool de connexions de base de données (DBCP), qui utilise le pool de connexions de base de données Jakarta-Commons. Une base de données TestDB de source de données JNDI est configurée pour tirer parti de ce pool de connexions au serveur d’applications. Pour modifier la connexion de la base de données afin qu’elle pointe vers un serveur MySQL qui ne se trouve pas sur localhost, modifiez l’un des fichiers suivants :

* Le fichier [!DNL META-INF\context.xml], qui spécifie l’emplacement, le nom d’utilisateur et le mot de passe de la base de données du serveur de licences se trouvant dans le fichier [!DNL flashaccess.war].

* Le fichier `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl\WebContent/META-INF\context.xml`.

et recréer le fichier WAR en utilisant les fichiers mis à jour.

Pour modifier l&#39;un de ces paramètres, modifiez le fichier [!DNL context.xml] dans le répertoire [!DNL WebContent] et utilisez le script Ant pour recréer le fichier WAR. Pour régler la base de données, modifiez les paramètres de source de données JNDI dans ce fichier.

Si vous déboguez le projet d’implémentation des références dans Eclipse, ajoutez `$CATALINA_HOME\lib\tomcat-dbcp.jar` à votre configuration d’exécution/débogage.

>[!NOTE]
>
>Si vous exécutez le fichier [!DNL flashaccess.war] sur un serveur Tomcat 6.0 autonome, cette étape n’est pas requise.

