---
description: Ce flux de travaux multi-DRM vous guide tout au long de la configuration, de l’emballage, de la licence et de la lecture de contenu DASH chiffré avec Widevine et PlayReady.
seo-description: Ce flux de travaux multi-DRM vous guide tout au long de la configuration, de l’emballage, de la licence et de la lecture de contenu DASH chiffré avec Widevine et PlayReady.
seo-title: Flux de travaux multiDRM pour Windows et PlayReady
title: Flux de travaux multiDRM pour Windows et PlayReady
uuid: 295a7024-353c-4ff5-a46a-927020834322
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# Flux de travaux multiDRM pour Windows et PlayReady {#multi-drm-workflow-for-widevine-and-playready}

Ce flux de travaux multi-DRM vous guide tout au long de la configuration, de l’emballage, de la licence et de la lecture de contenu DASH chiffré avec Widevine et PlayReady.

Primetime TVSDK prend en charge la lecture de contenu DASH chiffré par Widevine ou PlayReady sur HTML5 et Android uniquement dans TVSDK version 2.X. Le chiffrement du contenu DASH est défini par la spécification Common Encryption, dont les détails complets ne relèvent pas du présent document. Cette section fournit des détails pertinents sur le format DASH, la spécification de chiffrement et des informations sur certains des outils que vous pouvez utiliser pour générer le contenu pris en charge.

>[!NOTE]
>
>Aucun plan n&#39;a été fait pour renvoyer vers Android TVSDK 1.X la lecture du contenu DASH chiffré à l&#39;aide de la technologie Widevine.

## Contenu DASH et chiffrement commun en un coup d&#39;oeil {#section_33A881158F724835B4B89AAE97302B17}

Le contenu du tiret est constitué d’un manifeste principal, écrit en xml, qui pointe vers les fichiers vidéo et audio à lire. Dans l’exemple ci-dessous, le manifeste DASH pointe vers une URL de vidéo, video/1080_30.mp4, et une URL audio, audio/1080_30.mp4, par rapport à l’URL du manifeste.

```
<MPD xmlns="urn:mpeg:DASH:schema:MPD:2011" xmlns:cenc="urn:mpeg:cenc:2013" xmlns:scte35="urn:scte:scte35:2013" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"mediaPresentationDuration="PT30S" minBufferTime="PT8S" profiles="urn:mpeg:dash:profile:isoff-on-demand:2011" type="static" xsi:schemaLocation="urn:mpeg:DASH:schema:MPD:2011 DASH-MPD.xsd">
    <Period id="1" start="PT0S">
        <AdaptationSet bitstreamSwitching="true" contentType="video" id="1" segmentAlignment="true" startWithSAP="2">
            <Representation bandwidth="4215100" codecs="avc1.4d4029" height="1080" id="1" mimeType="video/mp4" width="1920">
                <BaseURL>video/1080_30.mp4</BaseURL>
                <CueInfo schemeIdUri="urn:adobe:mpeg:dash:cueinfo:2012"/>
            </Representation>
        </AdaptationSet>
 
        <AdaptationSet bitstreamSwitching="true" contentType="audio" id="2" segmentAlignment="1" startWithSAP="1">
            <Representation bandwidth="320600" codecs="mp4a.40.02" id="1" mimeType="audio/mp4">
                <BaseURL>audio/1080_30.mp4</BaseURL>
                <CueInfo schemeIdUri="urn:adobe:mpeg:dash:cueinfo:2012"/>
            </Representation>
        </AdaptationSet>
    </Period>
</MPD>
```

Vous trouverez ci-dessous un exemple de manifeste auquel le chiffrement commun est appliqué. Les éléments XML de protection de contenu Widevine (les blocs `<ContentProtection>`) du manifeste contiennent une zone pssh codée en base64 (en-tête spécifique du système de protection). La zone Pssh contient les données nécessaires à l’initialisation du déchiffrement du contenu. Ces données sont également intégrées au contenu vidéo/audio auquel le manifeste fait référence. Le contenu DASH peut comporter plusieurs éléments de protection du contenu, par exemple 1 pour PlayReady et 1 pour Widevine.

```
<?xml version="1.0" ?>
<MPD mediaPresentationDuration="PT3M35.533S" minBufferTime="PT15.00S" profiles="urn:mpeg:dash:profile:isoff-live:2011" type="static" xmlns="urn:mpeg:dash:schema:mpd:2011" xmlns:cenc="urn:mpeg:cenc:2013">
  <!-- Created with Bento4 mp4-dash.py, VERSION=1.6.0-607 -->
  <Period>
    <!-- Audio -->
    <AdaptationSet mimeType="audio/mp4" segmentAlignment="true" startWithSAP="1">
      <!-- Common Encryption -->
      <ContentProtection cenc:default_KID="9e828b37-842d-9f71-0233-c007fb1d4f5b" schemeIdUri="urn:mpeg:dash:mp4protection:2011" value="cenc"/>
      <!-- Widevine -->
      <ContentProtection schemeIdUri="urn:uuid:edef8ba9-79d6-4ace-a3c8-27dcd51d21ed">
        <cenc:pssh>
        AAAAQ3Bzc2gAAAAA7e+LqXnWSs6jyCfc1R0h7QAAACMIARIQnoKLN4Qtn3ECM8AH+x1PWxoKaW50ZXJ0cnVzdCIBKg==
        </cenc:pssh>
      </ContentProtection>
      <Representation audioSamplingRate="44100" bandwidth="200429" codecs="mp4a.40.2" id="audio/und">
        <AudioChannelConfiguration schemeIdUri="urn:mpeg:dash:23003:3:audio_channel_configuration:2011" value="2"/>
        <SegmentList duration="15000" timescale="1000">
          <Initialization sourceURL="audio/und/init.mp4"/>
          <SegmentURL media="audio/und/seg-1.m4f"/>
          <SegmentURL media="audio/und/seg-2.m4f"/>
          <SegmentURL media="audio/und/seg-3.m4f"/>
          <SegmentURL media="audio/und/seg-4.m4f"/>
          <SegmentURL media="audio/und/seg-5.m4f"/>
          <SegmentURL media="audio/und/seg-6.m4f"/>
          <SegmentURL media="audio/und/seg-7.m4f"/>
          <SegmentURL media="audio/und/seg-8.m4f"/>
          <SegmentURL media="audio/und/seg-9.m4f"/>
          <SegmentURL media="audio/und/seg-10.m4f"/>
          <SegmentURL media="audio/und/seg-11.m4f"/>
          <SegmentURL media="audio/und/seg-12.m4f"/>
          <SegmentURL media="audio/und/seg-13.m4f"/>
          <SegmentURL media="audio/und/seg-14.m4f"/>
          <SegmentURL media="audio/und/seg-15.m4f"/>
          <SegmentURL media="audio/und/seg-16.m4f"/>
        </SegmentList>
      </Representation>
    </AdaptationSet>
 
    <!-- Video -->
    <AdaptationSet maxHeight="720" maxWidth="1280" mimeType="video/mp4" minHeight="720" minWidth="1280" segmentAlignment="true" startWithSAP="1">
      <!-- Common Encryption -->
      <ContentProtection cenc:default_KID="9e828b37-842d-9f71-0233-c007fb1d4f5b" schemeIdUri="urn:mpeg:dash:mp4protection:2011" value="cenc"/>
      <!-- Widevine -->
      <ContentProtection schemeIdUri="urn:uuid:edef8ba9-79d6-4ace-a3c8-27dcd51d21ed">
        <cenc:pssh>
        AAAAQ3Bzc2gAAAAA7e+LqXnWSs6jyCfc1R0h7QAAACMIARIQnoKLN4Qtn3ECM8AH+x1PWxoKaW50ZXJ0cnVzdCIBKg==
        </cenc:pssh>
      </ContentProtection>
 
      <Representation bandwidth="2640920" codecs="avc1.64001F" frameRate="30" height="720" id="video/1" scanType="progressive" width="1280">
        <SegmentList duration="15000" timescale="1000">
          <Initialization sourceURL="video/1/init.mp4"/>
          <SegmentURL media="video/1/seg-1.m4f"/>
          <SegmentURL media="video/1/seg-2.m4f"/>
          <SegmentURL media="video/1/seg-3.m4f"/>
          <SegmentURL media="video/1/seg-4.m4f"/>
          <SegmentURL media="video/1/seg-5.m4f"/>
          <SegmentURL media="video/1/seg-6.m4f"/>
          <SegmentURL media="video/1/seg-7.m4f"/>
          <SegmentURL media="video/1/seg-8.m4f"/>
          <SegmentURL media="video/1/seg-9.m4f"/>
          <SegmentURL media="video/1/seg-10.m4f"/>
          <SegmentURL media="video/1/seg-11.m4f"/>
          <SegmentURL media="video/1/seg-12.m4f"/>
          <SegmentURL media="video/1/seg-13.m4f"/>
          <SegmentURL media="video/1/seg-14.m4f"/>
          <SegmentURL media="video/1/seg-15.m4f"/>
        </SegmentList>
      </Representation>
    </AdaptationSet>
  </Period>
</MPD>
```

Observez que le premier exemple ci-dessus fait référence à un seul fichier pour chaque flux, tandis que le second fait référence à une série de petits fragments de contenu. Au lieu de faire explicitement référence à des fragments, vous pouvez également définir un modèle de fragment, par exemple :

```
<Representation bandwidth="348000" codecs="avc1.42c01e" height="360" id="1" width="640">
    <BaseURL>video/</BaseURL>
    <SegmentTemplate initialization="JaigoInit.mp4" media="Jaigo$Number$.m4s" startNumber="0" timescale="1000">
        <SegmentTimeline>
            <S d="4538" t="0"/>
            <S d="4304" t="4538"/>
            <S d="4004" t="8842"/>
            <S d="2102" t="12846"/>
        </SegmentTimeline>
    </SegmentTemplate>
</Representation>
```

Dans ce cas, l’analyseur de contenu (TVSDK) s’attend à trouver du contenu vidéo à Jaigo0.m4s, Jaigo1.m4s, Jaigo2.m4s, etc. Il est principalement utilisé pour la diffusion en direct en flux continu et présente l’avantage de ne pas demander au client de télécharger à nouveau le manifeste de temps en temps.
