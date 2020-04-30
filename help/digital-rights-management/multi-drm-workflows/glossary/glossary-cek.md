---
uuid: 2d927ae8-4c4b-4b64-88b8-9c86430e226c
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Glossaire {#glossary}

Termes fréquemment utilisés nécessitant une définition spéciale.

## Clé de chiffrement du contenu {#content-encryption-key}

La clé de chiffrement de contenu (CEK), générée par un utilitaire, est par la suite utilisée par un gestionnaire de contenu pour préparer le contenu qui doit être protégé.
L&#39;utilitaire génère la clé en hexadécimal avec une longueur de 16 octets.
Ce guide présente, dans les notes et les exemples de message d’erreur, de fichier et de commande, les variantes suivantes de noms de paramètre et de noms de valeur pour le CEK :

* clé de contenu
* `&contentKey=`
* `?cek=`
* `<CEK>`
* `[YOUR CONTENT KEY]`

Les noms de fichier pour un CEK sont affichés comme suit :

* `keyfile.bin`
* `creds/fairplaybin`
* `Jaigo_DASH/_info/key.B64.random`

Le CEK lui-même peut être stocké dans un système de gestion des clés ainsi que crypté. Ce guide fait référence à l’index d’enregistrement en tant que CEKSID ID d’Enregistrement CEK. Le terme clé de chiffrement de clé (KEK) fait référence à la clé de chiffrement de second niveau et le terme `ek` fait référence à la valeur de ce chiffrement.
Certains appels utilisent à la fois le CEK et le CEKSID d’ID d’Enregistrement du CEK, et le CEK récupéré de l’enregistrement doit correspondre au CEK fourni dans l’appel.
Pour HLS Offline avec FairPlay, il existe également un `persistentContentKey` qui peut être défini pour expirer.

## ID d’Enregistrement clé de chiffrement de contenu {#content-encryption-key-storage-id}

L’Enregistrement de clé de chiffrement de contenu (CEKSID) est un identifiant permettant de récupérer une clé de chiffrement de contenu à partir d’un système de gestion des clés.

Le CEKSID est également appelé
* ID de clé
* ID de contenu
* `&kid`

## Authentification du client {#customer-authenticator}

Clé d’authentification dans les demandes à l’API d’Expressplay. Les demandes peuvent inclure des demandes de jetons.