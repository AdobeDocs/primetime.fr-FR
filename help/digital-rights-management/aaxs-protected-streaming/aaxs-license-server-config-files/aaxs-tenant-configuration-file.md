---
seo-title: Fichier de configuration du client
title: Fichier de configuration du client
uuid: 6e5c82c9-b8f5-4fca-8325-a884b2c779f7
translation-type: tm+mt
source-git-commit: 47b2ed65ff0ea4f54a210cf7627ed535782296b9

---


# Fichier de configuration du client {#tenant-configuration-file}

Le fichier de configuration flashaccess-locataire.xml contient les paramètres qui s’appliquent à un client spécifique du serveur de licences. Chaque client dispose de sa propre instance de ce fichier de configuration situé dans *LicenseServer.ConfigRoot* [!DNL /flashaccessserver/tenants/]*nom *du client. Voir le[!DNL configs/flashaccessserver/tenants/sampletenant]répertoire pour consulter un exemple de fichier de configuration de client.

Vous pouvez spécifier tous les chemins d’accès aux fichiers du fichier de configuration du client sous la forme de chemins d’accès absolus ou de chemins d’accès relatifs au répertoire de configuration du client (*LicenseServer.ConfigRoot*[!DNL /flashaccessserver/tenants/]*tenantname *).

Le fichier de configuration du client inclut :

* **Informations d&#39;identification** de transport — Spécifie une ou plusieurs informations d’identification de transport (certificat et clé privée) émises par Adobe. Peut être spécifié sous la forme d’un chemin d’accès à un fichier .pfx et d’un mot de passe, ou d’un alias pour des informations d’identification stockées sur un HSM. Plusieurs informations d’identification de ce type peuvent être spécifiées ici, comme des chemins d’accès aux fichiers ou des alias clés, ou les deux. Voir &quot;[Gestion des mises à jour](../../aaxs-protecting-content/content-implementing-the-license-server/content-handling-cert-updates.md)des certificats&quot; dans *Utilisation du SDK Adobe Access pour la protection du contenu* pour en savoir plus sur les informations d’identification supplémentaires nécessaires.
* **Informations d’identification** du serveur de licences — Spécifie une ou plusieurs informations d’identification de serveur de licences (certificat et clé privée) émises par Adobe. Peut être spécifié sous la forme d’un chemin d’accès à un fichier .pfx et d’un mot de passe, ou d’un alias pour des informations d’identification stockées sur un HSM. Plusieurs informations d’identification de ce type peuvent être spécifiées ici, comme des chemins d’accès aux fichiers ou des alias clés, ou les deux. Voir Gestion des mises à jour de certificats dans *Utilisation du SDK Adobe Access pour la protection du contenu *pour plus d’informations sur les informations d’identification supplémentaires requises.
* **Certificats** de serveur clé — Facultatif. Spécifie le certificat du serveur de licences du serveur de clés émis par Adobe. Peut être spécifié sous la forme d’un chemin d’accès à un fichier .cer ou d’un alias vers un certificat stocké sur un HSM. Cette option doit être spécifiée afin d’émettre des licences pour le contenu fourni avec une stratégie nécessitant des  de clé à distance pour les périphériques iOS.
* **Autorisations** personnalisées — Facultatif. Spécifie les classes d’autorisation personnalisées à appeler pour chaque demande de licence. Si plusieurs autorités sont spécifiées, elles sont appelées dans l’ordre indiqué. Pour plus d’informations, voir &quot;Extensions[d’autorisation](../../aaxs-protected-streaming/custom-authorization-extensions.md)personnalisées&quot;.
* **des conditionneurs** autorisés — Facultatif. Spécifie les certificats identifiant les entités autorisées à assembler du contenu pour ce serveur de licences. Si aucun certificat Packager n’est spécifié, le serveur délivre des licences pour le contenu compressé par un quelconque gestionnaire de package.
* **Version** client minimale prise en charge (voir *Utilisation du SDK Adobe Access pour la protection du contenu*).
* **Règles d’utilisation**

   * **Mise en cache** des licences — Facultatif. Indique la durée pendant laquelle la licence peut être stockée sur le client. Par défaut, la mise en cache des licences est désactivée. Pour activer la mise en cache des licences pendant une période limitée, définissez la date de fin ou le nombre de secondes pendant lesquelles la licence doit être stockée (à partir du moment où la licence est délivrée). La définition du nombre de secondes sur 0 désactive la mise en cache des licences.

      Notez que toutes les licences émises par le serveur pour la diffusion en flux continu protégée ont une durée d’expiration de 24 heures (86 400 secondes). Cette valeur s’applique donc implicitement en tant que limite supérieure à la date ou la durée de fin définie pour la mise en cache de la licence, avec une valeur maximale de 86 400 secondes, même si le impose des limites plus élevées.

   * **Lecture droite** — Au moins un droit doit être spécifié. Si plusieurs droits sont spécifiés, le client utilisera le premier droit pour lequel il répond à toutes les exigences.

      * **Protection** de sortie — Contrôle si la sortie vers des périphériques de rendu externes doit être protégée.
      * **Restrictions** des applications AIR et SWF — Liste blanche facultative des applications SWF et AIR pouvant lire le contenu (c.-à-d. que seules les applications spécifiées sont autorisées). Les applications SWF sont identifiées par une URL ou par le résumé du fichier SWF et le temps maximal pour permettre le téléchargement et la vérification du fichier digest. Pour plus d’informations sur le calcul du condensé SWF, consultez la section &quot;Calculateur de hachage SWF&quot;. Les applications AIR et iOS sont identifiées par un ID d’éditeur et un facultatif, une version minimale et une version maximale. Si aucune restriction d’application n’est spécifiée, tout fichier SWF ou toute application AIR peut lire le contenu.
      * **Restrictions** de DRM et de module d&#39;exécution — Spécifie le niveau de sécurité minimal requis pour le module DRM/Runtime. Vous pouvez éventuellement inclure une liste noire des versions qui ne sont pas autorisées à lire le contenu. Les versions des modules sont identifiées par des attributs tels que le système d’exploitation et/ou un numéro de version. Les restrictions des modules DRM et les restrictions des modules d’exécution prennent désormais en charge les attributs supplémentaires suivants :

         * `oemVendor`
         * `model`
         * `screenType`
         Les attributs suivants sont désormais facultatifs :

         * `osVersion`
         * `version`
      * **Exigences** en matière de capacité de l&#39;appareil — Le cas échéant, indique les capacités matérielles requises pour accéder au contenu.
      * **Exigences** en matière de détection des sauts de chasse — Le cas échéant, cette option indique que la lecture n’est pas autorisée pour les périphériques sur lesquels le jailbreak est détecté.



Voir les commentaires dans l&#39;exemple de fichier de configuration du client pour plus d&#39;informations.
