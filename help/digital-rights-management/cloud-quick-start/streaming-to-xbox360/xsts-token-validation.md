---
title: Validation du jeton Xbox Live XSTS
description: Validation du jeton Xbox Live XSTS
copied-description: true
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---


# Validation du jeton Xbox Live XSTS{#xbox-live-xsts-token-validation}

Pour les requêtes XSTS, la variable `customerSpecificAuthToken` contient le jeton XSTS codé Base64. L’exemple `XSTSValidator` Le code examine le jeton décodé Base64 pour déterminer si la variable `EncryptedAssertion` ; toutefois, vous pouvez utiliser d’autres méthodes pour distinguer ces requêtes des requêtes autres que Xbox. Par exemple, vous pouvez utiliser une autre URL.

La stratégie renvoyée dans le message de réponse remplace la stratégie d’origine dans les métadonnées DRM fournies avec la requête de clé Xbox. Seul un sous-ensemble de fonctionnalités de stratégie est pris en charge par le client Xbox. Ces champs sont les seuls à remplacer la stratégie d’origine.

D’autres étapes de configuration sont nécessaires pour prendre en charge le décryptage et la validation des jetons. Vous devez charger la variable [!DNL xsts_partner_cert.pfx] et [!DNL x_secure_token_service.part.xboxlive.com.cer] informations d’identification dans un fichier de stockage de clés au format JKS, que vous fournissez ensuite à votre serveur de droits principal en tant que propriété système `xsts-keystore`. Par défaut, le partenaire [!DNL .pfx] a l’alias `xsts`et le certificat de validation du jeton a l’alias `xsts-verify-cert`. Vous pouvez également les remplacer à l’aide des propriétés système. Enfin, il existe une propriété système `xsts-keystore-password` qui ne comporte pas de valeur par défaut et qui contient le mot de passe du KeyStore. Les propriétés système lues par la variable `XSTSValidator` sont résumées ci-dessous :

| Propriété du système | Valeur par défaut | Commentaire |
|---|---|---|
| `xsts-keystore` | `xsts.jks` | Fichier de stockage de clés au format JKS utilisé par le programme de validation. |
| `xsts-keystore-password` | | Mot de passe du KeyStore |
| `xsts-alias` | `xsts` | Alias utilisé pour récupérer la clé de décryptage du KeyStore |
| `xsts-verify-cert-alias` | `xsts-verify-cert` | Alias utilisé pour récupérer le certificat de validation du KeyStore |

