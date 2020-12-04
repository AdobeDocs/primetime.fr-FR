---
seo-title: Présentation de la mise en oeuvre des modèles d’utilisation
title: Présentation de la mise en oeuvre des modèles d’utilisation
uuid: 1041bb84-9996-4284-b2a0-d6fc6d4b73d9
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---


# Mise en oeuvre de l&#39;aperçu des modèles d&#39;utilisation {#implementing-the-usage-models-overview}

L’implémentation des références comprend une logique métier permettant de démontrer comment activer les quatre modèles d’utilisation suivants pour un élément de contenu assemblé :

* Téléchargement à soi-même (DTO)
* Location/Vidéo sur demande (VOD)
* Abonnement (à volonté)
* Publicités financées

Pour activer la démonstration du modèle d’utilisation, spécifiez la propriété personnalisée `RI_UsageModelDemo=true` au moment du conditionnement. Si vous assemblez du contenu à l’aide de l’outil de ligne de commande Media Packager, spécifiez :

```
    java -jar AdobeMediaPackager.jar source.flv dest.flv -k RI_UsageModelDemo=true
```

>[!NOTE]
>
>Si vous n’activez pas le mode de démonstration facultatif au moment du pack, le serveur de licences utilise la stratégie spécifiée au moment du pack pour émettre une licence. Si plusieurs stratégies ont été spécifiées, le serveur de licences utilise la première stratégie valide.

Dans la démonstration, la logique métier du serveur contrôle les attributs réels des licences générées. Au moment de l’emballage, seules quelques informations de stratégie minimales doivent être incluses dans le contenu. Plus précisément, la stratégie doit uniquement indiquer si une authentification est nécessaire pour accéder au contenu. Pour activer les quatre modèles d’utilisation, incluez une stratégie qui autorise l’accès anonyme (pour le modèle financé par les publicités) et une stratégie qui requiert l’authentification du nom d’utilisateur/mot de passe (pour les trois autres modèles d’utilisation). Lors de la demande de licence, une application cliente peut déterminer si l’utilisateur doit demander une authentification en fonction des informations d’authentification contenues dans les stratégies.

Pour contrôler le modèle d’utilisation sous lequel un utilisateur particulier doit obtenir une licence, des entrées peuvent être ajoutées à la base de données de mise en oeuvre des références. La table `Customer` contient les noms d’utilisateur et les mots de passe d’authentification des utilisateurs. Il indique également si l’utilisateur dispose d’un abonnement. Les utilisateurs dotés d&#39;abonnements recevront des licences en vertu du modèle d&#39;utilisation *Abonnement*. Pour autoriser un utilisateur à accéder aux modèles d&#39;utilisation *Télécharger vers Propre* ou *Vidéo à la demande*, une entrée peut être ajoutée à la table `CustomerAuthorization`, qui spécifie chaque élément de contenu auquel l&#39;utilisateur est autorisé à accéder et le modèle d&#39;utilisation. Consultez le script [!DNL PopulateSampleDB.sql] pour plus d&#39;informations sur le remplissage de chaque tableau.

Lorsqu’un utilisateur demande une licence, le serveur d’implémentation des références vérifie les métadonnées envoyées par le client afin de déterminer si le contenu a été compressé à l’aide de la propriété `RI_UsageModelDemo`. Si tel est le cas, les règles de fonctionnement suivantes sont utilisées :

* Si l’une des stratégies nécessite une authentification :

   * Si la requête contient un jeton d’authentification valide, recherchez l’utilisateur dans la table de la base de données du client. Si l&#39;utilisateur a été trouvé :

      * Si la propriété `Customer.IsSubscriber` est `true`, générez une licence pour le modèle d’utilisation *Abonnement* et envoyez-la à l’utilisateur.

      * Recherchez un enregistrement dans la table de base de données `CustomerAuthorization` pour cet utilisateur et cet ID de contenu. Si un enregistrement a été trouvé :

         * Si `CustomerAuthorization.UsageType` est `DTO`, générez une licence pour le modèle d’utilisation *Télécharger vers vous* et envoyez-la à l’utilisateur.

         * Si `CustomerAuthorization.UsageType` est `VOD`, générez une licence pour le modèle d&#39;utilisation *Vidéo à la demande* et envoyez-la à l&#39;utilisateur.
   * Si aucune des stratégies n’autorise l’accès anonyme :

      * S’il n’existe pas de jeton d’authentification valide dans la demande, renvoyez une erreur &quot;authentification requise&quot;.
      * Sinon, renvoyez une erreur &quot;non autorisé&quot;.


* Si l’une des stratégies autorise un accès anonyme, générez une licence pour le modèle d’utilisation financé par la publicité et envoyez-la à l’utilisateur.

Avant que le serveur d’implémentation de référence puisse émettre des licences pour la démonstration du modèle d’utilisation, le serveur doit être configuré pour spécifier comment les licences sont générées pour chacun des quatre modèles d’utilisation. Pour ce faire, vous devez spécifier une stratégie pour chaque modèle d’utilisation. La mise en oeuvre de référence comprend quatre exemples de stratégies ( [!DNL dto-policy.pol], [!DNL vod-policy.pol], [!DNL sub-policy.pol], [!DNL ad-policy.pol]) ou vous pouvez remplacer vos propres stratégies. Dans [!DNL flashaccess-refimpl.properties], définissez les propriétés suivantes pour spécifier la stratégie à utiliser pour chaque modèle d&#39;utilisation et placez les fichiers de stratégie dans le répertoire spécifié par la propriété `config.resourcesDirectory` :

```
# Policy file name for Download To Own usage  
RefImpl.UsageModelDemo.Policy.DTO=dto-policy.pol  
# Policy file name for Rental usage  
RefImpl.UsageModelDemo.Policy.VOD=vod-policy.pol  
# Policy file name for Subscription usage  
RefImpl.UsageModelDemo.Policy.Subscribe=sub-policy.pol  
# Policy file name for Ad Supported (free) usage  
RefImpl.UsageModelDemo.Policy.Free=ad-policy.pol
```

