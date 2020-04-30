---
seo-title: Traiter les requêtes DRM Adobe Primetime
title: Traiter les requêtes DRM Adobe Primetime
uuid: ee10504d-84f0-472a-b58a-2a87fdeedfc1
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Traiter les requêtes DRM Adobe Primetime {#process-adobe-primetime-drm-requests}

La méthode générale de gestion des requêtes consiste à créer un gestionnaire, analyser la requête, définir les données de réponse ou le code d’erreur et fermer le gestionnaire.

La classe de base utilisée pour gérer l&#39;interaction requête/réponse unique est `com.adobe.flashaccess.sdk.protocol.MessageHandlerBase`. Une instance de la `HandlerConfiguration` classe est utilisée pour initialiser le gestionnaire. `HandlerConfiguration` stocke les informations de configuration du serveur, notamment les informations d&#39;identification de transport, la tolérance d&#39;horodatage, les listes de mise à jour de stratégie et les listes de révocation. Le gestionnaire lit les données de demande et analyse la demande dans une instance de `RequestMessageBase`. L’appelant peut examiner les informations contenues dans la requête et décider s’il doit renvoyer une erreur ou une réponse positive (les sous-classes de `RequestMessageBase` fournissent une méthode de définition des données de réponse).

Si la demande aboutit, définissez les données de la réponse ; dans le cas contraire, appelez `RequestMessageBase.setErrorData()` en cas d’échec. Mettez toujours fin à l’implémentation en appelant la `close()` méthode (il est recommandé d’ `close()` appeler dans le `finally` bloc d’une `try` instruction). Consultez la documentation de référence sur les `MessageHandlerBase` API pour un exemple d’appel du gestionnaire.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Le code d’état HTTP 200 (OK) doit être envoyé en réponse à toutes les requêtes traitées par le gestionnaire. Si le gestionnaire n&#39;a pas pu être créé en raison d&#39;une erreur du serveur, le serveur peut répondre avec un autre code d&#39;état, tel que 500 (Erreur interne du serveur).

Le client utilise l’URL du serveur de licences spécifiée au moment du pack comme URL de base pour toutes les requêtes envoyées au serveur de licences. Par exemple, si l’URL du serveur est spécifiée comme &lt;[!DNL ht<span></span>tps://licenseserver.com/path]>, le client envoie alors des requêtes à &lt;[!DNL ht<span></span>tps://licenseserver.com/path/flashaccess/...]> Voir les sections suivantes pour plus d’informations sur le chemin d’accès spécifique utilisé pour chaque type de requête. Lors de la mise en oeuvre de votre serveur de licences, veillez à ce qu’il réponde aux chemins d’accès requis pour chaque type de requête.

Une demande de licence peut contenir un jeton d’authentification. Si l’authentification par nom d’utilisateur/mot de passe a été utilisée, la demande peut contenir une `AuthenticationToken` générée par le `AuthenticationHandler`SDK et le jeton s’assurera qu’il est valide avant d’émettre une licence.

## Utiliser des identifiants de machine {#use-machine-identifiers}

Toutes les requêtes DRM Adobe Primetime (à l’exception des requêtes prenant en charge la compatibilité FMRMS) incluent des informations sur le jeton d’ordinateur qui ont été émises au client lors de l’individualisation. Le jeton machine comprend un ID machine, qui est un identifiant attribué lors de l’individualisation. Vous pouvez utiliser cet identifiant pour comptabiliser le nombre de machines à partir desquelles un utilisateur a demandé une licence ou a rejoint un domaine.

Vous pouvez utiliser un identifiant comme suit :

* La `getUniqueId()` méthode renvoie une chaîne qui a été affectée à un périphérique lors de l’individualisation. Vous pouvez stocker les chaînes dans une base de données et les rechercher par identifiant. Cependant, cet identifiant change si l&#39;utilisateur reformate le disque dur et se individualise à nouveau. Cet identifiant a également une valeur différente entre Adobe AIR et Adobe Flash Player dans différents navigateurs sur le même ordinateur.
* Si vous souhaitez comptabiliser plus précisément les machines, vous pouvez utiliser `getBytes()` pour stocker l’identifiant entier. Pour déterminer si l&#39;ordinateur a déjà été vu, obtenez tous les identifiants d&#39;un nom d&#39;utilisateur et appelez `matches()` pour vérifier si une correspondance est trouvée. Étant donné que la `matches()` méthode doit être utilisée pour comparer les valeurs renvoyées par `MachineId.getBytes`, cette option n&#39;est pratique que lorsqu&#39;il y a un petit nombre de valeurs à comparer ; par exemple, les machines associées à un utilisateur particulier.

## Authentification des utilisateurs {#user-authentication}

Une demande DRM Adobe Primetime peut contenir un jeton d’authentification.

Si l’authentification par nom d’utilisateur/mot de passe a été utilisée, la requête peut inclure une requête `AuthenticationToken` générée par le `AuthenticationHandler`. Si vous souhaitez accéder au jeton et le vérifier, vous devez l’utiliser `RequestMessageBase.getAuthenticationToken()`. Pour lancer une demande de nom d&#39;utilisateur/mot de passe sur le client, utilisez l&#39;API `DRMManager.authenticate()` ActionScript ou iOS.

Si le client et le serveur utilisent un mécanisme d&#39;authentification personnalisé, le client obtient un jeton d&#39;authentification par le biais d&#39;un autre canal et définit le jeton d&#39;authentification personnalisé à l&#39;aide de l&#39;API `DRMManager.setAuthenticationToken` ActionScript 3.0. Utilisez `RequestMessageBase.getRawAuthenticationToken()` pour obtenir le jeton d’authentification personnalisé. L’implémentation du serveur détermine si le jeton d’authentification personnalisé est valide.

## Protection de relecture {#replay-protection}

Pour la protection de la relecture, vous pouvez vérifier si l’identifiant du message a été vu récemment en appelant `RequestMessageBase.getMessageId()`. Si tel est le cas, un attaquant peut essayer de rejouer la requête, ce qui devrait être refusé. Pour détecter les tentatives de relecture, le serveur peut stocker une liste d’identifiants de message récemment vus et vérifier chaque requête entrante par rapport à la liste mise en cache. Pour limiter la durée de stockage des identifiants de message, appelez `HandlerConfiguration.setTimestampTolerance()`. Si cette propriété est définie, le SDK refuse toute requête qui comporte un horodatage pendant plus de la durée spécifiée en secondes.

## Détection de restauration {#rollback-detection}

Pour la détection de restauration, certaines règles d’utilisation exigent que le client conserve les informations d’état pour l’application des droits. Par exemple, pour appliquer la règle d’utilisation de la fenêtre de lecture, le client stocke la date et l’heure auxquelles l’utilisateur a commencé à consulter le contenu pour la première fois. Ce événement déclenche le début de la fenêtre de lecture. Pour appliquer de manière sécurisée la fenêtre de lecture, le serveur doit s’assurer que l’utilisateur ne sauvegarde pas et ne restaure pas l’état du client afin de supprimer le début de la fenêtre de lecture stocké sur le client. Pour ce faire, le serveur effectue le suivi de la valeur du compteur d’annulation du client.

Pour chaque requête, le serveur obtient la valeur du compteur en appelant `RequestMessageBase.getClientState()` pour obtenir l’ `ClientState` objet, puis en appelant `ClientState.getCounter()` pour obtenir la valeur actuelle du compteur d’état client. Le serveur doit stocker cette valeur pour chaque client (à utiliser `MachineId.getUniqueId()` pour identifier le client associé à la valeur du compteur d&#39;annulation), puis appeler `ClientState.incrementCounter()` pour augmenter la valeur du compteur d&#39;une unité. Si le serveur détecte que la valeur du compteur est inférieure à la dernière valeur vue par le serveur, l’état du client a peut-être été rétabli.

Pour plus d’informations sur la détection des falsificateurs d’état client, consultez la documentation de référence `ClientState` API.

## Données de configuration du serveur global{#global-server-configuration-data}

Outre la configuration utilisée par le serveur de licences, `HandlerConfiguration` stocke les informations de configuration qui peuvent être envoyées au client pour contrôler la manière dont les licences sont appliquées. Pour ce faire, vous créez une `ServerConfigData` classe et vous appelez `HandlerConfiguration.setServerConfigData()`. Ces paramètres s’appliquent uniquement aux licences délivrées par ce serveur de licences.

La tolérance au retour à l’arrière-plan de l’horloge est une propriété qui peut être définie par le serveur de licences pour contrôler comment le client applique les licences. Par défaut, les utilisateurs peuvent redéfinir l’horloge de leur ordinateur sur 4 heures sans invalider les licences. Si un opérateur de serveur de licences souhaite utiliser un paramètre différent, la nouvelle valeur peut être définie dans la `ServerConfigData` classe. Lorsque vous modifiez la valeur de l&#39;un de ces paramètres, veillez à incrémenter le numéro de version en appelant `setVersion()`. Les nouvelles valeurs ne sont envoyées au client que si la version du client est antérieure à la `ServerConfigData` version actuelle.

## Fichier de stratégie DRM interdomaines {#crossdomain-drm-policy-file}

Si le serveur de licences est hébergé sur un domaine différent de celui du fichier SWF de lecture vidéo, un fichier de stratégie DRM interdomaines ( [!DNL crossdomain.xml]) est nécessaire pour permettre au fichier SWF de demander des licences à un serveur de licences. Un fichier de stratégie DRM interdomaines est représenté par un fichier XML qui permet au serveur d’indiquer que ses données et documents sont disponibles pour les fichiers SWF fournis à partir d’autres domaines. Tout fichier SWF diffusé à partir d’un domaine spécifié dans le fichier de stratégie DRM interdomaines du serveur de licences est autorisé à accéder aux données ou aux ressources provenant de ce serveur de licences.

Adobe recommande aux développeurs de suivre les meilleures pratiques lors du déploiement du fichier de stratégie interdomaines en autorisant uniquement les domaines approuvés à accéder au serveur de licences et en limitant l’accès au sous-répertoire de licences sur le serveur Web.

Pour plus d’informations sur les fichiers de stratégie DRM interdomaines, voir les emplacements suivants :

* Contrôles de site Web (fichiers de stratégie DRM)
* Spécification de fichier de stratégie DRM interdomaines : [https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html](https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html)