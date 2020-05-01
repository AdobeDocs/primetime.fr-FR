---
seo-title: Configuration de la base de données et configuration de la source de données JNDI
title: Configuration de la base de données et configuration de la source de données JNDI
uuid: 1326523f-c053-4169-a934-1b2d3907b1f4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Configuration de la base de données et configuration de la source de données JNDI {#setting-up-the-database-and-configuring-the-jndi-datasource}

Le serveur de licences d’implémentation de référence requiert une base de données pour prendre en charge les fonctionnalités suivantes :

* Authentification des utilisateurs
* Règles métier de la démonstration de modèle d’utilisation
* Conversion des métadonnées
* Prise en charge des domaines

L’acquisition de licence anonyme ne nécessite pas l’exécution d’une base de données.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Les instructions de cette section concernent la plate-forme Microsoft Windows. Pour les autres systèmes d’exploitation, consultez la documentation de votre système d’exploitation ou la documentation MySQL.

Pour exécuter le serveur de licences, vous devez installer et configurer MySQL 5.1.34 :

1. Exécutez le programme d’installation MySQL (situé dans le troisième dossier Party\MySQL\Installer\5.1 sur le DVD).
1. A la fin de la procédure d&#39;installation, vérifiez **[!UICONTROL Configure MySQL Server Now]** le début de l&#39;assistant de configuration. Utilisez les paramètres par défaut ou sélectionnez des paramètres spécifiques à des fins de test, à l&#39;exception près que dans le 5e écran, vous devez sélectionner **[!UICONTROL Online Transaction Processing (OLTP)]** ou **[!UICONTROL Manual Setting]** et entrer le nombre maximal de connexions autorisées.

1. Notez le mot de passe racine.
1. Si vous devez réinstaller MySQL, procédez comme suit pour éviter tout problème lors du démarrage du serveur par la suite :

   * Supprimez le lecteur *système de dossiers :* [!DNL \Documents and Settings\All Users\Application Data\MySQL].

   * Supprimez l’ancien dossier d’installation MySQL : par exemple, lecteur *système :* [!DNL \Program Files\MySQL\MySQL Server 5.1].

Ensuite, vous devrez installer MySQL JDBC Driver 5.1.7. Pour ce faire, copiez [!DNL mysql-connector-java-5.1.7-bin.jar] (situé dans le dossier [!DNL Third Party\MySQL\Installer\5.1] du DVD) dans le répertoire de la bibliothèque Tomcat Server lib : [!DNL ...\Tomcat6.0\lib].

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>MySQL JDBC Driver 5.1.7 fonctionne avec Tomcat 6.0. Les versions plus anciennes de Tomcat ne sont pas prises en charge.

Configurez la base de données exemple en configurant le schéma de base de données et en renseignant la base de données avec des données d’exemple. Pour ce faire, procédez comme suit :

1. Accédez à **[!UICONTROL Window's Start Menu]** > **[!UICONTROL MySQL]** > **[!UICONTROL MySQL Server 5.1]** > **[!UICONTROL MySQL Command Line Client]** .
1. Après avoir saisi le mot de passe, exécutez le script SQL suivant pour ajouter le compte utilisateur `dbuser` permettant d’établir une connexion par le biais d’une application Web et créer un schéma de base de données (assurez-vous qu’il n’y a pas de &quot;;&quot; à la fin. Appuyez simplement sur Entrée.) :

   ```
       mysql> source “Reference Implementation\Server\dbscript\createsampledb.sql”
   ```

1. Modifiez le script qui renseigne des données d’exemple dans les tableaux afin d’inclure des données à des fins de test : [!DNL Reference Implementation\Server\dbscript\PopulateSampleDB.sql].
1. Exécutez ce script pour renseigner les données comme vous l’avez fait à l’étape 2.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>La première fois que vous exécutez le [!DNL CreateSampleDB.sql] script, vous recevez l’erreur suivante :

*ERREUR 1396 (HY000) : Échec de l&#39;opération DROP USER pour la Requête &#39;dbuser&#39;@&#39;localhost&#39; OK, 0 ligne affectée (0,00 seconde).*

Vous pouvez ignorer cette erreur en toute sécurité. Cela ne se produit que la première fois que vous exécutez ce script.

A ce stade, vous devrez configurer le pool de connexions de base de données (DBCP). DBCP utilise le pool de connexions de base de données Jakarta-Commons. Une base de données TestDB de source de données JNDI est configurée pour tirer parti de ce pool de connexions au serveur d’applications. Pour modifier la connexion à la base de données afin qu’elle pointe vers un serveur MySQL qui ne se trouve pas sur localhost, modifiez le [!DNL META-INF\context.xml] fichier (qui spécifie l’emplacement, le nom d’utilisateur et le mot de passe de la base de données du serveur de licences) situé dans [!DNL flashaccess.war], ou modifiez [!DNL \Reference Implementation\Server\refimpl\WebContent\META-INF\context.xml] et recréez le fichier WAR à l’aide des fichiers mis à jour. Pour modifier l&#39;un de ces paramètres, modifiez le répertoire [!DNL context.xml] situé dans le répertoire WebContent et utilisez le script Ant pour recréer le fichier WAR. Pour régler la base de données, modifiez les paramètres de source de données JNDI dans ce fichier.

Si vous déboguez le projet d’implémentation des références dans Eclipse, vous devez ajouter `$CATALINA_HOME\lib\tomcat-dbcp.jar` à votre configuration d’exécution/débogage. Cette étape n’est pas requise si vous exécutez le [!DNL flashaccess.war] fichier sur un serveur Tomcat 6.0 autonome.
