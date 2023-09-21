---
description: Un lecteur vidéo client ou le serveur de manifeste peuvent interagir avec CRS pour réaliser un reconditionnement JIT. Toutes deux utilisent la même logique de sélection des publicités.
title: Workflows détaillés pour la correction JIT
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---


# Workflows détaillés pour la correction JIT {#detailed-workflows-for-jit-repackaging}

Un lecteur vidéo client ou le serveur de manifeste peuvent interagir avec CRS pour réaliser un reconditionnement JIT. Toutes deux utilisent la même logique de sélection des publicités.

## Réplication JIT initiée par le serveur de manifeste {#section_1F1C1B7DD146403890C2B43E24FEF0EB}

![](assets/ssai_JIT-workflow_web.png)

Le workflow de reconditionnement JIT côté serveur manifeste est le suivant :

1. Le serveur de manifeste envoie une requête au serveur d’annonces.
1. Le serveur de manifeste reçoit un élément créatif publicitaire qui n’est pas au format HLS.
1. Le serveur de manifeste envoie une requête au serveur CDN pour une version HLS précédemment transcodée du créatif publicitaire.

   >[!NOTE]
   >
   >Dans une configuration multi-CDN, le serveur manifeste utilise la variable `ptcdn` dans l’URL de bootstrap pour identifier le serveur CDN.

1. Le serveur de manifeste vérifie la réponse :

   1. Si la requête réussit, le serveur de manifeste insère la version HLS précédemment transcodée de l’élément créatif publicitaire dans le flux de contenu.
   1. Si la requête échoue, le serveur de manifeste génère une entrée de journal et demande une version transcodée à partir de CRS.

1. CRS transcode le contenu publicitaire et télécharge la version HLS sur le serveur CDN en vue d’une utilisation ultérieure.

Pour toutes les requêtes suivantes de ce créatif, le serveur de manifeste récupère la version HLS du réseau de diffusion de contenu et l’insère dans le flux de contenu.

## Reprise JIT initiée par le client {#section_FBC97D40043F4FDD98247A08BB6195B0}

<!--<a id="fig_hkn_ndt_3z"></a>-->

![](assets/ssai_JIT-workflow_client_web.png)

Un client basé sur TVSDK ou avec des fonctionnalités similaires peut interagir avec CRS pour réaliser un reconditionnement JIT, comme suit :

1. Le client demande une publicité au serveur d’annonces.
1. Le serveur de publicités renvoie la publicité au client.
1. Le client vérifie le format de la publicité à partir du serveur de publicités :

   1. Si le créatif publicitaire est au format HLS, le client l’insère (l’assemble) dans le contenu, et c’est fait.
   1. Si le contenu publicitaire n’est pas au format HLS, le client en demande un auprès du serveur CDN.

      >[!NOTE]
      >
      >Dans une configuration multi-CDN, le serveur manifeste utilise la variable `ptcdn` dans l’URL de bootstrap pour identifier le serveur CDN.

1. Le client vérifie la réponse du serveur CDN.

   1. Si le réseau de diffusion de contenu a fourni une version HLS, le client l’insère (l’assemble) dans le contenu, et c’est fait.
   1. Si le serveur CDN ne fournit pas de version HLS, le client demande au serveur d’annonces d’en demander une auprès de CRS. Le client n’insère pas la publicité dans le contenu.

1. Le serveur d’annonces demande que les non-HLS soient transcodés en HLS.
1. CRS crée une version HLS et la télécharge sur le serveur CDN pour une utilisation ultérieure.

## Priorités et chronologie du format de publicité {#section_A74DE37A57BF45D7B6D09E3DE40F8E61}

Le serveur de manifeste et le client utilisent la même logique de sélection pour déterminer les priorités de lecture des publicités disponibles. Les publicités au format HLS sont prioritaires, suivies par MP4, FLV et enfin WebM.

CRS nécessite généralement 2 à 4 minutes pour traiter un contenu publicitaire non HLS, et généralement moins de 3 minutes.

CRS produit des débits HLS différents, de sorte que la publicité peut être lue à une vitesse adaptée à la vitesse de connexion et à la bande passante disponibles. S’il existe plusieurs débits, CRS choisit le débit le plus élevé disponible. Si CRS reçoit un contenu publicitaire non HLS, il produit une version HLS à la résolution la plus élevée disponible.