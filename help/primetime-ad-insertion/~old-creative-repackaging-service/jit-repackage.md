---
description: Un lecteur vidéo client ou le serveur de manifeste peuvent interagir avec CRS pour obtenir un reconditionnement JIT. Les deux utilisent la même logique de sélection des publicités.
seo-description: Un lecteur vidéo client ou le serveur de manifeste peuvent interagir avec CRS pour obtenir un reconditionnement JIT. Les deux utilisent la même logique de sélection des publicités.
seo-title: Workflows détaillés pour la restauration JIT
title: Workflows détaillés pour la restauration JIT
uuid: 11b6eb3c-f6aa-4018-9b20-ab6f5910508b
translation-type: tm+mt
source-git-commit: e437f4143fb939f46d106c64efc391137c33fe17
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 0%

---


# Workflows détaillés pour la restauration JIT {#detailed-workflows-for-jit-repackaging}

Un lecteur vidéo client ou le serveur de manifeste peuvent interagir avec CRS pour obtenir un reconditionnement JIT. Les deux utilisent la même logique de sélection des publicités.

## Réparation JIT initiée par le serveur de manifeste {#section_1F1C1B7DD146403890C2B43E24FEF0EB}

![](assets/ssai_JIT-workflow_web.png)

Le processus de reconditionnement JIT côté serveur de manifeste est le suivant :

1. Le serveur de manifeste envoie une requête au serveur d’annonces.
1. Le serveur de manifeste reçoit un créatif publicitaire qui n’est pas au format HLS.
1. Le serveur de manifeste envoie une requête au serveur CDN pour une version HLS précédemment transcodée du créatif publicitaire.

   >[!NOTE]
   >
   >Dans une configuration multi-CDN, le serveur de manifeste utilise le paramètre `ptcdn` de l’URL d’amorçage pour identifier le serveur CDN.

1. Le serveur manifeste vérifie la réponse :

   1. Si la requête réussit, le serveur de manifeste insère la version HLS précédemment transcodée de l’élément créatif publicitaire dans le flux de contenu.
   1. Si la requête échoue, le serveur de manifeste génère une entrée de journal et demande une version transcodée à CRS.

1. CRS transcode la création publicitaire et télécharge la version HLS sur le serveur CDN pour une utilisation ultérieure.

Pour toutes les demandes suivantes pour ce créatif, le serveur de manifeste récupère la version HLS du CDN et l’insère dans le flux de contenu.

## Réparation JIT initiée par le client {#section_FBC97D40043F4FDD98247A08BB6195B0}

<!--<a id="fig_hkn_ndt_3z"></a>-->

![](assets/ssai_JIT-workflow_client_web.png)

Un client basé sur TVSDK ou disposant de capacités similaires peut interagir avec CRS pour obtenir un reconditionnement JIT, comme suit :

1. Le client demande une publicité au serveur d’annonces.
1. Le serveur d’annonces renvoie la publicité au client.
1. Le client vérifie le format de la publicité à partir du serveur d’annonces :

   1. Si le créatif de la publicité est au format HLS, le client l’insère (s’attache) dans le contenu, puis il le fait.
   1. Si le créatif publicitaire n’est pas au format HLS, le client en demande un auprès du serveur CDN.

      >[!NOTE]
      >
      >Dans une configuration multi-CDN, le serveur de manifeste utilise le paramètre `ptcdn` de l’URL d’amorçage pour identifier le serveur CDN.

1. Le client vérifie la réponse du serveur CDN.

   1. Si le réseau de diffusion de contenu a fourni une version HLS, le client l’insère (l’étale) dans le contenu, et cela est fait.
   1. Si le serveur CDN ne fournit pas de version HLS, le client demande au serveur d’annonces d’en demander une auprès de CRS. Le client n’insère pas la publicité dans le contenu.

1. Le serveur d’annonces demande que les non-HLS soient transcodés vers HLS.
1. CRS crée une version HLS et la télécharge sur le serveur CDN pour une utilisation ultérieure.

## Priorités et calendrier des formats publicitaires {#section_A74DE37A57BF45D7B6D09E3DE40F8E61}

Le serveur de manifeste et le client utilisent la même logique de sélection pour déterminer les priorités de lecture des publicités disponibles. Les publicités au format HLS sont prioritaires, suivies par MP4, FLV et enfin WebM.

En règle générale, il faut 2 à 4 minutes pour traiter un élément créatif publicitaire non-HLS, et généralement moins de 3 minutes.

CRS produit des débits HLS différents, de sorte que la publicité peut être lue à une vitesse adaptée à la vitesse de connexion et à la bande passante disponibles. S’il existe plusieurs débits disponibles, CRS choisit le débit le plus élevé disponible. Si CRS reçoit une version publicitaire non HLS, elle produit une version HLS à la résolution la plus élevée disponible.