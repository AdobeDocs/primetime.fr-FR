---
seo-title: Traitement des demandes DRM Adobe Primetime
title: Traitement des demandes DRM Adobe Primetime
uuid: ee10504d-84f0-472a-b58a-2a87fdeedfc1
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Traitement des demandes DRM Adobe Primetime {#process-adobe-primetime-drm-requests}

La méthode générale de gestion des requêtes consiste à créer un gestionnaire, analyser la requête, définir les données de réponse ou le code d’erreur et fermer le gestionnaire.

La classe de base utilisée pour gérer l’interaction requête/réponse unique est `com.adobe.flashaccess.sdk.protocol.MessageHandlerBase`. Une instance de la `HandlerConfiguration` classe est utilisée pour initialiser le gestionnaire. `HandlerConfiguration` stocke les informations de configuration du serveur, notamment les informations d’identification du transport, la tolérance d’horodatage, les  de mise à jour de stratégie et les de révocation. Le gestionnaire lit les données de requête et analyse la requête dans une instance de `RequestMessageBase`. L’appelant peut examiner les informations contenues dans la requête et décider s’il renvoie une erreur ou une réponse positive (les sous-classes de `RequestMessageBase` fournissent une méthode de définition des données de réponse).

Si la requête aboutit, définissez les données de réponse ; invoquez sinon `RequestMessageBase.setErrorData()` en cas d’échec. Mettez toujours fin à l’implémentation en appelant la `close()` méthode (il est recommandé `close()` d’être appelé dans le `finally` bloc d’une `try` instruction). Consultez la documentation de référence `MessageHandlerBase` API pour obtenir un exemple d’appel du gestionnaire.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Le code d’état HTTP 200 (OK) doit être envoyé en réponse à toutes les requêtes traitées par le gestionnaire. Si le gestionnaire n’a pas pu être créé en raison d’une erreur du serveur, le serveur peut répondre avec un autre code d’état, tel que 500 (Erreur interne du serveur).

Le client utilise l’URL du serveur de licences spécifiée au moment du pack comme URL de base pour toutes les requêtes envoyées au serveur de licences. Par exemple, si l’URL du serveur est spécifiée sous la forme &lt;[!DNL ht<span></span>tps://licenseserver.com/path]>, le client envoie alors des requêtes à &lt;[!DNL ht<span></span>tps://licenseserver.com/path/flashaccess/...]> Voir les sections suivantes pour plus d’informations sur le chemin spécifique utilisé pour chaque type de requête. Lors de la mise en oeuvre de votre serveur de licences, veillez à ce que le serveur réponde aux chemins d’accès requis pour chaque type de requête.

Une demande de licence peut contenir un jeton d’authentification. Si l’authentification par nom d’utilisateur/mot de passe a été utilisée, la requête peut contenir une `AuthenticationToken` générée par le `AuthenticationHandler`, et le SDK s’assurera que le jeton est valide avant d’émettre une licence.

## Utiliser des identifiants de machine {#use-machine-identifiers}

Toutes les demandes DRM Adobe Primetime (à l’exception des demandes prenant en charge la compatibilité FMRMS) incluent des informations sur le jeton d’ordinateur qui a été émis au client lors de l’individualisation. Le jeton de l’ordinateur comprend un ID d’ordinateur, identifiant qui a été attribué lors de l’individualisation. Vous pouvez utiliser cet identifiant pour compter le nombre de machines à partir desquelles un utilisateur a demandé une licence ou a rejoint un domaine.

Vous pouvez utiliser un identifiant comme suit :

* La `getUniqueId()` méthode renvoie une chaîne qui a été affectée à un périphérique lors de l’individualisation. Vous pouvez stocker les chaînes dans une base de données et effectuer une recherche par identifiant. Toutefois, cet identifiant change si l’utilisateur reformate le disque dur et le personnalise à nouveau. Cet identifiant a également une valeur différente entre Adobe AIR et Adobe Flash Player dans différents navigateurs sur le même ordinateur.
* Si vous souhaitez comptabiliser plus précisément les machines, vous pouvez utiliser `getBytes()` pour stocker l’identifiant complet. Pour déterminer si l’ordinateur a déjà été vu, obtenez tous les identifiants d’un nom d’utilisateur et appelez `matches()` pour vérifier si une correspondance est possible. La `matches()` méthode devant être utilisée pour comparer les valeurs renvoyées par `MachineId.getBytes`, cette option n&#39;est pratique que lorsqu&#39;il existe un petit nombre de valeurs à comparer ; par exemple, les machines associées à un utilisateur particulier.

## Authentification des utilisateurs {#user-authentication}

Une requête DRM Adobe Primetime peut contenir un jeton d’authentification.

Si l’authentification par nom d’utilisateur/mot de passe a été utilisée, la requête peut inclure une `AuthenticationToken` générée par le `AuthenticationHandler`. Si vous souhaitez accéder au jeton et le vérifier, vous devez l’utiliser `RequestMessageBase.getAuthenticationToken()`. Pour lancer une demande de nom d’utilisateur/mot de passe sur le client, utilisez l’API `DRMManager.authenticate()` ActionScript ou iOS.

Si le client et le serveur utilisent un mécanisme d’authentification personnalisé, le client obtient un jeton d’authentification par l’intermédiaire d’un autre et définit le jeton d’authentification personnalisé à l’aide de l’API `DRMManager.setAuthenticationToken` ActionScript 3.0. Utilisez `RequestMessageBase.getRawAuthenticationToken()` pour obtenir le jeton d’authentification personnalisé. L’implémentation du serveur détermine si le jeton d’authentification personnalisé est valide.

## Protection de relecture {#replay-protection}

Pour la protection de la relecture, vous pouvez vérifier si l’identifiant du message a été vu récemment en appelant `RequestMessageBase.getMessageId()`. Si tel est le cas, un attaquant peut essayer de relayer la requête, ce qui doit être refusé. Pour détecter les tentatives de relecture, le serveur peut stocker un  d’identifiants de message récemment affichés et vérifier chaque requête entrante par rapport au mis en cache . Pour limiter la durée de stockage des identifiants de message, appelez `HandlerConfiguration.setTimestampTolerance()`. Si cette propriété est définie, le SDK refuse toute requête qui comporte un horodatage pendant plus de la durée spécifiée en secondes.

## Détection de restauration {#rollback-detection}

Pour la détection de restauration, certaines règles d’utilisation exigent que le client conserve les informations d’état pour l’application des droits. Par exemple, pour appliquer la règle d’utilisation de la fenêtre de lecture, le client stocke la date et l’heure auxquelles l’utilisateur a commencé à consulter le contenu pour la première fois. Ce  déclenche le de la fenêtre de lecture. Pour appliquer la fenêtre de lecture de manière sécurisée, le serveur doit s’assurer que l’utilisateur ne sauvegarde pas et ne restaure pas l’état du client afin de supprimer le de la fenêtre de lecture  le temps stocké sur le client. Pour ce faire, le serveur effectue le suivi de la valeur du compteur de restauration du client.

Pour chaque requête, le serveur obtient la valeur du compteur en appelant `RequestMessageBase.getClientState()` pour obtenir l’ `ClientState` objet, puis `ClientState.getCounter()` pour obtenir la valeur actuelle du compteur d’état client. Le serveur doit stocker cette valeur pour chaque client (à utiliser `MachineId.getUniqueId()` pour identifier le client associé à la valeur du compteur de restauration), puis appeler `ClientState.incrementCounter()` pour augmenter la valeur du compteur de 1. Si le serveur détecte que la valeur du compteur est inférieure à la dernière valeur vue par le serveur, l’état du client a peut-être été rétabli.

Voir la documentation de référence `ClientState` API pour plus d’informations sur la détection des falsificateurs d’état client.

## Données de configuration du serveur global{#global-server-configuration-data}

Outre la configuration utilisée par le serveur de licences, `HandlerConfiguration` stocke les informations de configuration qui peuvent être envoyées au client pour contrôler la manière dont les licences sont appliquées. Cela se fait en créant une `ServerConfigData` classe et en appelant `HandlerConfiguration.setServerConfigData()`. Ces paramètres s’appliquent uniquement aux licences délivrées par ce serveur de licences.

La tolérance au vent de l’horloge est une propriété qui peut être définie par le serveur de licences pour contrôler la manière dont le client applique les licences. Par défaut, les utilisateurs peuvent redéfinir l’horloge de leur ordinateur sur 4 heures sans invalider les licences. Si un opérateur de serveur de licences souhaite utiliser un paramètre différent, la nouvelle valeur peut être définie dans la `ServerConfigData` classe. Lorsque vous modifiez la valeur de l’un de ces paramètres, veillez à incrémenter le numéro de version en appelant `setVersion()`. Les nouvelles valeurs ne sont envoyées au client que si la version du client est antérieure à la `ServerConfigData` version actuelle.

## Fichier de stratégie DRM interdomaines {#crossdomain-drm-policy-file}

Si le serveur de licences est hébergé sur un domaine différent de celui du fichier SWF de lecture vidéo, un fichier de stratégie DRM interdomaines ( [!DNL crossdomain.xml]) est nécessaire pour permettre au fichier SWF de demander des licences à un serveur de licences. Un fichier de stratégie DRM interdomaines est représenté par un fichier XML qui permet au serveur d’indiquer que ses données et ses  sont disponibles pour les fichiers SWF fournis à partir d’autres domaines. Tout fichier SWF diffusé à partir d’un domaine spécifié dans le fichier de stratégie DRM interdomaines du serveur de licences est autorisé à accéder aux données ou aux ressources provenant de ce serveur de licences.

Adobe recommande aux développeurs de suivre les bonnes pratiques lors du déploiement du fichier de stratégie interdomaines en autorisant uniquement les domaines de confiance à accéder au serveur de licences et en limitant l’accès au sous-répertoire de licences sur le serveur Web.

Pour plus d’informations sur les fichiers de stratégie DRM interdomaines, voir les emplacements suivants :

* Contrôles de site Web (fichiers de stratégie DRM)
* Spécification de fichier de stratégie DRM interdomaines : [https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html](https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html)