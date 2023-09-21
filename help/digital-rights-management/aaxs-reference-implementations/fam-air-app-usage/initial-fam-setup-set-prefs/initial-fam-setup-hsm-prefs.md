---
title: Préférences HSM
description: Préférences HSM
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# Préférences HSM {#hsm-preferences}

Les préférences de cet onglet ne doivent être spécifiées que si la variable **[!UICONTROL Enable HSM]** est sélectionnée dans l’onglet Packager. Le tableau suivant décrit ces préférences :

| Préférence | Description |
|---|---|
| Nom du fichier de configuration Sun PKCS#11 | Chemin d’accès complet au fichier de configuration du fournisseur Sun PKCS#11. Pour plus d’informations sur le contenu de ce fichier de configuration, consultez le Guide de référence de Java PKCS#11 sur le site web de Sun. |
| Mot de passe de partition | Mot de passe de la partition HSM spécifiée dans le fichier de configuration PKCS#11. |
| Alias du certificat du serveur de licences | Alias du certificat du serveur de licences émis par un Adobe stocké sur HSM. Ce certificat est utilisé pour chiffrer le CEK pendant le conditionnement. Spécifiez plutôt *Certificat du serveur de licences* dans l’onglet Packager . |
| Alias du certificat de transport du serveur de licences | Alias du certificat de transport de serveur émis par l’Adobe stocké sur HSM. Ce certificat est utilisé pour sécuriser les communications entre le client et le serveur de licences. Spécifiez plutôt *Certificat de transport du serveur de licences* dans l’onglet Packager . |
| Alias d’informations d’identification de Packager | Alias des informations d’identification du package (certificat et clé privée) émises par l’Adobe stockées sur HSM. Il est utilisé pour signer les métadonnées lors du conditionnement. Spécifiez plutôt *Informations d’identification de Packager* dans l’onglet Packager . |
| Alias d’identification du serveur de licences | Alias des informations d’identification du serveur de licences (certificat et clé privée) délivrées par l’Adobe stockées sur HSM. Ces informations d’identification sont utilisées pour signer les listes de mise à jour de stratégie. Spécifiez plutôt *Informations d’identification du serveur de licences* dans l’onglet Liste à jour des stratégies . (Cet alias sera probablement le même que *Alias du certificat du serveur de licences*.) |
