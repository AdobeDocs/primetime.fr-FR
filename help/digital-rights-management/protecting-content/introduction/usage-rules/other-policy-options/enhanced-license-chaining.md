---
title: Amélioration de la chaîne de licence
description: Amélioration de la chaîne de licence
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# Amélioration de la chaîne de licence {#enhanced-license-chaining}

Vous pouvez utiliser le chaînage de licences amélioré pour mettre à jour une licence en utilisant une licence racine parente pour la mise à jour par lots des licences.

Primetime DRM 2.0 prend en charge le chaînage de licences dans lequel les licences feuille et racine sont liées à une machine spécifique. Primetime DRM 3.0 et versions ultérieures prend en charge le chaînage de licences améliorées, dans lequel une feuille est liée à une licence racine, et seule la licence racine est liée à une machine ou un domaine spécifique. Le chaînage de licences amélioré prend en charge l’incorporation d’une licence feuille avec le contenu, et le client ne doit acquérir la licence racine du serveur de licences que pour pouvoir consommer le contenu protégé.

Si vous souhaitez activer un chaînage de licences amélioré, vous devez attribuer une clé de chiffrement racine à une stratégie DRM Primetime. La clé de chiffrement racine est utilisée pour lier de manière cryptographique la licence feuille à la licence racine.

>[!NOTE]
>
>Le chaînage de licences amélioré est pris en charge par les clients Primetime DRM version 3.0 ou ultérieure. Si un client plus âgé demande une licence pour du contenu prenant en charge le chaînage de licences amélioré, le serveur de licences peut toujours émettre une licence pour ce client en utilisant le chaînage de licences pris en charge par Primetime DRM 2.0.

Exemple de cas d’utilisation : utilisez cette option pour mettre à jour les licences liées en téléchargeant une seule licence racine. Par exemple, implémentez des modèles d’abonnement dans lesquels le contenu peut être lu tant que l’utilisateur renouvelle l’abonnement sur une base mensuelle. L’avantage de cette approche est que les utilisateurs n’ont qu’à acquérir une seule licence pour mettre à jour toutes leurs licences d’abonnement.
