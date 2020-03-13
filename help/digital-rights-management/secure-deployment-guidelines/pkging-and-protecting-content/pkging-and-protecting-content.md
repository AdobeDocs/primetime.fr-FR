---
description: Les informations sur l'emballage et la protection du contenu vous permettent de protéger votre contenu.
seo-description: Les informations sur l'emballage et la protection du contenu vous permettent de protéger votre contenu.
seo-title: Emballage et protection du contenu
title: Emballage et protection du contenu
uuid: 9bf89f86-082e-40f9-8deb-c9774a9d8e02
translation-type: tm+mt
source-git-commit: a33e1f290fcf78e6f131910f6037f4803f7be98d

---


# Assemblage et protection de contenu {#packaging-protecting-content}

Les informations sur l&#39;emballage et la protection du contenu vous permettent de protéger votre contenu.

## Sécurisation du serveur {#securing-the-server}

Vous devez sécuriser physiquement l’ordinateur sur lequel se produisent la gestion des stratégies et l’assemblage du contenu.

Pour plus d’informations, voir Sécurité [physique et accès](../../secure-deployment-guidelines/physical-sec-and-access.md).

Si votre implémentation de création de package de contenu nécessite une connectivité réseau, vous devez renforcer votre système d’exploitation et mettre en oeuvre une solution de pare-feu appropriée. Pour plus d’informations, voir Topologie [](../../secure-deployment-guidelines/overview/network-topology.md)réseau.

## Assemblage sécurisé du contenu {#securely-packaging-content}

Le fichier de configuration de l’outil de ligne de commande Adobe Primetime DRM Media Packager requiert des informations d’identification PKCS12 utilisées lors de la création de packs.

Dans les outils de la version de commande de l’implémentation des références, le mot de passe du fichier d’informations d’identification PKCS12 est stocké dans le `flashaccess.properties` fichier en clair. Pour cette raison, faites très attention lorsque vous sécurisez l’ordinateur qui héberge ce fichier et assurez-vous que l’ordinateur est dans un   sécurisé. Pour plus d’informations, voir Sécurité [physique et accès](../../secure-deployment-guidelines/physical-sec-and-access.md).

Le gestionnaire de package utilise également les certificats de transport du serveur de licences et du serveur de licences, et l’intégrité et la confidentialité de ces informations doivent être protégées. Seules les entités autorisées doivent être autorisées à utiliser l’outil d’emballage. Si vos clés privées sont compromises, informez Adobe Systems Incorporated immédiatement afin que le certificat puisse être révoqué.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>L’API vous permet d’utiliser la même clé pour plusieurs éléments de contenu. Pour garantir un niveau de sécurité optimal, vous devez uniquement utiliser cette fonctionnalité pour le contenu FMS à débit multiple. N’utilisez pas la même clé pour plusieurs fichiers qui représentent un contenu différent.

L’API de création de package DRM de Primetime émet des avertissements dans certaines conditions. Vérifiez ces avertissements pour déterminer si vos fichiers ont bien été chiffrés. Les messages d’avertissement peuvent être l’un des suivants :

* La stratégie a expiré et une balise ou un suivi non reconnu ne peut pas être chiffré.
* Les fragments de film ne peuvent pas être chiffrés et les références à l’intérieur de ces fragments peuvent être incorrectes.
* Les métadonnées ne peuvent pas être chiffrées.

Si le contenu est compressé à l’aide d’une stratégie avec des attributs incorrects, la stratégie doit être mise à jour. La stratégie mise à jour doit être mise à la disposition du serveur de licences par le biais d’un de mise à jour de stratégie ou d’un autre mécanisme de  de. Certains attributs de stratégie ne peuvent pas être modifiés une fois la stratégie créée. Si ces attributs sont incorrects, retirez le contenu des sites de distribution, révoquez la stratégie afin qu’aucune licence ultérieure ne puisse être accordée et chiffrez à nouveau le contenu.

Une fois l’emballage terminé, la clé d’emballage est récupérée et n’est pas explicitement détruite. Par conséquent, la clé d’emballage reste présente en mémoire pendant un certain temps. Vous devez vous protéger contre tout accès non autorisé à l’ordinateur et vous assurer de ne pas exposer de fichiers, tels que des vidages de base, qui pourraient révéler ces informations.

## Stockage sécurisé des stratégies {#securely-storing-policies}

Le SDK DRM d’Adobe Primetime vous permet de développer des applications qui peuvent être utilisées dans le cadre de la création de packages de contenu et de stratégies.

Lorsque vous créez ces applications, vous pouvez autoriser certains utilisateurs à créer et modifier des stratégies et limiter les autres utilisateurs à appliquer uniquement des stratégies existantes au contenu. Vous devez mettre en oeuvre les  nécessaires et créer des comptes d’utilisateurs avec des privilèges différents pour la création de stratégies et l’application de stratégies.

Les stratégies ne sont signées ni protégées contre toute modification tant qu’elles ne sont pas utilisées dans l’emballage. Si vous pensez que les utilisateurs de l’outil de création de package peuvent modifier des stratégies, signez-les afin de vous assurer qu’elles ne peuvent pas être modifiées.

Pour plus d’informations sur la création d’applications à l’aide du SDK, voir les API DRM Primetime sur les références [API Primetime d’](https://help.adobe.com/en_US/primetime/api/index.html#api-Adobe_Primetime_API_References)API.

## Chiffrement asymétrique des clés {#asymmetric-key-encryption}

Le chiffrement asymétrique des clés, également appelé chiffrement des clés publiques, utilise des paires de clés. Une clé est pour le chiffrement, et l&#39;autre pour le déchiffrement.

La clé de déchiffrement, ou la clé *`private key`*, est gardée secrète ; la clé de chiffrement, ou la clé *`public key`*, est mise à la disposition de toute personne autorisée à chiffrer du contenu. Toute personne ayant accès à la clé publique peut chiffrer du contenu. Cependant, seule une personne ayant accès à la clé privée peut déchiffrer le contenu. La clé privée ne peut pas être reconstruite à partir de la clé publique.

Lorsque vous assemblez du contenu, la clé publique du serveur de licences est utilisée pour chiffrer la clé de chiffrement de contenu (CEK) dans les métadonnées DRM. Vous devez vous assurer que seul le serveur de licences a accès à la clé privée du serveur de licences. Si quelqu&#39;un d&#39;autre a la clé, il peut déchiffrer et  le contenu.

>[!CAUTION]
>
>Assurez-vous d’obtenir le certificat du serveur de licences qui comprend la clé publique auprès d’une source approuvée. Vous pouvez ainsi vous assurer qu’il s’agit de la clé du serveur de licences et non d’une clé publique non fiable. Si les attaquants devaient substituer leur clé publique à la clé du serveur de licences, ils pourraient déchiffrer votre contenu.

Pour plus d’informations sur la manière de compresser du contenu, voir [Utilisation du SDK DRM d’Adobe Primetime pour la protection du contenu](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_protecting_content.pdf).