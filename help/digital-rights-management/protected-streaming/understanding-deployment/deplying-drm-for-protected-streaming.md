---
seo-title: Déploiement d’Adobe Primetime DRM Server pour la diffusion en flux continu protégée
title: Déploiement d’Adobe Primetime DRM Server pour la diffusion en flux continu protégée
uuid: 83ef8237-0026-4677-b42b-ea4b6de19630
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Déploiement d’Adobe Primetime DRM Server pour la diffusion en flux continu protégée{#deploying-the-adobe-primetime-drm-server-for-protected-streaming}

Avant de pouvoir déployer Adobe Primetime DRM Server pour la diffusion en flux continu protégée, vous devez avoir installé les versions de Java et Tomcat comme indiqué dans la rubrique Conditions requises.

Le package Primetime DRM Server for Protected Streaming inclut [!DNL flashaccesserver.war]. Si vous :

* Pour déployer ce fichier WAR, vous devez le copier dans le [!DNL webapps] répertoire de Tomcat.
* Ayant déjà déployé le fichier WAR, vous devrez peut-être supprimer le répertoire WAR décompressé ( [!DNL flashaccessserver] dans le [!DNL webapps] répertoire de Tomcat).

* Pour empêcher Tomcat de décompresser les fichiers WAR, modifiez le [!DNL server.xml] fichier dans le [!DNL conf] répertoire de Tomcat et configurez l’ `unpackWARs` attribut en le définissant sur `false`.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Si vous avez configuré Tomcat pour inclure [!DNL commons-logging.jar] le chemin de classe System (non requis pour le serveur DRM Primetime pour la diffusion en flux continu protégée), vous devez configurer la journalisation des données communes pour utiliser Log4J.

Le serveur utilise éventuellement une bibliothèque spécifique à une plateforme ( [!DNL jsafe.dll] sous Microsoft Windows ou [!DNL libjsafe.so] sous Linux pour des performances optimales. Vous pouvez copier la bibliothèque appropriée pour votre plate-forme depuis la [!DNL thirdparty/cryptoj/]*plateforme *vers un emplacement spécifié par la`PATH`variable  de  ou`LD_LIBRARY_PATH`sous Linux.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Vous ne devez utiliser la version 64 bits que si le système d’exploitation et le JDK prennent en charge la version 64 bits. Sinon, vous devez utiliser la version 32 bits.

