---
title: Présentation du déploiement de Primetime DRM Key Server
description: Présentation du déploiement de Primetime DRM Key Server
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1075'
ht-degree: 0%

---

# Déploiement du serveur de clés DRM Primetime {#deploy-the-primetime-drm-key-server}

Avant de déployer Primetime DRM Key Server, vérifiez que vous avez installé les versions requises de Java et Tomcat. Voir [Exigences du serveur de clé DRM](../../digital-rights-management/using-the-drm-key-server/requirements.md).

Le téléchargement du serveur de clé DRM Primetime comprend les éléments suivants : [!DNL faxsks.war]. Pour déployer ce fichier WAR, copiez-le dans le fichier de Tomcat [!DNL webapps] répertoire . Si vous avez déjà déployé le fichier WAR, vous devrez peut-être supprimer manuellement le répertoire WAR décompressé, [!DNL faxsks] chez Tomcat [!DNL webapps] ). Pour empêcher Tomcat de décompresser des fichiers WAR, modifiez la variable [!DNL server.xml] dans le fichier Tomcat [!DNL conf] et définissez `unpackWARs` Attribuer à `false`.

Le serveur de clé DRM Primetime utilise éventuellement une bibliothèque spécifique à la plateforme (`jsafe.dll` sous Windows ou `libjsafe.so` sous Linux) pour de meilleures performances. Copiez la bibliothèque appropriée pour votre plateforme depuis `thirdparty/cryptoj/platform` à un emplacement spécifié par la variable `PATH` variable d’environnement (ou `LD_LIBRARY_PATH` sous Linux).

>[!NOTE]
>
>La version 64 bits du [!DNL jsafe] ne doit être utilisée que si le système d’exploitation et JDK prennent en charge la version 64 bits, sinon utilisez la version 32 bits.

## Configuration SSL {#ssl-configuration}

SSL est requis pour la diffusion de clé HTTPS distante. Les connexions SSL peuvent être gérées par le serveur d’applications (c’est-à-dire en configurant SSL dans Tomcat) ou par un autre serveur (c’est-à-dire un équilibreur de charge, un accélérateur SSL ou Apache). La diffusion de clé HTTPS distante nécessite une connexion SSL. Le serveur a besoin d’un certificat SSL émis par une autorité de certification approuvée.

Il existe plusieurs options pour configurer SSL. Vous trouverez ci-dessous des exemples de configuration de SSL avec authentification du client dans Apache et Tomcat.

L’exemple suivant illustre la configuration Apache SSL :

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

L’exemple suivant illustre la configuration SSL de Tomcat. Pour générer les fichiers de certificat et de clé :

```
Generate key:  
 openssl genrsa -des3 -out server.key 1024 
Generate CSR: 
 openssl req -new -key server.key -out server.csr 
Generate Certificate: 
 openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.cer
```

Lorsque vous y êtes invité, utilisez le nom de domaine complet (FQDN) de votre serveur.

Copier [!DNL server.cer], et [!DNL server.key] vers le répertoire Tomcat. Spécifiez le connecteur suivant dans [!DNL conf/server.xml]:

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

Vous avez la possibilité de définir les deux propriétés système Java suivantes pour modifier l’emplacement des fichiers de configuration et journaux pour le serveur de clés DRM Primetime :

* `KeyServer.ConfigRoot` - Ce répertoire contient tous les fichiers de configuration pour le serveur de clé DRM Primetime. Pour plus d’informations sur le contenu de ces fichiers, voir [Fichiers de configuration du serveur clés](#key-server-configuration-files). Si elle n’est pas définie, la valeur par défaut est [!DNL CATALINA_BASE/keyserver].

* `KeyServer.LogRoot` - Il s’agit d’un répertoire de journaux qui contient les journaux d’application iOS Key Server. Si elle n’est pas définie, la valeur par défaut est la même que `KeyServer.ConfigRoot`

* `XboxKeyServer.LogRoot` - Il s’agit d’un répertoire de journaux qui contient les journaux d’application du serveur Xbox Key. Si elle n’est pas définie, la valeur par défaut est la même que `KeyServer.ConfigRoot`.

Si vous utilisez [!DNL catalina.bat] ou [!DNL catalina.sh] Pour démarrer Tomcat, ces propriétés système peuvent facilement être définies à l’aide de la propriété `JAVA_OPTS` Variable d’environnement. Toutes les options Java définies ici seront utilisées au démarrage de Tomcat. Par exemple, définissez :

```
JAVA_OPTS=-DKeyServer.ConfigRoot=”absolute-path-to-config-folder” 
  -DKeyServer.LogRoot=”absolute-path-to-log-folder”
```

## Informations d’identification DRM Primetime {#primetime-drm-credentials}

Pour traiter les demandes clés des clients Primetime DRM iOS et Xbox 360, le serveur de clé Primetime DRM doit être configuré avec un ensemble d’informations d’identification émises par Adobe. Ces informations d’identification peuvent être stockées dans PKCS#12 ( [!DNL .pfx]) ou sur un module HSM.

La variable [!DNL .pfx] Les fichiers peuvent être localisés n’importe où, mais pour faciliter la configuration, Adobe recommande de placer la variable [!DNL .pfx] dans le répertoire de configuration du client. Pour plus d’informations, voir [Fichiers de configuration du serveur clés](#key-server-configuration-files).

### Configuration HSM {#section_13A19E3E32934C5FA00AEF621F369877}

Si vous choisissez d’utiliser un HSM pour stocker les informations d’identification de votre serveur, vous devez charger les clés privées et les certificats sur le HSM et créer une *pkcs11.cfg* fichier de configuration. Ce fichier doit se trouver dans la variable *KeyServer.ConfigRoot* répertoire . Voir `<Primetime DRM Key Server>/configs` pour un exemple de fichier de configuration PKCS 11. Pour plus d’informations sur le format de [!DNL pkcs11.cfg], consultez la documentation du fournisseur Sun PKCS11 .

Pour vérifier que vos fichiers de configuration HSM et Sun PKCS11 sont correctement configurés, vous pouvez utiliser la commande suivante à partir du répertoire où la variable [!DNL pkcs11.cfg] Le fichier se trouve ( [!DNL keytool] est installé avec Java JRE et JDK) :

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

Si vos informations d’identification s’affichent dans la liste, le module HSM est correctement configuré et le serveur de clés pourra accéder aux informations d’identification.

## Fichiers de configuration du serveur clés {#key-server-configuration-files}

Le serveur de clé DRM Primetime requiert deux types de fichiers de configuration :

* un fichier de configuration global, [!DNL flashaccess-keyserver-global.xml]
* Un fichier de configuration du client pour chaque tenant, [!DNL flashaccess-keyserver-tenant.xml]

Si des modifications sont apportées aux fichiers de configuration, le serveur doit être redémarré pour que les modifications soient prises en compte.

Pour éviter de rendre les mots de passe disponibles en texte clair dans les fichiers de configuration, tous les mots de passe spécifiés dans les fichiers de configuration globale et client doivent être chiffrés. Pour plus d’informations sur le chiffrement des mots de passe, voir [*Scrambler de mot de passe* in *Utilisation du serveur DRM Primetime pour la diffusion en continu protégée*](../protected-streaming/understanding-deployment/drm-for-protected-streaming-utilities/password-scrambler.md).

## Structure du répertoire de configuration {#configuration-directory-structure}

Les répertoires de configuration présentent la structure suivante :

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

La variable [!DNL flashaccess-keyserver-global.xml] Le fichier de configuration contient les paramètres qui s’appliquent à tous les clients du serveur de clés. Ce fichier doit se trouver dans `KeyServer.ConfigRoot`. Voir [!DNL configs] pour un exemple de fichier de configuration global. Le fichier de configuration global comprend les éléments suivants :

* Journalisation : indique le niveau de journalisation et la fréquence à laquelle les fichiers journaux sont roulés.
* Mot de passe HSM : requis uniquement si un HSM est utilisé pour stocker les informations d’identification du serveur.

Consultez les commentaires dans l’exemple de fichier de configuration global situé dans `<Primetime DRM Key Server>/configs` pour plus d’informations.

## Fichiers de configuration du client {#tenant-configuration-files}

La variable [!DNL flashaccess-ioskeyserver-tenant.xml] et [!DNL flashaccess-xboxkeyserver-tenant.xml] Les fichiers de configuration contiennent des paramètres qui s’appliquent à un client spécifique du serveur de clés DRM Primetime. Chaque client possède sa propre instance de ces fichiers de configuration situés dans [!DNL <KeyServer.ConfigRoot>/faxsks/tenants/tenantname]. Voir [!DNL configs/faxsks/tenants/sampletenant] pour un exemple de fichier de configuration du client.

Vous pouvez spécifier tous les chemins d’accès aux fichiers dans le fichier de configuration du client sous la forme de chemins d’accès absolus ou de chemins d’accès relatifs au répertoire de configuration du client ( [!DNL <KeyServer.ConfigRoot>/faxsks/tenants/tenantname]).

Tous les fichiers de configuration du client incluent :

* Informations d’identification du serveur de clés : spécifie une ou plusieurs informations d’identification du serveur de clés (certificat et clé privée) émises par l’Adobe. Peut être spécifié en tant que chemin d’accès à un [!DNL .pfx] fichier et mot de passe, ou alias des informations d’identification stockées sur un HSM. Plusieurs informations d’identification de ce type peuvent être spécifiées ici, comme les chemins d’accès aux fichiers ou les alias clés, ou les deux.

La variable **iOS** Le fichier de configuration du client comprend :

* Fenêtre de remise de clé : (facultatif) spécifie la fenêtre de validité de l’horodatage de la demande de diffusion clé (en secondes). La valeur par défaut est de 500 secondes.

La variable **Xbox 360** Le fichier de configuration du client comprend :

* Informations d’identification XSTS : indique les informations d’identification du développeur d’applications utilisées pour déchiffrer les jetons XSTS.
* Certificat de signature XSTS : indique le certificat utilisé pour vérifier la signature sur les jetons XSTS.
* Liste autorisée Packager : certificats Packager approuvés par le serveur de clés. S’il n’existe aucun certificat de packager contenu dans la liste, tous les certificats de packager seront approuvés.

## Fichiers de log {#log-files}

Les fichiers journaux générés par l’application Primetime DRM Key Server ( [!DNL flashaccess-ioskeyserver_*.log] et [!DNL flashaccess-xboxkeyserver_*.log]) se trouve dans le répertoire spécifié par `KeyServer.LogRoot`.

Les fichiers journaux se distinguent par le type de client. Il existe deux journaux par type de client :

* Un *journal d&#39;accès* - Surveille les requêtes et les réponses uniquement.
* A *journal contextuel* - Contient des messages d’erreur détaillés et des traces de pile.

## Démarrage du serveur de clés {#starting-the-key-server}

Pour démarrer le serveur de clés, démarrez Tomcat.
