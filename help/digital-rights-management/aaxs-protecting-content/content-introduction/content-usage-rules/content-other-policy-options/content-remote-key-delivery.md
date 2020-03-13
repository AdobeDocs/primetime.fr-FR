---
seo-title: 'clé iOS local et distant '
title: 'clé iOS local et distant '
uuid: 3c20b1d1-f842-438a-ae3a-4ec31da306ad
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# clé iOS local et distant{#remote-and-local-ios-key-delivery}

Adobe Primetime prend en charge deux options pour les clés aux clients iOS :

* Distant : exactement comme spécifié dans la spécification HLS, le manifeste M3U8 spécifie un chemin HTTPS contenant une clé AES qui doit être utilisée pour déchiffrer les segments chiffrés suivants dans le flux. Lorsque &quot;Remote&quot; est spécifié, le périphérique client se rend sur un serveur HTTPS distant pour récupérer la clé AES.
* Local - Lorsque le paramètre &quot;Local&quot; est spécifié, au lieu d’accéder par Internet/réseau à la clé AES, un serveur HTTPS local est intégré à l’application iOS qui traitera toutes les demandes de clés AES. Le serveur HTTPS intégré est automatiquement configuré et configuré dans l’application Primetime. Aucune intervention n’est requise de la part du développeur d’applications.

Le  des clés distantes est activé par le biais de la stratégie utilisée pour compresser le contenu (la modification de ce paramètre nécessite un reconditionnement du contenu). Lorsque le des clés distantes est activé, un serveur de clés Adobe Access doit être déployé pour traiter les requêtes clés des clients iOS, mais le flux de travail des clients sur d’autres plateformes n’est pas modifié.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>La sélection des  clés n’affecte que les clients iOS. Tous les autres périphériques qui consomment du contenu HLS utiliseront toujours le de clés &quot;local&quot;, même si &quot;distant&quot; a été spécifié.

Pour plus d’informations, voir *Utilisation d’Adobe Access Key Server*.
