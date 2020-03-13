---
seo-title: Présentation de la mise à jour des fichiers de configuration
title: Présentation de la mise à jour des fichiers de configuration
uuid: e9be21cf-ad23-4ed6-8bef-f194bc1fd749
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Présentation de la mise à jour des fichiers de configuration {#updating-configuration-files-overview}

Une fois que le serveur de licences lit l’un des fichiers de configuration du serveur de licences (configuration globale ou de client), les informations de configuration sont mises en cache en mémoire. Par conséquent, les fichiers n’ont pas besoin d’être lus sur le disque pour chaque demande de licence. Cependant, le serveur permet également de modifier la plupart des valeurs des fichiers de configuration sans avoir à redémarrer le serveur pour que les modifications prennent effet. (Voir ci-dessous pour plus d’informations sur les valeurs de configuration recherchées pour les mises à jour.)

Pour recharger la configuration lorsque des modifications sont effectuées, le serveur de licences stocke le moment de la dernière modification du fichier. À un intervalle configurable, le serveur vérifie si l’heure de modification du fichier a changé et, le cas échéant, recharge le contenu du fichier.

Pour contrôler la fréquence à laquelle le serveur recherche les mises à jour, définissez l’ `refreshDelaySeconds` attribut dans l’élément Mise en cache du fichier de configuration globale. Si, par exemple, `refreshDelaySeconds` est défini sur 3 600 secondes, il faut au plus une heure à partir du moment où le fichier est mis à jour pour que les mises à jour de configuration soient détectées par le serveur. Si `refreshDelaySeconds` est défini sur 0, le serveur recherche les mises à jour de configuration pour chaque requête. Il n’est pas recommandé `refreshDelaySeconds` de définir une valeur faible pour les  de production  car cela pourrait avoir un impact sur les performances.

L’élément Mise en cache contrôle également le nombre de configurations de locataires mises en cache à la fois. Vous pouvez définir cette valeur sur un nombre inférieur au nombre total de locataires afin de limiter la quantité de mémoire utilisée pour mettre en cache les informations de configuration. Si une requête est reçue pour un client ne se trouvant pas dans le cache, la configuration est chargée avant que la requête ne puisse être traitée. Si le cache est plein, le client le moins récemment utilisé est supprimé du cache.

Si une modification est enregistrée dans un fichier de configuration ou dans l’un des fichiers de certificat référencés pendant [!DNL flashaccess-tenant.xml] que le serveur tente de lire le fichier, ou si l’horodatage du fichier est inférieur à une seconde avant l’heure actuelle ou est dans le futur, la version mise en cache de la configuration est utilisée jusqu’à la prochaine vérification par le serveur des mises à jour. S’il n’existe aucune version mise en cache, le chargement de la configuration échoue et une erreur est renvoyée au client. Le serveur tente de charger à nouveau le fichier la prochaine fois qu’il reçoit une demande pour ce client.
