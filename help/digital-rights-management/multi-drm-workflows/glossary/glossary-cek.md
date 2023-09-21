---
title: Glossaire
description: Termes fréquemment utilisés qui nécessitent une définition spéciale.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# Glossaire {#glossary}

Termes fréquemment utilisés qui nécessitent une définition spéciale.

## Clé de chiffrement du contenu {#content-encryption-key}

La clé de chiffrement de contenu (CEK), générée par un utilitaire, est ensuite utilisée par un module de contenu pour préparer le contenu qui doit être protégé.
L’utilitaire génère la clé en hexadécimal avec une longueur de 16 octets.
Ce guide présente, dans les notes et les exemples de message d’erreur, de fichier et de commande, les variantes suivantes de noms de paramètre et de noms de valeur pour le CEK :

* clé de contenu
* `&contentKey=`
* `?cek=`
* `<CEK>`
* `[YOUR CONTENT KEY]`

Les noms de fichier d’un CEK sont affichés comme suit :

* `keyfile.bin`
* `creds/fairplaybin`
* `Jaigo_DASH/_info/key.B64.random`

Le CEK lui-même peut être stocké dans un système de gestion des clés ainsi que crypté. Ce guide fait référence à l’index de stockage en tant que CEKSID d’identifiant de stockage du CEK. Le terme clé de chiffrement de clé (KEK) fait référence à la clé de chiffrement de deuxième niveau et le terme `ek` fait référence à la valeur de ce chiffrement.
Certains appels utilisent le CEK et le CEKSID ID de stockage du CEK, et le CEK récupéré du stockage doit correspondre au CEK fourni dans l’appel.
Pour HLS Offline avec FairPlay, il existe également une `persistentContentKey` qui peut être défini pour expirer.

## Identifiant de stockage de clé de chiffrement de contenu {#content-encryption-key-storage-id}

L’identifiant de stockage de clé de chiffrement de contenu (CEKSID) est un identifiant permettant de récupérer une clé de chiffrement de contenu à partir d’un système de gestion des clés.

Le CEKSID est également appelé
* ID de clé
* Identifiant de contenu
* `&kid`

## Authentificateur client {#customer-authenticator}

Clé d’authentification dans les demandes à l’API d’Expression. Les demandes peuvent inclure des demandes de jetons.
