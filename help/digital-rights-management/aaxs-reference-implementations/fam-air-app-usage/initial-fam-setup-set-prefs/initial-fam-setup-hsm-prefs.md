---
seo-title: Préférences HSM
title: Préférences HSM
uuid: 1b97d582-d4b6-48cd-9c24-2d13493571e9
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Préférences HSM {#hsm-preferences}

Les préférences de cet onglet doivent uniquement être spécifiées si la **[!UICONTROL Enable HSM]** case à cocher est activée dans l’onglet Packager. Le tableau suivant décrit ces préférences :

| Préférence | Description |
|---|---|
| Nom du fichier de configuration Sun PKCS#11 | Chemin d’accès complet au fichier de configuration du fournisseur Sun PKCS#11. Consultez le Guide de référence de Java PKCS#11 sur le site Web de Sun pour en savoir plus sur le contenu de ce fichier de configuration. |
| Mot de passe de partition | mot de passe de la partition HSM spécifiée dans le fichier de configuration PKCS#11. |
| Alias de certificat du serveur de licences | Alias du certificat de serveur de licences émis par Adobe stocké sur HSM. Ce certificat est utilisé pour chiffrer le CEK pendant l’emballage. Indiquez cette valeur au lieu du certificat *du serveur de* licences dans l’onglet Packager. |
| Alias de certificat de transport du serveur de licences | Alias du certificat de transport de serveur émis par Adobe stocké sur HSM. Ce certificat permet de sécuriser les communications entre le client et le serveur de licences. Indiquez cette valeur au lieu du certificat *de transport du serveur de* licences dans l’onglet Packager. |
| Alias d’identification de Packager | Alias pour les informations d’identification de packager émises par Adobe (certificat et clé privée) stockées sur HSM. Cette méthode est utilisée pour signer les métadonnées lors de la création de package. Indiquez cette valeur au lieu des informations d’identification *de* Packager dans l’onglet Packager. |
| Alias d’identification du serveur de licences | Alias pour les informations d’identification du serveur de licences émises par Adobe (certificat et clé privée) stockées sur HSM. Ces informations d’identification sont utilisées pour signer des Listes de mise à jour de stratégie. Indiquez cette valeur au lieu des informations d’identification *du serveur de* licences dans l’onglet Liste de mise à jour de la stratégie. (Cet alias sera probablement identique à l’alias *de certificat du serveur de* licences.) |

