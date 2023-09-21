---
title: Configuration de la base de données et configuration de la source de données JNDI
description: Configuration de la base de données et configuration de la source de données JNDI
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---

# Configuration de la base de données et configuration de la source de données JNDI {#setting-up-the-database-and-configuring-the-jndi-datasource}

Le serveur de licence de mise en oeuvre de référence requiert une base de données pour prendre en charge les fonctionnalités suivantes :

* Authentification de l’utilisateur
* Règles de fonctionnement de démonstration du modèle d’utilisation
* Conversion des métadonnées
* Prise en charge des domaines

L’acquisition de licences anonymes ne nécessite pas l’exécution d’une base de données.

>[!NOTE]
>
>Les instructions de cette section concernent la plateforme Windows Microsoft. Pour les autres systèmes d’exploitation, consultez la documentation de votre système d’exploitation ou la documentation de MySQL.

Pour exécuter le serveur de licences, vous devez installer et configurer MySQL 5.1.34 :

1. Exécutez le programme d’installation MySQL (situé dans le dossier Troisième Party\MySQL\Installer\5.1 du DVD).
1. A la fin de la procédure d&#39;installation, vérifiez **[!UICONTROL Configure MySQL Server Now]** pour lancer l&#39;assistant de configuration. Utilisez les paramètres par défaut ou sélectionnez des paramètres spécifiques à des fins de test, à l’exception que vous devez sélectionner sur le 5e écran. **[!UICONTROL Online Transaction Processing (OLTP)]** ou **[!UICONTROL Manual Setting]** et saisissez le nombre maximal de connexions autorisées.

1. Notez le mot de passe racine.
1. Si vous devez réinstaller MySQL, procédez comme suit pour éviter tout problème lors du démarrage ultérieur du serveur :

   * Supprimer le dossier *lecteur système :* [!DNL \Documents and Settings\All Users\Application Data\MySQL].

   * Supprimez l’ancien dossier d’installation de MySQL : par exemple, *lecteur système :* [!DNL \Program Files\MySQL\MySQL Server 5.1].

Ensuite, vous devrez installer MySQL JDBC Driver 5.1.7. Pour ce faire, copiez [!DNL mysql-connector-java-5.1.7-bin.jar] (dans la variable [!DNL Third Party\MySQL\Installer\5.1] dossier sur le DVD) vers le répertoire lib du serveur Tomcat : [!DNL ...\Tomcat6.0\lib].

>[!NOTE]
>
>MySQL JDBC Driver 5.1.7 fonctionne avec Tomcat 6.0. Les versions plus anciennes de Tomcat ne sont pas prises en charge.

Configurez la base de données d’exemple en configurant le schéma de la base de données et en la remplissant avec des données d’exemple. Pour ce faire, procédez comme suit :

1. Accédez à  **[!UICONTROL Window's Start Menu]** > **[!UICONTROL MySQL]** > **[!UICONTROL MySQL Server 5.1]** > **[!UICONTROL MySQL Command Line Client]** .
1. Après avoir saisi le mot de passe, exécutez le script SQL suivant pour ajouter le compte d’utilisateur. `dbuser` pour établir une connexion par le biais d’une application web et créer un schéma de base de données (assurez-vous qu’il n’y a pas &quot;;&quot; à la fin. Appuyez simplement sur Entrée :

   ```
       mysql> source “Reference Implementation\Server\dbscript\createsampledb.sql”
   ```

1. Modifiez le script qui renseigne les exemples de données dans les tableaux afin d’inclure les données à des fins de test : [!DNL Reference Implementation\Server\dbscript\PopulateSampleDB.sql].
1. Exécutez ce script pour renseigner les données comme vous l’avez fait à l’étape 2.

>[!NOTE]
>
>La première fois que vous exécutez le [!DNL CreateSampleDB.sql] vous recevrez l’erreur suivante :

*ERREUR 1396 (HY000) : L’opération DROP USER a échoué pour la requête &#39;dbuser&#39;@&#39;localhost&#39; OK, 0 ligne affectée (0,00 seconde).*

Vous pouvez ignorer cette erreur en toute sécurité. Cela ne se produit que la première fois que vous exécutez ce script.

À ce stade, vous devez configurer le pool de connexions à la base de données (DBCP). DBCP utilise le pool de connexion à la base de données Jakarta-Commons. Une source de données JNDI TestDB est configurée pour tirer parti de ce pool de connexions au serveur d’applications. Pour modifier la connexion de la base de données afin qu’elle pointe vers un serveur MySQL qui ne se trouve pas sur localhost, modifiez la variable [!DNL META-INF\context.xml] (qui spécifie l’emplacement, le nom d’utilisateur et le mot de passe de la base de données du serveur de licences) situé dans [!DNL flashaccess.war]ou modifier [!DNL \Reference Implementation\Server\refimpl\WebContent\META-INF\context.xml] et recréez le fichier WAR à l’aide des fichiers mis à jour. Pour modifier l’un de ces paramètres, modifiez la variable [!DNL context.xml] situé dans le répertoire WebContent et utilisez le script Ant pour recréer le fichier WAR. Pour régler la base de données, modifiez les paramètres de source de données JNDI dans ce fichier.

Si vous déboguez le projet d’implémentation de référence dans Eclipse, vous devez ajouter `$CATALINA_HOME\lib\tomcat-dbcp.jar` à votre configuration d’exécution/de débogage. Cette étape n’est pas requise si vous exécutez la [!DNL flashaccess.war] sur un serveur Tomcat 6.0 autonome.
