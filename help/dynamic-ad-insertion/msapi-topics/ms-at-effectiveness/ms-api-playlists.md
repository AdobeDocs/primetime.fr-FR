---
description: Le serveur de manifeste renvoie des listes de lecture originales au format M3U8, conformément à la norme proposée pour la diffusion en flux continu en direct HTTP. Il se compose d’un ensemble de flux de transport (TS) de variantes, chacun contenant des rendus du même contenu pour des débits et des formats différents. L’insertion d’une publicité Adobe Primetime ajoute la balise de directive EXT-X-MARKER, à interpréter par les lecteurs vidéo clients.
seo-description: Le serveur de manifeste renvoie des listes de lecture originales au format M3U8, conformément à la norme proposée pour la diffusion en flux continu en direct HTTP. Il se compose d’un ensemble de flux de transport (TS) de variantes, chacun contenant des rendus du même contenu pour des débits et des formats différents. L’insertion d’une publicité Adobe Primetime ajoute la balise de directive EXT-X-MARKER, à interpréter par les lecteurs vidéo clients.
seo-title: Directive EXT-X-MARKER
title: Directive EXT-X-MARKER
uuid: e349bf89-b196-47b4-a362-9913fa28b2c6
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# Directive EXT-X-MARKER {#ext-x-marker-directive}

Le serveur de manifeste renvoie des listes de lecture originales au format M3U8, conformément à la norme proposée pour la diffusion en flux continu en direct HTTP. Il se compose d’un ensemble de flux de transport (TS) de variantes, chacun contenant des rendus du même contenu pour des débits et des formats différents. L’insertion d’une publicité Adobe Primetime ajoute la balise de directive EXT-X-MARKER, à interpréter par les lecteurs vidéo clients.

Pour plus d’informations sur la balise EXT-X-MARKER, reportez-vous à la Adobe Primetime HTTP Live Streaming [](https://wwwimages2.adobe.com/content/dam/acom/en/devnet/primetime/PrimetimeHLS_April2014.pdf).

>[!NOTE]
>
>Cette fonctionnalité n’est disponible que si l’URL du serveur de manifeste d’amorçage ne contient pas le `pttrackingmode` paramètre.

>[!NOTE]
>
>La balise EXT-X-MARKER est ajoutée aux segments d’annonce et non aux segments de contenu.

Le brouillon de la norme [HTTP Live Streaming](https://tools.ietf.org/html/draft-pantos-http-live-streaming-23) décrit le contenu et le format des listes de diffusion variantes. La balise EXT-X-MARKER indique au client d’appeler un rappel. Il contient les composants suivants :

* **Identifiant** Identifiant unique (chaîne) pour ce de rappel dans le contexte du flux de .

* **TYPE** Type (chaîne) du de rappel : PodBegin, PodEnd, PrerollPodBegin, PrerollPodEnd ou AdBegin

* **DURÉE** Durée (en secondes) à partir du du segment porteur de la balise pour laquelle la directive reste valide.

* **DÉCALAGE** Facultatif. Décalage (en secondes) relatif au début de la lecture du segment, lorsque le rappel doit être appelé.

   * `PodBegin` et `PrerollPodBegin` contiennent des informations de balise dans l’attribut DATA et sont déclenchées sur les  du segment. La `OFFSET` balise n&#39;est donc pas disponible ici.

   * `AdBegin` contient des informations sur les balises dans l’attribut DATA et les balises d’impression sont déclenchées sur les  de ce segment. La `OFFSET` balise n&#39;est donc pas disponible ici non plus.

   * `PodEnd` et `PrerollPodEnd` contiennent des informations de balise dans l’attribut DATA, mais sont déclenchées à la fin du segment actuel, car ces balises doivent être déclenchées à la fin du dernier segment de la dernière publicité dans la capsule. Dans ce cas, `OFFSET` est défini pour `<duration of segment>` spécifier que la balise doit être déclenchée à la fin du segment actuel.

* **Chaîne codée en base de données** 64, entourée de guillemets de contenant les données à transmettre à l’application lors de l’appel du rappel. Il contient des informations de suivi des publicités conformes aux spécifications VMAP1.0 et VAST3.0.

* **NOMBRE** de publicités qui seront assemblées au cours de la coupure publicitaire.

   Applicable uniquement si le composant TYPE est défini sur PodBegin ou PrerollPodBegin.

* **VENTILATION** Durée totale (en secondes) de la coupure publicitaire remplie.

   Applicable uniquement si le composant TYPE est défini sur PodBegin ou PrerollPodBegin.

Lors de la création du rappel, interprétez les composants EXT-X-MARKER comme suit :

* Lorsque la balise contient `OFFSET`, déclenchez le rappel au décalage spécifié par rapport au début de la lecture du contenu dans ce segment. Sinon, déclenchez le rappel dès que le contenu de ce segment  lu.
* Permet `DURATION` de suivre la progression du contenu de la publicité et de demander des URL pour effectuer le suivi des .
* Transmettez `ID`, `TYPE`et `DATA` au rappel.

Utilisez les valeurs `PrerollPodBegin`et `PrerollPodEnd` pour `TYPE` décider quel segment TS lire en premier dans les flux dynamiques/linéaires.

>[!NOTE]
>
>Les valeurs `PrerollPodBegin`et `PrerollPodEnd` ne sont disponibles que lorsqu’une publicité preroll est insérée dans un flux en direct.

Le serveur de manifeste inclut des balises EXT-X-MARKER dans les segments suivants :

* Premier segment de la coupure publicitaire, pour suivre le début d’une capsule publicitaire.
* Premier segment de la publicité, pour effectuer le suivi du /achèvement/progression d’une publicité individuelle dans une capsule publicitaire.
* Dernier segment de la coupure publicitaire, pour effectuer le suivi de la fin d’une capsule publicitaire.

Le serveur de manifeste envoie un `VMAP1.0-conformant` XML pour effectuer le suivi du et de la fin de chaque coupure publicitaire. Il s’agit d’une version filtrée de la réponse VMAP1.0 réelle renvoyée par le serveur d’annonces, et contient principalement le de suivi, comme indiqué ici :

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

Pour chaque élément créatif de publicité que le serveur de manifeste insère dans le contenu  du, il envoie un XML conforme à VAST3.0 pour effectuer le suivi de cette publicité. Chaque XML contient un `<InLine>` élément décrivant le créatif publicitaire linéaire inséré, ou un `<Wrapper>` élément dans le cas des publicités wrapper (c’est-à-dire des publicités liées ou redirigées), ainsi que les publicités et extensions connexes. Si la réponse VAST contient un attribut de séquence, par exemple lorsque la publicité fait partie d’une capsule publicitaire, le  inclut cet attribut. Vous trouverez ci-dessous un exemple de  XML conforme à la norme VAST3.0 pour le suivi d&#39;une publicité individuelle :

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
