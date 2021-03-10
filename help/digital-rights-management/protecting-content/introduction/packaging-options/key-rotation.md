---
description: 'Vous pouvez sélectionner les options de chiffrement suivantes lorsque vous créez un pack. Cependant, vous ne pouvez pas modifier les options de chiffrement lors de l’acquisition de la licence. '
title: Rotation clé
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 0%

---


# Rotation des clés {#key-rotation}

Vous pouvez sélectionner les options de chiffrement suivantes lorsque vous créez un pack. Cependant, vous ne pouvez pas modifier les options de chiffrement lors de l’acquisition de la licence :

Lors de l’assemblage, le contenu est généralement chiffré à l’aide de la clé de chiffrement de contenu (CEK). Le client obtient une licence contenant le CEK pour consommer le contenu.

Lorsque vous activez la rotation des clés, la clé de rotation est utilisée pour chiffrer le contenu et la clé peut être modifiée de sorte que chaque clé de rotation ne soit utilisée que pour chiffrer une partie du contenu. Les clés de rotation sont protégées à l’aide de la clé de chiffrement de contenu et le client obtient toujours une licence unique contenant le CEK pour consommer le contenu.

L’implémentation de Packager peut contrôler la clé de chiffrement de contenu et les clés de rotation utilisées, ainsi que la fréquence de modification des clés de rotation.

>[!NOTE]
>
>Le contenu assemblé à l’aide de la rotation clé ne peut être lu que sur les clients DRM Primetime version 3.0 ou ultérieure. Il se peut que les clients plus âgés aient besoin d’effectuer la mise à niveau pour lire ce contenu.