---
seo-title: Validation du jeton Xbox Live XSTS
title: Validation du jeton Xbox Live XSTS
uuid: 9647f8ee-32d6-4bed-bae2-8b36a72d04ce
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Validation du jeton Xbox Live XSTS{#xbox-live-xsts-token-validation}

Pour les requêtes XSTS, le `customerSpecificAuthToken` champ contient le jeton XSTS codé en Base64. L&#39;exemple de `XSTSValidator` code examine le jeton décodé Base64 pour déterminer l&#39;existence de l&#39; `EncryptedAssertion` élément ; toutefois, vous pouvez utiliser d’autres méthodes pour faire la distinction entre ces requêtes et les requêtes non Xbox. Par exemple, vous pouvez utiliser une autre URL.

La stratégie renvoyée dans le message de réponse remplacera la stratégie d&#39;origine dans les métadonnées DRM fournies avec la demande de clé Xbox. Seul un sous-ensemble de fonctionnalités de stratégie est pris en charge par le client Xbox, et ces champs sont les seuls à remplacer la stratégie d&#39;origine.

D’autres étapes de configuration sont nécessaires pour prendre en charge le déchiffrement et la validation des jetons. Vous devez charger les informations d’ [!DNL xsts_partner_cert.pfx] identification [!DNL x_secure_token_service.part.xboxlive.com.cer] et dans un fichier de stockage de clés au format JKS, que vous fournissez ensuite à votre serveur de droits principal en tant que propriété système `xsts-keystore`. Par défaut, le partenaire [!DNL .pfx] possède l’alias `xsts`et le certificat de validation de jeton l’a `xsts-verify-cert`. Vous pouvez également les remplacer à l’aide des propriétés système. Enfin, il existe une propriété système `xsts-keystore-password` qui n’a pas de valeur par défaut et qui contient le mot de passe du fichier de stockage des clés. Les propriétés système lues par le `XSTSValidator` code sont résumées ci-dessous :

| Propriété système | Valeur par défaut | Commentaire |
|---|---|---|
| `xsts-keystore` | `xsts.jks` | Fichier de stockage de clés au format JKS utilisé par le programme de validation. |
| `xsts-keystore-password` |  | Mot de passe du fichier de stockage des clés |
| `xsts-alias` | `xsts` | Alias utilisé pour récupérer la clé de déchiffrement dans le fichier de stockage des clés |
| `xsts-verify-cert-alias` | `xsts-verify-cert` | Alias utilisé pour récupérer le certificat de validation dans le fichier de stockage des clés |

