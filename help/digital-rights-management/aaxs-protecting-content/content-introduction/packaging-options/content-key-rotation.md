---
description: Les options de chiffrement suivantes sont sélectionnées au moment de la création du pack et ne peuvent pas être modifiées lors de l’acquisition de la licence.
title: Rotation clé
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---


# Rotation de clé{#key-rotation}

Les options de chiffrement suivantes sont sélectionnées au moment de la création du pack et ne peuvent pas être modifiées lors de l’acquisition de la licence.

Lors de l’assemblage, le contenu est généralement chiffré à l’aide de la clé de chiffrement de contenu (CEK) et le client obtient une licence contenant le CEK afin de consommer le contenu. Lorsque la rotation des clés est activée, la clé de rotation est utilisée pour chiffrer le contenu et la clé peut être modifiée afin que chaque clé de rotation ne soit utilisée que pour chiffrer une partie du contenu. Les clés de rotation sont protégées à l’aide de la clé de chiffrement de contenu et le client obtient toujours une licence unique contenant le CEK afin de consommer le contenu. L’implémentation de Packager peut contrôler la clé de chiffrement de contenu et les clés de rotation utilisées, ainsi que la fréquence de modification des clés de rotation.

Le contenu compressé à l&#39;aide de la rotation de clé ne peut être lu que sur les clients Adobe Access versions 3.0 et ultérieures. Les clients plus âgés doivent effectuer la mise à niveau pour lire ce contenu.
