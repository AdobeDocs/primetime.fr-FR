---
seo-title: Création de l'application AIR de Flash Access Manager
title: Création de l'application AIR de Flash Access Manager
uuid: 00927eb3-b8eb-4dd4-b528-91b70760c8cd
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Création de l&#39;application AIR de Flash Access Manager {#building-the-flash-access-manager-air-application}

Pour générer le fichier AIR de Flash Access Manager à partir du code source, vous devez installer Flex et AIR SDK sur votre ordinateur. Avant de pouvoir compresser et exécuter l’application, vous devez compiler le code MXML dans un fichier SWF à l’aide du [!DNL amxmlc] compilateur. Le [!DNL amxmlc] compilateur se trouve dans le [!DNL bin] répertoire du SDK Flex 4 ou version ultérieure. Si vous le souhaitez, vous pouvez définir la variable d’environnement de chemin d’accès pour inclure le répertoire bin du SDK Flex afin de faciliter l’exécution des utilitaires sur la ligne de commande.

Procédez comme suit pour créer le fichier AIR de Flash Access Manager :

1. Ouvrez un shell de commande ou un terminal et accédez au dossier de projet de l&#39;application AIR Flash Access Manager ( [!DNL UI Tools\Flash Access Manager] dans le répertoire de mise en oeuvre des références).
1. Saisissez la commande suivante :

   ```
   amxmlc src\FlashAccessmanager.mxml
   ```

   L’exécution [!DNL amxmlc] produit [!DNL FlashAccessManager.swf], qui contient le code compilé de l’application.

Le SDK Adobe AIR comprend l’utilitaire ADT (AIR Developer Tool) permettant de regrouper les applications AIR et de générer des certificats. les applications AIR doivent être signées numériquement ; les utilisateurs reçoivent un avertissement lorsqu’ils installent des applications qui ne sont pas correctement signées ou qui ne sont pas signées du tout. Pour générer un certificat à l’aide de la ligne de commande, ouvrez une fenêtre de console dans le même dossier que votre application AIR et tapez ce qui suit :

```
adt -certificate -cn SelfSigned 1024-RSA testCert.pfx  
<i class="+ topic ph hi-d="" i "="">
  some_password 
</i class="+ topic>
```

Remplacez *some_password* par un mot de passe de votre choix. Après quelques secondes, ADT doit terminer son processus de génération de certificats et vous devez disposer d’un nouveau [!DNL testCert.pfx] fichier dans votre répertoire d’applications.

Ensuite, utilisez ADT pour compresser l’application dans un [!DNL .air] fichier à l’aide de la commande :

```
adt -package -storetype pkcs12 -keystore testCert.pfx FlashAccessManager.air src\FlashAccessManager-app.xml . -C src assets
```

Cette commande indique à ADT de compresser votre application, en utilisant le fichier de clé dans [!DNL testCert.pfx]. Dans la ligne ci-dessus, vous configurez ADT pour regrouper l’ensemble de votre application dans un fichier nommé [!DNL FlashAccessManager.air], et pour inclure les fichiers [!DNL FlashAccessManager-app.xml] et [!DNL FlashAccessManager.swf] ainsi que les images du répertoire des ressources.

Dans le cadre de ce processus, vous serez invité à saisir le mot de passe que vous avez défini pour votre nouveau fichier de certificat. Saisissez-la, patientez un instant et un [!DNL FlashAccessManager.air] fichier doit apparaître dans le même répertoire que les fichiers de votre projet.
