---
description: Pour mettre en oeuvre DRM, vous avez besoin de certificats et de clés spécifiques, y compris une clé de chiffrement de contenu ou un CEK pour chiffrer votre contenu, d’un authentificateur de client pour protéger les communications avec les serveurs ExpressPlay et d’un CEKSID pour identifier vos clés de chiffrement de contenu stockées dans un système de gestion des clés.
seo-description: Pour mettre en oeuvre DRM, vous avez besoin de certificats et de clés spécifiques, y compris une clé de chiffrement de contenu ou un CEK pour chiffrer votre contenu, d’un authentificateur de client pour protéger les communications avec les serveurs ExpressPlay et d’un CEKSID pour identifier vos clés de chiffrement de contenu stockées dans un système de gestion des clés.
seo-title: Clés, identifiants et authentificateurs
title: Clés, identifiants et authentificateurs
uuid: 9e5b1a64-b4e9-442f-ac15-26831aaf585d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Clés, identifiants et authentificateurs{#keys-ids-and-authenticators}

Pour mettre en oeuvre DRM, vous avez besoin de certificats et de clés spécifiques, y compris une clé de chiffrement de contenu ou un CEK pour chiffrer votre contenu, d’un authentificateur de client pour protéger les communications avec les serveurs ExpressPlay et d’un CEKSID pour identifier vos clés de chiffrement de contenu stockées dans un système de gestion des clés.

Vous avez besoin de ces éléments pour créer des packs, activer des licences et lire votre contenu protégé :

## Clé de chiffrement du contenu {#section_8D16D36BAE3B4D1F92A0C43567D782D0}

La clé de chiffrement de contenu (CEK) est une chaîne de 16 octets utilisée pour chiffrer du contenu.

**Qu&#39;est-ce que la CEK ?** - Le CEK est la clé que votre gestionnaire de package utilise pour chiffrer votre contenu. C&#39;est une chaîne codée hexadécimale de 16 octets.

**D&#39;où vient la CEK ?** - Vous (fournisseur de contenu) créez vous-même cette clé à l’aide d’un outil tel qu’OpenSSL ou Notepad++. Par exemple :

```
openssl rand 16 -hex > cek_hex_file
```

ou (pour Adobe Offline Packager) :

1. Générez la chaîne codée hexadécimale de 16 octets, comme ci-dessus ou à l’aide d’un autre outil. Voici à quoi cela ressemblera :

   ```
   7debe705d938c76bfd886f077b8fa5f7
   ```

1. Ouvrez le Bloc-notes++ et collez-le dans la chaîne hexadécimale de 16 octets.
1. Convertissez cette valeur d’ASCII hexadécimal en encodant la valeur Base64 pour créer votre [!DNL keyfile.bin]valeur. (Ceci est couvert par [](../../multi-drm-workflows/quick-start/package-your-content.md).)

**Même clé, autre nom ?** - Oui, vous pouvez voir le CEK mentionné par d&#39;autres noms à d&#39;autres endroits, comme :

* ** [!DNL [somefile].bin]** - Adobe Offline Packager fait référence au CEK comme [!DNL [somefile].bin]; * [!DNL Keyfile.bin]*, par exemple : il s’agit du CEK utilisé par Adobe Offline Packager sous la forme d’un fichier sur l’ordinateur utilisé pour la création de package de contenu.

   Vous &quot;Base64&quot; votre chaîne hexadécimale CEK aléatoire, et vous l&#39;enregistrez sous forme de fichier (par exemple, [!DNL keyfile.bin]), habituellement situé dans le [!DNL creds] répertoire sous [!DNL offlinepkgr/]. Dans votre fichier de configuration Packager (par exemple, vous pouvez l’appeler [!DNL widevine.xml] si vous incluez un pack pour le DRM Widevine), vous faites référence à votre CEK dans votre fichier de configuration comme suit :

   ```
   <config>  
     <in_path>sample.mp4</in_path>  
     <out_type>dash</out_type>
     <b><key_file_path>keyfile.bin</key_file_path></b> // This is your CEK  
     […] 
   </config> 
   ```

* **Clé** de contenu - Vous pouvez également voir le CEK désigné comme clé de contenu dans les appels ( `&contentKey=`), dans les messages d&#39;erreur, dans les tickets d&#39;assistance et dans d&#39;autres documents.

**Quand / où l&#39;utiliser ?**

1. Tout d&#39;abord, vous devez avoir le CEK disponible sur la machine sur laquelle vous faites votre emballage. Votre outil d’emballage utilise votre CEK pour chiffrer votre contenu.
1. Ensuite, vous devez stocker le CEK sous une forme ou une autre du système de gestion des clés (KMS), chaque CEK étant associé à sa propre clé [de chiffrement de](../../multi-drm-workflows/glossary/glossary-cek.md)contenu. Vous pouvez créer votre propre KMS ou utiliser le  clé [ExpressPlay](https://www.expressplay.com/developer/key-storage/). Cela permet à votre vitrine (votre serveur de droits, qui gère les droits du client et la disposition du jeton de licence) d’extraire un jeton de licence pour le client du KMS à l’aide d’un ID de clé au lieu du CEK réel (c’est beaucoup plus sécurisé).

## Clé de chiffrement de contenu  ID de {#section_0C94F54970E04BDB82DE3C8A33A62CD4}

La clé de chiffrement de contenu  l’ID  du (CEKSID) identifie de manière unique la clé stockée qui décrypte un élément chiffré de contenu vidéo.

**Qu&#39;est-ce que le CEKSID ?** - Le CEKSID est l&#39;identifiant unique d&#39;une clé de chiffrement de contenu (CEK). Le CEK est nécessaire pour déverrouiller le contenu protégé; le CEKSID est nécessaire pour accéder au CEK à partir de son emplacement de stockage. Lorsque vous testez votre configuration, vous pouvez fournir un CEKSID et un CEK aléatoires au moment de l’assemblage, à condition d’utiliser les mêmes informations pour les contrôles de licence et de lecture.

**D&#39;où vient-il ?** - Vous (fournisseur de contenu) pouvez créer vous-même cet identifiant ou vous pouvez utiliser un service tel que le de  de clé [ExpressPlay](https://www.expressplay.com/developer/key-storage/) pour générer des SID CEKSID pour chacun de vos CEK (et les stocker tous les deux). De plus, vous pouvez utiliser des CEKSID générés de manière aléatoire ou utiliser un schéma qui correspond à votre modèle d’entreprise. Par exemple, vous pouvez utiliser des CEKSID qui sont des chaînes significatives plutôt que des chaînes hexadécimales aléatoires (le nom d’ID peut être composé de sujets, de dates, d’heures, etc.)

**Comment nomme-t-on le CEKSID ?** - Il est parfois appelé ID *de* contenu.

## Authentification du client {#section_F9DDBAA54C544D82A42320CBEEB6CD74}

L’authentificateur de client est une clé que vous obtenez d’ExpressPlay lorsque vous y configurez un compte administrateur. L’authentificateur est utilisé dans les communications avec les serveurs ExpressPlay.

**Quels sont les authentificateurs du client ?** - Les deux authentificateurs de clients constituent la paire d&#39;identifiants — un pour les essais, un pour la production .. que ExpressPlay s&#39;enregistre pour vous lorsque vous vous inscrivez à leur service. Ils sont toujours disponibles sur votre page d’administration ExpressPlay :
<!--<a id="fig_c5h_xdl_wv"></a>-->

![](assets/expressplay_admin_dashboard-web.png)

**Quand est-ce que j&#39;utilise ça ?** - Vous incluez cela dans tous les appels aux serveurs ExpressPlay — par exemple, les serveurs de licences, le [ExpressPlay Key ](https://www.expressplay.com/developer/key-storage/)et d’autres appels.
