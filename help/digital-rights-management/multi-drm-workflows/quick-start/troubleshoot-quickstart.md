---
description: Les problèmes courants au cours du test concernent souvent vos authentificateurs ExpressPlay, les protocoles de transport et les paramètres de demande de service requis.
seo-description: Les problèmes courants au cours du test concernent souvent vos authentificateurs ExpressPlay, les protocoles de transport et les paramètres de demande de service requis.
seo-title: Dépannage de votre début rapide
title: Dépannage de votre début rapide
uuid: 42256aa0-2efc-4602-aefc-3bab2dc58ec0
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Dépannage de votre début rapide{#troubleshooting-your-quick-start}

Les problèmes courants au cours du test concernent souvent vos authentificateurs ExpressPlay, les protocoles de transport et les paramètres de demande de service requis.

Si vos [!DNL curl] demandes à ExpressPlay pour la génération de jetons échouent, le corps de la réponse contient un message d’erreur expliquant la raison de l’échec.

Si la génération du jeton a réussi, mais que le contenu n’est toujours pas lu, vérifiez dans les journaux de remboursement du jeton ExpressPlay les erreurs telles que &quot;Jeton expiré&quot;.

Si la génération du jeton a réussi et que l’échange n’a pas généré d’erreur, mais que la vidéo ne se lance toujours pas, vérifiez que le CEK correspond au contenu et que le format de contenu correspond aux fonctionnalités du périphérique de cible.

En outre :

* Vérifiez que vous utilisez l’authentificateur de client correct dans vos demandes de service. Il est facile d’utiliser accidentellement l’authentificateur de production lorsque vous vouliez utiliser l’authentificateur de test. Assurez-vous également d’utiliser *votre* authentificateur. Par exemple, pendant le test, vous pouvez emprunter la `curl` commande de quelqu&#39;un d&#39;autre et oublier d&#39;échanger votre authentificateur contre la leur.

* Vérifiez que vous utilisez le protocole de transport approprié dans vos demandes ou dans vos manifestes ( `https://` contre `https://`, ou dans le cas de FairPlay, `skd://` contre `https://``https://`.

* Veillez à inclure tous les paramètres de requête requis pour la solution DRM que vous utilisez. Par exemple, il est facile de se faire confondre entre PlayReady et Widevine, parce qu&#39;elles fonctionnent toutes deux avec DASH, mais les paramètres de demande requis et les configurations de conditionnement sont différents.
* Vérifiez que votre compte ExpressPlay dispose de suffisamment de crédits de jeton et n’est pas épuisé.
* Vérifiez que le triplet de données DRM envoyées à TVSDK est correct : Jeton ExpressPlay, URL du serveur de licences et type DRM.
* Vérifiez que tous vos composants font la même hypothèse quant à l’environnement ExpressPlay en cours d’utilisation, car il existe deux environnements, Test and Production.
* Sachez que les différents navigateurs ne prennent généralement en charge qu’un seul DRM pour le contenu DASH.
* Depuis TVSDK 2.4, seul le profil d’emballage DASH-LIVE est pris en charge. (Le support DASH-OnDemand est sur la feuille de route.)
* La prise en charge d’AndroidTV PlayReady est intermittente en raison des limitations du fabricant du périphérique. Pour donner des exemples,

   * le périphérique Razer Forge rencontre des problèmes avec le contenu PlayReady
   * Amazon FireTV ne peut pas consommer de contenu DASH dont la piste audio est chiffrée

* Depuis TVSDK 2.4, seuls les périphériques AndroidTV prennent généralement en charge les DRM PlayReady et Widevine. Tous les autres périphériques Android ne prennent généralement en charge que Widevine.
* Depuis TVSDK 2.4, l’Android TVSDK exige actuellement que la zone PSSH figure dans le manifeste .mpd. Ceci est contraire à la norme DASH, qui spécifie que la zone PSSH peut être n&#39;importe où, comme dans le contenu lui-même, et pas seulement dans le .mpd.

