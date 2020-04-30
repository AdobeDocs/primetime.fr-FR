---
seo-title: Version minimale du client
title: Version minimale du client
uuid: 9f39e4e7-64eb-43ea-b194-b744838a411e
translation-type: tm+mt
source-git-commit: 53654b740b03c6a79394d30704a41186d4655237

---


# Version minimale du client {#minimum-client-version}

Adobe Access 2.0.2 et versions ultérieures introduisent de nouvelles règles d&#39;utilisation qui ne sont pas comprises par les clients Adobe Access 2.0. En définissant la version minimale du client prise en charge ( `HandlerConfiguration.setMinSupportedClientVersion()`), le serveur de licences peut contrôler le comportement des clients plus âgés lorsqu’ils rencontrent des licences avec ces règles d’utilisation. En fonction de ce paramètre, le serveur peut indiquer si les clients plus âgés peuvent ignorer les règles d’utilisation qu’ils ne comprennent pas ou si les clients plus âgés ne pourront pas consommer de licences avec ces règles d’utilisation.

Par exemple,

* Si la licence spécifie les capacités requises pour l’appareil (capacités de [périphérique requises pour lire du contenu](../../../aaxs-protecting-content/content-introduction/content-usage-rules/content-runtime-application-restrictions/content-device-capabilities.md)protégé), les clients Adobe Access 2.0.2 et versions ultérieures peuvent appliquer ces exigences.
* Si le serveur de licences ne souhaite pas que le contenu soit lu sur des clients qui ne comprennent pas les capacités requises du périphérique, définissez la version minimale du client prise en charge sur 2 (pour la version 2.0.2). Cela empêchera le serveur d’émettre des licences aux clients Adobe Access avant la version 2.0.2. La version minimale du client sera également appliquée si la licence est transférée d’un client à un autre.
* Si le serveur de licences souhaite permettre aux clients plus âgés d’ignorer les exigences en matière de capacités de l’appareil, définissez la version minimale du client prise en charge sur 1 (pour Adobe Access 2.0). Le serveur délivre une licence à tout client version 2.0 et ultérieure. Si le client met à niveau ou transfère la licence vers un autre client avec la version 2.0.2 ou ultérieure, les exigences de capacités du périphérique dans la licence seront appliquées, puisque le client prend désormais en charge cette règle d’utilisation.

