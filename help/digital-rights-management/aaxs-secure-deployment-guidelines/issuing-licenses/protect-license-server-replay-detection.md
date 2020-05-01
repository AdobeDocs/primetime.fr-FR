---
seo-title: Protection de relecture
title: Protection de relecture
uuid: 5e6488e6-0834-4dcf-bc26-55019f5db320
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Protection de relecture{#replay-protection}

La protection Replay empêche un attaquant de relire un message de demande de licence et peut entraîner une attaque par déni de service (DoS) contre le client (Une attaque par *déni de service* est une tentative d&#39;attaquant visant à empêcher les utilisateurs légitimes d&#39;un service d&#39;utiliser ce service.) Par exemple, une attaque de relecture utilisant le compteur d&#39;annulation peut être utilisée pour &quot;tromper&quot; le serveur de licences afin de lui faire croire que le client DRM est en train de restaurer son état, ce qui entraîne la suspension du compte.

Pour en savoir plus sur la protection contre la relecture, consultez `AbstractRequestMessage.getMessageId()` le Guide de référence *de l’API* Adobe Access.
