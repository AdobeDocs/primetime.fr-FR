---
seo-title: Présentation de l’utilitaire d’ID d’éditeur AIR
title: Présentation de l’utilitaire d’ID d’éditeur AIR
uuid: 31aecc0e-ad9b-43ad-ba58-77d2c999f4a4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Présentation de l’utilitaire d’ID d’éditeur AIR {#air-publisher-id-utility-overview}

Dans le cadre du processus de création d’un fichier AIR, l’outil ADT (AIR Developer Tool) génère un identifiant d’éditeur. Identificateur unique du certificat utilisé pour créer le fichier AIR. Si vous réutilisez le même certificat pour plusieurs applications AIR, elles auront le même ID d’éditeur. L’utilitaire d’ID d’éditeur AIR est utilisé pour calculer l’ID d’éditeur d’une application AIR. Les versions d’AIR ultérieures à la version 1.5.2 n’écrivent pas l’ID d’éditeur généré dans un fichier. Il est donc nécessaire d’utiliser cet outil pour déterminer l’ID d’éditeur si vous utilisez une liste blanche d’application AIR.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>L’ID de l’éditeur, utilisé pour l’application de la liste blanche d’AIR, n’est pas identique à l’ID de l’éditeur spécifié par l’éditeur de l’application dans le [!DNL application.xml] fichier de l’application.

