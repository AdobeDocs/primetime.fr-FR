---
description: Pour mettre en oeuvre DRM, vous avez besoin de certificats et de clés spécifiques, notamment une clé de chiffrement de contenu ou un CEK pour chiffrer votre contenu, un authentificateur client pour la protection des communications avec les serveurs ExpressPlay et des CEKSID pour identifier vos clés de chiffrement de contenu stockées dans un système de gestion des clés.
title: Clés, identifiants et authentificateurs
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Clés, identifiants et authentificateurs{#keys-ids-and-authenticators}

Pour mettre en oeuvre DRM, vous avez besoin de certificats et de clés spécifiques, notamment une clé de chiffrement de contenu ou un CEK pour chiffrer votre contenu, un authentificateur client pour la protection des communications avec les serveurs ExpressPlay et des CEKSID pour identifier vos clés de chiffrement de contenu stockées dans un système de gestion des clés.

Vous avez besoin de ces éléments pour compresser, acquérir sous licence et lire votre contenu protégé :

## Clé de chiffrement du contenu {#section_8D16D36BAE3B4D1F92A0C43567D782D0}

La clé de chiffrement de contenu (CEK) est une chaîne de 16 octets utilisée pour chiffrer le contenu.

**Qu&#39;est-ce que la CEK ?** - Le CEK est la clé que votre packager utilise pour chiffrer votre contenu. C&#39;est une chaîne codée en hexadécimal de 16 octets.

**D&#39;où vient la CEK ?** - Vous (fournisseur de contenu) créez vous-même cette clé à l’aide d’un outil tel que OpenSSL ou Notepad++. Par exemple :

```
openssl rand 16 -hex > cek_hex_file
```

ou (pour Adobe Offline Packager) :

1. Générez la chaîne codée hexadécimale de 16 octets, comme ci-dessus ou en utilisant un autre outil. Il ressemblera à ceci :

   ```
   7debe705d938c76bfd886f077b8fa5f7
   ```

1. Ouvrez Notepad++ et collez-y la chaîne hexadécimale de 16 octets.
1. Convertissez cette valeur de hex ASCII en Base64-encoding la valeur pour créer votre [!DNL keyfile.bin]. (Cela est couvert par la section [](../../multi-drm-workflows/quick-start/package-your-content.md).)

**Même clé, nom différent ?** - Oui, vous pouvez voir le CEK désigné par d’autres noms à d’autres endroits, par exemple :

* ** [!DNL [some].bin]** - L’Adobe Offline Packager fait référence au CEK en tant que [!DNL [some].bin] ; par exemple, * [!DNL Keyfile.bin]* - Il s’agit de votre CEK utilisé par l’Adobe Offline Packager sous la forme d’un fichier sur la machine que vous utilisez pour le conditionnement du contenu.

  Vous &quot;Base64&quot; votre chaîne hexadécimale de CEK aléatoire et vous l’enregistrez sous forme de fichier (par exemple, [!DNL keyfile.bin]), généralement situé dans la variable [!DNL creds] répertoire sous [!DNL offlinepkgr/]. Dans votre fichier de configuration Packager (par exemple, vous pouvez l’appeler [!DNL widevine.xml] si vous êtes un package pour le DRM Windows), reportez-vous à votre CEK dans votre fichier de configuration comme suit :

  ```
  <config>  
    <in_path>sample.mp4</in_path>  
    <out_type>dash</out_type>
    <b><key_file_path>keyfile.bin</key_file_path></b> // This is your CEK  
    […] 
  </config> 
  ```

* **Clé de contenu** - Vous pouvez également voir le CEK désigné comme clé de contenu dans les appels ( `&contentKey=`), dans les messages d’erreur, dans les tickets d’assistance et dans d’autres documents.

**Quand / où l’utiliser ?**

1. Tout d&#39;abord, vous devez disposer du CEK sur la machine sur laquelle vous faites votre emballage. Votre outil de conditionnement utilise votre CEK pour chiffrer votre contenu.
1. Deuxièmement, vous devez stocker le CEK dans une forme ou une autre de système de gestion des clés (KMS), chaque CEK étant associé à son propre système. [Clé de chiffrement du contenu](../../multi-drm-workflows/glossary/glossary-cek.md). Vous pouvez créer votre propre KMS ou utiliser [Stockage clé ExpressPlay](https://www.expressplay.com/developer/key-storage/). Cela permet à votre storefront (votre serveur de droits, qui gère les droits des clients et les conditions de jeton de licence) d’extraire un jeton de licence pour le client du KMS à l’aide d’un identifiant de clé au lieu du véritable CEK (c’est beaucoup plus sécurisé).

## Identifiant de stockage de clé de chiffrement de contenu {#section_0C94F54970E04BDB82DE3C8A33A62CD4}

L’identifiant de stockage de clé de chiffrement de contenu (CEKSID) identifie de manière unique la clé stockée qui déchiffre un élément de contenu vidéo chiffré.

**Qu&#39;est-ce que le CEKSID ?** - Le CEKSID est l’identifiant unique d’une clé de chiffrement de contenu (CEK). Le CEK est nécessaire pour déverrouiller le contenu protégé ; le CEKSID est nécessaire pour accéder au CEK à partir de l’emplacement de stockage. Lorsque vous testez votre configuration, vous pouvez fournir un CEKSID et un CEK aléatoires au moment de l’assemblage, à condition d’utiliser les mêmes informations pour les contrôles de licence et de lecture.

**D&#39;où vient-il ?** - Vous (fournisseur de contenu) pouvez créer vous-même cet identifiant ou vous pouvez utiliser un service tel que [Stockage clé ExpressPlay](https://www.expressplay.com/developer/key-storage/) pour générer des CEKSID pour chacun de vos CEK (et les stocker tous les deux). De plus, vous pouvez utiliser des CEKSID générés de manière aléatoire ou utiliser un schéma qui correspond à votre modèle d’entreprise. Par exemple, vous pouvez utiliser des SIC qui sont des chaînes significatives plutôt que des chaînes hexadécimales aléatoires (le nom de l’ID peut se composer de sujets, de dates, d’heures, etc.)

**Comment s&#39;appelle le CEKSID ?** - On parle parfois de *Identifiant de contenu*.

## Authentificateur client {#section_F9DDBAA54C544D82A42320CBEEB6CD74}

L’authentificateur client est une clé que vous obtenez d’ExpressPlay lorsque vous y configurez un compte administrateur. L’authentificateur est utilisé dans les communications avec les serveurs ExpressPlay.

**Que sont les authentificateurs de clients ?** - Les deux authentificateurs client constituent la paire d’identifiants — un pour les tests, un pour la production — que ExpressPlay enregistre pour vous lorsque vous vous inscrivez à leur service. Ils sont toujours disponibles sur votre page d’administration ExpressPlay :
<!--<a id="fig_c5h_xdl_wv"></a>-->

![](assets/expressplay_admin_dashboard-web.png)

**Quand dois-je utiliser ceci ?** - Vous incluez cela dans tous les appels aux serveurs ExpressPlay — par exemple, les serveurs de licences, [Stockage clé ExpressPlay](https://www.expressplay.com/developer/key-storage/), ainsi que d’autres appels .
