---
seo-title: Traiter les demandes DRM Adobe Primetime
title: Traiter les demandes DRM Adobe Primetime
uuid: ee10504d-84f0-472a-b58a-2a87fdeedfc1
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '1251'
ht-degree: 0%

---


# Traiter les demandes DRM Adobe Primetime {#process-adobe-primetime-drm-requests}

La méthode générale de gestion des requêtes consiste à créer un gestionnaire, analyser la requête, définir les données de réponse ou le code d’erreur et fermer le gestionnaire.

La classe de base utilisée pour gérer l&#39;interaction requête/réponse unique est `com.adobe.flashaccess.sdk.protocol.MessageHandlerBase`. Une instance de la classe `HandlerConfiguration` est utilisée pour initialiser le gestionnaire. `HandlerConfiguration` stocke les informations de configuration du serveur, notamment les informations d&#39;identification de transport, la tolérance d&#39;horodatage, les listes de mise à jour de stratégie et les listes de révocation. Le gestionnaire lit les données de demande et analyse la demande dans une instance de  `RequestMessageBase`. L’appelant peut examiner les informations contenues dans la requête et décider s’il doit renvoyer une erreur ou une réponse positive (les sous-classes `RequestMessageBase` fournissent une méthode de définition des données de réponse).

Si la demande aboutit, définissez les données de la réponse ; sinon, appelez `RequestMessageBase.setErrorData()` en cas d’échec. Mettez toujours fin à l&#39;implémentation en appelant la méthode `close()` (il est recommandé d&#39;appeler `close()` dans le bloc `finally` d&#39;une instruction `try`). Consultez la documentation de référence de l&#39;API `MessageHandlerBase` pour un exemple d&#39;appel du gestionnaire.

>[!NOTE]
>
>Le code d’état HTTP 200 (OK) doit être envoyé en réponse à toutes les requêtes traitées par le gestionnaire. Si le gestionnaire n&#39;a pas pu être créé en raison d&#39;une erreur du serveur, le serveur peut répondre avec un autre code d&#39;état, tel que 500 (Erreur interne du serveur).

Le client utilise l’URL du serveur de licences spécifiée au moment du pack comme URL de base pour toutes les requêtes envoyées au serveur de licences. Par exemple, si l’URL du serveur est spécifiée comme &quot;a0/>tps://licenseserver.com/path&lt;a1/&quot;, le client envoie alors des requêtes à &quot;a2/>tps://licenseserver.com/path/flashaccess/...&lt;a3/&quot; Consultez les sections suivantes pour plus d&#39;informations sur le chemin d&#39;accès spécifique utilisé pour chaque type de requête. [!DNL ht<span></span>][!DNL ht<span></span>] Lors de la mise en oeuvre de votre serveur de licences, veillez à ce qu’il réponde aux chemins d’accès requis pour chaque type de requête.

Une demande de licence peut contenir un jeton d’authentification. Si l’authentification par nom d’utilisateur/mot de passe a été utilisée, la demande peut contenir un `AuthenticationToken` généré par `AuthenticationHandler` et le SDK s’assurera que le jeton est valide avant d’émettre une licence.

## Utiliser les identifiants d&#39;ordinateur {#use-machine-identifiers}

Toutes les demandes Adobe Primetime DRM (à l’exception des demandes qui prennent en charge la compatibilité FMRMS) incluent des informations sur le jeton machine qui ont été émises au client lors de l’individualisation. Le jeton machine comprend un ID machine, qui est un identifiant attribué lors de l’individualisation. Vous pouvez utiliser cet identifiant pour comptabiliser le nombre de machines à partir desquelles un utilisateur a demandé une licence ou a rejoint un domaine.

Vous pouvez utiliser un identifiant comme suit :

* La méthode `getUniqueId()` renvoie une chaîne qui a été attribuée à un périphérique lors de l&#39;individualisation. Vous pouvez stocker les chaînes dans une base de données et les rechercher par identifiant. Cependant, cet identifiant change si l&#39;utilisateur reformate le disque dur et se individualise à nouveau. Cet identifiant a également une valeur différente entre Adobe AIR et Flash Player d’Adobe dans différents navigateurs sur la même machine.
* Si vous souhaitez comptabiliser plus précisément les machines, vous pouvez utiliser `getBytes()` pour stocker l&#39;identifiant complet. Pour déterminer si l&#39;ordinateur a été vu auparavant, obtenez tous les identifiants pour un nom d&#39;utilisateur et appelez `matches()` pour vérifier si une correspondance est trouvée. Étant donné que la méthode `matches()` doit être utilisée pour comparer les valeurs renvoyées par `MachineId.getBytes`, cette option n&#39;est pratique que lorsqu&#39;il y a un petit nombre de valeurs à comparer ; par exemple, les machines associées à un utilisateur particulier.

## Authentification de l&#39;utilisateur {#user-authentication}

Une demande Adobe Primetime DRM peut contenir un jeton d’authentification.

Si l&#39;authentification par nom d&#39;utilisateur/mot de passe a été utilisée, la demande peut inclure un `AuthenticationToken` généré par le `AuthenticationHandler`. Si vous souhaitez accéder au jeton et le vérifier, vous devez utiliser `RequestMessageBase.getAuthenticationToken()`. Pour lancer une demande de nom d’utilisateur/mot de passe sur le client, utilisez l’ActionScript `DRMManager.authenticate()` ou l’API iOS.

Si le client et le serveur utilisent un mécanisme d’authentification personnalisé, le client obtient un jeton d’authentification par le biais d’un autre canal et définit le jeton d’authentification personnalisé à l’aide de l’API `DRMManager.setAuthenticationToken` ActionScript 3.0. Utilisez `RequestMessageBase.getRawAuthenticationToken()` pour obtenir le jeton d’authentification personnalisé. L’implémentation du serveur détermine si le jeton d’authentification personnalisé est valide.

## Protection de relecture {#replay-protection}

Pour la protection de la relecture, vous pouvez vérifier si l&#39;identifiant du message a été vu récemment en appelant `RequestMessageBase.getMessageId()`. Si tel est le cas, un attaquant peut essayer de rejouer la requête, ce qui devrait être refusé. Pour détecter les tentatives de relecture, le serveur peut stocker une liste d’identifiants de message récemment vus et vérifier chaque requête entrante par rapport à la liste mise en cache. Pour limiter la durée de stockage des identificateurs de message, appelez `HandlerConfiguration.setTimestampTolerance()`. Si cette propriété est définie, le SDK refuse toute requête qui comporte un horodatage pendant plus de la durée spécifiée en secondes.

## Détection de restauration {#rollback-detection}

Pour la détection de restauration, certaines règles d’utilisation exigent que le client conserve les informations d’état pour l’application des droits. Par exemple, pour appliquer la règle d’utilisation de la fenêtre de lecture, le client stocke la date et l’heure auxquelles l’utilisateur a commencé à consulter le contenu pour la première fois. Ce événement déclenche le début de la fenêtre de lecture. Pour appliquer de manière sécurisée la fenêtre de lecture, le serveur doit s’assurer que l’utilisateur ne sauvegarde pas et ne restaure pas l’état du client afin de supprimer le début de la fenêtre de lecture stocké sur le client. Pour ce faire, le serveur effectue le suivi de la valeur du compteur d’annulation du client.

Pour chaque requête, le serveur obtient la valeur du compteur en appelant `RequestMessageBase.getClientState()` pour obtenir l&#39;objet `ClientState`, puis en appelant `ClientState.getCounter()` pour obtenir la valeur actuelle du compteur d&#39;état client. Le serveur doit stocker cette valeur pour chaque client (utiliser `MachineId.getUniqueId()` pour identifier le client associé à la valeur du compteur d&#39;annulation), puis appeler `ClientState.incrementCounter()` pour augmenter la valeur du compteur de un. Si le serveur détecte que la valeur du compteur est inférieure à la dernière valeur vue par le serveur, l’état du client a peut-être été rétabli.

Consultez la documentation de référence de l&#39;API `ClientState` pour plus d&#39;informations sur la détection des falsificateurs d&#39;état client.

## Données de configuration du serveur global{#global-server-configuration-data}

Outre la configuration utilisée par le serveur de licences, `HandlerConfiguration` stocke les informations de configuration qui peuvent être envoyées au client pour contrôler la manière dont les licences sont appliquées. Pour ce faire, créez une classe `ServerConfigData` et appelez `HandlerConfiguration.setServerConfigData()`. Ces paramètres s’appliquent uniquement aux licences délivrées par ce serveur de licences.

La tolérance au retour à l’arrière-plan de l’horloge est une propriété qui peut être définie par le serveur de licences pour contrôler comment le client applique les licences. Par défaut, les utilisateurs peuvent redéfinir l’horloge de leur ordinateur sur 4 heures sans invalider les licences. Si un opérateur de serveur de licences souhaite utiliser un paramètre différent, la nouvelle valeur peut être définie dans la classe `ServerConfigData`. Lorsque vous modifiez la valeur de l&#39;un de ces paramètres, veillez à incrémenter le numéro de version en appelant `setVersion()`. Les nouvelles valeurs ne sont envoyées au client que si la version du client est antérieure à la version actuelle `ServerConfigData`.

## Fichier de stratégie DRM interdomaines {#crossdomain-drm-policy-file}

Si le serveur de licences est hébergé sur un domaine différent du SWF de lecture vidéo, un fichier de stratégie DRM interdomaines ( [!DNL crossdomain.xml]) est nécessaire pour permettre au SWF de demander des licences à un serveur de licences. Un fichier de stratégie DRM interdomaines est représenté par un fichier XML qui permet au serveur d’indiquer que ses données et documents sont disponibles pour les fichiers SWF fournis à partir d’autres domaines. Tout fichier SWF diffusé à partir d’un domaine spécifié dans le fichier de stratégie DRM interdomaines du serveur de licences est autorisé à accéder aux données ou aux ressources provenant de ce serveur de licences.

L’Adobe recommande aux développeurs de suivre les meilleures pratiques lors du déploiement du fichier de stratégie interdomaines en autorisant uniquement les domaines approuvés à accéder au serveur de licences et en limitant l’accès au sous-répertoire de licences sur le serveur Web.

Pour plus d’informations sur les fichiers de stratégie DRM interdomaines, voir les emplacements suivants :

* Contrôles de site Web (fichiers de stratégie DRM)
* Spécification de fichier de stratégie DRM interdomaines : [https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html](https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html)