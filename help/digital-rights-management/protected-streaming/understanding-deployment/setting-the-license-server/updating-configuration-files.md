---
description: Dès que le serveur de licences lit l’un des fichiers de configuration du serveur de licences (configuration globale ou locataire), les informations de configuration sont mises en cache en mémoire. Par conséquent, les fichiers ne doivent pas être lus sur le disque pour chaque demande de licence. Cependant, le serveur permet également de modifier la plupart des valeurs des fichiers de configuration sans avoir à redémarrer le serveur pour que les modifications prennent effet.
seo-description: Dès que le serveur de licences lit l’un des fichiers de configuration du serveur de licences (configuration globale ou locataire), les informations de configuration sont mises en cache en mémoire. Par conséquent, les fichiers ne doivent pas être lus sur le disque pour chaque demande de licence. Cependant, le serveur permet également de modifier la plupart des valeurs des fichiers de configuration sans avoir à redémarrer le serveur pour que les modifications prennent effet.
seo-title: Mise à jour des fichiers de configuration
title: Mise à jour des fichiers de configuration
uuid: 34b3247c-3458-49de-b1b0-dc0ebbf61c88
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Mise à jour des fichiers de configuration{#updating-configuration-files}

Dès que le serveur de licences lit l’un des fichiers de configuration du serveur de licences (configuration globale ou locataire), les informations de configuration sont mises en cache en mémoire. Par conséquent, les fichiers ne doivent pas être lus sur le disque pour chaque demande de licence. Cependant, le serveur permet également de modifier la plupart des valeurs des fichiers de configuration sans avoir à redémarrer le serveur pour que les modifications prennent effet.

Chaque fois que vous modifiez le fichier de configuration, le serveur de licences enregistre l’heure de la dernière modification du fichier. À un intervalle configurable, le serveur vérifie si l’heure de modification du fichier a changé. S’il a changé, le serveur recharge automatiquement le contenu du fichier de configuration.

Si vous souhaitez contrôler la fréquence à laquelle le serveur recherche les mises à jour, vous devez définir l’ `refreshDelaySeconds` attribut dans l’ `Caching` élément du fichier de configuration global. Si, par exemple, `refreshDelaySeconds` est défini sur 3 600 secondes, le serveur met à jour la configuration dans un délai maximal d’une heure à compter de la date de modification du fichier de configuration. Si `refreshDelaySeconds` est défini sur 0, le serveur recherche les mises à jour de configuration à chaque demande. Il n’est pas recommandé de définir `refreshDelaySeconds` une valeur faible dans un de production  car cela peut affecter les performances.

L’ `Caching` élément contrôle également le nombre de configurations de locataires mises en cache à la fois. Vous pouvez définir cette valeur sur un nombre inférieur au nombre total de locataires afin de limiter la quantité de mémoire utilisée pour mettre en cache les informations de configuration. Si une requête est reçue pour un client qui ne se trouve pas dans le cache, la configuration est chargée avant que la requête ne puisse être traitée. Si le cache est plein, le client le moins récemment utilisé est supprimé du cache.

La version mise en cache de la configuration continue à être utilisée dans les situations suivantes (jusqu’à la prochaine fois que le serveur vérifie les mises à jour) :

* Si une modification est enregistrée dans un fichier de configuration ou dans l’un des fichiers de certificat référencés dans le [!DNL flashaccess-tenant.xml] fichier pendant que le serveur tente de lire le fichier
* Si l’horodatage du fichier est inférieur à une seconde avant l’heure actuelle
* Si l’horodatage du fichier est dans le futur

S’il n’existe pas de version mise en cache, le chargement de la configuration échoue et une erreur est renvoyée au client. Le serveur tente ensuite de charger à nouveau le fichier la prochaine fois qu’il reçoit une demande pour ce client.

## Mise à jour du fichier de configuration global {#section_AA546C72442646CFB8906AEEBDF50587}

Vous pouvez à tout moment modifier le mot de passe HSM [!DNL flashaccess-global.xml] à tout moment. Les modifications prennent effet la prochaine fois que le serveur recharge le fichier de configuration. Toutefois, les modifications apportées aux éléments Journalisation et Mise en cache ne sont pas rechargées. Vous devez redémarrer le serveur avant que les modifications apportées à ces éléments ne prennent effet.

## Mise à jour du fichier de configuration du client {#section_71624DB8DF28480F84F34F0FF7FD4365}

Vous pouvez à tout moment modifier toutes les valeurs spécifiées dans le [!DNL flashaccess-tenant.xml] fichier. Les modifications prennent effet la prochaine fois que le serveur recharge le fichier de configuration. En outre, le serveur recherche toutes les modifications apportées à tous les fichiers d’informations d’identification ( [!DNL .pfx]) et aux fichiers de certificat de liste blanche de l’outil de traitement des balises qui sont référencés dans le fichier de configuration du client.
