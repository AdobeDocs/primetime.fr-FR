---
seo-title: Présentation de l’utilitaire d’identification de l’éditeur AIR
title: Présentation de l’utilitaire d’identification de l’éditeur AIR
uuid: 31aecc0e-ad9b-43ad-ba58-77d2c999f4a4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Présentation de l’utilitaire d’identification de l’éditeur AIR {#air-publisher-id-utility-overview}

Dans le cadre du processus de création d’un fichier AIR, l’outil ADT (AIR Developer Tool) génère un identifiant d’éditeur. Il s’agit d’un identifiant unique au certificat utilisé pour créer le fichier AIR. Si vous réutilisez le même certificat pour plusieurs applications AIR, elles auront le même ID d&#39;éditeur. L&#39;utilitaire d&#39;identification de l&#39;éditeur AIR est utilisé pour calculer l&#39;ID d&#39;éditeur d&#39;une application AIR. Les versions d’AIR ultérieures à la version 1.5.2 n’écrivent pas l’identifiant d’éditeur généré dans un fichier. Il est donc nécessaire d’utiliser cet outil pour déterminer l’identifiant d’éditeur si vous utilisez une liste blanche d’applications AIR.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>L’ID d’éditeur, utilisé pour l’application de la liste blanche AIR, n’est pas identique à l’ID d’éditeur spécifié par l’éditeur de l’application dans le [!DNL application.xml] fichier de l’application.

