---
seo-title: Mettre à jour le fichier WAR du serveur de licences
title: Mettre à jour le fichier WAR du serveur de licences
uuid: 0cde53d6-185d-4bf2-84fc-0c31d17904a8
translation-type: tm+mt
source-git-commit: 1547eb3dd220fafc08df923f40504736c16a866c

---


# Mettre à jour le fichier WAR du serveur de licences{#update-the-license-server-war-file}

Afin de prendre en charge les clients qui se sont individualisés via un serveur d’individualisation sur site, vous devez mettre à jour la racine de certificat du serveur de licences pour inclure les informations d’identification d’autorité de certification d’individualisation nouvellement acquises. Un script Python ( [!DNL addIndivCert.py]) est inclus dans le [!DNL update_license_server] dossier.

Procédez comme suit pour mettre à jour le serveur de licences :

1. Effectuez une copie des fichiers WAR à mettre à jour (exemples : [!DNL flashaccess.war], [!DNL faxsks.war]).
1. Assurez-vous que les fichiers WAR sont déverrouillés et que leurs autorisations sont définies pour pouvoir être modifiés.
1. Exécutez le script [!DNL addIndivCert.py] Python pour mettre à jour les fichiers WAR de License Server.

   Les entrées du script sont les suivantes :

   * `cert`: Fichier PKCS12 contenant le certificat d’autorité de certification d’individualisation
   * `war`: Fichier WAR à mettre à jour
   Le fichier de sortie est un fichier WAR mis à jour.

   ```
   ./addIndivCert.py -cert NEW_IndivCA.cer -war flashaccess.war
   ```

Les fichiers WAR seront modifiés. Si nécessaire, vous pouvez modifier le script Python en fonction de vos besoins. Après avoir effectué les mises à jour, vous pouvez déployer les fichiers WAR normalement.
