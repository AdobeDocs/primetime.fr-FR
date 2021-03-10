---
description: Si le client demande des informations de suivi, le serveur de manifeste renvoie un fichier formaté. Son format et son contenu dépendent de la valeur du paramètre de requête pttrackingversion
seo-description: Si le client demande des informations de suivi, le serveur de manifeste renvoie un fichier formaté. Son format et son contenu dépendent de la valeur du paramètre de requête pttrackingversion
seo-title: Format VMAP pour les URL de suivi
title: Format VMAP pour les URL de suivi
uuid: e3173fad-caa2-49cb-9a65-631573812e52
translation-type: tm+mt
source-git-commit: e437f4143fb939f46d106c64efc391137c33fe17
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

---


# Format VMAP pour les URL de suivi {#vmap-format-for-tracking-urls}

Si le client demande des informations de suivi, le serveur de manifeste renvoie un fichier formaté. Son format et son contenu dépendent de la valeur du paramètre de requête `pttrackingversion`

## Format VMAP unique {#vmap}

Le fichier VMAP que le serveur de manifeste envoie si `pttrackingversion=vmap` a le format de l&#39;exemple suivant, qui provient d&#39;un bloc VMAP type. Il a été raccourci pour éviter toute répétition inutile, de sorte que la structure soit plus claire. Une ellipse (trois points, séparés par des espaces) indique l’omission d’informations dans certaines URL et entre certains blocs de code. Les URL non abrégées s’affichent sur plusieurs lignes, bien qu’elles s’affichent sur une seule ligne dans le fichier VMAP.

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?> 
<vmap:VMAP version="1.0.1" xmlns:vmap="https://www.iab.net/videosuite/vmap"> 
<vmap:AdBreak timeOffset="00:00:00.000" breakType="linear" breakId="0"> 
<vmap:AdSource><vmap:VASTAdData><VAST version="3.0"> 
<Ad id="334690" sequence="1"><InLine> 
<AdSystem>Auditude</AdSystem><AdTitle>lee_pre_266647</AdTitle> 
<Impression>https://ad.auditude.com/adserver/e? 
    type=adimp&a=334690&w=200&uid=hm7f2YHSQxiOqp1dNVqevw& 
    u=cecebae72a919de350b9ac52602623f3& 
    t=1476120645&s=d4b8307&z=266647&cid=1270337971&br=1& 
    pod=id:1,ctype:l,ptype:p,dur:150,lot:5,cpos:1&sq=1&ax=0,0,0,0 
</Impression> 
<Creatives> 
  <Creative AdID="334690"><Linear><Duration>00:00:15.139</Duration> 
    <TrackingEvents> 
      <Tracking event="creativeView">https://ad.auditude.com/adserver/i/; 
                       uid=hm7f2YHSQxiOqp1dNVqevw;u=cecebae72a919de350b9ac52602623f3; 
                       t=1476120645;s=d4b8307;z=266647;cid=1270337971;br=1; 
                       pod=id:1,ctype:l,ptype:p,dur:150,lot:5,cpos:1;sq=1;ax=0,0,0,0; 
                       a1=105;a=334690;w=200/c340x192.m3u8 
      </Tracking> 
      <Tracking event="start">https://ad.auditude.com/adserver/e?type=AD_PROGRESS& 
                       a=334690&a1=105&ref=urn:asset:334690:105&unit=percent& 
                       progress=0&uid=hm7f2YHSQxiOqp1dNVqevw& 
                       u=cecebae72a919de350b9ac52602623f3& 
                       t=1476120645&s=d4b8307&z=266647&cid=1270337971&br=1& 
                       pod=id:1,ctype:l,ptype:p,dur:150,lot:5,cpos:1&sq=1&ax=0,0,0,0 
      </Tracking> 
      <Tracking event="start">https://dpm.demdex.net/ibs:dpid=22619& 
                       dpuuid=hm7f2YHSQxiOqp1dNVqevw 
      </Tracking> 
      <Tracking event="firstQuartile">https://ad.auditude.com/adserver/e? 
                       type=AD_PROGRESS&a=334690&a1=105&ref=urn:asset:334690:105& 
                       unit=percent&progress=25& 
                       uid=hm7f2YHSQxiOqp1dNVqevw&u=cecebae72a919de350b9ac52602623f3& 
                       t=1476120645&s=d4b8307&z=266647&cid=1270337971&br=1& 
                       pod=id:1,ctype:l,ptype:p,dur:150,lot:5,cpos:1&sq=1&ax=0,0,0,0 
      </Tracking> 
      <Tracking event="midpoint">https://ad.auditude.com/adserver/e? 
                       type=AD_PROGRESS&a=334690&a1=105&ref=urn:asset:334690:105& 
                       unit=percent&progress=50& 
                       uid=hm7f2YHSQxiOqp1dNVqevw&u=cecebae72a919de350b9ac52602623f3& 
                       t=1476120645&s=d4b8307&z=266647&cid=1270337971&br=1& 
                       pod=id:1,ctype:l,ptype:p,dur:150,lot:5,cpos:1&sq=1&ax=0,0,0,0 
      </Tracking> 
      <Tracking event="thirdQuartile">https://ad.auditude.com/adserver/e? 
                       type=AD_PROGRESS&a=334690&a1=105&ref=urn:asset:334690:105& 
                       unit=percent&progress=75& 
                       uid=hm7f2YHSQxiOqp1dNVqevw&u=cecebae72a919de350b9ac52602623f3& 
                       t=1476120645&s=d4b8307&z=266647&cid=1270337971&br=1& 
                       pod=id:1,ctype:l,ptype:p,dur:150,lot:5,cpos:1&sq=1&ax=0,0,0,0 
      </Tracking> 
      <Tracking event="complete">https://ad.auditude.com/adserver/e? 
                       type=AD_PROGRESS&a=334690&a1=105&ref=urn:asset:334690:105& 
                       unit=percent&progress=100& 
                       uid=hm7f2YHSQxiOqp1dNVqevw&u=cecebae72a919de350b9ac52602623f3& 
                       t=1476120645&s=d4b8307&z=266647&cid=1270337971&br=1& 
                       pod=id:1,ctype:l,ptype:p,dur:150,lot:5,cpos:1&sq=1&ax=0,0,0,0 
      </Tracking> 
    </TrackingEvents> 
    <MediaFiles> 
      <MediaFile id="Auditude" delivery="streaming" type="application/x-mpegURL"  
                 width="0" height="0"> 
                 https://olyhdliveextra-vh.akamaihd.net/. . ..mp4.csmil/master.m3u8 
      </MediaFile> 
    </MediaFiles> 
  </Linear></Creative> 
</Creatives> 
</InLine></Ad></VAST></vmap:VASTAdData></vmap:AdSource> 
<vmap:TrackingEvents> 
  <vmap:Tracking event="breakStart">https://ad.auditude.com/adserver/e? 
                        type=podprogress&event=start&uid=hm7f2YHSQxiOqp1dNVqevw& 
                        u=cecebae72a919de350b9ac52602623f3&t=1476120645& 
                        s=d4b8307&z=266647&cid=1270337971&br=1& 
                        pod=id:1,ctype:l,ptype:p,dur:150,lot:5,cpos:1 
  </vmap:Tracking> 
  <vmap:Tracking event="breakEnd">https://ad.auditude.com/adserver/e? 
                        type=podprogress&event=complete&uid=hm7f2YHSQxiOqp1dNVqevw& 
                        u=cecebae72a919de350b9ac52602623f3&t=1476120645& 
                        s=d4b8307&z=266647&cid=1270337971&br=1& 
                        pod=id:1,ctype:l,ptype:p,dur:150,lot:5,cpos:1 
  </vmap:Tracking> 
</vmap:TrackingEvents<vmap:Extensions/></vmap:AdBreak> 
<vmap:AdBreak timeOffset="00:06:15.139" breakType="linear" breakId="2"> 
<vmap:AdSource><vmap:VASTAdData><VAST version="3.0"><Ad id="334759" sequence="1"> 
<InLine><AdSystem>Auditude</AdSystem><AdTitle>lee_mid2_266652</AdTitle> 
<Impression>https://ad.auditude.com/adserver/e?type=adimp&a=334759&w=200& 
    uid=hm7f2YHSQxiOqp1dNVqevw&u=cecebae72a919de350b9ac52602623f3&t=1476120645& 
    s=d4b8307&z=266647&cid=1270337971&br=3& 
    pod=id:3,ctype:l,ptype:m,dur:150,lot:5,cpos:2&sq=1&ax=0,0,0,0 
</Impression> 
<Creatives> 
  <Creative AdID="334759"><Linear><Duration>00:00:15.000</Duration> 
    <TrackingEvents> 
      <Tracking event="creativeView">https://ad.auditude.com/adserver/i/; 
                       uid=hm7f2YHSQxiOqp1dNVqevw;u=cecebae72a919de350b9ac52602623f3; 
                       t=1476120645;s=d4b8307;z=266647;cid=1270337971;br=3; 
                       pod=id:3,ctype:l,ptype:m,dur:150,lot:5,cpos:2; 
                       sq=1;ax=0,0,0,0;a1=105; 
                       a=334759;w=200/c320x240.m3u8 
      </Tracking> 
      <Tracking event="start">https://ad.auditude.com/adserver/e? 
                       type=AD_PROGRESS&a=334759&a1=105&ref=urn:asset:334759:105& 
                       unit=percent&progress=0&uid=hm7f2YHSQxiOqp1dNVqevw& 
                       u=cecebae72a919de350b9ac52602623f3& 
                       t=1476120645&s=d4b8307&z=266647&cid=1270337971&br=3& 
                       pod=id:3,ctype:l,ptype:m,dur:150,lot:5,cpos:2&sq=1&ax=0,0,0,0 
      </Tracking> 
      <Tracking event="start">https://dpm.demdex.net/ibs:dpid=22619& 
                       dpuuid=hm7f2YHSQxiOqp1dNVqevw 
      </Tracking> 
      <Tracking event="firstQuartile">https://ad.auditude.com/adserver/e? 
                       type=AD_PROGRESS&a=334759&a1=105&ref=urn:asset:334759:105& 
                       unit=percent&progress=25&uid=hm7f2YHSQxiOqp1dNVqevw& 
                       u=cecebae72a919de350b9ac52602623f3&t=1476120645&s=d4b8307& 
                       z=266647&cid=1270337971&br=3& 
                       pod=id:3,ctype:l,ptype:m,dur:150,lot:5,cpos:2&sq=1&ax=0,0,0,0 
      </Tracking> 
      <Tracking event="midpoint">https://ad.auditude.com/adserver/e? 
                       type=AD_PROGRESS&a=334759&a1=105&ref=urn:asset:334759:105& 
                       unit=percent&progress=50& 
                       uid=hm7f2YHSQxiOqp1dNVqevw&u=cecebae72a919de350b9ac52602623f3& 
                       t=1476120645&s=d4b8307&z=266647&cid=1270337971&br=3& 
                       pod=id:3,ctype:l,ptype:m,dur:150,lot:5,cpos:2&sq=1&ax=0,0,0,0 
      </Tracking> 
      <Tracking event="thirdQuartile">https://ad.auditude.com/adserver/e? 
                       type=AD_PROGRESS&a=334759&a1=105&ref=urn:asset:334759:105& 
                       unit=percent&progress=75& 
                       uid=hm7f2YHSQxiOqp1dNVqevw&u=cecebae72a919de350b9ac52602623f3& 
                       t=1476120645&s=d4b8307&z=266647&cid=1270337971&br=3& 
                       pod=id:3,ctype:l,ptype:m,dur:150,lot:5,cpos:2&sq=1&ax=0,0,0,0 
      </Tracking> 
      <Tracking event="complete">https://ad.auditude.com/adserver/e? 
                       type=AD_PROGRESS&a=334759&a1=105&ref=urn:asset:334759:105& 
                       unit=percent&progress=100& 
                       uid=hm7f2YHSQxiOqp1dNVqevw&u=cecebae72a919de350b9ac52602623f3& 
                       t=1476120645&s=d4b8307&z=266647&cid=1270337971&br=3& 
                       pod=id:3,ctype:l,ptype:m,dur:150,lot:5,cpos:2&sq=1&ax=0,0,0,0 
      </Tracking> 
    </TrackingEvents> 
    <MediaFiles> 
      <MediaFile id="Auditude" delivery="streaming" type="application/x-mpegURL"  
                 width="0" height="0"> 
                 https://cdn2.auditude.com/assets/. . ..m3u8 
      </MediaFile> 
    </MediaFiles> 
  </Linear></Creative> 
</Creatives> 
</InLine></Ad> 
<Ad id="334691" sequence="2"><InLine> 
<AdSystem>Auditude</AdSystem><AdTitle>lee_mid1_266647</AdTitle> 
<Impression>https://ad.auditude.com/adserver/e?type=adimp&a=334691&w=200& 
    uid=hm7f2YHSQxiOqp1dNVqevw&u=cecebae72a919de350b9ac52602623f3&t=1476120645& 
    s=d4b8307&z=266647&cid=1270337971&br=3& 
    pod=id:3,ctype:l,ptype:m,dur:150,lot:5,cpos:2&sq=2&ax=0,0,0,0 
</Impression> 
<Creatives> 
  <Creative AdID="334691"><Linear><Duration>00:00:15.023</Duration> 
    <TrackingEvents> 
      <Tracking event="creativeView">https://ad.auditude.com/adserver/i/; 
                       uid=hm7f2YHSQxiOqp1dNVqevw;u=cecebae72a919de350b9ac52602623f3; 
                       t=1476120645;s=d4b8307;z=266647;cid=1270337971;br=3; 
                       pod=id:3,ctype:l,ptype:m,dur:150,lot:5,cpos:2;sq=2;ax=0,0,0,0; 
                       a1=105;a=334691;w=200/c384x216.m3u8 
      </Tracking> 
      <Tracking event="start">https://ad.auditude.com/adserver/e? 
                       type=AD_PROGRESS&a=334691&a1=105&ref=urn:asset:334691:105& 
                       unit=percent&progress=0& 
                       uid=hm7f2YHSQxiOqp1dNVqevw&u=cecebae72a919de350b9ac52602623f3& 
                       t=1476120645&s=d4b8307&z=266647&cid=1270337971&br=3& 
                       pod=id:3,ctype:l,ptype:m,dur:150,lot:5,cpos:2&sq=2&ax=0,0,0,0 
      </Tracking> 
      <Tracking event="start">https://dpm.demdex.net/ibs:dpid=22619& 
                       dpuuid=hm7f2YHSQxiOqp1dNVqevw 
      </Tracking> 
      <Tracking event="firstQuartile">https://ad.auditude.com/adserver/e? 
                       type=AD_PROGRESS&a=334691&a1=105&ref=urn:asset:334691:105& 
                       unit=percent&progress=25& 
                       uid=hm7f2YHSQxiOqp1dNVqevw&u=cecebae72a919de350b9ac52602623f3& 
                       t=1476120645&s=d4b8307&z=266647&cid=1270337971&br=3& 
                       pod=id:3,ctype:l,ptype:m,dur:150,lot:5,cpos:2&sq=2&ax=0,0,0,0 
      </Tracking> 
      <Tracking event="midpoint">https://ad.auditude.com/adserver/e? 
                       type=AD_PROGRESS&a=334691&a1=105&ref=urn:asset:334691:105& 
                       unit=percent&progress=50& 
                       uid=hm7f2YHSQxiOqp1dNVqevw&u=cecebae72a919de350b9ac52602623f3& 
                       t=1476120645&s=d4b8307&z=266647&cid=1270337971&br=3& 
                       pod=id:3,ctype:l,ptype:m,dur:150,lot:5,cpos:2&sq=2&ax=0,0,0,0 
      </Tracking> 
      <Tracking event="thirdQuartile">https://ad.auditude.com/adserver/e? 
                       type=AD_PROGRESS&a=334691&a1=105&ref=urn:asset:334691:105& 
                       unit=percent&progress=75& 
                       uid=hm7f2YHSQxiOqp1dNVqevw&u=cecebae72a919de350b9ac52602623f3& 
                       t=1476120645&s=d4b8307&z=266647&cid=1270337971&br=3& 
                       pod=id:3,ctype:l,ptype:m,dur:150,lot:5,cpos:2&sq=2&ax=0,0,0,0 
      </Tracking> 
      <Tracking event="complete">https://ad.auditude.com/adserver/e? 
                       type=AD_PROGRESS&a=334691&a1=105&ref=urn:asset:334691:105& 
                       unit=percent&progress=100& 
                       uid=hm7f2YHSQxiOqp1dNVqevw&u=cecebae72a919de350b9ac52602623f3& 
                       t=1476120645&s=d4b8307&z=266647&cid=1270337971&br=3& 
                       pod=id:3,ctype:l,ptype:m,dur:150,lot:5,cpos:2&sq=2&ax=0,0,0,0 
      </Tracking> 
    </TrackingEvents> 
    <MediaFiles> 
      <MediaFile id="Auditude" delivery="streaming" type="application/x-mpegURL"  
                 width="0" height="0"> 
                 https://olyhdliveextra-vh.akamaihd.net/. . ..mp4.csmil/master.m3u8 
      </MediaFile> 
    </MediaFiles> 
  </Linear></Creative> 
</Creatives> 
</InLine></Ad> 
<Ad id="334693" sequence="3"><InLine> 
<AdSystem>Auditude</AdSystem><AdTitle>lee_mid3_266647</AdTitle> 
<Impression>https://ad.auditude.com/adserver/e?type=adimp&a=334693&w=200& 
    uid=hm7f2YHSQxiOqp1dNVqevw&u=cecebae72a919de350b9ac52602623f3&t=1476120645& 
    s=d4b8307&z=266647&cid=1270337971&br=3& 
    pod=id:3,ctype:l,ptype:m,dur:150,lot:5,cpos:2&sq=3&ax=0,0,0,0 
</Impression> 
<Creatives> 
  <Creative AdID="334693"><Linear><Duration>00:00:30.000</Duration> 
    <TrackingEvents> 
      <Tracking event="creativeView">https://ad.auditude.com/adserver/i/; 
                       uid=hm7f2YHSQxiOqp1dNVqevw;u=cecebae72a919de350b9ac52602623f3; 
                       t=1476120645;s=d4b8307;z=266647;cid=1270337971;br=3; 
                       pod=id:3,ctype:l,ptype:m,dur:150,lot:5,cpos:2;sq=3; 
                       ax=0,0,0,0;a1=105;a=334693;w=200/c384x216.m3u8 
      </Tracking> 
      <Tracking event="start">https://ad.auditude.com/adserver/e? 
                       type=AD_PROGRESS&a=334693&a1=105&ref=urn:asset:334693:105& 
                       unit=percent&progress=0& 
                       uid=hm7f2YHSQxiOqp1dNVqevw&u=cecebae72a919de350b9ac52602623f3& 
                       t=1476120645&s=d4b8307&z=266647&cid=1270337971&br=3& 
                       pod=id:3,ctype:l,ptype:m,dur:150,lot:5,cpos:2&sq=3&ax=0,0,0,0 
      </Tracking> 
      <Tracking event="start">https://dpm.demdex.net/ibs:dpid=22619& 
                       dpuuid=hm7f2YHSQxiOqp1dNVqevw 
      </Tracking> 
      <Tracking event="firstQuartile">https://ad.auditude.com/adserver/e? 
                       type=AD_PROGRESS&a=334693&a1=105&ref=urn:asset:334693:105& 
                       unit=percent&progress=25& 
                       uid=hm7f2YHSQxiOqp1dNVqevw&u=cecebae72a919de350b9ac52602623f3& 
                       t=1476120645&s=d4b8307&z=266647&cid=1270337971&br=3& 
                       pod=id:3,ctype:l,ptype:m,dur:150,lot:5,cpos:2&sq=3&ax=0,0,0,0 
      </Tracking> 
      <Tracking event="midpoint">https://ad.auditude.com/adserver/e? 
                       type=AD_PROGRESS&a=334693&a1=105&ref=urn:asset:334693:105& 
                       unit=percent&progress=50& 
                       uid=hm7f2YHSQxiOqp1dNVqevw&u=cecebae72a919de350b9ac52602623f3& 
                       t=1476120645&s=d4b8307&z=266647&cid=1270337971&br=3& 
                       pod=id:3,ctype:l,ptype:m,dur:150,lot:5,cpos:2&sq=3&ax=0,0,0,0 
      </Tracking> 
      <Tracking event="thirdQuartile">https://ad.auditude.com/adserver/e? 
                       type=AD_PROGRESS&a=334693&a1=105&ref=urn:asset:334693:105& 
                       unit=percent&progress=75& 
                       uid=hm7f2YHSQxiOqp1dNVqevw&u=cecebae72a919de350b9ac52602623f3& 
                       t=1476120645&s=d4b8307&z=266647&cid=1270337971&br=3& 
                       pod=id:3,ctype:l,ptype:m,dur:150,lot:5,cpos:2&sq=3&ax=0,0,0,0 
      </Tracking> 
      <Tracking event="complete">https://ad.auditude.com/adserver/e? 
                       type=AD_PROGRESS&a=334693&a1=105&ref=urn:asset:334693:105& 
                       unit=percent&progress=100& 
                       uid=hm7f2YHSQxiOqp1dNVqevw&u=cecebae72a919de350b9ac52602623f3& 
                       t=1476120645&s=d4b8307&z=266647&cid=1270337971&br=3& 
                       pod=id:3,ctype:l,ptype:m,dur:150,lot:5,cpos:2&sq=3&ax=0,0,0,0 
      </Tracking> 
    </TrackingEvents> 
    <MediaFiles> 
      <MediaFile id="Auditude" delivery="streaming" type="application/x-mpegURL"  
                 width="0" height="0"> 
                 https://olyhdliveextra-vh.akamaihd.net/. . ..mp4.csmil/master.m3u8 
      </MediaFile> 
    </MediaFiles> 
  </Linear></Creative> 
</Creatives> 
</InLine></Ad> 
<Ad id="334705" sequence="4"> 
<InLine> 
<AdSystem>Auditude</AdSystem> 
<AdTitle>lee_mid1_266652</AdTitle> 
<Impression>https://ad.auditude.com/adserver/e?type=adimp&a=334705&w=200& 
    uid=hm7f2YHSQxiOqp1dNVqevw&u=cecebae72a919de350b9ac52602623f3&t=1476120645& 
    s=d4b8307&z=266647&cid=1270337971&br=3& 
    pod=id:3,ctype:l,ptype:m,dur:150,lot:5,cpos:2&sq=4&ax=0,0,0,0 
</Impression> 
<Creatives> 
  <Creative AdID="334705"><Linear><Duration>00:00:30.069</Duration> 
    <TrackingEvents> 
      <Tracking event="creativeView">https://ad.auditude.com/adserver/i/; 
                       uid=hm7f2YHSQxiOqp1dNVqevw;u=cecebae72a919de350b9ac52602623f3; 
                       t=1476120645;s=d4b8307;z=266647;cid=1270337971;br=3; 
                       pod=id:3,ctype:l,ptype:m,dur:150,lot:5,cpos:2;sq=4; 
                       ax=0,0,0,0;a1=105;a=334705;w=200/c340x192.m3u8 
      </Tracking> 
      <Tracking event="start">https://ad.auditude.com/adserver/e? 
                       type=AD_PROGRESS&a=334705&a1=105&ref=urn:asset:334705:105& 
                       unit=percent&progress=0& 
                       uid=hm7f2YHSQxiOqp1dNVqevw&u=cecebae72a919de350b9ac52602623f3& 
                       t=1476120645&s=d4b8307&z=266647&cid=1270337971&br=3& 
                       pod=id:3,ctype:l,ptype:m,dur:150,lot:5,cpos:2&sq=4&ax=0,0,0,0 
      </Tracking> 
      <Tracking event="start">https://dpm.demdex.net/ibs:dpid=22619& 
                       dpuuid=hm7f2YHSQxiOqp1dNVqevw 
      </Tracking> 
      <Tracking event="firstQuartile">https://ad.auditude.com/adserver/e? 
                       type=AD_PROGRESS&a=334705&a1=105&ref=urn:asset:334705:105& 
                       unit=percent&progress=25& 
                       uid=hm7f2YHSQxiOqp1dNVqevw&u=cecebae72a919de350b9ac52602623f3& 
                       t=1476120645&s=d4b8307&z=266647&cid=1270337971&br=3& 
                       pod=id:3,ctype:l,ptype:m,dur:150,lot:5,cpos:2&sq=4&ax=0,0,0,0 
      </Tracking> 
      <Tracking event="midpoint">https://ad.auditude.com/adserver/e? 
                       type=AD_PROGRESS&a=334705&a1=105&ref=urn:asset:334705:105& 
                       unit=percent&progress=50& 
                       uid=hm7f2YHSQxiOqp1dNVqevw&u=cecebae72a919de350b9ac52602623f3& 
                       t=1476120645&s=d4b8307&z=266647&cid=1270337971&br=3& 
                       pod=id:3,ctype:l,ptype:m,dur:150,lot:5,cpos:2&sq=4&ax=0,0,0,0 
      </Tracking> 
      <Tracking event="thirdQuartile">https://ad.auditude.com/adserver/e? 
                       type=AD_PROGRESS&a=334705&a1=105&ref=urn:asset:334705:105& 
                       unit=percent&progress=75& 
                       uid=hm7f2YHSQxiOqp1dNVqevw&u=cecebae72a919de350b9ac52602623f3& 
                       t=1476120645&s=d4b8307&z=266647&cid=1270337971&br=3& 
                       pod=id:3,ctype:l,ptype:m,dur:150,lot:5,cpos:2&sq=4&ax=0,0,0,0 
      </Tracking> 
      <Tracking event="complete">https://ad.auditude.com/adserver/e? 
                       type=AD_PROGRESS&a=334705&a1=105&ref=urn:asset:334705:105& 
                       unit=percent&progress=100& 
                       uid=hm7f2YHSQxiOqp1dNVqevw&u=cecebae72a919de350b9ac52602623f3& 
                       t=1476120645&s=d4b8307&z=266647&cid=1270337971&br=3& 
                       pod=id:3,ctype:l,ptype:m,dur:150,lot:5,cpos:2&sq=4&ax=0,0,0,0 
      </Tracking> 
    </TrackingEvents> 
    <MediaFiles> 
      <MediaFile id="Auditude" delivery="streaming" type="application/x-mpegURL"  
                 width="0" height="0"> 
                 https://olyhdliveextra-vh.akamaihd.net/. . ..mp4.csmil/master.m3u8 
      </MediaFile> 
    </MediaFiles> 
  </Linear></Creative> 
</Creatives> 
</InLine> 
</Ad> 
</VAST></vmap:VASTAdData></vmap:AdSource> 
<vmap:TrackingEvents> 
  <vmap:Tracking event="breakStart">https://ad.auditude.com/adserver/e? 
                        type=podprogress&event=start&uid=hm7f2YHSQxiOqp1dNVqevw& 
                        u=cecebae72a919de350b9ac52602623f3&t=1476120645&s=d4b8307& 
                        z=266647&cid=1270337971&br=3& 
                        pod=id:3,ctype:l,ptype:m,dur:150,lot:5,cpos:2 
  </vmap:Tracking> 
  <vmap:Tracking event="breakEnd">https://ad.auditude.com/adserver/e? 
                        type=podprogress&event=complete&uid=hm7f2YHSQxiOqp1dNVqevw& 
                        u=cecebae72a919de350b9ac52602623f3&t=1476120645&s=d4b8307& 
                        z=266647&cid=1270337971&br=3& 
                        pod=id:3,ctype:l,ptype:m,dur:150,lot:5,cpos:2 
  </vmap:Tracking> 
</vmap:TrackingEvents> 
<vmap:Extensions/> 
</vmap:AdBreak></vmap:VMAP>
```