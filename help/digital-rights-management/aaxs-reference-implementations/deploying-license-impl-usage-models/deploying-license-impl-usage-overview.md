---
seo-title: Présentation de la mise en oeuvre des modèles d’utilisation
title: Présentation de la mise en oeuvre des modèles d’utilisation
uuid: 1041bb84-9996-4284-b2a0-d6fc6d4b73d9
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Présentation de la mise en oeuvre des modèles d’utilisation {#implementing-the-usage-models-overview}

L’implémentation de référence comprend une logique métier qui permet de démontrer comment activer les quatre modèles d’utilisation suivants pour un élément de contenu assemblé :

* Téléchargement vers la propriété (DTO)
* Location/Vidéo sur demande (VOD)
*   (à volonté)
* Publicitaire

Pour activer la démonstration du modèle d’utilisation, spécifiez la propriété personnalisée `RI_UsageModelDemo=true` au moment de l’assemblage. Si vous assemblez du contenu à l’aide de l’outil de ligne de commande Media Packager, spécifiez :

```
    java -jar AdobeMediaPackager.jar source.flv dest.flv -k RI_UsageModelDemo=true
```

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Si vous n’activez pas le mode de démonstration facultatif au moment de l’assemblage, le serveur de licences utilise la stratégie spécifiée au moment de l’assemblage pour émettre une licence. Si plusieurs stratégies ont été spécifiées, le serveur de licences utilise la première stratégie valide.

Dans la démonstration, la logique métier du serveur contrôle les attributs réels des licences générées. Au moment de l’assemblage, seules quelques informations de stratégie minimales doivent être incluses dans le contenu. Plus précisément, la stratégie doit uniquement indiquer si l’authentification est requise pour accéder au contenu. Pour activer les quatre modèles d’utilisation, incluez une stratégie qui autorise l’accès anonyme (pour le modèle financé par les publicités) et une stratégie qui requiert l’authentification du nom d’utilisateur/mot de passe (pour les trois autres modèles d’utilisation). Lors de la demande d’une licence, une application cliente peut déterminer si l’utilisateur doit demander une authentification en fonction des informations d’authentification contenues dans les stratégies.

Pour contrôler le modèle d’utilisation sous lequel un utilisateur particulier doit obtenir une licence, des entrées peuvent être ajoutées à la base de données de mise en oeuvre des références. Le `Customer` tableau contient les noms d’utilisateur et les mots de passe d’authentification des utilisateurs. Il indique également si l’utilisateur dispose d’un  . Les utilisateurs disposant de    se verront octroyer des licences selon le modèle d’utilisation du ** . Pour autoriser un utilisateur à accéder aux modèles d’utilisation *Télécharger vers soi* ou *Vidéo à la demande* , une entrée peut être ajoutée au `CustomerAuthorization` tableau, qui spécifie chaque élément de contenu auquel l’utilisateur est autorisé à accéder et le modèle d’utilisation. Consultez le [!DNL PopulateSampleDB.sql] script pour plus d’informations sur le remplissage de chaque tableau.

Lorsqu’un utilisateur demande une licence, le serveur d’implémentation des références vérifie les métadonnées envoyées par le client afin de déterminer si le contenu a été compressé à l’aide de la `RI_UsageModelDemo` propriété. Si tel est le cas, les règles de fonctionnement suivantes sont utilisées :

* Si l’une des stratégies nécessite une authentification :

   * Si la requête contient un jeton d’authentification valide, recherchez l’utilisateur dans la table de base de données du client. Si l’utilisateur a été trouvé :

      * Si la `Customer.IsSubscriber` propriété est `true`, générez une licence pour le modèle d’utilisation de la *de l’* et envoyez-la à l’utilisateur.

      * Recherchez un enregistrement dans la table de la `CustomerAuthorization` base de données pour cet utilisateur et cet ID de contenu. Si un enregistrement a été trouvé :

         * Si `CustomerAuthorization.UsageType` est `DTO`, générez une licence pour le modèle d’utilisation *Télécharger vers soi* et envoyez-la à l’utilisateur.

         * Le cas `CustomerAuthorization.UsageType` échéant, `VOD`générez une licence pour le modèle d’utilisation de la *vidéo à la demande* et envoyez-la à l’utilisateur.
   * Si aucune des stratégies n’autorise l’accès anonyme :

      * S’il n’existe pas de jeton d’authentification valide dans la requête, renvoyez une erreur &quot;authentification requise&quot;.
      * Sinon, renvoyez une erreur &quot;non autorisé&quot;.


* Si l’une des stratégies autorise un accès anonyme, générez une licence pour le modèle d’utilisation financé par les publicités et envoyez-la à l’utilisateur.

Avant que le serveur d’implémentation des références puisse émettre des licences pour la démonstration du modèle d’utilisation, le serveur doit être configuré pour spécifier le mode de génération des licences pour chacun des quatre modèles d’utilisation. Pour ce faire, vous spécifiez une stratégie pour chaque modèle d’utilisation. L’implémentation de référence comprend quatre exemples de stratégies ( [!DNL dto-policy.pol], [!DNL vod-policy.pol], [!DNL sub-policy.pol], [!DNL ad-policy.pol]) ou vous pouvez remplacer vos propres stratégies. Dans [!DNL flashaccess-refimpl.properties], définissez les propriétés suivantes pour spécifier la stratégie à utiliser pour chaque modèle d’utilisation et placez les fichiers de stratégie dans le répertoire spécifié par la `config.resourcesDirectory` propriété :

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

