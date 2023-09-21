---
description: Le serveur de manifeste renvoie les listes de lecture principales au format M3U8, conforme à la norme HTTP Live Streaming proposée. Il se compose d’un ensemble de variantes de flux de transport (TS), chacune contenant des rendus du même contenu pour différents formats et débits en bits. L’insertion de publicités Adobe Primetime ajoute la balise de directive EXT-X-MARKER, à interpréter par les lecteurs vidéo clients.
title: Directive EXT-X-MARKER
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '748'
ht-degree: 0%

---


# Directive EXT-X-MARKER {#ext-x-marker-directive}

Le serveur de manifeste renvoie les listes de lecture principales au format M3U8, conforme à la norme HTTP Live Streaming proposée. Il se compose d’un ensemble de variantes de flux de transport (TS), chacune contenant des rendus du même contenu pour différents formats et débits en bits. L’insertion de publicités Adobe Primetime ajoute la balise de directive EXT-X-MARKER, à interpréter par les lecteurs vidéo clients.

Pour plus d’informations sur la balise EXT-X-MARKER, voir [Profil de diffusion en continu HTTP Adobe Primetime](https://wwwimages2.adobe.com/content/dam/acom/en/devnet/primetime/PrimetimeHLS_April2014.pdf).

>[!NOTE]
>
>Cette fonctionnalité n’est disponible que si l’URL du serveur de manifeste de bootstrap ne contient pas le paramètre `pttrackingmode` .

>[!NOTE]
>
>La balise EXT-X-MARKER est ajoutée aux segments de publicité et non aux segments de contenu.

Le projet de norme à [HTTP Live Streaming](https://tools.ietf.org/html/draft-pantos-http-live-streaming-23) décrit le contenu et le format des listes de lecture des variantes. La balise EXT-X-MARKER demande au client d’appeler un rappel. Il contient les composants suivants :

* **ID** Identifiant unique (chaîne) pour cet événement de rappel dans le contexte du flux de programme.

* **TYPE** Type (chaîne) de l’événement de rappel : PodBegin, PodEnd, PrerollPodBegin, PrerollPodEnd ou AdBegin

* **DURÉE** Durée (en secondes) à partir du début du segment contenant la balise pour laquelle la directive reste valide.

* **OFFSET** Facultatif. Décalage (en secondes) relatif au début de la lecture du segment, lorsque le rappel doit être appelé.

   * `PodBegin` et `PrerollPodBegin` contiennent des informations de balise dans l’attribut DATA et sont déclenchées au début du segment. Ainsi, la variable `OFFSET` n’est pas disponible ici.

   * `AdBegin` contient des informations de balise dans l’attribut DATA et les balises d’impression sont déclenchées au début de ce segment. Ainsi, la variable `OFFSET` n’est pas disponible ici non plus.

   * `PodEnd` et `PrerollPodEnd` contiennent des informations de balise dans l’attribut DATA , mais sont déclenchées à la fin du segment actuel, car ces balises doivent être déclenchées à la fin du dernier segment de la dernière publicité dans la capsule. Dans ce cas, `OFFSET` est défini sur `<duration of segment>` pour indiquer que la balise doit être déclenchée à la fin du segment actuel.

* **DONNÉES** Chaîne codée en Base64 entre guillemets doubles contenant les données à transmettre à l’application lors de l’appel du rappel. Elle contient des informations de suivi des publicités conformes aux spécifications VMAP1.0 et VAST3.0.

* **COUNT** Nombre de publicités qui seront regroupées dans la coupure publicitaire.

  Applicable uniquement si le composant TYPE est défini sur PodBegin ou PrerollPodBegin.

* **VENTILATION** Durée totale (en secondes) de la coupure publicitaire remplie.

  Applicable uniquement si le composant TYPE est défini sur PodBegin ou PrerollPodBegin.

Lors de la création du rappel, interprétez les composants EXT-X-MARKER comme suit :

* Lorsque la balise contient `OFFSET`, déclenche le rappel au décalage spécifié par rapport au début de la lecture du contenu dans ce segment. Sinon, déclenchez le rappel dès que la lecture du contenu de ce segment commence.
* Utilisation `DURATION` pour suivre la progression du contenu de la publicité et demander des URL pour le suivi des événements.
* Pass `ID`, `TYPE`, et `DATA` au rappel.

Utilisez la variable `PrerollPodBegin`, et `PrerollPodEnd` valeurs pour `TYPE` pour décider quel segment TS lire en premier dans les flux linéaire/en direct.

>[!NOTE]
>
>La variable `PrerollPodBegin`, et `PrerollPodEnd` ne sont disponibles que lorsqu’une publicité preroll est insérée dans un flux en direct.

Le serveur de manifeste comprend des balises EXT-X-MARKER dans les segments suivants :

* Premier segment de la coupure publicitaire, pour effectuer le suivi du début d’une capsule publicitaire.
* Premier segment de la publicité, pour effectuer le suivi du début/fin/progression d’une publicité individuelle dans une capsule.
* Dernier segment de la coupure publicitaire pour effectuer le suivi de la fin d’une capsule publicitaire.

Le serveur de manifeste envoie une `VMAP1.0-conformant` Document XML pour suivre le début et la fin de chaque coupure publicitaire. Il s’agit d’une version filtrée de la réponse VMAP1.0 réelle renvoyée par le serveur de publicités, et qui contient principalement les événements de suivi, comme illustré ici :

```xml
<?xml version="1.0"?> 
<AdTrackingFragments> 
<AdTrackingFragment> 
<vmap:VMAP xmlns:vmap="https://www.iab.net/vmap-1.0" version="1.0"> 
    <vmap:AdBreak breakType="linear" breakId="mypre" timeOffset="start"> 
        <vmap:TrackingEvents> 
            <vmap:Tracking event="breakStart"> 
                https://MyServer.com/breakstart.gif 
            </vmap:Tracking> 
            <vmap:Tracking event="breakEnd"> 
                https://MyServer.com/breakend.gif 
            </vmap:Tracking> 
            <vmap:Tracking event="error"> 
                https://MyServer.com/error.gif 
            </vmap:Tracking> 
        </vmap:TrackingEvents> 
    </vmap:AdBreak> 
</vmap:VMAP> 
</AdTrackingFragment> 
</AdTrackingFragments>
```

Pour chaque publicité créative que le serveur de manifeste insère dans le contenu du programme, il envoie un document XML conforme à VAST3.0 pour effectuer le suivi de cette publicité. Chaque document XML contient une `<InLine>` élément décrivant la publicité linéaire insérée, ou un élément `<Wrapper>` dans le cas des publicités wrapper (c’est-à-dire des publicités liées ou redirigées), ainsi que toute publicité compagnon et extension associée. Si la réponse VAST contient un attribut de séquence, par exemple lorsque la publicité fait partie d’une capsule publicitaire, le document inclut cet attribut. Voici un exemple de document XML conforme à VAST3.0 pour le suivi d’une publicité individuelle :

```xml
<?xml version="1.0"?> 
<AdTrackingFragments> 
<AdTrackingFragment> 
<VAST xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"  
      version="3.0"  
      xsi:noNamespaceSchemaLocation="https://service.videoplaza.com/schema/iab/vast-3.0.xsd"> 
<Ad id="903395"> 
    <InLine> 
      <AdSystem version="1.0">Auditude</AdSystem> 
      <AdTitle/> 
      <Error>https://ad.qa.auditude.com/adserver/?ErrAd1=[ERRORCODE]</Error> 
      <Impression id="urn:aeid:903395">https://ad.qa.auditude.com/adserver/e?type=adimp&amp; 
                 cid=127860991&amp; 
                 z=50183&amp; 
                 a=903395&amp; 
                 s=ef8c51dc&amp; 
                 t=1355309735&amp; 
                 w=100000&amp; 
                 uid=_CxLm0b1SeKD8KXco__5TQ&amp; 
                 l=1355280906&amp; 
                 u=956c3cd141086a1da44dcae8ea4ed14a&amp; 
                 br=1&amp; 
                 sq=1&amp; 
                 pod=id:1,ctype:l,ptype:p,dur:400,lot:8,cpos:1,edur:400,elot:8&amp; 
                 ax=0,0,1720,0/?ContentPosition=[CONTENTPLAYHEAD] 
                               ?Cashcash=[CACHEBUSTING] 
                               ?Asset=[ASSETURI] 
      </Impression> 
      <Creatives> 
        <Creative> 
          <Linear> 
            <Duration>00:00:15</Duration> 
            <TrackingEvents> 
              ... 
              <Tracking event="firstQuartile"> 
                https://ad.qa.auditude.com/adserver/e?type=AD_PROGRESS&amp; 
                  a=903395&amp; 
                  a1=105&amp; 
                  ref=urn:asset:903395:105&amp; 
                  unit=percent&amp; 
                  progress=25&amp; 
                  cid=127860991&amp; 
                  z=50183&amp; 
                  a=903395&amp; 
                  s=ef8c51dc&amp; 
                  t=1355309735&amp; 
                  w=100000&amp; 
                  uid=_CxLm0b1SeKD8KXco__5TQ&amp; 
                  l=1355280906&amp; 
                  u=956c3cd141086a1da44dcae8ea4ed14a&amp; 
                  br=1&amp; 
                  sq=1&amp; 
                  pod=id:1,ctype:l,ptype:p,dur:400,lot:8,cpos:1,edur:400,elot:8&amp; 
                  ax=0,0,1720,0/?ContentPosition=[CONTENTPLAYHEAD] 
                                ?Cashcash=[CACHEBUSTING] 
                                ?Asset=[ASSETURI] 
              </Tracking>                
              <Tracking event="midpoint"> 
                https://ad.qa.auditude.com/adserver/e?type=AD_PROGRESS&amp; 
                  a=903395&amp; 
                  a1=105&amp; 
                  ref=urn:asset:903395:105&amp; 
                  unit=percent&amp; 
                  progress=50&amp; 
                  cid=127860991&amp; 
                  z=50183&amp; 
                  a=903395&amp; 
                  s=ef8c51dc&amp; 
                  t=1355309735&amp; 
                  w=100000&amp; 
                  uid=_CxLm0b1SeKD8KXco__5TQ&amp; 
                  l=1355280906&amp; 
                  u=956c3cd141086a1da44dcae8ea4ed14a&amp; 
                  br=1&amp; 
                  sq=1&amp; 
                  pod=id:1,ctype:l,ptype:p,dur:400,lot:8,cpos:1,edur:400,elot:8&amp; 
                  ax=0,0,1720,0/?ContentPosition=[CONTENTPLAYHEAD] 
                                ?Cashcash=[CACHEBUSTING] 
                                ?Asset=[ASSETURI] 
              </Tracking> 
              <Tracking event="firstQuartile"> 
                https://www.Tweeeen.com/?ContentPosition=[CONTENTPLAYHEAD] 
                                       ?Cashcash=[CACHEBUSTING] 
                                       ?Asset=[ASSETURI] 
              </Tracking> 
              <Tracking event="midpoint"> 
                https://www.Fiftyyyy.com/?ContentPosition=[CONTENTPLAYHEAD] 
                                        ?Cashcash=[CACHEBUSTING] 
                                        ?Asset=[ASSETURI] 
              </Tracking> 
              ... 
            </TrackingEvents> 
            <VideoClicks> 
              <ClickTracking> 
                https://www.MP4-Vid-ClickTrack.com/?ContentPosition=[CONTENTPLAYHEAD] 
                                                  ?Cashcash=[CACHEBUSTING] 
                                                  ?Asset=[ASSETURI] 
              </ClickTracking> 
              <ClickThrough> 
                https://www.cnn.com/?ContentPosition=[CONTENTPLAYHEAD] 
                                   ?Cashcash=[CACHEBUSTING] 
                                   ?Asset=[ASSETURI] 
              </ClickThrough> 
              ... 
            </VideoClicks> 
            <AdParameters>campaign_id=7012</AdParameters> 
            <MediaFiles> 
              ...            
            </MediaFiles> 
          </Linear> 
        </Creative> 
        <Creative> 
          <CompanionAds> 
            <Companion id="103" width="300" height="250"> 
              <StaticResource creativeType="image/jpeg"> 
                https://ad.qa.auditude.com/adserver/c/z=50183; 
                  l=1355280906; 
                  u=956c3cd141086a1da44dcae8ea4ed14a; 
                  uid=_CxLm0b1SeKD8KXco__5TQ; 
                  cid=127860991; 
                  s=ef8c51dc; 
                  t=1355309735; 
                  br=1; 
                  sq=1; 
                  pod=id%3a1%2cctype%3al%2cptype%3ap%2cdur 
                    %3a400%2clot%3a8%2ccpos%3a1%2cedur%3a400%2celot%3a8; 
                  ax=0%2c0%2c1720%2c0; 
                  w=100000; 
                  a=903395; 
                  a1=103/c300x250.jpeg 
              </StaticResource> 
              <CompanionClickThrough> 
                https://ad.qa.auditude.com/adserver/l/a=903395%3Ba1=103 
                  %3Ba2=1%3Bz=50183%3Bl=1355280906%3Bu=956c3cd141086a1da44dcae8ea4ed14a 
                  %3Bcid=127860991%3Bs=ef8c51dc%3Buid=_CxLm0b1SeKD8KXco__5TQ 
                  %3Bt=1355309735%3Bbr=1%3Bsq=1%3Bpod=id%3a1%2cctype%3al%2cptype 
                  %3ap%2cdur%3a400%2clot%3a8%2ccpos%3a1%2cedur%3a400%2celot%3a8 
                  %3Bax=0%2c0%2c1720%2c0 
              </CompanionClickThrough> 
              <AdParameters>campaign_id=7012</AdParameters> 
            </Companion> 
          </CompanionAds> 
        </Creative> 
        ... 
      </Creatives> 
      <Extensions> 
        <Extension type="Behavior"> 
          ... 
        </Extension> 
      </Extensions> 
    </InLine> 
  </Ad> 
  </VAST> 
</AdTrackingFragment> 
</AdTrackingFragments> 
```
