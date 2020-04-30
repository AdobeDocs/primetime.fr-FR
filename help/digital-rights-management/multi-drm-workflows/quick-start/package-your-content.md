---
description: La création de packages de contenu est le processus de préparation de contenu vidéo en vue d’une lecture sur le Web. La création de package comprend la transformation de la vidéo brute en fichiers manifestes et, éventuellement, le chiffrement du contenu à l’aide de différentes solutions DRM pour différents périphériques et navigateurs.
seo-description: La création de packages de contenu est le processus de préparation de contenu vidéo en vue d’une lecture sur le Web. La création de package comprend la transformation de la vidéo brute en fichiers manifestes et, éventuellement, le chiffrement du contenu à l’aide de différentes solutions DRM pour différents périphériques et navigateurs.
seo-title: Assemblage de votre contenu
title: Assemblage de votre contenu
uuid: b9bc6104-a1ea-4ea0-a0a4-af8a606e5d47
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# Assemblage de votre contenu {#package-your-content}

La création de packages de contenu est le processus de préparation de contenu vidéo en vue d’une lecture sur le Web. La création de package comprend la transformation de la vidéo brute en fichiers manifestes et, éventuellement, le chiffrement du contenu à l’aide de différentes solutions DRM pour différents périphériques et navigateurs.

Pour préparer votre contenu, vous pouvez utiliser Adobe Offline Packager ou d’autres outils tels que le programme d’assemblage Bento4 d’ExpressPlay. Les Packagers préparent la vidéo pour la lecture (par exemple, fragmentation du fichier d’origine et placement de celui-ci dans un manifeste) et protègent la vidéo avec la solution DRM que vous avez choisie (PlayReady, Widevine, FairPlay, Access, etc.).:

* [Adobe Offline Packager](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf)
* [Packagers ExpressPlay](https://www.expressplay.com/developer/packaging-tools/)

<!--<a id="fig_jbn_fw5_xw"></a>-->

![](assets/pkg_lic_play_web.png)

1. Empaquetez ou obtenez du contenu à utiliser pour tester votre configuration.

   L’un des points essentiels à retenir pour le pack est que l’ID de clé (ID de contenu) que vous utilisez dans cette étape du pack est le même que celui que vous devez fournir dans votre demande de jeton de licence ultérieure. L&#39;ID de clé est le seul élément qui identifie votre CEK (qui peut être stocké dans votre propre base de données de gestion des clés, ou stocké à l&#39;aide du service [d&#39;Enregistrement clé](https://www.expressplay.com/developer/key-storage/)ExpressPlay.

   >[!NOTE]
   >
   >Pour ceux qui connaissent bien Adobe Access, il s’agit d’une différence importante dans le fonctionnement des différentes solutions. Dans Access, la clé de licence est incorporée dans les métadonnées DRM et transmise à l’aide du contenu protégé. Dans les systèmes Multi-DRM décrits ici, la licence réelle n&#39;est pas transmise, mais stockée en toute sécurité et obtenue via l&#39;ID de clé.

<!--<a id="example_52AF76B730174B79B6088280FCDF126D"></a>-->

Voici un exemple d’assemblage utilisant Adobe Offline Packager pour Windows. L’outil Packager utilise un fichier de configuration ( [!DNL widevine.xml]par exemple) qui ressemble à ce qui suit :

```
<config> 
<in_path>sample.mp4</in_path> 
<out_type>dash</out_type> 
<out_path>dash2</out_path> 
<drm/> 
<drm_sys>widevine</drm_sys> 
<frag_dur>4</frag_dur> 
<target_dur>6</target_dur> 
<key_file_path>keyfile.bin</key_file_path> 
<widevine_content_id>2a</widevine_content_id> 
<widevine_provider>intertrust</widevine_provider> 
<widevine_key_id>7debe705d938c76bfd886f077b8fa5f7</widevine_key_id> 
</config>
```

* `in_path` - Cette entrée indique l&#39;emplacement de la vidéo source sur votre machine d&#39;emballage locale.
* `out_type` - Cette entrée décrit le type de sortie emballée, dans ce cas DASH (pour la protection Widevine au format HTML5).
* `out_path` - L&#39;emplacement sur la machine locale où vous voulez que votre sortie aille.
* `drm_sys` - La solution DRM que vous incluez dans votre pack. Ce sera soit `widevine`, `fairplay`, soit `playready`.

* `frag_dur` et `target_dur` sont des entrées de durée spécifiques à DASH relatives à la lecture vidéo.

* `key_file_path` - Il s’agit de l’emplacement du fichier de licence sur votre machine de conditionnement qui sert de clé de chiffrement de contenu (CEK). Il s’agit d’une chaîne hexadécimale codée en base 64 et codée sur 16 octets.
* `widevine_content_id` - Il s&#39;agit de &quot;boilerplate&quot; de Widevine ; c&#39;est toujours `2a`. (Ne confondez pas ceci avec le `widevine_key_id`.)

* `widevine_provider` - Pour nos besoins, toujours régler sur `intertrust`.

* `widevine_key_id` - Identificateur de la licence que vous avez spécifiée dans l&#39; `key_file_path` entrée. En d’autres termes, cette méthode identifie la clé que vous utilisez pour chiffrer le contenu. Cet identifiant est une chaîne HEX de 16 octets que vous créez vous-même.

Comme indiqué dans la documentation [de](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf)Packager, &quot;Il est recommandé de créer un fichier de configuration contenant les options courantes que vous souhaitez utiliser pour générer les sorties. Ensuite, créez la sortie en fournissant des options spécifiques sous forme d&#39;argument de ligne de commande.&quot; Dans ce cas, notre fichier de configuration est assez complet. Vous pouvez donc créer votre sortie comme suit :

```
java -jar OfflinePackager.jar -conf_path widevine.xml -out_path test_dash/ 
```

>[!NOTE]
>
>Les paramètres de ligne de commande ont priorité sur les paramètres de fichier de configuration. Dans cet exemple, tout ce qui est nécessaire se trouve dans le fichier de configuration, mais nous avons remplacé le chemin de sortie spécifié dans le fichier de configuration par `-out_path test_dash/`.

