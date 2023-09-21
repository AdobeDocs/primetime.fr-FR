---
title: Configuration d’Adobe Primetime Ad Insertion
description: Configuration d’Adobe Primetime Ad Insertion
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---

# Configuration d’Adobe Primetime Ad Insertion {#ptai-setup}

Le processus de configuration de l’Ad Insertion Primetime est le suivant :

1. Intégrez votre serveur d’annonces à l’Ad Insertion Primetime en vous connectant à la console de l’Ad Insertion Primetime et en configurant des règles de redirection. Pour plus d’informations, voir [Intégration de votre serveur d’annonces](/help/primetime-ad-insertion/getting-started/integrate-ad-server.md).

1. Configurez les canaux ou les plateformes dans la console Ad Insertion Primetime afin de garantir des dimensions de création de rapports adéquates.

1. Configurez et intégrez votre réseau de diffusion de contenu dans l’Ad Insertion Primetime. Pour plus d’informations, voir [Intégration de votre réseau de diffusion de contenu](integrate-cdn.md).

1. Déterminez si un module de reconditionnement des publicités juste à temps est requis pour votre workflow publicitaire. Contactez votre représentant de l’assistance Primetime pour activer le service.

1. Mettez à jour votre application pour utiliser la variable [API BOOTSTRAP](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md) pour effectuer et recevoir des demandes pour l’Ad Insertion Primetime, et configurer votre application pour qu’elle soit prise en charge. Pour plus d’informations, voir [Suivi des publicités](set-up-ad-tracking.md).

1. Testez votre application pour vous assurer que la lecture de la publicité est correcte à l’aide de la variable [Outils de débogage](/help/primetime-ad-insertion/performance-monitoring-debugging-reporting/troubleshoot-and-debug.md).

1. Testez vos applications pour vérifier le déclenchement correct des balises de suivi et d’impression publicitaires à l’aide de la variable [Reporting](/help/primetime-ad-insertion/performance-monitoring-debugging-reporting/reporting-and-billing.md).
