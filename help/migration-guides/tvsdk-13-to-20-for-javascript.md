---
title: Conversion de TVSDK - 1.3 à 2.0 pour JavaScript
seo-title: Conversion de TVSDK - 1.3 à 2.0 pour JavaScript
description: De nombreuses signatures de méthode et noms d'éléments d'API ont changé pour la version 2.0. Consultez ces tableaux pour voir tous les détails de modification de l'API.
seo-description: De nombreuses signatures de méthode et noms d'éléments d'API ont changé pour la version 2.0. Consultez ces tableaux pour voir tous les détails de modification de l'API.
uuid: d2d1742d-c90c-43f5-94fc-8c4a57cb8ed4
contentOwner: asgupta
products: SG_PRIMETIME
topic-tags: migration
discoiquuid: c732f54d-116c-43f3-bec4-5e71af208426
translation-type: tm+mt
source-git-commit: e644e8497e118e2d03e72bef727c4ce1455d68d6

---


# Conversion de TVSDK - 1.3 à 2.0 pour JavaScript {#tvsdk-conversion-to-for-javascript}

De nombreuses signatures de méthode et noms d&#39;éléments d&#39;API ont changé pour la version 2.0. Consultez ces tableaux pour voir tous les détails de modification de l&#39;API.

## Mise en oeuvre des fonctions de rappel dans JavaScript {#implement-callback-functions-in-javascript}

Les commentaires dans la documentation de la méthode suggèrent la signature des rappels que vous devez implémenter.

Pour JavaScript, la syntaxe de l’API est basée sur l’ID Web. Pour une interface TVSDK, les noms des méthodes sont appelés *methodName*(). Pour que les méthodes soient implémentées par votre application, un attribut de lecture/écriture appelé ** methodNameCallbackFunc est ajouté à l&#39;interface et votre application doit le définir pour qu&#39;il pointe vers une fonction qui implémente la méthode. Par exemple :

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
   <td><p> <strong>TimedMetadata</strong>: interface TimedMetadata {<br /> const unsigned short METADATA_TYPE_TAG = 0; <br /> const unsigned short METADATA_TYPE_ID3 = 1; <br /> readonly attribut non signé short type ; <br /> readonly attribut long ;<br /> readonly attribut DomString id;<br /> readonly attribut DomString name;<br /> readonly attribut contenu DomString ; <br /> readonly, attribut, métadonnées d'objet ;<br /> }; </p> </td> 
   <td><p>interface TimedMetadata {<br /> const unsigned short METADATA_TYPE_TAG = 0;<br /> const unsigned short METADATA_TYPE_ID3 = 1;<br /> readonly attribut unsigned short metadataType ;<br /> readonly attribut long ;<br /> readonly attribut long id ;<br /> readonly attribut DomString name;<br /> <br /> readonly, attribut, métadonnées d'objet ;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>TimedMetadataList</strong>: (Aucun changement pour la version 2.0)</td> 
   <td><p>interface TimedMetadataList {<br /> readonly attribut non signé long ;<br /> getter TimedMetadata(index long non signé);<br /> };</p> </td> 
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
   <td><p>Interface AdSignalingMode { <br /> const unsigned short MODE_DEFAULT, <br /> const unsigned short MODE_MANIFEST_CUES, <br /> const short non signé MODE_SERVER_MAP, const <br /> unsigned short MODE_CUSTOM_RANGES <br /> };</p> </td> 
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
   <td><p>Interface AdvertisingMetadata { <br /> attribut AdSignalingMode ; <br /> attribut AdBreakWatchedPolicy adBreakAsWatched ; <br /> attribut booléen livePreroll ; <br /> attribut booléen delayAdLoading ; <br /> };</p> </td> 
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
   <td><p>Interface CustomRangeMetadata { <br /> const non signé short TYPE_MARK_RANGE; <br /> const unsigned short TYPE_DELETE_RANGE; <br /> const unsigned short TYPE_REPLACE_RANGE; <br /> attribut de type court non signé ; <br /> attribut booléen modifySeekPosition; <br /> attribut TimeRangeList timeRangeList ; <br /> };</p> </td> 
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
   <td><p>interface ReplaceTimeRange { <br /> attribut non signé long begin; <br /> readonly attribut non signé long end; <br /> attribut non signé longue durée ; <br /> attribut unsigned long replaceDuration ; <br /> };</p> </td> 
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
   <td><p>Interface Placement { <br /> const non signé short TYPE_MID_ROLL; <br /> const unsigned short TYPE_PRE_ROLL; <br /> const unsigned short TYPE_POST_ROLL; <br /> const unsigned short TYPE_SERVER_MAP; <br /> const unsigned short TYPE_CUSTOM_RANGE;<br /> readonly attribut non signé short type ; <br /> readonly attribut long ; <br /> attribut readonly longue durée ; <br /> const unsigned short MODE_DEFAULT; <br /> const unsigned short MODE_INSERT; <br /> const unsigned short MODE_REPLACE; <br /> const unsigned short MODE_DELETE; <br /> const unsigned short MODE_MARK; <br /> const unsigned short MODE_FREE_REPLACE; <br /> readonly attribut unsigned short mode ; <br /> readonly, attribut plage TimeRange ; <br /> };</p> </td> 
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
   <td><p>interface Opportunity { <br /> readonly attribut DomString id; <br /> attribut readonly Placement placement ; <br /> Paramètres d’objet d’attribut readonly ; <br /> readonly, attribut Object customParameters ; <br /> }; </p> </td> 
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
   <td><p>interface Reservation { <br /> readonly attribut plage TimeRange; <br /> readonly attribut long hold ; <br /> }; </p> </td> 
   <td> (Nouveau pour la version 2.0)</td> 
  </tr> 
 </tbody> 
</table>

### Journal / TimelineItem / TimelineMarker {#timeline-timelineitem-timelinemarker}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>API 1.3</th> 
  </tr> 
  <tr> 
   <td><p><strong>Chronologie</strong>: interface Timeline <br /> { readonly attribut TimelineMarkerList timelineMarkers ; <br /> readonly attribut TimelineItemList timelineItems ; <br /> doublon convertToLocalTime( doublon); <br /> doublon convertToVirtualTime( doublon); <br /> };</p> </td> 
   <td><p>interface Timeline {<br /> readonly attribut TimelineMarkerList timelineMarkers ;<br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p> <strong>TimelineItem</strong>: interface TimelineItem :<br /> TimelineMarker {<br /> readonly attribut long id ; <br /> readonly attribut TimeRange virtualRange; <br /> readonly attribut TimeRange localRange; <br /> readonly attribut boolean watched; <br /> readonly, attribut booléen temporaire ; <br /> }; </p> </td> 
   <td>(Nouveau pour la version 2.0)</td> 
  </tr> 
  <tr> 
   <td><strong>TimelineMarker</strong>: (Aucun changement pour la version 2.0)</td> 
   <td><p>interface TimelineMarker {<br /> readonly attribut doublon time;<br /> durée du doublon d'attribut en lecture seule ;<br /> };</p> </td> 
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
   <td><p>interface AdBreak {<br /> <br /> <br /> <br /> readonly attribut doublon duration ;<br /> readonly attribut ads AdList ;<br /> <br /> <br /> readonly, attribut AdInsertionType insertType ;<br /> }; </p> </td> 
   <td><p>interface AdBreak {<br /> readonly attribut doublon time;<br /> readonly, attribut doublon replaceDuration ;<br /> <br /> durée du doublon d'attribut en lecture seule ;<br /> readonly attribut AdList adList ;<br /> <br /> readonly attribut données DomString ;<br /> <br /> }; </p> </td> 
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
   <td><p> <strong>Publicité</strong>: interface Ad {<br /> readonly attribut AdAsset primaryAsset ;<br /> readonly attribut AdAssetList CompanionAssets;<br /> <br /> durée du doublon d'attribut en lecture seule ;<br /> readonly attribut DomString id;<br /> const unsigned short ADTYPE_LINEAR = 0;<br /> const unsigned short ADTYPE_NONLINEAR = 1;<br /> <br /> readonly attribut unsigned short adType ;<br /> readonly, attribut AdInsertionType adInsertionType ; <br /> <br /> readonly attribut booléen cliquable ; <br /> readonly, attribut booléen isCustomAdMarker;<br /> }; </p> </td> 
   <td><p>interface Ad {<br /> readonly attribut AdAsset primaryAsset ;<br /> readonly attribut AdAssetList CompanionAssets;<br /> <br /> durée du doublon d'attribut en lecture seule ;<br /> readonly attribut DomString id;<br /> const unsigned short ADTYPE_LINEAR = 0;<br /> const unsigned short ADTYPE_NONLINEAR = 1;<br /> <br /> readonly attribut non signé short type ;<br /> readonly, attribut AdInsertionType insertType ; <br /> readonly, attribut suivi d'objet Object ;<br /> <br /> <br /> }; </p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdAsset</strong>: (Aucun changement pour la version 2.0)</td> 
   <td><p>interface AdAsset {<br /> readonly attribut DomString id;<br /> durée du doublon d'attribut en lecture seule ;<br /> readonly, attribut MediaResource ;<br /> readonly attribut AdClick adClick ;<br /> readonly, attribut, métadonnées d'objet ;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdClick</strong>: (Aucun changement pour la version 2.0)</td> 
   <td><p>interface AdClick {<br /> readonly attribut DomString id;<br /> readonly attribut DomString title;<br /> readonly attribut URL DomString ;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdList</strong>: (Aucun changement pour la version 2.0)</td> 
   <td><p>interface AdList {<br /> readonly attribut unsigned long length ;<br /> getter Ad(index long non signé);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdAssetList</strong>: (Aucun changement pour la version 2.0)</td> 
   <td><p>interface AdAssetList {<br /> attribut readonly non signé long ;<br /> getter AdAsset(index long non signé);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p><strong>AdBannerAsset</strong>: interface AdBannerAsset : AdAsset<br /> {<br /> readonly attribut int width;<br /> readonly attribute int height;<br /> readonly, attribut DomString staticUrl;<br /> readonly attribut DomString height;<br /> readonly attribut Largeur de DomString ;<br /> };</p> </td> 
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
   <td><p> <strong>AdBreakTimelineItem</strong>: interface AdBreakTimelineItem : TimelineItem { <br /> attribut readonly AdBreak adBreak; <br /> readonly attribut éléments AdTimelineItemList ; <br /> }; </p> </td> 
   <td> (Nouveau pour la version 2.0)</td> 
  </tr> 
  <tr> 
   <td><p><strong>AdTimelineItem</strong>: interface AdTimelineItem : TimelineItem { <br /> attribut readonly AdBreak adBreak; <br /> readonly attribut publicité ; <br /> }; </p> </td> 
   <td> (Nouveau pour la version 2.0)</td> 
  </tr> 
  <tr> 
   <td><p><strong>AdBreakTimelineItemList</strong>: interface AdBreakTimelineItemList { <br /> attribut readonly non signé long ; <br /> getter AdBreakTimelineItem (index lo ng non signé); <br /> };</p> </td> 
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
   <td><p>interface AdBreakPolicy {<br /> readonly attribut short AD_BREAK_POLICY_SKIP;<br /> readonly attribut short AD_BREAK_POLICY_PLAY;<br /> readonly attribut short AD_BREAK_POLICY_REMOVE;<br /> readonly attribut short AD_BREAK_POLICY_REMOVE_AFTER_PLAY;<br /> };</p> </td> 
   <td><p> interface AdPolicyConstants {<br /> readonly attribut short AD_BREAK_POLICY_SKIP;<br /> readonly attribut short AD_BREAK_POLICY_PLAY;<br /> readonly attribut short AD_BREAK_POLICY_REMOVE;<br /> readonly attribut short AD_BREAK_POLICY_REMOVE_AFTER_PLAY;<br /> ...</p> </td> 
  </tr> 
  <tr> 
   <td><p> interface AdBreakWatchedPolicy {<br /> readonly attribut short AD_BREAK_AS_WATCHED_ON_BEGIN;<br /> readonly attribut short AD_BREAK_AS_WATCHED_ON_END;<br /> readonly attribut short AD_BREAK_AS_WATCHED_NEVER;<br /> }; </p> </td> 
   <td><p> ...<br /> readonly attribut short AD_BREAK_AS_WATCHED_ON_BEGIN ;<br /> readonly attribut short AD_BREAK_AS_WATCHED_ON_END;<br /> readonly attribut short AD_BREAK_AS_WATCHED_NEVER;<br /> ...</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicy {<br /> readonly attribut short AD_POLICY_PLAY;<br /> readonly attribut short AD_POLICY_PLAY_FROM_AD_BEGIN ;<br /> readonly attribut short AD_POLICY_PLAY_FROM_AD_BREAK_BEGIN ; readonly attribut short AD_POLICY_SKIP_TO_NEXT_AD_IN_BREAK ;<br /> <br /> readonly attribut short AD_POLICY_SKIP_AD_BREAK ;<br /> };</p> </td> 
   <td><p> ... <br /> readonly attribut short AD_POLICY_PLAY;<br /> readonly attribut short AD_POLICY_PLAY_FROM_AD_BEGIN ;<br /> readonly attribut short AD_POLICY_PLAY_FROM_AD_BREAK_BEGIN ;<br /> readonly attribut short AD_POLICY_SKIP_TO_NEXT_AD_IN_BREAK ;<br /> readonly attribut short AD_POLICY_SKIP_AD_BREAK ;<br /> ...</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicyMode {<br /> readonly attribut short AD_POLICY_MODE_PLAY;<br /> readonly attribut short AD_POLICY_MODE_SEEK;<br /> readonly attribut short AD_POLICY_MODE_TRICKPLAY;<br /> };</p> </td> 
   <td><p> ...<br /> readonly attribut short AD_POLICY_MODE_PLAY;<br /> readonly attribut short AD_POLICY_MODE_SEEK;<br /> readonly attribut short AD_POLICY_MODE_TRICKPLAY;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicyInfo {<br /> readonly attribut AdBreakTimelineItemList <br /> adBreakTimelineItems;<br /> readonly attribut AdTimelineItem adTimelineItem ;<br /> readonly attribut doublon currentTime ;<br /> readonly attribut doublon searchToTime ;<br /> taux de doublon des attributs en lecture seule ;<br /> readonly attribut short mode ; //AdPolicyMode<br /> };</p> </td> 
   <td><p>interface AdPolicyInfo {<br /> readonly attribut AdBreakPlacementList <br /> adBreakPlacements ;<br /> readonly attribut publicité ;<br /> readonly attribut doublon currentTime ;<br /> readonly attribut doublon searchToTime ;<br /> taux de doublon des attributs en lecture seule ;<br /> readonly attribut short mode ; //AdPolicyMode<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicySelector {<br /> /**<br /> * AdbreakPolicy selectPolicyForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribut Objet selectPolicyForAdBreakCallbackFunc;<br /> /**<br /> * AdBreakTimelineItemList selectAdBreaksToPlay(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribut Objet selectAdBreaksToPlayCallbackFunc;<br /> /**<br /> * AdPolicy selectPolicyForSeekIntoAd(AdPolicyInfo adPolicyInfo);<br /> */<br /> attribut Objet selectPolicyForSeekIntoAdCallbackFunc; <br /> /**<br /> * AdBreakWatchedPolicy selectWatchedPolicyForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribut Objet selectWatchedPolicyForAdBreakCallbackFunc;<br /> };</p> </td> 
   <td><p>interface AdPolicySelector {<br /> /**<br /> * AdbreakPolicy selectPolicyForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribut Objet selectPolicyForAdBreakFuncCallback ;<br /> /**<br /> * AdBreakPlacementList selectAdBreaksToPlay(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribut Objet selectAdBreaksToPlayCallback ;<br /> /**<br /> * AdPolicy selectPolicyForSeekIntoAd(AdPolicyInfo adPolicyInfo);<br /> */<br /> attribut Objet selectPolicyForSeekIntoAdCallback ; <br /> /**<br /> * AdBreakAsWatched selectWatchedPolicyForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribut Objet selectWatchedPolicyForAdBreakCallback ;<br /> };</p> </td> 
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
   <td><p>interface TimelineOperation { <br /> attribut readonly Placement placement ; <br /> };</p> </td> 
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
   <td><p>interface AdBreakPlacement : TimelineOperation {<br /> readonly attribute AdBreak adBreak ;<br /> attribut readonly Placement placement ; // De TimelineOperation<br /> readonly attribut doublon time ;<br /> durée du doublon d'attribut en lecture seule ;<br /> };</p> </td> 
   <td><p>interface AdBreakPlacement {<br /> readonly attribut AdBreak adBreak ;<br /> attribut readonly Placement placement ;<br /> délai de doublon de l'attribut readonly ;<br /> durée du doublon d'attribut en lecture seule ;<br /> };</p> </td> 
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
   <td><p>interface Paramètres d’audience : AdvertisingMetadata { <br /> , attribut DomString zoneId; <br /> attribut DomString mediaId; <br /> attribut DomString defaultMediaId ; <br /> attribut Domaine DomString ; <br /> attribut Objet targetInfo ; <br /> attribute Object customParameters ; <br /> attribut Boolean creativePackingEnabled;<br /> attribut Boolean showStaticBanners ;<br /> };</p> </td> 
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
   <td><p>interface MediaPlayerItemConfig {<br /> attribut ContentFactory adFactory ;<br /> attribut StringList subscriptionTags ;<br /> <br /> attribut StringList adTags;<br /> <br /> <br /> attribut AdSignalingMode adSignalingMode ;<br /> attribut CustomRangeMetadata customRangeMetadata ;<br /> attribut NetworkConfiguration networkConfiguration ;<br /> attribut AdvertisingMetadata AdvertisingMetadata ;<br /> attribut Boolean useHardwareDecoder;<br /> };</p> </td> 
   <td><p>interface MediaPlayerConfig {<br /> <br /> <br /> <br /> attribut StringList adTags;<br /> attribut StringList subscribedTags ;<br /> attribut MediaPlayerClientFactory clientFactory ;<br /> <br /> <br /> <br /> <br /> <br /> };</p> </td> 
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
   <td><p>interface ContentFactory {<br /> /*<br /> * AdPolicySelector retrieveAdPolicySelector(<br /> * élément MediaPlayerItem);<br /> */<br /> attribut Object retrieveAdPolicySelectorCallbackFunc ;<br /> };</p> </td> 
   <td><p>interface MediaPlayerClientFactory {<br /> /*<br /> * AdPolicySelector retrieveAdPolicySelector(<br /> * élément MediaPlayerItem);<br /> */<br /> attribut Object retrieveAdPolicySelectorFunc ;<br /> };</p> </td> 
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
   <td><p>interface NetworkConfiguration<br /> {<br /> attribut booléen forceNativeNetworking;<br /> attribut booléen useRedirectUrl;<br /> attribut Object cookieHeader;<br /> attribut booléen readSetCookieHeader;<br /> attribut int masterUpdateInterval; <br /> attribut booléen useCookieHeaderForAllRequests ;<br /> attribut int readLimit;<br /> };</p> </td> 
   <td>Dans la version 1.3, certaines de ces fonctionnalités ont été fournies par MetadataKeys.</td> 
  </tr> 
 </tbody> 
</table>

## Modifications des éléments de l’API DRM pour la version 2.0 {#drm-api-element-changes-for}

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
   <td>L’application doit appeler AdobePSDK.initiateDRMWorkflow pour lancer le processus DRM. Sans cet appel, les vidéos DRM ne seront pas lues.<p>interface AdobePSDK<br /> {<br /> void initiateDRMWorkFlow(<br /> DomString appStoratePath, <br /> DomString publisherId, <br /> DomString appId, <br /> DomString appVersion, <br /> booléen privacyModeOn);<br /> };</p> </td> 
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
   <td><p>interface DRMMetadata<br /> {<br /> readonly attribut DomString serverUrl;<br /> readonly, attribut DomString licenseId ;<br /> readonly, attribut stratégies DRMPolicyArray ; <br /> };</p> </td> 
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
   <td><p>interface DRMPlaybackTimeWindow {<br /> readonly attribut int playbackPeriodInSeconds;<br /> readonly attribut long playbackStartDate ;<br /> readonly attribut long playbackEndDate ;<br /> };</p> </td> 
   <td><p>interface DRMPlaybackTimeWindow {<br /> readonly attribut int periodInSeconds;<br /> readonly attribut int startDate ;<br /> readonly attribut int endDate ;<br /> };</p> </td> 
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
   <td><p>interface DRMLicense {<br /> readonly attribut Uint8Array bytes;<br /> readonly attribut Date licenseStartDate ;<br /> readonly attribut Date licenseEndDate ;<br /> readonly, attribut Date offlineStorageStartDate ;<br /> readonly, attribut Date offlineStorageEndDate ; <br /> readonly, attribut DomString serverUrl;<br /> readonly attribut DomString licenseID ;<br /> readonly attribut DomString policyID;<br /> readonly, attribut DRMPlaybackTimeWindow playbackTimeWindow ;<br /> readonly, attribut Object customProperties;<br /> }; </p> </td> 
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
   <td><p>interface DRMLicenseDomain {<br /> readonly attribut DomString authenticationDomain;<br /> readonly, attribut DRMAuthenticationMethod authenticationMethod ; <br /> readonly, attribut DomString serverUrl;<br /> };</p> </td> 
   <td><p>interface DRMLicenseDomain {<br /> readonly attribut DomString authDomain;<br /> readonly, attribut DRMAuthenticationMethod authMethod ; <br /> readonly, attribut DomString serverURL;<br /> };</p> </td> 
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
   <td><p>interface DRMPolicy<br /> {<br /> readonly attribut DomString authenticationDomain;<br /> readonly, attribut DRMAuthenticationMethod authenticationMethod ;<br /> <br /> readonly attribut DomString displayName;<br /> readonly, attribut DRMLicenseDomain licenseDomain;<br /> };</p> </td> 
   <td><p>interface DRMPolicy<br /> {<br /> readonly attribut DomString authDomain;<br /> readonly, attribut DRMAuthenticationMethod authMethod ;<br /> readonly attribut DomString dispName;<br /> readonly, attribut DRMLicenseDomain licenseDomain;<br /> };</p> </td> 
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
   <td><p>interface DRMManager : EventTarget {<br /> void acquisitionLicense(DRMMetadata metadata, <br /> paramètre DRMAcquireLicenseSettings, <br /> écouteur DRMAquireLicenseListener);<br /> void acquisitionPreviewLicense(DRMMetadata metadata, <br /> DRMAquireLicenseListener listener);<br /> void authenticate(DRMMetadata metadata metadata, <br /> DomString url,<br /> DomString &amp;authenticationDomain, <br /> utilisateur DomString, <br /> mot de passe DomString, écouteur <br /> DRMAuthenticateListener);<br /> <br /> DRMMetadata createMetadataFromBytes(tableau Uint8Array, écouteur DRMErrorListener<br /> );<br /> void initialize(écouteur DRMOperationCompleteListener);<br /> attribut long maxOperationTime;<br /> <br /> void joinLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> boolean forceRefresh, <br /> DRMOperationCompleteListener listener);<br /> void leaveLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> écouteur DRMOperationCompleteListener);<br /> <br /> void resetDRM(DRMOperationCompleteListener listener);<br /> void returnLicense(DomString serverURL, <br /> DomString licenseID, <br /> DomString policyID, <br /> boolean commitImmédiatement,<br /> DRMReturnLicenseListener);<br /> void setAuthenticationToken(<br /> métadonnées DRMMetadata, <br /> DomString authenticationDomain, <br /> jeton Uint8Array, <br /> écouteur DRMOperationCompleteListener);<br /> void storeLicenseBytes (Uint8Array licenseBytes, <br /> écouteur DRMOperationCompleteListener);<br /> };</p> </td> 
   <td><p>interface DRMManager : EventTarget {<br /> void acquisitionLicense(DRMMetadata metadata metadata, <br /> paramètre DRMAcquireLicenseSettings, <br /> EventContext eventContext);<br /> void acquisitionPreviewLicense(DRMMetadata metadata, <br /> EventContext eventContext);<br /> void authenticate(DRMMetadata metadata metadata, <br /> DomString url,<br /> DomString &amp;authenticationDomain, <br /> utilisateur DomString, <br /> mot de passe DomString, <br /> EventContext);<br /> <br /> DRMMetadata createMetadataFromBytes(tableau Uint8Array, EventContext eventContext);<br /><br /> void initialize(EventContext eventContext);<br /> attribut long maxOperationTime;<br /> <br /> void joinLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> boolean forceRefresh, <br /> EventContext eventContext);<br /> void leaveLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> EventContext eventContext);<br /> <br /> void resetDRM(EventContext eventContext);<br /> void returnLicense(DomString serverURL, <br /> DomString licenseID,<br /> DomString policyID, <br /> booléen commitImmédiatement,<br /> EventContext);<br /> void setAuthenticationToken(<br /> métadonnées de métadonnées DRMMetadata, <br /> DomString authenticationDomain, <br /> jeton Uint8Array, <br /> EventContext eventContext);<br /> void storeLicenseBytes (Uint8Array licenseBytes, EventContext eventContext); <br /><br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>classe DRMErrorListener : <br /> public psdkutils::PSDKInterfaceWithUserData {<br /> public:<br /> virtual void onDRMError(uint32_t major, <br /> uint32_t mineur, <br /> const psdkutils : PSDKString&amp; errorString, <br /> const psdkutils::PSDKString&amp; errorServerUrl) = 0;<br /> <br /> protected :<br /> virtual ~DRMErrorListener() {}<br /> }</p> </td> 
   <td>Événement / Interface / Description 
    <ul> 
     <li>kEventDRMOperationError<p>/ DRMOperationErrorEvent</p> <p>Lorsqu'une erreur se produit lors de l'une des méthodes asynchrones de DRMManger.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>classe DRMOperationCompleteListener : <br /> public DRMErrorListener {<br /> public :<br /> void virtuel onDRMOperationComplete() = 0;<br /> <br /> protected :<br /> virtual ~DRMOperationCompleteListener() {}<br /> };</p> </td> 
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
   <td><p>classe DRMAuthenticateListener : <br /> public DRMErrorListener {<br /> public :<br /> virtual void onAuthenticationComplete(<br /> psdkutils::PSDKImmutableByteArray* <br /> authenticationToken) = 0;<br /> <br /> protected :<br /> virtual ~DRMAuthenticateListener() {}<br /> }</p> </td> 
   <td>Événement / Interface / Description 
    <ul> 
     <li>kEventDRMAuthenticationComplete<p>/ DRMAuthenticationCompleteEvent</p> <p>Lorsque l'appel de la méthode DRMManager::authenticate est réussi.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>classe DRMAquireLicenseListener : <br /> public DRMErrorListener {<br /> public :<br /> virtual void onLicenseAcquired(const DRMLicense*) = 0;<br /> <br /> protected :<br /> virtual ~DRMAquireLicenseListener() {}<br /> };</p> </td> 
   <td>Événement / Interface / Description 
    <ul> 
     <li>kEventDRMPreviewLicenseAcquired<p>/ DRMLicenseAcquiredEvent</p> <p>Lorsque l'appel de la méthode DRMManager::acquisitionPreviewLicense réussit.</p> </li> 
     <li>kEventDRMLicenseAcquired<p>/ DRMLicenseAcquiredEvent</p> <p>Lorsque l'appel de la méthode DRMManager::acquisitionLicense est réussi.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>classe DRMReturnLicenseListener: <br /> public DRMErrorListener {<br /> public :<br /> void virtuel onLicenseReturnComplete(uint32_t numReturn ) = 0;<br /> <br /> protected :<br /> virtual ~DRMReturnLicenseListener() {}<br /> };</p> </td> 
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
   <td><p>interface MediaResource {<br /> attribut URL DomString ; <br /> attribut de type court non signé ;<br /> les métadonnées d’objet d’attribut ;<br /> const unsigned short TYPE_HLS;<br /> const unsigned short TYPE_HDS;<br /> const unsigned short TYPE_DASH;<br /> const unsigned short TYPE_CUSTOM;<br /> const unsigned short TYPE_UNKNOWN;<br /> };</p> </td> 
   <td><p>interface MediaResource {<br /> attribut URL DomString ;<br /> attribut type DomString ;<br /> les métadonnées d’objet d’attribut ;<br /> <br /> <br /> <br /> <br /> <br /> };</p> </td> 
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
   <td><p>interface MediaPlayer : EventTarget<br /> {<br /> void prepareToPlay( doublon position);<br /> void play();<br /> void pause();<br /> void search( position du doublon);<br /> void searchToLocal( position du doublon);<br /> void reset();<br /> void release();<br /> void replaceCurrentItem(élément MediaPlayerItem);<br /> void replaceCurrentResource(MediaResource, <br /> MediaPlayerItemConfig); <br /> void suspend();<br /> void restore();<br /> void notificationClick();<br /> <br /> readonly, attribut TimeRange playbackRange;<br /> readonly attribut TimeRange seekableRange;<br /> readonly attribut doublon currentTime ;<br /> readonly attribut doublon localTime ;<br /> readonly attribut TimeRange bufferedRange;<br /> readonly attribut DRMManager drmManager ;<br /> readonly attribut MediaPlayerItem currentItem ;<br /> <br /> // PlayerStatus<br /> <br /> <br /> const non signé short PLAYER_STATUS_INITIALIZED;<br /> const unsigned short PLAYER_STATUS_PREPARING;<br /> const unsigned short PLAYER_STATUS_PREPARED;<br /> const unsigned short PLAYER_STATUS_PLAYING;<br /> const unsigned short PLAYER_STATUS_PAUSED;<br /> const unsigned short PLAYER_STATUS_SEEKING;<br /> const unsigned short PLAYER_STATUS_COMPLETE;<br /> const unsigned short PLAYER_STATUS_ERROR;<br /> const unsigned short PLAYER_STATUS_RELEASED;<br /> <br /> readonly attribut statut court non signé ;<br /> <br /> attribut volume court non signé ;<br /> attribut ABRControlParameters abrControlParameters;<br /> attribut BufferControlParameters bufferControlParameters;<br /> <br /> const unsigned short VISIBLE; //Pour le conte de visibilité<br /> CC non signé court INVISIBLE ; //Pour l'attribut de visibilité<br /> CC non signé courte ccVisibility ;<br /> attribut TextFormat ccStyle;<br /> readonly attribut PlaybackMetrics playbackMetrics ;<br /> <br /> taux de doublon d'attributs ;<br /> attribut vue MediaPlayerView ;<br /> readonly attribut Chroneline ;<br /> attribut doublon currentTimeUpdateInterval ; <br /> // cette définition ne sera pas prise en charge pour la version 2.0<br /> };</p> </td> 
   <td><p>interface MediaPlayer : EventTarget<br /> {<br /> void prepareToPlay( int position);<br /> void play();<br /> void pause();<br /> void search( int position);<br /> void searchToLocalTime( int position);<br /> void reset();<br /> void release();<br /> void replaceCurrentItem(source MediaResource);<br /> <br /> <br /> <br /> <br /> <br /> <br /> readonly, attribut TimeRange playbackRange;<br /> readonly attribut TimeRange seekableRange;<br /> readonly attribut doublon currentTime ;<br /> readonly attribut doublon localTime ;<br /> readonly attribut TimeRange bufferedRange;<br /> readonly attribut DRMManager drmManager ;<br /> readonly attribut MediaPlayerItem currentItem ;<br /> <br /> // PlayerState<br /> const unsigned short PLAYER_STATE_IDLE;<br /> const unsigned short PLAYER_STATE_INITIALIZING;<br /> const unsigned short PLAYER_STATE_INITIALIZED;<br /> const unsigned short PLAYER_STATE_PREPARING;<br /> const unsigned short PLAYER_STATE_PREPARED;<br /> const unsigned short PLAYER_STATE_PLAYING;<br /> const unsigned short PLAYER_STATE_PAUSED;<br /> const unsigned short PLAYER_STATE_SEEKING;<br /> const unsigned short PLAYER_STATE_COMPLETE;<br /> const unsigned short PLAYER_STATE_ERROR;<br /> const unsigned short PLAYER_STATE_RELEASED;<br /> const unsigned short PLAYER_STATUS_SUSPENDED;<br /> readonly attribut unsigned short state ;<br /> <br /> attribut volume court non signé ;<br /> attribut ABRControlParameters abrControlParameters;<br /> attribut BufferControlParameters bufferControlParameters;<br /> <br /> readonly non signé short VISIBLE; //Pour les lecteurs de visibilité<br /> CC en lecture seule non signé court INVISIBLE ; //Pour l'attribut de visibilité<br /> CC non signé courte ccVisibility ;<br /> attribut TextFormat ccStyle;<br /> readonly attribut PlaybackMetrics playbackMetrics ;<br /> attribut MediaPlayerConfig mediaPlayerConfig;<br /> taux de doublon d'attributs ;<br /> attribut vue MediaPlayerView ;<br /> readonly attribut Chroneline ;<br /> <br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayerStatus<br /> {<br /> // PlayerStatus<br /> const unsigned short PLAYER_STATUS_IDLE;<br /> const unsigned short PLAYER_STATUS_INITIALIZING;<br /> const unsigned short PLAYER_STATUS_INITIALIZED;<br /> const unsigned short PLAYER_STATUS_PREPARING;<br /> const unsigned short PLAYER_STATUS_PREPARED;<br /> const unsigned short PLAYER_STATUS_PLAYING;<br /> const unsigned short PLAYER_STATUS_PAUSED;<br /> const unsigned short PLAYER_STATUS_SEEKING;<br /> const unsigned short PLAYER_STATUS_COMPLETE;<br /> const unsigned short PLAYER_STATUS_ERROR;<br /> const unsigned short PLAYER_STATUS_RELEASED;<br /> const unsigned short PLAYER_STATUS_SUSPENDED;<br /> };</p> </td> 
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
   <td>adClicked<br /> Lorsque l'utilisateur clique sur une publicité.</td> 
   <td>AdClickedEvent</td> 
   <td> </td> 
   <td><p>Nouveautés de la version 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>profileChangement<br /> lorsque le profil de lecture change.</td> 
   <td>ProfileEvent</td> 
   <td> </td> 
   <td><p>Nouveautés de la version 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>ChercherPositionAjusté<br /> lorsque la position de recherche s'ajuste en raison de règles internes ou externes.</td> 
   <td>SeekEvent</td> 
   <td> </td> 
   <td><p>Nouveautés de la version 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>audioMis à jour<br /> lorsqu’un élément du lecteur multimédia est mis à jour. Pour certains flux contenant des pistes audio détectables uniquement au moment de la lecture, ce événement est déclenché lorsque de nouvelles pistes audio sont disponibles.</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>Nouveautés de la version 2.0</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>légendesMise à jour <br /> lorsqu’un élément du lecteur multimédia est mis à jour. Pour les flux en direct/linéaires, le client doit périodiquement actualiser la ressource média pour détecter le nouveau contenu disponible. Dans ce cas, certaines caractéristiques du support peuvent changer.</td> 
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
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface ABRControlParameters<br /> {<br /> const unsigned short ABR_POLICY_CONSERVATIVE = 0;<br /> const unsigned short ABR_POLICY_MODERATE = 1;<br /> const unsigned short ABR_POLICY_AGGRESIVE = 2;<br /> <br /> attribut unsigned short abrPolicy ;<br /> attribut unsigned int initialBitRate;<br /> attribut unsigned int minBitRate;<br /> attribut unsigned int maxBitRate;<br /> const unsigned short DEFAULT_ABR_INITIAL_BITRATE;<br /> const unsigned short DEFAULT_ABR_MIN_BITRATE;<br /> const unsigned short DEFAULT_ABR_MAX_BITRATE;<br /> const ABRPolicy DEFAULT_ABR_POLICY;<br /> };</p> </td> 
   <td><p>interface ABRControlParameters<br /> {<br /> const unsigned short ABR_POLICY_CONSERVATIVE = 0;<br /> const unsigned short ABR_POLICY_MODERATE = 1;<br /> const unsigned short ABR_POLICY_AGGRESIVE = 2;<br /> <br /> attribut unsigned short abrPolicy ;<br /> attribut unsigned int initialBitRate;<br /> attribut unsigned int minBitRate;<br /> attribut unsigned int maxBitRate;<br /> <br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### ParamètresContrôleTampon {#buffercontrolparameters}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface BufferControlParameters<br /> {<br /> attribut doublon initialBufferTime;<br /> attribut doublon playBufferTime ;<br /> const doublon DEFAULT_INITIAL_BUFFER_TIME;<br /> const doublon DEFAULT_PLAY_BUFFER_TIME;<br /> };</p> </td> 
   <td><p>interface BufferControlParameters<br /> {<br /> attribut doublon initialBufferTime;<br /> attribut doublon playBufferTime ;<br /> <br /> <br /> };</p> </td> 
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
   <td><p>interface TextFormat<br /> {<br /> // Conteneur de couleurs<br /> non signé short COLOR_DEFAULT = 0;<br /> const unsigned short COLOR_BLACK = 1;<br /> const unsigned short COLOR_GRAY = 2;<br /> const unsigned short COLOR_WHITE = 3;<br /> const unsigned short COLOR_BRIGHT_WHITE = 4;<br /> const unsigned short COLOR_DARK_RED = 5;<br /> const unsigned short COLOR_RED = 6;<br /> const unsigned short COLOR_BRIGHT_RED = 7;<br /> const unsigned short COLOR_DARK_GREEN = 8;<br /> const unsigned short COLOR_GREEN = 9;<br /> const unsigned short COLOR_BRIGHT_GREEN = 10;<br /> const unsigned short COLOR_DARK_BLUE = 11;<br /> const unsigned short COLOR_BLUE = 12;<br /> const unsigned short COLOR_BRIGHT_BLUE = 13;<br /> const unsigned short COLOR_DARK_YELLOW = 14;<br /> const unsigned short COLOR_YELLOW = 15;<br /> const unsigned short COLOR_BRIGHT_YELLOW = 16;<br /> const unsigned short COLOR_DARK_MAGENTA = 17;<br /> const unsigned short COLOR_MAGENTA = 18;<br /> const unsigned short COLOR_BRIGHT_MAGENTA = 19;<br /> const unsigned short COLOR_DARK_CYAN = 20;<br /> const unsigned short COLOR_CYAN = 21;<br /> const unsigned short COLOR_BRIGHT_CYAN = 22;<br /> <br /> readonly attribut unsigned short fontColor ;<br /> readonly attribut unsigned short BackgroundColor ;<br /> readonly attribut unsigned short fillColor ;<br /> readonly attribut unsigned short edgeColor ;<br /> <br /> // Nombre de tailles<br /> non signé court SIZE_DEFAULT = 0;<br /> const unsigned short SIZE_SMALL = 1;<br /> const unsigned short SIZE_MEDIUM = 2;<br /> const unsigned short SIZE_LARGE = 3;<br /> <br /> readonly attribut unsigned short size;<br /> <br /> // FontEdge<br /> const unsigned short FONT_EDGE_DEFAULT = 0;<br /> const unsigned short FONT_EDGE_NONE = 1;<br /> const unsigned short FONT_EDGE_RAISED = 2;<br /> const unsigned short FONT_EDGE_DEPRESED = 3;<br /> const unsigned short FONT_EDGE_UNIFORM = 4;<br /> const unsigned short FONT_EDGE_DROP_SHADOW_LEFT = 5;<br /> const unsigned short FONT_EDGE_DROP_SHADOW_RIGHT = 6;<br /> readonly attribut unsigned short fontEdge ;<br /> <br /> // Font const<br /> unsigned short FONT_DEFAULT = 0;<br /> const unsigned short FONT_MONOSPACED_WITH_SERIFS = 1;<br /> const unsigned short FONT_PROPORTIONAL_WITH_SERIFS = 2;<br /> const unsigned short FONT_MONSPACED_WITHOUT_SERIFS = 3;<br /> const unsigned short FONT_CASUAL = 4;<br /> const unsigned short FONT_CURSIVE = 5;<br /> const unsigned short FONT_SMALL_CAPITALS = 6;<br /> readonly attribut unsigned short font ;<br /> readonly attribut unsigned short fontOpacity;<br /> readonly attribut unsigned short BackgroundOpacity;<br /> readonly attribut unsigned short fillOpacity;<br /> readonly attribut non signé short DEFAULT_OPACITY;<br /> };</p> </td> 
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
   <td><p>interface MediaPlayerItemLoader :<br /> {<br /> void load(MediaResource resource, long resourceId,<br /> ItemLoaderListener listener, <br /> MediaPlayerItemConfig);<br /> void cancel();<br /> readonly attribut MediaPlayerItem currentItem ;<br /> };</p> </td> 
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
   <td><p>interface MediaPlayerItem {<br /> readonly attribut MediaResource ;<br /> readonly attribut long resourceId ;<br /> readonly, attribut booléen live ;<br /> <br /> readonly, attribut booléen hasAlternateAudio ;<br /> readonly attribut AudioTrackList audioTracks ;<br /> readonly, attribut AudioTrack selectedAudioTrack ;<br /> void selectAudioTrack(AudioTrack track); <br /> <br /> readonly, attribut booléen hasClosedCaptions ;<br /> readonly attribut ClosedCaptionsTrackList ClosedCaptionsTracks ;<br /> readonly attribut ClosedCaptionsTrack selectedClosedCaptionsTrack ;<br /> void selectClosedCaptionsTrack(<br /> ClosedCaptionsTrack); <br /> <br /> readonly, attribut booléen hasTimedMetadata ;<br /> readonly, attribut TimedMetadataList timedMetadata ;<br /> readonly, attribut booléen dynamique ;<br /> <br /> readonly, attribut booléen isProtected ;<br /> readonly, attribut DRMMetadataInfoList drmMetadataInfos ;<br /> les profils readonly attribute ProfileList ;<br /> readonly attribut Profil selectedProfile;<br /> <br /> readonly attribut boolean trickPlaySupported;<br /> readonly attribut FloatArray availablePlaybackRates ;<br /> readonly attribut float selectedPlaybackRate;<br /> <br /> <br /> readonly, attribut MediaPlayer mediaPlayer ;<br /> readonly, attribut MediaPlayerItemConfig;<br /> };</p> </td> 
   <td><p>interface MediaPlayerItem {<br /> readonly attribut MediaResource ;<br /> readonly attribut long resourceId ;<br /> readonly, attribut booléen live ;<br /> <br /> readonly, attribut booléen hasAlternateAudio ;<br /> readonly attribut AudioTrackList audioTracks ;<br /> attribut AudioTrack selectedAudioTrack ;<br /> <br /> <br /> readonly, attribut booléen hasClosedCaptions ;<br /> readonly attribut ClosedCaptionsTrackList ccTracks ;<br /> attribut ClosedCaptionsTrack selectedCCTrack ;<br /> <br /> <br /> <br /> readonly, attribut booléen hasTimedMetadata ;<br /> readonly, attribut TimedMetadataList timedMetadata ;<br /> readonly, attribut booléen dynamique ;<br /> <br /> readonly, attribut booléen isProtected ;<br /> readonly, attribut DRMMetadataInfoList drmMetadataInfos ;<br /> les profils readonly attribute ProfileList ;<br /> <br /> <br /> readonly attribut boolean trickPlaySupported;<br /> readonly attribut Int32Array availablePlaybackRates ;<br /> <br /> readonly attribut StringList adTags ;<br /> <br /> readonly, attribut MediaPlayer mediaPlayer ;<br /> <br /> };</p> </td> 
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
   <td><p>interface Track<br /> {<br /> readonly attribut DomString name;<br /> readonly, attribut langage DomString ;<br /> readonly, attribut booléen par défaut ;<br /> readonly, attribut booléen autoSelect ;<br /> }; </p> </td> 
   <td>Nouveautés de la version 2.0</td> 
  </tr> 
  <tr> 
   <td><p>interface AudioTrack : Track<br /> {<br /> readonly attribut DomString name; //FromTrack<br /> readonly attribut DomString langue ;//FromTrack<br /> readonly attribut booléen default ; // De l'attribut de lecture<br /> seule booléen autoSelect ;//DeTrack<br /> <br /> readonly attribut non signé int pid ;<br /> };</p> </td> 
   <td><p>interface AudioTrack<br /> {<br /> readonly attribut DomString name;<br /> readonly, attribut langage DomString ; <br /> readonly, attribut booléen par défaut ;<br /> readonly, attribut booléen autoSelect ;<br /> readonly, attribut booléen forcé ;<br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td>Aucune modification pour la version 2.0</td> 
   <td><p>interface AudioTrackList<br /> {<br /> readonly attribut non signé long ;<br /> getter AudioTrack (index long non signé);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface ClosedCaptionsTrack : Track<br /> {<br /> readonly attribut DomString name; //FromTrack<br /> readonly attribut DomString langue ;//FromTrack<br /> readonly attribut booléen default ; // FromTrack<br /> readonly attribut booléen autoSelect;//FromTrack<br /> const <br /> <br /> non signé short SERVICE_608_CAPTIONS = 0;<br /> const unsigned short SERVICE_708_CAPTIONS = 1;<br /> const unsigned short SERVICE_WEB_VTT_CAPTIONS = 2;<br /> readonly attribut unsigned short serviceType ;<br /> readonly, attribut booléen forcé ;<br /> };</p> </td> 
   <td><p>interface ClosedCaptionsTrack<br /> {<br /> readonly attribute DomString name;<br /> readonly, attribut langage DomString ;<br /> readonly, attribut booléen par défaut ;<br /> <br /> <br /> readonly attribut booléen actif ;<br /> <br /> <br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td>Aucune modification pour la version 2.0</td> 
   <td><p>interface ClosedCaptionsTrackList<br /> {<br /> attribut readonly non signé long ;<br /> getter ClosedCaptionsTrack(index long non signé);<br /> };</p> </td> 
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
   <td><p>Profil<br /> d'interface {<br /> readonly attribut non signé int width;<br /> readonly attribut unsigned int height;<br /> readonly attribut unsigned int bitRate ;<br /> }; </p> </td> 
  </tr> 
  <tr> 
   <td>ProfileList : Aucune modification pour la version 2.0</td> 
   <td><p>interface ProfileList<br /> {<br /> readonly attribut non signé long ;<br /> getter Profil(index long non signé);<br /> };</p> </td> 
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
   <td><strong>DRMMetadataInfo</strong>: Aucune modification pour la version 2.0</td> 
   <td><p>interface DRMMetadataInfo<br /> { <br /> attribut readonly métadonnées DRMMetadata ;<br /> readonly attribut long prefetchTimestamp ;<br /> readonly, attribut TimeRange timeRange ;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>DRMMetadataInfoList</strong>: Aucune modification pour la version 2.0</td> 
   <td><p>interface DRMMetadataInfoList<br /> {<br /> readonly attribut unsigned long length ;<br /> getter DRMMetadataInfo(index long non signé);<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

## Mappage des erreurs C++ à des exceptions dans différentes langues {#mapping-c-errors-to-exceptions-in-different-languages}

Vous pouvez mapper des codes d’erreur C++ à des exceptions dans différentes langues.

Le PSDK C++ a une stratégie &quot;pas de jeton&quot; pour ses API. La plupart des méthodes API renvoient une valeur PSDKErrorCode pour indiquer si la méthode a bien été exécutée. Les erreurs asynchrones sont signalées par le biais des événements d’erreur.

La stratégie du PSDK ActionScript et JAVA est différente. La plupart des erreurs renvoient une exception ArgumentError ou IllegalStateException pour indiquer que la partie synchrone de la méthode n&#39;a pas pu être exécutée. Ces exceptions ne sont pas détectées et le code de l’application est responsable du traitement des exceptions. Ils contiennent généralement des informations utiles sur les raisons de l&#39;échec de l&#39;appel de méthode. Par exemple, si la commande prepareToPlay est appelée dans un état non valide, l’exception suivante est levée :

```shell
throw new IllegalStateException("Invalid player state. prepareToPlay method 
must be called only once after replaceCurrentItem or replaceCurrentResource method.");
```

Le code ActionScript/JAVA renvoie également des exceptions aux constructeurs pour indiquer que certains objets internes ont été créés de manière incorrecte. Ces exceptions sont gérées en interne et ne sont pas propagées à l’application. Les exceptions seront incluses dans une notification d&#39;avertissement envoyée à la demande.

Par exemple, si aucun fichier multimédia valide n’a été trouvé pour la réponse à la publicité reçue, aucun objet ou publicité publicitaire valide ne peut être créé. Par conséquent, aucune publicité n&#39;est placée sur la chronologie et une notification NotificationEvent.OperationFailed est envoyée.

Les codes d’erreur ou d’avertissement reçus de manière asynchrone par le moteur vidéo Adobe (AVE) sont envoyés normalement à l’application. Le événement de notification contient tous les codes d’erreur reçus et toutes les métadonnées supplémentaires, telles que l’URL, l’identifiant de ressource, le nom d’utilisateur, etc. Si l&#39;erreur est grave et que la lecture du média actuel ne peut pas se poursuivre, le événement MediaPlayer transition à l&#39;état ERROR et au rappel onStatusChanged ou MediaPlayerStatusChanged.STATUS_CHANGED est distribué. Si la lecture peut continuer, un événement de notification normal est distribué.

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
   <td><p>interface Version<br /> {<br /> readonly attribut DomString version;<br /> readonly, attribut description de DomString ;<br /> readonly attribut long major;<br /> readonly attribut long mineur ;<br /> révision longue d'attribut readonly ;<br /> readonly attribut long apiVersion ;<br /> };</p> </td> 
   <td><p>interface Version<br /> {<br /> readonly attribut DomString version;<br /> readonly, attribut description de DomString ;<br /> readonly attribut DomString major;<br /> readonly attribut DomString mineur ;<br /> readonly attribut révision DomString ;<br /> readonly, attribut DomString apiVersion;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### TimeRange {#timerange}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td>Aucune modification pour la version 2.0</td> 
   <td><p>interface TimeRange<br /> {<br /> readonly attribut non signé long begin;<br /> readonly attribut non signé long end;<br /> attribut readonly non signé longue durée ;<br /> };</p> </td> 
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
   <td><p>interface QOSProvider<br /> {<br /> void attachementMediaPlayer(MediaPlayer player);<br /> void detachMediaPlayer();<br /> <br /> readonly attribut DeviceInformation deviceInformation ;<br /> readonly attribut PlaybackInformation playbackInformation ;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### Informations sur le périphérique {#deviceinformation}

<table> 
 <tbody> 
  <tr> 
   <th>API 2.0</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface DeviceInformation<br /> {<br /> readonly attribut DomString os;<br /> <br /> <br /> <br /> readonly attribut DomString id;<br /> readonly, attribut int densitéDPI ;<br /> readonly attribut int heightPixels ;<br /> readonly attribut int widthPixels ;<br /> readonly, attribut booléen searchToKeyFrame;<br /> };</p> </td> 
   <td><p>interface DeviceInformation<br /> {<br /> readonly attribut DomString os;<br /> readonly attribute int sdk;<br /> readonly attribut modèle DomString ;<br /> readonly attribut fabricant DomString ;<br /> readonly attribut DomString id;<br /> readonly, attribut int densitéDPI ;<br /> readonly attribut int heightPixels ;<br /> readonly attribut int widthPixels ;<br /> <br /> };</p> </td> 
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
   <td><p>interface LoadInfo<br /> {<br /> readonly attribut URL DomString ;<br /> readonly attribut int size;<br /> readonly, attribut doublon downloadDuration ;<br /> readonly attribut int periodIndex ;<br /> readonly, attribut doublon mediaDuration ;<br /> readonly attribut short TRACK_TYPE_FRAGMENT;<br /> readonly attribut short TRACK_TYPE_TRACK;<br /> readonly attribut short TRACK_TYPE_MANIFEST;<br /> type abrégé d'attribut readonly ;<br /> readonly attribut DomString trackName;<br /> readonly attribut DomString trackType;<br /> readonly attribut int trackIndex ;<br /> };</p> </td> 
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
   <td><p>Vue<br /> d'interface {<br /> readonly attribut unsigned short x;<br /> readonly attribut non signé short y;<br /> attribut readonly non signé short width;<br /> readonly attribut unsigned short height;<br /> <br /> void setSize(unsigned short width, unsigned short height);<br /> void setPos(unsigned short x, unsigned short y);<br /> }</p> </td> 
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
   <td><p>interface PlaybackInformation<br /> {<br /> readonly attribut doublon timeToFirstByte;<br /> readonly attribut doublon timeToLoad;<br /> readonly attribut doublon timeToStart;<br /> readonly attribut doublon timeToFail ;<br /> readonly attribut int totalSecondsPlayed ;<br /> readonly attribut int totalSecondsSpent;<br /> readonly attribut doublon frameRate;<br /> readonly attribut int droppedFrameCount;<br /> readonly attribut intperceptionBandwidth;<br /> readonly attribut int bitrate ;<br /> readonly attribut bufferTime du doublon ;<br /> readonly attribut int bufferLength;<br /> readonly attribut int emptyBufferCount;<br /> readonly attribut doublon bufferingTime ;<br /> };</p> </td> 
   <td><p>interface PlaybackInformation<br /> {<br /> readonly attribut doublon timeToFirstByte;<br /> readonly attribut doublon timeToLoad;<br /> readonly attribut doublon timeToStart;<br /> readonly attribut doublon timeToFail ;<br /> readonly attribut int totalSecondsPlayed ;<br /> readonly attribut int totalSecondsSpent;<br /> readonly attribut doublon frameRate;<br /> readonly attribut int droppedFrameCount;<br /> <br /> readonly attribut int bitrate ;<br /> readonly attribut bufferTime du doublon ;<br /> readonly attribut int bufferLength;<br /> readonly attribut int emptyBufferCount;<br /> readonly attribut doublon bufferingTime ;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

## Ressources utiles {#helpful-resources}

* Consultez la documentation d’aide complète sur la page de formation et d’assistance [d’](https://helpx.adobe.com/support/primetime.html) Adobe Primetime.
