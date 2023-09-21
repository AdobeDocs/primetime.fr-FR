---
title: Mise en oeuvre des modèles d’utilisation - Aperçu
description: Mise en oeuvre des modèles d’utilisation - Aperçu
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---

# Mise en oeuvre des modèles d’utilisation - Aperçu {#implementing-the-usage-models-overview}

La mise en oeuvre de référence comprend une logique métier qui permet de démontrer comment activer les quatre modèles d’utilisation suivants pour un élément de contenu empaqueté :

* Téléchargement vers soi (DTO)
* Location/Video-on-demand (VOD)
* Abonnement (à volonté)
* Publicité financée

Pour activer la démonstration du modèle d’utilisation, spécifiez la propriété personnalisée. `RI_UsageModelDemo=true` au moment de l’emballage. Si vous mettez en package du contenu à l’aide de l’outil de ligne de commande Media Packager, spécifiez :

```
    java -jar AdobeMediaPackager.jar source.flv dest.flv -k RI_UsageModelDemo=true
```

>[!NOTE]
>
>Si vous n’activez pas le mode de démonstration facultatif au moment du conditionnement, le serveur de licences utilise la stratégie indiquée au moment du conditionnement pour émettre une licence. Si plusieurs stratégies ont été spécifiées, le serveur de licences utilise la première stratégie valide.

Dans la démonstration, la logique commerciale sur le serveur contrôle les attributs réels des licences générées. Au moment de l’emballage, seule une information de politique minimale doit être incluse dans le contenu. Plus précisément, la stratégie doit uniquement indiquer si l’authentification est requise pour accéder au contenu. Pour activer les quatre modèles d’utilisation, incluez une stratégie permettant l’accès anonyme (pour le modèle financé par l’annonce) et une stratégie nécessitant une authentification par nom d’utilisateur/mot de passe (pour les trois autres modèles d’utilisation). Lorsque vous demandez une licence, une application cliente peut déterminer si l’utilisateur doit demander une authentification en fonction des informations d’authentification figurant dans les stratégies.

Pour contrôler le modèle d’utilisation sous lequel un utilisateur particulier doit obtenir une licence, des entrées peuvent être ajoutées à la base de données de mise en oeuvre de référence. La variable `Customer` contient les noms d’utilisateur et les mots de passe pour l’authentification des utilisateurs. Il indique également si l’utilisateur dispose d’un abonnement. Les utilisateurs avec des abonnements recevront des licences sous la *Abonnement* modèle d’utilisation. Pour accorder un accès à un utilisateur sous *Télécharger vers vous* ou *Vidéo sur demande* modèles d’utilisation, une entrée peut être ajoutée au `CustomerAuthorization` qui spécifie chaque élément de contenu auquel l’utilisateur est autorisé à accéder et le modèle d’utilisation. Voir [!DNL PopulateSampleDB.sql] pour plus d’informations sur le remplissage de chaque tableau.

Lorsqu’un utilisateur demande une licence, le serveur de mise en oeuvre de référence vérifie les métadonnées envoyées par le client pour déterminer si le contenu a été compilé à l’aide de la variable `RI_UsageModelDemo` . Si tel est le cas, les règles de fonctionnement suivantes sont utilisées :

* Si l’une des stratégies nécessite une authentification :

   * Si la requête contient un jeton d’authentification valide, recherchez l’utilisateur dans la table de la base de données client. Si l’utilisateur a été trouvé :

      * Si la variable `Customer.IsSubscriber` est `true`, générez une licence pour le *Abonnement* modèle d’utilisation et envoyez-le à l’utilisateur.

      * Recherchez un enregistrement dans la variable `CustomerAuthorization` table de base de données pour cet utilisateur et cet identifiant de contenu. Si un enregistrement a été trouvé :

         * If `CustomerAuthorization.UsageType` is `DTO`, générez une licence pour le *Télécharger à soi* modèle d’utilisation et envoyez-le à l’utilisateur.

         * If `CustomerAuthorization.UsageType` is `VOD`, générez une licence pour le *Vidéo à la demande* modèle d’utilisation et envoyez-le à l’utilisateur.

   * Si aucune des stratégies n’autorise l’accès anonyme :

      * S’il n’existe pas de jeton d’authentification valide dans la requête, renvoyez une erreur &quot;authentification requise&quot;.
      * Sinon, renvoie une erreur &quot;non autorisé&quot;.

* Si l’une des politiques autorise l’accès anonyme, générez une licence pour le modèle d’utilisation financé par l’annonce et envoyez-la à l’utilisateur.

Avant que le serveur d’implémentation de référence puisse émettre des licences pour la démonstration du modèle d’utilisation, le serveur doit être configuré pour spécifier la manière dont les licences sont générées pour chacun des quatre modèles d’utilisation. Pour ce faire, spécifiez une stratégie pour chaque modèle d’utilisation. L’implémentation de référence comprend quatre exemples de stratégies ( [!DNL dto-policy.pol], [!DNL vod-policy.pol], [!DNL sub-policy.pol], [!DNL ad-policy.pol]) ou vous pouvez substituer vos propres politiques. Dans [!DNL flashaccess-refimpl.properties], définissez les propriétés suivantes pour spécifier la stratégie à utiliser pour chaque modèle d’utilisation et placez les fichiers de stratégie dans le répertoire spécifié par le `config.resourcesDirectory` property:

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
