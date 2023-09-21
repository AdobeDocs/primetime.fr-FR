---
title: Clés de magasin
description: Clés de magasin
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---

# Clés de magasin{#store-keys}

Adobe recommande que les éditeurs de contenu stockent les clés privées cryptographiques pour la signature et le chiffrement dans un périphérique matériel sécurisé et protégé par un tampon. Les clés stockées dans un logiciel sont plus susceptibles de compromis que les clés stockées dans un matériel. Par exemple, si une clé logicielle est divulguée, la clé ou le fichier contenant la clé est généralement copié, ce qui rend difficile de détecter la brèche. Les clés stockées sur du matériel sont moins vulnérables aux compromis non détectés.

Les modules de sécurité matérielle (HSM) sont des périphériques matériels dédiés qui stockent et protègent les clés cryptographiques. Pour plus d’informations, voir *Stockage des informations d’identification* in *Utilisation du SDK Adobe Primetime DRM pour la protection du contenu*.
