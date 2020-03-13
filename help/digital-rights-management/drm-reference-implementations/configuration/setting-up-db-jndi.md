---
description: 'null'
seo-description: 'null'
seo-title: Configuration de la base de données du serveur de licences
title: Configuration de la base de données du serveur de licences
uuid: aa6185f2-8e9d-4b65-971a-b7534d910580
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Configuration de la base de données du serveur de licences{#set-up-the-license-server-database}

Le serveur de licences d’implémentation de référence requiert une base de données pour prendre en charge les éléments suivants :

* Authentification des utilisateurs
* Règles métier de démonstration du modèle d’utilisation
* Conversion des métadonnées
* Prise en charge des domaines

L’acquisition de licence anonyme ne nécessite pas l’exécution de la base de données.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Cette procédure s’applique uniquement à Microsoft Windows. Pour les autres systèmes d’exploitation, consultez la documentation de votre système d’exploitation ou consultez la documentation MySQL.

Pour exécuter le serveur de licences, vous devez installer et configurer MySQL :

1. Sur le DVD, accédez au [!DNL Third Party\MySQL\Installer\5.1] dossier et le d’installation .
1. Exécutez l’installation de MySQL.
1. Sélectionnez **[!UICONTROL Configure MySQL Server Now]** pour  l’assistant de configuration.
1. Jusqu’au cinquième écran, utilisez les paramètres par défaut ou sélectionnez des paramètres spécifiques pour vos tests.
1. Dans le cinquième écran, sélectionnez **[!UICONTROL Online Transaction Processing (OLTP)]** ou **[!UICONTROL Manual Setting]** saisissez le nombre maximal de connexions autorisées.
1. Notez le mot de passe racine.
1. Pour réinstaller MySQL, si vous devez le serveur ultérieurement, procédez comme suit :
   1. Supprimez le lecteur *système :* dossier.

      Ce dossier se trouve dans [!DNL \Documents and Settings\All Users\Application Data\MySQL].
   1. Supprimez l’ancien dossier d’installation de MySQL.

      Par exemple, lecteur *système:*, qui se trouve dans [!DNL \Program Files\MySQL\MySQL Server 5.1].
1. Pour installer MySQL JDBC Driver 5.1.7, copiez le [!DNL mysql-connector-java-5.1.7-bin.jar] fichier situé dans le [!DNL Third Party\MySQL\Installer\5.1] dossier du DVD dans le [!DNL ...\Tomcat6.0\lib] répertoire du serveur Tomcat.

   >[!NOTE] {class=&quot;- rubrique/note &quot;}
   >
   >MySQL JDBC Driver 5.1.7 fonctionne avec Tomcat 6.0. Les anciennes versions de Tomcat ne sont plus prises en charge.

