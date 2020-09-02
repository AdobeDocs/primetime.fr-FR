---
description: Vous pouvez liste autorisée vos applications iOS à l’aide de l’outil de machotools de Adobe.
seo-description: Vous pouvez liste autorisée vos applications iOS à l’aide de l’outil de machotools de Adobe.
seo-title: Liste autorisée de votre application iOS
title: Liste autorisée de votre application iOS
uuid: bc558f5f-d4e6-4c1c-81eb-f8bd61c63016
translation-type: tm+mt
source-git-commit: eb9f0a2f6d2118b953c711dfdc0402d1d923b016
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 0%

---


# Liste autorisée de votre application iOS {#allowlist-your-ios-application}

Vous pouvez liste autorisée vos applications iOS à l’aide de l’outil de machotools de Adobe.

En règle générale, lorsque vous exécutez une application TVSDK, vous pouvez utiliser les outils de ligne de commande Adobe Primetime DRM pour liste autorisée de votre application.

>[!TIP]
>
>Vous pouvez également utiliser ces outils pour créer des stratégies DRM et chiffrer du contenu.

L’option Autoriser l’affichage de la liste de votre application garantit que le contenu protégé ne peut être lu que dans votre lecteur vidéo. Toutefois, l’autorisation de la mise en vente d’une application iOS requiert que vous effectuiez une procédure spéciale compatible avec les règles d’envoi des applications d’Apple.

Avant d’envoyer une application iOS, vous devez la signer et la publier sur Apple.

>[!NOTE]
>
>Apple dépouille la signature de votre développeur et signe à nouveau l’application avec son propre certificat.

En raison de la nouvelle signature, les informations d’inscription que vous avez générées avant de les envoyer à l’App Store d’Apple ne sont pas utilisables.

Pour utiliser cette stratégie d’envoi, l’Adobe a créé un `machotools` outil qui permet d’empreintes digitales dans votre application iOS pour créer une valeur digest, la signer et l’insérer dans votre application iOS. Une fois votre application iOS empreinte digitale identifiée, vous pouvez la soumettre à l’Apple App Store. Lorsqu’un utilisateur exécute votre application à partir de l’App Store, Primetime DRM effectue un calcul à l’exécution de l’empreinte digitale de l’application et la confirme avec la valeur digest qui a été précédemment injectée dans l’application. Si l’empreinte correspond, l’application est confirmée comme étant autorisée à être répertoriée et le contenu protégé est autorisé à lire.

L’outil d’Adobe `machotools` est inclus dans le SDK iOS TVSDK, dans le [ ! DNL [...]/tools/DRM].

Pour utiliser `machotools`:

1. Générez une paire de clés.

   Pour utiliser un utilitaire tel qu’OpenSSL, ouvrez une fenêtre de commande et saisissez ce qui suit :

   ```shell
   openssl genrsa -des3 -out selfsigncert-ios.key 1024
   ```

1. Lorsque vous y êtes invité, saisissez un mot de passe pour protéger la clé privée.

   Les mots de passe doivent contenir au moins 12 caractères et les caractères doivent contenir un mélange de caractères ASCII majuscules et minuscules et de chiffres.
1. Pour utiliser OpenSSL pour générer un mot de passe fort pour vous, ouvrez une fenêtre de commande et saisissez les informations suivantes :

   ```shell
   openssl rand -base64 8
   ```

1. Générer une demande de signature de certificat (CSR).

   Pour utiliser OpenSSL pour générer une CSR, ouvrez une fenêtre de commande et saisissez les informations suivantes :

   ```shell
   openssl req -new -key selfsigncert-ios.key -out selfsigncert-ios.csr -batch
   ```

1. Signez le certificat par vous-même et entrez toute durée.

   L’exemple suivant donne une expiration de 20 ans :

   ```shell
   openssl x509 -req -days 7300 -in selfsigncert-ios.csr  
     -signkey selfsigncert-ios.key -out selfsigncert-ios.crt
   ```

1. Convertissez le certificat autosigné en fichier PKCS#12 :

   ```shell
   openssl pkcs12 -export -out selfsigncert-ios.pfx  
     -inkey selfsigncert-ios.key -in selfsigncert-ios.crt
   ```

   Vous pouvez utiliser le certificat autosigné pour signer votre application iOS.

1. Mettez à jour l’emplacement du fichier PFX et du mot de passe.
1. Avant de créer votre application dans Xcode, accédez à **[!UICONTROL Build Phases]** > **[!UICONTROL Run Script]** et ajoutez la commande suivante à votre script d’exécution :

   ```shell
   mkdir -p "${PROJECT_DIR}/generatedRes" "${PROJECT_DIR}/machotools" sign  
     -in "${CODESIGNING_FOLDER_PATH}/${EXECUTABLE_NAME}"  
     -out "${PROJECT_DIR}/generatedRes/AAXSAppDigest.digest"  
     -pfx "${PROJECT_DIR}/selfsigncert-ios.pfx"  
     -pass PASSWORD
   ```

1. Exécutez [!DNL machotools] pour générer la valeur de hachage de l’ID d’éditeur de votre application.

   ```shell
   ./machotools dumpMachoSignature -in ${PROJECT_DIR}/generatedRes/AAXSAppDigest.digest
   ```

1. Créez une nouvelle stratégie DRM ou mettez à jour votre stratégie existante afin d’inclure la valeur de hachage de l’ID d’éditeur renvoyée.
1. A l’aide de la [!DNL AdobePolicyManager.jar], créez une nouvelle stratégie DRM (mettez à jour votre stratégie existante) afin d’inclure la valeur de hachage de l’ID d’éditeur renvoyée, un ID d’application facultatif et les attributs de version minimale et maximale dans le [!DNL flashaccess-tools.properties] fichier inclus.

   ```shell
   java -jar libs/AdobePolicyManager.jar new app_allowlist.pol
   ```

1. Créez un package du contenu à l’aide de la nouvelle stratégie DRM et vérifiez la lecture du contenu répertorié autorisé dans votre application iOS.
