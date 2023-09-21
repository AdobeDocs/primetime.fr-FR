---
description: Dès que le serveur de licences lit l’un des fichiers de configuration du serveur de licences (configuration globale ou client), les informations de configuration sont mises en cache en mémoire. Par conséquent, les fichiers n’ont pas à être lus sur le disque pour chaque demande de licence. Cependant, le serveur permet également de modifier la plupart des valeurs des fichiers de configuration sans qu’il faille redémarrer le serveur pour que les modifications soient prises en compte.
title: Mise à jour des fichiers de configuration
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 0%

---


# Mise à jour des fichiers de configuration{#updating-configuration-files}

Dès que le serveur de licences lit l’un des fichiers de configuration du serveur de licences (configuration globale ou client), les informations de configuration sont mises en cache en mémoire. Par conséquent, les fichiers n’ont pas à être lus sur le disque pour chaque demande de licence. Cependant, le serveur permet également de modifier la plupart des valeurs des fichiers de configuration sans qu’il faille redémarrer le serveur pour que les modifications soient prises en compte.

Chaque fois que vous modifiez le fichier de configuration, le serveur de licences stocke l’heure de la dernière modification du fichier. À un intervalle configurable, le serveur vérifie si l’heure de modification du fichier a changé. S’il a changé, le serveur recharge automatiquement le contenu du fichier de configuration.

Si vous souhaitez contrôler la fréquence à laquelle le serveur recherche des mises à jour, vous devez définir la variable `refreshDelaySeconds` dans la variable `Caching` élément du fichier de configuration global. Par exemple, si `refreshDelaySeconds` est définie sur 3 600 secondes, le serveur met à jour la configuration au plus une heure à compter de l’heure de modification du fichier de configuration. If `refreshDelaySeconds` est définie sur 0, le serveur recherche les mises à jour de configuration à chaque demande. Il n’est pas recommandé de définir `refreshDelaySeconds` à une valeur faible dans tous les environnements de production, car cela peut affecter les performances.

La variable `Caching` contrôle également le nombre de configurations de clients mises en cache simultanément. Vous pouvez définir cette valeur sur un nombre inférieur au nombre total de clients afin de limiter la quantité de mémoire utilisée pour mettre en cache les informations de configuration. Si une demande est reçue pour un client qui ne se trouve pas dans le cache, la configuration est chargée avant que la demande ne puisse être traitée. Si le cache est plein, le client le moins récemment utilisé est supprimé du cache.

La version mise en cache de la configuration continue à être utilisée dans les situations suivantes (jusqu’à la prochaine vérification de mise à jour par le serveur) :

* Si une modification est enregistrée dans un fichier de configuration ou dans l’un des fichiers de certificat référencés dans la variable [!DNL flashaccess-tenant.xml] pendant que le serveur tente de lire le fichier
* Si l’horodatage du fichier se trouve être inférieur à une seconde avant l’heure actuelle
* Si l’horodatage du fichier se situe dans le futur

En l’absence de version mise en cache, le chargement de la configuration échoue et une erreur est renvoyée au client. Le serveur tente ensuite de charger à nouveau le fichier la prochaine fois qu’il reçoit une demande pour ce client.

## Mise à jour du fichier de configuration global {#section_AA546C72442646CFB8906AEEBDF50587}

Vous pouvez modifier le mot de passe HSM dans [!DNL flashaccess-global.xml] à tout moment. Les modifications prennent effet la prochaine fois que le serveur recharge le fichier de configuration. Toutefois, les modifications apportées aux éléments Journalisation et Mise en cache ne sont pas rechargées. Vous devez redémarrer le serveur avant que les modifications de ces éléments ne prennent effet.

## Mise à jour du fichier de configuration du client {#section_71624DB8DF28480F84F34F0FF7FD4365}

Vous pouvez modifier toutes les valeurs spécifiées dans la variable [!DNL flashaccess-tenant.xml] à tout moment. Les modifications prennent effet la prochaine fois que le serveur recharge le fichier de configuration. De plus, le serveur recherche toutes les modifications apportées aux informations d’identification ( [!DNL .pfx]) et les fichiers de certificat de liste autorisée de packager qui sont référencés dans le fichier de configuration du client.
