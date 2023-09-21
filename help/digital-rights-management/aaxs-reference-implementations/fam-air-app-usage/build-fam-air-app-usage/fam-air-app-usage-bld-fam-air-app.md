---
title: Création de l’application AIR Flash Access Manager
description: Création de l’application AIR Flash Access Manager
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Création de l’application AIR Flash Access Manager {#building-the-flash-access-manager-air-application}

Pour créer le fichier AIR Flash Access Manager à partir du code source, vous devez installer le SDK Flex et AIR sur votre ordinateur. Avant de pouvoir créer un package et exécuter l’application, vous devez compiler le code MXML dans un fichier de SWF à l’aide de la fonction [!DNL amxmlc] compilateur. La variable [!DNL amxmlc] Le compilateur se trouve dans la [!DNL bin] du SDK Flex 4 ou version ultérieure. Si vous le souhaitez, vous pouvez définir votre variable d’environnement de chemin d’accès pour inclure le répertoire bin du SDK Flex afin de faciliter l’exécution des utilitaires sur la ligne de commande.

Pour créer le fichier AIR Flash Access Manager, procédez comme suit :

1. Ouvrez un shell de commande ou un terminal et accédez au dossier du projet de l’application AIR Flash Access Manager ( [!DNL UI Tools\Flash Access Manager] dans le répertoire d’implémentation de référence).
1. Saisissez la commande suivante :

   ```
   amxmlc src\FlashAccessmanager.mxml
   ```

   En cours [!DNL amxmlc] produit [!DNL FlashAccessManager.swf], qui contient le code compilé de l’application.

Le SDK Adobe AIR comprend l’utilitaire AIR Developer Tool (ADT) pour compresser les applications AIR et générer des certificats. Les applications AIR doivent être signées numériquement ; les utilisateurs recevront un avertissement lorsqu’ils installeront des applications qui ne sont pas correctement signées ou qui ne le sont pas du tout. Pour générer un certificat à partir de la ligne de commande, ouvrez une fenêtre de console dans le même dossier que votre application AIR et saisissez ce qui suit :

```
adt -certificate -cn SelfSigned 1024-RSA testCert.pfx  
<i class="+ topic ph hi-d="" i "="">
  some_password 
</i class="+ topic>
```

Substituer *some_password* avec un mot de passe de votre choix. Au bout de quelques secondes, ADT doit terminer son processus de génération de certificat et vous devez disposer d’un nouveau [!DNL testCert.pfx] dans le répertoire de votre application.

Ensuite, utilisez ADT pour regrouper l’application dans une [!DNL .air] en utilisant la commande :

```
adt -package -storetype pkcs12 -keystore testCert.pfx FlashAccessManager.air src\FlashAccessManager-app.xml . -C src assets
```

Cette commande indique à ADT de compresser votre application à l’aide du fichier clé dans [!DNL testCert.pfx]. Dans la ligne ci-dessus, vous configurez ADT pour regrouper l’ensemble de votre application dans un fichier nommé [!DNL FlashAccessManager.air]et pour inclure les fichiers [!DNL FlashAccessManager-app.xml] et [!DNL FlashAccessManager.swf] et les images du répertoire des ressources.

Dans le cadre de ce processus, vous serez invité à saisir le mot de passe que vous avez défini pour votre nouveau fichier de certificat. Saisissez-le, attendez un moment et un [!DNL FlashAccessManager.air] doit apparaître dans le même répertoire que les fichiers de votre projet.
