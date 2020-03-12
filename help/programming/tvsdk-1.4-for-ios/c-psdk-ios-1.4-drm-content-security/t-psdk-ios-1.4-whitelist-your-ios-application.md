---
description: Vous pouvez mettre en liste blanche vos applications iOS à l’aide de l’outil machotools d’Adobe.
seo-description: Vous pouvez mettre en liste blanche vos applications iOS à l’aide de l’outil machotools d’Adobe.
seo-title: Liste blanche de votre application iOS
title: Liste blanche de votre application iOS
uuid: 52ce1dd7-5f10-418e-9916-cec60eae874e
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Liste blanche de votre application iOS{#whitelist-your-ios-application}

Vous pouvez mettre en liste blanche vos applications iOS à l’aide de l’outil machotools d’Adobe.

En règle générale, lorsque vous terminez une application TVSDK, vous pouvez utiliser les outils de ligne de commande DRM d’Adobe Primetime pour mettre votre application en liste blanche.

>[!TIP]
>
>Vous pouvez également utiliser ces outils pour créer des stratégies DRM et chiffrer du contenu.

La liste blanche de votre application garantit que le contenu protégé ne peut être lu que dans votre lecteur vidéo. Toutefois, la liste blanche d’une application iOS requiert que vous exécutiez une procédure spéciale compatible avec les règles d’envoi des applications d’Apple.

Avant d’envoyer une application iOS, vous devez la signer et la publier sur Apple.

>[!NOTE]
>
>Apple retire la signature de votre développeur et signe à nouveau l’application avec son propre certificat.

En raison de la nouvelle signature, les informations de liste blanche que vous avez générées avant d’être envoyées à l’App Store d’Apple ne sont pas utilisables.

Pour utiliser cette stratégie d’envoi, Adobe a créé un `machotools` outil qui imprime l’empreinte digitale de votre application iOS afin de créer une valeur digest, de signer cette valeur et d’injecter cette valeur dans votre application iOS. Une fois votre application iOS identifiée, vous pouvez l’envoyer à l’Apple App Store. Lorsqu’un utilisateur exécute votre application à partir de l’App Store, le DRM Primetime effectue un calcul à l’exécution de l’empreinte digitale de l’application et la confirme avec la valeur de prétraitement qui a été précédemment injectée dans l’application. Si l’empreinte correspond, l’application est confirmée comme étant en liste blanche et le contenu protégé est autorisé à être lu.

L’outil Adobe `machotools` est inclus dans le SDK iOS TVSDK, dans le fichier [!DNL [...]/tools/DRM].

Pour utiliser `machotools`:

1. Générez une paire de clés.

   Pour utiliser un utilitaire tel qu’OpenSSL, ouvrez une fenêtre de commande et saisissez ce qui suit :

   ```
   openssl genrsa -des3 -out selfsigncert-ios.key 1024
   ```

1. Lorsque vous y êtes invité, saisissez un mot de passe pour protéger la clé privée.

   Les mots de passe doivent contenir au moins 12 caractères et les caractères doivent contenir un mélange de caractères ASCII majuscules et minuscules et de nombres.
1. Pour utiliser OpenSSL pour générer un mot de passe fort pour vous, ouvrez une fenêtre de commande et saisissez ce qui suit :

   ```
   openssl rand -base64 8
   ```

1. Générer une demande de signature de certificat (CSR).

   Pour utiliser OpenSSL pour générer une page CSR, ouvrez une fenêtre de commande et saisissez ce qui suit :

   ```
   openssl req -new -key selfsigncert-ios.key -out selfsigncert-ios.csr -batch
   ```

1. Signez le certificat par vous-même et entrez une durée.

   L’exemple suivant donne une expiration de 20 ans :

   ```
   openssl x509 -req -days 7300 -in selfsigncert-ios.csr  
     -signkey selfsigncert-ios.key -out selfsigncert-ios.crt
   ```

1. Convertissez le certificat autosigné en fichier PKCS#12 :

   ```
   openssl pkcs12 -export -out selfsigncert-ios.pfx  
     -inkey selfsigncert-ios.key -in selfsigncert-ios.crt
   ```

   Vous pouvez utiliser le certificat autosigné pour signer votre application iOS.

1. Mettez à jour l’emplacement du fichier PFX et du mot de passe.
1. Avant de créer votre application dans Xcode, accédez à **[!UICONTROL Build Phases]** > **[!UICONTROL Run Script]** et ajoutez la commande suivante à votre script d’exécution :

   ```
   mkdir -p "${PROJECT_DIR}/generatedRes" "${PROJECT_DIR}/machotools" sign  
     -in "${CODESIGNING_FOLDER_PATH}/${EXECUTABLE_NAME}"  
     -out "${PROJECT_DIR}/generatedRes/AAXSAppDigest.digest"  
     -pfx "${PROJECT_DIR}/selfsigncert-ios.pfx"  
     -pass PASSWORD
   ```

1. Exécutez [!DNL machotools] pour générer la valeur de hachage de l’ID d’éditeur de votre application.

   ```
   ./machotools dumpMachoSignature -in ${PROJECT_DIR}/generatedRes/AAXSAppDigest.digest
   ```

1. Créez une nouvelle stratégie DRM ou mettez à jour votre stratégie existante afin d’inclure la valeur de hachage de l’ID d’éditeur renvoyée.
1. A l’aide de la [!DNL AdobePolicyManager.jar]méthode, créez une nouvelle stratégie DRM (mettez à jour votre stratégie existante) afin d’inclure la valeur de hachage de l’ID d’éditeur renvoyée, un ID d’application facultatif et les attributs de version min et max. dans le [!DNL flashaccess-tools.properties] fichier inclus.

   ```
   java -jar libs/AdobePolicyManager.jar new app_whitelist.pol
   ```

1. Créez un package du contenu à l’aide de la nouvelle stratégie DRM et confirmez la lecture du contenu autorisé dans votre application iOS.

