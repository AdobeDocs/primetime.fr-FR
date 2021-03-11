---
title: Exécution du serveur DRM pour la diffusion en flux continu protégée
description: Exécution du serveur DRM pour la diffusion en flux continu protégée
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 0%

---


# Exécution du serveur DRM pour la diffusion en flux continu protégée {#running-the-drm-server-for-protected-streaming}

Avant de pouvoir début au serveur Adobe Primetime DRM pour la diffusion en flux continu protégée, il est recommandé de vérifier la validité des paramètres dans les fichiers de configuration.

Vous pouvez vérifier la validité des paramètres en utilisant les utilitaires fournis avec le serveur de licences. (Voir *Validation de configuration* dans ce guide.

Si vous souhaitez début Tomcat et le serveur de licences, vous devez exécuter [!DNL catalina.bat start] ou [!DNL catalina.sh start] à partir du répertoire [!DNL bin] de Tomcat.

Une fois le serveur démarré, vous devez vérifier qu’il a été correctement configuré en ouvrant `https://<lic<span></span>ense-server-host:port>/flashaccessserver/<tenant-name>/flashaccess/license/v1` dans une fenêtre de navigateur. Si la configuration du client a été correctement chargée, un message de confirmation s&#39;affiche.

## Fichiers journaux {#log-files}

Les fichiers journaux générés par le serveur DRM Adobe Primetime pour l’application de diffusion en flux continu protégée se trouvent dans le répertoire spécifié par LicenseServer.LogRoot.

>[!NOTE]
>
>Si les fichiers journaux actuels sont supprimés ou déplacés pendant l&#39;exécution du serveur, il est possible que le fichier journal ne soit pas recréé. Par conséquent, certaines informations de journal peuvent être supprimées.

### Structure du répertoire de journalisation {#section_F490A483D60145ADBC21038914C39203}

Les répertoires de journaux sont structurés pour faciliter leur utilisation. Le répertoire des journaux possède la structure suivante :

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

Le fichier journal global, [!DNL flashaccess-global.log], se trouve dans *LicenseServer.LogRoot*. Le journal peut inclure des messages de journal que le SDK Java DRM d&#39;Adobe Primetime ou des messages de journal peuvent avoir générés au moment de l&#39;initialisation du serveur.

### Fichier journal de partition {#section_5660137CD6AA40519E72A4315534846B}

Le fichier journal des partitions, [!DNL flashaccess-partition.log], se trouve dans le répertoire `<LicenseServer.LogRoot>/flashaccesserver`. Il comprend les messages du journal qui ont été générés pendant le traitement d’une demande de licence.

### Fichier journal du client {#section_F0257CC0831647F18A746B4F02E3E910}

Le fichier journal du client de chaque client, [!DNL flashaccess-tenant.log], se trouve dans `<LicenseServer.LogRoot>/flashaccesserver/tenants/<tenantname>`. Le journal du client contient des informations de contrôle décrivant chaque licence générée pour ce client.

## Mise à jour des fichiers de configuration {#updating-configuration-files}

Dès que le serveur de licences lit l’un des fichiers de configuration du serveur de licences (configuration globale ou de client), les informations de configuration sont mises en cache en mémoire. Par conséquent, les fichiers ne doivent pas être lus sur le disque pour chaque demande de licence. Cependant, le serveur permet également de modifier la plupart des valeurs des fichiers de configuration sans redémarrer le serveur pour que les modifications prennent effet.

Chaque fois que vous modifiez le fichier de configuration, le serveur de licences enregistre l’heure de la dernière modification du fichier. À un intervalle configurable, le serveur vérifie si l’heure de modification du fichier a changé. Si elle a été modifiée, le serveur recharge automatiquement le contenu du fichier de configuration.

Si vous souhaitez contrôler la fréquence à laquelle le serveur recherche des mises à jour, vous devez définir l&#39;attribut `refreshDelaySeconds` dans l&#39;élément `Caching` du fichier de configuration global. Par exemple, si `refreshDelaySeconds` est défini sur 3 600 secondes, le serveur mettra à jour la configuration dans un délai maximum d&#39;une heure à compter de l&#39;heure de modification du fichier de configuration. Si `refreshDelaySeconds` est défini sur 0, le serveur recherche les mises à jour de configuration à chaque requête. Il n’est pas recommandé de définir `refreshDelaySeconds` sur une valeur faible dans les environnements de production, car cela peut affecter les performances.

L’élément `Caching` contrôle également le nombre de configurations de locataires mises en cache en même temps. Vous pouvez définir cette valeur sur un nombre inférieur au nombre total de locataires afin de limiter la quantité de mémoire utilisée pour mettre en cache les informations de configuration. Si une demande est reçue pour un client qui ne se trouve pas dans le cache, la configuration est chargée avant que la demande ne puisse être traitée. Si le cache est plein, le locataire le moins récemment utilisé est supprimé du cache.

La version mise en cache de la configuration continue à être utilisée dans les situations suivantes (jusqu’à la prochaine fois que le serveur recherche des mises à jour) :

* Si une modification est enregistrée dans un fichier de configuration ou dans l&#39;un des fichiers de certificat référencés dans le fichier [!DNL flashaccess-tenant.xml] pendant que le serveur tente de lire le fichier
* Si l’horodatage du fichier se révèle inférieur à une seconde avant l’heure actuelle
* Si l’horodatage du fichier est dans le futur

S’il n’existe aucune version mise en cache, le chargement de la configuration échoue et une erreur est renvoyée au client. Le serveur tente ensuite de charger à nouveau le fichier la prochaine fois qu’il reçoit une demande pour ce client.

### Mise à jour du fichier de configuration global {#section_AA546C72442646CFB8906AEEBDF50587}

Vous pouvez à tout moment modifier le mot de passe HSM dans [!DNL flashaccess-global.xml]. Les modifications prennent effet la prochaine fois que le serveur recharge le fichier de configuration. Toutefois, les modifications apportées aux éléments de journalisation et de mise en cache ne sont pas rechargées. Vous devez redémarrer le serveur avant que les modifications apportées à ces éléments ne prennent effet.

### Mise à jour du fichier de configuration du client {#section_71624DB8DF28480F84F34F0FF7FD4365}

Vous pouvez à tout moment modifier toutes les valeurs spécifiées dans le fichier [!DNL flashaccess-tenant.xml]. Les modifications prennent effet la prochaine fois que le serveur recharge le fichier de configuration. En outre, le serveur recherche toutes les modifications apportées à tous les fichiers d’informations d’identification ( [!DNL .pfx]) et aux fichiers de certificat de liste autorisée de packager référencés dans le fichier de configuration du client.