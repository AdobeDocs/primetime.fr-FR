---
description: Les options de chiffrement suivantes sont sélectionnées au moment de la création du pack et ne peuvent pas être modifiées lors de l’acquisition de la licence.
seo-description: Les options de chiffrement suivantes sont sélectionnées au moment de la création du pack et ne peuvent pas être modifiées lors de l’acquisition de la licence.
seo-title: Rotation clé
title: Rotation clé
uuid: 6ee47c06-9981-4281-b10b-343f8b1e55b7
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Rotation clé{#key-rotation}

Les options de chiffrement suivantes sont sélectionnées au moment de la création du pack et ne peuvent pas être modifiées lors de l’acquisition de la licence.

Lors de l’assemblage, le contenu est généralement chiffré à l’aide de la clé de chiffrement de contenu (CEK) et le client obtient une licence contenant le CEK afin de consommer le contenu. Lorsque la rotation des clés est activée, la clé de rotation est utilisée pour chiffrer le contenu et la clé peut être modifiée afin que chaque clé de rotation ne soit utilisée que pour chiffrer une partie du contenu. Les clés de rotation sont protégées à l’aide de la clé de chiffrement de contenu et le client obtient toujours une licence unique contenant le CEK afin de consommer le contenu. L’implémentation de Packager peut contrôler la clé de chiffrement de contenu et les clés de rotation utilisées, ainsi que la fréquence de modification des clés de rotation.

Le contenu compressé à l’aide de la rotation de clé ne peut être lu que sur les clients Adobe Access versions 3.0 et ultérieures. Les clients plus âgés doivent effectuer la mise à niveau pour lire ce contenu.
