---
title: Stockage des informations d’identification
description: Stockage des informations d’identification
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---


# Stockage des informations d’identification{#storing-credentials}

Le SDK prend en charge plusieurs méthodes de stockage des informations d’identification (un certificat de clé publique et sa clé privée associée), y compris sur un HSM ou sous la forme d’un fichier PKCS12. Les informations d’identification sont utilisées lorsque la clé privée est requise (par exemple, pour que le gestionnaire de package signe les métadonnées ou pour que le serveur de licences déchiffre les données chiffrées avec le serveur de licences ou la clé publique Transport). Les clés privées doivent être surveillées de près pour garantir la sécurité de votre contenu et de votre serveur de licences. PKCS12 est un format standard pour un fichier contenant des informations d’identification chiffrées à l’aide d’un mot de passe. L&#39;extension de fichier .pfx est généralement utilisée pour les fichiers de ce format.

>[!NOTE]
>
>Adobe recommande d’utiliser un module HSM pour une sécurité maximale. Pour plus d&#39;informations, consultez les consignes de déploiement sécurisé d&#39;Accès aux Adobes.

>[!NOTE]
>
>Depuis Java1.7, Sun Java 64 bits pour Windows ne prend pas en charge les interfaces PKCS11 dont Adobe Access DRM a besoin pour communiquer avec les périphériques HSM. Si vous prévoyez d’utiliser un module HSM, utilisez une version 32 bits de Java ou utilisez un JDK qui prend en charge les interfaces PKCS11 complètes.

Vous pouvez conserver une clé privée sur un module de sécurité matérielle (HSM) et utiliser le SDK pour transmettre les informations d’identification que vous obtenez du HSM. Pour utiliser des informations d’identification stockées sur un HSM, utilisez un fournisseur JCE qui peut communiquer avec un HSM pour obtenir une poignée de la clé privée. Ensuite, transmettez à `ServerCredentialFactory.getServerCredential()` le nom de la clé privée, le nom du fournisseur et le certificat contenant la clé publique.

Le fournisseur SunPKCS11 est un exemple de fournisseur JCE qui peut être utilisé pour accéder à une clé privée sur un HSM (voir la documentation Sun Java pour obtenir des instructions sur l’utilisation de ce fournisseur). Certains HSM sont également fournis avec un SDK Java incluant un fournisseur JCE.

PEM et DER permettent de coder un certificat de clé publique de deux manières. PEM est un encodage de base 64 et DER est un encodage binaire. Les fichiers de certificat utilisent généralement l’extension .cer, .pem. ou .der. Les certificats sont utilisés dans les endroits où seule la clé publique est requise. Si un composant nécessite uniquement la clé publique pour fonctionner, il est préférable de fournir ce composant avec le certificat plutôt qu’un fichier d’informations d’identification ou PKCS12.
