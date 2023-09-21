---
description: Vous pouvez sélectionner les options de chiffrement suivantes lorsque vous créez un package. Cependant, vous ne pouvez pas modifier les options de chiffrement lors de l’acquisition d’une licence.
title: Rotation des clés
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 0%

---

# Rotation des clés {#key-rotation}

Vous pouvez sélectionner les options de chiffrement suivantes lorsque vous créez un package. Cependant, vous ne pouvez pas modifier les options de chiffrement lors de l’acquisition de la licence :

Lors du conditionnement, le contenu est généralement chiffré à l’aide de la clé de chiffrement de contenu (CEK). Le client obtient une licence contenant le CEK pour utiliser le contenu.

Lorsque vous activez la rotation des clés, la clé de rotation est utilisée pour chiffrer le contenu. La clé peut être modifiée de sorte que chaque clé de rotation ne soit utilisée que pour chiffrer une partie du contenu. Les clés de rotation sont protégées à l’aide de la clé de chiffrement du contenu, et le client obtient toujours une seule licence contenant le CEK pour consommer le contenu.

L’implémentation du service de package peut contrôler la clé de chiffrement du contenu et les clés de rotation utilisées, ainsi que la fréquence à laquelle les clés de rotation changent.

>[!NOTE]
>
>Le contenu empaqueté à l’aide de la rotation clé ne peut être lu que sur les clients DRM Primetime version 3.0 ou ultérieure. Les clients plus anciens peuvent avoir besoin d’une mise à niveau pour lire ce contenu.
