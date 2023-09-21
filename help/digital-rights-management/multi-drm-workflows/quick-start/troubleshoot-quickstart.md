---
description: Les problèmes courants au cours des tests impliquent souvent vos authentificateurs ExpressPlay, vos protocoles de transport et vos paramètres de demande de service requis.
title: Dépannage de votre démarrage rapide
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# Dépannage de votre démarrage rapide{#troubleshooting-your-quick-start}

Les problèmes courants au cours des tests impliquent souvent vos authentificateurs ExpressPlay, vos protocoles de transport et vos paramètres de demande de service requis.

Si votre [!DNL curl] les demandes à ExpressPlay pour la génération de jetons échouent. Le corps de la réponse contient un message d’erreur qui explique la raison de l’échec.

Si la génération du jeton est réussie, mais que le contenu n’est toujours pas lu, vérifiez dans les journaux de rédemption du jeton ExpressPlay les erreurs telles que &quot;Jeton expiré&quot;.

Si la génération du jeton a réussi et que la rédemption n’a pas rencontré d’erreur, mais que la vidéo n’est toujours pas lue, vérifiez que le CEK correspond au contenu et que le format de contenu correspond aux fonctionnalités de l’appareil cible.

En outre :

* Vérifiez que vous utilisez le bon authentificateur client dans vos demandes de service. Il est facile d’utiliser accidentellement l’authentificateur de production lorsque vous avez l’intention d’utiliser l’authentificateur de test. Vérifiez également que vous utilisez *your* authentificateur. Par exemple, pendant les tests, vous pouvez emprunter le `curl` et oubliez d’échanger votre authentificateur contre le leur.

* Vérifiez que vous utilisez le protocole de transport approprié dans vos requêtes ou dans vos manifestes ( `https://` versus `https://`, ou dans le cas de FairPlay, `skd://` versus `https://` versus `https://`.

* Veillez à inclure tous les paramètres de requête requis pour la solution DRM que vous utilisez. Par exemple, il est facile de vous brouiller entre PlayReady et Widevine, car elles fonctionnent toutes deux avec DASH, mais les paramètres de requête et les configurations de package requis sont différents.
* Vérifiez que votre compte ExpressPlay dispose de suffisamment de crédits de jeton et n’a pas été épuisé.
* Vérifiez que le triplet de données DRM envoyé à TVSDK est correct : jeton ExpressPlay, URL du serveur de licences et type DRM.
* Vérifiez que tous vos composants font la même hypothèse sur l’environnement ExpressPlay en cours d’utilisation, car il existe deux environnements : Test et Production.
* Gardez à l’esprit que les différents navigateurs ne prennent généralement en charge qu’un seul DRM pour le contenu DASH.
* Depuis TVSDK 2.4, seul le profil de package DASH-LIVE est pris en charge. (La prise en charge de DASH-OnDemand figure sur la feuille de route.)
* La prise en charge d’AndroidTV PlayReady est intermittente en raison des restrictions du fabricant de l’appareil. Pour donner des exemples :

   * Le périphérique Razer Forge a des problèmes avec le contenu PlayReady .
   * Amazon FireTV ne peut pas utiliser de contenu DASH dont la piste audio est chiffrée

* Depuis TVSDK 2.4, seuls les appareils AndroidTV prennent généralement en charge les DRM PlayReady et Windows. En règle générale, tous les autres appareils Android ne prennent en charge que Windows.
* Depuis TVSDK 2.4, Android TVSDK requiert actuellement que la boîte PSSH soit dans le manifeste .mpd. Cela est contraire à la norme DASH, qui spécifie que la boîte PSSH peut être n’importe où, comme dans le contenu lui-même, et pas seulement dans le fichier .mpd.
