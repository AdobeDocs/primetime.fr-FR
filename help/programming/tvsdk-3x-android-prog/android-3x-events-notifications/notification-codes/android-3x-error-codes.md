---
title: Codes d’erreur PSDK
description: Informations sur divers codes d’erreur, avertissements et codes d’erreur natifs.
translation-type: tm+mt
source-git-commit: eddc327087411a6214cfd8dafef66b850a603f97
workflow-type: tm+mt
source-wordcount: '1897'
ht-degree: 6%

---


# Codes d&#39;erreur PSDK {#psdk-error-codes}

Lisez la section pour en savoir plus sur les codes d’erreur PSDK, les avertissements et les codes d’erreur natifs.

## Erreurs

Le tableau suivant fournit des informations détaillées sur les notifications de type ERROR. La plupart des erreurs contiennent des métadonnées pertinentes ; par exemple, URL de la ressource dont le téléchargement a échoué. Certaines notifications contiennent des métadonnées pour indiquer si le problème s’est produit dans le contenu vidéo principal, dans l’autre contenu audio ou dans une publicité.

<table frame="all" colsep="1" rowsep="1">
  <tr> 
   <th><b>Nom d’erreur PSDK</b></th>
   <th><b>Code d’erreur PSDK</b></th>
   <th><b>Description</b></th>
  </tr>
  <tr>
    <td>RÉUSSITE</td>
    <td>0</td>
    <td>L'opération effectuée par l'API sous-jacente a réussi.</td>
  </tr>
  <tr>
    <td>INVALID_ARGUMENT</td>
    <td>3</td>
    <td>Les données ou le format de l'argument fourni à l'API sous-jacente ne sont pas valides.</td>
  </tr>
  <tr>
    <td>NULL_POINTER</td>
    <td>2</td>
    <td>L'un des arguments transmis est NULL ou l'un des membres internes n'a pas été initialisé.</td>
  </tr>
  <tr>
    <td>ILLEGAL_STATE</td>
    <td>1</td>
    <td>L'opération n'est pas prise en charge dans l'état actuel du lecteur.</td>
  </tr>
  <tr>
    <td>INTERFACE_NOT_FOUND</td>
    <td>4</td>
    <td>La méthode interfaceCast renvoie cette erreur lorsque l’interface demandée n’est pas implémentée/héritée par cette méthode.</td>
  </tr>
  <tr>  
    <td>CREATION_FAILED</td>
    <td>5</td>
    <td>Échec de la création de l'une des ressources internes.</td>
  </tr>
  <tr>
    <td>UNSUPPORTED_OPERATION</td>
    <td>6</td>
    <td>L'opération demandée n'est actuellement pas prise en charge.</td>
  </tr>
  <tr>
    <td>DATA_NOT_AVAILABLE</td>
    <td>7</td>
    <td>Les données demandées ne sont actuellement pas disponibles.</td>
  </tr>
  <tr>
    <td>SEEK_ERROR</td>
    <td>8</td>
    <td>Une erreur s'est produite lors de l'exécution d'une opération de recherche.</td>
  </tr>
  <tr>
    <td>NON SUPPORTED_FEATURE</td>
    <td>9</td>
    <td>Cette fonction n’est pas prise en charge.</td>
  </tr>
  <tr>
    <td>RANGE_ERROR</td>
    <td>10</td>
    <td>La valeur spécifiée est hors limites.</td>
  </tr>
  <tr>
    <td>CODEC_NOT_SUPPORTED</td>
    <td>11</td>
    <td>Le codec audio/vidéo de la diffusion en continu n’est pas pris en charge par TVSDK ou par le périphérique sous-jacent.</td>
  </tr>
  <tr>
    <td>MEDIA_ERROR</td>
    <td>12</td>
    <td>Le support spécifié est introuvable.</td>
  </tr>
  <tr>
    <td>NETWORK_ERROR</td>
    <td>13</td>
    <td>Une erreur s'est produite lors du téléchargement d'un fragment ou d'un segment (vidéo et audio).</td>
  </tr>
  <tr>
    <td>GENERIC_ERROR</td>
    <td>14</td>
    <td>Événement d’erreur générique. Non pas réellement émis par TVSDK. Il s’agit uniquement d’un marqueur pour la fin de la plage de codes numériques correspondant aux événements d’erreur TVSDK.</td>
  </tr>
  <tr>
    <td>INVALID_SEEK_TIME</td>
    <td>15</td>
    <td>Le temps de recherche fourni n'est pas valide.</td>
  </tr>
  <tr>
    <td>AUDIO_TRACK_ERROR</td>
    <td>16</td>
    <td>Une erreur liée à une piste audio s'est produite (Autre audio)</td>
  </tr>
  <tr>
    <td>ACCESS_FROM_DIFFERENT_THREAD</td>
    <td>17</td>
    <td>L’API PSDK est appelée à partir d’un thread différent de celui dans lequel le PSDK a été initialisé.</td>
  </tr>
  <tr>
    <td>ELEMENT_NOT_FOUND</td>
    <td>18</td>
    <td>L'élément est introuvable.</td>
  </tr>
  <tr>
    <td>NOT_IMPLEMENTED</td>
    <td>19</td>
    <td>Fonction non implémentée.</td>
  </tr>
  <tr>
    <td>PRE_ROLL_DISABLED</td>
    <td>20</td>
    <td>La pré-lecture a été désactivée via AdvertisingMetadata.</td>
  </tr>
  <tr>
    <td>PLAYBACK_NOT_AUTHORIZED</td>
    <td>57</td>
    <td>La lecture HLS n'a pas été activée dans le Flash Player. Voir AuthorizedFeatures.enableMediaPlayerHLSPlayback().</td>
  </tr>
  <tr>
    <td>NETWORK_TIMEOUT</td>
    <td>58</td>
    <td>Délai d'expiration du réseau lors de la récupération d'une ressource/d'un serveur de connexion.</td>
  </tr>
</table>

## Avertissements

Le tableau suivant fournit des informations détaillées sur les notifications de type WARN.
La plupart des avertissements contiennent des métadonnées pertinentes ; par exemple, l’URL de la ressource dont le téléchargement a échoué. Certaines notifications contiennent des métadonnées pour indiquer si le problème s’est produit dans le contenu vidéo principal, dans l’autre contenu audio ou dans une publicité.

<table frame="all" colsep="1" rowsep="1">
  <tr>
    <th><b>Nom d’erreur</b></th>
    <th><b>Code</b></th>
    <th><b>Description</b></th>
  </tr>
  <tr>
    <td>PLAYBACK_OPERATION_FAILED</td>
    <td>200</td>
    <td>Une erreur s’est produite pendant l’opération de lecture. Une opération liée à la lecture a échoué</td>
  </tr>
  <tr>  
    <td>NATIVE_WARNING</td>
    <td>2011</td>
    <td>La bibliothèque AVE de bas niveau a généré une erreur.</td>
  </tr>
  <tr>
    <td>AD_RESOLVER_FAILED</td>
    <td>202</td>
    <td>Le plug-in publicitaire n'a pas réussi à résoudre les publicités.</td>
  </tr>
  <tr>
    <td>AD_MANIFEST_LOAD_FAILED</td>
    <td>203</td>
    <td>Échec du chargement du manifeste de publicité.</td>
  </tr>
  <tr>
    <td>AD_RESOLUTION_IN_PROGRESS</td>
    <td>204</td>
    <td>L'opération de résolution des publicités est en cours.</td>
  </tr>
  </table>

## Infos

<table frame="all" colsep="1" rowsep="1">
  <tr> 
    <th><b>Nom d’erreur</b></th>
    <th><b>Code</b></th>
    <th><b>Description</b></th>
  </tr>
  <tr>
    <td>REVENUE_OPTIMIZATION_RAPPORTS</td>
    <td>300</td>
    <td>TVSDK - Notifications détaillées pour plus d’rapports et d’analyse.</td>
  </tr>
 </table>

## Codes d’erreur natifs

L’interface Video Encoder de l’AVE renvoie ces notifications de lecture vidéo dans l’objet de métadonnées NATIVE_ERROR.

<table frame="all" colsep="1" rowsep="1">
  <tr>
    <th><b>Nom d’erreur</b></th>
    <th><b>Code</b></th>
    <th><b>Description</b></th>
  </tr>
  <tr>  
    <td>END_OF_PERIOD</td>
    <td>-1</td>
    <td>Fin de la période.</td>
  </tr>
  <tr>
    <td>RÉUSSITE</td>
    <td>0</td>
    <td>Opération réussie.</td>
  </tr>
  <tr>
    <td>ASYNC_OPERATION_IN_PROGRESS</td>
    <td>1</td>
    <td>Opération asynchrone. La demande d'opération a été effectuée. Les informations de réussite/d’échec seront disponibles ultérieurement.</td>
  </tr>
  <tr>
    <td>EOF</td>
    <td>2</td>
    <td>Opération impossible en raison de la condition de fin de fichier (EOF).</td>
  </tr>
  <tr>
    <td>DECODER_FAILED</td>
    <td>1</td>
    <td>Échec du décodeur au moment de l'exécution.</td>
  </tr>
  <tr>
    <td>DEVICE_OPEN_ERROR</td>
    <td>4</td>
    <td>Échec de l'ouverture du décodeur matériel.</td>
  </tr>
  <tr>
    <td>FILE_NOT_FOUND</td>
    <td>5</td>
    <td>Impossible de localiser la ressource.</td>
  </tr>
  <tr>
    <td>GENERIC_ERROR</td>
    <td>6</td>
    <td>Erreur générique.</td>
  </tr>
  <tr>
    <td>IRRECOVERABLE_ERROR</td>
    <td>7</td>
    <td>Condition d’erreur à laquelle le moteur vidéo ne peut pas récupérer.</td>
  </tr>
  <tr>
    <td>LOST_CONNECTION_RECOVERABLE</td>
    <td>8</td>
    <td>Erreur réseau, tentative de récupération.</td>
  </tr>
  <tr> 
    <td>NO_FIXED_SIZE</td>
    <td>9</td>
    <td>Impossible de déterminer la taille de la ressource.</td>
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
    <td>Erreur lors de l'analyse du fichier multimédia.</td>
  </tr>
  <tr>  
    <td>TAILLE_INCONNUE</td>
    <td>13</td>
    <td>La ressource a une taille, mais elle est inconnue.</td>
  </tr>
  <tr>  
    <td>UNDER_FLOW</td>
    <td>14</td>
    <td>Condition de débordement.</td>
  </tr>
  <tr> 
    <td>UNSUPPORTED_CONFIG</td>
    <td>15</td>
    <td>La configuration n'est pas prise en charge.</td>
  </tr>
  <tr>  
    <td>UNSUPPORTED_OPERATION</td>
    <td>16</td>
    <td>L'opération n'est pas prise en charge.</td>
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
    <td>L'opération n'est autorisée que pendant la mise en pause.</td>
  </tr>
  <tr> 
    <td>OP_INVALID_WITH_AUDIO_ONLY_FILE</td>
    <td>21</td>
    <td>L'opération ne peut pas être utilisée sur des fichiers audio uniquement.</td>
  </tr>
  <tr>
    <td>PREVIOUS_STEP_SEEK_IN_PROGRESS</td>
    <td>22</td>
    <td>L'opération de recherche précédente est toujours en cours.</td>
  </tr>
  <tr> 
    <td>SOURCE_NOT_SPECIFIED</td>
    <td>23</td>
    <td>Ressource non spécifiée.</td>
  </tr>
  <tr>
    <td>RANGE_ERROR</td>
    <td>24</td>
    <td>La valeur spécifiée est hors limites.</td>
  </tr>
  <tr>
    <td>INVALID_SEEK_TIME</td>
    <td>25</td>
    <td>Heure de recherche non valide.</td>
  </tr>
  <tr>
    <td>FILE_STRUCTURE_INVALID</td>
    <td>26</td>
    <td>Le fichier spécifié n'est pas conforme à la syntaxe attendue.</td>
  </tr>
  <tr>
    <td>COMPONENT_CREATION_FAILURE</td>
    <td>27</td>
    <td>Un composant essentiel n'a pas pu être créé.</td>
  </tr>
  <tr>
    <td>DRM_INIT_ERROR</td>
    <td>28</td>
    <td>Échec de la création du contexte DRM.</td>
  </tr>
  <tr>
    <td>CONTENEUR_NOT_SUPPORTED</td>
    <td>29</td>
    <td>Le type de conteneur n'est pas pris en charge.</td>
  </tr>
  <tr>
    <td>SEEK_FAILED</td>
    <td>30</td>
    <td>Échec de la recherche.</td>
  </tr>
  <tr>
    <td>CODEC_NOT_SUPPORTED</td>
    <td>31</td>
    <td>Codec non pris en charge.</td>
  </tr>
  <tr>
    <td>NETWORK_UNAVAILABLE</td>
    <td>32</td>
    <td>Le réseau n'est pas disponible.</td>
  </tr>
  <tr>  
    <td>NETWORK_ERROR</td>
    <td>33</td>
    <td>Erreur lors de l'obtention des données du réseau.</td>
  </tr>
  <tr>
    <td>DÉBORDEMENT</td>
    <td>34</td>
    <td>Débordement.</td>
  </tr>
  <tr>  
    <td>VIDEO_PROFIL_NOT_SUPPORTED</td>
    <td>35</td>
    <td>Profil vidéo non pris en charge.</td>
  </tr>
  <tr>
    <td>PERIOD_NOT_LOADED</td>
    <td>36</td>
    <td>Une opération a été tentée sur une période HOLD ou une période qui n'a pas encore été chargée.</td>
  </tr>
  <tr> 
    <td>INVALID_REPLACE_DURATION</td>
    <td>37</td>
    <td>La durée de remplacement spécifiée n'est pas valide ou s'étend au-delà de la fin du flux.</td>
  </tr>
  <tr>
    <td>CALLED_FROM_WRONG_THREAD</td>
    <td>38</td>
    <td>L'API ne peut pas être appelée à partir du mauvais thread. Surtout pour les éléments d’API qui doivent être appelés à partir du thread principal uniquement.</td>
  </tr>
  <tr>
    <td>FRAGMENT_READ_ERROR</td>
    <td>39</td>
    <td>Erreur de lecture du fragment. Aucun basculement n'est présent. Le moteur essaiera de lire le fragment suivant.</td>
  </tr>
  <tr>
    <td>ABORDÉ</td>
    <td>40</td>
    <td>L'opération a été abandonnée par un appel explicite d'Abandon ou de Détruire.</td>
  </tr>
  <tr>
    <td>UNSUPPORTED_HLS_VERSION</td>
    <td>41</td>
    <td>Impossible de lire cette version du média HLS.</td>
  </tr>
  <tr>
    <td>CANNOT_FAIL_OVER</td>
    <td>42</td>
    <td>Impossible d'échouer.</td>
  </tr>
  <tr> 
    <td>HTTP_TIME_OUT</td>
    <td>43</td>
    <td>Le téléchargement HTTP a expiré.</td>
  </tr>
  <tr>
    <td>NETWORK_DOWN</td>
    <td>44</td>
    <td>La connexion réseau de l'utilisateur est interrompue. La lecture peut s’arrêter à tout moment et reprendra lorsque la connexion sera disponible.</td>
  </tr>
  <tr>
    <td>NO_USABLE_BITRATE_PROFIL</td>
    <td>45</td>
    <td>Profil de débit binaire utilisable introuvable dans le flux.</td>
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
    <td>Le remplacement spécifié dans une API d'insertion n'a pas pu réussir. Cela signifie que l’insertion a réussi mais que le remplacement n’a pas eu lieu. Le remplacement peut échouer si le manifeste à remplacer a été supprimé du plan de montage chronologique.</td>
  </tr>
  <tr>
    <td>SWITCH_TO_ASYMMETRIC_PROFIL</td>
    <td>49</td>
    <td>DRM passe à un profil asymétrique. Tous les profils devraient être alignés sur la durée. Si ce n’est pas le cas, cet avertissement est généré et la lecture peut être sauterelle.</td>
  </tr>
  <tr>
    <td>LIVE_WINDOW_MOVED_BACKWARD</td>
    <td>50</td>
    <td>La fenêtre active ne doit avancer que. Si ce n'est pas le cas, cet avertissement sera lancé et la fenêtre ne sera pas lue. De ce fait, il peut y avoir des sauts (ou une longue pause/arrêt) dans la lecture.</td>
  </tr>
  <tr>
    <td>CURRENT_PERIOD_EXPIRED</td>
    <td>51</td>
    <td>La fenêtre active a dépassé la période actuelle.</td>
  </tr>
  <tr>
    <td>CONTENT_LENGTH_MISMATCH</td>
    <td>52</td>
    <td>La longueur de contenu signalée par le serveur HTTP ne correspondait pas à la taille réelle du média.</td>
  </tr>
  <tr>
    <td>PERIOD_HOLD</td>
    <td>53</td>
    <td>Le lecteur de médias ne peut pas lire davantage, car il a atteint l’heure définie par l’API setHoldAt.</td>
  </tr>
  <tr>  
    <td>LIVE_HOLD</td>
    <td>54</td>
    <td>Le lecteur de médias ne peut pas charger les segments, car il a atteint la fin de la fenêtre active. Le chargement des segments reprend lorsque le serveur ajoute de nouveaux médias à la fenêtre active. Cet état est généralement atteint si :<ul><li>La valeur bufferTime est trop élevée (égale ou supérieure à la durée de la fenêtre active).</li><li>Une combinaison d’une ou de plusieurs API d’insertion/suppression a remplacé plus de supports qu’elle n’en a ajouté.</li><li>La période suivante est une période de production avec un remplacement de média en attente (en raison de l'appel API InsertBy)</li></ul></td>
  </tr>
  <tr>
    <td>BAD_MEDIA_INTERLEAVING</td>
    <td>55</td>
    <td>L'interception audio et vidéo dans le média n'est pas effectuée correctement. Il s’agit d’une erreur de création de package. L’avertissement est envoyé lorsque la différence dépasse deux secondes.</td>
  </tr>
  <tr>
    <td>DRM_NOT_AVAILABLE</td>
    <td>56</td>
    <td></td>
  </tr>
  <tr>  
    <td>PLAYBACK_NOT_AUTHORIZED</td>
    <td>57</td>
    <td>La lecture HLS n'a pas été activée dans le Flash Player. Voir AuthorizedFeatures.enableHLSPlayback.</td>
  </tr>
  <tr>
    <td>BAD_MEDIA_SAMPLE_FOUND</td>
    <td>78</td>
    <td>Le décodeur a reçu un échantillon incorrect qui ne peut pas être décodé. Il ne s’agit généralement pas d’une erreur fatale, mais indique qu’il peut y avoir des problèmes dans l’audio/la vidéo. Trop d'instances de cette erreur indiquent un mauvais codage ou un fichier incorrect.</td>
  </tr>
  <tr>
    <td>RANGE_SPANS_READ_HEAD</td>
    <td>59</td>
    <td>Une fois la lecture commencée, la plage Insérer/Remplacer ne doit pas contenir le titre de lecture.</td>
  </tr>
  <tr> 
    <td>POSTROLL_WITH_LIVE_NOT_ALLOWED</td>
    <td>60</td>
    <td>Les insertions postroulées ne sont pas autorisées sur un support en direct. Ils sont toutefois autorisés une fois que le serveur a marqué le support comme terminé.</td>
  </tr>
  <tr>
    <td>INTERNAL_ERROR</td>
    <td>61</td>
    <td>Un problème très rare qui ne devrait jamais se produire.</td>
  </tr>
  <tr>  
    <td>SPS_PPS_FOUND_OUTSIDE_AVCC</td>
    <td>62</td>
    <td>Le flux ne suit pas la recommandation d’empaquetage consistant à toujours placer H264 SPS/PPS dans un AVCC. Des problèmes de recherche/lecture peuvent être observés.</td>
  </tr>
  <tr>  
    <td>PARTIAL_REPLACEMENT</td>
    <td>63</td>
    <td>Le remplacement spécifié dans une API d'insertion n'a été effectué que partiellement. Cela se produit lorsque replaceDuration s’étend sur la durée de la chronologie.</td>
  </tr>
  <tr>
    <td>RENDITION_M3U8_ERROR</td>
    <td>64</td>
    <td>La liste de lecture du rendu comportait une erreur de chargement. Il s'agit uniquement d'AVE, et non de FlashPlayer.</td>
  </tr>
  <tr>
    <td>NULL_OPERATION</td>
    <td>65</td>
    <td>L'opération ne fait rien.</td>
  </tr>
  <tr>
    <td>SEGMENT_SKIPPED_ON_FAILURE</td>
    <td>66</td>
    <td>Impossible de lire le segment et est ignoré en cas d'échec.</td>
  </tr>
  <tr>
    <td>INCOMPATIBLE_RENDER_MODE</td>
    <td>67</td>
    <td>Mode de rendu incompatible.</td>
  </tr>
  <tr>
    <td>PROTOCOL_NOT_SUPPORTED</td>
    <td>68</td>
    <td>Le protocole Web utilisé dans l’URL n’est pas pris en charge.</td>
  </tr>
  <tr>
    <td>PARSE_ERROR_INCOMPATIBLE_VERSION</td>
    <td>69</td>
    <td>Erreur lors de l'analyse du fichier multimédia.</td>
  </tr>
  <tr>  
    <td>MANIFEST_FILE_UNEXPECTEDLY_CHANGED</td>
    <td>70</td>
    <td>Le fichier manifeste a été modifié de manière inattendue.</td>
  </tr>
  <tr>
    <td>CANNOT_SPLIT_TIMELINE</td>
    <td>71</td>
    <td>Impossible d'effectuer une opération de fractionnement sur un plan de montage chronologique.</td>
  </tr>
  <tr>
    <td>CANNOT_ERASE_TIMELINE</td>
    <td>72</td>
    <td>Impossible d'effectuer une opération d'effacement sur un plan de montage chronologique.</td>
  </tr>
  <tr>
    <td>DID_NOT_GET_NEXT_FRAGMENT</td>
    <td>73</td>
    <td>N'a pas obtenu le fragment suivant.</td>
  </tr>
  <tr>
    <td>NO_TIMELINE</td>
    <td>74</td>
    <td>Aucune chronologie présente dans une structure de données interne.</td>
  </tr>
  <tr>
    <td>LISTENER_NOT_FOUND</td>
    <td>75</td>
    <td>Aucun écouteur n'a été trouvé dans une structure de données interne.</td>
  </tr>
  <tr>
    <td>AUDIO_DÉBUT_ERROR</td>
    <td>76</td>
    <td>Impossible de début de l'audio.</td>
  </tr>
  <tr>
    <td>NO_AUDIO_SINK</td>
    <td>77</td>
    <td>Aucun récepteur audio présent dans une structure de données interne.</td>
  </tr>
  <tr>  
    <td>FILE_OPEN_ERROR</td>
    <td>78</td>
    <td>Impossible d'ouvrir le fichier.</td>
  </tr>
  <tr>
    <td>FILE_WRITE_ERROR</td>
    <td>79</td>
    <td>Impossible d'écrire dans un fichier.</td>
  </tr>
  <tr>
    <td>FILE_READ_ERROR</td>
    <td>80</td>
    <td>Impossible de lire à partir d'un fichier.</td>
  </tr>
  <tr>
    <td>ID3PARSE_ERROR</td>
    <td>81</td>
    <td>Une erreur s'est produite lors de l'analyse des données ID3.</td>
  </tr>
  <tr>
    <td>SECURITY_ERROR</td>
    <td>82</td>
    <td>Le chargement du contenu a échoué en raison de restrictions de sécurité.</td>
  </tr>
  <tr>
    <td>TIMELINE_TOO_SHORT</td>
    <td>83</td>
    <td>La durée de la chronologie est trop courte. S’il s’agit d’un flux en direct, une mise en mémoire tampon fréquente peut se produire.</td>
  </tr>
  <tr>
    <td>AUDIO_ONLY_STREAM_DÉBUT</td>
    <td>84</td>
    <td>Le flux est passé à un flux audio uniquement.</td>
  </tr>
  <tr>  
    <td>AUDIO_ONLY_STREAM_END</td>
    <td>85</td>
    <td>Le flux est passé d’un flux audio uniquement à un flux vidéo.</td>
  </tr>
  <tr>
    <td>KEY_NOT_FOUND</td>
    <td>87</td>
    <td>Clé introuvable.</td>
  </tr>
  <tr>
    <td>INVALID_KEY</td>
    <td>88</td>
    <td>La clé n'est pas valide.</td>
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
    <td>Discontinuité de temps non signalé (PTS) détectée.</td>
  </tr>
  <tr>
    <td>UNMATCHED_AV_DISCONTINUITY_FOUND</td>
    <td>92</td>
    <td>Discontinuité audio et vidéo inégalée détectée.</td>
  </tr>
  <tr>
    <td>TRICKPLAY_ENDED_DUE_TO_ERROR</td>
    <td>93</td>
    <td>Une erreur s'est produite lors de la lecture du média en mode de lecture par astuces. Le mode de lecture des vidéos est terminé et le flux est suspendu. Appelez Play() pour lire le média en mode normal.</td>
  </tr>
  <tr>
    <td>LIVE_WINDOW_MOVED_AHEAD</td>
    <td>95</td>
    <td>Le joueur est sorti de la fenêtre active et doit chercher à rattraper son retard.</td>
  </tr>
</table>
