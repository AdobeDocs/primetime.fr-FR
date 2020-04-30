---
seo-title: Stockage des informations d’identification
title: Stockage des informations d’identification
uuid: a9e9db72-c921-4c28-ad1d-3fd3c2283f14
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Stockage des informations d’identification{#storing-credentials}

Le SDK DRM de Primetime prend en charge différentes méthodes de stockage des informations d’identification, notamment l’utilisation d’un module de sécurité matérielle (HSM) ou d’un fichier PKCS12. Le SDK utilise des informations d’identification (certificat de clé publique et clé privée associée) lorsque la clé privée est requise. Par exemple, le gestionnaire de package utilise des informations d’identification pour signer les métadonnées ; le serveur de licences utilise des informations d’identification pour déchiffrer les données chiffrées à l’aide de la clé publique License Server ou Transport.

Vous devez surveiller de près les clés privées pour assurer la sécurité de votre contenu et de votre serveur de licences. PKCS12 est un format de fichier d’archive standard permettant de stocker les informations d’identification chiffrées avec un mot de passe. (Vous pouvez également chiffrer et signer le fichier PKCS12 lui-même.) L’extension de fichier [!DNL .pfx] est généralement utilisée pour les fichiers qui prennent en charge ce format.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Adobe recommande d’utiliser un HSM pour une sécurité maximale.
>
>Consultez le guide *Adobe Primetime DRM Secure Deployment Guidelines* .

>[!NOTE] {importance=&quot;high&quot;}
>
>Depuis Java 1.7, Sun Java 64 bits pour Windows ne prend plus en charge les interfaces PKCS11 requises par Primetime DRM pour la communication avec les périphériques HSM. Si vous prévoyez d’utiliser un module HSM, vous devez utiliser une version 32 bits de Java ou un JDK prenant en charge les interfaces PKCS11 complètes.

Vous pouvez conserver une clé privée sur un module HSM et utiliser le SDK DRM Primetime pour transmettre les informations d’identification que vous obtenez du module HSM. Si vous souhaitez utiliser des informations d’identification stockées sur un HSM, vous devez utiliser un fournisseur JCE qui peut communiquer avec un HSM pour obtenir une poignée sur la clé privée. Ensuite, vous devez transmettre à `ServerCredentialFactory.getServerCredential()`la clé privée, le nom du fournisseur et le certificat qui comprend la clé publique.

Le fournisseur SunPKCS11 représente un exemple de fournisseur JCE que vous pouvez utiliser pour accéder à une clé privée sur un module HSM. Certains modules HSM sont également inclus dans un SDK Java fourni avec un fournisseur JCE.

Consultez la documentation Sun Java pour savoir comment utiliser ce fournisseur.

PEM et DER permettent de coder un certificat de clé publique. PEM est un encodage de base 64 et DER est un encodage binaire. Les fichiers de certificat utilisent généralement l’extension [!DNL .cer], [!DNL .pem]ou [!DNL .der]. Les certificats sont utilisés lorsque seule une clé publique est requise. Si un composant nécessite uniquement la clé publique pour fonctionner, il est recommandé de fournir ce composant avec le certificat au lieu d’un fichier d’informations d’identification ou PKCS12.
