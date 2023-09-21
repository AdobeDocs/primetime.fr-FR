---
title: Préférences du module
description: Préférences du module
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# Préférences du module {#packager-preferences}

Cet onglet contient les paramètres requis pour le contenu du package. Le tableau suivant décrit ces préférences :

| Préférence | Description |
|--- |--- |
| Certificat de transport du serveur de licences | Le certificat de transport du serveur, émis par Adobe. Ce certificat est utilisé pour sécuriser les communications entre le client et le serveur de licences. Le fichier doit se trouver dans le répertoire des ressources. |
| Activer HSM | Indique si les certificats et les informations d’identification sont stockés sur un HSM. Si tel est le cas, les préférences relatives aux certificats et aux informations d’identification sont désactivées et les propriétés de l’onglet HSM doivent être spécifiées. |
| Options de chiffrement des clés | Indique comment la clé de chiffrement de contenu est chiffrée au moment du conditionnement. |
| Certificat du serveur de licences | Certificat du serveur de licences, émis par Adobe. Le fichier doit se trouver dans le répertoire des ressources. Le CEK est chiffré avec la clé publique du serveur de licences. Seuls les détenteurs de la clé privée du serveur de licences peuvent déchiffrer le CEK. |
| Informations d’identification de Packager | Informations d’identification du packager, émises par Adobe. Ce fichier est utilisé pour signer les métadonnées lors du conditionnement. |
| Nom du fichier | La variable `PKCS#12` fichier ( .pfx) contenant le certificat et la clé privée. Le fichier doit se trouver dans le répertoire des ressources. |
| Mot de passe du fichier | Mot de passe du fichier .pfx |
| Propriétés globales du dossier de contrôle | Spécifie les paramètres communs à tous les dossiers de contrôle configurés sur ce serveur. |
| Intervalle de vérification en millisecondes | Indique la fréquence à laquelle les dossiers de contrôle doivent rechercher le nouveau contenu à compresser. Le serveur effectue une itération sur tous les dossiers de contrôle configurés, puis dort pendant cette durée. |
| Suffixe du nom du fichier de sortie | Spécifie une extension de fichier à ajouter aux fichiers de sortie. Par exemple, si .out est spécifié et que le fichier d’entrée est video.flv, le fichier de sortie sera video.out.flv. |
| Fichiers d’entrée de sauvegarde | Indique si une copie du contenu d’origine doit être enregistrée. Si cette option n&#39;est pas sélectionnée, le fichier d&#39;origine sera supprimé une fois le package terminé. |
| Input Backup Subfolder Name | Si l’option Sauvegarder les fichiers d’entrée est sélectionnée, indique un dossier dans lequel les fichiers d’entrée seront enregistrés. Cette option spécifie un nom de dossier relatif au répertoire d’entrée du dossier de contrôle. Si le dossier n&#39;existe pas, il sera créé lors du conditionnement. |
| Remplacer les fichiers de sortie existants | Indique si le fichier de sortie peut être remplacé s’il existe déjà un fichier portant le même nom. Si cette option n’est pas sélectionnée et que le fichier de sortie existe déjà, le traitement du fichier d’entrée sera ignoré. |
