---
seo-title: Présentation du déploiement de Primetime DRM Key Server
title: Présentation du déploiement de Primetime DRM Key Server
uuid: 86630675-c15d-4f32-8212-d7343f4f92e0
translation-type: tm+mt
source-git-commit: 105dedcfe47a5f454a067e66a95827e638290742

---


# Déploiement du serveur clé DRM Primetime {#deploy-the-primetime-drm-key-server}

Avant de déployer Primetime DRM Key Server, assurez-vous d’avoir installé les versions requises de Java et Tomcat. Voir Configuration requise [pour](../../digital-rights-management/using-the-drm-key-server/requirements.md)DRM Key Server.

Le téléchargement de Primetime DRM Key Server inclut [!DNL faxsks.war]. Pour déployer ce fichier WAR, copiez-le dans le [!DNL webapps] répertoire de Tomcat. Si vous avez déjà déployé le fichier WAR, vous devrez peut-être supprimer manuellement le répertoire WAR décompressé, [!DNL faxsks] dans le [!DNL webapps] répertoire de Tomcat). Pour empêcher Tomcat de décompresser les fichiers WAR, modifiez le [!DNL server.xml] fichier dans le [!DNL conf] répertoire de Tomcat et définissez l’ `unpackWARs` attribut sur `false`.

Primetime DRM Key Server utilise éventuellement une bibliothèque spécifique à la plate-forme (`jsafe.dll` sous Windows ou `libjsafe.so` sous Linux) pour améliorer les performances. Copiez la bibliothèque appropriée pour votre plateforme `thirdparty/cryptoj/platform` vers un emplacement spécifié par la variable `PATH` d’environnement (ou `LD_LIBRARY_PATH` sous Linux).

>[!NOTE]
>
>La version 64 bits de la [!DNL jsafe] bibliothèque ne doit être utilisée que si le système d’exploitation et le JDK prennent en charge la version 64 bits, sinon la version 32 bits.

## Configuration SSL {#ssl-configuration}

SSL est requis pour la diffusion de clés HTTPS à distance. Les connexions SSL peuvent être gérées par le serveur d’applications (c.-à-d. en configurant SSL dans Tomcat) ou par un autre serveur (c.-à-d. un équilibreur de charge, un accélérateur SSL ou Apache). La diffusion de clés HTTPS distante requiert une connexion SSL. Le serveur a besoin d’un certificat SSL émis par une autorité de certification approuvée.

Il existe plusieurs options pour configurer SSL. Vous trouverez ci-dessous des exemples de configuration de SSL avec l’authentification du client dans Apache et Tomcat.

L’exemple suivant illustre la configuration SSL d’Apache :

```
SSLEngineon 
SSLCertificateFile "certs/server_cert.pem" 
SSLCertificateKeyFile "certs/server_key.pem" 
SSLOptions +StdEnvVars +FakeBasicAuth -ExportCertData +StrictRequire 
SSLRequireSSL 
ProxyRequests Off 
ProxyPass /https://keyserver-name:port/ 
ProxyPassReverse /https://keyserver-name:port/
```

L’exemple suivant illustre la configuration SSL de Tomcat. Pour générer des fichiers de certificat et de clé :

```
Generate key:  
 openssl genrsa -des3 -out server.key 1024 
Generate CSR: 
 openssl req -new -key server.key -out server.csr 
Generate Certificate: 
 openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.cer
```

Lorsque vous êtes invité à saisir le nom commun, utilisez le nom de domaine complet (FQDN) de votre serveur.

Copiez [!DNL server.cer]et [!DNL server.key] dans le répertoire Tomcat. Spécifiez le connecteur suivant dans [!DNL conf/server.xml]:

```
<Connector port="8443" protocol="HTTP/1.1" SSLEnabled="true" 
 maxThreads="150" scheme="https" secure="true" 
 sslProtocol="TLS" 
 SSLCertificateFile="${catalina.base}/server.cer" 
 SSLCertificateKeyFile="${catalina.base}/server.key" 
 SSLPassword="password-for-key-file" 
 SSLVerifyClient="require"/>
```

## Propriétés du système Java {#java-system-properties}

Vous avez la possibilité de définir les deux propriétés système Java suivantes pour modifier l&#39;emplacement de la configuration et des fichiers journaux pour le serveur de clés DRM Primetime :

* `KeyServer.ConfigRoot` - Ce répertoire contient tous les fichiers de configuration du serveur de clés DRM Primetime. Pour plus d’informations sur le contenu de ces fichiers, voir Fichiers [de configuration du serveur de](#key-server-configuration-files)clés. Si elle n’est pas définie, la valeur par défaut est [!DNL CATALINA_BASE/keyserver].

* `KeyServer.LogRoot` - Il s&#39;agit d&#39;un répertoire de journaux qui contient les journaux d&#39;application iOS Key Server. Si elle n’est pas définie, la valeur par défaut est la même que `KeyServer.ConfigRoot`

* `XboxKeyServer.LogRoot` - Il s&#39;agit d&#39;un répertoire de journaux qui contient les journaux d&#39;application du serveur Xbox Key Server. Si elle n’est pas définie, la valeur par défaut est identique à `KeyServer.ConfigRoot`.

Si vous utilisez [!DNL catalina.bat] ou [!DNL catalina.sh] pour début Tomcat, ces propriétés système peuvent être facilement définies à l’aide de la variable `JAVA_OPTS` environnement. Toutes les options Java définies ici seront utilisées au démarrage de Tomcat. Par exemple, définissez :

```
JAVA_OPTS=-DKeyServer.ConfigRoot=”absolute-path-to-config-folder” 
  -DKeyServer.LogRoot=”absolute-path-to-log-folder”
```

## Informations d’identification DRM Primetime {#primetime-drm-credentials}

Pour traiter les requêtes clés des clients iOS DRM Primetime et Xbox 360, le serveur de clés DRM Primetime doit être configuré avec un jeu d’informations d’identification émises par Adobe. Ces informations d’identification peuvent être stockées dans des fichiers PKCS#12 ( [!DNL .pfx]) ou sur un HSM.

Les [!DNL .pfx] fichiers peuvent être localisés n’importe où, mais pour faciliter la configuration, Adobe conseille de placer les [!DNL .pfx] fichiers dans le répertoire de configuration du client. Pour plus d’informations, voir Fichiers [de configuration du serveur de](#key-server-configuration-files)clés.

### Configuration HSM {#section_13A19E3E32934C5FA00AEF621F369877}

Si vous choisissez d’utiliser un HSM pour stocker les informations d’identification de votre serveur, vous devez charger les clés privées et les certificats sur le HSM et créer un fichier de configuration *pkcs11.cfg* . Ce fichier doit se trouver dans le répertoire *KeyServer.ConfigRoot* . Consultez la section [!DNL <Primetime DRM Key Server>/configs] répertoire pour un exemple de fichier de configuration PKCS 11. Pour plus d’informations sur le format de [!DNL pkcs11.cfg]la bibliothèque, reportez-vous à la documentation du fournisseur Sun PKCS11.

Pour vérifier que vos fichiers de configuration HSM et Sun PKCS11 sont correctement configurés, vous pouvez utiliser la commande suivante à partir du répertoire où se trouve le [!DNL pkcs11.cfg] fichier ( [!DNL keytool] est installé avec Java JRE et JDK) :

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

Si vos informations d’identification s’affichent dans la liste, le module HSM est correctement configuré et le serveur de clés pourra accéder aux informations d’identification.

## Fichiers de configuration du serveur de clés {#key-server-configuration-files}

Le serveur de clés DRM Primetime nécessite deux types de fichiers de configuration :

* Un fichier de configuration global, [!DNL flashaccess-keyserver-global.xml]
* Un fichier de configuration de client pour chaque client, [!DNL flashaccess-keyserver-tenant.xml]

Si des modifications sont apportées aux fichiers de configuration, le serveur doit être redémarré pour que les modifications prennent effet.

Pour éviter de rendre les mots de passe disponibles en texte clair dans les fichiers de configuration, tous les mots de passe spécifiés dans les fichiers de configuration globale et locataire doivent être chiffrés. Pour plus d’informations sur le chiffrement des mots de passe, voir [*Password Scrambler *dans* Utilisation du serveur DRM Primetime pour la diffusion en continu *](../protected-streaming/understanding-deployment/drm-for-protected-streaming-utilities/password-scrambler.md)protégée.

## Structure du répertoire de configuration {#configuration-directory-structure}

Les répertoires de configuration ont la structure suivante :

```
KeyServer.ConfigRoot/  
--flashaccess-keyserver-global.xml 
--pkcs11.cfg (optional) 
--faxsks/ 
----tenants/ 
------tenantname/
---------flashaccess-keyserver-tenant.xml 
---------credential.pfx (optional) 
```

## Fichier de configuration global {#global-configuration-file}

Le fichier [!DNL flashaccess-keyserver-global.xml] de configuration contient les paramètres qui s&#39;appliquent à tous les locataires du serveur de clés. Ce fichier doit être situé dans `KeyServer.ConfigRoot`. Consultez le [!DNL configs] répertoire pour un exemple de fichier de configuration global. Le fichier de configuration global comprend les éléments suivants :

* Journalisation : indique le niveau de journalisation et la fréquence d&#39;enregistrement des fichiers journaux.
* Mot de passe HSM : requis uniquement si un HSM est utilisé pour stocker les informations d’identification du serveur.

Consultez les commentaires dans l&#39;exemple de fichier de configuration global situé dans [!DNL <Primetime DRM Key Server>/configs] pour plus de détails.

## Fichiers de configuration du client {#tenant-configuration-files}

Les fichiers [!DNL flashaccess-ioskeyserver-tenant.xml] et [!DNL flashaccess-xboxkeyserver-tenant.xml] de configuration contiennent des paramètres qui s&#39;appliquent à un client spécifique du serveur de clés DRM Primetime. Chaque client dispose de sa propre instance de ces fichiers de configuration situés dans [!DNL <KeyServer.ConfigRoot>/faxsks/tenants/tenantname]. Consultez le répertoire [!DNL configs/faxsks/tenants/sampletenant] pour un exemple de fichier de configuration de client.

Vous pouvez spécifier tous les chemins d&#39;accès aux fichiers dans le fichier de configuration du client sous la forme de chemins d&#39;accès absolus ou de chemins d&#39;accès relatifs au répertoire de configuration du client ( [!DNL <KeyServer.ConfigRoot>/faxsks/tenants/tenantname]).

Tous les fichiers de configuration de client incluent :

* Informations d’identification du serveur de clés - Spécifie une ou plusieurs informations d’identification du serveur de clés (certificat et clé privée) émises par Adobe. Peut être spécifié sous la forme d’un chemin d’accès à un [!DNL .pfx] fichier et d’un mot de passe, ou d’un alias pour des informations d’identification stockées sur un HSM. Plusieurs informations d’identification de ce type peuvent être spécifiées ici, par exemple chemins d’accès aux fichiers ou alias clés, ou les deux.

Le fichier de configuration du client **iOS** comprend les éléments suivants :

* Fenêtre de Diffusion clé - (facultatif) Spécifie la fenêtre de validité de l&#39;horodatage de la demande de diffusion clé (en secondes). La valeur par défaut est de 500 secondes.

Le fichier de configuration du client **Xbox 360** comprend :

* Informations d’identification XSTS - Spécifie les informations d’identification du développeur d’applications utilisées pour déchiffrer les jetons XSTS.
* Certificat de signature XSTS : indique le certificat utilisé pour vérifier la signature sur les jetons XSTS.
* Liste blanche de Packager - Certificats de Packager approuvés par le serveur de clés. S’il n’y a aucun certificat packager contenu dans la liste, tous les certificats packager seront approuvés.

## Fichiers journaux {#log-files}

Les fichiers journaux générés par l&#39;application Primetime DRM Key Server ( [!DNL flashaccess-ioskeyserver_*.log] et [!DNL flashaccess-xboxkeyserver_*.log]) seront situés dans le répertoire spécifié par `KeyServer.LogRoot`.

Les fichiers journaux sont distingués par le type de client. Il existe deux journaux par type de client :

* Un journal *d&#39;* accès : surveille uniquement les requêtes et les réponses.
* Un journal ** contextuel : contient des messages d&#39;erreur détaillés et des traces de pile.

## Démarrage du serveur de clés {#starting-the-key-server}

Pour début au serveur de clés, début Tomcat.