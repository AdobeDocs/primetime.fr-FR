---
title: Conversion de TVSDK - 1.3 à 2.0 pour JavaScript
description: De nombreuses signatures de méthode et noms d'éléments d'API ont changé pour la version 2.0. Consultez ces tableaux pour voir tous les détails de modification de l'API.
contentOwner: asgupta
products: SG_PRIMETIME
topic-tags: migration
translation-type: tm+mt
source-git-commit: b33240bf1b42b80389cd95a7ae4d3f85185a2d32
workflow-type: tm+mt
source-wordcount: '5034'
ht-degree: 0%

---


# Conversion de TVSDK - 1.3 à 2.0 pour JavaScript {#tvsdk-conversion-to-for-javascript}

De nombreuses signatures de méthode et noms d&#39;éléments d&#39;API ont changé pour la version 2.0. Consultez ces tableaux pour voir tous les détails de modification de l&#39;API.

## Mise en oeuvre des fonctions de rappel dans JavaScript {#implement-callback-functions-in-javascript}

Les commentaires dans la documentation de la méthode suggèrent la signature des rappels que vous devez implémenter.

Pour JavaScript, la syntaxe de l’API est basée sur l’ID Web. Pour une interface TVSDK, les noms de méthode sont appelés *methodName*(). Pour que les méthodes soient implémentées par votre application, un attribut de lecture/écriture appelé *methodName* CallbackFunc est ajouté à l&#39;interface et votre application doit le définir pour qu&#39;il pointe vers une fonction qui implémente la méthode. Par exemple :

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

## Modifications des éléments de l’API de flux de travaux publicitaires pour la version 2.0 {#advertising-workflow-api-element-changes-for}

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
* Journal / TimelineItem / TimelineMarker
* AdBreak
* Ad / AdAsset / AdClick / AdList / AdAssetList / AdBannerAsset
* AdBreakTimelineItem / AdTimelineItem
* AdBreakPolicy / AdBreakWatchedPolicy / AdPolicy / AdPolicyMode / AdPolicyInfo / AdPolicySelector
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
   <td><p> <strong>TimedMetadata</strong> : interface TimedMetadata {<br /> const unsigned short METADATA_TYPE_TAG = 0;  <br /> const unsigned short METADATA_TYPE_ID3 = 1;  <br /> readonly attribut non signé short type ;  <br /> readonly attribut long ; <br /> readonly attribut DomString id ; <br /> readonly attribut nom DomString ; <br /> readonly attribut contenu DomString ;  <br /> readonly, attribut, métadonnées d'objet;<br /> }; </p> </td> 
   <td><p>interface TimedMetadata {<br /> const unsigned short METADATA_TYPE_TAG = 0;<br /> const unsigned short METADATA_TYPE_ID3 = 1;<br /> readonly attribute unsigned short metadataType;<br /> readonly attribute long time;<br /> readonly attribute long id;<br /> readonly attribute dom_chaîne; <br /> <br /> attribut readonly Métadonnées d'objet Object;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>TimedMetadataList</strong> : (Aucun changement pour la version 2.0)</td> 
   <td><p>interface TimedMetadataList {<br /> attribut readonly non signé long ;<br /> getter TimedMetadata(index long non signé);<br /> };</p> </td> 
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
   <td><p>Interface AdSignalingMode { <br /> const unsigned short MODE_DEFAULT, <br /> const unsigned short MODE_MANIFEST_CUES, <br /> const short non signé MODE_SERVER_MAP, <br /> const unsigned short MODE_CUSTOM_RANGES <br /> };</p> </td> 
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
   <td><p>Interface AdvertisingMetadata { <br /> attribut AdSignalingMode ; <br /> attribut AdBreakWatchedPolicy adBreakAsWatched ; <br /> attribut booléen livePreroll ; Attribut <br /> booléen delayAdLoading ; <br /> };</p> </td> 
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
   <td><p>Interface CustomRangeMetadata { <br /> const non signé short TYPE_MARK_RANGE; <br /> const short non signé TYPE_DELETE_RANGE; <br /> const unsigned short TYPE_REPLACE_RANGE ; <br /> attribut de type court non signé ; <br /> attribut booléen modifySeekPosition ; <br /> attribut TimeRangeList timeRangeList ; <br /> };</p> </td> 
   <td>(Nouveau pour la version 2.0)</td> 
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
   <td><p>interface ReplaceTimeRange { <br /> attribut non signé long begin; <br /> attribut readonly non signé long end ; attribut <br /> non signé de longue durée ; <br /> attribut non signé long replaceDuration ; <br /> };</p> </td> 
   <td>(Nouveau pour la version 2.0)</td> 
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
   <td><p>Interface Placement { <br /> const non signé short TYPE_MID_ROLL; <br /> const unsigned short TYPE_PRE_ROLL; <br /> const short non signé TYPE_POST_ROLL; <br /> const unsigned short TYPE_SERVER_MAP; <br /> const unsigned short TYPE_CUSTOM_RANGE;<br /> attribut readonly non signed short type ; <br /> attribut readonly long ; <br /> attribut lecture seule longue durée ; <br /> const unsigned short MODE_DEFAULT; <br /> const unsigned short MODE_INSERT; <br /> const unsigned short MODE_REPLACE ; <br /> const unsigned short MODE_DELETE ; <br /> const unsigned short MODE_MARK; <br /> const unsigned short MODE_FREE_REPLACE ; <br /> attribut readonly non signé mode court ; <br /> attribut readonly Plage TimeRange; <br /> };</p> </td> 
   <td>(Nouveau pour la version 2.0)</td> 
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
   <td><p>interface Opportunity { <br /> attribut readonly DomString id; <br /> attribut en lecture seule Emplacement ; <br /> Paramètres d'objet en lecture seule ; <br /> attribut readonly Object customParameters; <br /> }; </p> </td> 
   <td>(Nouveau pour la version 2.0)</td> 
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
   <td><p>interface Reservation { <br /> attribut readonly plage de TimeRange; <br /> attribut readonly long hold ; <br /> }; </p> </td> 
   <td> (Nouveau pour la version 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### Timeline / TimelineItem / TimelineMarker {#timeline-timelineitem-timelinemarker}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p><strong>Chronologie</strong> : interface Timeline  <br /> { readonly attribut TimelineMarkerList timelineMarkers ;  <br /> readonly attribut TimelineItemList timelineItems ;  <br /> doublon convertToLocalTime( doublon);  <br /> doublon convertToVirtualTime( doublon);  <br /> };</p> </td> 
   <td><p>interface Timeline {<br /> attribut readonly TimelineMarkerList timelineMarkers;<br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p> <strong>TimelineItem</strong> : interface TimelineItem : <br /> TimelineMarker {<br /> readonly attribut long id;  <br /> readonly attribut TimeRange virtualRange;  <br /> readonly attribut TimeRange localRange;  <br /> readonly attribut boolean watched;  <br /> readonly, attribut booléen temporaire ;  <br /> }; </p> </td> 
   <td>(Nouveau pour la version 2.0)</td> 
  </tr> 
  <tr> 
   <td><strong>TimelineMarker</strong> : (Aucun changement pour la version 2.0)</td> 
   <td><p>interface TimelineMarker {<br /> readonly attribute doublon time;<br /> readonly attribute doublon duration;<br /> };</p> </td> 
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
   <td><p>interface AdBreak {<br /> <br /> <br /> <br /> durée du doublon d'attribut readonly ;<br /> attribut readonly publicités AdList ; <br /> <br /> <br /> attribut readonly AdInsertionTypeInsertionType ;<br /> }; </p> </td> 
   <td><p>interface AdBreak {<br /> readonly attribute doublon time;<br /> readonly attribute doublon replaceDuration;<br /> <br /> readonly attribute doublon duration;<br /> readonly attribute adList;<br /> <br /> readonly attribute DomString data;<br /> <br /> }; </p> </td> 
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
   <td><p> <strong>Publicité</strong> : interface Publicité {<br /> readonly attribut AdAsset primaryAsset;<br /> readonly attribut AdAssetList CompanionAssets;<br /> <br /> readonly attribut doublon duration;<br /> readonly attribut DomString id;<br /> const unsigned short ADTYPE_LINEAR = 0;<br /> const unsigned short ADTYPE_NONLINEAR = 1;<br /> <br /> readonly attribut unsigned short adType; attribut AdInsertionType adInsertionType;  <br /> <br /> readonly attribut booléen cliquable ;  <br /> readonly, attribut booléen isCustomAdMarker;<br /> };<br /> </p> </td> 
   <td><p>interface Ad {<br /> attribut readonly AdAsset primaryAsset ;<br /> attribut readonly AdAssetList CompanionAssets ; <br /> <br /> durée du doublon d'attribut readonly ;<br /> attribut readonly ID DomString ;<br /> const unsigned short ADTYPE_LINEAR = 0 ;<br /> const unsigned short ADTYPE_NADKYTORK ONLINEAR = 1 ; <br /> <br /> attribut readonly type short non signé ;<br /> attribut readonly attribut AdInsertionType insertType ; <br /> attribut readonly Suivi d'objet Object;<br /> <br /> <br /> }; </p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdAsset</strong> : (Aucun changement pour la version 2.0)</td> 
   <td><p>interface AdAsset {<br /> attribut readonly DomString id;<br /> durée du doublon d'attribut readonly ;<br /> attribut readonly ressource MediaResource ;<br /> attribut readonly AdClick adClick ;<br /> attribut readonly metadata Object ;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdClick</strong> : (Aucun changement pour la version 2.0)</td> 
   <td><p>interface AdClick {<br /> attribut readonly DomString id;<br /> attribut readonly DomString title;<br /> attribut readonly DomString url;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdList</strong> : (Aucun changement pour la version 2.0)</td> 
   <td><p>interface AdList {<br /> attribut readonly non signé long ;<br /> getter Ad(index long non signé);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdAssetList</strong> : (Aucun changement pour la version 2.0)</td> 
   <td><p>interface AdAssetList {<br /> attribut readonly non signé de longue durée ;<br /> getter AdAsset(index long non signé);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p><strong>AdBannerAsset</strong> : interface AdBannerAsset : AdAsset<br /> {<br /> readonly attribut int width;<br /> readonly attribut int height;<br /> readonly attribut DomString staticUrl;<br /> readonly attribut DomString height;<br /> readonly attribut DomString width;<br /> };</p> </td> 
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
   <td><p> <strong>AdBreakTimelineItem</strong> : interface AdBreakTimelineItem : TimelineItem { attribut  <br /> readonly AdBreak adBreak;  <br /> readonly attribut éléments AdTimelineItemList ;  <br /> }; </p> </td> 
   <td> (Nouveau pour la version 2.0)</td> 
  </tr> 
  <tr> 
   <td><p><strong>AdTimelineItem</strong> : interface AdTimelineItem : TimelineItem { attribut  <br /> readonly AdBreak adBreak;  <br /> readonly attribut publicité ;  <br /> }; </p> </td> 
   <td> (Nouveau pour la version 2.0)</td> 
  </tr> 
  <tr> 
   <td><p><strong>AdBreakTimelineItemList</strong> : interface AdBreakTimelineItemList {  <br /> attribut readonly non signé long ;  <br /> getter AdBreakTimelineItem (index lo ng non signé);  <br /> };</p> </td> 
   <td> (Nouveau pour la version 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### AdBreakPolicy / AdBreakWatchedPolicy / AdPolicy / AdPolicyMode / AdPolicyInfo / AdPolicySelector {#adbreakpolicy-adbreakwatchedpolicy-adpolicy-adpolicymode-adpolicyinfo-adpolicyselector}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p>interface AdBreakPolicy {<br /> attribut readonly short AD_BREAK_POLICY_SKIP;<br /> attribut readonly short AD_BREAK_POLICY_PLAY;<br /> attribut readonly short AD_BREAK_POLICY_REMOVE;<br /> attribut readonly short AD_BREAK_POLICY_REMOVE_AFV_PLAY;<br /> };</p> </td> 
   <td><p> interface AdPolicyConstants {<br /> attribut readonly short AD_BREAK_POLICY_SKIP;<br /> attribut readonly short AD_BREAK_POLICY_PLAY;<br /> attribut readonly short AD_BREAK_POLICY_REMOVE;<br /> attribut readonly short AD_BREAK_POLICY_AFVE_REMOVE TER_PLAY;}<br /> ...</p> </td> 
  </tr> 
  <tr> 
   <td><p> interface AdBreakWatchedPolicy {<br /> attribut readonly short AD_BREAK_AS_WATCHED_ON_BEGIN;<br /> attribut readonly short AD_BREAK_AS_WATCHED_ON_END;<br /> attribut readonly short AD_BREAK_AS_WATCHED_NEVER;<br /> }; </p> </td> 
   <td><p> ...<br /> attribut readonly short AD_BREAK_AS_WATCHED_ON_BEGIN;<br /> attribut readonly short AD_BREAK_AS_WATCHED_ON_END;<br /> attribut readonly short AD_BREAK_AS_WATCHED_NEVER;<br /> ...</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicy {<br /> attribut readonly short AD_POLICY_PLAY ;<br /> attribut readonly short AD_POLICY_PLAY_FROM_AD_BEGIN ;<br /> attribut readonly short AD_POLICY_PLAY_FROM_AD_BREAK_BEGIN ; readonly attribut short AD_POLICY_SKIP_TO_NEXT_AD_IN_BREAK;<br /> <br /> attribut readonly short AD_POLICY_SKIP_AD_BREAK;<br /> };</p> </td> 
   <td><p> <br /> attribut readonly short AD_POLICY_PLAY ;<br /> attribut readonly short AD_POLICY_PLAY_FROM_AD_BEGIN ;<br /> attribut readonly short AD_POLICY_PLAY_FROM_AD_BREAK_BEGIN ;<br /> attribut readonly short AD_POLICY_SKIP_TO_NEXT_AD_AD_AD_BREAK;<br /> attribut readonly short AD_POLICY_SKIP_AD_BREAK;<br /> ...</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicyMode {<br /> attribut readonly short AD_POLICY_MODE_PLAY;<br /> attribut readonly short AD_POLICY_MODE_SEEK;<br /> attribut readonly short AD_POLICY_MODE_TRICKPLAY;<br /> };</p> </td> 
   <td><p> ...<br /> {readonly attribute short AD_POLICY_MODE_PLAY;<br /> readonly attribute short AD_POLICY_MODE_SEEK;<br /> readonly attribute short AD_POLICY_MODE_TRICKPLAY;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicyInfo {<br /> attribut readonly AdBreakTimelineItemList <br /> adBreakTimelineItems;<br /> attribut readonly AdTimelineItem adTimelineItem;<br /> attribut readonly doublon currentTime;<br /> attribut readonly doublon searchToTime;<br /> attribut readonly Taux de doublon ; <br /> mode court d'attribut readonly ; //AdPolicyMode<br /> };</p> </td> 
   <td><p>interface AdPolicyInfo {<br /> attribut readonly AdBreakPlacementList <br /> adBreakPlacements;<br /> attribut readonly publicité ;<br /> attribut readonly doublon currentTime ;<br /> attribut readonly rechercheToTime du doublon d'attributs readonly ;<br /> taux de doublon d'attributs readonly ;<br /> attribut readonly ; //AdPolicyMode<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicySelector {<br /> /**<br /> * AdbreakPolicy selectPolicyForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribut Object selectPolicyForAdBreakCallbackFunc;<br /> /*<br /> * AdBreakTimelineItemList selectAdBreaksToPlay(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribut Objet selectAdBreaksToPlayCallbackFunc;<br /> /*<br /> * AdPolicy selectPolicy SeekIntoAd(AdPolicyInfo adPolicyInfo);<br /> */<br /> attribut Objet selectPolicyForSeekIntoAdCallbackFunc; <br /> /**<br /> * AdBreakWatchedPolicy selectWatchedPolicyForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribut Object selectWatchedPolicyForAdBreak CallbackFunc;<br /> };</p> </td> 
   <td><p>interface AdPolicySelector {<br /> /**<br /> * AdbreakPolicy selectPolicyForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribut Object selectPolicyForAdBreakFuncCallback;<br /> /*<br /> * AdBreakPlacementList selectAdBreaksToPlay(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribut Objet selectAdBreaksToPlayCallback;<br /> /**<br /> * AdPolicy selectPolicyForSeek toAd(AdPolicyInfo adPolicyInfo);<br /> */<br /> attribut Objet selectPolicyForSeekIntoAdCallback; <br /> /**<br /> * AdBreakAsWatched selectWatchedPolicyForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribut Object selectWatchedPolicyForAdBreak Callback;<br /> };</p> </td> 
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
   <td> (Nouveau pour la version 2.0)</td> 
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
   <td><p>interface AdBreakPlacement : TimelineOperation {<br /> attribut readonly AdBreak adBreak ; <br /> attribut readonly Placement emplacement ; // De TimelineOperation<br /> Temps de doublon de l'attribut readonly ;<br /> Durée du doublon de l'attribut readonly ;<br /> };</p> </td> 
   <td><p>interface AdBreakPlacement {<br /> attribut readonly AdBreak adBreak ;<br /> attribut readonly Placement ;<br /> temps de doublon d'attribut readonly ;<br /> durée de doublon d'attribut readonly ;<br /> };</p> </td> 
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
   <td><p>interface Paramètres d’audience : AdvertisingMetadata { <br /> attribut DomString zoneId; <br /> attribut DomString mediaId ; Attribut <br /> DomString defaultMediaId ; <br /> attribut Domaine DomString ; <br /> attribut Objet targetInfo ; <br /> attribut Object customParameters ; <br /> attribut Boolean creativePackaingEnabled;<br /> attribut Boolean showStaticBanners;<br /> };</p> </td> 
   <td>La fonctionnalité a été fournie par la clé MetadataKeys::AUDITUDE_METADATA_KEY.</td> 
  </tr> 
 </tbody> 
</table>

## Modifications des éléments de l’API de personnalisation pour la version 2.0 {#customization-api-element-changes-for}

Ces tableaux comparent les éléments d’API de personnalisation pour le SDK JavaScript TVSDK entre les versions 1.3 et 2.0.

Tableaux dans cette rubrique :

* MediaPlayerItemConfig
* ContentFactory
* NetworkConfiguration

### MediaPlayerItemConfig {#mediaplayeritemconfig}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayerItemConfig {<br /> attribut ContentFactory adFactory ;<br /> attribut StringList subscriptionTags ; <br /> attribut StringList adTags ; <br /> <br /> attribut AdSignalingMode adSignalingMode ;<br /> attribut personnaliséRangeMetadata RangeMetadata ; <br /> attribut NetworkConfiguration networkConfiguration ;<br /> attribut AdvertisingMetadata publicadataMetadata ;<br /> attribut booléen useHardwareDecoder ;<br /> };<br /><br /></p> </td> 
   <td><p>interface MediaPlayerConfig {<br /> <br /> <br /> <br /> attribut StringList adTags;<br /> attribut StringList subscribedTags;<br /> attribut MediaPlayerClientFactory clientFactory;<br /> <br /> <br /> <br />   &lt;a10/&lt;a10/&lt;a0/<br /> <br /> &lt;a a11/&gt; };</p> </td> 
  </tr> 
 </tbody> 
</table>

### ContentFactory {#contentfactory}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
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
   <th>API 2.0</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface NetworkConfiguration<br /> {<br /> attribut booléen forceNativeNetworking;<br /> attribut booléen useRedirectUrl;<br /> attribut Object cookieHeader;<br /> attribut booléen readSetCookieHeader;<br /> attribut int masterUpdateInterval; <br /> attribut booléen useCookieHeaderForAllRequests;<br /> attribut int readLimit;<br /> };</p> </td> 
   <td>Dans la version 1.3, certaines de ces fonctionnalités ont été fournies par MetadataKeys.</td> 
  </tr> 
 </tbody> 
</table>

## Modifications de l’élément d’API DRM pour la version 2.0 {#drm-api-element-changes-for}

Ces tableaux comparent les éléments d’API DRM pour le SDK JavaScript TVSDK entre les versions 1.3 et 2.0.

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
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td>L’application doit appeler AdobePSDK.initiateDRMWorkflow pour lancer le processus DRM. Sans cet appel, les vidéos DRM ne seront pas lues.<p>interface AdobePSDK<br /> {<br /> void initiateDRMWorkFlow(<br /> DomString appStoratePath, <br /> DomString publisherId, <br /> DomString appId, <br /> DomString appVersion, <br /> boolean privacyModeOn);<br /> };</p> </td> 
   <td>L'initialisation a été effectuée en interne et aucun appel explicite n'a été requis.</td> 
  </tr> 
 </tbody> 
</table>

### DRMAcquireLicenseSettings/DRMAuthenticationMethod {#drmacquirelicensesettings-drmauthenticationmethod}

| API 2.0 | 1.3 API |
|--- |--- |
| **DRMAcquireLicenseSettings** |  |
| Aucune modification pour la version 2.0. | enum DRMAcquireLicenseSettings <br>{<br> const unsigned int FORCE_REFRESH = 0;<br> const unsigned int LOCAL_ONLY = 1;<br> const unsigned int ALLOW_SERVER = 2;<br> }; |
| **DRMAuthenticationMethod** |  |
| Aucune modification pour la version 2.0. | enum DRMAuthenticationMethod <br>{<br> const unsigned int UNKNOWN = 0;<br> const unsigned int ANONYMOUS = 1;<br> const unsigned int USERNAME_AND_PASSWORD = 2;<br> } |

### DRMMetadata {#drmmetadata}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td>Aucune modification pour la version 2.0.</td> 
   <td><p>interface DRMMetadata<br /> {<br /> attribut readonly DomString serverUrl;<br /> attribut readonly licenseId DomString;<br /> attribut readonly stratégies DRMPolicyArray; <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMPlaybackTimeWindow {#drmplaybacktimewindow}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface DRMPlaybackTimeWindow {<br /> attribut readonly int playbackPeriodInSeconds;<br /> attribut readonly long playbackStartDate;<br /> attribut readonly long playbackEndDate;<br /> };</p> </td> 
   <td><p>interface DRMPlaybackTimeWindow {<br /> attribut readonly int periodInSeconds;<br /> attribut readonly int startDate;<br /> attribut readonly int endDate;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMLicense {#drmlicense}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td>Aucune modification pour la version 2.0.</td> 
   <td><p>interface DRMLicense {<br /> attribut readonly Octets Uint8Array ;<br /> attribut readonly Date licenseStartDate ;<br /> attribut readonly DateEndDate ;<br /> attribut readonly Date offlineStorageStartDate ;<br /> attribut readonly Date offlineStorageEndDate ; <br /> attribut readonly DomString serverUrl;<br /> attribut readonly licenseID DomString;<br /> attribut readonly DomString policyID;<br /> attribut readonly DRMPlaybackTimeWindow playbackTimeWindow;<br /> attribut readonly Object customProperties;<br /> }; </p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMLicenseDomain {#drmlicensedomain}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>1.3 API</th> 
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
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface DRMPolicy<br /> {<br /> attribut readonly DomString authenticationDomain;<br /> attribut readonly DRMAuthenticationMethod authenticationMethod;<br /> <br /> attribut readonly DomString displayName;<br /> attribut readonly DRMLicenseDomain;<br /> };</p> </td> 
   <td><p>interface DRMPolicy<br /> {<br /> attribut readonly DomString authDomain;<br /> attribut readonly DRMAuthenticationMethod authMethod;<br /> attribut readonly DomString dispName;<br /> attribut readonly DRMLicenseDomain licenseDomain;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMManager {#drmmanager}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface DRMManager : EventTarget {<br /> void acquisitionLicense(DRMMetadata metadata, <br /> paramètre DRMAcquireLicenseSettings, <br /> écouteur DRMAquireLicenseListener);<br /> void acquisitionPreviewLicense(DRMMetadata metadata, <br /> écouteur DRMAquireLicenseListener);&lt;a5/ &gt; void authenticate(DRMMetadata metadata metadata, <br /> URL DomString,<br /> DomString &amp;authenticationDomain, <br /> utilisateur DomString, <br /> mot de passe DomString, <br /> écouteur DRMAuthenticateListener); <br /> <br /> createMetadataFromBytes(<br /> tableau Uint8Array, écouteur DRMErrorListener);<br /> void initialize(écouteur DRMOperationCompleteListener);<br /> attribut long maxOperationTime;<br /> <br /> void join LicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> booléen forceRefresh, <br /> écouteur DRMOperationCompleteListener);<br /> void leaveLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> écouteur DRMOperationCompleteListener);<br /> <br /> void resetDRM(DRMOperationCompleteListener listener);<br /> void returnLicense(DomString serverURL, <br /> DomString licenseID, <br /> Dom String policyID, <br /> booléen commitImmédiatement,<br /> DRMReturnLicenseListener listener);<br /> void setAuthenticationToken(<br /> Métadonnées DRMMetadata, <br /> DomString authenticationDomain, <br /> jeton int8Array, <br /> écouteur DRMOperationCompleteListener);<br /> void storeLicenseBytes(Uint8Array licenseBytes, <br /> écouteur DRMOperationCompleteListener);<br /> };<br /></p> </td> 
   <td><p>interface DRMManager : EventTarget {<br /> void acquisitionLicense(DRMMetadata metadata, <br /> paramètre DRMAcquireLicenseSettings, <br /> EventContext eventContext);<br /> void acquisitionPreviewLicense(DRMMetadata metadata, <br /> EventContextContext);<br /> void authenticate(DRMMetadata, metadata) <br /> URL DomString,<br /> DomString &amp;authenticationDomain, <br /> utilisateur DomString, <br /> mot de passe DomString, <br /> EventContext eventContext);<br /> <br /> DRMMetadata createMetadataFromBytes(<br /> 3/&gt; Tableau Uint8Array, EventContext eventContext);<br /> void initialize(EventContext eventContext);<br /> attribut long maxOperationTime;<br /> <br /> void joinLicenseDomain(<br /> DRMLicenseDomain licenseDomain, &lt;a1 9/&gt; booléen forceRefresh, <br /> EventContext eventContext);<br /> void leaveLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> EventContextContext);<br /> <br /> voidDRM(Event) Context eventContext);<br /> void returnLicense(DomString serverURL, <br /> DomString licenseID,<br /> DomString policyID, <br /> booléen commitImmédiatement,<br /> EventContextEvent);<br /> void setAuthenticationToken(<br /> métadonnées DRMMetadata, <br /> DomString authenticationDomain, <br /> jeton Uint8Array, <br /> EventContext eventContext);<br /> void storeLicenseBytes(Uint8Array licenseBytes, <br /> EventContext eventContext);<br /> };<br /></p> </td> 
  </tr> 
  <tr> 
   <td><p>classe DRMErrorListener : <br /> public psdkutils::PSDKInterfaceWithUserData {<br /> public:<br /> virtuel void onDRMError(uint32_t major, <br /> uint32_t mineur, <br /> const psdkutils : PSDKString&amp; errorString, <br /> const psdkutils::PSDKString&amp; errorServerUrl) = 0;<br /> <br /> protégé:<br /> virtuel ~DRMErrorListener() {}<br /> }</p> </td> 
   <td>Événement / Interface / Description 
    <ul> 
     <li>kEventDRMOperationError<p>/ DRMOperationErrorEvent</p> <p>Lorsqu'une erreur se produit lors de l'une des méthodes asynchrones de DRMManger.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>classe DRMOperationCompleteListener : <br /> public DRMErrorListener {<br /> public:<br /> virtuel void on DRMOperationComplete() = 0;<br /> <br /> protégé:<br /> virtuel ~DRMOperationCompleteListener() {}<br /> };</p> </td> 
   <td>Événement / Interface / Description 
    <ul> 
     <li>kEventDRMInitializationComplete<p>/ PSDKEvent</p> <p>Lorsque l'initialisation de DRM est terminée.</p> </li> 
     <li>kEventDRMJoinLicenseDomainComplete<p>/ PSDKEvent</p> <p>Lorsque l'action joinLicenseDomain() se termine correctement.</p> </li> 
     <li>kEventDRMLeaveLicenseDomainComplete<p>/ PSDKEvent</p> <p>Lorsque l'action leaveLicenseDomain() se termine correctement.</p> </li> 
     <li>kEventDRMResetCompletePSDKEvent<p>/ PSDKEvent</p> <p>Lorsque l’action resetDRM() se termine correctement.</p> </li> 
     <li>kEventDRMAuthenticationTokenSet<p>/ PSDKEvent</p> <p>Lorsque l'action setAuthenticationTokenSet() se termine correctement.</p> </li> 
     <li>kEventDRMLicenseStored<p>/ PSDKEvent</p> <p>Lorsque l'action storeLicenseBytes() se termine correctement.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>classe DRMAuthenticateListener : <br /> public DRMErrorListener {<br /> public:<br /> virtuel void onAuthenticationComplete(<br /> psdkutils::PSDKImmutableByteArray* <br /> authenticationToken) = 0;<br /> <br /> protégé :<br /> virtuel ~DRMAuthuthenticen ateListener() {}<br /> }</p> </td> 
   <td>Événement / Interface / Description 
    <ul> 
     <li>kEventDRMAuthenticationComplete<p>/ DRMAuthenticationCompleteEvent</p> <p>Lorsque l'appel de la méthode DRMManager::authenticate est réussi.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>classe DRMAquireLicenseListener : <br /> public DRMErrorListener {<br /> public:<br /> virtuel void on LicenseAcquired(const DRMLicense*) = 0;<br /> <br /> protégé:<br /> virtuel ~DRMAquireLicenseListener() {}<br /> };</p> </td> 
   <td>Événement / Interface / Description 
    <ul> 
     <li>kEventDRMPreviewLicenseAcquired<p>/ DRMLicenseAcquiredEvent</p> <p>Lorsque l'appel de la méthode DRMManager::acquisitionPreviewLicense réussit.</p> </li> 
     <li>kEventDRMLicenseAcquired<p>/ DRMLicenseAcquiredEvent</p> <p>Lorsque l'appel de la méthode DRMManager::acquisitionLicense est réussi.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>classe DRMReturnLicenseListener: <br /> public DRMErrorListener {<br /> public:<br /> virtual void onLicenseReturnComplete(uint32_t numReturn ) = 0;<br /> <br /> protégé:<br /> virtuel ~DRMReturnLicenseListener() {}<br /> };</p> </td> 
   <td>Événement / Interface / Description 
    <ul> 
     <li>kEventDRMLicenseReturnComplete<p>/ DRMLicenseReturnCompleteEvent</p> <p>Lorsque l'appel de la méthode DRMManager::returnLicense réussit.</p> </li> 
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
* ParamètresContrôleTampon
* TextFormat
* MediaPlayerItemLoader

### MediaResource {#mediaresource}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaResource {<br /> attribut URL DomString; <br /> attribut type court non signé ;<br /> attribut Métadonnées d'objet ;<br /> const unsigned short TYPE_HLS ;<br /> const short non signé TYPE_HDS ;<br /> const unsigned short TYPE_DASH ;<br /> const unsigned short TYPE_CUSTOM ; <br /> const non signé short TYPE_UNKNOWN ; <br /> };</p> </td> 
   <td><p>interface MediaResource {<br /> attribut URL DomString ;<br /> attribut type DomString ;<br /> attribut métadonnées d'objet ; <br /> <br /> <br /> <br /> <br />  <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### MediaPlayer {#mediaplayer}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayer : EventTarget<br /> {<br /> void prepareToPlay( position du doublon);<br /> void play();<br /> void pause();<br /> void search( position du doublon);<br /> void searchToLocal( position du doublon);<br /> void reset();<br /> void();&lt;a8/ &gt; void replaceCurrentItem(élément MediaPlayerItem);<br /> void replaceCurrentResource(ressource MediaResource, <br /> MediaPlayerItemConfig); <br /> void suspend();<br /> void restore();<br /> void notificationClick();<br /> <br /> attribut en lecture seule TimeRange playbackRange;<br /> attribut en lecture seule TimeRange SekableRange;<br /> attribut en lecture seule doublon currentTime ;<br /> attribut readonly doublon localTime ;<br /> attribut readonly TimeRange bufferedRange ;<br /> attribut readonly DRMManager drmManager ;<br /> attribut readonly MediaPlayerItem currentItem;<br /> <br /> /&gt; PlayerStatus<br /> <br /> <br /> const unsigned short PLAYER_STATUS_INITIALIZED;<br /> const unsigned short PLAYER_STATUS_PREPARING;<br /> const unsigned short PLAYER_STATUS_PREPARED;&lt;a220 9/&gt; const unsigned short PLAYER_STATUS_PLAYING;<br /> const unsigned short PLAYER_STATUS_PAUSED;<br /> const unsigned short PLAYER_STATUS_SEEKING;<br /> const unsigned short PLAYER_STATUS_COMPLETE;&lt;a3 const unsigned short PLAYER_STATUS_ERROR;<br /> const unsigned short PLAYER_STATUS_RELEASED;<br /> <br /> attribut readonly non signé short status;<br /> <br /> attribut unsigned short volume;&lt;a39/ &gt; attribut ABRControlParameters abrControlParameters ; <br /> attribut BufferControlParameters bufferControlParameters ; <br /> <br /> const unsigned short VISIBLE ; //Pour la visibilité CC<br /> const unsigned short INVISIBLE; //Pour la visibilité CC<br /> attribut non signé ccVisibility court ;<br /> attribut TextFormat ccStyle ;<br /> attribut readonly playbackMetrics playbackMetrics ;<br /> <br /> taux de doublon d'attribut ;<br /> attribut MediaPlayerView ; a50/&gt; attribut en lecture seule Chronologie du journal ; <br /> doublon d'attribut currentTimeUpdateInterval ; <br /> // ce paramètre ne sera pas pris en charge pour 2.0<br /> };<br /><br /><br /><br /><br /></p> </td> 
   <td><p>interface MediaPlayer : EventTarget<br /> {<br /> void prepareToPlay( int position);<br /> void play();<br /> void pause();<br /> void search( int position);<br /> void searchToLocalTime( int position);<br /> void reset();<br /> void release();<br /> void replaceCurrentItem(MediaResource source);<br /> <br /> <br /> <br /> <br /> <br /> <br /> attribut en lecture seule TimeRange playbackRange;<br /> attribut en lecture seule TimeRange Sekable;&lt;a 17/&gt; attribut readonly doublon currentTime ;<br /> attribut readonly doublon localTime ;<br /> attribut readonly TimeRange bufferedRange ;<br /> attribut readonly DRMManager drmManager ;<br /> attribut readonly MediaPlayerItem currentItem;<br /> a23/&gt; // PlayerState<br /> const unsigned short PLAYER_STATE_IDLE;<br /> const unsigned short PLAYER_STATE_INITIALIZING;<br /> const unsigned short PLAYER_STATE_INITIALIZED;<br /> const unsigned PLAYER_STATE_PREPARING;<br /> const unsigned short PLAYER_STATE_PREPARRED;<br /> const unsigned short PLAYER_STATE_PLAYING;<br /> const unsigned short PLAYER_STATE_PAUSED;<br /> const unsigned short PLAYER_PREPLAYER STATE_SEEKING;<br /> const unsigned short PLAYER_STATE_COMPLETE;<br /> const short PLAYER_STATE_ERROR;<br /> const short PLAYER_STATE_RELEASED;<br /> const short PLAYER_STATUS non signé_SUSPENDED;<br /> attribut readonly non signé état court ;<br /> <br /> attribut volume court non signé ;<br /> attribut ABRControlParameters abrControlParameters ;<br /> attribut BufferControlParameters bufferControlParameters ;<br /> &lt;a4 2/&gt; readonly non signé short VISIBLE; //Pour la visibilité CC<br /> lecture seule non signée short INVISIBLE ; //Pour la visibilité CC<br /> attribut non signé ccVisibility court ;<br /> attribut TextFormat ccStyle ;<br /> attribut readonly attribut PlaybackMetrics playbackMetrics ;<br /> attribut MediaPlayerConfig mediaPlayerConfig ;<br /> taux de doublon d'attributs.&lt;a4 9/&gt; attribut vue MediaPlayerView ;<br /> attribut readonly Chroneline ;<br /> <br /> <br /> };<br /><br /><br /><br /></p> </td> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayerStatus<br /> {<br /> // PlayerStatus<br /> const unsigned short PLAYER_STATUS_IDLE;<br /> const short non signé PLAYER_STATUS_INITIALIZING;<br /> const unsigned short PLAYER_STATUS_INITIALIZED;<br /> const unsigned short PLAYER_STATUS_PREPARING;<br /> const unsigned short PLAYER_STATUS_PREPARED;<br /> const short PLAYER_STATUS_PLAYING;<br /> const unsigned short PLAYER_STATUS_PAUSED;<br /> const short PLAYER_STATUS_SEKING ;<br /> const unsigned short PLAYER_STATUS_COMPLETE ;<br /> const unsigned short PLAYER_STATUS_ERROR ;<br /> const unsigned short PLAYER_STATUS_RELEASED ;<br /> const not signed short PLAYER_STATUS_SST PENDED;<br /> };</p> </td> 
   <td>(Nouveau pour la version 2.0)</td> 
  </tr> 
 </tbody> 
</table>

#### Événements pris en charge par MediaPlayer {#events-supported-by-mediaplayer}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 Nom du Événement</th> 
   <th>Interface 2.0</th> 
   <th> </th> 
   <th>1.3 Nom du Événement</th> 
   <th>1.3 Interface</th> 
  </tr> 
  <tr> 
   <td><p>(supprimé pour la version 2.0)</p> </td> 
   <td> </td> 
   <td> </td> 
   <td>préparé</td> 
   <td>Événement</td> 
  </tr> 
  <tr> 
   <td><p>itemUpdate</p> <p>Lorsqu’un élément du lecteur multimédia est mis à jour.</p> </td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>mis à jour</p> <p>Une fois que le lecteur de médias a mis à jour le média.</p> </td> 
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
   <td>timelineUpdate</td> 
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
   <td>progress</td> 
   <td>ProgressEvent</td> 
  </tr> 
  <tr> 
   <td>bufferingBegin</td> 
   <td>Événement</td> 
   <td> </td> 
   <td>tampon</td> 
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
   <td>réservationatteinte</td> 
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
   <td>CherchePositionAjusté<br /> Lorsque la position de recherche s'ajuste en raison de règles internes ou externes.</td> 
   <td>SeekEvent</td> 
   <td> </td> 
   <td><p>Nouveautés de la version 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>audioUpdate<br /> Lorsqu’un élément du lecteur multimédia est mis à jour. Pour certains flux contenant des pistes audio détectables uniquement au moment de la lecture, ce événement est déclenché lorsque de nouvelles pistes audio sont disponibles.</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>Nouveautés de la version 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>captionsMise à jour <br /> lorsqu’un élément du lecteur multimédia est mis à jour. Pour les flux en direct/linéaires, le client doit périodiquement actualiser la ressource média pour détecter le nouveau contenu disponible. Dans ce cas, certaines caractéristiques du support peuvent changer.</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>Nouveautés de la version 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>masterUpdate <br /> Lorsqu’un élément du lecteur multimédia est mis à jour. Pour les flux en direct/linéaires, le client doit périodiquement actualiser la ressource média pour détecter le nouveau contenu disponible. Dans ce cas, certaines caractéristiques du support peuvent changer.</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>Nouveautés de la version 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>playbackRangeUpdate<br /> Lorsqu’un élément du lecteur multimédia est mis à jour. Pour les flux en direct/linéaires, le client doit périodiquement actualiser la ressource média pour détecter le nouveau contenu disponible. Dans ce cas, certaines caractéristiques du support peuvent changer.</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>Nouveautés de la version 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>timedEvent<br /> Envoyé lorsque des événements temporisés sont générés.</td> 
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
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface ABRControlParameters<br /> {<br /> const unsigned short ABR_POLICY_CONSERVATIVE = 0;<br /> const unsigned short ABR_POLICY_MODERATE = 1;<br /> const unsigned short ABR_POLICY_AGGRESIVE = 2;<br /> <br /> attribut non short abr Stratégie ;<br /> attribut non signé int initialBitRate ;<br /> attribut non signé int minBitRate ;<br /> attribut non signé int maxBitRate ;<br /> const non signé short DEFAULT_ABR_INITIAL_BITRATE ;<br /> const short DEFAULT_ABR_MIN_NON signé BITRATE;<br /> const unsigned short DEFAULT_ABR_MAX_BITRATE;<br /> const ABRPolicy DEFAULT_ABR_POLICY;<br /> };</p> </td> 
   <td><p>interface ABRControlParameters<br /> {<br /> const unsigned short ABR_POLICY_CONSERVATIVE = 0;<br /> const unsigned short ABR_POLICY_MODERATE = 1;<br /> const unsigned short ABR_POLICY_AGGRESIVE = 2;<br /> <br /> attribut non short abr Stratégie ;<br /> attribut non signé int initialBitRate ;<br /> attribut non signé int minBitRate ;<br /> attribut non signé int maxBitRate ;<br /> <br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### BufferControlParameters {#buffercontrolparameters}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface BufferControlParameters<br /> {<br /> attribut doublon initialBufferTime;<br /> attribut doublon playBufferTime;<br /> const doublon DEFAULT_INITIAL_BUFFER_TIME;<br /> const doublon DEFAULT_PLAY_BUFFER_TIME;<br /> ;</p> </td> 
   <td><p>interface BufferControlParameters<br /> {<br /> attribut doublon initialBufferTime;<br /> attribut doublon playBufferTime;<br /> <br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### TextFormat {#textformat}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td>Aucune modification pour la version 2.0</td> 
   <td><p>interface TextFormat<br /> {<br /> // Color<br /> const unsigned short COLOR_DEFAULT = 0;<br /> const unsigned short COLOR_BLACK = 1;<br /> const unsigned short COLOR_GRAY = 2;<br /> const unsigned short COLOR_WHITE = 3;&lt;a 6/&gt; const unsigned short COLOR_BRIGHT_WHITE = 4 ;<br /> const unsigned short COLOR_DARK_RED = 5 ;<br /> const unsigned short COLOR_RED = 6 ;<br /> const unsigned short COLOR_BRIGHT_RED = 7 ; <br /> const unsigned short COLOR_DOR_RED ARK_GREEN = 8 ;<br /> const unsigned short COLOR_GREEN = 9 ;<br /> const unsigned short COLOR_BRIGHT_GREEN = 10 ;<br /> const unsigned short COLOR_DARK_BLUE = 11 ; <br /> const unsigned short COLCOLCO OR_BLUE = 12 ; <br /> const unsigned short COLOR_BRIGHT_BLUE = 13 ;<br /> const unsigned short COLOR_DARK_YELLOW = 14 ; <br /> const unsigned short COLOR_YELLOW = 15 ; <br /> const unsigned short COLOR_BRIGHT_YELLOW = 16 ;<br /> const unsigned short COLOR_DARK_MAGENTA = 17 ;<br /> const unsigned short COLOR_MAGENTA = 18 ; <br /> const unsigned short COLOR_BRIGHT_MAGENTA = 1 9 ; <br /> const unsigned short COLOR_DARK_CYAN = 20 ;<br /> const unsigned short COLOR_CYAN = 21 ; <br /> const unsigned short COLOR_BRIGHT_CYAN = 22 ; <br /> <br /> attribut unsigned short fontColor ;<br /> attribut readonly unsigned short BackgroundColor ;<br /> attribut readonly non signé short fillColor ;<br /> attribut readonly non signé short edgeColor ; <br /> <br /> // Size<br /> const short non signé SIZE_DEZE ULT = 0 ; <br /> const unsigned short SIZE_SMALL = 1 ;<br /> const unsigned short SIZE_MEDIUM = 2 ;<br /> const unsigned short SIZE_LARGE = 3 ; <br /> <br /> attribut readonly unsigned short size ;&lt;aa 38/&gt; <br /> // FontEdge<br /> const unsigned short FONT_EDGE_DEFAULT = 0;<br /> const unsigned short FONT_EDGE_NONE = 1;<br /> const unsigned short FONT_EDGE_RAISED = 2;<br /> const unsigned short FONT_EDGE_DEPRESED = 3 ;<br /> const unsigned short FONT_EDGE_UNIFORM = 4 ;<br /> const unsigned short FONT_EDGE_DROP_SHADOW_LEFT = 5 ; <br /> const unsigned short FONT_EDGE_DROP_DROP ADOW_RIGHT = 6 ; <br /> attribut readonly non signé fontEdge ; <br /> <br /> // Font<br /> const unsigned short FONT_DEFAULT = 0 ; <br /> const unsigned short FONT_MONOSPACED_WITH_SERIFS = 1; a52/&gt; const unsigned short FONT_PROPORTIONAL_WITH_SERIFS = 2 ;<br /> const unsigned short FONT_MONSPACED_WITHOUT_SERIFS = 3 ;<br /> const unsigned short FONT_CASUAL = 4 ;<br /> const unsigned short FONT_CURT SIVE = 5 ; <br /> const unsigned short FONT_SMALL_CAPITALS = 6 ;<br /> readonly attribute unsigned short font ;<br /> readonly attribute unsigned short fontOpacity ;<br /> readonly attribute unsigned short BackgroundOpacity ;<br /> readonly attribute signed short fillOpacity;<br /> attribut readonly non signé short DEFAULT_OPACITY;<br /> };<br /><br /><br /></p> </td> 
  </tr> 
 </tbody> 
</table>

### MediaPlayerItemLoader {#mediaplayeritemloader}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayerItemLoader:<br /> {<br /> void load(MediaResource resource, long resourceId,<br /> ItemLoaderListener listener, <br /> MediaPlayerItemConfig);<br /> void cancel();<br /> attribut readonly MediaPlayerItem currentItem;&lt;a6/ };<br /></p> </td> 
   <td>Nouveautés de la version 2.0</td> 
  </tr> 
  <tr> 
   <td><p>interface ItemLoaderListener<br /> {<br /> //onLoadCompleteCallbackFunc(MediaPlayerItem)<br /> var onLoadCompleteCallbackFunc;<br /> //onErrorCallbackFunc(PSDKErrorCode)<br /> var onErrorCallbackFunc; a5/&gt; }<br /></p> </td> 
   <td>Nouveautés de la version 2.0</td> 
  </tr> 
 </tbody> 
</table>

## Modifications de l’élément d’API des caractéristiques du média pour la version 2.0 {#media-characteristics-api-element-changes-for}

Ces tableaux comparent les éléments d’API caractéristiques du média pour le SDK TVSDK C++ entre les versions 1.3 et 2.0.

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
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayerItem {<br /> attribut readonly MediaResource ;<br /> attribut readonly long resourceId ;<br /> attribut readonly boolean live ;<br /> <br /> attribut readonly boolean hasAlternateAudio ;<br /> attribut readonly AudioTrackList audioTracks ;<br /> attribut readonly audioTrack sélectionné Track;<br /> void selectAudioTrack(AudioTrack track); <br /> <br /> attribut readonly boolean hasClosedCaptions ; <br /> attribut readonly ClosedCaptionsTrackList ClosedCaptionsTracks ;<br /> attribut readonly ClosedCaptionsTrack selectedClosedCaptionsTrack ;<br /> void selectCaptionsTrack(&lt;a 13/&gt; ClosedCaptionsTrack); <br /> <br /> attribut readonly boolean hasTimedMetadata ;<br /> attribut readonly TimedMetadataList timedMetadata ;<br /> attribut readonly boolean dynamic ; <br /> <br /> attribut readonly boolean isProtected ;<br /> attribut readonly DRMMetadataInfoList drmMetadataInfos ;<br /> attribut readonly profils ProfileList ;<br /> Profil d'attribut readonly selectedProfile ;<br /> <br /> attribut readonly boolean trickPlaySupported ;<br /> attribut readonly Tableau availablePlaybackRates ; <br /> attribut readonly float selectedPlaybackRate;<br /> <br /> <br /> attribut readonly MediaPlayer mediaPlayer ;<br /> attribut readonly MediaPlayerItemConfig;<br /> };<br /></p> </td> 
   <td><p>interface MediaPlayerItem {<br /> attribut readonly MediaResource ;<br /> attribut readonly long resourceId ;<br /> attribut readonly boolean live ;<br /> <br /> attribut readonly boolean hasAlternateAudio ;<br /> attribut readonly AudioTrackList audioTracks ;<br /> attribut AudioTrack selectedAudioTrack ; <br /> <br /> <br /> attribut readonly boolean hasClosedCaptions;<br /> attribut readonly ClosedCaptionsTrackList ccTracks;<br /> attribut ClosedCaptionsTrack selectedCCTrack;<br /> <br /> <br /> <br /> attribut readonly boolean hasTimedMetadata ;<br /> attribut readonly TimedMetadataList timedMetadata ;<br /> attribut readonly boolean dynamic ; <br /> <br /> attribut readonly boolean isProtected ;<br /> attribut readonly DRMM etadataInfoList drmMetadataInfos ; <br /> attribut readonly profils ProfileList ; <br /> <br /> <br /> attribut readonly boolean trickPlaySupported ;<br /> attribut readonly Int32Array availablePlaybackRates ;&lt;a22 6/&gt; <br /> attribut readonly StringList adTags;<br /> <br /> attribut readonly MediaPlayer mediaPlayer;<br /> <br /> };<br /></p> </td> 
  </tr> 
 </tbody> 
</table>

### Track / AudioTrack / ClosedCaptionsTrack {#track-audiotrack-closedcaptionstrack}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface Track<br /> {<br /> attribut readonly nom DomString ;<br /> attribut readonly langage DomString ;<br /> attribut readonly boolean default ;<br /> attribut readonly boolean autoSelect ;<br /> }; </p> </td> 
   <td>Nouveautés de la version 2.0</td> 
  </tr> 
  <tr> 
   <td><p>interface AudioTrack : Track<br /> {<br /> attribut readonly nom DomString ; //FromTrack<br /> readonly attribut DomString language;//FromTrack<br /> readonly attribut booléen default ; // De l'attribut Track<br /> readonly booléen autoSelect;//FromTrack<br /> <br /> attribut readonly non signé dans pid ;<br /> };</p> </td> 
   <td><p>interface AudioTrack<br /> {<br /> attribut readonly nom DomString ;<br /> attribut readonly langage DomString ; <br /> attribut readonly boolean default ;<br /> attribut readonly boolean autoSelect ;<br /> attribut readonly boolean forcé ;<br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td>Aucune modification pour la version 2.0</td> 
   <td><p>interface AudioTrackList<br /> {<br /> attribut readonly non signé long ;<br /> getter AudioTrack (index long non signé);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface ClosedCaptionsTrack : Track<br /> {<br /> attribut readonly nom DomString ; //FromTrack<br /> readonly attribut DomString language;//FromTrack<br /> readonly attribut booléen default ; // FromTrack<br /> attribut readonly booléen autoSelect;//FromTrack<br /> <br /> <br /> const unsigned short SERVICE_608_CAPTIONS = 0;<br /> const unsigned short SERVICE_708_CAPTIONS = 1;<br /> const unsigned short SERVICE_WEB_VTT CAPTIONS = 2;<br /> attribut readonly non signé serviceType ;<br /> attribut readonly booléen forcé ;<br /> };</p> </td> 
   <td><p>interface ClosedCaptionsTrack<br /> {<br /> attribut readonly nom DomString ;<br /> attribut readonly langage DomString ;<br /> attribut readonly valeur booléenne par défaut booléenne ; <br /> <br /> <br /> attribut readonly valeur booléenne principal ; <br /> <br /> <br /> &lt;a10/<br /> <br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td>Aucune modification pour la version 2.0</td> 
   <td><p>interface ClosedCaptionsTrackList<br /> {<br /> attribut readonly non signé long ;<br /> get ClosedCaptionsTrack(index long non signé);<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### Profil {#profile}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td>Profil : Aucune modification pour la version 2.0</td> 
   <td><p>profil d'interface<br /> {<br /> attribut readonly non signé int width;<br /> attribut readonly non signé int height;<br /> attribut readonly non signé int bitRate;<br /> }; </p> </td> 
  </tr> 
  <tr> 
   <td>ProfileList : Aucune modification pour la version 2.0</td> 
   <td><p>interface ProfileList<br /> {<br /> attribut readonly non signé long ;<br /> Profil get(index long non signé);<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMMetadataInfo {#drmmetadatainfo}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><strong>DRMMetadataInfo</strong> : Aucune modification pour la version 2.0</td> 
   <td><p>interface DRMMetadataInfo<br /> { <br /> attribut readonly métadonnées DRMMetadata;<br /> attribut readonly long prefetchTimestamp;<br /> attribut readonly TimeRange;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>DRMMetadataInfoList</strong> : Aucune modification pour la version 2.0</td> 
   <td><p>interface DRMMetadataInfoList<br /> {<br /> attribut readonly non signé long ;<br /> getter DRMMetadataInfo(index long non signé);<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

## Mappage des erreurs C++ à des exceptions dans différentes langues {#mapping-c-errors-to-exceptions-in-different-languages}

Vous pouvez mapper des codes d’erreur C++ à des exceptions dans différentes langues.

Le PSDK C++ a une stratégie &quot;pas de jeton&quot; pour ses API. La plupart des méthodes API renvoient une valeur PSDKErrorCode pour indiquer si la méthode a bien été exécutée. Les erreurs asynchrones sont signalées par le biais des événements d’erreur.

L’ActionScript et le JAVA PSDK ont une politique différente. La plupart des erreurs renvoient une exception ArgumentError ou IllegalStateException pour indiquer que la partie synchrone de la méthode n&#39;a pas pu être exécutée. Ces exceptions ne sont pas détectées et le code de l’application est responsable du traitement des exceptions. Ils contiennent généralement des informations utiles sur les raisons de l&#39;échec de l&#39;appel de méthode. Par exemple, si la commande prepareToPlay est appelée dans un état non valide, l’exception suivante est levée :

```shell
throw new IllegalStateException("Invalid player state. prepareToPlay method 
must be called only once after replaceCurrentItem or replaceCurrentResource method.");
```

L’ActionScript/JAVA renvoie également des exceptions aux constructeurs pour indiquer que certains objets internes ont été créés de manière incorrecte. Ces exceptions sont gérées en interne et ne sont pas propagées à l’application. Les exceptions seront incluses dans une notification d&#39;avertissement envoyée à la demande.

Par exemple, si aucun fichier multimédia valide n’a été trouvé pour la réponse à la publicité reçue, aucun objet ou publicité publicitaire valide ne peut être créé. Par conséquent, aucune publicité n&#39;est placée sur la chronologie et une notification NotificationEvent.OperationFailed est envoyée.

Les codes d’erreur ou d’avertissement reçus de manière asynchrone par le moteur de vidéo d’Adobe (AVE) sont distribués dans l’application en tant que événements normaux. Le événement de notification contient tous les codes d’erreur reçus et toutes les métadonnées supplémentaires, telles que l’URL, l’identifiant de ressource, le nom d’utilisateur, etc. Si l&#39;erreur est grave et que la lecture du média actuel ne peut pas se poursuivre, le événement MediaPlayer transition à l&#39;état ERROR et au rappel onStatusChanged ou MediaPlayerStatusChanged.STATUS_CHANGED est distribué. Si la lecture peut continuer, un événement de notification normal est distribué.

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
   <td>Exception avec le code = 1, description = "INVALID_ARGUMENT" et additionalInfo= &lt;tel que transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECNullPointer</td> 
   <td> </td> 
   <td>IllegalArgumentException</td> 
   <td>ArgumentError</td> 
   <td>Exception avec le code = 2, description = "GENERIC_ERROR" et additionalInfo= &lt;transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECIllegalState</td> 
   <td> </td> 
   <td>IllegalStateException</td> 
   <td>IllegalStateException</td> 
   <td>Exception avec le code = 3, description = "ILLEGAL_STATE" et additionalInfo= &lt;transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECIInterfaceNotFound</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec le code = 4, description = "GENERIC_ERROR" et additionalInfo= &lt;transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECCreationFailed</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec le code = 5, description = "CREATION_FAILED" et additionalInfo= &lt;tel que transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECUnsupportedOperation</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec le code = 5, description = "CREATION_FAILED" et additionalInfo= &lt;tel que transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kCEDataNotAvailable</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec le code = 7, description = "DATA_NOT_AVAILABLE" et additionalInfo= &lt;tel que transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECSeekError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec le code = 8, description = "SEEK_ERROR" et additionalInfo= &lt;transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECUnsupportedFeature</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec le code = 9, description = "UNSUPPORTED_FEATURE" et additionalInfo= &lt;tel que transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECRangeError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec le code = 10, description = "RANGE_ERROR" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception</td> 
  </tr> 
  <tr> 
   <td>kECCodecNotSupported</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec le code = 11, description = "CODEC_NOT_SUPPORTED" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECMediaError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec le code = 12, description = "MEDIA_ERROR" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECNetworkError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec le code = 13, description = "NETWORK_ERROR" et additionalInfo= &lt;tel que transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECGenericError</td> 
   <td> </td> 
   <td>MediaPlayerNotification.Error ou MediaPlayerNotification.Warning</td> 
   <td>MediaError ou NotificationEvent</td> 
   <td>Exception avec le code = 14, description = "GENERIC_ERROR" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECInvalidSeekTime</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec le code = 15, description = "INVALID_SEEK_TIME" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECAudioTrackError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec le code = 16, description = "AUDIO_TRACK_ERROR" et additionalInfo= &lt;tel que transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECAccessFromDifferent<p>ThreadError</p> </td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec le code = 17, description = "GENERIC_ERROR" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECElementNotFound</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec le code = 18, description = "GENERIC_ERROR" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception</td> 
  </tr> 
  <tr> 
   <td>kECNotImplémenté</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec le code = 19, description = "GENERIC_ERROR" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECPlaybackOperationFailed</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>Exception avec le code = 200, description = "PLAYBACK_OPERATION_FAILED" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
  <tr> 
   <td>kECNativeWarning</td> 
   <td> </td> 
   <td>MediaPlayerNotification.Warning</td> 
   <td>NotificationEvent</td> 
   <td>Exception avec le code = 201, description = "NATIVE_WARNING" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception</td> 
  </tr> 
  <tr> 
   <td>kECAdResolverFailed</td> 
   <td> </td> 
   <td>MediaPlayerNotification.Warning</td> 
   <td>-</td> 
   <td>Exception avec le code = 202, description = "AD_RESOLVER_FAILED" et additionalInfo= &lt;comme transmis par la méthode qui a déclenché cette exception&gt;</td> 
  </tr> 
 </tbody> 
</table>

## Modifications des éléments de l’API Utilitaire et Assistant pour la version 2.0 {#utility-and-helper-api-element-changes-for}

Ces tableaux comparent les éléments de l’API Utilitaire et Aide pour le SDK JavaScript TVSDK entre les versions 1.3 et 2.0.

Tableaux dans cette rubrique :

* Version
* TimeRange
* QOSProvider
* Informations sur le périphérique
* LoadInfo
* Vue
* PlaybackInformation

### Version {#version}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface Version<br /> {<br /> attribut readonly version de DomString ;<br /> attribut readonly description de DomString ;<br /> attribut readonly long major ;<br /> attribut readonly long minor ;<br /> attribut readonly long revision ;<br /> attribut readonly long apiVersion ;<br /> };</p> </td> 
   <td><p>interface Version<br /> {<br /> attribut readonly version de DomString ;<br /> attribut readonly description de DomString ;<br /> attribut readonly majeur de DomString ;<br /> attribut readonly mineur de DomString ;<br /> attribut readonly révision de DomString ;<br /> attribut readonly api de DomString ;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### Période {#timerange}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td>Aucune modification pour la version 2.0</td> 
   <td><p>interface TimeRange<br /> {<br /> attribut readonly non signé long begin;<br /> attribut readonly non signé long end;<br /> attribut readonly non signé long duration;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### QOSProvider {#qosprovider}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td>Aucune modification pour la version 2.0</td> 
   <td><p>interface QOSProvider<br /> {<br /> void attachementMediaPlayer(MediaPlayer player);<br /> void detachMediaPlayer();<br /> <br /> attribut lecture seule DeviceInformation deviceInformation;<br /> attribut lecture seule PlaybackInformation playbackInformation;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DeviceInformation {#deviceinformation}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface DeviceInformation<br /> {<br /> attribut readonly DomString os;<br /> <br /> <br /> <br /> attribut readonly DomString id;<br /> attribut readonly int densitéDPI;<br /> attribut readonly int heightPixels;<br /> attribut readonly int width int widthPixels;<br /> attribut readonly booléen searchToKeyFrame;<br /> };</p> </td> 
   <td><p>interface DeviceInformation<br /> {<br /> attribut readonly DomString os;<br /> attribut readonly int sdk;<br /> attribut readonly modèle DomString;<br /> attribut readonly fabricant DomString;<br /> attribut readonly DomString id;<br /> attribut readonly int densitéDPI;<br /> attribut int heightPixels ; <br /> attribut readonly int widthPixels ;<br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### LoadInfo {#loadinfo}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td>Aucune modification pour la version 2.0</td> 
   <td><p>interface LoadInfo<br /> {<br /> attribut readonly DomString url;<br /> attribut readonly int size;<br /> attribut readonly downloaddoublonDuration;<br /> attribut readonly int periodIndex;<br /> attribut readonly mediaDuration du doublon ;<br /> attribut readonly short TRACK_TYPE_FRAGMENT;<br /> attribut readonly short TRACK_TYPE_TRACK;<br /> attribut readonly short TRACK_TYPE_MANIFEST;<br /> type abrégé d'attribut readonly;<br /> attribut readonly DomString trackName;<br /> attribut readonly DomString trackType;<br /> attribut readonly int trackIndex;&lt;atrackIndex; 13/&gt; };<br /></p> </td> 
  </tr> 
 </tbody> 
</table>

### Vue {#view}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td>Aucune modification pour la version 2.0</td> 
   <td><p>vue d'interface<br /> {<br /> attribut readonly non signé x ;<br /> attribut readonly non signé y ;<br /> attribut readonly non signé short width ;<br /> attribut readonly non signé short height ;<br /> <br /> void setSize(unsigned short width, unsigned short height);<br /> void setPos(unsigned unsigned) short x, unsigned short y);<br /> }</p> </td> 
  </tr> 
 </tbody> 
</table>

### PlaybackInformation {#playbackinformation}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface PlaybackInformation<br /> {<br /> attribut readonly tempsdoublonToFirstByte;<br /> temps de doublon d'attribut readonlyToLoad;<br /> temps de doublon d'attribut readonlyToStart;<br /> temps de doublon d'attribut readonlyToFail;<br /> attribut readonly int totalSecondsPlayed;&lt;a&lt;a/&gt; attribut readonly int totalSecondsSpent;<br /> attribut readonly doublon frameRate;<br /> attribut readonly int droppedFrameCount;<br /> attribut readonly int percevoirBandwidth;<br /> attribut readonly int bitrate;<br /> attribut readonly doublon bufferTime;<br /> attribut readonly readonly attribut int bufferLength;<br /> attribut readonly attribut int emptyBufferCount;<br /> attribut readonly doublon bufferingTime;<br /> };<br /></p> </td> 
   <td><p>interface PlaybackInformation<br /> {<br /> attribut readonly tempsdoublonToFirstByte;<br /> temps de doublon d'attribut readonlyToLoad;<br /> temps de doublon d'attribut readonlyToStart;<br /> temps de doublon d'attribut readonlyToFail;<br /> attribut readonly int totalSecondsPlayed;&lt;a&lt;a/&gt; attribut readonly int totalSecondsSpent;<br /> attribut readonly doublon frameRate;<br /> attribut readonly int droppedFrameCount;<br /> <br /> attribut readonly int bitrate;<br /> attribut readonly bufferTime de doublon ;<br /> attribut readonly int bufferLength; a13/&gt; attribut readonly int emptyBufferCount;<br /> attribut readonly doublon bufferingTime;<br /> };<br /><br /></p> </td> 
  </tr> 
 </tbody> 
</table>

## Ressources utiles {#helpful-resources}

* Consultez la documentation d’aide complète à la [page Apprentissage et support Adobe Primetime](https://helpx.adobe.com/support/primetime.html).
