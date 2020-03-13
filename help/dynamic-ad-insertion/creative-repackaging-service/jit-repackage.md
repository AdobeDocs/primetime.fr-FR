---
description: Un lecteur vidéo client ou le serveur de manifeste peuvent interagir avec CRS pour obtenir un reconditionnement JIT. Tous deux utilisent la même logique de sélection des publicités.
seo-description: Un lecteur vidéo client ou le serveur de manifeste peuvent interagir avec CRS pour obtenir un reconditionnement JIT. Tous deux utilisent la même logique de sélection des publicités.
seo-title: détaillé pour le reconditionnement JIT
title: détaillé pour le reconditionnement JIT
uuid: 11b6eb3c-f6aa-4018-9b20-ab6f5910508b
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# détaillé pour le reconditionnement JIT {#detailed-workflows-for-jit-repackaging}

Un lecteur vidéo client ou le serveur de manifeste peuvent interagir avec CRS pour obtenir un reconditionnement JIT. Tous deux utilisent la même logique de sélection des publicités.

## Réparation JIT initiée par le serveur Manifest {#section_1F1C1B7DD146403890C2B43E24FEF0EB}

![](assets/ssai_JIT-workflow_web.png)

Le processus de reconditionnement JIT côté serveur de manifeste est le suivant :

1. Le serveur de manifeste envoie une requête au serveur d’annonces.
1. Le serveur de manifeste reçoit un élément créatif publicitaire qui n’est pas au format HLS.
1. Le serveur de manifeste envoie une requête au serveur CDN pour une version HLS précédemment transcodée du créatif publicitaire.

   >[!NOTE]
   >
   >Dans une configuration multi-CDN, le serveur de manifeste utilise le `ptcdn` paramètre de l’URL d’amorçage pour identifier le serveur CDN.

1. Le serveur de manifeste vérifie la réponse :

   1. Si la requête réussit, le serveur de manifeste insère la version HLS précédemment transcodée du créatif publicitaire dans le flux de contenu.
   1. Si la requête échoue, le serveur de manifeste génère une entrée de journal et demande une version transcodée à CRS.

1. CRS transcode la création publicitaire et télécharge la version HLS sur le serveur CDN pour une utilisation ultérieure.

Pour toutes les demandes suivantes pour ce créatif, le serveur de manifeste récupère la version HLS du CDN et l’insère dans le flux de contenu.

## Le reconditionnement JIT initié par le client {#section_FBC97D40043F4FDD98247A08BB6195B0}

<!--<a id="fig_hkn_ndt_3z"></a>-->

![](assets/ssai_JIT-workflow_client_web.png)

Un client basé sur TVSDK ou ayant des capacités similaires peut interagir avec CRS pour obtenir un reconditionnement JIT, comme suit :

1. Le client demande une publicité au serveur d’annonces.
1. Le serveur d’annonces renvoie la publicité au client.
1. Le client vérifie le format de la publicité à partir du serveur d’annonces :

   1. Si le créatif de la publicité est au format HLS, le client l’insère (l’assemble) dans le contenu, puis il est terminé.
   1. Si le créatif de la publicité n’est pas au format HLS, le client en demande un auprès du serveur CDN.

      >[!NOTE]
      >
      >Dans une configuration multi-CDN, le serveur de manifeste utilise le `ptcdn` paramètre de l’URL d’amorçage pour identifier le serveur CDN.

1. Le client vérifie la réponse du serveur CDN.

   1. Si le CDN a fourni une version HLS, le client l’insère (l’assemble) dans le contenu, et c’est fait.
   1. Si le serveur CDN ne fournit pas de version HLS, le client demande au serveur d’annonces d’en demander une auprès de CRS. Le client n’insère pas la publicité dans le contenu.

1. Le serveur d’annonces demande que la publicité non-HLS soit transcodée dans HLS.
1. CRS crée une version HLS et la télécharge vers le serveur CDN pour une utilisation ultérieure.

## Priorités et calendrier des formats publicitaires {#section_A74DE37A57BF45D7B6D09E3DE40F8E61}

Le serveur de manifeste et le client utilisent la même logique de sélection pour déterminer les priorités de lecture des publicités disponibles. Les publicités au format HLS sont prioritaires, suivies par MP4, FLV et enfin WebM.

En règle générale, il faut de 2 à 4 minutes pour traiter un élément créatif publicitaire non HLS, et généralement moins de 3 minutes.

CRS produit des débits HLS différents, de sorte que la publicité puisse être lue à une vitesse adaptée à la vitesse de connexion et à la bande passante disponibles. S’il existe plusieurs débits, CRS choisit le débit le plus élevé disponible. Si CRS reçoit un élément créatif publicitaire non-HLS, il produit une version HLS à la résolution la plus élevée disponible.