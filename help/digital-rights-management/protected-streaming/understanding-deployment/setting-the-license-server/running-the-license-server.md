---
seo-title: Exécution du serveur DRM pour la diffusion en flux continu protégée
title: Exécution du serveur DRM pour la diffusion en flux continu protégée
uuid: 9bbe211d-268b-43c2-9e55-7ce62de40d30
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Exécution du serveur DRM pour la diffusion en flux continu protégée {#running-the-drm-server-for-protected-streaming}

Avant de pouvoir début d’Adobe Primetime DRM Server for Protected Streaming, il est recommandé de vérifier la validité des paramètres des fichiers de configuration.

Vous pouvez vérifier la validité des paramètres en utilisant les utilitaires fournis avec le serveur de licences. (Voir *Configuration validator* dans ce guide.

Si vous voulez début Tomcat et le serveur de licences, vous devez exécuter [!DNL catalina.bat start] ou [!DNL catalina.sh start] à partir du [!DNL bin] répertoire de Tomcat.

Une fois le serveur démarré, vous devez vérifier qu’il a été correctement configuré en ouvrant [!DNL https://<lic<span></span>ense-server-host:port>/flashaccessserver/<tenant-name>/flashaccess/license/v1] dans une fenêtre de navigateur. Si la configuration du client a été correctement chargée, un message de confirmation s&#39;affiche.

## Fichiers journaux {#log-files}

Les fichiers journaux générés par le serveur DRM d’Adobe Primetime pour l’application de diffusion en flux continu protégée se trouvent dans le répertoire spécifié par LicenseServer.LogRoot.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
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

Le fichier journal global [!DNL flashaccess-global.log]se trouve dans *LicenseServer.LogRoot*. Le journal peut inclure des messages journaux que le SDK Java DRM d’Adobe Primetime ou des messages journaux peuvent avoir générés pendant l’initialisation du serveur.

### Fichier journal de partition {#section_5660137CD6AA40519E72A4315534846B}

Le fichier journal des partitions [!DNL flashaccess-partition.log]se trouve dans le [!DNL <LicenseServer.LogRoot>/flashaccesserver] répertoire. Il comprend les messages du journal qui ont été générés pendant le traitement d’une demande de licence.

### Fichier journal du client {#section_F0257CC0831647F18A746B4F02E3E910}

Le fichier journal de chaque client, [!DNL flashaccess-tenant.log], se trouve dans [!DNL &lt;LicenseServer.LogRoot>/flashaccesserver/locants/<tenantname>]. Le journal du client contient des informations de contrôle décrivant chaque licence générée pour ce client.

## Mise à jour des fichiers de configuration {#updating-configuration-files}

Dès que le serveur de licences lit l’un des fichiers de configuration du serveur de licences (configuration globale ou de client), les informations de configuration sont mises en cache en mémoire. Par conséquent, les fichiers ne doivent pas être lus sur le disque pour chaque demande de licence. Cependant, le serveur permet également de modifier la plupart des valeurs des fichiers de configuration sans redémarrer le serveur pour que les modifications prennent effet.

Chaque fois que vous modifiez le fichier de configuration, le serveur de licences enregistre l’heure de la dernière modification du fichier. À un intervalle configurable, le serveur vérifie si l’heure de modification du fichier a changé. Si elle a été modifiée, le serveur recharge automatiquement le contenu du fichier de configuration.

Si vous souhaitez contrôler la fréquence à laquelle le serveur recherche des mises à jour, vous devez définir l’ `refreshDelaySeconds` attribut dans l’ `Caching` élément du fichier de configuration global. Si, par exemple, `refreshDelaySeconds` est défini sur 3 600 secondes, le serveur met à jour la configuration dans un délai maximum d’une heure à compter de l’heure de modification du fichier de configuration. Si la valeur `refreshDelaySeconds` est 0, le serveur recherche les mises à jour de configuration à chaque demande. Il n’est pas recommandé de définir `refreshDelaySeconds` une valeur faible dans les environnements de production, car cela peut affecter les performances.

L’ `Caching` élément contrôle également le nombre de configurations de locataires mises en cache à la fois. Vous pouvez définir cette valeur sur un nombre inférieur au nombre total de locataires afin de limiter la quantité de mémoire utilisée pour mettre en cache les informations de configuration. Si une demande est reçue pour un client qui ne se trouve pas dans le cache, la configuration est chargée avant que la demande ne puisse être traitée. Si le cache est plein, le locataire le moins récemment utilisé est supprimé du cache.

La version mise en cache de la configuration continue à être utilisée dans les situations suivantes (jusqu’à la prochaine fois que le serveur recherche des mises à jour) :

* Si une modification est enregistrée dans un fichier de configuration ou dans l’un des fichiers de certificat référencés dans le [!DNL flashaccess-tenant.xml] fichier pendant que le serveur tente de lire le fichier
* Si l’horodatage du fichier se révèle inférieur à une seconde avant l’heure actuelle
* Si l’horodatage du fichier est dans le futur

S’il n’existe aucune version mise en cache, le chargement de la configuration échoue et une erreur est renvoyée au client. Le serveur tente ensuite de charger à nouveau le fichier la prochaine fois qu’il reçoit une demande pour ce client.

### Mise à jour du fichier de configuration global {#section_AA546C72442646CFB8906AEEBDF50587}

Vous pouvez à tout moment modifier le mot de passe HSM [!DNL flashaccess-global.xml] à tout moment. Les modifications prennent effet la prochaine fois que le serveur recharge le fichier de configuration. Toutefois, les modifications apportées aux éléments de journalisation et de mise en cache ne sont pas rechargées. Vous devez redémarrer le serveur avant que les modifications apportées à ces éléments ne prennent effet.

### Mise à jour du fichier de configuration du client {#section_71624DB8DF28480F84F34F0FF7FD4365}

Vous pouvez à tout moment modifier toutes les valeurs spécifiées dans le [!DNL flashaccess-tenant.xml] fichier. Les modifications prennent effet la prochaine fois que le serveur recharge le fichier de configuration. En outre, le serveur recherche toutes les modifications dans tous les fichiers d’informations d’identification ( [!DNL .pfx]) et les fichiers de certificat de liste blanche de packager qui sont référencés dans le fichier de configuration du client.