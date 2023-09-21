---
title: Traitement des demandes Adobe Primetime DRM
description: Traitement des demandes Adobe Primetime DRM
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1251'
ht-degree: 0%

---

# Traitement des demandes Adobe Primetime DRM {#process-adobe-primetime-drm-requests}

La méthode générale de gestion des requêtes consiste à créer un gestionnaire, à analyser la requête, à définir les données de réponse ou le code d’erreur et à fermer le gestionnaire.

La classe de base utilisée pour gérer l’interaction requête/réponse unique est `com.adobe.flashaccess.sdk.protocol.MessageHandlerBase`. Une instance de la fonction `HandlerConfiguration` est utilisée pour initialiser le gestionnaire. `HandlerConfiguration` stocke les informations de configuration du serveur, notamment les informations d’identification du transport, la tolérance à l’horodatage, les listes de mise à jour de stratégie et les listes de révocation. Le gestionnaire lit les données de requête et analyse la requête dans une instance de `RequestMessageBase`. L’appelant peut examiner les informations de la requête et décider s’il doit renvoyer une erreur ou une réponse réussie (sous-classes de `RequestMessageBase` fournir une méthode pour définir les données de réponse).

Si la requête aboutit, définissez les données de réponse ; sinon appelez `RequestMessageBase.setErrorData()` en cas d’échec. Mettez toujours fin à l’implémentation en appelant la variable `close()` (il est recommandé d’utiliser la méthode `close()` être appelée dans la variable `finally` bloc d’un `try` ). Voir `MessageHandlerBase` Documentation de référence sur l’API pour obtenir un exemple d’appel du gestionnaire.

>[!NOTE]
>
>Le code d’état HTTP 200 (OK) doit être envoyé en réponse à toutes les requêtes traitées par le gestionnaire. Si le gestionnaire n’a pas pu être créé en raison d’une erreur du serveur, le serveur peut répondre avec un autre code d’état, tel que 500 (Erreur interne du serveur).

Le client utilise l’URL du serveur de licences spécifiée au moment du regroupement comme URL de base pour toutes les demandes envoyées au serveur de licences. Par exemple, si l’URL du serveur est spécifiée sous la forme &lt;[!DNL ht<span></span>tps://licenseserver.com/path]>, le client envoie ensuite des requêtes à &lt;[!DNL ht<span></span>tps://licenseserver.com/path/flashaccess/...]> Consultez les sections suivantes pour plus d’informations sur le chemin spécifique utilisé pour chaque type de requête. Lors de la mise en oeuvre de votre serveur de licences, assurez-vous que le serveur répond aux chemins requis pour chaque type de demande.

Une demande de licence peut contenir un jeton d’authentification. Si l’authentification par nom d’utilisateur/mot de passe a été utilisée, la requête peut contenir une `AuthenticationToken` généré par la variable `AuthenticationHandler`, et le SDK s’assure que le jeton est valide avant d’émettre une licence.

## Utilisation des identifiants de machine {#use-machine-identifiers}

Toutes les demandes Adobe Primetime DRM (à l’exception des demandes qui prennent en charge la compatibilité FMRMS) incluent des informations sur le jeton de la machine qui a été émis au client lors de l’individualisation. Le jeton de machine comprend un ID de machine, qui est un identifiant attribué lors de l’individualisation. Vous pouvez utiliser cet identifiant pour compter le nombre de machines à partir desquelles un utilisateur a demandé une licence ou a rejoint un domaine.

Vous pouvez utiliser un identifiant comme suit :

* La variable `getUniqueId()` renvoie une chaîne qui a été affectée à un appareil lors de l’individualisation. Vous pouvez stocker les chaînes dans une base de données et les rechercher par identifiant. Cependant, cet identifiant change si l’utilisateur reformate le disque dur et s’individualise à nouveau. Cet identifiant a également une valeur différente entre Adobe AIR et Adobe Flash Player dans différents navigateurs sur le même ordinateur.
* Si vous souhaitez comptabiliser plus précisément les machines, vous pouvez utiliser `getBytes()` pour stocker l’identifiant entier. Pour déterminer si la machine a déjà été vue, récupérez tous les identifiants pour un nom d’utilisateur et appelez `matches()` pour vérifier si une correspondance est trouvée. Parce que la variable `matches()` doit être utilisée pour comparer les valeurs renvoyées par `MachineId.getBytes`, cette option n’est pratique que s’il existe un petit nombre de valeurs à comparer ; par exemple, les machines associées à un utilisateur particulier.

## Authentification de l’utilisateur {#user-authentication}

Une requête DRM Adobe Primetime peut contenir un jeton d’authentification.

Si l’authentification par nom d’utilisateur/mot de passe a été utilisée, la demande peut inclure une `AuthenticationToken` généré par la variable `AuthenticationHandler`. Si vous souhaitez accéder au jeton et le vérifier, vous devez utiliser `RequestMessageBase.getAuthenticationToken()`. Pour lancer une demande de nom d’utilisateur/mot de passe sur le client, utilisez la variable `DRMManager.authenticate()` API ActionScript ou iOS.

Si le client et le serveur utilisent un mécanisme d’authentification personnalisé, le client obtient un jeton d’authentification par le biais d’un autre canal et définit le jeton d’authentification personnalisé à l’aide de la variable `DRMManager.setAuthenticationToken` API ActionScript 3.0. Utilisation `RequestMessageBase.getRawAuthenticationToken()` pour obtenir le jeton d’authentification personnalisé. L’implémentation du serveur détermine si le jeton d’authentification personnalisé est valide.

## Protection des relecture {#replay-protection}

Pour la protection de relecture, vous pouvez vérifier si l’identifiant du message a été vu récemment en appelant `RequestMessageBase.getMessageId()`. Si tel est le cas, un attaquant peut essayer de relayer la requête, ce qui doit être refusé. Pour détecter les tentatives de relecture, le serveur peut stocker une liste d’identifiants de message récemment consultés et comparer chaque requête entrante à la liste mise en cache. Pour limiter la durée de stockage des identifiants de message, appelez `HandlerConfiguration.setTimestampTolerance()`. Si cette propriété est définie, le SDK refuse toute demande qui comporte un horodatage pendant plus de secondes de l’heure du serveur.

## Détection de restauration {#rollback-detection}

Pour la détection de restauration, certaines règles d’utilisation exigent que le client conserve les informations d’état pour l’application des droits. Par exemple, pour appliquer la règle d’utilisation de la fenêtre de lecture, le client stocke la date et l’heure auxquelles l’utilisateur a commencé à afficher le contenu. Cet événement déclenche le début de la fenêtre de lecture. Pour appliquer de manière sécurisée la fenêtre de lecture, le serveur doit s’assurer que l’utilisateur ne sauvegarde pas et ne restaure pas l’état du client afin de supprimer l’heure de début de la fenêtre de lecture stockée sur le client. Pour ce faire, le serveur effectue le suivi de la valeur du compteur de restauration du client.

Pour chaque requête, le serveur obtient la valeur du compteur en appelant `RequestMessageBase.getClientState()` pour obtenir la variable `ClientState` , puis en appelant `ClientState.getCounter()` pour obtenir la valeur actuelle du compteur d’états client. Le serveur doit stocker cette valeur pour chaque client (utilisez `MachineId.getUniqueId()` pour identifier le client associé à la valeur de compteur de restauration, puis appelez `ClientState.incrementCounter()` pour augmenter la valeur du compteur d’une unité. Si le serveur détecte que la valeur du compteur est inférieure à la dernière valeur affichée par le serveur, l’état du client peut avoir été restauré.

Voir `ClientState` Documentation de référence sur l’API pour plus d’informations sur la détection de l’horodatage de l’état client.

## Données de configuration du serveur global{#global-server-configuration-data}

En plus de la configuration utilisée par le serveur de licences, `HandlerConfiguration` stocke des informations de configuration qui peuvent être envoyées au client pour contrôler la manière dont les licences sont appliquées. Pour ce faire, créez une `ServerConfigData` classe et appel `HandlerConfiguration.setServerConfigData()`. Ces paramètres s’appliquent uniquement aux licences délivrées par ce serveur de licences.

La tolérance au vent arrière est une propriété qui peut être définie par le serveur de licences pour contrôler la manière dont le client applique les licences. Par défaut, les utilisateurs peuvent redéfinir l’horloge de leur ordinateur sur 4 heures sans invalider les licences. Si un opérateur de serveur de licences souhaite utiliser un autre paramètre, la nouvelle valeur peut être définie dans la variable `ServerConfigData` classe . Lorsque vous modifiez la valeur de l’un de ces paramètres, veillez à incrémenter le numéro de version en appelant `setVersion()`. Les nouvelles valeurs ne sont envoyées au client que si la version du client est antérieure à la version actuelle. `ServerConfigData` version.

## Fichier de stratégie DRM interdomaine {#crossdomain-drm-policy-file}

Si le serveur de licences est hébergé sur un domaine différent du SWF de lecture vidéo, un fichier de stratégie DRM interdomaines ( [!DNL crossdomain.xml]) est nécessaire pour permettre au SWF de demander des licences à un serveur de licences. Un fichier de stratégie DRM interdomaines est représenté par un fichier XML qui permet au serveur d’indiquer que ses données et documents sont disponibles pour les fichiers SWF diffusés à partir d’autres domaines. Tout fichier de SWF provenant d’un domaine spécifié dans le fichier de stratégie DRM interdomaines du serveur de licences est autorisé à accéder aux données ou aux ressources provenant de ce serveur de licences.

Adobe recommande aux développeurs de suivre les bonnes pratiques lors du déploiement du fichier de stratégie inter-domaines en autorisant uniquement les domaines approuvés à accéder au serveur de licences et en limitant l’accès au sous-répertoire de licence sur le serveur web.

Pour plus d’informations sur les fichiers de stratégie DRM interdomaines, voir les emplacements suivants :

* Contrôles de site web (fichiers de stratégie DRM)
* Spécification de fichier de stratégie DRM interdomaines : [https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html](https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html)
