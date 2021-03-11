---
title: Emballage sécurisé de contenu
description: Emballage sécurisé de contenu
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---


# Emballage sécurisé de contenu {#securely-packaging-content}

Le fichier de configuration de l&#39;outil de ligne de commande Adobe Access Media Packager requiert des informations d&#39;identification PKCS12 utilisées lors de la création de packs.

Dans les outils de ligne de commande d’implémentation de référence, le mot de passe du fichier d’informations d’identification PKCS12 est stocké dans le fichier flashaccess.properties en clair. Pour cette raison, assurez-vous de sécuriser l&#39;ordinateur hébergeant ce fichier et assurez-vous qu&#39;il se trouve dans un environnement sécurisé. (Voir [Sécurité physique et accès](../../aaxs-secure-deployment-guidelines/physical-sec-and-access.md)).

Il utilise également les certificats License Server et License Server Transport. L&#39;intégrité et la confidentialité de ces informations doivent être protégées. Seules les entités autorisées doivent être autorisées à utiliser l&#39;emballeur. Si l’une de vos clés privées est compromise, informez immédiatement Adobe Systems Incorporated afin que le certificat puisse être révoqué.

>[!NOTE]
>
>L’API vous permet d’utiliser la même clé pour plusieurs éléments de contenu. Pour garantir le niveau de sécurité le plus élevé, nous vous recommandons de ne l’utiliser que pour le contenu FMS à débit multiple. Il n’est pas recommandé d’utiliser la même clé pour plusieurs fichiers représentant un contenu différent.

L&#39;API de création de package d&#39;accès à l&#39;Adobe émet des avertissements dans certaines conditions. Vous devez examiner ces avertissements pour déterminer si vos fichiers ont été chiffrés correctement. Les messages d’avertissement peuvent indiquer que la stratégie a expiré, qu’une balise ou un suivi non reconnu ne sera pas chiffré, que les fragments de film ne seront pas chiffrés (et que les références à l’intérieur de ces fragments peuvent devenir non valides) et que les métadonnées ne seront pas chiffrées.

Si le contenu est compressé à l’aide d’une stratégie avec des attributs incorrects, la stratégie doit être mise à jour et la stratégie mise à jour doit être rendue disponible pour le serveur de licences par le biais d’une liste de mise à jour de la stratégie ou d’un autre mécanisme permettant de fournir la stratégie mise à jour au serveur. Certains attributs de stratégie ne peuvent plus être modifiés une fois la stratégie créée. Si ces attributs sont incorrects, récupérez le contenu des sites de distribution, révoquez la stratégie afin qu’aucune licence ultérieure ne puisse être accordée et chiffrez à nouveau le contenu.

Lorsque l&#39;emballage est terminé, la clé d&#39;emballage n&#39;est pas explicitement détruite ; cependant, il s&#39;agit d&#39;une collecte de déchets. Par conséquent, la clé d&#39;emballage reste présente en mémoire pendant un certain temps ; vous devez vous protéger contre tout accès non autorisé à la machine et prendre des mesures pour vous assurer que vous n&#39;exposez aucun fichier, tel que les vidages de noyau, qui pourrait révéler ces informations.
