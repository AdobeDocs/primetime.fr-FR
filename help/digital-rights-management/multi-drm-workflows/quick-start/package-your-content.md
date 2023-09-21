---
description: L’assemblage de contenu est le processus de préparation du contenu vidéo en vue de la lecture sur le Web. Le groupement comprend la transformation de la vidéo brute en fichiers manifestes et, éventuellement, le chiffrement du contenu à l’aide de différentes solutions DRM pour différents appareils et navigateurs.
title: Mettre en package votre contenu
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---

# Mettre en package votre contenu {#package-your-content}

L’assemblage de contenu est le processus de préparation du contenu vidéo en vue de la lecture sur le Web. Le groupement comprend la transformation de la vidéo brute en fichiers manifestes et, éventuellement, le chiffrement du contenu à l’aide de différentes solutions DRM pour différents appareils et navigateurs.

Pour préparer votre contenu, vous pouvez utiliser Adobe Offline Packager ou d’autres outils tels que le package Bento4 ExpressPlay. Les packages préparent la vidéo pour la lecture (par exemple, la fragmentation du fichier d’origine et sa mise dans un manifeste) et protègent la vidéo avec la solution DRM que vous avez choisie (PlayReady, Widevine, FairPlay, Access, etc.).:

* [Adobe Offline Packager](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf)
* [Packagers ExpressPlay](https://www.expressplay.com/developer/packaging-tools/)

<!--<a id="fig_jbn_fw5_xw"></a>-->

![](assets/pkg_lic_play_web.png)

1. Empaqueter ou obtenir un autre contenu à utiliser pour tester votre configuration.

   L’un des points essentiels à retenir pour le package est que l’ID de clé (ID de contenu) que vous utilisez dans cette étape de package est le même que celui que vous devez fournir dans votre demande de jeton de licence suivante. L’identifiant de clé est le seul élément qui identifie votre CEK (qui peut être stocké dans votre propre base de données de gestion des clés ou stocké à l’aide de [Service de stockage clé ExpressPlay](https://www.expressplay.com/developer/key-storage/).

   >[!NOTE]
   >
   >Pour ceux qui connaissent bien Adobe Access, il s’agit d’une différence importante dans le fonctionnement des différentes solutions. Dans Access, la clé de licence est incorporée dans les métadonnées DRM et transmise avec le contenu protégé. Dans les systèmes multi-DRM décrits ici, la licence réelle n’est pas transmise, mais stockée en toute sécurité et obtenue via l’identifiant de clé.

<!--<a id="example_52AF76B730174B79B6088280FCDF126D"></a>-->

Voici un exemple de package utilisant Adobe Offline Packager pour Windows. Le Packager utilise un fichier de configuration (par exemple, [!DNL widevine.xml]), qui ressemble à ceci :

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

* `in_path` - Cette entrée indique l’emplacement de la vidéo source sur votre machine locale d’emballage.
* `out_type` - Cette entrée décrit le type de la sortie empaquetée, dans ce cas, DASH (pour la protection Windows sur HTML5).
* `out_path` - Emplacement sur l’ordinateur local sur lequel vous souhaitez que la sortie s’effectue.
* `drm_sys` - La solution DRM que vous proposez. Cela sera soit `widevine`, `fairplay`, ou `playready`.

* `frag_dur` et `target_dur` sont des entrées de durée spécifiques à DASH relatives à la lecture vidéo.

* `key_file_path` - Il s’agit de l’emplacement du fichier de licence sur votre ordinateur de package qui sert de clé de chiffrement de contenu (CEK). Il s’agit d’une chaîne hexadécimale de 16 octets codée en base 64.
* `widevine_content_id` - Ceci est &quot;standard&quot; de Widevine ; il est toujours `2a`. (Ne confondez pas cela avec la variable `widevine_key_id`.)

* `widevine_provider` - À nos fins, définissez toujours cette variable sur `intertrust`.

* `widevine_key_id` - Il s’agit de l’identifiant de la licence que vous avez spécifiée dans la variable `key_file_path` entrée . En d’autres termes, ceci identifie la clé que vous utilisez pour chiffrer le contenu. Cet identifiant est une chaîne HEX de 16 octets que vous créez vous-même.

Comme indiqué dans la variable [Documentation sur Packager](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf), &quot;Il est recommandé de créer un fichier de configuration contenant les options courantes que vous souhaitez utiliser pour générer les sorties. Créez ensuite la sortie en fournissant des options spécifiques sous forme d’argument de ligne de commande.&quot; Dans ce cas, notre fichier de configuration est assez complet. Vous pouvez donc créer votre sortie comme suit :

```
java -jar OfflinePackager.jar -conf_path widevine.xml -out_path test_dash/ 
```

>[!NOTE]
>
>Les paramètres de ligne de commande ont la priorité sur les paramètres du fichier de configuration. Dans cet exemple, tout ce qui est nécessaire se trouve dans le fichier de configuration, mais nous avons remplacé le chemin de sortie spécifié dans le fichier de configuration par `-out_path test_dash/`.
