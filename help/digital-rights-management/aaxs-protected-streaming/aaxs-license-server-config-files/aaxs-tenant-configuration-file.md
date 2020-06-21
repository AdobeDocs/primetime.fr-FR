---
seo-title: Fichier de configuration du client
title: Fichier de configuration du client
uuid: 6e5c82c9-b8f5-4fca-8325-a884b2c779f7
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 0%

---


# Fichier de configuration du client {#tenant-configuration-file}

Le fichier de configuration flashaccess-locataire.xml contient des paramètres qui s’appliquent à un client spécifique du serveur de licences. Chaque client a sa propre instance de ce fichier de configuration située dans *LicenseServer.ConfigRoot* [!DNL /flashaccessserver/tenants/]*tenantname *. Consultez le répertoire[!DNL configs/flashaccessserver/tenants/sampletenant]pour un exemple de fichier de configuration de client.

Vous pouvez spécifier tous les chemins d&#39;accès aux fichiers dans le fichier de configuration du client sous la forme de chemins d&#39;accès absolus par rapport au répertoire de configuration du client (*LicenseServer.ConfigRoot* [!DNL /flashaccessserver/tenants/]*tenantname *).

Le fichier de configuration du client comprend :

* **Informations d&#39;identification** de transport : spécifie une ou plusieurs informations d&#39;identification de transport (certificat et clé privée) émises par Adobe. Peut être spécifié sous la forme d’un chemin d’accès à un fichier .pfx et d’un mot de passe, ou d’un alias pour des informations d’identification stockées sur un HSM. Plusieurs informations d’identification de ce type peuvent être spécifiées ici, par exemple chemins d’accès aux fichiers ou alias clés, ou les deux. Voir &quot;[Gestion des mises à jour](../../aaxs-protecting-content/content-implementing-the-license-server/content-handling-cert-updates.md)des certificats&quot; dans *Utilisation du SDK Adobe Access pour la protection du contenu* pour en savoir plus sur les informations d’identification supplémentaires nécessaires.
* **Informations d&#39;identification** du serveur de licences : spécifie une ou plusieurs informations d&#39;identification du serveur de licences (certificat et clé privée) émises par Adobe. Peut être spécifié sous la forme d’un chemin d’accès à un fichier .pfx et d’un mot de passe, ou d’un alias pour des informations d’identification stockées sur un HSM. Plusieurs informations d’identification de ce type peuvent être spécifiées ici, par exemple chemins d’accès aux fichiers ou alias clés, ou les deux. Voir Gestion des mises à jour des certificats dans *Utilisation du SDK Adobe Access pour la protection du contenu *pour plus d’informations sur les informations d’identification supplémentaires requises.
* **Certificats** de serveur clé — Facultatif. Spécifie le certificat du serveur de licences du serveur de clés émis par Adobe. Peut être spécifié en tant que chemin d’accès à un fichier .cer ou alias à un certificat stocké sur un HSM. Cette option doit être spécifiée afin d’émettre des licences pour le contenu fourni avec une stratégie qui requiert une diffusion de clé à distance pour les périphériques iOS.
* **Autorisations** personnalisées — Facultatif. Spécifie les classes d&#39;autorisation personnalisées à appeler pour chaque demande de licence. Si plusieurs agents d’autorisation sont spécifiés, ils sont appelés dans l’ordre indiqué. Pour plus d’informations, voir &quot;Extensions[d’autorisation](../../aaxs-protected-streaming/custom-authorization-extensions.md)personnalisées&quot;.
* **Liste des Packagers** autorisés — Facultatif. Spécifie les certificats identifiant les entités autorisées à assembler du contenu pour ce serveur de licences. Si aucun certificat de packager n’est spécifié, le serveur délivre des licences pour le contenu conditionné par tout packager.
* **Version** client minimale prise en charge (voir *Utilisation du SDK Adobe Access pour la protection du contenu*).
* **Règles d’utilisation**

   * **Mise en cache** des licences — Facultatif. Indique la durée pendant laquelle la licence peut être stockée sur le client. Par défaut, la mise en cache des licences est désactivée. Pour activer la mise en cache des licences pendant une période limitée, définissez la date de fin ou le nombre de secondes pendant lesquelles la licence doit être stockée (à compter de la date de délivrance de la licence). La définition du nombre de secondes sur 0 désactive la mise en cache des licences.

      Notez que toutes les licences délivrées par le serveur pour la diffusion en flux continu protégée ont une durée d’expiration de 24 heures (86 400 secondes). Cette valeur s’applique donc implicitement en tant que limite supérieure à toute date de fin ou durée définie pour la mise en cache des licences, avec une valeur maximale de 86 400 secondes, même si le schéma impose des limites plus élevées.

   * **Lecture droite** — Au moins un droit doit être spécifié. Si plusieurs droits sont spécifiés, le client utilisera le premier droit pour lequel il répond à toutes les exigences.

      * **Protection** de sortie : contrôle si la sortie sur des périphériques de rendu externes doit être protégée.
      * **Restrictions** des applications AIR et SWF — liste autorisée facultative des applications SWF et AIR pouvant lire le contenu (c&#39;est-à-dire que seules les applications spécifiées sont autorisées). Les applications SWF sont identifiées par une URL ou par le résumé du fichier SWF et le temps maximal de téléchargement et de vérification du fichier digest. Pour plus d&#39;informations sur le calcul du digest SWF, consultez la section &quot;SWF Hash Calculator&quot;. Les applications AIR et iOS sont identifiées par un ID d’éditeur et un ID de l&#39;application facultatif, une version minimale et une version maximale. Si aucune restriction d’application n’est spécifiée, toute application SWF ou AIR peut lire le contenu.
      * **Restrictions** du module DRM et d&#39;exécution : indique le niveau de sécurité minimum requis pour le module DRM/Runtime. Vous pouvez éventuellement inclure une liste bloquée de versions qui ne sont pas autorisées à lire le contenu. Les versions des modules sont identifiées par des attributs tels que le système d’exploitation et/ou un numéro de version. Les restrictions des modules DRM et les restrictions des modules d’exécution prennent désormais en charge les attributs supplémentaires suivants :

         * `oemVendor`
         * `model`
         * `screenType`
         Les attributs suivants sont désormais facultatifs :

         * `osVersion`
         * `version`
      * **Exigences** en matière de capacités du périphérique : spécifie éventuellement les capacités matérielles requises pour accéder au contenu.
      * **Exigences** de détection de jailbreak : spécifie (facultatif) que la lecture n&#39;est pas autorisée pour les périphériques sur lesquels un jailbreak est détecté.



Pour plus d&#39;informations, consultez les commentaires de l&#39;exemple de fichier de configuration du client.
