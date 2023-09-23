---
title: Stockage des informations d’identification
description: Stockage des informations d’identification
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# Stockage des informations d’identification{#storing-credentials}

Le SDK DRM Primetime prend en charge différentes méthodes de stockage des informations d’identification, notamment l’utilisation d’un module de sécurité matérielle (HSM) ou sous la forme d’un fichier PKCS12. Le SDK utilise des informations d’identification (certificat de clé publique et clé privée associée) lorsque la clé privée est requise. Par exemple, le service de package utilise des informations d’identification pour signer les métadonnées ; le serveur de licences utilise des informations d’identification pour décrypter les données chiffrées à l’aide de la clé du serveur de licences ou du service de transport public.

Vous devez surveiller de près les clés privées pour garantir la sécurité de votre contenu et de votre serveur de licences. PKCS12 est un format de fichier d’archive standard permettant de stocker les informations d’identification chiffrées avec un mot de passe. (Vous pouvez également chiffrer et signer le fichier PKCS12 lui-même.) L’extension de fichier [!DNL .pfx] est généralement utilisé pour les fichiers qui prennent en charge ce format.

>[!NOTE]
>
>Adobe recommande d’utiliser un HSM pour une sécurité maximale.
>
>Voir *Instructions de déploiement sécurisé DRM Adobe Primetime* guide.

>[!NOTE]
>
>Depuis Java 1.7, Sun Java 64 bits pour Windows ne prend plus en charge les interfaces PKCS11 requises par Primetime DRM pour la communication avec les périphériques HSM. Si vous prévoyez d’utiliser un HSM, vous devez utiliser une version 32 bits de Java, ou utiliser un JDK qui prend en charge les interfaces PKCS11 complètes.

Vous pouvez conserver une clé privée sur un HSM et utiliser le SDK DRM Primetime pour transmettre les informations d’identification que vous obtenez du HSM. Si vous souhaitez utiliser des informations d’identification stockées sur un HSM, vous devez utiliser un fournisseur JCE qui peut communiquer avec un HSM pour obtenir une gestion de la clé privée. Ensuite, vous devez transmettre la clé privée, le nom du fournisseur et le certificat qui incluent la clé publique à `ServerCredentialFactory.getServerCredential()`.

Le fournisseur SunPKCS11 représente un exemple de fournisseur JCE que vous pouvez utiliser pour accéder à une clé privée sur un HSM. Certains HSM sont également inclus avec un SDK Java fourni avec un fournisseur JCE.

Consultez la documentation Sun Java pour obtenir des instructions sur l’utilisation de ce fournisseur.

PEM et DER sont des moyens de coder un certificat de clé publique. PEM est un encodage de base 64 et DER est un encodage binaire. Les fichiers de certificat utilisent généralement l’extension [!DNL .cer], [!DNL .pem], ou [!DNL .der]. Les certificats sont utilisés lorsqu’une seule clé publique est requise. Si un composant nécessite uniquement la clé publique pour fonctionner, il est recommandé de lui fournir le certificat au lieu d’un fichier d’informations d’identification ou PKCS12.
