---
title: Version minimale du client
description: Version minimale du client
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---

# Version minimale du client {#minimum-client-version}

Adobe Primetime DRM 2.0.2 et versions ultérieures introduisent de nouvelles règles d’utilisation qui ne sont pas comprises par les clients Primetime DRM 2.0. En définissant la version minimale du client prise en charge ( `HandlerConfiguration.setMinSupportedClientVersion()`), le serveur de licences peut contrôler le comportement des clients plus âgés lorsqu’ils rencontrent des licences avec ces règles d’utilisation. Selon ce paramètre, le serveur peut indiquer si les clients plus anciens peuvent ignorer les règles d’utilisation qu’ils ne comprennent pas ou si les clients plus anciens ne pourront pas utiliser de licences avec ces règles d’utilisation.

Par exemple :

* Si la licence spécifie les exigences de capacités de l’appareil ( [Fonctionnalités de l’appareil requises pour lire du contenu protégé](../../../protecting-content/introduction/usage-rules/runtime-application-restrictions/device-capabilities.md)), les clients DRM Primetime 2.0.2 et versions ultérieures peuvent appliquer ces exigences.
* Si le serveur de licences ne souhaite pas que le contenu soit lu sur des clients qui ne comprennent pas les exigences en matière de capacités de l’appareil , définissez la version minimale du client prise en charge sur 2 (pour la version 2.0.2). Cela empêchera le serveur d’émettre des licences aux clients Primetime DRM avant la version 2.0.2. La version cliente minimale est également appliquée si la licence est transférée d’un client à un autre.
* Si le serveur de licences souhaite permettre aux clients plus âgés d’ignorer les exigences en matière de fonctionnalités de l’appareil, définissez la version minimale du client prise en charge sur 1 (pour Primetime DRM 2.0). Le serveur émet ensuite une licence à n’importe quel client version 2.0 ou ultérieure. Si le client met à niveau ou transfère la licence vers un autre client avec la version 2.0.2 ou ultérieure, les exigences de capacités de l’appareil dans la licence sont alors appliquées car le client peut alors prendre en charge cette règle d’utilisation.
