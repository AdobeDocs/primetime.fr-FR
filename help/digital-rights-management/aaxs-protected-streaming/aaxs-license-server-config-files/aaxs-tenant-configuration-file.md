---
title: Fichier de configuration du client
description: Fichier de configuration du client
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Fichier de configuration du client {#tenant-configuration-file}

Le fichier de configuration flashaccess-tenant.xml contient les paramètres qui s’appliquent à un client spécifique du serveur de licences. Chaque client possède sa propre instance de ce fichier de configuration située dans *LicenseServer.ConfigRoot* [!DNL /flashaccessserver/tenants/]*tenantname*. Voir [!DNL configs/flashaccessserver/tenants/sampletenant] pour un exemple de fichier de configuration du client.

Vous pouvez spécifier tous les chemins d’accès aux fichiers dans le fichier de configuration du client sous la forme de chemins ou chemins absolus relatifs au répertoire de configuration du client (*LicenseServer.ConfigRoot* [!DNL /flashaccessserver/tenants/]*tenantname*).

Le fichier de configuration du client comprend :

* **Transport Credential** — Indique une ou plusieurs informations d’identification de transport (certificat et clé privée) émises par l’Adobe. Peut être spécifié sous la forme d’un chemin d’accès à un fichier .pfx et à un mot de passe, ou d’un alias pour des informations d’identification stockées sur un HSM. Plusieurs informations d’identification de ce type peuvent être spécifiées ici, comme les chemins d’accès aux fichiers ou les alias clés, ou les deux. Voir &quot;[Gestion des mises à jour des certificats](../../aaxs-protecting-content/content-implementing-the-license-server/content-handling-cert-updates.md)&quot; dans *Utilisation du SDK Adobe Access pour la protection du contenu* pour plus d’informations sur le moment où des informations d’identification supplémentaires sont nécessaires.
* **Informations d’identification du serveur de licences** — Spécifie une ou plusieurs informations d’identification de serveur de licences (certificat et clé privée) émises par l’Adobe. Peut être spécifié sous la forme d’un chemin d’accès à un fichier .pfx et à un mot de passe, ou d’un alias pour des informations d’identification stockées sur un HSM. Plusieurs informations d’identification de ce type peuvent être spécifiées ici, comme les chemins d’accès aux fichiers ou les alias clés, ou les deux. Voir Gestion des mises à jour de certificat dans *Utilisation du SDK Adobe Access pour la protection du contenu* pour plus d’informations sur les cas où des informations d’identification supplémentaires sont nécessaires.
* **Certificats de serveur clés** : facultatif. Indique le certificat du serveur de licences du serveur de clés émis par Adobe. Peut être spécifié sous la forme d’un chemin d’accès à un fichier .cer ou d’un alias vers un certificat stocké sur un HSM. Cette option doit être spécifiée afin d’émettre des licences pour le contenu mis en package avec une stratégie qui nécessite une diffusion à distance par clé pour les appareils iOS.
* **Autorisateurs personnalisés** : facultatif. Spécifie les classes d’autorisation personnalisées à appeler pour chaque demande de licence. Si plusieurs agents d’autorisation sont spécifiés, ils sont appelés dans l’ordre indiqué. Pour plus d’informations, voir &quot;[Extensions d’autorisation personnalisées](../../aaxs-protected-streaming/custom-authorization-extensions.md)&quot;.
* **Liste des packages autorisés** : facultatif. Indique les certificats identifiant les entités autorisées à regrouper du contenu pour ce serveur de licences. Si aucun certificat de packager n’est spécifié, le serveur émet des licences pour le contenu conditionné par n’importe quel programme de package.
* **Version minimale du client prise en charge** (Voir *Utilisation du SDK Adobe Access pour la protection du contenu*).
* **Règles d’utilisation**

   * **Mise en cache des licences** : facultatif. Indique la durée pendant laquelle la licence peut être stockée sur le client. Par défaut, la mise en cache des licences est désactivée. Pour activer la mise en cache des licences pendant une période limitée, définissez la date de fin ou le nombre de secondes pour lesquelles la licence doit être stockée (à partir de l’émission de la licence). La définition du nombre de secondes sur 0 désactive la mise en cache de licence.

     Notez que toutes les licences émises par le serveur pour la diffusion en continu protégée ont une période d’expiration de 24 heures (86 400 secondes). Cette valeur s’applique donc implicitement en tant que limite supérieure à toute date de fin ou durée définie pour la mise en cache de licence, avec une valeur maximale de 86 400 secondes, même si le schéma applique des limites plus élevées.

   * **Lecture droite** — Au moins un droit doit être spécifié. Si plusieurs droits sont spécifiés, le client utilisera le premier droit pour lequel il répond à toutes les exigences.

      * **Protection de sortie** — Contrôle si la sortie vers les périphériques de rendu externes doit être protégée.
      * **Restrictions relatives aux applications AIR et SWF** — liste autorisée facultative des applications SWF et AIR pouvant lire le contenu (c.-à-d. que seules les applications spécifiées sont autorisées). Les applications de SWF sont identifiées par une URL ou par le résumé du SWF, ainsi que par la durée maximale de téléchargement et de vérification du résumé. Pour plus d’informations sur le calcul du condensé du SWF, voir la section &quot;Calcul de hachage du SWF&quot;. Les applications AIR et iOS sont identifiées par un ID d’éditeur et un ID d’application facultatif, une version minimale et une version maximale. Si aucune restriction d’application n’est spécifiée, tout SWF ou application AIR peut lire le contenu.
      * **Restrictions des modules DRM et d’exécution** — Indique le niveau de sécurité minimal requis pour le module DRM/Runtime. Vous pouvez éventuellement inclure une liste bloquée de versions qui ne sont pas autorisées à lire le contenu. Les versions des modules sont identifiées par des attributs tels que le système d’exploitation et/ou un numéro de version. Les restrictions des modules DRM et les restrictions des modules d’exécution prennent désormais en charge les attributs supplémentaires suivants :

         * `oemVendor`
         * `model`
         * `screenType`

        Les attributs suivants sont désormais facultatifs :

         * `osVersion`
         * `version`

      * **Exigences en matière de capacité d’appareil** — Permet de spécifier les fonctionnalités matérielles requises pour accéder au contenu.
      * **Exigences de détection des jailliers** — Le cas échéant, indique que la lecture n’est pas autorisée pour les appareils sur lesquels un saut de jaillissement est détecté.

Pour plus d’informations, consultez les commentaires dans l’exemple de fichier de configuration du client.
