---
title: Conversion TVSDK - 1.3 à 2.0 pour JavaScript
seo-title: Conversion TVSDK - 1.3 à 2.0 pour JavaScript
description: De nombreuses signatures de méthode et noms d’élément d’API ont changé pour la version 2.0. Consultez ces tableaux pour voir tous les détails de modification de l’API.
seo-description: De nombreuses signatures de méthode et noms d’élément d’API ont changé pour la version 2.0. Consultez ces tableaux pour voir tous les détails de modification de l’API.
uuid: d2d1742d-c90c-43f5-94fc-8c4a57cb8ed4
contentOwner: asgupta
products: SG_PRIMETIME
topic-tags: migration
discoiquuid: c732f54d-116c-43f3-bec4-5e71af208426
translation-type: tm+mt
source-git-commit: e644e8497e118e2d03e72bef727c4ce1455d68d6

---


# Conversion TVSDK - 1.3 à 2.0 pour JavaScript {#tvsdk-conversion-to-for-javascript}

De nombreuses signatures de méthode et noms d’élément d’API ont changé pour la version 2.0. Consultez ces tableaux pour voir tous les détails de modification de l’API.

## Mise en oeuvre des fonctions de rappel dans JavaScript {#implement-callback-functions-in-javascript}

Les commentaires dans la documentation de la méthode suggèrent la signature des rappels que vous devez implémenter.

Pour JavaScript, la syntaxe de l’API est basée sur l’ID Web. Pour une interface TVSDK, les noms de méthode sont appelés *methodName*(). Pour que les méthodes soient implémentées par votre application, un attribut de lecture/écriture appelé ** methodNameCallbackFunc est ajouté à l’interface et votre application doit le définir pour qu’il pointe vers une fonction qui implémente la méthode. Par exemple :

```shell
// An app implementable interface
interface ContentFactory
{
    /*
     * AdPolicySelector retrieveAdPolicySelector(MediaPlayerItem item);
     */
    attribute Object retrieveAdPolicySelectorCallbackFunc;
 
    /*
     * ContentResolverList retrieveResolvers(MediaPlayerItem item);
     */
    attribute Object retrieveResolversCallbackFunc;
 
    /*
     * OpportunityGeneratorList retrieveGenerators(MediaPlayerItem item);
     */
    attribute Object retrieveGeneratorsCallbackFunc;
};

// this is how to implement it
var factory = new AdobePSDK.ContentFactory();
factory.retrieveAdPolicySelectorCallbackFunc = function(item)
{
    // return your adPolicySelector according to the item
    return adPolicySelector;
}
 
mediaPlayerItemConfig = new AdobePSDK.MediaPlayerItemConfig ();
playerConfig.adFactory = factory;
// Use this config to load new MediaResource
```

## Modifications de l’élément API de flux de travaux publicitaires pour la version 2.0 {#advertising-workflow-api-element-changes-for}

Ces tableaux comparent les éléments de l’API de flux de travaux publicitaires pour le SDK JavaScript TVSDK entre les versions 1.3 et 2.0.

Tableaux dans cette rubrique :

* TimedMetadata
* AdSignalingMode
* AdvertisingMetadata
* CustomRangeMetadata
* ReplaceTimeRange
* Placement
* Opportunité
* Réservation
* Chronologie / ElémentCalendrier / MarqueurCalendrier
* AdBreak
* Ad / AdAsset / AdClick / AdList / AdAssetList / AdBannerAsset
* AdBreakTimelineItem / AdTimelineItem
* AdBreakPolicy / AdBreakWatchedPolicy / AdPolicyMode / AdPolicyInfo / AdPolicySelector
* TimelineOperation
* AdBreakPlacement
* ParamètresAuditude

### TimedMetadata {#timedmetadata}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p> <strong>TimedMetadata</strong>: interface TimedMetadata {<br /> const unsigned short METADATA_TYPE_TAG = 0 ; <br /> const unsigned short METADATA_TYPE_ID3 = 1 ; attribut <br /> readonly, type court non signé; attribut <br /> readonly long;<br /> readonly attribut DomString id;<br /> readonly, attribut nom DomString;<br /> readonly, attribut contenu DomString ; Métadonnées d’objet <br /> readonly d’attribut ;<br /> }; </p> </td> 
   <td><p>interface TimedMetadata {<br /> const unsigned short METADATA_TYPE_TAG = 0 ;<br /> const unsigned short METADATA_TYPE_ID3 = 1 ;<br /> readonly attribut unsigned short metadataType;<br /> readonly attribut long time;<br /> readonly attribut long id;<br /> readonly, attribut nom DomString;<br /> Métadonnées d’objet <br /> readonly d’attribut ;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>TimedMetadataList</strong>: (Pas de modification pour la version 2.0)</td> 
   <td><p>interface TimedMetadataList {<br /> readonly attribut de longue durée non signé;<br /> getter TimedMetadata(index long non signé);<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### AdSignalingMode {#adsignalingmode}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>Interface AdSignalingMode { <br /> const short non signé MODE_DEFAULT, <br /> const short non signé MODE_MANIFEST_CUES, <br /> const short non signé MODE_SERVER_MAP,const short non signé MODE_CUSTOM_RANGES <br /> <br /> };</p> </td> 
   <td>Ceci remplace la clé MetadataKeys::MANIFEST_CUES.</td> 
  </tr> 
 </tbody> 
</table>

### AdvertisingMetadata {#advertisingmetadata}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>Interface AdvertisingMetadata { <br /> attribut Mode AdSignalingMode; <br /> attribut AdBreakWatchedPolicy adBreakAsWatched; <br /> attribut booléen livePreroll; <br /> attribut booléen delayAdLoading ; <br /> };</p> </td> 
   <td>Cette fonctionnalité a été fournie par<p>MetadataKeys::ADVERTISING_METADATA</p> clé.</td> 
  </tr> 
 </tbody> 
</table>

### CustomRangeMetadata {#customrangemetadata}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>Interface CustomRangeMetadata { <br /> const short non signé TYPE_MARK_RANGE; const <br /> short non signé TYPE_DELETE_RANGE; const <br /> short non signé TYPE_REPLACE_RANGE; attribut <br /> type court non signé; <br /> attribut booléen modifySeekPosition; <br /> attribut TimeRangeList timeRangeList; <br /> };</p> </td> 
   <td>(Nouveauté de la version 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### ReplaceTimeRange {#replacetimerange}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>interface ReplaceTimeRange { <br /> attribut start long non signé; attribut <br /> readonly unsigned long end; <br /> attribut de durée longue non signée ; <br /> attribut unsigned long replaceDuration; <br /> };</p> </td> 
   <td>(Nouveauté de la version 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### Placement {#placement}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>Placement de l'interface { <br /> const short non signé TYPE_MID_ROLL; <br /> const short non signé TYPE_PRE_ROLL; const <br /> short non signé TYPE_POST_ROLL; const <br /> short non signé TYPE_SERVER_MAP; const <br /> short non signé TYPE_CUSTOM_RANGE;<br /> readonly attribut unsigned short type; attribut <br /> readonly long; attribut <br /> readonly longue durée; const short <br /> non signé MODE_DEFAULT; const short <br /> non signé MODE_INSERT; const short <br /> non signé MODE_REPLACE; const short <br /> non signé MODE_DELETE; <br /> const short MODE_MARK non signé; const short <br /> non signé MODE_FREE_REPLACE; attribut <br /> readonly non signé short mode; plage TimeRange de l'attribut <br /> readonly; <br /> };</p> </td> 
   <td>(Nouveauté de la version 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### Opportunité {#opportunity}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>interface Opportunity { <br /> attribut readonly DomString id; placement de l'attribut <br /> en lecture seule ; Paramètres d’objet <br /> readonly attribute ; attribut <br /> readonly Object customParameters; <br /> }; </p> </td> 
   <td>(Nouveauté de la version 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### Réservation {#reservation}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>interface Réservation { <br /> attribut readonly plage TimeRange; attribut <br /> readonly long hold; <br /> }; </p> </td> 
   <td> (Nouveauté de la version 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### Chronologie / ElémentCalendrier / MarqueurCalendrier {#timeline-timelineitem-timelinemarker}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p><strong>Chronologie</strong>: journal de l'interface <br /> { readonly attribut TimelineMarkerList timelineMarkers; attribut <br /> readonly TimelineItemList timelineItems;  de <br /> convertToLocalTime(  temps);  de <br /> convertToVirtualTime(  temps); <br /> };</p> </td> 
   <td><p>journal de l'interface {<br /> readonly attribut TimelineMarkerList timelineMarkers;<br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p> <strong>TimelineItem</strong>: interface TimelineItem :<br /> TimelineMarker {<br /> readonly attribut long id; attribut <br /> readonly TimeRange virtualRange; attribut <br /> readonly TimeRange localRange; attribut <br /> readonly boolean watched; attribut <br /> readonly boolean temporaire; <br /> }; </p> </td> 
   <td>(Nouveauté de la version 2.0)</td> 
  </tr> 
  <tr> 
   <td><strong>TimelineMarker</strong>: (Pas de modification pour la version 2.0)</td> 
   <td><p>interface TimelineMarker {<br /> readonly attribut temps de  de l'attribut ;<br /> readonly attribut  la durée du;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### AdBreak {#adbreak}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>interface AdBreak {<br /> <br /> <br /> readonly attribut durée de  de l'attribut <br /> readonly;<br /> readonly attribut ads AdList;<br /> <br /> <br /> readonly attribut AdInsertionType insertType;<br /> }; </p> </td> 
   <td><p>interface AdBreak {<br /> readonly attribut temps  temps de;<br /> readonly, attribut  replaceDuration;<br />  d'attribut <br /> en lecture seule de la durée la variable<br /> readonly attribut AdList adList;<br /> <br /> readonly attribut données DomString ;<br /> <br /> }; </p> </td> 
  </tr> 
 </tbody> 
</table>

### Ad / AdAsset / AdClick / AdList / AdAssetList / AdBannerAsset {#ad-adasset-adclick-adlist-adassetlist-adbannerasset}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p> <strong>Publicité</strong>: attribut d'annonce d'interface {<br /> readonly AdAsset PrimaryAsset;<br /> readonly attribut AdAssetList CompanionAssets;<br />  d'attribut <br /> en lecture seule de la durée la variable<br /> readonly attribut DomString id;<br /> const unsigned short ADTYPE_LINEAR = 0 ;<br /> const unsigned short ADTYPE_NONLINEAR = 1 ;<br /> attribut <br /> readonly unsigned short adType;<br /> readonly attribut AdInsertionType adInsertionType; attribut <br /> <br /> readonly booléen cliquable ; attribut <br /> readonly boolean isCustomAdMarker;<br /> }; </p> </td> 
   <td><p>attribut d'annonce d'interface {<br /> readonly AdAsset PrimaryAsset;<br /> readonly attribut AdAssetList CompanionAssets;<br />  d'attribut <br /> en lecture seule de la durée la variable<br /> readonly attribut DomString id;<br /> const unsigned short ADTYPE_LINEAR = 0 ;<br /> const unsigned short ADTYPE_NONLINEAR = 1 ;<br /> attribut <br /> readonly, type court non signé;<br /> readonly, attribut AdInsertionType insertType; attribut <br /> readonly Suivi d'objet ;<br /> <br /> } <br /> ; </p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdAsset</strong>: (Pas de modification pour la version 2.0)</td> 
   <td><p>interface AdAsset {<br /> readonly attribut DomString id;<br /> readonly attribut  la durée du;<br /> readonly attribut ressource MediaResource;<br /> readonly attribut AdClick adClick;<br /> readonly, attribut, métadonnées d’objet ;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdClick</strong>: (Pas de modification pour la version 2.0)</td> 
   <td><p>interface AdClick {<br /> readonly attribut DomString id;<br /> readonly, attribut Titre DomString;<br /> readonly, attribut URL DomString;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdList</strong>: (Pas de modification pour la version 2.0)</td> 
   <td><p>interface AdList {<br /> readonly attribut unsigned long length;<br /> getter Ad(index long non signé);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdAssetList</strong>: (Pas de modification pour la version 2.0)</td> 
   <td><p>interface AdAssetList {<br /> readonly attribut de longue durée non signé ;<br /> getter AdAsset(index long non signé);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p><strong>AdBannerAsset</strong>: interface AdBannerAsset : AdAsset<br /> {<br /> readonly attribut int width;<br /> readonly attribut int height;<br /> readonly, attribut DomString staticUrl;<br /> readonly, attribut Hauteur DomString;<br /> readonly, attribut Largeur de DomString;<br /> };</p> </td> 
   <td> Nouveautés de la version 2.0</td> 
  </tr> 
 </tbody> 
</table>

### AdBreakTimelineItem / AdTimelineItem {#adbreaktimelineitem-adtimelineitem}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p> <strong>AdBreakTimelineItem</strong>: interface AdBreakTimelineItem : TimelineItem { <br /> attribut readonly AdBreak adBreak; attribut <br /> readonly éléments AdTimelineItemList ; <br /> }; </p> </td> 
   <td> (Nouveauté de la version 2.0)</td> 
  </tr> 
  <tr> 
   <td><p><strong>AdTimelineItem</strong>: interface AdTimelineItem : TimelineItem { <br /> attribut readonly AdBreak adBreak; Attribuer <br /> en lecture seule la publicité publicitaire ; <br /> }; </p> </td> 
   <td> (Nouveauté de la version 2.0)</td> 
  </tr> 
  <tr> 
   <td><p><strong>AdBreakTimelineItemList</strong>: interface AdBreakTimelineItemList { <br /> attribut readonly de longueur longue non signée ; getAdBreakTimelineItem (index lo ng non signé) <br /> ; <br /> };</p> </td> 
   <td> (Nouveauté de la version 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### AdBreakPolicy / AdBreakWatchedPolicy / AdPolicyMode / AdPolicyInfo / AdPolicySelector {#adbreakpolicy-adbreakwatchedpolicy-adpolicy-adpolicymode-adpolicyinfo-adpolicyselector}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>interface AdBreakPolicy {<br /> readonly attribut short AD_BREAK_POLICY_SKIP;<br /> readonly attribut short AD_BREAK_POLICY_PLAY;<br /> readonly attribut short AD_BREAK_POLICY_REMOVE;<br /> readonly attribut short AD_BREAK_POLICY_REMOVE_AFTER_PLAY;<br /> };</p> </td> 
   <td><p> interface AdPolicyConstants {<br /> readonly attribut short AD_BREAK_POLICY_SKIP;<br /> readonly attribut short AD_BREAK_POLICY_PLAY;<br /> readonly attribut short AD_BREAK_POLICY_REMOVE;<br /> readonly attribut short AD_BREAK_POLICY_REMOVE_AFTER_PLAY;<br /> ...</p> </td> 
  </tr> 
  <tr> 
   <td><p> interface AdBreakWatchedPolicy {<br /> readonly attribut short AD_BREAK_AS_WATCHED_ON_BEGIN;<br /> readonly attribut short AD_BREAK_AS_WATCHED_ON_END;<br /> readonly attribut short AD_BREAK_AS_WATCHED_NEVER;<br /> }; </p> </td> 
   <td><p> ...<br /> readonly attribut short AD_BREAK_AS_WATCHED_ON_BEGIN;<br /> readonly attribut short AD_BREAK_AS_WATCHED_ON_END;<br /> readonly attribut short AD_BREAK_AS_WATCHED_NEVER;<br /> ...</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicy {<br /> readonly attribut short AD_POLICY_PLAY;<br /> readonly attribut short AD_POLICY_PLAY_FROM_AD_BEGIN;<br /> readonly attribut short AD_POLICY_PLAY_FROM_AD_BREAK_BEGIN; readonly attribut short AD_POLICY_SKIP_TO_NEXT_AD_IN_BREAK;<br /> attribut <br /> readonly short AD_POLICY_SKIP_AD_BREAK;<br /> };</p> </td> 
   <td><p> ... attribut <br /> readonly short AD_POLICY_PLAY;<br /> readonly attribut short AD_POLICY_PLAY_FROM_AD_BEGIN;<br /> readonly attribut short AD_POLICY_PLAY_FROM_AD_BREAK_BEGIN;<br /> readonly attribut short AD_POLICY_SKIP_TO_NEXT_AD_IN_BREAK;<br /> readonly attribut short AD_POLICY_SKIP_AD_BREAK;<br /> ...</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicyMode {<br /> readonly attribut short AD_POLICY_MODE_PLAY;<br /> readonly attribut short AD_POLICY_MODE_SEEK;<br /> readonly attribut short AD_POLICY_MODE_TRICKPLAY;<br /> };</p> </td> 
   <td><p> ...<br /> readonly attribut short AD_POLICY_MODE_PLAY;<br /> readonly attribut short AD_POLICY_MODE_SEEK;<br /> readonly attribut short AD_POLICY_MODE_TRICKPLAY;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicyInfo {<br /> attribut readonly AdBreakTimelineItemList <br /> adBreakTimelineItems;<br /> readonly attribut AdTimelineItem adTimelineItem;<br /> readonly, attribut  currentTime;<br /> l'attribut readonly  searchToTime;<br /> taux de  des attributs readonly;<br /> readonly attribut short mode; //AdPolicyMode<br /> };</p> </td> 
   <td><p>interface AdPolicyInfo {<br /> readonly attribut AdBreakPlacementList <br /> adBreakPlacements;<br /> readonly attribut publicité de l'annonce publicitaire ;<br /> readonly, attribut  currentTime;<br /> l'attribut readonly  searchToTime;<br /> taux de  des attributs readonly;<br /> readonly attribut short mode; //AdPolicyMode<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicySelector {<br /> /**<br /> * AdbreakPolicy selectPolicyForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribut Objet selectPolicyForAdBreakCallbackFunc;<br /> /**<br /> * AdBreakTimelineItemList selectAdBreaksToPlay(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribut Objet selectAdBreaksToPlayCallbackFunc;<br /> /**<br /> * AdPolicy selectPolicyForSeekIntoAd(AdPolicyInfo adPolicyInfo);<br /> */<br /> attribut Objet selectPolicyForSeekIntoAdCallbackFunc; <br /> /**<br /> * AdBreakWatchedPolicy selectWatchedPolicyForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribut Objet selectWatchedPolicyForAdBreakCallbackFunc;<br /> };</p> </td> 
   <td><p>interface AdPolicySelector {<br /> /**<br /> * AdbreakPolicy selectPolicyForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribut Objet selectPolicyForAdBreakFuncCallback;<br /> /**<br /> * AdBreakPlacementList selectAdBreaksToPlay(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribut Objet selectAdBreaksToPlayCallback;<br /> /**<br /> * AdPolicy selectPolicyForSeekIntoAd(AdPolicyInfo adPolicyInfo);<br /> */<br /> attribut Objet selectPolicyForSeekIntoAdCallback; <br /> /**<br /> * AdBreakAsWatched selectWatchedPolicyForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribut Objet selectWatchedPolicyForAdBreakCallback;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### TimelineOperation {#timelineoperation}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>interface TimelineOperation { <br /> attribut readonly Emplacement ; <br /> };</p> </td> 
   <td> (Nouveauté de la version 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### AdBreakPlacement {#adbreakplacement}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>interface AdBreakPlacement : TimelineOperation {<br /> readonly attribute AdBreak adBreak;<br /> placement de l'attribut readonly; // A partir de TimelineOperation<br /> readonly attribut  temps de ;<br /> readonly attribut  la durée du;<br /> };</p> </td> 
   <td><p>interface AdBreakPlacement {<br /> en lecture seule attribut AdBreak adBreak;<br /> placement de l'attribut readonly;<br /> readonly attribut  temps de ;<br /> readonly attribut  la durée du;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### ParamètresAuditude {#auditudesettings}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>interface AuditudeSettings : AdvertisingMetadata { <br /> attribut DomString zoneId; <br /> attribut DomString mediaId; <br /> attribut DomString defaultMediaId ; <br /> attribut Domaine DomString ; <br /> attribut Objet targetingInfo ; <br /> attribut Object customParameters ; <br /> attribut Boolean creativePackingEnabled ;<br /> attribut Boolean showStaticBanners ;<br /> };</p> </td> 
   <td>La fonctionnalité a été fournie par la clé MetadataKeys::AUDITUDE_METADATA_KEY.</td> 
  </tr> 
 </tbody> 
</table>

## Modifications de l’élément API de personnalisation pour la version 2.0 {#customization-api-element-changes-for}

Ces tableaux comparent les éléments d’API de personnalisation pour le SDK JavaScript TVSDK entre les versions 1.3 et 2.0.

Tableaux dans cette rubrique :

* MediaPlayerItemConfig
* ContentFactory
* NetworkConfiguration

### MediaPlayerItemConfig {#mediaplayeritemconfig}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayerItemConfig {<br /> attribut ContentFactory adFactory;<br /> attribute StringList subscriTags;<br /> <br /> attribut StringList adTags;<br /> <br /> <br /> attribut AdSignalingMode adSignalingMode;<br /> attribut CustomRangeMetadata customRangeMetadata;<br /> attribut NetworkConfiguration networkConfiguration;<br /> attribut AdvertisingMetadata AdvertisingMetadata;<br /> attribut Boolean useHardwareDecoder;<br /> };</p> </td> 
   <td><p>interface MediaPlayerConfig {<br /> <br /> <br /> attribut <br /> StringList adTags;<br /> attribute StringList subscribedTags;<br /> attribut MediaPlayerClientFactory clientFactory;<br /> <br /> <br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### ContentFactory {#contentfactory}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface ContentFactory {<br /> /*<br /> * AdPolicySelector retrieveAdPolicySelector(<br /> * élément MediaPlayerItem);<br /> */<br /> attribut Object retrieveAdPolicySelectorCallbackFunc;<br /> };</p> </td> 
   <td><p>interface MediaPlayerClientFactory {<br /> /*<br /> * AdPolicySelector retrieveAdPolicySelector(<br /> * élément MediaPlayerItem);<br /> */<br /> attribut Object retrieveAdPolicySelectorFunc;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### NetworkConfiguration {#networkconfiguration}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface NetworkConfiguration<br /> {<br /> attribut booléen forceNativeNetworking;<br /> attribut booléen useRedirectUrl;<br /> attribute Object cookieHeader;<br /> attribut booléen readSetCookieHeader;<br /> attribut int masterUpdateInterval; <br /> attribut booléen useCookieHeaderForAllRequests;<br /> attribut int readLimit;<br /> };</p> </td> 
   <td>Dans la version 1.3, certaines de ces fonctionnalités étaient fournies par MetadataKeys.</td> 
  </tr> 
 </tbody> 
</table>

## Modifications des éléments de l’API DRM pour la version 2.0 {#drm-api-element-changes-for}

Ces tableaux comparent les éléments de l’API DRM pour le SDK JavaScript TVSDK entre les versions 1.3 et 2.0.

Tableaux dans cette rubrique :

* Initialisation du processus DRM
* DRMAcquireLicenseSettings / DRMAuthenticationMethod
* DRMMetadata
* DRMPlaybackTimeWindow
* DRMLicense
* DRMLicenseDomain
* DRMPolicy
* DRMManager

### Initialisation du processus DRM {#drm-workflow-initialization}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td>L’application doit appeler AdobePSDK.initiateDRMWorkflow pour lancer le flux de travaux DRM. Sans cet appel, les vidéos DRM ne seront pas lues.<p>interface AdobePSDK<br /> {<br /> void initiateDRMWorkFlow(<br /> DomString appStoratePath, <br /> DomString publisherId, <br /> DomString appId, <br /> DomString appVersion, <br /> booléen privacyModeOn);<br /> };</p> </td> 
   <td>L’initialisation a été effectuée en interne et aucun appel explicite n’était requis.</td> 
  </tr> 
 </tbody> 
</table>

### DRMAcquireLicenseSettings/DRMAuthenticationMethod {#drmacquirelicensesettings-drmauthenticationmethod}

| 2.0 API | 1.3 API |
|--- |--- |
| **DRMAcquireLicenseSettings** |  |
| Aucune modification pour la version 2.0. | enum DRMAcquireLicenseSettings <br>{<br> const unsigned int FORCE_REFRESH = 0;<br> const unsigned int LOCAL_ONLY = 1;<br> const unsigned int ALLOW_SERVER = 2;<br> }; |
| **DRMAuthenticationMethod** |  |
| Aucune modification pour la version 2.0. | enum DRMAuthenticationMethod <br>{<br> const unsigned int UNKNOWN = 0;<br> const unsigned int ANONYMOUS = 1;<br> const unsigned int USERNAME_AND_PASSWORD = 2;<br> } |

### DRMMetadata {#drmmetadata}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td>Aucune modification pour la version 2.0.</td> 
   <td><p>interface DRMMetadata<br /> {<br /> readonly attribut DomString serverUrl;<br /> readonly, attribut DomString licenseId;<br /> readonly, attribut stratégies DRMPolicyArray ; <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMPlaybackTimeWindow {#drmplaybacktimewindow}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface DRMPlaybackTimeWindow {<br /> attribut readonly int playbackPeriodInSeconds;<br /> readonly attribut long playbackStartDate;<br /> readonly attribut long playbackEndDate;<br /> };</p> </td> 
   <td><p>interface DRMPlaybackTimeWindow {<br /> attribut readonly int periodInSeconds;<br /> readonly attribut int startDate;<br /> readonly attribut int endDate;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMLicense {#drmlicense}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td>Aucune modification pour la version 2.0.</td> 
   <td><p>interface DRMLicense {<br /> readonly attribut Uint8Array bytes;<br /> readonly attribut Date licenseStartDate;<br /> readonly attribut Date licenseEndDate;<br /> readonly, attribut Date offlineStorageStartDate;<br /> readonly, attribut Date offlineStorageEndDate; attribut <br /> readonly DomString serverUrl;<br /> readonly, attribut DomString licenseID;<br /> readonly attribut DomString policyID;<br /> readonly, attribut DRMPlaybackTimeWindow playbackTimeWindow;<br /> readonly, attribut Object customProperties;<br /> }; </p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMLicenseDomain {#drmlicensedomain}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface DRMLicenseDomain {<br /> readonly attribut DomString authenticationDomain;<br /> readonly, attribut DRMAuthenticationMethod authenticationMethod; attribut <br /> readonly DomString serverUrl;<br /> };</p> </td> 
   <td><p>interface DRMLicenseDomain {<br /> readonly attribut DomString authDomain;<br /> readonly, attribut DRMAuthenticationMethod authMethod; attribut <br /> readonly DomString serverURL;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMPolicy {#drmpolicy}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface DRMPolicy<br /> {<br /> readonly attribut DomString authenticationDomain;<br /> readonly, attribut DRMAuthenticationMethod authenticationMethod;<br /> attribut <br /> readonly DomString displayName;<br /> readonly, attribut DRMLicenseDomain licenseDomain;<br /> };</p> </td> 
   <td><p>interface DRMPolicy<br /> {<br /> readonly attribut DomString authDomain;<br /> readonly, attribut DRMAuthenticationMethod authMethod;<br /> readonly attribut DomString dispName;<br /> readonly, attribut DRMLicenseDomain licenseDomain;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMManager {#drmmanager}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface DRMManager : EventTarget {<br /> void acquisitionLicense(DRMMetadata metadata metadata, <br /> paramètre DRMAcquireLicenseSettings, <br /> écouteur DRMAquireLicenseListener);<br /> void acquisitionPreviewLicense(DRMMetadata metadata, <br /> écouteur DRMAquireLicenseListener);<br /> void authenticate (métadonnées DRMMetadata, <br /> URL DomString,<br /> domaine d’authentification <br /> DomString, <br /> utilisateur DomString, mot de passe DomString, <br /> écouteur DRMAuthenticateListener);<br /> <br /> DRMMetadata createMetadataFromBytes(<br /> tableau Uint8Array, écouteur DRMErrorListener);<br /> void initialize(écouteur DRMOperationCompleteListener);<br /> attribut long maxOperationTime;<br /> void joinLicenseDomain( <br /> DRMLicenseDomain licenseDomain,<br /> booléen forceRefresh, <br /> <br /> écouteur DRMOperationCompleteListener);<br /> void leaveLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> écouteur DRMOperationCompleteListener);<br /> void resetDRM(écouteur DRMOperationCompleteListener <br /> );<br /> void returnLicense(DomString serverURL, <br /> DomString licenseID, <br /> DomString policyID, <br /> booléen commitImmédiatement,<br /> écouteur DRMReturnLicenseListener);<br /> void setAuthenticationToken(<br /> métadonnées de métadonnées DRMMetadata, <br /> DomString authenticationDomain, <br /> jeton Uint8Array, <br /> écouteur DRMOperationCompleteListener);<br /> void storeLicenseBytes(Uint8Array licenseBytes, <br /> écouteur DRMOperationCompleteListener);<br /> };</p> </td> 
   <td><p>interface DRMManager : EventTarget {<br /> void acquisitionLicense(DRMMetadata metadata metadata, <br /> paramètre DRMAcquireLicenseSettings, <br /> EventContext eventContext);<br /> void acquisitionPreviewLicense(DRMMetadata metadata, <br /> EventContext eventContext);<br /> void authenticate (métadonnées de métadonnées DRMMetadata, <br /> URL DomString,<br /> domaine d’authentification <br /> DomString, <br /> utilisateur DomString, mot de passe DomString, <br /> contexte d’événementContext);<br /> <br /> DRMMetadata createMetadataFromBytes(<br /> tableau Uint8Array, EventContext eventContext);<br /> void initialize(EventContext eventContext);<br /> attribut long maxOperationTime;<br /> void joinLicenseDomain( <br /> DRMLicenseDomain licenseDomain,<br /> booléen forceRefresh, <br /> <br /> EventContext eventContext);<br /> void leaveLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> EventContext eventContext);<br /> void resetDRM(EventContext eventContext) <br /> ;<br /> void returnLicense(DomString serverURL, <br /> DomString licenseID,<br /> DomString policyID, <br /> booléen commitImmédiatement,<br /> EventContext);<br /> void setAuthenticationToken(<br /> métadonnées de métadonnées DRMMetadata, <br /> DomString authenticationDomain, <br /> jeton Uint8Array, <br /> EventContext eventContext);<br /> void storeLicenseBytes(Uint8Array licenseBytes, <br /> EventContext eventContext);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>class DRMErrorListener : <br /> public psdkutils::PSDKInterfaceWithUserData {<br /> public:<br /> void virtuel onDRMError(uint32_t majeur, <br /> uint32_t mineur, <br /> const psdkutils: PSDKString&amp; errorString, <br /> const psdkutils::PSDKString&amp; errorServerUrl) = 0;<br /> <br /> protégé :<br /> virtual ~DRMErrorListener() {}<br /> }</p> </td> 
   <td> / Interface / Description 
    <ul> 
     <li>kEventDRMOperationError<p>/ DRMOperationErrorEvent</p> <p>Lorsqu’une erreur se produit lors de l’une des méthodes asynchrones de DRMManger.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>class DRMOperationCompleteListener : <br /> public DRMErrorListener {<br /> public :<br /> void virtuel onDRMOperationComplete() = 0;<br /> <br /> protégé :<br /> virtual ~DRMOperationCompleteListener() {}<br /> };</p> </td> 
   <td> / Interface / Description 
    <ul> 
     <li>kEventDRMInitializationComplete<p>/ PSDKEvent</p> <p>Une fois l’initialisation de DRM terminée.</p> </li> 
     <li>kEventDRMJoinLicenseDomainComplete<p>/ PSDKEvent</p> <p>Lorsque l’action joinLicenseDomain() se termine correctement.</p> </li> 
     <li>kEventDRMLeaveLicenseDomainComplete<p>/ PSDKEvent</p> <p>Lorsque l’action leaveLicenseDomain() se termine correctement.</p> </li> 
     <li>kEventDRMResetCompletePSDKEvent<p>/ PSDKEvent</p> <p>Lorsque l’action resetDRM() se termine correctement.</p> </li> 
     <li>kEventDRMAuthenticationTokenSet<p>/ PSDKEvent</p> <p>Lorsque l’action setAuthenticationTokenSet() se termine correctement.</p> </li> 
     <li>kEventDRMLicenseStored<p>/ PSDKEvent</p> <p>Lorsque l’action storeLicenseBytes() se termine correctement.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>class DRMAuthenticateListener : <br /> public DRMErrorListener {<br /> public :<br /> void virtuel onAuthenticationComplete(<br /> psdkutils::PSDKImmutableByteArray* <br /> authenticationToken) = 0;<br /> <br /> protégé :<br /> virtual ~DRMAuthenticateListener() {}<br /> }</p> </td> 
   <td> / Interface / Description 
    <ul> 
     <li>kEventDRMAuthenticationComplete<p>/ DRMAuthenticationCompleteEvent</p> <p>Lorsque l’appel de la méthode DRMManager::authenticate réussit.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>classe DRMAquireLicenseListener: <br /> public DRMErrorListener {<br /> public :<br /> void virtuel onLicenseAcquired(const DRMLicense*) = 0;<br /> <br /> protégé :<br /> virtual ~DRMAquireLicenseListener() {}<br /> };</p> </td> 
   <td> / Interface / Description 
    <ul> 
     <li>kEventDRMPreviewLicenseAcquired<p>/ DRMLicenseAcquiredEvent</p> <p>Lorsque l’appel de la méthode DRMManager::acquisitionPreviewLicense réussit.</p> </li> 
     <li>kEventDRMLicenseAcquired<p>/ DRMLicenseAcquiredEvent</p> <p>Lorsque l’appel de la méthode DRMManager::purchaseLicense réussit.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>classe DRMReturnLicenseListener: <br /> public DRMErrorListener {<br /> public :<br /> void virtuel onLicenseReturnComplete(uint32_t numReturn ) = 0;<br /> <br /> protégé :<br /> virtual ~DRMReturnLicenseListener() {}<br /> };</p> </td> 
   <td> / Interface / Description 
    <ul> 
     <li>kEventDRMLicenseReturnComplete<p>/ DRMLicenseReturnCompleteEvent</p> <p>Lorsque l’appel de la méthode DRMManager::returnLicense réussit.</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Modifications de l’élément API de lecture générique pour la version 2.0 {#generic-playback-api-element-changes-for}

Ces tableaux comparent les éléments génériques de l’API de lecture entre JavaScript TVSDK 1.3 et 2.0.

Tableaux dans cette rubrique :

* MediaResource
* MediaPlayer
* ABRControlParameters
* BufferControlParameters
* TextFormat
* MediaPlayerItemLoader

### MediaResource {#mediaresource}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaResource {<br /> attribut URL DomString; attribut <br /> type court non signé;<br /> métadonnées d’objet d’attribut ;<br /> const short TYPE_HLS non signé;<br /> const short TYPE_HDS non signé;<br /> const unsigned short TYPE_DASH;<br /> const unsigned short TYPE_CUSTOM;<br /> const unsigned short TYPE_UNKNOWN;<br /> };</p> </td> 
   <td><p>interface MediaResource {<br /> attribut URL DomString;<br /> attribut DomString type;<br /> métadonnées d’objet d’attribut ;<br /> <br /> <br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### MediaPlayer {#mediaplayer}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayer : EventTarget<br /> {<br /> void prepareToPlay(  position du);<br /> void play();<br /> void pause();<br /> void search(position  du);<br /> void searchToLocal(position );<br /> void reset();<br /> void release();<br /> void replaceCurrentItem(élément MediaPlayerItem);<br /> void replaceCurrentResource(MediaResource source, <br /> MediaPlayerItemConfig); void suspend(); <br /><br /> void restore();<br /> void notificationClick();<br /> attribut <br /> readonly TimeRange playbackRange;<br /> readonly, attribut TimeRange seekableRange;<br /> readonly, attribut  currentTime;<br /> readonly, attribut  localTime;<br /> readonly, attribut TimeRange bufferedRange;<br /> readonly, attribut DRMManager drmManager;<br /> readonly attribut MediaPlayerItem currentItem;<br /> <br /> // PlayerStatus<br /> const <br /> <br /> non signé short PLAYER_STATUS_INITIALIZED;<br /> const unsigned short PLAYER_STATUS_PREPARING;<br /> const unsigned short PLAYER_STATUS_PREPARED;<br /> const unsigned short PLAYER_STATUS_PLAYING;<br /> const unsigned short PLAYER_STATUS_PAUSED;<br /> const unsigned short PLAYER_STATUS_SEEKING;<br /> const unsigned short PLAYER_STATUS_COMPLETE;<br /> const unsigned short PLAYER_STATUS_ERROR;<br /> const unsigned short PLAYER_STATUS_RELEASED;<br /> attribut <br /> readonly statut court non signé ;<br /> <br /> attribut volume court non signé;<br /> attribut ABRControlParameters abrControlParameters;<br /> attribut BufferControlParameters bufferControlParameters;<br /> const <br /> non signé short VISIBLE; //Pour la conne de visibilité<br /> CC non signée short INVISIBLE; //Pour l'attribut de visibilité<br /> CC unsigned short ccVisibility;<br /> attribut TextFormat ccStyle;<br /> readonly attribut PlaybackMetrics playbackMetrics ;<br /> <br /> attribut  taux;<br /> attribut  MediaPlayerView ;<br /> readonly, attribut Chronologie chronologique du journal;<br /> d'attributs  currentTimeUpdateInterval; <br /> // la définition de ce paramètre ne sera pas prise en charge pour 2.0<br /> };</p> </td> 
   <td><p>interface MediaPlayer : EventTarget<br /> {<br /> void prepareToPlay( position int);<br /> void play();<br /> void pause();<br /> void search( position int);<br /> void searchToLocalTime( position int);<br /> void reset();<br /> void release();<br /> void replaceCurrentItem(source MediaResource);<br /> <br /><br /> <br /> <br /> <br /> <br /> attribut en lecture seule de TimeRange playbackRange;<br /> readonly, attribut TimeRange seekableRange;<br /> readonly, attribut  currentTime;<br /> readonly, attribut  localTime;<br /> readonly, attribut TimeRange bufferedRange;<br /> readonly, attribut DRMManager drmManager;<br /> readonly attribut MediaPlayerItem currentItem;<br /> <br /> // PlayerState<br /> conne short non signé PLAYER_STATE_IDLE;<br /> const unsigned short PLAYER_STATE_INITIALIZING;<br /> const unsigned short PLAYER_STATE_INITIALIZED;<br /> const unsigned short PLAYER_STATE_PREPARING;<br /> const unsigned short PLAYER_STATE_PREPARED;<br /> const unsigned short PLAYER_STATE_PLAYING;<br /> const unsigned short PLAYER_STATE_PAUSED;<br /> const unsigned short PLAYER_STATE_SEEKING;<br /> const unsigned short PLAYER_STATE_COMPLETE;<br /> const unsigned short PLAYER_STATE_ERROR;<br /> const unsigned short PLAYER_STATE_RELEASED;<br /> const unsigned short PLAYER_STATUS_SUSPENDED;<br /> readonly attribut unsigned short state;<br /> <br /> attribut volume court non signé;<br /> attribut ABRControlParameters abrControlParameters;<br /> attribut BufferControlParameters bufferControlParameters;<br /> VISIBLE en <br /> lecture seule non signée; //Pour la visibilité<br /> CC en lecture seule, non signé court INVISIBLE; //Pour l'attribut de visibilité<br /> CC unsigned short ccVisibility;<br /> attribut TextFormat ccStyle;<br /> readonly attribut PlaybackMetrics playbackMetrics ;<br /> attribut MediaPlayerConfig mediaPlayerConfig;<br />  d'attributs;<br /> attribut  MediaPlayerView ;<br /> readonly, attribut Chronologie chronologique du journal;<br /> <br /> } <br /> ;</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayerStatus<br /> {<br /> // PlayerStatus<br /> consuite non signée short PLAYER_STATUS_IDLE;<br /> const unsigned short PLAYER_STATUS_INITIALIZING;<br /> const unsigned short PLAYER_STATUS_INITIALIZED;<br /> const unsigned short PLAYER_STATUS_PREPARING;<br /> const unsigned short PLAYER_STATUS_PREPARED;<br /> const unsigned short PLAYER_STATUS_PLAYING;<br /> const unsigned short PLAYER_STATUS_PAUSED;<br /> const unsigned short PLAYER_STATUS_SEEKING;<br /> const unsigned short PLAYER_STATUS_COMPLETE;<br /> const unsigned short PLAYER_STATUS_ERROR;<br /> const unsigned short PLAYER_STATUS_RELEASED;<br /> const unsigned short PLAYER_STATUS_SUSPENDED;<br /> };</p> </td> 
   <td>(Nouveauté de la version 2.0)</td> 
  </tr> 
 </tbody> 
</table>

####  pris en charge par MediaPlayer {#events-supported-by-mediaplayer}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 Nom  du</th> 
   <th>Interface 2.0</th> 
   <th> </th> 
   <th>1.3 Nom  du</th> 
   <th>1.3 Interface</th> 
  </tr> 
  <tr> 
   <td><p>(supprimé pour la version 2.0)</p> </td> 
   <td> </td> 
   <td> </td> 
   <td>préparé</td> 
   <td>Event</td> 
  </tr> 
  <tr> 
   <td><p>itemUpgrade</p> <p>Lorsqu’un élément du lecteur multimédia est mis à jour.</p> </td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>mis à jour</p> <p>Une fois que le lecteur de médias a mis à jour le média.</p> </td> 
   <td>Event</td> 
  </tr> 
  <tr> 
   <td>timedMetadataAvailable</td> 
   <td>TimedMetadataEvent</td> 
   <td> </td> 
   <td>TtmedMetadata</td> 
   <td>TimedMetadataEvent</td> 
  </tr> 
  <tr> 
   <td>timelineUpdate</td> 
   <td>Event</td> 
   <td> </td> 
   <td>CalendrierMis à jour</td> 
   <td>Event</td> 
  </tr> 
  <tr> 
   <td>Supprimé dans la version 2.0</td> 
   <td> </td> 
   <td> </td> 
   <td>playStart</td> 
   <td>Event</td> 
  </tr> 
  <tr> 
   <td>Supprimé pour la version 2.0</td> 
   <td> </td> 
   <td> </td> 
   <td>playComplete</td> 
   <td>Event</td> 
  </tr> 
  <tr> 
   <td>statusChanged</td> 
   <td>StatusEvent</td> 
   <td> </td> 
   <td>stateChanged</td> 
   <td>StateEvent</td> 
  </tr> 
  <tr> 
   <td>sizeAvailable</td> 
   <td>SizeEvent</td> 
   <td> </td> 
   <td>taille</td> 
   <td>SizeEvent</td> 
  </tr> 
  <tr> 
   <td>adBreakStarted</td> 
   <td>AdBreakEvent</td> 
   <td> </td> 
   <td>adBreakStart</td> 
   <td>AdBreakEvent</td> 
  </tr> 
  <tr> 
   <td>adStarted</td> 
   <td>AdEvent</td> 
   <td> </td> 
   <td>adStart</td> 
   <td>AdEvent</td> 
  </tr> 
  <tr> 
   <td>adProgress</td> 
   <td>AdProgressEvent</td> 
   <td> </td> 
   <td>adProgress</td> 
   <td>AdProgressEvent</td> 
  </tr> 
  <tr> 
   <td>adCompleted</td> 
   <td>AdEvent</td> 
   <td> </td> 
   <td>adComplete</td> 
   <td>AdEvent</td> 
  </tr> 
  <tr> 
   <td>adBreakCompleted</td> 
   <td>AdBreakEvent</td> 
   <td> </td> 
   <td>adBreakComplete</td> 
   <td>AdBreakEvent</td> 
  </tr> 
  <tr> 
   <td>timeChanged</td> 
   <td>TimeEvent</td> 
   <td> </td> 
   <td>progression</td> 
   <td>ProgressEvent</td> 
  </tr> 
  <tr> 
   <td>bufferingBegin</td> 
   <td>Event</td> 
   <td> </td> 
   <td>tampon</td> 
   <td>Event</td> 
  </tr> 
  <tr> 
   <td>bufferingEnd</td> 
   <td>Event</td> 
   <td> </td> 
   <td>bufferComplete</td> 
   <td>Event</td> 
  </tr> 
  <tr> 
   <td>searchBegin</td> 
   <td>SeekEvent</td> 
   <td> </td> 
   <td>searchStart</td> 
   <td>Event</td> 
  </tr> 
  <tr> 
   <td>searchEnd</td> 
   <td>SeekEvent</td> 
   <td> </td> 
   <td>searchComplete</td> 
   <td>TimeEvent</td> 
  </tr> 
  <tr> 
   <td>loadInformationAvailable</td> 
   <td>LoadInformationEvent</td> 
   <td> </td> 
   <td>loadInfo</td> 
   <td>LoadInfoEvent</td> 
  </tr> 
  <tr> 
   <td>operationFailed</td> 
   <td>NotificationEvent</td> 
   <td> </td> 
   <td>operationFailed</td> 
   <td>ErrorEvent</td> 
  </tr> 
  <tr> 
   <td>drmMetadataInfoAvailable</td> 
   <td>DRMMetadataEvent</td> 
   <td> </td> 
   <td>drmMetadata</td> 
   <td>DRMMetadataEvent</td> 
  </tr> 
  <tr> 
   <td>reservationReached</td> 
   <td>ReservationEvent</td> 
   <td> </td> 
   <td>timelineHolderReached</td> 
   <td>TimelineHolderEvent</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td>bitrateChanged</td> 
   <td>BitrateChangedEvent</td> 
  </tr> 
  <tr> 
   <td>rateSelected</td> 
   <td>PlaybackRateEvent</td> 
   <td> </td> 
   <td>rateSelected</td> 
   <td>PlaybackRateEvent</td> 
  </tr> 
  <tr> 
   <td>ratePlaying</td> 
   <td>PlaybackRateEvent</td> 
   <td> </td> 
   <td>ratePlaying</td> 
   <td>PlaybackRateEvent</td> 
  </tr> 
  <tr> 
   <td>adBreakSkipped</td> 
   <td>AdBreakEvent</td> 
   <td> </td> 
   <td>adBreakSkipped</td> 
   <td>AdBreakEvent</td> 
  </tr> 
  <tr> 
   <td>adClick<br /> Lorsque l’utilisateur clique sur une publicité.</td> 
   <td>AdClickedEvent</td> 
   <td> </td> 
   <td><p>Nouveautés de la version 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>profileChanged<br /> Lorsque le de lecture change.</td> 
   <td>ProfileEvent</td> 
   <td> </td> 
   <td><p>Nouveautés de la version 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>ChercherPositionAjusté<br /> Lorsque la position de recherche s'ajuste en raison de règles internes ou externes.</td> 
   <td>SeekEvent</td> 
   <td> </td> 
   <td><p>Nouveautés de la version 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>audioUpdate<br /> Lorsqu’un élément du lecteur multimédia est mis à jour. Pour certains flux contenant des pistes audio détectables uniquement au moment de la lecture, ce est déclenché lorsque de nouvelles pistes audio sont disponibles.</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>Nouveautés de la version 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>légendesMise à jour <br /> lorsqu’un élément du lecteur multimédia est mis à jour. Pour les flux en direct/linéaires, le client doit actualiser périodiquement la ressource média afin de détecter le nouveau contenu disponible. Dans ce cas, certaines caractéristiques du média peuvent changer.</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>Nouveautés de la version 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>masterUpdate <br /> Lorsqu’un élément du lecteur multimédia est mis à jour. Pour les flux en direct/linéaires, le client doit actualiser périodiquement la ressource média afin de détecter le nouveau contenu disponible. Dans ce cas, certaines caractéristiques du média peuvent changer.</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>Nouveautés de la version 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>playbackRangeUpdate<br /> Lorsqu’un élément du lecteur multimédia est mis à jour. Pour les flux en direct/linéaires, le client doit actualiser périodiquement la ressource média afin de détecter le nouveau contenu disponible. Dans ce cas, certaines caractéristiques du média peuvent changer.</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>Nouveautés de la version 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>timedEvent<br /> Envoyé lors de la génération des  minutées.</td> 
   <td>TimedEvent</td> 
   <td> </td> 
   <td><p>Nouveautés de la version 2.0</p> </td> 
  </tr> 
 </tbody> 
</table>

### ABRControlParameters {#abrcontrolparameters}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface ABRControlParameters<br /> {<br /> const unsigned short ABR_POLICY_CONSERVATIVE = 0 ;<br /> const unsigned short ABR_POLICY_MODERATE = 1 ;<br /> const unsigned short ABR_POLICY_AGGRESIVE = 2 ;<br /> <br /> attribut abrPolicy non signé ;<br /> attribut unsigned int initialBitRate;<br /> attribut unsigned int minBitRate;<br /> attribut unsigned int maxBitRate;<br /> const unsigned short DEFAULT_ABR_INITIAL_BITRATE;<br /> const unsigned short DEFAULT_ABR_MIN_BITRATE;<br /> const unsigned short DEFAULT_ABR_MAX_BITRATE;<br /> const ABRPolicy DEFAULT_ABR_POLICY;<br /> };</p> </td> 
   <td><p>interface ABRControlParameters<br /> {<br /> const unsigned short ABR_POLICY_CONSERVATIVE = 0 ;<br /> const unsigned short ABR_POLICY_MODERATE = 1 ;<br /> const unsigned short ABR_POLICY_AGGRESIVE = 2 ;<br /> <br /> attribut abrPolicy non signé ;<br /> attribut unsigned int initialBitRate;<br /> attribut unsigned int minBitRate;<br /> attribut unsigned int maxBitRate;<br /> <br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### BufferControlParameters {#buffercontrolparameters}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface BufferControlParameters<br /> {<br /> attribut  initialBufferTime;<br /> attribut  playBufferTime;<br /> const  DEFAULT_INITIAL_BUFFER_TIME;<br /> const  DEFAULT_PLAY_BUFFER_TIME;<br /> };</p> </td> 
   <td><p>interface BufferControlParameters<br /> {<br /> attribut  initialBufferTime;<br /> attribut  playBufferTime;<br /> <br /> } <br /> ;</p> </td> 
  </tr> 
 </tbody> 
</table>

### TextFormat {#textformat}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td>Aucune modification pour la version 2.0</td> 
   <td><p>interface TextFormat<br /> {<br /> // Conteneur de couleurs<br /> courte non signée COLOR_DEFAULT = 0 ;<br /> const unsigned short COLOR_BLACK = 1 ;<br /> const unsigned short COLOR_GRAY = 2 ;<br /> const unsigned short COLOR_WHITE = 3 ;<br /> const unsigned short COLOR_BRIGHT_WHITE = 4 ;<br /> const unsigned short COLOR_DARK_RED = 5 ;<br /> const unsigned short COLOR_RED = 6 ;<br /> const unsigned short COLOR_BRIGHT_RED = 7 ;<br /> const unsigned short COLOR_DARK_GREEN = 8 ;<br /> const unsigned short COLOR_GREEN = 9 ;<br /> const unsigned short COLOR_BRIGHT_GREEN = 10 ;<br /> const unsigned short COLOR_DARK_BLUE = 11 ;<br /> const unsigned short COLOR_BLUE = 12 ;<br /> const unsigned short COLOR_BRIGHT_BLUE = 13 ;<br /> const unsigned short COLOR_DARK_YELLOW = 14 ;<br /> const unsigned short COLOR_YELLOW = 15 ;<br /> const unsigned short COLOR_BRIGHT_YELLOW = 16 ;<br /> const unsigned short COLOR_DARK_MAGENTA = 17 ;<br /> const unsigned short COLOR_MAGENTA = 18 ;<br /> const unsigned short COLOR_BRIGHT_MAGENTA = 19 ;<br /> const unsigned short COLOR_DARK_CYAN = 20 ;<br /> const unsigned short COLOR_CYAN = 21 ;<br /> const unsigned short COLOR_BRIGHT_CYAN = 22 ;<br /> attribut <br /> readonly unsigned short fontColor;<br /> readonly attribut unsigned short BackgroundColor;<br /> readonly attribut unsigned short fillColor;<br /> readonly attribut short edgeColor non signé;<br /> <br /> // Taille<br /> conne courte non signée SIZE_DEFAULT = 0 ;<br /> const unsigned short SIZE_SMALL = 1 ;<br /> const unsigned short SIZE_MEDIUM = 2 ;<br /> const unsigned short SIZE_LARGE = 3 ;<br /> attribut <br /> readonly unsigned short size;<br /> <br /> // FontEdge<br /> const unsigned short FONT_EDGE_DEFAULT = 0 ;<br /> const unsigned short FONT_EDGE_NONE = 1 ;<br /> const unsigned short FONT_EDGE_RAISED = 2 ;<br /> const unsigned short FONT_EDGE_DEPRESED = 3 ;<br /> const unsigned short FONT_EDGE_UNIFORM = 4 ;<br /> const unsigned short FONT_EDGE_DROP_SHADOW_LEFT = 5 ;<br /> const unsigned short FONT_EDGE_DROP_SHADOW_RIGHT = 6 ;<br /> readonly attribut unsigned short fontEdge;<br /> <br /> // Conteneur de polices<br /> non signée court FONT_DEFAULT = 0 ;<br /> const unsigned short FONT_MONOSPACED_WITH_SERIFS = 1 ;<br /> const unsigned short FONT_PROPORtional_WITH_SERIFS = 2 ;<br /> const unsigned short FONT_MONSPACED_WITHOUT_SERIFS = 3 ;<br /> const unsigned short FONT_CASUAL = 4 ;<br /> const unsigned short FONT_CURSIVE = 5 ;<br /> const unsigned short FONT_SMALL_CAPITALS = 6 ;<br /> readonly attribut unsigned short font;<br /> readonly attribut unsigned short fontOpacity;<br /> readonly attribut unsigned short BackgroundOpacity;<br /> readonly attribut unsigned short fillOpacity;<br /> readonly attribut unsigned short DEFAULT_OPACITY;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### MediaPlayerItemLoader {#mediaplayeritemloader}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayerItemLoader :<br /> {<br /> void load(ressource MediaResource, long resourceId,<br /> écouteur ItemLoaderListener, configuration <br /> MediaPlayerItemConfig) ;<br /> void cancel();<br /> readonly attribut MediaPlayerItem currentItem;<br /> };</p> </td> 
   <td>Nouveautés de la version 2.0</td> 
  </tr> 
  <tr> 
   <td><p>interface ItemLoaderListener<br /> {<br /> //onLoadCompleteCallbackFunc(MediaPlayerItem)<br /> var onLoadCompleteCallbackFunc;<br /> //onErrorCallbackFunc(PSDKErrorCode)<br /> var onErrorCallbackFunc;<br /> }</p> </td> 
   <td>Nouveautés de la version 2.0</td> 
  </tr> 
 </tbody> 
</table>

## Modifications des éléments de l’API des caractéristiques du média pour la version 2.0 {#media-characteristics-api-element-changes-for}

Ces tableaux comparent les éléments d’API caractéristiques du média pour le SDK TVSDK C++ entre les versions 1.3 et 2.0.

Tableaux dans cette rubrique :

* MediaPlayerItem
* Track, AudioTrack, ClosedCaptionsTrack
* Profile
* DRMMetadataInfo

### MediaPlayerItem {#mediaplayeritem}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayerItem {<br /> readonly attribut ressource MediaResource;<br /> readonly attribut long resourceId;<br /> readonly, attribut booléen live;<br /> attribut <br /> readonly boolean hasAlternateAudio;<br /> readonly attribut AudioTrackList audioTracks;<br /> attribut readonly AudioTrack selectedAudioTrack;<br /> void selectAudioTrack(AudioTrack); <br /> <br /> readonly attribut boolean hasClosedCaptions;<br /> readonly attribut ClosedCaptionsTrackList closeCaptionsTracks;<br /> readonly attribut ClosedCaptionsTrack selectedClosedCaptionsTrack;<br /> void selectClosedCaptionsTrack(<br /> ClosedCaptionsTrack); <br /> <br /> readonly attribut boolean hasTimedMetadata;<br /> readonly, attribut TimedMetadataList timedMetadata;<br /> readonly, attribut boolean dynamic;<br /> L'attribut <br /> readonly boolean isProtected;<br /> readonly, attribut DRMMetadataInfoList drmMetadataInfos;<br /> readonly attribut ProfileList ;<br /> readonly, attribut  selectedProfile;<br /> attribut <br /> readonly boolean trickPlaySupported;<br /> readonly attribut FloatArray availablePlaybackRates;<br /> readonly attribut float selectedPlaybackRate;<br /> <br /> <br /> readonly attribut MediaPlayer mediaPlayer;<br /> readonly attribut MediaPlayerItemConfig config;<br /> };</p> </td> 
   <td><p>interface MediaPlayerItem {<br /> readonly attribut ressource MediaResource;<br /> readonly attribut long resourceId;<br /> readonly, attribut booléen live;<br /> attribut <br /> readonly boolean hasAlternateAudio;<br /> readonly attribut AudioTrackList audioTracks;<br /> attribut AudioTrack selectedAudioTrack;<br /> <br /> <br /> readonly attribut boolean hasClosedCaptions;<br /> readonly attribut ClosedCaptionsTrackList ccTracks;<br /> attribut ClosedCaptionsTrack selectedCCTrack;<br /> <br /><br /> <br /> readonly attribut boolean hasTimedMetadata;<br /> readonly, attribut TimedMetadataList timedMetadata;<br /> readonly, attribut boolean dynamic;<br /> L'attribut <br /> readonly boolean isProtected;<br /> readonly, attribut DRMMetadataInfoList drmMetadataInfos;<br /> readonly attribut ProfileList ;<br /> attribut <br /> <br /> readonly boolean trickPlaySupported;<br /> attribut readonly Int32Array availablePlaybackRates;<br /> attribut <br /> readonly StringList adTags;<br /> <br /> readonly attribut MediaPlayer mediaPlayer;<br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### Track / AudioTrack / ClosedCaptionsTrack {#track-audiotrack-closedcaptionstrack}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface Track<br /> {<br /> readonly attribut DomString name;<br /> readonly, attribut langage DomString ;<br /> readonly, attribut booléen par défaut;<br /> readonly, attribut booléen autoSelect;<br /> }; </p> </td> 
   <td>Nouveautés de la version 2.0</td> 
  </tr> 
  <tr> 
   <td><p>interface AudioTrack : Track<br /> {<br /> readonly attribut DomString name; //FromTrack<br /> readonly attribut DomString language;//FromTrack<br /> readonly attribut booléen default; // De l'attribut de piste<br /> readonly booléen autoSelect;//DeTrack<br /> <br /> readonly attribut unsigned int pid;<br /> };</p> </td> 
   <td><p>interface AudioTrack<br /> {<br /> readonly attribut DomString name;<br /> readonly, attribut langage DomString ; attribut <br /> readonly boolean default;<br /> readonly, attribut booléen autoSelect;<br /> readonly, attribut booléen forcé;<br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td>Aucune modification pour la version 2.0</td> 
   <td><p>interface AudioTrackList<br /> {<br /> readonly attribut de longue durée non signé;<br /> getter AudioTrack (index long non signé);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface ClosedCaptionsTrack : Track<br /> {<br /> readonly attribut DomString name; //FromTrack<br /> readonly attribut DomString language;//FromTrack<br /> readonly attribut booléen default; // FromTrack<br /> readonly attribut booléen autoSelect;//FromTrack<br /> <br /> <br /> const abrégé SERVICE_608_CAPTIONS = 0;<br /> const unsigned short SERVICE_708_CAPTIONS = 1;<br /> const unsigned short SERVICE_WEB_VTT_CAPTIONS = 2;<br /> readonly attribut unsigned short serviceType;<br /> readonly, attribut booléen forcé;<br /> };</p> </td> 
   <td><p>interface ClosedCaptionsTrack<br /> {<br /> readonly attribut nom DomString;<br /> readonly, attribut langage DomString ;<br /> readonly, attribut booléen par défaut;<br /> attribut <br /> <br /> readonly boolean actif;<br /> <br /> <br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td>Aucune modification pour la version 2.0</td> 
   <td><p>interface ClosedCaptionsTrackList<br /> {<br /> attribut readonly de longue durée non signé ;<br /> getter ClosedCaptionsTrack(index long non signé);<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### Profile {#profile}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td> : Aucune modification pour la version 2.0</td> 
   <td><p>d'interface<br /> {<br /> readonly attribut unsigned int width;<br /> readonly attribut unsigned int height;<br /> readonly attribut unsigned int bitRate;<br /> }; </p> </td> 
  </tr> 
  <tr> 
   <td>ProfileList : Aucune modification pour la version 2.0</td> 
   <td><p>interface ProfileList<br /> {<br /> readonly attribut de longue durée non signé ;<br /> getter (index long non signé);<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMMetadataInfo {#drmmetadatainfo}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><strong>DRMMetadataInfo</strong>: Aucune modification pour la version 2.0</td> 
   <td><p>interface DRMMetadataInfo<br /> { <br /> attribut readonly métadonnées DRMMetadata;<br /> readonly attribut long prefetchTimestamp;<br /> readonly, attribut TimeRange timeRange;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>DRMMetadataInfoList</strong>: Aucune modification pour la version 2.0</td> 
   <td><p>interface DRMMetadataInfoList<br /> {<br /> attribut readonly de longue durée non signé;<br /> getter DRMMetadataInfo(index long non signé);<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

## Mappage des erreurs C++ aux exceptions dans différentes langues {#mapping-c-errors-to-exceptions-in-different-languages}

Vous pouvez mapper des codes d’erreur C++ à des exceptions dans différentes langues.

Le PSDK C++ a une stratégie &quot;pas de jeton&quot; pour ses API. La plupart des méthodes API renvoient une valeur PSDKErrorCode pour indiquer si la méthode a bien été exécutée. Les erreurs asynchrones sont averties via le d’erreurs.

La stratégie du PSDK ActionScript et JAVA est différente. La plupart des erreurs renvoient une exception ArgumentError ou IllegalStateException pour indiquer que la partie synchrone de la méthode n&#39;a pas pu être exécutée. Ces exceptions ne sont pas prises en compte et le code de l’application est responsable du traitement des exceptions. Elles contiennent généralement des informations utiles sur les raisons de l’échec de l’appel de méthode. Par exemple, si la commande prepareToPlay est appelée dans un état non valide, l’exception suivante est levée :

```shell
throw new IllegalStateException("Invalid player state. prepareToPlay method 
must be called only once after replaceCurrentItem or replaceCurrentResource method.");
```

Le code ActionScript/JAVA renvoie également des exceptions aux constructeurs pour indiquer que certains objets internes ont été créés de manière incorrecte. Ces exceptions sont gérées en interne et ne sont pas propagées dans l’application. Les exceptions seront incluses dans une notification d’avertissement envoyée à l’application.

Par exemple, si aucun fichier multimédia valide n’a été trouvé pour la réponse à la publicité reçue, aucun objet ou publicité de ressource publicitaire valide ne peut être créé. Par conséquent, aucune publicité n’est placée sur la chronologie et une notification NotificationEvent.OperationFailed est distribuée.

Les codes d’erreur ou d’avertissement reçus de manière asynchrone à partir du moteur vidéo Adobe (AVE) sont distribués dans l’application en tant que  normal. Le de notification contient tous les codes d’erreur reçus et toutes les métadonnées supplémentaires, telles que l’URL, l’identifiant de ressource, le nom d’utilisateur, etc. Si l’erreur est grave et que la lecture du média actuel ne peut pas continuer, le MediaPlayer  à l’état ERROR et le rappel onStatusChanged ou MediaPlayerStatusChanged.STATUS_CHANGED est distribué. Si la lecture peut continuer, un de notification normal est distribué.

<table> 
 <tbody> 
  <tr> 
   <th>Erreur C++ (code PSDKError)</th> 
   <th> </th> 
   <th>Java</th> 
   <th>ActionScript</th> 
   <th>JavaScript</th> 
  </tr> 
  <tr> 
   <td>kECInvalidArgument</td> 
   <td> </td> 
   <td>IllegalArgumentException</td> 
   <td>ArgumentError</td> 
   <td>Exception avec le code = 1, description = "INVALID_ARGUMENT" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECNullPointer</td> 
   <td> </td> 
   <td>IllegalArgumentException</td> 
   <td>ArgumentError</td> 
   <td>Exception avec le code = 2, description = "GENERIC_ERROR" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECIllegalState</td> 
   <td> </td> 
   <td>IllegalStateException</td> 
   <td>IllegalStateException</td> 
   <td>Exception avec le code = 3, description = "ILLEGAL_STATE" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECIInterfaceNotFound</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec le code = 4, description = "GENERIC_ERROR" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECCreationFailed</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec le code = 5, description = "CREATION_FAILED" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECUnsupportedOperation</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec le code = 5, description = "CREATION_FAILED" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kDCEataNotAvailable</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec le code = 7, description = "DATA_NOT_AVAILABLE" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECSeekError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec le code = 8, description = "SEEK_ERROR" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECUnsupportedFeature</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec le code = 9, description = "UNSUPPORTED_FEATURE" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECRangeError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec code = 10, description = "RANGE_ERROR" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception</td> 
  </tr> 
  <tr> 
   <td>kECCodecNotSupported</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec code = 11, description = "CODEC_NOT_SUPPORTED" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECMediaError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec code = 12, description = "MEDIA_ERROR" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECNetworkError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec code = 13, description = "NETWORK_ERROR" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECGenericError</td> 
   <td> </td> 
   <td>MediaPlayerNotification.Error ou MediaPlayerNotification.Warning</td> 
   <td>MediaError ou NotificationEvent</td> 
   <td>Exception avec code = 14, description = "GENERIC_ERROR" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECInvalidSeekTime</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec code = 15, description = "INVALID_SEEK_TIME" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECAudioTrackError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec code = 16, description = "AUDIO_TRACK_ERROR" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECAccessFromDifferent<p>ThreadError</p> </td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec code = 17, description = "GENERIC_ERROR" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECElementNotFound</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec code = 18, description = "GENERIC_ERROR" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception</td> 
  </tr> 
  <tr> 
   <td>kECNotImplémenté</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec code = 19, description = "GENERIC_ERROR" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECPlaybackOperationFailed</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec code = 200, description = "PLAYBACK_OPERATION_FAILED" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECNativeWarning</td> 
   <td> </td> 
   <td>MediaPlayerNotification.Warning</td> 
   <td>NotificationEvent</td> 
   <td>Exception avec code = 201, description = "NATIVE_WARNING" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception</td> 
  </tr> 
  <tr> 
   <td>kECAdResolverFailed</td> 
   <td> </td> 
   <td>MediaPlayerNotification.Warning</td> 
   <td>-</td> 
   <td>Exception avec code = 202, description = "AD_RESOLVER_FAILED" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
 </tbody> 
</table>

## Modifications des éléments de l’API Utilitaire et Assistant pour la version 2.0 {#utility-and-helper-api-element-changes-for}

Ces tableaux comparent les éléments API Utilitaire et Assistant pour le SDK JavaScript TVSDK entre les versions 1.3 et 2.0.

Tableaux dans cette rubrique :

* Version
* TimeRange
* QOSProvider
* DeviceInformation
* LoadInfo
* View
* PlaybackInformation

### Version {#version}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>version<br /> de l'interface {<br /> readonly attribut DomString version;<br /> readonly, attribut description de DomString;<br /> readonly attribut long major;<br /> readonly attribut long mineur;<br /> révision longue de l'attribut readonly;<br /> readonly attribut long apiVersion;<br /> };</p> </td> 
   <td><p>version<br /> de l'interface {<br /> readonly attribut DomString version;<br /> readonly, attribut description de DomString;<br /> readonly attribut DomString major;<br /> readonly attribut DomString mineur;<br /> révision DomString de l'attribut readonly;<br /> readonly, attribut DomString apiVersion;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### TimeRange {#timerange}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td>Aucune modification pour la version 2.0</td> 
   <td><p>interface TimeRange<br /> {<br /> readonly attribut unsigned long begin;<br /> readonly attribut unsigned long end;<br /> attribut readonly non signé longue durée;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### QOSProvider {#qosprovider}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td>Aucune modification pour la version 2.0</td> 
   <td><p>interface QOSProvider<br /> {<br /> void AttacheMediaPlayer(MediaPlayer player);<br /> void detachMediaPlayer();<br /> attribut <br /> readonly DeviceInformation deviceInformation ;<br /> readonly attribut PlaybackInformation playbackInformation;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DeviceInformation {#deviceinformation}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface DeviceInformation<br /> {<br /> readonly attribut DomString os;<br /> <br /><br /> <br /> readonly attribut DomString id;<br /> readonly, attribut int densitéDPI;<br /> readonly attribut int heightPixels;<br /> readonly attribut int widthPixels;<br /> readonly, attribut booléen searchToKeyFrame;<br /> };</p> </td> 
   <td><p>interface DeviceInformation<br /> {<br /> readonly attribut DomString os;<br /> readonly attribut int sdk;<br /> readonly, attribut modèle DomString;<br /> readonly, attribut fabricant de DomString;<br /> readonly attribut DomString id;<br /> readonly, attribut int densitéDPI;<br /> readonly attribut int heightPixels;<br /> readonly attribut int widthPixels;<br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### LoadInfo {#loadinfo}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td>Aucune modification pour la version 2.0</td> 
   <td><p>interface LoadInfo<br /> {<br /> readonly attribut DomString url;<br /> readonly attribut int size;<br /> readonly, attribut downloadDuration ;<br /> readonly attribut int periodIndex;<br /> readonly, attribut  mediaDuration;<br /> readonly attribut short TRACK_TYPE_FRAGMENT;<br /> readonly attribut short TRACK_TYPE_TRACK;<br /> readonly attribut short TRACK_TYPE_MANIFEST;<br /> readonly attribut short type;<br /> readonly attribut DomString trackName;<br /> readonly attribut DomString trackType;<br /> readonly attribut int trackIndex;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### View {#view}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td>Aucune modification pour la version 2.0</td> 
   <td><p><br /> d'interface {<br /> readonly attribut unsigned short x;<br /> readonly attribut unsigned short y;<br /> readonly attribut unsigned short width;<br /> readonly attribut unsigned short height;<br /> void setSize (largeur courte non signée, hauteur courte non signée); <br /><br /> void setPos(unsigned short x, unsigned short y);<br /> }</p> </td> 
  </tr> 
 </tbody> 
</table>

### PlaybackInformation {#playbackinformation}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface PlaybackInformation<br /> {<br /> readonly attribut timeToFirstByteToFirstByte;<br /> readonly, attribut timeToLoad<br /> readonly attribut  timeToStart;<br /> readonly, attribut timeToFail  timeToFail;<br /> readonly attribut int totalSecondsPlayed;<br /> readonly attribut int totalSecondsSpent;<br /> readonly, attribut  frameRate;<br /> readonly attribut int droppedFrameCount;<br /> readonly attribut int perçeeBandwidth;<br /> readonly attribut int bitrate;<br /> readonly, attribut  bufferTime du;<br /> readonly attribut int bufferLength;<br /> readonly attribut int emptyBufferCount;<br /> readonly, attribut  bufferingTime;<br /> };</p> </td> 
   <td><p>interface PlaybackInformation<br /> {<br /> readonly attribut timeToFirstByteToFirstByte;<br /> readonly, attribut timeToLoad<br /> readonly attribut  timeToStart;<br /> readonly, attribut timeToFail  timeToFail;<br /> readonly attribut int totalSecondsPlayed;<br /> readonly attribut int totalSecondsSpent;<br /> readonly, attribut  frameRate;<br /> readonly attribut int droppedFrameCount;<br /> attribut <br /> readonly int bitrate;<br /> readonly, attribut  bufferTime du;<br /> readonly attribut int bufferLength;<br /> readonly attribut int emptyBufferCount;<br /> readonly, attribut  bufferingTime;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

## Ressources utiles {#helpful-resources}

* Reportez-vous à la documentation d’aide complète sur la page de formation et d’assistance [d’](https://helpx.adobe.com/support/primetime.html) Adobe Primetime.
