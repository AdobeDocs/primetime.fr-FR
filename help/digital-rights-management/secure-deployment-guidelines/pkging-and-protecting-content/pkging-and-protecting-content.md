---
description: Les informations sur le conditionnement et la protection du contenu vous permettent de protéger votre contenu.
title: Compilation et protection du contenu
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 0%

---

# Modules et protection du contenu {#packaging-protecting-content}

Les informations sur le conditionnement et la protection du contenu vous permettent de protéger votre contenu.

## Sécurisation du serveur {#securing-the-server}

Vous devez sécuriser physiquement l’ordinateur sur lequel se produit la gestion des stratégies et le conditionnement du contenu.

Pour plus d’informations, voir [Sécurité physique et accès](../../secure-deployment-guidelines/physical-sec-and-access.md).

Si la mise en oeuvre de votre package de contenu nécessite une connectivité réseau, vous devez renforcer votre système d’exploitation et mettre en oeuvre une solution de pare-feu appropriée. Pour plus d’informations, voir [Topologie réseau](../../secure-deployment-guidelines/overview/network-topology.md).

## Empilement sécurisé du contenu {#securely-packaging-content}

Le fichier de configuration de l’outil de ligne de commande Adobe Primetime DRM Media Packager nécessite des informations d’identification PKCS12 utilisées lors du conditionnement.

Dans les outils de mise en oeuvre de la commande, le mot de passe du fichier d’informations d’identification PKCS12 est stocké dans le `flashaccess.properties` en texte clair. Pour cette raison, soyez très prudent lorsque vous sécurisez l’ordinateur hébergeant ce fichier et assurez-vous que l’ordinateur est dans un environnement sécurisé. Pour plus d’informations, voir [Sécurité physique et accès](../../secure-deployment-guidelines/physical-sec-and-access.md).

Il utilise également les certificats de transport du serveur de licences et du serveur de licences, et l’intégrité et la confidentialité de ces informations doivent être protégées. Seules les entités autorisées doivent être autorisées à utiliser le service de package. Si vos clés privées sont compromises, informez immédiatement Adobe Systems Incorporated afin que le certificat puisse être révoqué.

>[!NOTE]
>
>L’API vous permet d’utiliser la même clé pour plusieurs éléments de contenu. Pour garantir le niveau de sécurité le plus élevé, utilisez cette fonctionnalité uniquement pour le contenu FMS à débit multi-bits. N’utilisez pas la même clé pour plusieurs fichiers qui représentent un contenu différent.

L’API Primetime DRM Packaging émet des avertissements dans certaines conditions. Consultez ces avertissements pour déterminer si vos fichiers ont bien été chiffrés. Les messages d’avertissement peuvent être les suivants :

* La stratégie a expiré et une balise ou un suivi non reconnu ne peut pas être chiffré.
* Les fragments de film ne peuvent pas être chiffrés et les références qu’ils contiennent peuvent être incorrectes.
* Les métadonnées ne peuvent pas être chiffrées.

Si le contenu est empaqueté à l’aide d’une stratégie avec des attributs incorrects, la stratégie doit être mise à jour. La stratégie mise à jour doit être mise à disposition du serveur de licences par le biais d’une liste de mise à jour de stratégie ou d’un autre mécanisme de diffusion. Certains attributs de stratégie ne peuvent pas être modifiés une fois la stratégie créée. Si ces attributs sont incorrects, récupérez le contenu des sites de distribution, révoquez la stratégie afin qu’aucune licence future ne puisse être accordée et chiffrez à nouveau le contenu.

Une fois l&#39;emballage terminé, la clé de l&#39;emballage est nettoyée et n&#39;est pas explicitement détruite. Par conséquent, la clé d&#39;emballage reste présente dans la mémoire pendant un certain temps. Vous devez vous protéger contre tout accès non autorisé à la machine et vous assurer de ne pas exposer les fichiers, tels que les images mémoire de base, susceptibles de révéler ces informations.

## Stockage sécurisé des stratégies {#securely-storing-policies}

Le SDK DRM Adobe Primetime permet de développer des applications qui peuvent être utilisées dans le conditionnement de contenu et la création de stratégies.

Lorsque vous créez ces applications, vous pouvez autoriser certains utilisateurs à créer et modifier des stratégies, et limiter les autres utilisateurs à appliquer uniquement des stratégies existantes au contenu. Vous devez mettre en oeuvre les contrôles d’accès nécessaires et créer des comptes d’utilisateurs avec des privilèges différents pour la création et l’application de stratégies.

Les stratégies ne sont pas signées ni protégées de la modification tant qu’elles ne sont pas utilisées dans le package. Si vous pensez que les utilisateurs de l’outil de conditionnement peuvent modifier des stratégies, signez-les pour vous assurer que les stratégies ne peuvent pas être modifiées.

Pour plus d’informations sur la création d’applications avec le SDK, voir API DRM Primetime sur [Références API Primetime](https://help.adobe.com/en_US/primetime/api/index.html#api-Adobe_Primetime_API_References).

## Cryptage de clé asymétrique {#asymmetric-key-encryption}

Le cryptage de clé asymétrique, également appelé cryptage de clé publique, utilise des paires de clés. Une clé est pour le cryptage, l’autre pour le décryptage.

La clé de décryptage ou la variable *`private key`*, est tenu secret ; la clé de chiffrement, ou la variable *`public key`*, est mis à la disposition de toute personne autorisée à chiffrer du contenu. Toute personne ayant accès à la clé publique peut chiffrer du contenu. Cependant, seule une personne ayant accès à la clé privée peut déchiffrer le contenu. La clé privée ne peut pas être reconstruite à partir de la clé publique.

Lorsque vous compressez du contenu, la clé publique du serveur de licences est utilisée pour chiffrer la clé de chiffrement de contenu (CEK) dans les métadonnées DRM. Vous devez vous assurer que seul le serveur de licences a accès à la clé privée du serveur de licences. Si quelqu’un d’autre dispose de la clé, il peut déchiffrer et afficher le contenu.

>[!CAUTION]
>
>Assurez-vous d’obtenir le certificat du serveur de licences qui comprend la clé publique auprès d’une source de confiance. Ainsi, vous pouvez vous assurer qu’il s’agit de la clé du serveur de licences et non d’une clé publique non fiable. Si les attaquants devaient substituer leur clé publique à la clé du serveur de licences, ils pourraient déchiffrer votre contenu.

Pour plus d’informations sur la création de package de contenu, voir [Utilisation du SDK Adobe Primetime DRM pour la protection du contenu](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_protecting_content.pdf).
