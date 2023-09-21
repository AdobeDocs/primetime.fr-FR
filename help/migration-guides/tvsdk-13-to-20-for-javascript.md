---
title: Conversion TVSDK - 1.3 à 2.0 pour JavaScript
description: De nombreuses signatures de méthode et noms d’éléments d’API ont été modifiés pour la version 2.0. Consultez ces tableaux pour afficher tous les détails des modifications de l’API.
contentOwner: asgupta
products: SG_PRIMETIME
topic-tags: migration
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '5034'
ht-degree: 0%

---

# Conversion TVSDK - 1.3 à 2.0 pour JavaScript {#tvsdk-conversion-to-for-javascript}

De nombreuses signatures de méthode et noms d’éléments d’API ont été modifiés pour la version 2.0. Consultez ces tableaux pour afficher tous les détails des modifications de l’API.

## Mise en oeuvre des fonctions de rappel dans JavaScript {#implement-callback-functions-in-javascript}

Les commentaires dans la documentation de la méthode suggèrent la signature des rappels que vous devez implémenter.

Pour JavaScript, la syntaxe de l’API est basée sur l’ID web. Pour une interface TVSDK, les noms des méthodes sont appelés *methodName*(). Pour que les méthodes soient implémentées par votre application, un attribut read/write appelé *methodName* CallbackFunc est ajouté à l’interface et votre application doit la définir pour qu’elle pointe vers une fonction qui implémente la méthode . Par exemple :

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

## Modifications des éléments de l’API de workflow publicitaire pour la version 2.0 {#advertising-workflow-api-element-changes-for}

Ces tableaux comparent les éléments de l’API de workflow publicitaire pour le TVSDK JavaScript entre les versions 1.3 et 2.0.

Tableaux dans cette rubrique :

* TimedMetadata
* AdSignalingMode
* AdvertisingMetadata
* CustomRangeMetadata
* ReplaceTimeRange
* Placement
* Opportunité
* Réservation
* Chronologie / Elément de la chronologie / Marqueur de chronologie
* AdBreak
* Ad / AdAsset / AdClick / AdList / AdAssetList / AdBannerAsset
* AdBreakTimelineItem / AdTimelineItem
* AdBreakPolicy/AdBreakWatchedPolicy/AdPolicy/AdPolicyMode/AdPolicyInfo/AdPolicySelector
* TimelineOperation
* AdBreakPlacement
* AuditudeSettings

### TimedMetadata {#timedmetadata}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p> <strong>TimedMetadata</strong>: interface TimedMetadata {<br /> const unsigned short METADATA_TYPE_TAG = 0 ; <br /> const unsigned short METADATA_TYPE_ID3 = 1 ; <br /> attribut readonly de type court non signé ; <br /> durée d’attribut en lecture seule ;<br /> attribut readonly DomString id;<br /> attribut readonly DomString name;<br /> content DomString en lecture seule ; <br /> métadonnées d’objet en lecture seule ;<br /> }; </p> </td> 
   <td><p>interface TimedMetadata {<br /> const unsigned short METADATA_TYPE_TAG = 0 ;<br /> const unsigned short METADATA_TYPE_ID3 = 1 ;<br /> readonly attribut unsigned short metadataType;<br /> durée d’attribut en lecture seule ;<br /> identifiant long de l’attribut readonly ;<br /> attribut readonly DomString name;<br /> <br /> métadonnées d’objet en lecture seule ;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>TimedMetadataList</strong>: (aucune modification pour 2.0)</td> 
   <td><p>interface TimedMetadataList {<br /> attribut readonly non signé long length ;<br /> getter TimedMetadata (index long non signé);<br /> };</p> </td> 
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
   <td><p>Interface AdSignalingMode { <br /> conf unsigned short MODE_DEFAULT, <br /> conf non signé MODE_MANIFEST_CUES , <br /> Contenir MODE_SERVER_MAP courte non signée , <br /> Contenir MODE_CUSTOM_RANGES courts non signés <br /> };</p> </td> 
   <td>Cette opération remplace la clé MetadataKeys::MANIFEST_CUES .</td> 
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
   <td><p>Interface AdvertisingMetadata { <br /> attribut AdSignalingMode ; <br /> attribut AdBreakWatchedPolicy adBreakAsWatched; <br /> attribute boolean livePreroll; <br /> attribut booléen delayAdLoading ; <br /> };</p> </td> 
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
   <td><p>Interface CustomRangeMetadata { <br /> const short TYPE_MARK_RANGE non signé; <br /> contez short TYPE_DELETE_RANGE non signé ; <br /> contez short TYPE_REPLACE_RANGE non signé ; <br /> attribut non signé court type; <br /> attribut boolean adaptSeekPosition; <br /> attribut TimeRangeList timeRangeList; <br /> };</p> </td> 
   <td>(Nouveautés de la version 2.0)</td> 
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
   <td><p>interface ReplaceTimeRange { <br /> attribut non signé long start; <br /> attribut readonly non signé long end; <br /> attribut non signé de longue durée ; <br /> attribut unsigned long replaceDuration; <br /> };</p> </td> 
   <td>(Nouveautés de la version 2.0)</td> 
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
   <td><p>Interface Placement { <br /> const non signé short TYPE_MID_ROLL; <br /> const non signé short TYPE_PRE_ROLL; <br /> const non signé short TYPE_POST_ROLL; <br /> concorde short TYPE_SERVER_MAP non signé ; <br /> contez short TYPE_CUSTOM_RANGE non signé ;<br /> attribut readonly de type court non signé ; <br /> durée d’attribut en lecture seule ; <br /> durée d’attribut en lecture seule ; <br /> concorde MODE_DEFAULT court non signé ; <br /> conte non signé MODE_INSERT; <br /> concorde MODE_REPLACE court non signé ; <br /> const non signé MODE_DELETE; <br /> conf non signé MODE_MARK ; <br /> concorde MODE_FREE_REPLACE courte non signée ; <br /> l’attribut readonly non signé short mode ; <br /> attribut readonly Période ; <br /> };</p> </td> 
   <td>(Nouveautés de la version 2.0)</td> 
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
   <td><p>interface Opportunity { <br /> attribut readonly DomString id; <br /> placement en lecture seule de l’attribut Placement ; <br /> Paramètres d’objet d’attribut readonly ; <br /> attribut readonly Object customParameters ; <br /> }; </p> </td> 
   <td>(Nouveautés de la version 2.0)</td> 
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
   <td><p>interface Réservation { <br /> attribut readonly Période ; <br /> Readonly attribut long hold; <br /> }; </p> </td> 
   <td> (Nouveautés de la version 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### Chronologie / Elément de la chronologie / Marqueur de chronologie {#timeline-timelineitem-timelinemarker}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p><strong>Chronologie</strong>: chronologie de l’interface <br /> { attribut en lecture seule TimelineMarkerList timelineMarkers; <br /> attribut readonly TimelineItemList timelineItems ; <br /> double convertToLocalTime( double heure); <br /> double convertToVirtualTime( double heure); <br /> };</p> </td> 
   <td><p>Interface Timeline {<br /> attribut readonly TimelineMarkerList timelineMarkers ;<br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p> <strong>TimelineItem</strong>: interface TimelineItem :<br /> TimelineMarker {<br /> identifiant long de l’attribut readonly ; <br /> attribut readonly TimeRange virtualRange; <br /> attribut readonly TimeRange localRange; <br /> L’attribut readonly boolean surveillé ; <br /> readonly attribut booléen temporaire ; <br /> }; </p> </td> 
   <td>(Nouveautés de la version 2.0)</td> 
  </tr> 
  <tr> 
   <td><strong>TimelineMarker</strong>: (aucune modification pour 2.0)</td> 
   <td><p>interface TimelineMarker {<br /> le temps double de l’attribut readonly ;<br /> double durée d’attribut readonly ;<br /> };</p> </td> 
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
   <td><p>interface AdBreak {<br /> <br /> <br /> <br /> double durée d’attribut readonly ;<br /> attribut readonly publicités AdList ;<br /> <br /> <br /> attribut readonly AdInsertionType insertType;<br /> }; </p> </td> 
   <td><p>interface AdBreak {<br /> le temps double de l’attribut readonly ;<br /> attribut readonly double replaceDuration;<br /> <br /> double durée d’attribut readonly ;<br /> attribut readonly AdList adList ;<br /> <br /> données DomString en lecture seule ;<br /> <br /> }; </p> </td> 
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
   <td><p> <strong>Publicité</strong>: interface Ad {<br /> attribut readonly AdAsset primaryAsset ;<br /> attribut readonly AdAssetList compagionAssets;<br /> <br /> double durée d’attribut readonly ;<br /> attribut readonly DomString id;<br /> const non signé short ADTYPE_LINEAR = 0 ;<br /> const short ADTYPE_NONLINEAR non signé = 1 ;<br /> <br /> readonly attribut non signé short adType;<br /> attribut readonly AdInsertionType adInsertionType; <br /> <br /> attribut readonly boolean cliquable ; <br /> attribut readonly boolean isCustomAdMarker;<br /> }; </p> </td> 
   <td><p>interface Ad {<br /> attribut readonly AdAsset primaryAsset ;<br /> attribut readonly AdAssetList compagionAssets;<br /> <br /> double durée d’attribut readonly ;<br /> attribut readonly DomString id;<br /> const non signé short ADTYPE_LINEAR = 0 ;<br /> const short ADTYPE_NONLINEAR non signé = 1 ;<br /> <br /> attribut readonly de type court non signé ;<br /> attribut readonly AdInsertionType insertType; <br /> readonly attribute Object tracker :<br /> <br /> <br /> }; </p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdAsset</strong>: (aucune modification pour 2.0)</td> 
   <td><p>interface AdAsset {<br /> attribut readonly DomString id;<br /> double durée d’attribut readonly ;<br /> ressource MediaResource en lecture seule ;<br /> attribut readonly AdClick adClick ;<br /> métadonnées d’objet en lecture seule ;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdClick</strong>: (aucune modification pour 2.0)</td> 
   <td><p>interface AdClick {<br /> attribut readonly DomString id;<br /> attribut readonly titre de DomString ;<br /> L’attribut readonly DomString url ;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdList</strong>: (aucune modification pour 2.0)</td> 
   <td><p>interface AdList {<br /> attribut readonly non signé long length ;<br /> getter Ad (index long non signé);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdAssetList</strong>: (aucune modification pour 2.0)</td> 
   <td><p>interface AdAssetList {<br /> attribut readonly non signé long length ;<br /> getter AdAsset (index long non signé);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p><strong>AdBannerAsset</strong>: interface AdBannerAsset : AdAsset<br /> {<br /> readonly attribute int width;<br /> readonly attribute int height;<br /> attribut readonly DomString staticUrl ;<br /> attribut readonly DomString height;<br /> attribut readonly DomString width;<br /> };</p> </td> 
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
   <td><p> <strong>AdBreakTimelineItem</strong>: interface AdBreakTimelineItem : TimelineItem { <br /> attribut readonly AdBreak adBreak; <br /> attribut en lecture seule des éléments AdTimelineItemList ; <br /> }; </p> </td> 
   <td> (Nouveautés de la version 2.0)</td> 
  </tr> 
  <tr> 
   <td><p><strong>AdTimelineItem</strong>: interface AdTimelineItem : TimelineItem { <br /> attribut readonly AdBreak adBreak; <br /> attribut readonly publicité ; <br /> }; </p> </td> 
   <td> (Nouveautés de la version 2.0)</td> 
  </tr> 
  <tr> 
   <td><p><strong>AdBreakTimelineItemList</strong>: interface AdBreakTimelineItemList { <br /> attribut readonly non signé long length ; <br /> getter AdBreakTimelineItem (index ng non signé); <br /> };</p> </td> 
   <td> (Nouveautés de la version 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### AdBreakPolicy/AdBreakWatchedPolicy/AdPolicy/AdPolicyMode/AdPolicyInfo/AdPolicySelector {#adbreakpolicy-adbreakwatchedpolicy-adpolicy-adpolicymode-adpolicyinfo-adpolicyselector}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>interface AdBreakPolicy {<br /> attribut readonly short AD_BREAK_POLICY_SKIP;<br /> attribut readonly short AD_BREAK_POLICY_PLAY;<br /> readonly attribut short AD_BREAK_POLICY_REMOVE;<br /> attribut readonly short AD_BREAK_POLICY_REMOVE_AFTER_PLAY;<br /> };</p> </td> 
   <td><p> interface AdPolicyConstants {<br /> attribut readonly short AD_BREAK_POLICY_SKIP;<br /> attribut readonly short AD_BREAK_POLICY_PLAY;<br /> readonly attribut short AD_BREAK_POLICY_REMOVE;<br /> attribut readonly court AD_BREAK_POLICY_REMOVE_AFTER_PLAY;}<br /> ..</p> </td> 
  </tr> 
  <tr> 
   <td><p> interface AdBreakWatchedPolicy {<br /> readonly attribut short AD_BREAK_AS_WATCHED_ON_BEGIN ;<br /> attribut readonly short AD_BREAK_AS_WATCHED_ON_END;<br /> attribut readonly short AD_BREAK_AS_WATCHED_NEVER;<br /> }; </p> </td> 
   <td><p> ..<br /> readonly attribut short AD_BREAK_AS_WATCHED_ON_BEGIN ;<br /> attribut readonly short AD_BREAK_AS_WATCHED_ON_END;<br /> attribut readonly short AD_BREAK_AS_WATCHED_NEVER;<br /> ..</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicy {<br /> readonly attribut short AD_POLICY_PLAY;<br /> attribut readonly short AD_POLICY_PLAY_FROM_AD_BEGIN ;<br /> attribut readonly short AD_POLICY_PLAY_FROM_AD_BREAK_BEGIN; attribut readonly short AD_POLICY_SKIP_TO_NEXT_AD_IN_BREAK;<br /> <br /> attribut readonly short AD_POLICY_SKIP_AD_BREAK;<br /> };</p> </td> 
   <td><p> .. <br /> readonly attribut short AD_POLICY_PLAY;<br /> attribut readonly short AD_POLICY_PLAY_FROM_AD_BEGIN ;<br /> attribut readonly short AD_POLICY_PLAY_FROM_AD_BREAK_BEGIN ;<br /> attribut readonly short AD_POLICY_SKIP_TO_NEXT_AD_IN_BREAK;<br /> attribut readonly short AD_POLICY_SKIP_AD_BREAK;<br /> ..</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicyMode {<br /> attribut readonly short AD_POLICY_MODE_PLAY;<br /> attribut readonly short AD_POLICY_MODE_SEEK;<br /> attribut readonly short AD_POLICY_MODE_TRICKPLAY;<br /> };</p> </td> 
   <td><p> ..<br /> {readonly attribute short AD_POLICY_MODE_PLAY;<br /> attribut readonly short AD_POLICY_MODE_SEEK;<br /> attribut readonly short AD_POLICY_MODE_TRICKPLAY;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicyInfo {<br /> attribut readonly AdBreakTimelineItemList <br /> adBreakTimelineItems;<br /> attribut readonly AdTimelineItem adTimelineItem;<br /> attribut readonly double currentTime ;<br /> attribut readonly double searchToTime;<br /> taux de double attribut readonly ;<br /> readonly attribute short mode; //AdPolicyMode<br /> };</p> </td> 
   <td><p>interface AdPolicyInfo {<br /> attribut readonly AdBreakPlacementList <br /> adBreakPlacements;<br /> attribut readonly publicité ;<br /> attribut readonly double currentTime ;<br /> attribut readonly double searchToTime;<br /> taux de double attribut readonly ;<br /> readonly attribute short mode; //AdPolicyMode<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicySelector {<br /> /**<br /> * AdbreakPolicy selectPolicyForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectPolicyForAdBreakCallbackFunc;<br /> /**<br /> * AdBreakTimelineItemList selectAdBreaksToPlay(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectAdBreaksToPlayCallbackFunc;<br /> /**<br /> * AdPolicy selectPolicyForSeekIntoAd(AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectPolicyForSeekInAdCallbackFunc; <br /> /**<br /> * AdBreakWatchedPolicy selectWatchedPolicyForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectWatchedPolicyForAdBreakCallbackFunc;<br /> };</p> </td> 
   <td><p>interface AdPolicySelector {<br /> /**<br /> * AdbreakPolicy selectPolicyForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectPolicyForAdBreakFuncCallback;<br /> /**<br /> * AdBreakPlacementList selectAdBreaksToPlay(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectAdBreaksToPlayCallback;<br /> /**<br /> * AdPolicy selectPolicyForSeekIntoAd(AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectPolicyForSeekInAdCallback; <br /> /**<br /> * AdBreakAsWatched selectWatchedPolicyForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectWatchedPolicyForAdBreakCallback;<br /> };</p> </td> 
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
   <td><p>interface TimelineOperation { <br /> attribut readonly Placement ; <br /> };</p> </td> 
   <td> (Nouveautés de la version 2.0)</td> 
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
   <td><p>interface AdBreakPlacement : TimelineOperation {<br /> attribut readonly AdBreak adBreak;<br /> attribut readonly Placement placement ; // From TimelineOperation<br /> le temps double de l’attribut readonly ;<br /> double durée d’attribut readonly ;<br /> };</p> </td> 
   <td><p>interface AdBreakPlacement {<br /> attribut readonly AdBreak adBreak;<br /> placement en lecture seule de l’attribut Placement ;<br /> le temps double de l’attribut readonly ;<br /> double durée d’attribut readonly ;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### AuditudeSettings {#auditudesettings}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>interface AuditudeSettings : AdvertisingMetadata { <br /> attribute DomString zoneId; <br /> attribut DomString mediaId; <br /> attribut DomString defaultMediaId ; <br /> attribute DomString domain ; <br /> attribute Object targetingInfo ; <br /> attribute Object customParameters ; <br /> attribut booléen creativePackingEnabled ;<br /> attribut Booléen showStaticBanners ;<br /> };</p> </td> 
   <td>La fonctionnalité a été fournie par la clé MetadataKeys::AUDITUDE_METADATA_KEY .</td> 
  </tr> 
 </tbody> 
</table>

## Modifications des éléments de l’API de personnalisation pour la version 2.0 {#customization-api-element-changes-for}

Ces tableaux comparent les éléments d’API de personnalisation pour le TVSDK JavaScript entre les versions 1.3 et 2.0.

Tableaux dans cette rubrique :

* MediaPlayerItemConfig
* ContentFactory
* NetworkConfiguration

### MediaPlayerItemConfig {#mediaplayeritemconfig}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayerItemConfig {<br /> attribut ContentFactory adFactory ;<br /> attribute StringList subscribeTags;<br /> <br /> attribute StringList adTags;<br /> <br /> <br /> attribut AdSignalingMode adSignalingMode;<br /> attribut CustomRangeMetadata customRangeMetadata;<br /> attribute NetworkConfiguration networkConfiguration;<br /> attribute AdvertisingMetadata advertisingMetadata;<br /> attribut booléen useHardwareDecoder ;<br /> };</p> </td> 
   <td><p>interface MediaPlayerConfig {<br /> <br /> <br /> <br /> attribute StringList adTags;<br /> attribute StringList subscribedTags;<br /> attribut MediaPlayerClientFactory clientFactory ;<br /> <br /> <br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### ContentFactory {#contentfactory}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>interface ContentFactory {<br /> /*<br /> * AdPolicySelector retrieveAdPolicySelector(<br /> * MediaPlayerItem);<br /> */<br /> attribute Object retrieveAdPolicySelectorCallbackFunc;<br /> };</p> </td> 
   <td><p>interface MediaPlayerClientFactory {<br /> /*<br /> * AdPolicySelector retrieveAdPolicySelector(<br /> * MediaPlayerItem);<br /> */<br /> attribute Object retrieveAdPolicySelectorFunc;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### NetworkConfiguration {#networkconfiguration}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>interface NetworkConfiguration<br /> {<br /> attribute boolean forceNativeNetworking;<br /> attribut booléen useRedirectUrl ;<br /> attribute Object cookieHeader;<br /> attribut booléen readSetCookieHeader;<br /> attribute int masterUpdateInterval; <br /> attribut booléen useCookieHeaderForAllRequests;<br /> attribute int readLimit;<br /> };</p> </td> 
   <td>Dans la version 1.3, une partie de cette fonctionnalité a été fournie par MetadataKeys.</td> 
  </tr> 
 </tbody> 
</table>

## Modifications des éléments de l’API DRM pour la version 2.0 {#drm-api-element-changes-for}

Ces tableaux comparent les éléments d’API DRM pour le TVSDK JavaScript entre les versions 1.3 et 2.0.

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
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td>L’application doit appeler AdobePSDK.initiateDRMWorkflow pour lancer le processus DRM. Sans cet appel, les vidéos DRM ne seront pas lues.<p>interface AdobePSDK<br /> {<br /> void initiateDRMWorkFlow(<br /> DomString appStoratePath, <br /> DomString publisherId, <br /> DomString appId, <br /> DomString appVersion, <br /> privacyModeOn booléen);<br /> };</p> </td> 
   <td>L’initialisation a été effectuée en interne et aucun appel explicite n’était requis.</td> 
  </tr> 
 </tbody> 
</table>

### DRMAcquireLicenseSettings/DRMAuthenticationMethod {#drmacquirelicensesettings-drmauthenticationmethod}

| API 2.0 | API 1.3 |
|--- |--- |
| **DRMAcquireLicenseSettings** |  |
| Aucune modification pour la version 2.0. | enum DRMAcquireLicenseSettings <br>{<br> const unsigned int FORCE_REFRESH = 0;<br> const non signé int LOCAL_ONLY = 1;<br> conf unsigned int ALLOW_SERVER = 2;<br> }; |
| **DRMAuthenticationMethod** |  |
| Aucune modification pour la version 2.0. | enum DRMAuthenticationMethod <br>{<br> conf unsigned int UNKNOWN = 0;<br> const non signé int ANONYMOUS = 1;<br> conf unsigned int USERNAME_AND_PASSWORD = 2;<br> } |

### DRMMetadata {#drmmetadata}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td>Aucune modification pour la version 2.0.</td> 
   <td><p>interface DRMMetadata<br /> {<br /> attribut readonly DomString serverUrl;<br /> attribut readonly DomString licenseId;<br /> les stratégies DRMPolicyArray d’attribut readonly ; <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMPlaybackTimeWindow {#drmplaybacktimewindow}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>interface DRMPlaybackTimeWindow {<br /> attribut readonly int playbackPeriodInSeconds;<br /> readonly attribut long playbackStartDate;<br /> attribut readonly long playbackEndDate;<br /> };</p> </td> 
   <td><p>interface DRMPlaybackTimeWindow {<br /> attribut readonly int periodInSeconds;<br /> readonly attribute int startDate;<br /> readonly attribute int endDate;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMLicense {#drmlicense}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td>Aucune modification pour la version 2.0.</td> 
   <td><p>interface DRMLicense {<br /> attribut readonly Uint8Array bytes;<br /> attribut readonly Date licenseStartDate;<br /> attribut readonly Date licenseEndDate;<br /> attribut readonly Date offlineStorageStartDate;<br /> attribut readonly Date offlineStorageEndDate; <br /> attribut readonly DomString serverUrl;<br /> identifiant de licence DomString en lecture seule ;<br /> attribut readonly DomString policyID;<br /> attribut readonly DRMPlaybackTimeWindow playbackTimeWindow;<br /> attribut readonly Object customProperties;<br /> }; </p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMLicenseDomain {#drmlicensedomain}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>interface DRMLicenseDomain {<br /> attribut readonly DomString authenticationDomain;<br /> attribut readonly DRMAuthenticationMethod authenticationMethod; <br /> attribut readonly DomString serverUrl;<br /> };</p> </td> 
   <td><p>interface DRMLicenseDomain {<br /> attribut readonly DomString authDomain;<br /> attribut readonly DRMAuthenticationMethod authMethod; <br /> attribut readonly DomString serverURL;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMPolicy {#drmpolicy}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>interface DRMPolicy<br /> {<br /> attribut readonly DomString authenticationDomain;<br /> attribut readonly DRMAuthenticationMethod authenticationMethod;<br /> <br /> attribut readonly DomString displayName;<br /> attribut readonly DRMLicenseDomain licenseDomain;<br /> };</p> </td> 
   <td><p>interface DRMPolicy<br /> {<br /> attribut readonly DomString authDomain;<br /> attribut readonly DRMAuthenticationMethod authMethod;<br /> attribut readonly DomString dispName;<br /> attribut readonly DRMLicenseDomain licenseDomain;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMManager {#drmmanager}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>interface DRMManager : EventTarget {<br /> void acquireLicense(DRMMetadata metadata), <br /> paramètre DRMAcquireLicenseSettings, <br /> DRMAquireLicenseListener);<br /> void acquirePreviewLicense(DRMMetadata metadata), <br /> DRMAquireLicenseListener);<br /> void authenticate (métadonnées DRMMetadata), <br /> URL DomString,<br /> DomString &amp;authenticationDomain, <br /> Utilisateur DomString, <br /> Mot de passe DomString, <br /> DRMAuthenticateListener);<br /> <br /> DRMMetadata createMetadataFromBytes(<br /> Uint8Array (tableau, écouteur DRMErrorListener);<br /> void initialize(DRMOperationCompleteListener);<br /> attribut long maxOperationTime;<br /> <br /> void joinLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> boolean forceRefresh, <br /> DRMOperationCompleteListener);<br /> void leaveLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> DRMOperationCompleteListener);<br /> <br /> void resetDRM(DRMOperationCompleteListener);<br /> void returnLicense(DomString serverURL, <br /> DomString licenseID, <br /> DomString policyID, <br /> boolean commitImmédiatement,<br /> DRMReturnLicenseListener);<br /> void setAuthenticationToken(<br /> Métadonnées DRMM, <br /> DomString authenticationDomain, <br /> Jeton Uint8Array, <br /> DRMOperationCompleteListener);<br /> void storeLicenseBytes(Uint8Array licenseBytes, <br /> DRMOperationCompleteListener);<br /> };</p> </td> 
   <td><p>interface DRMManager : EventTarget {<br /> void acquireLicense(DRMMetadata metadata), <br /> paramètre DRMAcquireLicenseSettings, <br /> EventContext (eventContext);<br /> void acquirePreviewLicense(DRMMetadata metadata), <br /> EventContext (eventContext);<br /> void authenticate (métadonnées DRMMetadata), <br /> URL DomString,<br /> DomString &amp;authenticationDomain, <br /> Utilisateur DomString, <br /> Mot de passe DomString, <br /> EventContext (eventContext);<br /> <br /> DRMMetadata createMetadataFromBytes(<br /> Tableau Uint8Array, EventContext (eventContext);<br /> void initialize(EventContext eventContext);<br /> attribut long maxOperationTime;<br /> <br /> void joinLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> boolean forceRefresh, <br /> EventContext (eventContext);<br /> void leaveLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> EventContext (eventContext);<br /> <br /> void resetDRM(EventContext eventContext);<br /> void returnLicense(DomString serverURL, <br /> DomString licenseID,<br /> DomString policyID, <br /> boolean commitImmédiatement,<br /> EventContext (eventContext);<br /> void setAuthenticationToken(<br /> Métadonnées DRMM, <br /> DomString authenticationDomain, <br /> Jeton Uint8Array, <br /> EventContext (eventContext);<br /> void storeLicenseBytes(Uint8Array licenseBytes, <br /> EventContext (eventContext);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>classe DRMErrorListener : <br /> public psdkutils::PSDKInterfaceWithUserData {<br /> public :<br /> void virtuel onDRMError(uint32_t majeur, <br /> uint32_t mineur, <br /> const psdkutils: PSDKString&amp; errorString, <br /> const psdkutils::PSDKString&amp; errorServerUrl) = 0;<br /> <br /> protected :<br /> ~DRMErrorListener() {}<br /> }</p> </td> 
   <td>Événement / Interface / Description 
    <ul> 
     <li>kEventDRMOperationError<p>/ DRMOperationErrorEvent</p> <p>Lorsqu’une erreur se produit lors de l’une des méthodes asynchrones de DRMManger.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>classe DRMOperationCompleteListener : <br /> public DRMErrorListener {<br /> public :<br /> void virtuel onDRMOperationComplete() = 0;<br /> <br /> protected :<br /> ~DRMOperationCompleteListener() {}<br /> };</p> </td> 
   <td>Événement / Interface / Description 
    <ul> 
     <li>kEventDRMInitializationComplete<p>/ PSDKEvent</p> <p>Une fois l’initialisation de DRM terminée.</p> </li> 
     <li>kEventDRMJoinLicenseDomainComplete<p>/ PSDKEvent</p> <p>Lorsque l’action joinLicenseDomain() se termine correctement.</p> </li> 
     <li>kEventDRMLeaveLicenseDomainComplete<p>/ PSDKEvent</p> <p>Lorsque l’action leaveLicenseDomain() se termine correctement.</p> </li> 
     <li>kEventDRMResetCompletePSDKEevent<p>/ PSDKEvent</p> <p>Une fois l’action resetDRM() terminée,</p> </li> 
     <li>kEventDRMAuthenticationTokenSet<p>/ PSDKEvent</p> <p>Lorsque l’action setAuthenticationTokenSet() se termine correctement.</p> </li> 
     <li>kEventDRMLicenseStored<p>/ PSDKEvent</p> <p>Lorsque l’action storeLicenseBytes() se termine correctement.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>classe DRMAuthenticateListener : <br /> public DRMErrorListener {<br /> public :<br /> void virtuel onAuthenticationComplete(<br /> psdkutils::PSDKImmutableByteArray* <br /> authenticationToken) = 0;<br /> <br /> protected :<br /> ~DRMAuthenticateListener() {}<br /> }</p> </td> 
   <td>Événement / Interface / Description 
    <ul> 
     <li>kEventDRMAuthenticationComplete<p>/ DRMAuthenticationCompleteEvent</p> <p>Lorsque l’appel de méthode DRMManager::authenticate est réussi.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>classe DRMAquireLicenseListener: <br /> public DRMErrorListener {<br /> public :<br /> void virtuel onLicenseAcquired(const DRMLicense*) = 0;<br /> <br /> protected :<br /> ~DRMAquireLicenseListener() {}<br /> };</p> </td> 
   <td>Événement / Interface / Description 
    <ul> 
     <li>kEventDRMPreviewLicenseAcquired<p>/ DRMLicenseAcquiredEvent</p> <p>Lorsque l’appel de la méthode DRMManager::acquirePreviewLicense est réussi.</p> </li> 
     <li>kEventDRMLicenseAcquired<p>/ DRMLicenseAcquiredEvent</p> <p>Lorsque l’appel de la méthode DRMManager::acquireLicense est réussi.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>Classe DRMReturnLicenseListener: <br /> public DRMErrorListener {<br /> public :<br /> void virtuel onLicenseReturnComplete(uint32_t numReturned ) = 0;<br /> <br /> protected :<br /> ~DRMReturnLicenseListener() {}<br /> };</p> </td> 
   <td>Événement / Interface / Description 
    <ul> 
     <li>kEventDRMLicenseReturnComplete<p>/ DRMLicenseReturnCompleteEvent</p> <p>Lorsque l’appel de la méthode DRMManager::returnLicense est réussi.</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Modifications des éléments de l’API de lecture générique pour la version 2.0 {#generic-playback-api-element-changes-for}

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
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaResource {<br /> attribut URL DomString ; <br /> attribut non signé court type;<br /> métadonnées d’objet d’attribut ;<br /> const non signé short TYPE_HLS;<br /> const non signé short TYPE_HDS;<br /> const non signé short TYPE_DASH;<br /> const non signé short TYPE_CUSTOM;<br /> const unsigned short TYPE_UNKNOWN;<br /> };</p> </td> 
   <td><p>interface MediaResource {<br /> attribut URL DomString ;<br /> attribut type DomString ;<br /> métadonnées d’objet d’attribut ;<br /> <br /> <br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### MediaPlayer {#mediaplayer}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>Interface MediaPlayer : EventTarget<br /> {<br /> void prepareToPlay( double position);<br /> void play();<br /> void pause();<br /> void search( double position);<br /> void searchToLocal( double position);<br /> void reset();<br /> void release();<br /> void replaceCurrentItem(MediaPlayerItem);<br /> void replaceCurrentResource(MediaResource ressource, <br /> MediaPlayerItemConfig); <br /> void suspense();<br /> void restore();<br /> void notifyClick();<br /> <br /> attribut readonly TimeRange playbackRange;<br /> attribut readonly TimeRange seekableRange;<br /> attribut readonly double currentTime ;<br /> attribut readonly double localTime ;<br /> attribut readonly TimeRange bufferedRange;<br /> attribut readonly DRMManager drmManager ;<br /> attribut readonly MediaPlayerItem currentItem;<br /> <br /> // PlayerStatus<br /> <br /> <br /> contez le court PLAYER_STATUS_INITIALIZED non signé ;<br /> contez le court PLAYER_STATUS_PREPARING non signé.<br /> contez le court PLAYER_STATUS_PREPARED non signé ;<br /> contez LECTEUR court non signé_STATUS_PLAYING;<br /> contez le court PLAYER_STATUS_PAUSED non signé ;<br /> contez le court PLAYER_STATUS_SEEKING non signé ;<br /> contez le court PLAYER_STATUS_COMPLETE non signé ;<br /> contez LECTEUR court non signé_STATUS_ERROR;<br /> contez le court PLAYER_STATUS_RELEASED non signé ;<br /> <br /> attribut readonly non signé court status;<br /> <br /> Attribuer un volume court non signé;<br /> attribute ABRControlParameters abrControlParameters;<br /> attribut BufferControlParameters bufferControlParameters;<br /> <br /> Consigner non signé court VISIBLE ; //Pour la visibilité CC<br /> Consigner non signé court INVISIBLE ; //Pour la visibilité CC<br /> attribut non signé ccVisibility court ;<br /> attribute TextFormat ccStyle;<br /> attribut readonly PlaybackMetrics playbackMetrics ;<br /> <br /> attribut double rate;<br /> attribut MediaPlayerView ;<br /> attribut readonly Chronologie de la chronologie de la chronologie ;<br /> attribut double currentTimeUpdateInterval; <br /> // ce paramètre ne sera pas pris en charge pour la version 2.0<br /> };</p> </td> 
   <td><p>Interface MediaPlayer : EventTarget<br /> {<br /> void prepareToPlay( position int);<br /> void play();<br /> void pause();<br /> void search( int position);<br /> void searchToLocalTime( position int);<br /> void reset();<br /> void release();<br /> void replaceCurrentItem(MediaResource source);<br /> <br /> <br /> <br /> <br /> <br /> <br /> attribut readonly TimeRange playbackRange;<br /> attribut readonly TimeRange seekableRange;<br /> attribut readonly double currentTime ;<br /> attribut readonly double localTime ;<br /> attribut readonly TimeRange bufferedRange;<br /> attribut readonly DRMManager drmManager ;<br /> attribut readonly MediaPlayerItem currentItem;<br /> <br /> // PlayerState<br /> contez le court PLAYER_STATE_IDLE non signé ;<br /> contez le court PLAYER_STATE_INITIALIZING non signé ;<br /> const non signé short PLAYER_STATE_INITIALIZED;<br /> contez le court PLAYER_STATE_PREPARING non signé.<br /> concorde short PLAYER_STATE_PREPARED ;<br /> contez le court PLAYER_STATE_PLAYING non signé ;<br /> const non signé short PLAYER_STATE_PAUSED;<br /> contez le court PLAYER_STATE_SEEKING non signé.<br /> contez le court PLAYER_STATE_COMPLETE non signé ;<br /> contez LECTEUR court non signé_STATE_ERROR;<br /> contez le court PLAYER_STATE_RELEASED non signé ;<br /> contez le court PLAYER_STATUS_SUSPENDED non signé ;<br /> attribut readonly non signé short state;<br /> <br /> Attribuer un volume court non signé;<br /> attribute ABRControlParameters abrControlParameters;<br /> attribut BufferControlParameters bufferControlParameters;<br /> <br /> readonly non signé short VISIBLE; //Pour la visibilité CC<br /> readonly non signé short INVISIBLE; //Pour la visibilité CC<br /> attribut non signé ccVisibility court ;<br /> attribute TextFormat ccStyle;<br /> attribut readonly PlaybackMetrics playbackMetrics ;<br /> attribut MediaPlayerConfig mediaPlayerConfig;<br /> attribut double rate;<br /> attribut MediaPlayerView ;<br /> attribut readonly Chronologie de la chronologie de la chronologie ;<br /> <br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayerStatus<br /> {<br /> // PlayerStatus<br /> contez LECTEUR court non signé_STATUS_IDLE;<br /> contez le court PLAYER_STATUS_INITIALIZING non signé ;<br /> contez le court PLAYER_STATUS_INITIALIZED non signé ;<br /> contez le court PLAYER_STATUS_PREPARING non signé.<br /> contez le court PLAYER_STATUS_PREPARED non signé ;<br /> contez LECTEUR court non signé_STATUS_PLAYING;<br /> contez le court PLAYER_STATUS_PAUSED non signé ;<br /> contez le court PLAYER_STATUS_SEEKING non signé ;<br /> contez le court PLAYER_STATUS_COMPLETE non signé ;<br /> contez LECTEUR court non signé_STATUS_ERROR;<br /> contez le court PLAYER_STATUS_RELEASED non signé ;<br /> contez le court PLAYER_STATUS_SUSPENDED non signé ;<br /> };</p> </td> 
   <td>(Nouveautés de la version 2.0)</td> 
  </tr> 
 </tbody> 
</table>

#### Événements pris en charge par MediaPlayer {#events-supported-by-mediaplayer}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 Nom de l’événement</th> 
   <th>Interface 2.0</th> 
   <th> </th> 
   <th>1.3 Nom de l’événement</th> 
   <th>Interface 1.3</th> 
  </tr> 
  <tr> 
   <td><p>(supprimé pour la version 2.0)</p> </td> 
   <td> </td> 
   <td> </td> 
   <td>préparé</td> 
   <td>Événement</td> 
  </tr> 
  <tr> 
   <td><p>itemUpdated</p> <p>Lorsqu’un élément du lecteur multimédia est mis à jour.</p> </td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>mis à jour</p> <p>Une fois que le lecteur multimédia a correctement mis à jour le média.</p> </td> 
   <td>Événement</td> 
  </tr> 
  <tr> 
   <td>timedMetadataAvailable</td> 
   <td>TimedMetadataEvent</td> 
   <td> </td> 
   <td>TtmedMetadata</td> 
   <td>TimedMetadataEvent</td> 
  </tr> 
  <tr> 
   <td>timelineUpdated</td> 
   <td>Événement</td> 
   <td> </td> 
   <td>ChronologieMise à jour</td> 
   <td>Événement</td> 
  </tr> 
  <tr> 
   <td>Supprimé dans la version 2.0</td> 
   <td> </td> 
   <td> </td> 
   <td>playStart</td> 
   <td>Événement</td> 
  </tr> 
  <tr> 
   <td>Supprimé pour la version 2.0</td> 
   <td> </td> 
   <td> </td> 
   <td>playComplete</td> 
   <td>Événement</td> 
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
   <td>size</td> 
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
   <td>progress</td> 
   <td>ProgressEvent</td> 
  </tr> 
  <tr> 
   <td>bufferingBegin</td> 
   <td>Événement</td> 
   <td> </td> 
   <td>buffer</td> 
   <td>Événement</td> 
  </tr> 
  <tr> 
   <td>bufferingEnd</td> 
   <td>Événement</td> 
   <td> </td> 
   <td>bufferComplete</td> 
   <td>Événement</td> 
  </tr> 
  <tr> 
   <td>searchBegin</td> 
   <td>SeekEvent</td> 
   <td> </td> 
   <td>searchStart</td> 
   <td>Événement</td> 
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
   <td>ReserveEvent</td> 
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
   <td>adClicked<br /> Lorsque l’utilisateur clique sur une publicité.</td> 
   <td>AdClickedEvent</td> 
   <td> </td> 
   <td><p>Nouveautés de la version 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>profileChanged<br /> Lorsque le profil de lecture change.</td> 
   <td>ProfileEvent</td> 
   <td> </td> 
   <td><p>Nouveautés de la version 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>searchPositionAdjusted<br /> Lorsque la position de la recherche s’ajuste en raison de règles internes ou externes.</td> 
   <td>SeekEvent</td> 
   <td> </td> 
   <td><p>Nouveautés de la version 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>audioUpdated<br /> Lorsqu’un élément du lecteur multimédia est mis à jour. Pour certains flux contenant des pistes audio détectables uniquement au moment de la lecture, cet événement est déclenché lorsque de nouvelles pistes audio sont disponibles.</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>Nouveautés de la version 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>captionsUpdated <br /> Lorsqu’un élément du lecteur multimédia est mis à jour. Pour les diffusions en direct/linéaires, le client doit actualiser régulièrement la ressource multimédia pour détecter le nouveau contenu disponible. Dans ce cas, certaines caractéristiques de média peuvent changer.</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>Nouveautés de la version 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>masterUpdated <br /> Lorsqu’un élément du lecteur multimédia est mis à jour. Pour les diffusions en direct/linéaires, le client doit actualiser régulièrement la ressource multimédia pour détecter le nouveau contenu disponible. Dans ce cas, certaines caractéristiques de média peuvent changer.</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>Nouveautés de la version 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>playbackRangeUpdated<br /> Lorsqu’un élément du lecteur multimédia est mis à jour. Pour les diffusions en direct/linéaires, le client doit actualiser régulièrement la ressource multimédia pour détecter le nouveau contenu disponible. Dans ce cas, certaines caractéristiques de média peuvent changer.</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>Nouveautés de la version 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>timedEvent<br /> Envoyé lorsque des événements minutés sont générés.</td> 
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
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>interface ABRControlParameters<br /> {<br /> Consigner ABR_POLICY_CONSERVATIVE = 0 ;<br /> Contenir ABR_POLICY_MODERATE = 1 ;<br /> Contenir ABR_POLICY_AGGRESIVE = 2 ;<br /> <br /> attribut unsigned short abrPolicy;<br /> attribut unsigned int initialBitRate;<br /> attribut non signé dans minBitRate;<br /> attribut unsigned int maxBitRate;<br /> concorde non signé DEFAULT_ABR_INITIAL_BITRATE ;<br /> concorde non signée DEFAULT_ABR_MIN_BITRATE;<br /> concorde non signée DEFAULT_ABR_MAX_BITRATE;<br /> const ABRPolicy DEFAULT_ABR_POLICY;<br /> };</p> </td> 
   <td><p>interface ABRControlParameters<br /> {<br /> Consigner ABR_POLICY_CONSERVATIVE = 0 ;<br /> Contenir ABR_POLICY_MODERATE = 1 ;<br /> Contenir ABR_POLICY_AGGRESIVE = 2 ;<br /> <br /> attribut unsigned short abrPolicy;<br /> attribut unsigned int initialBitRate;<br /> attribut non signé dans minBitRate;<br /> attribut unsigned int maxBitRate;<br /> <br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### BufferControlParameters {#buffercontrolparameters}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>Interface BufferControlParameters<br /> {<br /> attribut double initialBufferTime;<br /> attribut double playBufferTime;<br /> concorde double DEFAULT_INITIAL_BUFFER_TIME;<br /> concorde double DEFAULT_PLAY_BUFFER_TIME;<br /> };</p> </td> 
   <td><p>Interface BufferControlParameters<br /> {<br /> attribut double initialBufferTime;<br /> attribut double playBufferTime;<br /> <br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### TextFormat {#textformat}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td>Aucune modification pour 2.0</td> 
   <td><p>interface TextFormat<br /> {<br /> // Couleur<br /> const non signé short COLOR_DEFAULT = 0 ;<br /> const short COLOR_BLACK = 1 ;<br /> Contenir COLOR_GRAY court non signé = 2 ;<br /> Contenir COLOR_WHITE court non signé = 3 ;<br /> Contenir COLOR_BRIGHT_WHITE = 4 ;<br /> Contenir COLOR_DARK_RED = 5 ;<br /> const unsigned short COLOR_RED = 6 ;<br /> const short COLOR_BRIGHT_RED = 7 ;<br /> conf short COLOR_DARK_GREEN = 8 ;<br /> conf short COLOR_GREEN = 9 ;<br /> const unsigned short COLOR_BRIGHT_GREEN = 10 ;<br /> const unsigned short COLOR_DARK_BLUE = 11 ;<br /> const unsigned short COLOR_BLUE = 12 ;<br /> const unsigned short COLOR_BRIGHT_BLUE = 13 ;<br /> const short COLOR_DARK_YELLOW = 14 ;<br /> const unsigned short COLOR_YELLOW = 15 ;<br /> const short COLOR_BRIGHT_YELLOW = 16 ;<br /> const short COLOR_DARK_MAGENTA = 17 ;<br /> const unsigned short COLOR_MAGENTA = 18 ;<br /> Const short COLOR_BRIGHT_MAGENTA = 19 ;<br /> const short non signé COLOR_DARK_CYAN = 20 ;<br /> const short COLOR_CYAN = 21 ;<br /> const unsigned short COLOR_BRIGHT_CYAN = 22 ;<br /> <br /> attribut readonly non signé short fontColor;<br /> attribut readonly non signé short backgroundColor;<br /> attribut readonly non signé short fillColor;<br /> attribut readonly non signé short edgeColor;<br /> <br /> // Taille<br /> const non signé SIZE_DEFAULT = 0 ;<br /> const short SIZE_SMALL = 1 ;<br /> const short SIZE_MEDIUM = 2 ;<br /> const short SIZE_LARGE = 3 ;<br /> <br /> readonly attribut unsigned short size;<br /> <br /> // FontEdge<br /> const unsigned short FONT_EDGE_DEFAULT = 0 ;<br /> conf non signé court FONT_EDGE_NONE = 1 ;<br /> conf non signé court FONT_EDGE_RAISED = 2 ;<br /> conf non signé court FONT_EDGE_DEPRESED = 3 ;<br /> conf non signé court FONT_EDGE_UNIFORM = 4 ;<br /> Contenir NON signé POLIT_EDGE_DROP_SHADOW_LEFT = 5 ;<br /> Contenir NON signé POLIT_EDGE_DROP_SHADOW_RIGHT = 6 ;<br /> attribut readonly non signé short fontEdge ;<br /> <br /> // Police<br /> const unsigned short FONT_DEFAULT = 0 ;<br /> contez POLIT_MONOSPACED_WITH_SERIFS non signé = 1 ;<br /> Contenir POLIT_PROPORTIONNEL_WITH_SERIFS = 2 ;<br /> contez le numéro court non signé FONT_MONSPACED_WITHOUT_SERIFS = 3 ;<br /> conf non signé FONT_CASUAL = 4 ;<br /> conf non signé FONT_CURSIVE = 5 ;<br /> Contenir les caractères courts non signés FONT_SMALL_CAPITALS = 6 ;<br /> readonly attribut non signé police courte ;<br /> attribut readonly non signé short fontOpacity;<br /> attribut readonly non signé short backgroundOpacity;<br /> attribut readonly non signé short fillOpacity;<br /> attribut readonly non signé short DEFAULT_OPACITY;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### MediaPlayerItemLoader {#mediaplayeritemloader}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayerItemLoader :<br /> {<br /> void load(MediaResource resource, long resourceId,<br /> ItemLoaderListener, <br /> MediaPlayerItemConfig) ;<br /> void cancel();<br /> attribut readonly MediaPlayerItem currentItem;<br /> };</p> </td> 
   <td>Nouveautés de la version 2.0</td> 
  </tr> 
  <tr> 
   <td><p>interface ItemLoaderListener<br /> {<br /> //onLoadCompleteCallbackFunc(MediaPlayerItem)<br /> var onLoadCompleteCallbackFunc;<br /> //onErrorCallbackFunc(PSDKErrorCode)<br /> var onErrorCallbackFunc;<br /> }</p> </td> 
   <td>Nouveautés de la version 2.0</td> 
  </tr> 
 </tbody> 
</table>

## Modifications des éléments de l’API des caractéristiques multimédia de la version 2.0 {#media-characteristics-api-element-changes-for}

Ces tableaux comparent les éléments d’API de caractéristique multimédia pour le kit C++ TVSDK entre les versions 1.3 et 2.0.

Tableaux dans cette rubrique :

* MediaPlayerItem
* Track, AudioTrack, ClosedCaptionsTrack
* Profil
* DRMMetadataInfo

### MediaPlayerItem {#mediaplayeritem}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayerItem {<br /> ressource MediaResource en lecture seule ;<br /> attribut readonly long resourceId ;<br /> attribut readonly boolean live;<br /> <br /> l’attribut readonly boolean hasAlternateAudio;<br /> attribut readonly AudioTrackList audioTracks ;<br /> attribut readonly AudioTrack selectedAudioTrack ;<br /> void selectAudioTrack(AudioTrack); <br /> <br /> attribut readonly boolean hasClosedCaptions;<br /> attribut readonly ClosedCaptionsTrackList closedCaptionsTracks ;<br /> attribut readonly ClosedCaptionsTrack selectedClosedCaptionsTrack;<br /> void selectClosedCaptionsTrack(<br /> ClosedCaptionsTrack); <br /> <br /> attribut readonly boolean hasTimedMetadata;<br /> attribut readonly TimedMetadataList timedMetadata;<br /> l’attribut readonly boolean dynamic;<br /> <br /> l’attribut readonly boolean isProtected;<br /> attribut readonly DRMMetadataInfoList drmMetadataInfos;<br /> attribut readonly Profils ProfileList ;<br /> attribut readonly Profil sélectionnéProfile;<br /> <br /> readonly attribut boolean trickPlaySupported;<br /> attribut readonly FloatArray availablePlaybackRates;<br /> attribut readonly float selectedPlaybackRate;<br /> <br /> <br /> attribut readonly MediaPlayer mediaPlayer ;<br /> attribut readonly MediaPlayerItemConfig;<br /> };</p> </td> 
   <td><p>interface MediaPlayerItem {<br /> ressource MediaResource en lecture seule ;<br /> attribut readonly long resourceId ;<br /> attribut readonly boolean live;<br /> <br /> l’attribut readonly boolean hasAlternateAudio;<br /> attribut readonly AudioTrackList audioTracks ;<br /> attribut AudioTrack selectedAudioTrack ;<br /> <br /> <br /> attribut readonly boolean hasClosedCaptions;<br /> attribut readonly ClosedCaptionsTrackList ccTracks ;<br /> attribut ClosedCaptionsTrack selectedCCTtrack;<br /> <br /> <br /> <br /> attribut readonly boolean hasTimedMetadata;<br /> attribut readonly TimedMetadataList timedMetadata;<br /> l’attribut readonly boolean dynamic;<br /> <br /> l’attribut readonly boolean isProtected;<br /> attribut readonly DRMMetadataInfoList drmMetadataInfos;<br /> attribut readonly Profils ProfileList ;<br /> <br /> <br /> readonly attribut boolean trickPlaySupported;<br /> attribut readonly Int32Array availablePlaybackRates;<br /> <br /> attribut readonly StringList adTags ;<br /> <br /> attribut readonly MediaPlayer mediaPlayer ;<br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### Track / AudioTrack / ClosedCaptionsTrack {#track-audiotrack-closedcaptionstrack}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>suivi de l’interface<br /> {<br /> attribut readonly DomString name;<br /> l’attribut readonly DomString language ;<br /> valeur booléenne par défaut de l’attribut readonly ;<br /> attribut readonly boolean autoSelect ;<br /> }; </p> </td> 
   <td>Nouveautés de la version 2.0</td> 
  </tr> 
  <tr> 
   <td><p>interface AudioTrack : Suivi<br /> {<br /> attribut readonly DomString name; //FromTrack<br /> attribut readonly Langue DomString;//FromTrack<br /> attribut readonly boolean par défaut ; // From Track<br /> attribut readonly booléen autoSelect;//FromTrack<br /> <br /> readonly attribut non signé int pid ;<br /> };</p> </td> 
   <td><p>interface AudioTrack<br /> {<br /> attribut readonly DomString name;<br /> l’attribut readonly DomString language ; <br /> valeur booléenne par défaut de l’attribut readonly ;<br /> attribut readonly boolean autoSelect ;<br /> attribut readonly booléen forcé ;<br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td>Aucune modification pour 2.0</td> 
   <td><p>interface AudioTrackList<br /> {<br /> attribut readonly non signé long length ;<br /> getter AudioTrack (index long non signé) ;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface ClosedCaptionsTrack : suivi<br /> {<br /> attribut readonly DomString name; //FromTrack<br /> attribut readonly Langue DomString;//FromTrack<br /> attribut readonly booléen par défaut ; // FromTrack<br /> attribut readonly booléen autoSelect;//FromTrack<br /> <br /> <br /> const short SERVICE_608_CAPTIONS = 0;<br /> const short SERVICE_708_CAPTIONS = 1;<br /> const non signé short SERVICE_WEB_VTT_CAPTIONS = 2;<br /> attribut readonly non signé short serviceType;<br /> attribut readonly booléen forcé ;<br /> };</p> </td> 
   <td><p>interface ClosedCaptionsTrack<br /> {<br /> attribut readonly DomString name;<br /> l’attribut readonly DomString language ;<br /> valeur booléenne par défaut de l’attribut readonly ;<br /> <br /> <br /> attribut readonly boolean actif;<br /> <br /> <br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td>Aucune modification pour 2.0</td> 
   <td><p>interface ClosedCaptionsTrackList<br /> {<br /> attribut readonly non signé long length ;<br /> getter ClosedCaptionsTrack(index long non signé);<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### Profil {#profile}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td>Profil : aucune modification pour 2.0</td> 
   <td><p>Profil d’interface<br /> {<br /> readonly attribut non signé largeur d’int ;<br /> readonly attribut sans signe int height;<br /> attribut readonly non signé int bitRate;<br /> }; </p> </td> 
  </tr> 
  <tr> 
   <td>ProfileList : aucune modification pour 2.0</td> 
   <td><p>interface ProfileList<br /> {<br /> attribut readonly non signé long length ;<br /> getter Profile (index long non signé);<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMMetadataInfo {#drmmetadatainfo}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><strong>DRMMetadataInfo</strong>: aucune modification pour 2.0</td> 
   <td><p>interface DRMMetadataInfo<br /> { <br /> métadonnées DRMMetadata d’attribut readonly ;<br /> readonly attribut long prefetchTimestamp;<br /> attribut readonly TimeRange timeRange;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>DRMMetadataInfoList</strong>: aucune modification pour 2.0</td> 
   <td><p>interface DRMMetadataInfoList<br /> {<br /> attribut readonly non signé long length ;<br /> getter DRMMetadataInfo(index long non signé);<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

## Mappage des erreurs C++ aux exceptions dans différentes langues {#mapping-c-errors-to-exceptions-in-different-languages}

Vous pouvez mapper des codes d’erreur C++ à des exceptions dans différentes langues.

Le PSDK C++ dispose d’une stratégie de &quot;pas de lancement&quot; pour ses API. La plupart des méthodes API renvoient une valeur PSDKErrorCode pour indiquer si la méthode a été exécutée correctement. Les erreurs asynchrones sont notifiées par le biais des événements d’erreur.

L’ActionScript et le JAVA PSDK ont une stratégie différente. La plupart des erreurs renvoient un ArgumentError ou IllegalStateException pour indiquer que la partie synchrone de la méthode n’a pas pu être exécutée. Ces exceptions ne sont pas interceptées et le code de l’application est chargé de gérer les exceptions. Elles contiennent généralement des informations utiles expliquant pourquoi l’appel de méthode a échoué. Par exemple, si la commande prepareToPlay est appelée dans un état non valide, l’exception suivante est générée :

```shell
throw new IllegalStateException("Invalid player state. prepareToPlay method 
must be called only once after replaceCurrentItem or replaceCurrentResource method.");
```

L’ActionScript/JAVA renvoie également des exceptions aux constructeurs pour indiquer que certains objets internes ont été créés de manière incorrecte. Ces exceptions sont gérées en interne et ne sont pas propagées à l’application. Les exceptions seront incluses dans une notification d’avertissement envoyée à l’application.

Par exemple, si aucun fichier multimédia valide n’a été trouvé pour la réponse de publicité reçue, aucun objet de ressource de publicité ou publicité valide ne peut être créé. Par conséquent, aucune publicité n’est placée sur la chronologie et une notification NotificationEvent.OperationFailed est envoyée.

Les codes d’erreur ou d’avertissement reçus de manière asynchrone à partir du moteur vidéo Adobe (AVE) sont envoyés vers l’application comme des événements normaux. L’événement de notification contient tous les codes d’erreur reçus et toutes les métadonnées supplémentaires, telles que l’URL, l’identifiant de la ressource, le gestionnaire, etc. Si l’erreur est grave et que la lecture du média actuel ne peut pas continuer, MediaPlayer passe à l’état ERROR et l’événement onStatusChanged ou MediaPlayerStatusChanged.STATUS_CHANGED est distribué. Si la lecture peut continuer, un événement de notification normal est distribué.

<table> 
 <tbody> 
  <tr> 
   <th>C++ Error (PSDKError Code)</th> 
   <th> </th> 
   <th>Java</th> 
   <th>ActionScript</th> 
   <th>JavaScript</th> 
  </tr> 
  <tr> 
   <td>kCIDnvalidArgument</td> 
   <td> </td> 
   <td>IllegalArgumentException</td> 
   <td>ArgumentError</td> 
   <td>Exception avec code = 1, description = "INVALID_ARGUMENT" et additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECNullPointer</td> 
   <td> </td> 
   <td>IllegalArgumentException</td> 
   <td>ArgumentError</td> 
   <td>Exception avec code = 2, description = "GENERIC_ERROR" et additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kCIDllegalState</td> 
   <td> </td> 
   <td>IllegalStateException</td> 
   <td>IllegalStateException</td> 
   <td>Exception avec code = 3, description = "ILLEGAL_STATE" et additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kCiFaceNotFound</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec code = 4, description = "GENERIC_ERROR" et additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECCreationFailed</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec code = 5, description = "CREATION_FAILED" et additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECUnsupportedOperation</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec code = 5, description = "CREATION_FAILED" et additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kDCEataNotAvailable</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec code = 7, description = "DATA_NOT_AVAILABLE" et additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECSeekError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec code = 8, description = "SEEK_ERROR" et additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECUnsupportedFeature</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec code = 9, description = "UNSUPPORTED_FEATURE" et additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kRecangeError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec code = 10, description = "RANGE_ERROR" et additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECCodecNotSupported</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec code = 11, description = "CODEC_NOT_SUPPORTED" et additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECMediaError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec code = 12, description = "MEDIA_ERROR" et additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECNetworkError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec code = 13, description = "NETWORK_ERROR" et additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECGenericError</td> 
   <td> </td> 
   <td>MediaPlayerNotification.Error ou MediaPlayerNotification.Warning</td> 
   <td>MediaError ou NotificationEvent</td> 
   <td>Exception avec code = 14, description = "GENERIC_ERROR" et additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kCIDnvalidSeekTime</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec code = 15, description = "INVALID_SEEK_TIME" et additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kACEudioTrackError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec code = 16, description = "AUDIO_TRACK_ERROR" et additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kACEcprocessFromDifferent<p>ThreadError</p> </td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec code = 17, description = "GENERIC_ERROR" et additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kCEElementNotFound</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec code = 18, description = "GENERIC_ERROR" et additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECNotImplémenté</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec code = 19, description = "GENERIC_ERROR" et additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECPlaybackOperationFailed</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec code = 200, description = "PLAYBACK_OPERATION_FAILED" et additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECNativeWarning</td> 
   <td> </td> 
   <td>MediaPlayerNotification.Warning</td> 
   <td>NotificationEvent</td> 
   <td>Exception avec code = 201, description = "NATIVE_WARNING" et additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kACEdResolverFailed</td> 
   <td> </td> 
   <td>MediaPlayerNotification.Warning</td> 
   <td>-</td> 
   <td>Exception avec code = 202, description = "AD_RESOLVER_FAILED" et additionalInfo= &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
 </tbody> 
</table>

## Modifications des éléments API Utilitaire et Assistant pour la version 2.0 {#utility-and-helper-api-element-changes-for}

Ces tableaux comparent les éléments de l’API Utility et Helper pour le TVSDK JavaScript entre les versions 1.3 et 2.0.

Tableaux dans cette rubrique :

* Version
* TimeRange
* QOSProvider
* DeviceInformation
* LoadInfo
* Affichage
* PlaybackInformation

### Version {#version}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>version de l’interface<br /> {<br /> version DomString de l’attribut readonly ;<br /> description de l’attribut readonly DomString;<br /> readonly attribute long major;<br /> readonly attribut long mineur ;<br /> révision longue d’attribut readonly ;<br /> l’attribut readonly long apiVersion ;<br /> };</p> </td> 
   <td><p>version de l’interface<br /> {<br /> version DomString de l’attribut readonly ;<br /> description de l’attribut readonly DomString;<br /> attribut readonly DomString majeur ;<br /> attribut readonly DomString mineur ;<br /> attribut readonly DomString revision;<br /> attribut readonly DomString apiVersion;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### TimeRange {#timerange}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td>Aucune modification pour 2.0</td> 
   <td><p>timeRange de l’interface<br /> {<br /> l’attribut readonly non signé long start.<br /> attribut readonly non signé long end;<br /> attribut readonly non signé de longue durée ;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### QOSProvider {#qosprovider}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td>Aucune modification pour 2.0</td> 
   <td><p>interface QOSProvider<br /> {<br /> void attachMediaPlayer(MediaPlayer player);<br /> void detachMediaPlayer();<br /> <br /> attribut readonly DeviceInformation deviceInformation ;<br /> attribut readonly PlaybackInformation playbackInformation;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DeviceInformation {#deviceinformation}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>interface DeviceInformation<br /> {<br /> attribut readonly DomString os;<br /> <br /> <br /> <br /> attribut readonly DomString id;<br /> readonly attribut int densitéDPI ;<br /> readonly attribute int heightPixels;<br /> attribut readonly int widthPixels;<br /> attribut readonly booléen searchToKeyFrame;<br /> };</p> </td> 
   <td><p>interface DeviceInformation<br /> {<br /> attribut readonly DomString os;<br /> readonly attribute int sdk;<br /> attribut readonly modèle DomString ;<br /> attribut readonly DomString manufacturer;<br /> attribut readonly DomString id;<br /> readonly attribut int densitéDPI ;<br /> readonly attribute int heightPixels;<br /> attribut readonly int widthPixels;<br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### LoadInfo {#loadinfo}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td>Aucune modification pour 2.0</td> 
   <td><p>interface LoadInfo<br /> {<br /> L’attribut readonly DomString url ;<br /> readonly attribute int size;<br /> attribut readonly double downloadDuration;<br /> attribut readonly int periodIndex;<br /> readonly attribut double mediaDuration;<br /> attribut readonly short TRACK_TYPE_FRAGMENT;<br /> readonly attribut short TRACK_TYPE_TRACK;<br /> attribut readonly short TRACK_TYPE_MANIFEST;<br /> type short d’attribut readonly ;<br /> attribut readonly DomString trackName;<br /> attribut readonly DomString trackType;<br /> attribut readonly int trackIndex;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### Affichage {#view}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td>Aucune modification pour 2.0</td> 
   <td><p>Vue de l’interface<br /> {<br /> attribut readonly non signé short x;<br /> attribut readonly non signé short y;<br /> attribut readonly non signé short width;<br /> attribut readonly non signé à une hauteur courte ;<br /> <br /> void setSize(largeur courte non signée, hauteur courte non signée);<br /> void setPos(unsigned short x, unsigned short y);<br /> }</p> </td> 
  </tr> 
 </tbody> 
</table>

### PlaybackInformation {#playbackinformation}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>Interface PlaybackInformation<br /> {<br /> attribut readonly double timeToFirstByte;<br /> attribut readonly double timeToLoad;<br /> readonly attribut double timeToStart;<br /> readonly attribut double timeToFail;<br /> attribut readonly int totalSecondsPlayed;<br /> attribut readonly int totalSecondsSpent;<br /> attribut readonly double frameRate;<br /> attribut readonly int droppedFrameCount;<br /> readonly attribute int perceptionBandwidth;<br /> readonly attribut int bitrate;<br /> attribut readonly double bufferTime ;<br /> attribut readonly int bufferLength;<br /> attribut readonly int emptyBufferCount;<br /> attribut readonly double bufferingTime;<br /> };</p> </td> 
   <td><p>Interface PlaybackInformation<br /> {<br /> attribut readonly double timeToFirstByte;<br /> attribut readonly double timeToLoad;<br /> readonly attribut double timeToStart;<br /> readonly attribut double timeToFail;<br /> attribut readonly int totalSecondsPlayed;<br /> attribut readonly int totalSecondsSpent;<br /> attribut readonly double frameRate;<br /> attribut readonly int droppedFrameCount;<br /> <br /> readonly attribut int bitrate;<br /> attribut readonly double bufferTime ;<br /> attribut readonly int bufferLength;<br /> attribut readonly int emptyBufferCount;<br /> attribut readonly double bufferingTime;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

## Ressources utiles {#helpful-resources}

* Consultez la documentation d’aide complète à l’adresse [Formation et assistance pour Adobe Primetime](https://helpx.adobe.com/support/primetime.html) page.
