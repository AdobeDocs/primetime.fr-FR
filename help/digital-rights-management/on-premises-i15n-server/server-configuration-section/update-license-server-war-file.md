---
title: Mise à jour du fichier WAR du serveur de licences
description: Mise à jour du fichier WAR du serveur de licences
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---

# Mise à jour du fichier WAR du serveur de licences{#update-the-license-server-war-file}

Pour prendre en charge les clients qui ont été personnalisés par le biais d’un serveur d’individualisation On Premise, vous devez mettre à jour la racine du certificat du serveur de licences afin d’inclure les informations d’identification d’autorité de certification de l’individualisation nouvellement acquises. Un script Python ( [!DNL addIndivCert.py]) est inclus dans la variable [!DNL update_license_server] dossier.

Procédez comme suit pour mettre à jour le serveur de licences :

1. Effectuez une copie des fichiers WAR à mettre à jour (exemples : [!DNL flashaccess.war], [!DNL faxsks.war]).
1. Assurez-vous que les fichiers WAR sont déverrouillés et que leurs autorisations sont définies afin qu’ils puissent être modifiés.
1. Exécutez la variable [!DNL addIndivCert.py] Script Python pour mettre à jour les fichiers WAR du serveur de licences.

   Les entrées pour le script sont les suivantes :

   * `cert`: fichier PKCS12 contenant le certificat d’autorité de certification de l’individualisation
   * `war`: fichier WAR à mettre à jour

   Le fichier de sortie est un fichier WAR mis à jour.

   ```
   ./addIndivCert.py -cert NEW_IndivCA.cer -war flashaccess.war
   ```

Les fichiers WAR seront modifiés sur place. Si nécessaire, vous pouvez modifier le script Python en fonction de vos besoins spécifiques. Après avoir effectué les mises à jour, vous pouvez déployer les fichiers WAR normalement.
