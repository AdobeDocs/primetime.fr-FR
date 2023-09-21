---
description: Vous pouvez liste autorisée de vos applications iOS à l’aide de l’outil machotools d’Adobe.
title: Liste autorisée de votre application iOS
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 0%

---

# Liste autorisée de votre application iOS {#allowlist-your-ios-application}

Vous pouvez liste autorisée de vos applications iOS à l’aide de l’outil machotools d’Adobe.

En règle générale, lorsque vous exécutez une application TVSDK, vous pouvez utiliser les outils de ligne de commande Adobe Primetime DRM pour liste autorisée de votre application.

>[!TIP]
>
>Vous pouvez également utiliser ces outils pour créer des stratégies DRM et chiffrer du contenu.

La mise en liste autorisée de votre application garantit que le contenu protégé ne peut être lu que dans votre lecteur vidéo. Toutefois, pour figurer sur une liste autorisée d’une application iOS, vous devez suivre une procédure spéciale qui fonctionne avec les stratégies d’envoi d’application Apple.

Avant d’envoyer une application iOS, vous devez la signer et la publier dans Apple.

>[!NOTE]
>
>Apple retire la signature de votre développeur et signe à nouveau l’application avec son propre certificat.

En raison de la nouvelle signature, les informations de liste autorisée que vous avez générées avant d’être envoyées à Apple App Store ne sont pas utilisables.

Pour utiliser cette stratégie d’envoi, Adobe a créé une `machotools` qui imprime votre application iOS pour créer une valeur digest, la signer et l’injecter dans votre application iOS. Une fois l’empreinte digitale de l’application iOS enregistrée, vous pouvez l’envoyer à Apple App Store. Lorsqu’un utilisateur exécute votre application à partir d’App Store, Primetime DRM effectue un calcul d’empreinte digitale de l’application au moment de l’exécution et le confirme avec la valeur de condensé qui a été précédemment injectée dans l’application. Si l’empreinte correspond, l’application est confirmée comme figurant sur la liste autorisée et le contenu protégé est autorisé à être lu.

L&#39;Adobe `machotools` est inclus dans le SDK iOS TVSDK, dans le fichier [!DNL [..]dossier /tools/DRM].

Pour utiliser `machotools`:

1. Générez une paire de clés.

   Pour utiliser un utilitaire tel qu’OpenSSL, ouvrez une fenêtre de commande et saisissez les informations suivantes :

   ```shell
   openssl genrsa -des3 -out selfsigncert-ios.key 1024
   ```

1. Lorsque vous y êtes invité, saisissez un mot de passe pour protéger la clé privée.

   Les mots de passe doivent contenir au moins 12 caractères, et les caractères doivent contenir un mélange de caractères ASCII majuscules et minuscules et de nombres.
1. Pour utiliser OpenSSL afin de générer un mot de passe sécurisé, ouvrez une fenêtre de commande et saisissez les informations suivantes :

   ```shell
   openssl rand -base64 8
   ```

1. Générer une demande de signature de certificat (CSR).

   Pour utiliser OpenSSL pour générer une demande de signature de certificat, ouvrez une fenêtre de commande et saisissez les informations suivantes :

   ```shell
   openssl req -new -key selfsigncert-ios.key -out selfsigncert-ios.csr -batch
   ```

1. Signez le certificat automatiquement et saisissez toute durée.

   L’exemple suivant donne une expiration de 20 ans :

   ```shell
   openssl x509 -req -days 7300 -in selfsigncert-ios.csr  
     -signkey selfsigncert-ios.key -out selfsigncert-ios.crt
   ```

1. Convertissez le certificat auto-signé en fichier PKCS#12 :

   ```shell
   openssl pkcs12 -export -out selfsigncert-ios.pfx  
     -inkey selfsigncert-ios.key -in selfsigncert-ios.crt
   ```

   Vous pouvez utiliser le certificat autosigné pour signer votre application iOS.

1. Mettez à jour l’emplacement du fichier PFX et le mot de passe.
1. Avant de créer votre application dans Xcode, accédez à  **[!UICONTROL Build Phases]** > **[!UICONTROL Run Script]** et ajoutez la commande suivante à votre script d’exécution :

   ```shell
   mkdir -p "${PROJECT_DIR}/generatedRes" "${PROJECT_DIR}/machotools" sign  
     -in "${CODESIGNING_FOLDER_PATH}/${EXECUTABLE_NAME}"  
     -out "${PROJECT_DIR}/generatedRes/AAXSAppDigest.digest"  
     -pfx "${PROJECT_DIR}/selfsigncert-ios.pfx"  
     -pass PASSWORD
   ```

1. Exécuter [!DNL machotools] pour générer la valeur de hachage de l’identifiant de l’éditeur de votre application.

   ```shell
   ./machotools dumpMachoSignature -in ${PROJECT_DIR}/generatedRes/AAXSAppDigest.digest
   ```

1. Créez une nouvelle stratégie DRM ou mettez à jour votre stratégie existante pour inclure la valeur de hachage Publisher ID renvoyée.
1. En utilisant la variable [!DNL AdobePolicyManager.jar], créez une nouvelle stratégie DRM (mettez à jour votre stratégie existante) afin d’inclure la valeur de hachage de l’identifiant de l’éditeur renvoyée, un ID d’application facultatif et les attributs de version min. et max. dans le [!DNL flashaccess-tools.properties] fichier .

   ```shell
   java -jar libs/AdobePolicyManager.jar new app_allowlist.pol
   ```

1. Regroupez le contenu à l’aide de la nouvelle stratégie DRM et confirmez la lecture du contenu autorisé répertorié dans votre application iOS.
