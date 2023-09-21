---
title: Mise à jour des fichiers de configuration - Aperçu
description: Mise à jour des fichiers de configuration - Aperçu
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# Mise à jour des fichiers de configuration - Aperçu {#updating-configuration-files-overview}

Une fois que le serveur de licences a lu l’un des fichiers de configuration du serveur de licences (configuration globale ou client), les informations de configuration sont mises en cache en mémoire. Par conséquent, les fichiers n’ont pas à être lus à partir du disque pour chaque demande de licence. Cependant, le serveur permet également de modifier la plupart des valeurs des fichiers de configuration sans qu’il faille redémarrer le serveur pour que les modifications soient prises en compte. (Voir ci-dessous pour plus d’informations sur les valeurs de configuration vérifiées pour les mises à jour.)

Pour recharger la configuration lorsque des modifications sont effectuées, le serveur de licences stocke l’heure de la dernière modification du fichier. À un intervalle configurable, le serveur vérifie si l’heure de modification du fichier a changé et, dans l’affirmative, recharge le contenu du fichier.

Pour contrôler la fréquence à laquelle le serveur recherche des mises à jour, définissez la variable `refreshDelaySeconds` dans l’élément Mise en cache du fichier de configuration global. Par exemple, si `refreshDelaySeconds` est définie sur 3 600 secondes, il faut au plus une heure à compter de la mise à jour du fichier pour que les mises à jour de configuration soient détectées par le serveur. If `refreshDelaySeconds` est définie sur 0, le serveur recherche les mises à jour de configuration pour chaque requête. Paramètre `refreshDelaySeconds` La valeur faible n’est pas recommandée pour les environnements de production, car elle peut avoir une incidence sur les performances.

L’élément Mise en cache contrôle également le nombre de configurations de clients mises en cache simultanément. Vous pouvez définir cette valeur sur un nombre inférieur au nombre total de clients afin de limiter la quantité de mémoire utilisée pour mettre en cache les informations de configuration. Si une demande est reçue pour un client ne se trouvant pas dans le cache, la configuration est chargée avant que la demande ne puisse être traitée. Si le cache est plein, le client le moins récemment utilisé est supprimé du cache.

Si une modification est enregistrée dans un fichier de configuration ou dans l’un des fichiers de certificat référencés dans [!DNL flashaccess-tenant.xml] pendant que le serveur tente de lire le fichier, ou si l’horodatage du fichier se trouve être inférieur à une seconde avant l’heure actuelle ou se situe à l’avenir, la version mise en cache de la configuration est utilisée jusqu’à la prochaine vérification des mises à jour par le serveur. En l’absence de version mise en cache, le chargement de la configuration échoue et une erreur est renvoyée au client. Le serveur tente de charger à nouveau le fichier la prochaine fois qu’il reçoit une demande pour ce client.
