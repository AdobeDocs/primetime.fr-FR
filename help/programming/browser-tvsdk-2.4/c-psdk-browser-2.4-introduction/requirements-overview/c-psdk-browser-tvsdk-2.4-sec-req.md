---
description: Certaines considérations de sécurité doivent être prises en compte pour le SDK du navigateur.
seo-description: Certaines considérations de sécurité doivent être prises en compte pour le SDK du navigateur.
seo-title: Considérations relatives à la sécurité
title: Considérations relatives à la sécurité
uuid: 78edf2b0-363c-4ab6-b588-ab4748ee6096
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Considérations relatives à la sécurité{#security-considerations}

Certaines considérations de sécurité doivent être prises en compte pour le SDK du navigateur.

* **Adobe Flash Player**

   * Flash Player n’autorise pas l’accès aux données résidant en dehors du domaine d’origine du fichier SWF.

      Pour autoriser l’accès, hébergez un fichier de stratégie interdomaines avec les autorisations appropriées à la racine du serveur qui héberge les données. En mode de secours Flash dans le navigateur TVSDK (Flash Player version 23 et ultérieure), vous avez besoin du jeton d’autorisation pour votre domaine. Pour générer le jeton, contactez votre représentant Adobe.

* **JavaScript**

   * JavaScript suit la même stratégie d’origine et empêche l’accès aux ressources au-delà des limites de domaine.

      Pour autoriser l&#39;accès à ces ressources, l&#39;en-tête Access-Control-Allow-Origine (CORS) doit être défini sur les ressources hébergées sur des origines autres que le lecteur. Si vous le souhaitez, si le contenu est spécifié à l’aide de plages d’octets, la demande d’options de pré-vol CORS doit indiquer que ces demandes sont autorisées par l’origine.

* **Navigateurs et contenu mixte**

   * Les navigateurs exigent que le contenu chiffré AES-128 soit hébergé par Origine sécurisée (HTTPS, par exemple).

      Comme la plupart des navigateurs n’autorisent pas le contenu mixte, nous recommandons que le lecteur, le contenu et les ressources associées, telles que les fichiers Key/WebVTT, soient également hébergés par Origine sécurisée.

      >[!IMPORTANT]
      >
      >À partir de la version 2.4.5, si le lecteur est hébergé sur HTTPS, le navigateur TVSDK convertit les appels HTTP en HTTPS lors de l’utilisation de la technologie MSE.

