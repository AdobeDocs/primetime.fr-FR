---
description: Pour mettre en oeuvre DRM, vous avez besoin de certificats et de clés particuliers, notamment une clé de chiffrement de contenu ou un CEK pour chiffrer votre contenu, un authentificateur de client pour la protection des communications avec les serveurs ExpressPlay et des CEKSID pour identifier vos clés de chiffrement de contenu stockées dans un système de gestion des clés.
seo-description: Pour mettre en oeuvre DRM, vous avez besoin de certificats et de clés particuliers, notamment une clé de chiffrement de contenu ou un CEK pour chiffrer votre contenu, un authentificateur de client pour la protection des communications avec les serveurs ExpressPlay et des CEKSID pour identifier vos clés de chiffrement de contenu stockées dans un système de gestion des clés.
seo-title: Raccourcis clavier, identifiants et authentificateurs
title: Raccourcis clavier, identifiants et authentificateurs
uuid: 9e5b1a64-b4e9-442f-ac15-26831aaf585d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Raccourcis clavier, identifiants et authentificateurs{#keys-ids-and-authenticators}

Pour mettre en oeuvre DRM, vous avez besoin de certificats et de clés particuliers, notamment une clé de chiffrement de contenu ou un CEK pour chiffrer votre contenu, un authentificateur de client pour la protection des communications avec les serveurs ExpressPlay et des CEKSID pour identifier vos clés de chiffrement de contenu stockées dans un système de gestion des clés.

Vous avez besoin de ces éléments pour créer des packs, activer des licences et lire votre contenu protégé :

## Clé de chiffrement du contenu {#section_8D16D36BAE3B4D1F92A0C43567D782D0}

La clé de chiffrement de contenu (CEK) est une chaîne de 16 octets utilisée pour chiffrer du contenu.

**Qu&#39;est-ce que la CEK ?** - Le CEK est la clé que votre outil de création de package utilise pour chiffrer votre contenu. C&#39;est une chaîne codée en hexadécimal de 16 octets.

**D&#39;où vient la CEK ?** - Vous (fournisseur de contenu) créez vous-même cette clé à l’aide d’un outil tel qu’OpenSSL ou Notepad++. Par exemple :

```
openssl rand 16 -hex > cek_hex_file
```

ou (pour Adobe Offline Packager) :

1. Générez la chaîne codée en hexadécimal de 16 octets, comme ci-dessus ou à l’aide d’un autre outil. Il ressemblera à ceci :

   ```
   7debe705d938c76bfd886f077b8fa5f7
   ```

1. Ouvrez Notepad++ et collez-le dans la chaîne hexadécimale de 16 octets.
1. Convertissez cette valeur d’ASCII hexadécimal en encodant la valeur de base64 pour créer votre [!DNL keyfile.bin]valeur. (Ceci est couvert dans [](../../multi-drm-workflows/quick-start/package-your-content.md).)

**Même clé, nom différent ?** - Oui, vous pouvez voir le CEK mentionné par d&#39;autres noms à d&#39;autres endroits, par exemple :

* ** [ ! DNL [somefile].bin]** - Adobe Offline Packager fait référence au CEK comme [ ! DNL [somefile].bin]; * [!DNL Keyfile.bin]*, par exemple : il s’agit du CEK utilisé par Adobe Offline Packager sous la forme d’un fichier sur l’ordinateur utilisé pour la création de packs de contenu.

   Vous &quot;Base64&quot; votre chaîne hexadécimale CEK aléatoire, et vous l&#39;enregistrez sous forme de fichier (par exemple, [!DNL keyfile.bin]), habituellement situé dans le [!DNL creds] répertoire sous [!DNL offlinepkgr/]. Dans votre fichier de configuration Packager (par exemple, vous pouvez l’appeler [!DNL widevine.xml] si vous effectuez un pack pour le DRM Widevine), vous devez vous référer à votre CEK dans votre fichier de configuration comme suit :

   ```
   <config>  
     <in_path>sample.mp4</in_path>  
     <out_type>dash</out_type>
     <b><key_file_path>keyfile.bin</key_file_path></b> // This is your CEK  
     […] 
   </config> 
   ```

* **Clé** de contenu - Vous pouvez également voir le CEK appelé clé de contenu dans les appels ( `&contentKey=`), les messages d&#39;erreur, les tickets d&#39;assistance et d&#39;autres documents.

**Quand / où l&#39;utiliser ?**

1. Tout d&#39;abord, vous devez disposer du CEK sur la machine sur laquelle vous faites votre emballage. Votre outil d’emballage utilise votre CEK pour chiffrer votre contenu.
1. Deuxièmement, vous devez stocker le CEK sous une forme ou une autre du système de gestion des clés (KMS), chaque CEK étant associé à sa propre clé [de chiffrement de](../../multi-drm-workflows/glossary/glossary-cek.md)contenu. Vous pouvez créer votre propre KMS ou utiliser l&#39;Enregistrement [clé](https://www.expressplay.com/developer/key-storage/)ExpressPlay. Cela permet à votre vitrine (votre serveur de droits, qui gère les droits des clients et la fourniture de jeton de licence) d&#39;extraire un jeton de licence pour le client à partir du KMS en utilisant un ID de clé plutôt que le CEK réel (c&#39;est beaucoup plus sécurisé).

## ID d’Enregistrement clé de chiffrement de contenu {#section_0C94F54970E04BDB82DE3C8A33A62CD4}

L’ID d’Enregistrement de clé de chiffrement de contenu (CEKSID) identifie de manière unique la clé stockée qui déchiffre un élément chiffré de contenu vidéo.

**Qu&#39;est-ce que le CEKSID ?** - Le CEKSID est l&#39;identifiant unique d&#39;une clé de chiffrement de contenu (CEK). Le CEK est nécessaire pour déverrouiller le contenu protégé ; le CEKSID est nécessaire pour accéder au CEK à partir de son emplacement de stockage. Lorsque vous testez votre configuration, vous pouvez fournir un CEKSID et un CEK aléatoires au moment de l’assemblage, à condition d’utiliser les mêmes informations pour les contrôles de licence et de lecture.

**D&#39;où vient-elle ?** - Vous (le fournisseur de contenu) pouvez créer cet identifiant vous-même, ou vous pouvez utiliser un service tel que l&#39;Enregistrement [clé d&#39;](https://www.expressplay.com/developer/key-storage/) ExpressPlay pour générer des SID CEKSID pour chacun de vos CEK (et les stocker tous les deux). De plus, vous pouvez utiliser des CEKSID générés de manière aléatoire ou utiliser un schéma qui correspond à votre modèle d’entreprise. Par exemple, vous pouvez utiliser des SICEK qui sont des chaînes significatives plutôt que des chaînes hexadécimales aléatoires (le nom d’ID peut être composé de sujets, de dates, d’heures, etc.).

**Comment nomme-t-on le CEKSID ?** - Il est parfois appelé ID *de* contenu.

## Authentification du client {#section_F9DDBAA54C544D82A42320CBEEB6CD74}

L’authentificateur de client est une clé que vous obtenez d’ExpressPlay lorsque vous y configurez un compte d’administrateur. L’authentificateur est utilisé dans les communications avec les serveurs ExpressPlay.

**Quels sont les authentificateurs de clients ?** - Les deux authentificateurs de clients constituent la paire d&#39;identifiants — un pour les tests, un pour la production — qu&#39;ExpressPlay enregistre pour vous lorsque vous vous inscrivez à leur service. Ils sont toujours disponibles sur votre page d’administration ExpressPlay :
<!--<a id="fig_c5h_xdl_wv"></a>-->

![](assets/expressplay_admin_dashboard-web.png)

**Quand dois-je utiliser ceci ?** - Vous incluez cela dans tous les appels vers les serveurs ExpressPlay — par exemple, les serveurs de licences, l’Enregistrement [clé](https://www.expressplay.com/developer/key-storage/)ExpressPlay et d’autres appels.
