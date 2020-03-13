---
seo-title: Version minimale du client
title: Version minimale du client
uuid: f2b56cff-96fa-4954-a08a-9b3e78f496d6
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Version minimale du client {#minimum-client-version}

Adobe Primetime DRM 2.0.2 et versions ultérieures introduisent de nouvelles règles d’utilisation qui ne sont pas comprises par les clients de Primetime DRM 2.0. En définissant la version minimale du client prise en charge ( `HandlerConfiguration.setMinSupportedClientVersion()`), le serveur de licences peut contrôler le comportement des clients plus anciens lorsqu’ils rencontrent des licences avec ces règles d’utilisation. Selon ce paramètre, le serveur peut indiquer si les clients plus âgés peuvent ignorer les règles d’utilisation qu’ils ne comprennent pas ou si les clients plus âgés ne pourront pas consommer de licences avec ces règles d’utilisation.

Par exemple,

* Si la licence spécifie les fonctionnalités requises pour le périphérique (fonctionnalités [du périphérique requises pour lire le contenu](../../../protecting-content/introduction/usage-rules/runtime-application-restrictions/device-capabilities.md)protégé), les clients DRM Primetime 2.0.2 et versions ultérieures peuvent appliquer ces exigences.
* Si le serveur de licences ne souhaite pas que le contenu soit lu sur des clients qui ne comprennent pas les exigences en matière de fonctionnalités du périphérique, définissez la version minimale du client prise en charge sur 2 (pour la version 2.0.2). Cela empêchera le serveur de délivrer des licences aux clients DRM Primetime avant la version 2.0.2. La version minimale du client est également appliquée si la licence est transférée d’un client à un autre.
* Si le serveur de licences souhaite permettre aux clients plus âgés d’ignorer les exigences de capacités du périphérique, définissez la version minimale du client prise en charge sur 1 (pour Primetime DRM 2.0). Le serveur délivre ensuite une licence à n’importe quel client version 2.0 ou ultérieure. Si le client met à niveau ou transfère la licence vers un autre client avec la version 2.0.2 ou ultérieure, les exigences de capacités du périphérique dans la licence sont alors appliquées car le client peut alors prendre en charge cette règle d’utilisation.

