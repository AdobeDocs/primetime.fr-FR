---
title: Notes de mise à jour de PTAI 19.11.1
description: Les notes de mise à jour de la version 19.11.1 de l’API décrivent les nouveautés ou les modifications, les problèmes résolus et connus de l’insertion d’annonces dynamiques Primetime en 2019.
translation-type: tm+mt
source-git-commit: ededb36a0b460fff4644a3716b36971ff9454c37

---


# Notes de mise à jour de Primetime Dynamic Ad Insertion 19.11.1

Les notes de mise à jour de la version 19.11.1 de l’insertion dynamique des publicités décrivent les nouveautés ou les modifications, les problèmes résolus et les problèmes connus dans l’insertion dynamique des publicités Primetime en 2019.

## Nouveautés de la version 19.11.1 de l’API

**Lorsque :** Lundi 4 novembre 2019 de 12h01 à 01h00 EST

Mises à jour de maintenance.

## Nouveautés des versions précédentes

### Version 19.10.2

**Lorsque :** Jeudi 31 octobre 2019 de 11h00 à 3h00 heure de l&#39;Est

Mises à jour de maintenance.

### Version 19.10.1

**Lorsque :**  Mardi 22 octobre de 11h00 à 02h00 EST

Mises à jour de maintenance.

### Version 19.9.1

**Lorsque :** Mardi 10 septembre 2019 de 12h30 à 2h00 heure de l&#39;Est

Mises à jour de sécurité

### Version 19.8.3

**Lorsque :** Mercredi 28 août 2019, de 12h30 à 1h30 heure de l&#39;EST

Correction d’un bogue en raison duquel les lecteurs Chromecast quittaient la lecture de manière inattendue lorsque les segments d’annonces sortaient de la fenêtre du DVR.

### Version 19.8.2

**Lorsque :** Mercredi 21 août 2019 De 2 h à 3 h, heure de l&#39;Est

* SSAI  : Statistiques de session. Vous pouvez exporter le de session  via l’option Télécharger CSV.
* Mises à jour de maintenance

### Version 19.8.1

**Lorsque :** Mardi 6 août 2019 2:30 heure de l&#39;Est au mardi 6 août 2019 4:30 heure de l&#39;Est

* SSAI  : Ajout d’une nouvelle section, Statistiques de session, au SSAI 
   * Si vous disposez de l’ID de session pour une session SSAI pour laquelle le mode de débogage était activé (ptdebug=true), vous pourrez rechercher l’ de  suivante qui s’est produite au cours de cette session :
      * Demandes/réponses d’annonce
      * Publicités insérées
      * Balises déclenchées (suivi côté serveur uniquement)
   * Vous pouvez rechercher   pour un ID de session spécifique jusqu’à 30 jours après la session SSAI.
   * Vous pouvez exporter le 
* Base de données : Mises à jour de sécurité

### Version 19.7.1

**Lorsque :** Mercredi 10 juillet

* SSAI : Pour les valeurs ptcueformat qui prennent en charge le signal de coupure publicitaire EXT-X-CUE-OUT dans les flux en direct, ajoutez une macro générique pour transmettre les données des attributs dans la balise EXT-X-ASSET Exemple : Balise accompagnant la balise #EXT-X-CUE-OUT : #EXT-X-ASSET:CAID=75BCD15,GENRE=News,=NewsAt10 Macros : # peut être utilisé pour transmettre des informations (de l&#39;attribut GENRE) à une URL d&#39;appel publicitaire # peut être utilisé pour transmettre NewsAt10 (de l&#39;attribut  du) à une exception d&#39;URL d&#39;appel publicitaire : Pour la compatibilité descendante, # et # ont la même fonctionnalité. Les deux macros peuvent être utilisées pour transmettre la valeur de l’attribut CAID, après avoir converti la valeur de hex en long La valeur longue est 123456789 pour la valeur hexadécimale, 75BCD15, dans l’exemple ci-dessus. Les deux macros seraient utilisées pour transmettre 123456789 à une URL d’appel publicitaire. La macro  toujours avec #. La macro est sensible à la casse, mais l’attribut de la balise EXT-X-ASSET ne l’est pas. En d’autres termes, les  et les  de sont tous deux autorisés dans la balise EXT-X-ASSET.
* SSAI : Changements de configuration pour un client spécifique pour les éléments suivants :
   * Longueur de la fenêtre coulissante (liste de lecture en direct) de quatre minutes
   * Si une exception de délai d’expiration du socket est générée lorsque le serveur Manifest récupère le contenu source, le serveur Manifest renvoie le code de réponse HTTP (404) au lieu de 500.
* Mises à jour de sécurité

### Version 19.6.1

**Lorsque :** Mercredi, 12 juin 2019 11h30 (heure du Pacifique) au jeudi 13 juin 2019 12h30 (heure du Pacifique)

* CRS: Règle de normalisation pour les créatifs de RevJet
   * Ajout d’une règle de normalisation des URL créatives pour RevJet, utilisée par CRS et SSAI
   * TVSDK : Si vous servez ou prévoyez de diffuser des publicités de RevJet, des règles de normalisation devront être ajoutées aux règles SIR JSON pour utiliser CRS avec leurs créatifs. Contactez votre gestionnaire de compte technique pour obtenir de l’aide.
* CRS: Règle de normalisation pour les créatifs d&#39;Innovid
   * Ajout d’une règle de normalisation des URL créatives pour Innovid, utilisée par SSAI
   * La règle de normalisation utilisée par CRS a été ajoutée dans une version précédente.
   * TVSDK : La règle de normalisation à ajouter dans le fichier JSON des règles CRS a été fournie après une version antérieure, mais pour être en sécurité, contactez votre gestionnaire de compte technique pour examiner toutes les règles de normalisation que vous avez en place.
      >[!NOTE]
      >
      >La plupart des URL de création Innovid seront transcodées et assemblées avec succès sans la règle de normalisation. Il arrive toutefois que des URL créatives Innovid avec des paramètres dynamiques soient rencontrées. La règle de normalisation est nécessaire pour gérer ces instances.

### Version 19.5.2

**Lorsque :** Mercredi, 22 mai 2002, 02h30, heure de l&#39;Est, au mercredi 22 mai, 04h30, heure de l&#39;Est

* Ajout de la prise en charge de CMAF (contenu HLS/fMP4)
   * SSAI : Manipulation des manifestes CMAF
   * SSAI : Lancer des demandes de transcodage et récupérer des fichiers CRS en fonction du format de contenu (HLS/ts et HLS/fMP4)
   * CRS: Ajout d’un flux de travail pour recompresser les publicités au format CMAF (HLS/fMP4)
* SSAI : Correction d’un problème qui empêchait l’insertion de publicités non muxes dans du contenu non muxé, lorsque le contenu et la publicité n’avaient pas de flux audio uniquement (EXT-X-STREAM-INF).
* SSAI : Ajout de la prise en charge des jetons d’authentification CDN Limelight (LLNW) pour les segments de contenu
   * Lorsque `pttoken=limelight` ou `pttoken=llnw` est ajouté à l’URL d’amorçage, nous ajouterons un en-tête secret lors de la récupération de la liste de lecture principale source, puis nous ajouterons les paramètres de  de l’en-tête X-Adobe-Sig du LLNW aux segments de contenu.
* SSAI : Ajout d’une autre valeur de jeton (`pttoken=centurylink`) pour la prise en charge du jeton d’authentification CDN CenturyLink, publiée le 30 juillet 2018
   * `pttoken=centurylink` a le même comportement que `pttoken=level3`, et les deux valeurs sont valides

### Version 19.5.1

**Lorsque :** Jeudi 9 mai 02h30 heure de l&#39;Est au jeudi 9 mai 04h30 heure de l&#39;Est

* SSAI : Mises à jour de sécurité
* CRS  : La chaîne &quot;FqAdId Sample&quot; a été tronquée à 255 caractères en raison de  de données  contraintes de (8 bits).
   * La chaîne &quot;FqAdId Sample&quot; comprend le système d’annonce et l’identifiant de publicité de chaque réponse XML de la chaîne d’encapsulage de l’annonce pour les insertions de toutes les publicités CRS avec l’interface SSAI (section Statistiques créatives du CRS).
* SSAI et CRS : Mises à jour des versions logicielles

### Version 19.4.1

**Lorsque :** Mercredi, 10 avril 02h30 heure de l&#39;Est au mercredi 10 avril 04h30 heure de l&#39;Est

* CRS: L’API de reconditionnement CRS ne prend plus en charge les commandes HTTP POST. L’API de reconditionnement CRS redirigera automatiquement (301) les commandes HTTP POST vers HTTPS.
   * À compter du 20 mai, la redirection HTTP->HTTPS pour les commandes HTTP POST sera désactivée.
   * Si vous utilisez l’API de reconditionnement CRS pour recompresser les publicités à l’avance, basculez vos commandes POST sur HTTPS d’ici le 20 mai.
* CRS: Nouvelle architecture et flux de travail pour le transfert des ressources CRS vers les CDN des clients 
   * Les processus de tâche par CDN   sont séparés, de sorte que les goulets d’étranglement de transfert pour un CDN  n’affectent pas les téléchargements vers d’autres CDN
   * Autres avantages : Les temps de traitement des tâches CRS et les taux de transfert vers les CDN des clients sont améliorés.
* SSAI : Ajout d’URL ClickThrough et ClickTracking pour les annonces vidéo au format JSON v2 sidecar
   * Une nouvelle propriété de tableau JSON, &quot;videoClicks&quot;, suivra la propriété &quot;trackingURLs&quot;.
   * Les noms de valeur &quot;&quot; seront &quot;clickThrough&quot; et &quot;clickTracking&quot;, et ils n’auront pas de valeur startTime.
* SSAI : Pour les actifs CRS, ajout d’une fonctionnalité permettant d’étendre l’expiration des enregistrements de recherche d’un actif CRS de 30 jours chaque fois qu’il est inséré
   * Comportement précédent : Les enregistrements de recherche de ressources CRS sont stockés dans memcache dans chaque capsule. Les enregistrements de recherche de ressources CRS sont automatiquement supprimés 30 jours après avoir été ajoutés à memcache. Pour remplir à nouveau l’enregistrement de recherche de ressources CRS d’un créatif dans un module après sa suppression de memcache, ce créatif doit être rencontré 3 fois dans ce module.
   * Nouveau comportement : Lorsqu’un conteneur accède à un enregistrement de recherche de fichier CRS afin d’insérer l’actif CRS, l’expiration de l’enregistrement de recherche de fichier CRS est prolongée de 30 jours dans ce conteneur. Par conséquent, les fichiers CRS fréquemment utilisés ne seront pas supprimés du cache de mémoire d’un module avant 30 jours après son utilisation la plus récente.
   * Le nouveau comportement est à l’échelle du système et peut être désactivé si une baisse de performances est détectée.
* SSAI : Comportement de manipulation de manifeste WebVTT mis à jour pour les flux en direct uniquement
   * Comportement précédent : Dans le manifeste WebVTT uniquement, supprimez les balises EXT-X-DISCONTINUITY qui seraient insérées avant chaque publicité insérée et après le dernier segment de la coupure publicitaire insérée.
   * Nouveau comportement : Ajout d’un nouveau paramètre, vttdisk, avec des valeurs acceptées de true et false, à l’URL d’amorçage SSAI.
      * vttdisc=true : Les balises EXT-X-DISCONTINUITY seront insérées dans le manifeste WebVTT avant chaque publicité insérée et après le dernier segment de coupure publicitaire insérée, ce qui correspond au comportement des manifestes audio/vidéo et audio uniquement.
      * vttdisc=false (identique au comportement précédent) : Dans le manifeste WebVTT uniquement, supprimez les balises EXT-X-DISCONTINUITY qui seraient insérées avant chaque publicité insérée et après le dernier segment de la coupure publicitaire insérée.
      * Si le paramètre vttdisk est omis ou a une valeur autre que true/false, vttdisk est défini par défaut sur true.
* SSAI : Mises à jour de sécurité et mises à jour des versions logicielles
   * Java : Mise à jour de la version Java afin de prendre en charge les suites de chiffrement supplémentaires pour les appels publicitaires déclenchés via TLS 1.2 (HTTPS)

### Version 19.2.1

**Lorsque :** Mercredi 20 février 2019 1 h 30 heure de l&#39;Est au mercredi 20 février 2019 3 h 30 heure de l&#39;Est

* SSAI : Ajout d’URL ClickThrough et ClickTracking pour les annonces vidéo au format JSON v2 sidecar
   * Sous la propriété &quot;trackingURLs&quot;, leurs noms de valeur &quot;&quot; seront &quot;clickthrough&quot; et &quot;clickTracking&quot;.
   * Leurs valeurs startTime seront le début de la publicité
* SSAI : Pour les actifs CRS, ajout d’une fonctionnalité permettant d’étendre l’expiration des enregistrements de recherche d’un actif CRS de 30 jours chaque fois qu’il est inséré
   * Comportement précédent : Les enregistrements de recherche de ressources CRS sont stockés dans memcache dans chaque capsule. Les enregistrements de recherche de ressources CRS sont automatiquement supprimés 30 jours après avoir été ajoutés à memcache. Pour remplir à nouveau l’enregistrement de recherche de ressources CRS d’un créatif dans un module après sa suppression de memcache, ce créatif doit être rencontré 3 fois dans ce module.
   * Nouveau comportement : Lorsqu’un conteneur accède à un enregistrement de recherche de fichier CRS afin d’insérer l’actif CRS, l’expiration de l’enregistrement de recherche de fichier CRS est prolongée de 30 jours dans ce conteneur. Par conséquent, les fichiers CRS fréquemment utilisés ne seront pas supprimés du cache de mémoire d’un module avant 30 jours après son utilisation la plus récente.
   * Le nouveau comportement est à l’échelle du système et peut être désactivé si une baisse de performances est détectée.

* SSAI : Mises à jour des versions logicielles pour NGINX et Kafka
   * NGINX et Kafka sont utilisés pour déclencher des URL de suivi des publicités côté serveur et transmettre des données au SSAI et CRS 
* CRS: Amélioration des performances du CRS 

### Version de l’interface utilisateur Web

**Lorsque :** Mercredi 13 février, de 4 h à 4 h 30 Pacifique

**Quoi :** Composant d&#39;interface Web Primetime et de prise de décision

* Correction d’un problème de l’interface utilisateur du calendrier en raison duquel l’utilisateur ne pouvait pas sélectionner une date au-delà du 31 décembre 2018 dans le composant Calendrier pendant le trafic d’une campagne ou la génération d’un rapport.

### Version 19.1.2

**Lorsque :** Mercredi 30 janvier 2019 1:30 heure de l&#39;Est au mercredi 30 janvier 3:30 heure de l&#39;Est

* SSAI : Mise à jour de la structure de clé de recherche utilisée par SSAI pour stocker et récupérer les ressources CRS, afin de gérer les scénarios dans lesquels les fournisseurs d’annonces ont un ID d’annonce dynamique ou un ID créatif pour la même publicité
   * Nouvelle structure de clé de recherche : Paramètres de zone, d’URL créative et de format (durée  du, format de sortie, CDN de destination)
   * Ancienne structure de clé de recherche : Zone, système publicitaire, ID de publicité, ID créatif, URL créative et paramètres de format (durée de  du, format de sortie, CDN de destination)
   * Les clés de recherche des ressources CRS existantes seront mises à jour pour correspondre à la nouvelle structure avant la version de production, mais notez que les nouvelles ressources transcodées entre la mise à jour des clés de recherche et la version de production pourraient être manquantes. Si c&#39;est le cas, ils lanceraient une nouvelle demande de CRS la prochaine fois qu&#39;ils seront rencontrés après la libération.

* CRS: Ajout de la possibilité de mettre en liste noire/liste blanche les requêtes CRS provenant de systèmes publicitaires spécifiques, d’ID de publicité, d’ID de création, d’URL de création et/ou de format créatif

   >Note
   >
   >Adobe ajoute des règles de liste noire lorsque des fournisseurs d’annonces avec des valeurs dynamiques (paramètre dynamique dans l’URL, par exemple) pour la même publicité sont trouvés. Ces règles de liste noire seront désactivées une fois le composant dynamique résolu, soit par le fournisseur, soit par le biais d’une règle de normalisation.

   * Si vous souhaitez ajouter une liste noire ou une règle de liste blanche pour votre zone, contactez votre gestionnaire de compte technique pour obtenir de l’aide.

### Version 19.1.1

**Lorsque :** Mercredi 9 janvier 2019 1 h 30 heure de l&#39;Est au mercredi 9 janvier 3 h 30 heure de l&#39;Est

* Correction d’un problème en raison duquel une interprétation erronée des en-têtes HTTP keep-alive pouvait générer une erreur lors de la validation des ressources créatives entrantes hébergées sur total-stream.net.
* Correction d’un problème en raison duquel les guillemets simples (’) et les guillemets (&quot;) dans l’ID de publicité, l’ID créatif et d’autres champs pour une demande de reconditionnement entraînaient l’échec de la demande de reconditionnement.
* Basculé sur Java long (type de données) pour résoudre un problème en raison duquel l’atteinte de la limite Java int de 2 147 483 647 dans les valeurs d’ID de tâche de transcodage provoquerait l’échec de toutes les demandes de reconditionnement.
* Optimisations de base de données.

## Problèmes résolus

Lorsque la résolution est associée à un problème signalé, une référence Zendesk s’affiche. Par exemple, ZD#xxxxx.

**PTAI 19.7.1**

ZD#37503 - Les réponses Json pour les règles CRS sont mises en cache afin d’éviter les demandes de  du.

## Problèmes et limites connus

**PTAI 19.7.1**

Aucune nouvelle limitation n’a été ajoutée.
