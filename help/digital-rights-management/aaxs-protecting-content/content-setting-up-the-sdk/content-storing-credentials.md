---
title: Stockage des informations d’identification
description: Stockage des informations d’identification
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# Stockage des informations d’identification{#storing-credentials}

Le SDK prend en charge plusieurs méthodes de stockage des informations d’identification (un certificat de clé publique et sa clé privée associée), notamment sur un fichier HSM ou PKCS12. Les informations d’identification sont utilisées lorsque la clé privée est requise (par exemple, pour que le module signe les métadonnées ou pour que le serveur de licences décrypte les données chiffrées avec le serveur de licences ou la clé publique Transport). Les clés privées doivent être surveillées de près pour garantir la sécurité de votre contenu et de votre serveur de licences. PKCS12 est un format standard pour un fichier contenant des informations d’identification chiffrées à l’aide d’un mot de passe. L’extension de fichier .pfx est généralement utilisée pour les fichiers de ce format.

>[!NOTE]
>
>Adobe recommande d’utiliser un HSM pour une sécurité maximale. Pour plus d’informations, voir les Instructions de déploiement sécurisé pour l’accès aux Adobes .

>[!NOTE]
>
>Depuis Java1.7, Sun Java 64 bits pour Windows ne prend pas en charge les interfaces PKCS11 requises par Adobe Access DRM pour communiquer avec les périphériques HSM. Si vous prévoyez d’utiliser un HSM, utilisez une version 32 bits de Java ou utilisez un JDK qui prend en charge les interfaces PKCS11 complètes.

Vous pouvez conserver une clé privée sur un module de sécurité matérielle (HSM) et utiliser le SDK pour transmettre les informations d’identification que vous obtenez du HSM. Pour utiliser des informations d’identification stockées sur un HSM, utilisez un fournisseur JCE qui peut communiquer avec un HSM pour obtenir une gestion de la clé privée. Ensuite, transmettez la clé privée, le nom du fournisseur et le certificat contenant la clé publique à `ServerCredentialFactory.getServerCredential()`.

Le fournisseur SunPKCS11 est un exemple de fournisseur JCE qui peut être utilisé pour accéder à une clé privée sur un HSM (voir la documentation Sun Java pour obtenir des instructions sur l’utilisation de ce fournisseur). Certains HSM sont également fournis avec un SDK Java qui inclut un fournisseur JCE.

PEM et DER sont deux manières de coder un certificat de clé publique. PEM est un encodage de base 64 et DER est un encodage binaire. Les fichiers de certificat utilisent généralement l’extension .cer, .pem. ou .der. Les certificats sont utilisés dans les endroits où seule la clé publique est requise. Si un composant nécessite uniquement la clé publique pour fonctionner, il est préférable de lui fournir le certificat au lieu d’un fichier d’informations d’identification ou PKCS12.
