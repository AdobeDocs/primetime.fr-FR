---
title: Empilement sécurisé du contenu
description: Empilement sécurisé du contenu
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# Empilement sécurisé du contenu {#securely-packaging-content}

Le fichier de configuration de l’outil de ligne de commande Adobe Access Media Packager nécessite des informations d’identification PKCS12 utilisées lors du conditionnement.

Dans les outils de ligne de commande de mise en oeuvre de référence, le mot de passe du fichier d’informations d’identification PKCS12 est stocké dans le fichier flashaccess.properties en texte clair. Pour cette raison, soyez très prudent lorsque vous sécurisez l’ordinateur hébergeant ce fichier et assurez-vous qu’il se trouve dans un environnement sécurisé. (Voir [Sécurité physique et accès](../../aaxs-secure-deployment-guidelines/physical-sec-and-access.md)).

Il utilise également les certificats de transport du serveur de licences et du serveur de licences. L&#39;intégrité et la confidentialité de ces informations doivent être protégées. Seules les entités autorisées doivent être autorisées à utiliser le service de package. Si l’une de vos clés privées est compromise, informez immédiatement Adobe Systems Incorporated afin que le certificat puisse être révoqué.

>[!NOTE]
>
>L’API vous permet d’utiliser la même clé pour plusieurs éléments de contenu. Pour garantir le niveau de sécurité le plus élevé, nous recommandons que cette fonctionnalité ne soit utilisée que pour le contenu FMS à débit multi-bits. Il n’est pas recommandé d’utiliser la même clé pour plusieurs fichiers représentant un contenu différent.

L’API Adobe Access Packaging génère des avertissements dans certaines conditions. Vous devez consulter ces avertissements pour déterminer si vos fichiers ont bien été chiffrés. Les messages d’avertissement peuvent indiquer que la stratégie a expiré, qu’une balise ou un suivi non reconnu ne sera pas chiffré, que les fragments de film ne seront pas chiffrés (et que les références à l’intérieur de ces fragments peuvent devenir invalides) et que les métadonnées ne seront pas chiffrées.

Si le contenu est compilé à l’aide d’une stratégie avec des attributs incorrects, la stratégie doit être mise à jour et la stratégie mise à jour doit être mise à disposition du serveur de licences par le biais d’une liste de mises à jour de stratégie ou d’un autre mécanisme pour fournir la stratégie mise à jour au serveur. Certains attributs de stratégie ne peuvent pas être modifiés une fois la stratégie créée. Si ces attributs sont incorrects, récupérez le contenu des sites de distribution, révoquez la stratégie afin qu’aucune licence future ne puisse être accordée et chiffrez à nouveau le contenu.

Une fois l&#39;emballage terminé, la clé de l&#39;emballage n&#39;est pas explicitement détruite, mais elle est nettoyée. Par conséquent, la clé de package reste présente dans la mémoire pendant un certain temps ; vous devez vous protéger contre tout accès non autorisé à la machine et prendre des mesures pour vous assurer que vous n’exposez aucun fichier, tel que les vidages principaux, qui pourrait révéler ces informations.
