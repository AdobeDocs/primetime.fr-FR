---
description: Certaines considérations de sécurité doivent être prises en compte pour le Browser TVSDK.
title: Considérations relatives à la sécurité
exl-id: bc98890a-082a-4e2d-b927-ecb3bd878de9
source-git-commit: 78be1575cc7bd6630a7bf85faa061327e5c414d7
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# Considérations relatives à la sécurité{#security-considerations}

Certaines considérations de sécurité doivent être prises en compte pour le Browser TVSDK.

* **Flash Player Adobe**

   * Flash Player n’autorise pas l’accès aux données qui résident en dehors du domaine d’origine du SWF.

      Pour autoriser l’accès, hébergez un fichier de stratégie interdomaines avec les autorisations appropriées à la racine du serveur qui héberge les données. En mode de secours par Flash dans Browser TVSDK (Flash Player version 23 et ultérieure), vous avez besoin du jeton d’autorisation pour votre domaine. Pour générer le jeton, contactez votre représentant d’Adobe.

* **JavaScript**

   * JavaScript applique la même stratégie d’origine et empêche l’accès aux ressources au-delà des limites de domaine.

      Pour permettre l’accès à ces ressources, l’en-tête Access-Control-Allow-Origin (CORS) doit être défini sur les ressources hébergées sur des origines autres que le lecteur. Si vous le souhaitez, si le contenu est spécifié à l’aide de plages d’octets, la demande d’options de pré-vol CORS doit indiquer que ces demandes sont autorisées par l’origine.

* **Navigateurs et contenu mixte**

   * Les navigateurs exigent que le contenu chiffré AES-128 soit hébergé sur l’origine sécurisée (par exemple, HTTPS).

      Comme la plupart des navigateurs n’autorisent pas le contenu mixte, nous recommandons que le lecteur, le contenu et les ressources associées, telles que les fichiers Key/WebVTT, soient également hébergés sur l’origine sécurisée.

      >[!IMPORTANT]
      >
      >À compter de la version 2.4.5, si le lecteur est hébergé via HTTPS, le navigateur TVSDK convertit les appels HTTP en HTTPS lors de l’utilisation de la technologie MSE.
