---
description: Le fichier de configuration flashaccess-tenant.xml comprend les paramètres qui s’appliquent à un client spécifique du serveur de licences.
title: Fichier de configuration du client
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 0%

---

# Fichier de configuration du client{#tenant-configuration-file}

Le fichier de configuration flashaccess-tenant.xml comprend les paramètres qui s’appliquent à un client spécifique du serveur de licences.

Chaque client prend en charge sa propre instance de ce fichier de configuration situé dans `<LicenseServer.ConfigRoot>/flashaccessserver/tenants/<tenantname>`. Voir `configs/flashaccessserver/tenants/sampletenant` pour un exemple de fichier de configuration du client.

Vous pouvez spécifier tous les chemins d’accès aux fichiers dans le fichier de configuration du client sous la forme de chemins d’accès absolus ou de chemins d’accès relatifs au répertoire de configuration du client (`<LicenseServer.ConfigRoot>/flashaccessserver/tenants/<tenantname>`).

Le fichier de configuration du client comprend :

* *Transport Credential* — Indique une ou plusieurs informations d’identification de transport (certificat et clé privée) émises par l’Adobe. Peut être spécifié en tant que chemin d’accès à un [!DNL .pfx] fichier et mot de passe, ou alias des informations d’identification stockées sur un HSM. Plusieurs informations d’identification de ce type peuvent être spécifiées ici, comme les chemins d’accès aux fichiers ou les alias clés, ou les deux.

  Voir *Gestion des mises à jour des certificats* in *Utilisation du SDK Adobe Primetime DRM pour la protection du contenu* pour plus d’informations sur le moment où des informations d’identification supplémentaires sont nécessaires.

* *Informations d’identification du serveur de licences* — Spécifie une ou plusieurs informations d’identification de serveur de licences (certificat et clé privée) que l’Adobe a émises. Vous pouvez spécifier les informations d’identification du serveur de licences en tant que chemin d’accès à un [!DNL .pfx] fichier et mot de passe, ou alias des informations d’identification stockées sur un HSM. Plusieurs informations d’identification de ce type peuvent être spécifiées ici, comme les chemins d’accès aux fichiers ou les alias clés, ou les deux.

  Voir *Gestion des mises à jour des certificats* in *Utilisation du SDK Adobe Primetime DRM pour la protection du contenu* pour plus d’informations sur le moment où des informations d’identification supplémentaires sont nécessaires.

* *Certificats de serveur clés* — Vous pouvez éventuellement spécifier le certificat du serveur de licences du serveur de clés émis par l’Adobe. Vous pouvez spécifier le certificat du serveur de licences du serveur de clés comme chemin d’accès à un [!DNL .cer] fichier ou alias d’un certificat stocké sur un HSM. Cette option doit être spécifiée pour émettre des licences pour le contenu fourni avec une stratégie DRM qui nécessite une diffusion à distance par clé pour les appareils iOS.

* *Autorisateurs personnalisés* — Vous pouvez éventuellement spécifier des classes d’agent d’autorisation personnalisées à appeler pour chaque demande de licence. Si plusieurs agents d’autorisation sont spécifiés, ils sont appelés dans l’ordre indiqué.
* *Liste des packages autorisés* — Vous pouvez éventuellement spécifier des certificats qui identifient les entités autorisées à regrouper du contenu pour ce serveur de licences. Si aucun certificat de packager n’est spécifié, le serveur émet des licences pour le contenu conditionné par n’importe quel programme de package. Si le serveur reçoit une demande de licence d’un packager non autorisé, la demande est refusée.
* *Version minimale du client prise en charge* Voir Utilisation du SDK DRM Adobe Primetime pour la protection du contenu.

* *Règles d’utilisation*

   * *Mise en cache des licences* — Permet d’indiquer la durée pendant laquelle vous pouvez stocker la licence sur le client. Par défaut, la mise en cache des licences est désactivée. Si vous souhaitez activer la mise en cache des licences pendant une période limitée, vous devez définir la date de fin ou le nombre de secondes pour lesquelles la licence doit être stockée (à partir du moment où la licence est émise). La définition du nombre de secondes sur 0 désactive la mise en cache de licence.

     >[!NOTE]
     >
     >Toutes les licences que le serveur pour la diffusion en continu protégée a délivrées comprennent une période d’expiration de 24 heures (86 400 secondes). Cette valeur s’applique implicitement en tant que limite supérieure à toute date ou durée définie pour la mise en cache de licence, avec une valeur maximale de 86 400 secondes, même si le schéma applique des limites plus élevées.

   * *Lecture droite* — Un droit minimum doit être spécifié. Si vous spécifiez plusieurs droits, le client utilise le premier droit qui répond à toutes les exigences.

      * *Protection de sortie* — Contrôle si la sortie vers les périphériques de rendu externes doit être protégée.
      * *Restrictions relatives aux applications AIR et SWF* — liste autorisée facultative des applications SWF et AIR pouvant lire le contenu (par exemple, seules les applications spécifiées sont autorisées). Les applications de SWF sont identifiées par une URL ou par le résumé du SWF, ainsi que par la durée maximale de téléchargement et de vérification du résumé.

        Voir *Calculateur de hachage du SWF* pour plus d’informations sur le calcul du condensé du SWF.

        Un ID d’éditeur et un ID d’application facultatif, une version minimale et une version maximale identifient les applications AIR et iOS. Si vous ne spécifiez aucune restriction d’application, toute application SWF ou AIR peut lire le contenu.

      * *Restrictions des modules DRM et d’exécution* — Indique le niveau de sécurité minimal requis pour le module DRM/Runtime. Vous pouvez éventuellement inclure une liste bloquée de versions qui ne sont pas autorisées à lire le contenu. Les versions des modules sont identifiées par des attributs, tels que le système d’exploitation et/ou un numéro de version.

        Les restrictions des modules DRM et les restrictions des modules d’exécution prennent désormais en charge les attributs supplémentaires suivants :

         * `oemVendor`
         * `model`
         * `screenType`

        Les attributs suivants sont désormais facultatifs :

         * `osVersion`
         * `version`

      * *Exigences en matière de capacité d’appareil* — Permet de spécifier les fonctionnalités matérielles requises pour accéder au contenu.
      * *Exigences de détection des jailliers* — Le cas échéant, indique que la lecture n’est pas autorisée pour les appareils sur lesquels un saut de jaillissement est détecté.

Pour plus d’informations, consultez les commentaires dans l’exemple de fichier de configuration du client.
