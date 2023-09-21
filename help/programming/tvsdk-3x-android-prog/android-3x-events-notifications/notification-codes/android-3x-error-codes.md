---
title: Codes d’erreur PSDK
description: Informations sur divers codes d’erreur, avertissements et codes d’erreur natifs.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1897'
ht-degree: 6%

---

# Codes d’erreur PSDK {#psdk-error-codes}

Lisez la suite pour en savoir plus sur les codes d’erreur, les avertissements et les codes d’erreur natifs du PSDK.

## Erreurs

Le tableau suivant fournit des informations détaillées sur les notifications de type ERROR. La plupart des erreurs contiennent des métadonnées pertinentes, par exemple l’URL de la ressource dont le téléchargement a échoué. Certaines notifications contiennent des métadonnées pour indiquer si le problème s’est produit dans le contenu vidéo principal, dans le contenu audio alternatif ou dans une publicité.

<table frame="all" colsep="1" rowsep="1">
  <tr> 
   <th><b>Nom d’erreur PSDK</b></th>
   <th><b>Code d’erreur PSDK</b></th>
   <th><b>Description</b></th>
  </tr>
  <tr>
    <td>SUCCÈS</td>
    <td>0</td>
    <td>L’opération effectuée par l’API sous-jacente réussit.</td>
  </tr>
  <tr>
    <td>INVALID_ARGUMENT</td>
    <td>1</td>
    <td>Les données ou le format d’argument fourni à l’API sous-jacente ne sont pas valides.</td>
  </tr>
  <tr>
    <td>NULL_POINTER</td>
    <td>2</td>
    <td>L’un des arguments transmis est NULL ou l’un des membres internes n’a pas été initialisé.</td>
  </tr>
  <tr>
    <td>ILLEGAL_STATE</td>
    <td>3</td>
    <td>L’opération n’est pas prise en charge dans l’état actuel du lecteur.</td>
  </tr>
  <tr>
    <td>INTERFACE_NOT_FOUND</td>
    <td>4</td>
    <td>La méthode interfaceCast renvoie cette erreur lorsque l’interface demandée n’est pas implémentée/héritée par celle-ci.</td>
  </tr>
  <tr>  
    <td>CREATION_FAILED</td>
    <td>5</td>
    <td>La création de l'une des ressources internes a échoué.</td>
  </tr>
  <tr>
    <td>UNSUPPORTED_OPERATION</td>
    <td>6</td>
    <td>L’opération demandée n’est actuellement pas prise en charge.</td>
  </tr>
  <tr>
    <td>DATA_NOT_AVAILABLE</td>
    <td>7</td>
    <td>Les données demandées ne sont actuellement pas disponibles.</td>
  </tr>
  <tr>
    <td>SEEK_ERROR</td>
    <td>8</td>
    <td>Une erreur s’est produite lors de l’exécution d’une opération de recherche.</td>
  </tr>
  <tr>
    <td>UNSUPPORTED_FEATURE</td>
    <td>9</td>
    <td>Cette fonction n’est pas prise en charge.</td>
  </tr>
  <tr>
    <td>RANGE_ERROR</td>
    <td>10</td>
    <td>La valeur spécifiée est hors plage.</td>
  </tr>
  <tr>
    <td>CODEC_NOT_SUPPORTED</td>
    <td>11</td>
    <td>Le codec audio/vidéo de la diffusion n’est pas pris en charge par TVSDK ou par l’appareil sous-jacent.</td>
  </tr>
  <tr>
    <td>MEDIA_ERROR</td>
    <td>12</td>
    <td>Le média spécifié est introuvable.</td>
  </tr>
  <tr>
    <td>NETWORK_ERROR</td>
    <td>13</td>
    <td>Une erreur s’est produite lors du téléchargement d’un fragment ou d’un segment (vidéo et audio).</td>
  </tr>
  <tr>
    <td>GENERIC_ERROR</td>
    <td>14</td>
    <td>Événement d’erreur générique. Non émis par TVSDK. Il ne s’agit que d’un marqueur pour la fin de la plage de codes numériques correspondant aux événements d’erreur TVSDK.</td>
  </tr>
  <tr>
    <td>INVALID_SEEK_TIME</td>
    <td>15</td>
    <td>L’heure de recherche fournie n’est pas valide.</td>
  </tr>
  <tr>
    <td>AUDIO_TRACK_ERROR</td>
    <td>16</td>
    <td>Une erreur liée à une piste audio s’est produite (Autre audio)</td>
  </tr>
  <tr>
    <td>ACCESS_FROM_DIFFÉRENT_THREAD</td>
    <td>17</td>
    <td>L’API PSDK est appelée à partir d’un autre thread que le thread dans lequel le PSDK a été initialisé.</td>
  </tr>
  <tr>
    <td>ELEMENT_NOT_FOUND</td>
    <td>18</td>
    <td>L’élément est introuvable.</td>
  </tr>
  <tr>
    <td>NOT_IMPLEMENTED</td>
    <td>19</td>
    <td>Fonction non implémentée.</td>
  </tr>
  <tr>
    <td>PRE_ROLL_DISABLED</td>
    <td>20</td>
    <td>La préroll a été désactivée via AdvertisingMetadata.</td>
  </tr>
  <tr>
    <td>PLAYBACK_NOT_AUTHORIZED</td>
    <td>57</td>
    <td>La lecture HLS n’a pas été activée dans le Flash Player. Voir AuthorizedFeatures.enableMediaPlayerHLSPlayback().</td>
  </tr>
  <tr>
    <td>NETWORK_TIMEOUT</td>
    <td>58</td>
    <td>Dépassement du réseau lors de la récupération d’une ressource/connexion au serveur.</td>
  </tr>
</table>

## Avertissements

Le tableau suivant fournit des informations détaillées sur les notifications de type WARN.
La plupart des avertissements contiennent des métadonnées pertinentes, par exemple l’URL de la ressource dont le téléchargement a échoué. Certaines notifications contiennent des métadonnées pour indiquer si le problème s’est produit dans le contenu vidéo principal, dans le contenu audio alternatif ou dans une publicité.

<table frame="all" colsep="1" rowsep="1">
  <tr>
    <th><b>Nom de l’erreur</b></th>
    <th><b>Code</b></th>
    <th><b>Description</b></th>
  </tr>
  <tr>
    <td>PLAYBACK_OPERATION_FAILED</td>
    <td>200</td>
    <td>Une erreur s’est produite lors de l’opération de lecture. Une opération liée à la lecture a échoué.</td>
  </tr>
  <tr>  
    <td>NATIVE_WARNING</td>
    <td>201</td>
    <td>La bibliothèque AVE de bas niveau a généré une erreur.</td>
  </tr>
  <tr>
    <td>AD_RESOLVER_FAILED</td>
    <td>202</td>
    <td>Le module externe d’annonce n’a pas pu résoudre les publicités.</td>
  </tr>
  <tr>
    <td>AD_MANIFEST_LOAD_FAILED</td>
    <td>203</td>
    <td>Échec du chargement du manifeste de publicité.</td>
  </tr>
  <tr>
    <td>AD_RESOLUTION_IN_PROGRESS</td>
    <td>204</td>
    <td>L’opération de résolution des publicités est en cours.</td>
  </tr>
  </table>

## Infos

<table frame="all" colsep="1" rowsep="1">
  <tr> 
    <th><b>Nom de l’erreur</b></th>
    <th><b>Code</b></th>
    <th><b>Description</b></th>
  </tr>
  <tr>
    <td>REVENUE_OPTIMIZATION_REPORTING</td>
    <td>300</td>
    <td>Notifications détaillées de TVSDK pour des analyses et des rapports ultérieurs.</td>
  </tr>
 </table>

## Codes d’erreur natifs

L’interface Codeur vidéo de l’AVE renvoie ces notifications de lecture vidéo dans l’objet de métadonnées NATIVE_ERROR.

<table frame="all" colsep="1" rowsep="1">
  <tr>
    <th><b>Nom de l’erreur</b></th>
    <th><b>Code</b></th>
    <th><b>Description</b></th>
  </tr>
  <tr>  
    <td>END_OF_PERIOD</td>
    <td>-1</td>
    <td>Fin de période.</td>
  </tr>
  <tr>
    <td>SUCCÈS</td>
    <td>0</td>
    <td>L'opération a réussi.</td>
  </tr>
  <tr>
    <td>ASYNC_OPERATION_IN_PROGRESS</td>
    <td>1</td>
    <td>Opération asynchrone. La demande d’opération a été effectuée. Les informations de succès/échec seront disponibles ultérieurement.</td>
  </tr>
  <tr>
    <td>EOF</td>
    <td>2</td>
    <td>Opération impossible en raison de la condition de fin de fichier (EOF).</td>
  </tr>
  <tr>
    <td>DECODER_FAILED</td>
    <td>3</td>
    <td>Le décodeur a échoué à l’exécution.</td>
  </tr>
  <tr>
    <td>DEVICE_OPEN_ERROR</td>
    <td>4</td>
    <td>Échec de l’ouverture du décodeur matériel.</td>
  </tr>
  <tr>
    <td>FILE_NOT_FOUND</td>
    <td>5</td>
    <td>La ressource est introuvable.</td>
  </tr>
  <tr>
    <td>GENERIC_ERROR</td>
    <td>6</td>
    <td>Erreur générique.</td>
  </tr>
  <tr>
    <td>IRRECOVERABLE_ERROR</td>
    <td>7</td>
    <td>Une condition d’erreur à laquelle le moteur vidéo ne peut pas récupérer.</td>
  </tr>
  <tr>
    <td>LOST_CONNECTION_RECOVERABLE</td>
    <td>8</td>
    <td>Erreur réseau, tentative de récupération.</td>
  </tr>
  <tr> 
    <td>NO_FIXED_SIZE</td>
    <td>9</td>
    <td>La taille de la ressource ne peut pas être déterminée.</td>
  </tr>
  <tr>
    <td>NOT_IMPLEMENTED</td>
    <td>10</td>
    <td>Fonction non implémentée.</td>
  </tr>
  <tr>
    <td>OUT_OF_MEMORY</td>
    <td>11</td>
    <td>Mémoire insuffisante.</td>
  </tr>
  <tr>
    <td>PARSE_ERROR</td>
    <td>12</td>
    <td>Erreur lors de l’analyse du fichier multimédia.</td>
  </tr>
  <tr>  
    <td>SIZE_UNKNOWN</td>
    <td>13</td>
    <td>La ressource a une taille, mais elle est inconnue.</td>
  </tr>
  <tr>  
    <td>UNDER_FLOW</td>
    <td>14</td>
    <td>Condition de sous-flux.</td>
  </tr>
  <tr> 
    <td>UNSUPPORTED_CONFIG</td>
    <td>15</td>
    <td>Configuration non prise en charge.</td>
  </tr>
  <tr>  
    <td>UNSUPPORTED_OPERATION</td>
    <td>16</td>
    <td>Le fonctionnement n’est pas pris en charge.</td>
  </tr>
  <tr>
    <td>WAITING_FOR_INIT</td>
    <td>17</td>
    <td>Pas encore initialisé.</td>
  </tr>
  <tr>  
    <td>INVALID_PARAMETER</td>
    <td>18</td>
    <td>Paramètre non valide.</td>
  </tr>
  <tr>
    <td>INVALID_OPERATION</td>
    <td>19</td>
    <td>Opération non autorisée.</td>
  </tr>
  <tr>
    <td>OP_ONLY_ALLOWED_IN_PAUSED_STATE</td>
    <td>20</td>
    <td>L’opération n’est autorisée que si elle est suspendue.</td>
  </tr>
  <tr> 
    <td>OP_INVALID_WITH_AUDIO_ONLY_FILE</td>
    <td>21</td>
    <td>L’opération ne peut pas être utilisée sur des fichiers audio uniquement.</td>
  </tr>
  <tr>
    <td>PREVIOUS_STEP_SEEK_IN_PROGRESS</td>
    <td>22</td>
    <td>L’opération de recherche précédente est toujours en cours.</td>
  </tr>
  <tr> 
    <td>SOURCE_NOT_SPECIFIED</td>
    <td>23</td>
    <td>Ressource non spécifiée.</td>
  </tr>
  <tr>
    <td>RANGE_ERROR</td>
    <td>24</td>
    <td>La valeur spécifiée est hors plage.</td>
  </tr>
  <tr>
    <td>INVALID_SEEK_TIME</td>
    <td>25</td>
    <td>Heure de recherche non valide.</td>
  </tr>
  <tr>
    <td>FILE_STRUCTURE_INVALID</td>
    <td>26</td>
    <td>Le fichier spécifié n’est pas conforme à la syntaxe attendue.</td>
  </tr>
  <tr>
    <td>COMPONENT_CREATION_FAILURE</td>
    <td>27</td>
    <td>Impossible de créer un composant essentiel.</td>
  </tr>
  <tr>
    <td>DRM_INIT_ERROR</td>
    <td>28</td>
    <td>Échec de la création du contexte DRM.</td>
  </tr>
  <tr>
    <td>CONTAINER_NOT_SUPPORTED</td>
    <td>29</td>
    <td>Le type de conteneur n’est pas pris en charge.</td>
  </tr>
  <tr>
    <td>SEEK_FAILED</td>
    <td>30</td>
    <td>Échec de la recherche.</td>
  </tr>
  <tr>
    <td>CODEC_NOT_SUPPORTED</td>
    <td>31</td>
    <td>Code non pris en charge.</td>
  </tr>
  <tr>
    <td>NETWORK_UNAVAILABLE</td>
    <td>32</td>
    <td>Le réseau n’est pas disponible.</td>
  </tr>
  <tr>  
    <td>NETWORK_ERROR</td>
    <td>33</td>
    <td>Erreur lors de l’obtention des données du réseau.</td>
  </tr>
  <tr>
    <td>DÉBORDEMENT</td>
    <td>34</td>
    <td>Débordement.</td>
  </tr>
  <tr>  
    <td>VIDEO_PROFILE_NOT_SUPPORTED</td>
    <td>35</td>
    <td>Profil vidéo non pris en charge</td>
  </tr>
  <tr>
    <td>PERIOD_NOT_LOADED</td>
    <td>36</td>
    <td>Une opération a été tentée sur une période HOLD ou une période qui n’a pas encore été chargée.</td>
  </tr>
  <tr> 
    <td>INVALID_REPLACE_DURATION</td>
    <td>37</td>
    <td>La durée de remplacement spécifiée n’est pas valide ou s’étend au-delà de la fin du flux.</td>
  </tr>
  <tr>
    <td>CALLED_FROM_WRONG_THREAD</td>
    <td>38</td>
    <td>L’API ne peut pas être appelée à partir du mauvais thread. Surtout pour les éléments d’API qui doivent être appelés à partir du thread principal uniquement.</td>
  </tr>
  <tr>
    <td>FRAGMENT_READ_ERROR</td>
    <td>39</td>
    <td>Erreur de lecture du fragment. Aucun basculement n’est présent. Le moteur essaiera de lire le fragment suivant.</td>
  </tr>
  <tr>
    <td>ABORDÉ</td>
    <td>40</td>
    <td>L’opération a été abandonnée par un appel Abandon ou Détruire explicite.</td>
  </tr>
  <tr>
    <td>UNSUPPORTED_HLS_VERSION</td>
    <td>41</td>
    <td>Impossible de lire cette version du média HLS.</td>
  </tr>
  <tr>
    <td>CANNOT_FAIL_OVER</td>
    <td>42</td>
    <td>Impossible d’échouer.</td>
  </tr>
  <tr> 
    <td>HTTP_TIME_OUT</td>
    <td>43</td>
    <td>Le téléchargement HTTP a expiré.</td>
  </tr>
  <tr>
    <td>NETWORK_DOWN</td>
    <td>44</td>
    <td>La connexion réseau de l’utilisateur est hors service. La lecture peut s’arrêter à tout moment et reprendre lorsque la connexion est disponible.</td>
  </tr>
  <tr>
    <td>NO_USABLE_BITRATE_PROFILE</td>
    <td>45</td>
    <td>Aucun profil de débit utilisable trouvé dans la diffusion.</td>
  </tr>
  <tr>
    <td>BAD_MANIFEST_SIGNATURE</td>
    <td>46</td>
    <td>Le manifeste a une mauvaise signature. Le test de signature du manifeste a échoué.</td>
  </tr>
  <tr>
    <td>CANNOT_LOAD_PLAYLIST</td>
    <td>47</td>
    <td>Impossible de charger une liste de lecture.</td>
  </tr>
  <tr>
    <td>REPLACEMENT_FAILED</td>
    <td>48</td>
    <td>Le remplacement spécifié dans une API d’insertion n’a pas réussi. Cela signifie que l’insertion a réussi, mais que le remplacement ne l’a pas été. Le remplacement peut échouer si le manifeste à remplacer a été supprimé de la chronologie.</td>
  </tr>
  <tr>
    <td>SWITCH_TO_ASYMMETRIC_PROFILE</td>
    <td>49</td>
    <td>DRM passe à un profil asymétrique. Tous les profils doivent être alignés dans la durée. Si ce n’est pas le cas, cet avertissement est généré et des sauts peuvent se produire dans la lecture.</td>
  </tr>
  <tr>
    <td>LIVE_WINDOW_MOVED_BACKWARD</td>
    <td>50</td>
    <td>La fenêtre active ne doit être redirigée que vers l’avant. Si ce n’est pas le cas, cet avertissement s’affiche et la fenêtre n’est pas lue. Pour cette raison, il peut y avoir des sauts (ou une longue pause/arrêt) dans la lecture.</td>
  </tr>
  <tr>
    <td>CURRENT_PERIOD_EXPIRED</td>
    <td>51</td>
    <td>Fenêtre active déplacée au-delà de la période actuelle.</td>
  </tr>
  <tr>
    <td>CONTENT_LENGTH_MISMATCH</td>
    <td>52</td>
    <td>La longueur du contenu consignée par le serveur HTTP ne correspondait pas à la taille réelle du média.</td>
  </tr>
  <tr>
    <td>PERIOD_HOLD</td>
    <td>53</td>
    <td>Le lecteur multimédia ne peut pas lire davantage, car il a atteint l’heure définie par l’API setholdAt.</td>
  </tr>
  <tr>  
    <td>LIVE_HOLD</td>
    <td>54</td>
    <td>Le lecteur multimédia ne peut pas charger les segments, car il a atteint la fin de la fenêtre active. Le chargement des segments reprend lorsque le serveur ajoute de nouveaux médias à la fenêtre active. Cet état est généralement atteint si :<ul><li>bufferTime est trop élevé (égal ou supérieur à la durée de la fenêtre active).</li><li>Une combinaison d’une ou de plusieurs API d’insertion/effacement a remplacé plus de médias qu’elle n’en a ajouté.</li><li>La période suivante est une période d’activation avec un remplacement de média en attente (en raison de l’appel API InsertBy).</li></ul></td>
  </tr>
  <tr>
    <td>BAD_MEDIA_INTERLEAVING</td>
    <td>55</td>
    <td>L’entrelacement audio et vidéo dans le média n’est pas effectué correctement. Il s’agit d’une erreur de package. L’avertissement est envoyé lorsque la différence dépasse deux secondes.</td>
  </tr>
  <tr>
    <td>DRM_NOT_AVAILABLE</td>
    <td>56</td>
    <td></td>
  </tr>
  <tr>  
    <td>PLAYBACK_NOT_AUTHORIZED</td>
    <td>57</td>
    <td>La lecture HLS n’a pas été activée dans le Flash Player. Voir AuthorizedFeatures.enableHLSPlayback.</td>
  </tr>
  <tr>
    <td>BAD_MEDIA_SAMPLE_FOUND</td>
    <td>58</td>
    <td>Le décodeur a reçu un mauvais échantillon qui ne peut pas être décodé. Il ne s’agit généralement pas d’une erreur fatale, mais cela indique qu’il peut y avoir des problèmes dans l’audio/la vidéo. Trop d’instances de cette erreur indiquent un mauvais codage ou un fichier incorrect.</td>
  </tr>
  <tr>
    <td>RANGE_SPANS_READ_HEAD</td>
    <td>59</td>
    <td>Une fois la lecture lancée, la plage Insérer/Remplacer ne doit pas contenir le titre de lecture.</td>
  </tr>
  <tr> 
    <td>POSTROLL_WITH_LIVE_NOT_ALLOWED</td>
    <td>60</td>
    <td>Les insertions post-roll ne sont pas autorisées sur un média en direct. Elles sont toutefois autorisées une fois que le serveur a marqué le média comme terminé.</td>
  </tr>
  <tr>
    <td>INTERNAL_ERROR</td>
    <td>61</td>
    <td>Un problème très rare qui ne devrait jamais se produire.</td>
  </tr>
  <tr>  
    <td>SPS_PPS_FOUND_OUTSIDE_AVCC</td>
    <td>62</td>
    <td>Le flux ne suit pas la recommandation de package de toujours placer H264 SPS/PPS dans un AVCC. Des problèmes de recherche/lecture peuvent s’afficher.</td>
  </tr>
  <tr>  
    <td>PARTIAL_REPLACEMENT</td>
    <td>63</td>
    <td>Le remplacement spécifié dans une API d’insertion n’a été que partiellement effectué. Cela se produit lorsque replaceDuration s’étend sur la durée de la chronologie.</td>
  </tr>
  <tr>
    <td>RENDITION_M3U8_ERROR</td>
    <td>64</td>
    <td>Une erreur de chargement s’est produite dans la liste de lecture du rendu. Il s’agit uniquement d’AVE, et non de FlashPlayer.</td>
  </tr>
  <tr>
    <td>NULL_OPERATION</td>
    <td>65</td>
    <td>L'opération ne fait rien.</td>
  </tr>
  <tr>
    <td>SEGMENT_SKIPPED_ON_FAILURE</td>
    <td>66</td>
    <td>Le segment ne peut pas être lu et est ignoré en cas d’échec.</td>
  </tr>
  <tr>
    <td>INCOMPATIBLE_RENDER_MODE</td>
    <td>67</td>
    <td>Mode de rendu non compatible.</td>
  </tr>
  <tr>
    <td>PROTOCOL_NOT_SUPPORTED</td>
    <td>68</td>
    <td>Le protocole Web utilisé dans l’URL n’est pas pris en charge.</td>
  </tr>
  <tr>
    <td>PARSE_ERROR_INCOMPATIBLE_VERSION</td>
    <td>69</td>
    <td>Erreur lors de l’analyse du fichier multimédia.</td>
  </tr>
  <tr>  
    <td>MANIFEST_FILE_UNEXPECTEDLY_CHANGED</td>
    <td>70</td>
    <td>Le fichier de manifeste a été modifié de manière inattendue.</td>
  </tr>
  <tr>
    <td>CANNOT_SPLIT_TIMELINE</td>
    <td>71</td>
    <td>Impossible d’effectuer une opération de partage sur une chronologie.</td>
  </tr>
  <tr>
    <td>CANNOT_ERASE_TIMELINE</td>
    <td>72</td>
    <td>Impossible d’effectuer une opération d’effacement sur une chronologie.</td>
  </tr>
  <tr>
    <td>DID_NOT_GET_NEXT_FRAGMENT</td>
    <td>73</td>
    <td>N’a pas obtenu le fragment suivant.</td>
  </tr>
  <tr>
    <td>NO_TIMELINE</td>
    <td>74</td>
    <td>Aucune chronologie présente dans une structure de données interne.</td>
  </tr>
  <tr>
    <td>LISTENER_NOT_FOUND</td>
    <td>75</td>
    <td>Aucun écouteur trouvé dans une structure de données interne.</td>
  </tr>
  <tr>
    <td>AUDIO_START_ERROR</td>
    <td>76</td>
    <td>Impossible de démarrer l’audio.</td>
  </tr>
  <tr>
    <td>NO_AUDIO_SINK</td>
    <td>77</td>
    <td>Aucun évier audio n’est présent dans une structure de données interne.</td>
  </tr>
  <tr>  
    <td>FILE_OPEN_ERROR</td>
    <td>78</td>
    <td>Impossible d’ouvrir le fichier.</td>
  </tr>
  <tr>
    <td>FILE_WRITE_ERROR</td>
    <td>79</td>
    <td>Impossible d’écrire dans un fichier.</td>
  </tr>
  <tr>
    <td>FILE_READ_ERROR</td>
    <td>80</td>
    <td>Impossible de lire à partir d’un fichier.</td>
  </tr>
  <tr>
    <td>ID3PARSE_ERROR</td>
    <td>81</td>
    <td>Une erreur s’est produite lors de l’analyse des données ID3.</td>
  </tr>
  <tr>
    <td>SECURITY_ERROR</td>
    <td>82</td>
    <td>Le chargement du contenu a échoué en raison de restrictions de sécurité.</td>
  </tr>
  <tr>
    <td>TIMELINE_TOO_SHORT</td>
    <td>83</td>
    <td>La durée de la chronologie est trop courte. S’il s’agit d’une diffusion en direct, une mise en mémoire tampon fréquente peut se produire.</td>
  </tr>
  <tr>
    <td>AUDIO_ONLY_STREAM_START</td>
    <td>84</td>
    <td>Le flux a été basculé vers un flux audio uniquement.</td>
  </tr>
  <tr>  
    <td>AUDIO_ONLY_STREAM_END</td>
    <td>85</td>
    <td>Le flux est passé de l’audio uniquement à un flux vidéo.</td>
  </tr>
  <tr>
    <td>KEY_NOT_FOUND</td>
    <td>87</td>
    <td>Clé introuvable.</td>
  </tr>
  <tr>
    <td>INVALID_KEY</td>
    <td>88</td>
    <td>La clé n’est pas valide.</td>
  </tr>
  <tr>
    <td>KEY_SERVER_NOT_FOUND</td>
    <td>89</td>
    <td>Le serveur de clés ne renvoie pas de clé.</td>
  </tr>
  <tr>
    <td>MAIN_MANIFEST_UPDATE_TO_BE_HANDLED</td>
    <td>90</td>
    <td>Impossible de gérer la mise à jour du manifeste principal.</td>
  </tr>
  <tr>
    <td>UNREPORTED_TIME_DISCONTINUITY_FOUND</td>
    <td>91</td>
    <td>Discontinuité de temps non signalé (PTS) trouvée.</td>
  </tr>
  <tr>
    <td>UNMATCHED_AV_DISCONTINUITY_FOUND</td>
    <td>92</td>
    <td>Discontinuité audio et vidéo inégalée trouvée.</td>
  </tr>
  <tr>
    <td>TRICKPLAY_ENDED_DUE_TO_ERROR</td>
    <td>93</td>
    <td>Une erreur s’est produite lors de la lecture du média en mode de lecture de l’astuce. Le mode de lecture de la marque est terminé et le flux est interrompu. Appelez Play() pour lire le média en mode normal.</td>
  </tr>
  <tr>
    <td>LIVE_WINDOW_MOVED_AHEAD</td>
    <td>95</td>
    <td>Le lecteur est hors de la fenêtre active et doit chercher à rattraper son retard.</td>
  </tr>
</table>
