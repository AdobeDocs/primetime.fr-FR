---
title: Mettre à jour le fichier WAR du serveur de licences
description: Mettre à jour le fichier WAR du serveur de licences
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---


# Mettre à jour le fichier WAR du serveur de licences{#update-the-license-server-war-file}

Afin de prendre en charge les clients qui se sont individualisés via un serveur d’individualisation sur site, vous devez mettre à jour la racine de certificat du serveur de licences pour inclure les informations d’identification d’autorité de certification d’individualisation nouvellement acquises. Un script Python ( [!DNL addIndivCert.py]) est inclus dans le dossier [!DNL update_license_server].

Procédez comme suit pour mettre à jour le serveur de licences :

1. Effectuez une copie des fichiers WAR à mettre à jour (exemples : [!DNL flashaccess.war], [!DNL faxsks.war]).
1. Assurez-vous que les fichiers WAR sont déverrouillés et que leurs autorisations sont définies pour pouvoir être modifiés.
1. Exécutez le script Python [!DNL addIndivCert.py] pour mettre à jour les fichiers WAR du serveur de licences.

   Les entrées du script sont les suivantes :

   * `cert`: Fichier PKCS12 contenant le certificat d’autorité de certification d’individualisation
   * `war`: Fichier WAR à mettre à jour

   Le fichier de sortie est un fichier WAR mis à jour.

   ```
   ./addIndivCert.py -cert NEW_IndivCA.cer -war flashaccess.war
   ```

Les fichiers WAR seront modifiés. Si nécessaire, vous pouvez modifier le script Python en fonction de vos besoins. Après avoir effectué les mises à jour, vous pouvez déployer les fichiers WAR normalement.
