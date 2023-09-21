---
title: Exécution du serveur DRM pour la diffusion en continu protégée
description: Exécution du serveur DRM pour la diffusion en continu protégée
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 0%

---

# Exécution du serveur DRM pour la diffusion en continu protégée {#running-the-drm-server-for-protected-streaming}

Avant de pouvoir démarrer Adobe Primetime DRM Server for Protected Streaming, il est recommandé de vérifier la validité des paramètres dans les fichiers de configuration.

Vous pouvez vérifier la validité des paramètres à l’aide des utilitaires fournis avec le serveur de licences. (Voir *Validateur de configuration* dans ce guide.

Si vous souhaitez démarrer Tomcat et le serveur de licences, vous devez exécuter [!DNL catalina.bat start] ou [!DNL catalina.sh start] de Tomcat [!DNL bin] répertoire .

Une fois le serveur démarré, vous devez vérifier qu’il a été correctement configuré en ouvrant `https://<lic<span></span>ense-server-host:port>/flashaccessserver/<tenant-name>/flashaccess/license/v1` dans une fenêtre de navigateur. Si la configuration du client a été chargée avec succès, un message de confirmation s’affiche.

## Fichiers de log {#log-files}

Les fichiers journaux générés par le serveur DRM Adobe Primetime pour l’application de diffusion en continu protégée se trouvent dans le répertoire spécifié par LicenseServer.LogRoot.

>[!NOTE]
>
>Si les fichiers journaux actuels sont supprimés ou déplacés pendant l’exécution du serveur, il est possible que le fichier journal ne soit pas recréé. Par conséquent, certaines informations de journal peuvent être supprimées.

### Structure du répertoire de journal {#section_F490A483D60145ADBC21038914C39203}

Les répertoires de logs sont structurés pour faciliter leur utilisation. Le répertoire des journaux présente la structure suivante :

```
<i class="+ topic ph hi-d="" i "="">
 LicenseServer.LogRoot/ 
 flashaccess-global.log 
     flashaccessserver/ 
         flashaccess-partition.log 
         tenants/ 
             
 <i class="+ topic ph hi-d="" i "="">
  tenantname/ 
                  flashaccess-tenant.log
 </i class="+ topic>
</i class="+ topic>
```

### Fichier journal global {#section_1CFA90748142439C9F3BE380969539DA}

Le fichier journal global, [!DNL flashaccess-global.log], se trouve dans *LicenseServer.LogRoot*. Le journal peut inclure des messages de journal générés par le SDK Java DRM d’Adobe Primetime ou des messages de journal pendant l’initialisation du serveur.

### Fichier journal de partition {#section_5660137CD6AA40519E72A4315534846B}

Le fichier journal de la partition, [!DNL flashaccess-partition.log], se trouve dans la variable `<LicenseServer.LogRoot>/flashaccesserver` répertoire . Il inclut les messages de journal qui ont été générés pendant le traitement d’une demande de licence.

### Fichier journal du client {#section_F0257CC0831647F18A746B4F02E3E910}

le fichier journal du client de chaque client, [!DNL flashaccess-tenant.log], se trouve dans `<LicenseServer.LogRoot>/flashaccesserver/tenants/<tenantname>`. Le journal du client comprend des informations d’audit qui décrivent chaque licence générée pour ce client.

## Mise à jour des fichiers de configuration {#updating-configuration-files}

Dès que le serveur de licences lit l’un des fichiers de configuration du serveur de licences (configuration globale ou client), les informations de configuration sont mises en cache en mémoire. Par conséquent, les fichiers n’ont pas à être lus sur le disque pour chaque demande de licence. Cependant, le serveur permet également de modifier la plupart des valeurs des fichiers de configuration sans qu’il faille redémarrer le serveur pour que les modifications soient prises en compte.

Chaque fois que vous modifiez le fichier de configuration, le serveur de licences stocke l’heure de la dernière modification du fichier. À un intervalle configurable, le serveur vérifie si l’heure de modification du fichier a changé. S’il a changé, le serveur recharge automatiquement le contenu du fichier de configuration.

Si vous souhaitez contrôler la fréquence à laquelle le serveur recherche des mises à jour, vous devez définir la variable `refreshDelaySeconds` dans la variable `Caching` élément du fichier de configuration global. Par exemple, si `refreshDelaySeconds` est définie sur 3 600 secondes, le serveur met à jour la configuration au plus une heure à compter de l’heure de modification du fichier de configuration. If `refreshDelaySeconds` est définie sur 0, le serveur recherche les mises à jour de configuration à chaque demande. Il n’est pas recommandé de définir `refreshDelaySeconds` à une valeur faible dans tous les environnements de production, car cela peut affecter les performances.

La variable `Caching` contrôle également le nombre de configurations de clients mises en cache simultanément. Vous pouvez définir cette valeur sur un nombre inférieur au nombre total de clients afin de limiter la quantité de mémoire utilisée pour mettre en cache les informations de configuration. Si une demande est reçue pour un client qui ne se trouve pas dans le cache, la configuration est chargée avant que la demande ne puisse être traitée. Si le cache est plein, le client le moins récemment utilisé est supprimé du cache.

La version mise en cache de la configuration continue à être utilisée dans les situations suivantes (jusqu’à la prochaine vérification de mise à jour par le serveur) :

* Si une modification est enregistrée dans un fichier de configuration ou dans l’un des fichiers de certificat référencés dans la variable [!DNL flashaccess-tenant.xml] pendant que le serveur tente de lire le fichier
* Si l’horodatage du fichier se trouve être inférieur à une seconde avant l’heure actuelle
* Si l’horodatage du fichier se situe dans le futur

En l’absence de version mise en cache, le chargement de la configuration échoue et une erreur est renvoyée au client. Le serveur tente ensuite de charger à nouveau le fichier la prochaine fois qu’il reçoit une demande pour ce client.

### Mise à jour du fichier de configuration global {#section_AA546C72442646CFB8906AEEBDF50587}

Vous pouvez modifier le mot de passe HSM dans [!DNL flashaccess-global.xml] à tout moment. Les modifications prennent effet la prochaine fois que le serveur recharge le fichier de configuration. Toutefois, les modifications apportées aux éléments Journalisation et Mise en cache ne sont pas rechargées. Vous devez redémarrer le serveur avant que les modifications de ces éléments ne prennent effet.

### Mise à jour du fichier de configuration du client {#section_71624DB8DF28480F84F34F0FF7FD4365}

Vous pouvez modifier toutes les valeurs spécifiées dans la variable [!DNL flashaccess-tenant.xml] à tout moment. Les modifications prennent effet la prochaine fois que le serveur recharge le fichier de configuration. De plus, le serveur recherche toutes les modifications apportées aux informations d’identification ( [!DNL .pfx]) et les fichiers de certificat de liste autorisée de packager qui sont référencés dans le fichier de configuration du client.
