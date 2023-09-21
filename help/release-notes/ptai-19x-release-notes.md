---
title: Notes de mise à jour de PTAI 19.11.1
description: Les notes de mise à jour de PTAI 19.11.1 décrivent les nouveautés ou les modifications, les problèmes résolus et connus de l’Ad Insertion Primetime en 2019.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1971'
ht-degree: 0%

---

# Notes de mise à jour de Primetime Ad Insertion 19.11.1

Les notes de mise à jour de l’Ad Insertion Primetime 19.11.1 décrivent les nouveautés ou les modifications, les problèmes résolus et les problèmes connus de l’Ad Insertion Primetime en 2019.

## Nouveautés de l’API 19.11.1

**Lorsque :** Lundi 4 novembre 2019 de 12h01 à 01h00 EST

Mises à jour de maintenance.

## Changements dans les versions précédentes

### Version 19.10.2

**Lorsque :** Jeudi 31 octobre 2019 de 01h00 à 03h00, est

Mises à jour de maintenance.

### Version 19.10.1

**Lorsque :**  Mardi 22 octobre à 01h00 à 02h00 EST

Mises à jour de maintenance.

### Version 19.9.1

**Lorsque :** Mardi 10 septembre 2019 à 12h30 à 2h00, heure de l’Est

Mises à jour de sécurité

### Version 19.8.3

**Lorsque :** Mercredi 28 août 2019, de 12h30 à 1h30 heure de l’EST

Correction d’un bogue en raison duquel les lecteurs Chromecast quittaient inopinément la lecture lorsque les segments de publicité étaient déployés hors de la fenêtre du contenu numérique (DVR).

### Version 19.8.2

**Lorsque :** Mercredi 21 août 2019 de 02h00 à 03h00, heure de l’Est

* Tableau de bord SSAI : section Statistiques de session . Vous pouvez exporter les événements de session via l’option Télécharger CSV .

* Mises à jour de maintenance

### Version 19.8.1

**Lorsque :** Mardi 6 août 2019 à 14 h 30, heure de l’Est, et mardi 6 août 2019 à 4 h 30, heure de l’Est

* Tableau de bord SSAI : ajout d’une nouvelle section, Statistiques de session, au tableau de bord SSAI.
   * Si vous disposez de l’ID de session pour une session SSAI pour laquelle le mode de débogage était activé (ptdebug=true), vous pourrez rechercher l’activité suivante qui s’est produite au cours de cette session :
      * Requêtes/réponses de publicité
      * Publicités insérées
      * Balises déclenchées (suivi côté serveur uniquement)

   * Vous pouvez rechercher une activité pour un ID de session spécifique jusqu’à 30 jours après que la session SSAI ait eu lieu.
   * Vous pouvez exporter les événements
* Base de données : mises à jour de sécurité

### Version 19.7.1

**Lorsque :** Mercredi 10 juillet

* SSAI : Pour les valeurs ptcueformat qui prennent en charge le signalement de coupure publicitaire EXT-X-CUE-OUT dans les flux en direct, ajout d’une macro générique pour transmettre des données à partir des attributs dans la balise EXT-X-ASSET Exemple : balise qui accompagne la balise #EXT-X-CUE-OUT : #EXT-X-ASSET:CAID=75BCD15,GENRE=News,Program=NewsAt10 Macros: # peut être utilisé pour transmettre des nouvelles (de l’attribut GENRE) à un numéro d’URL d’appel publicitaire peut être utilisé pour transmettre NewsAt10 (de l’attribut Program) à une exception d’URL d’appel publicitaire : pour une compatibilité descendante, # et # ont la même fonctionnalité. Les deux macros peuvent être utilisées pour transmettre la valeur de l’attribut CAID, après avoir converti la valeur de hex en long La valeur long est 123456789 pour la valeur hexadécimale, 75BCD15, dans l’exemple ci-dessus. Les deux macros sont utilisées pour transmettre 123456789 à une URL d’appel publicitaire. La macro commence toujours par #. La macro est sensible à la casse, mais l’attribut de la balise EXT-X-ASSET ne l’est pas. Autrement dit, les programmes et les programmes sont tous deux autorisés dans la balise EXT-X-ASSET .
* SSAI : modifications de configuration pour un client spécifique pour les éléments suivants :
   * Durée de quatre minutes de la fenêtre glissante (lecture en direct)
   * Si une exception de délai d’expiration de socket est générée lorsque le serveur Manifest récupère le contenu source, le serveur Manifest renvoie le code de réponse HTTP (404) au lieu de 500.
* Mises à jour de sécurité

### Version 19.6.1

**Lorsque :** Mercredi 12 juin 2019 23h30 PST au jeudi 13 juin 2019 12h30 PST

* CRS : règle de normalisation pour les créatifs de RévJet
   * Ajout d’une règle de normalisation d’URL créative pour RévJet, utilisée par CRS et SSAI.
   * TVSDK : si vous diffusez ou prévoyez de diffuser des publicités à partir de RévJet, des règles de normalisation devront être ajoutées aux règles CRS JSON pour utiliser CRS avec leurs créatifs. Contactez votre gestionnaire de compte technique pour obtenir de l’aide.
* CRS : règle de normalisation pour les créatifs d&#39;Innovid
   * Ajout d’une règle de normalisation d’URL créative pour Innovid, utilisée par SSAI.
   * La règle de normalisation utilisée par CRS a été ajoutée dans une version précédente.
   * TVSDK : la règle de normalisation à ajouter au fichier JSON des règles CRS a été fournie après une version précédente. Pour être en sécurité, contactez votre gestionnaire de compte technique pour passer en revue toutes les règles de normalisation que vous avez mises en place.
     >[!NOTE]
     >
     >La plupart des URL créatives Innovid seront transcodées et assemblées avec succès sans la règle de normalisation. Toutefois, il arrive parfois que des URL créatives Innovid avec des paramètres dynamiques soient rencontrées. La règle de normalisation est nécessaire pour gérer ces instances.

### Version 19.5.2

**Lorsque :** Mercredi 22 mai à 02h30, heure de l’Est, et mercredi 22 mai à 04h30, heure de l’Est

* Ajout de la prise en charge de CMAF (contenu HLS/fMP4)
   * SSAI : gérer les manifestes CMAF
   * SSAI : lancer des demandes de transcodage et récupérer des ressources CRS en fonction du format de contenu (HLS/ts et HLS/fMP4)
   * CRS : ajout d’un workflow pour recompresser les publicités au format CMAF (HLS/fMP4)
* SSAI : correction d’un problème qui empêchait l’insertion de publicités non muxées dans du contenu non muxé, lorsque le contenu et la publicité n’avaient pas de flux audio uniquement (EXT-X-STREAM-INF).
* SSAI : ajout de la prise en charge des jetons d’authentification CDN Limelight (LLNW) pour les segments de contenu.
   * When `pttoken=limelight` ou `pttoken=llnw` est ajouté à l’URL de bootstrap. Nous ajouterons un en-tête secret lors de la récupération de la liste de lecture principale source, puis nous ajouterons les paramètres de requête de l’en-tête X-Adobe-Sig de LLNW aux segments de contenu.
* SSAI : ajout d’une autre valeur de jeton (`pttoken=centurylink`) pour la prise en charge du jeton d’authentification CDN CenturyLink, publiée le 30 juillet 2018
   * `pttoken=centurylink` a le même comportement que `pttoken=level3`et que les deux valeurs sont valides.

### Version 19.5.1

**Lorsque :** Jeudi 9 mai 02 h 30, heure de l’Est, au jeudi 9 mai 04 h 30, heure de l’Est

* SSAI : Mises à jour de sécurité
* Tableau de bord CRS : chaîne &quot;Exemple FqAdId&quot; tronquée à 255 caractères en raison de contraintes de stockage des données (8 bits)
   * La chaîne &quot;Exemple FqAdId&quot; comprend le système d’annonces et l’identifiant de l’annonce de chaque réponse XML de la chaîne de wrapper de l’annonce pour les insertions de toutes les publicités CRS avec l’interface utilisateur unique (section Statistiques créatives du tableau de bord CRS).
* Tableaux de bord SSAI et CRS : mises à jour de version logicielle

### Version 19.4.1

**Lorsque :** Mercredi 10 avril à 02h30, heure de l’Est, puis mercredi 10 avril à 04h30, heure de l’Est

* CRS : l’API de reconditionnement CRS ne prendra plus en charge les commandes du POST HTTP. L’API de reconditionnement CRS redirigera automatiquement (301) les commandes du POST HTTP vers HTTPS.
   * À compter du 20 mai, la redirection HTTP->HTTPS pour les commandes du POST HTTP sera désactivée.
   * Si vous utilisez l’API de repackage CRS pour recompresser les publicités à l’avance, basculez vos commandes de POST sur HTTPS d’ici le 20 mai.
* CRS : restructuration de l’architecture et du workflow de chargement de ressources CRS vers les origines CDN des clients.
   * Les processus de tâche par origine CDN sont séparés, de sorte que les goulets d’étranglement de chargement pour une origine CDN n’affectent pas les chargements vers d’autres origines CDN.
   * Autres avantages : les temps de traitement des tâches CRS et les taux de transfert vers les origines CDN des clients sont améliorés.
* SSAI : ajout des URL ClickThrough et ClickTracking pour les publicités vidéo au format sidecar JSON v2
   * Une nouvelle propriété de tableau JSON, &quot;videoClicks&quot;, suit la propriété &quot;trackingURLs&quot;.
   * Les noms des valeurs &quot;event&quot; sont &quot;clickThrough&quot; et &quot;clickTracking&quot;, et ils n’ont pas de valeur startTime
* SSAI : pour les ressources CRS, ajout d’une fonctionnalité permettant d’étendre l’expiration de l’enregistrement de recherche d’une ressource CRS de 30 jours chaque fois qu’elle est insérée.
   * Comportement précédent : les enregistrements de recherche de ressources CRS sont stockés dans memcache dans chaque capsule. Les enregistrements de recherche de ressources CRS sont automatiquement supprimés 30 jours après avoir été ajoutés au cache mémoire. Pour reremplir l’enregistrement de recherche de ressources CRS d’un créatif dans une capsule après sa suppression de memcache, ce créatif doit être rencontré trois fois dans cette capsule.
   * Nouveau comportement : lorsqu’un module accède à un enregistrement de recherche de ressources CRS pour insérer la ressource CRS, l’expiration de l’enregistrement de recherche de ressources CRS est prolongée de 30 jours dans cette capsule. Par conséquent, les ressources CRS qui sont fréquemment utilisées ne seront pas supprimées du mémoire cache d’une capsule avant 30 jours après sa dernière utilisation.
   * Le nouveau comportement est à l’échelle du système et peut être désactivé si une baisse de performances est détectée.
* SSAI : mise à jour du comportement de manipulation de manifeste WebVTT pour les diffusions en direct uniquement
   * Comportement précédent : dans le manifeste WebVTT uniquement, supprimez les balises EXT-X-DISCONTINUITY qui seraient insérées avant chaque publicité insérée et après le dernier segment de la coupure publicitaire insérée.
   * Nouveau comportement : ajout d’un nouveau paramètre, vttdisk, avec les valeurs acceptées true et false, à l’URL de l’amorçage de l’interface utilisateur (SSAI).
      * vttdisk=true : les balises EXT-X-DISCONTINUITY seront insérées dans le manifeste WebVTT avant chaque publicité insérée et après le dernier segment de la coupure publicitaire insérée, ce qui correspond au comportement des manifestes audio/vidéo et audio uniquement.
      * vttdisk=false (même que le comportement précédent) : dans le manifeste WebVTT uniquement, supprimez les balises EXT-X-DISCONTINUITY qui seraient insérées avant chaque publicité insérée et après le dernier segment de la coupure publicitaire insérée.
      * Si le paramètre vttdisk est omis ou a une valeur autre que true/false, vttdisk est défini par défaut sur true.
* SSAI : Mises à jour de sécurité et mises à jour des versions logicielles
   * Java : mise à jour de la version Java afin de prendre en charge des suites de chiffrement supplémentaires pour les appels publicitaires déclenchés via TLS 1.2 (HTTPS).

### Version 19.2.1

**Lorsque :** Mercredi 20 février 2019 à 1 h 30, heure de l’Est, jusqu’au mercredi 20 février 2019 à 3 h 30, heure de l’Est

* SSAI : ajout des URL ClickThrough et ClickTracking pour les publicités vidéo au format sidecar JSON v2
   * Sous la propriété &quot;trackingURLs&quot;, leurs noms de valeur &quot;event&quot; seront &quot;clickthrough&quot; et &quot;clickTracking&quot;.
   * Leurs valeurs startTime seront le début de la publicité.
* SSAI : pour les ressources CRS, ajout d’une fonctionnalité permettant d’étendre l’expiration de l’enregistrement de recherche d’une ressource CRS de 30 jours chaque fois qu’elle est insérée.
   * Comportement précédent : les enregistrements de recherche de ressources CRS sont stockés dans memcache dans chaque capsule. Les enregistrements de recherche de ressources CRS sont automatiquement supprimés 30 jours après avoir été ajoutés au cache mémoire. Pour reremplir l’enregistrement de recherche de ressources CRS d’un créatif dans une capsule après sa suppression de memcache, ce créatif doit être rencontré trois fois dans cette capsule.
   * Nouveau comportement : lorsqu’un module accède à un enregistrement de recherche de ressources CRS pour insérer la ressource CRS, l’expiration de l’enregistrement de recherche de ressources CRS est prolongée de 30 jours dans cette capsule. Par conséquent, les ressources CRS qui sont fréquemment utilisées ne seront pas supprimées du mémoire cache d’une capsule avant 30 jours après sa dernière utilisation.
   * Le nouveau comportement est à l’échelle du système et peut être désactivé si une baisse de performances est détectée.

* SSAI : Mises à jour de la version logicielle de NGINX et Kafka
   * NGINX et Kafka sont utilisés pour déclencher des URL de suivi des publicités côté serveur et envoyer des données aux tableaux de bord SSAI et CRS.
* CRS : améliorations des performances du tableau de bord CRS.

### Version de l’interface utilisateur web

**Lorsque :** Mercredi 13 février de 4 h à 4 h 30 Pacifique

**Quoi :** Composant de l’interface utilisateur web de Primetime et Decisioning

* Correction d’un problème de l’interface utilisateur du calendrier en raison duquel l’utilisateur ne pouvait pas sélectionner une date au-delà du 31 décembre 2018 dans le composant Calendrier lors du trafic d’une campagne ou de l’extraction d’un rapport.

### Version 19.1.2

**Lorsque :** Mercredi 30 janvier 2019 de 1 h 30, heure de l’Est, à mercredi 30 janvier 3 h 30, heure de l’Est

* SSAI : mise à jour de la structure de clé de recherche utilisée par SSAI pour stocker et récupérer les ressources CRS, afin de gérer les scénarios où les fournisseurs d’annonces ont un ID de publicité dynamique ou un ID de création pour la même publicité.
   * Nouvelle structure de clé de recherche : Zone, URL créative et paramètres de format (durée de cible, format de sortie, réseau de diffusion de contenu de destination)
   * Ancienne structure de clé de recherche : zone, système publicitaire, identifiant publicitaire, identifiant créatif, URL créative et paramètres de format (durée cible, format de sortie, réseau de diffusion de contenu de destination)
   * Les clés de recherche des ressources CRS existantes seront mises à jour pour correspondre à la nouvelle structure avant la version de production, mais notez que les nouvelles ressources codées entre la mise à jour des clés de recherche et la version de production peuvent être manquées. Si c’est le cas, ils lanceront une nouvelle demande CRS la prochaine fois qu’ils seront rencontrés après la version.

* CRS : ajout de la capacité de liste bloquée/liste autorisée des requêtes CRS provenant de systèmes publicitaires spécifiques, d’identifiants publicitaires, d’identifiants créatifs, d’URL créatives et/ou de format créatif.

  >Remarque
  >
  >Adobe ajoute des règles de liste bloquée lorsque des fournisseurs d’annonces avec des valeurs dynamiques (par exemple, un paramètre dynamique dans l’URL) pour la même publicité sont trouvés. Ces règles de liste bloquée seront désactivées une fois le composant dynamique résolu, soit par le fournisseur, soit par une règle de normalisation.

   * Si vous souhaitez ajouter une règle de liste bloquée ou de liste autorisée pour votre zone, contactez votre gestionnaire de compte technique pour obtenir de l’aide.

### Version 19.1.1

**Lorsque :** Mercredi 9 janvier 2019 de 1 h 30, heure de l’Est, à mercredi 9 janvier 3 h 30, heure de l’Est

* Correction d’un problème en raison duquel une mauvaise interprétation des en-têtes HTTP de maintien en vie pouvait entraîner une erreur lors de la validation des ressources créatives entrantes hébergées sur total-stream.net.
* Correction d’un problème en raison duquel les guillemets simples (&#39;) et les guillemets doubles (&quot;) dans l’ID de publicité, l’ID créatif et d’autres champs pour une demande de reconditionnement provoquaient l’échec de la demande de reconditionnement.
* Basculez vers Java long (type de données) pour résoudre un problème en raison duquel l’atteinte de la limite Java int de 2 147 483 647 dans les valeurs d’ID de tâche de transcodage provoquait l’échec de toutes les demandes de reconditionnement.
* Optimisations de la base de données.

## Problèmes résolus

Lorsque la résolution est associée à un problème signalé, une référence Zendesk s’affiche. Par exemple, ZD#xxxxx.

**PTAI 19.7.1**

ZD#37503 - Les réponses Json des règles CRS sont mises en cache afin d’éviter la duplication des requêtes.

## Problèmes connus et limites

**PTAI 19.7.1**

Aucune nouvelle limitation n’a été ajoutée.
