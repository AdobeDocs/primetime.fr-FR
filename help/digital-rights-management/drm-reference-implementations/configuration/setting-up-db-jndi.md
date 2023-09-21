---
title: Configuration de la base de données du serveur de licences
description: Configuration de la base de données du serveur de licences
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# Configuration de la base de données du serveur de licences{#set-up-the-license-server-database}

Le serveur de licence de mise en oeuvre de référence requiert une base de données pour prendre en charge les éléments suivants :

* Authentification de l’utilisateur
* Règles de fonctionnement de démonstration du modèle d’utilisation
* Conversion des métadonnées
* Prise en charge des domaines

L’acquisition de licences anonymes ne nécessite pas l’exécution de la base de données.

>[!NOTE]
>
>Cette procédure s’applique uniquement à Microsoft Windows. Pour les autres systèmes d’exploitation, consultez la documentation de votre système d’exploitation ou la documentation de MySQL.

Pour exécuter le serveur de licences, vous devez installer et configurer MySQL :

1. Sur le DVD, accédez au [!DNL Third Party\MySQL\Installer\5.1] et démarrez le programme d’installation.
1. Terminez l’installation de MySQL.
1. Sélectionner **[!UICONTROL Configure MySQL Server Now]** pour lancer l&#39;assistant de configuration.
1. Jusqu’au cinquième écran, utilisez les paramètres par défaut ou sélectionnez des paramètres spécifiques pour vos tests.
1. Sur le cinquième écran, sélectionnez **[!UICONTROL Online Transaction Processing (OLTP)]** ou **[!UICONTROL Manual Setting]** et saisissez le nombre maximal de connexions autorisées.
1. Notez le mot de passe racine.
1. Pour réinstaller MySQL, si vous devez démarrer le serveur ultérieurement, procédez comme suit :
   1. Supprimez le *lecteur système :* dossier.

      Ce dossier se trouve dans [!DNL \Documents and Settings\All Users\Application Data\MySQL].
   1. Supprimez l’ancien dossier d’installation de MySQL.

      Par exemple : *lecteur système :*, qui se trouve dans [!DNL \Program Files\MySQL\MySQL Server 5.1].
1. Pour installer MySQL JDBC Driver 5.1.7, copiez la variable [!DNL mysql-connector-java-5.1.7-bin.jar] dans le fichier [!DNL Third Party\MySQL\Installer\5.1] dossier sur le DVD [!DNL ...\Tomcat6.0\lib] sur le serveur Tomcat.

   >[!NOTE]
   >
   >MySQL JDBC Driver 5.1.7 fonctionne avec Tomcat 6.0. Les anciennes versions de Tomcat ne sont plus prises en charge.
