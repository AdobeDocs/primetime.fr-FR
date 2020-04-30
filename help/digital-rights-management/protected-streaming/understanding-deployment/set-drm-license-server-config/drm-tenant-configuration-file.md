---
description: Le fichier de configuration flashaccess-locataire.xml comprend des paramètres qui s’appliquent à un client spécifique du serveur de licences.
seo-description: Le fichier de configuration flashaccess-locataire.xml comprend des paramètres qui s’appliquent à un client spécifique du serveur de licences.
seo-title: Fichier de configuration du client
title: Fichier de configuration du client
uuid: bc9ee4a1-63b6-4362-9929-3e9fe8251075
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Fichier de configuration du client{#tenant-configuration-file}

Le fichier de configuration flashaccess-locataire.xml comprend des paramètres qui s’appliquent à un client spécifique du serveur de licences.

Chaque client prend en charge sa propre instance de ce fichier de configuration situé dans [!DNL &lt;LicenseServer.ConfigRoot>/flashaccessserver/locants/<tenantname>]. Consultez le répertoire [!DNL configs/flashaccessserver/tenants/sampletenant] pour un exemple de fichier de configuration de client.

Vous pouvez spécifier tous les chemins d&#39;accès aux fichiers dans le fichier de configuration du client sous la forme de chemins d&#39;accès absolus ou de chemins d&#39;accès relatifs au répertoire de configuration du client ( [!DNL &lt;LicenseServer.ConfigRoot>/flashaccessoserver/tenants/<tenantname>]).

Le fichier de configuration du client comprend :

* *Informations d’identification* de transport : spécifie une ou plusieurs informations d’identification de transport (certificat et clé privée) émises par Adobe. Peut être spécifié sous la forme d’un chemin d’accès à un [!DNL .pfx] fichier et d’un mot de passe, ou d’un alias pour des informations d’identification stockées sur un HSM. Plusieurs informations d’identification de ce type peuvent être spécifiées ici, par exemple chemins d’accès aux fichiers ou alias clés, ou les deux.

   Voir *Gestion des mises à jour* des certificats dans *Utilisation du SDK DRM d’Adobe Primetime pour la protection du contenu* pour en savoir plus sur les informations d’identification supplémentaires nécessaires.

* *Informations d’identification* du serveur de licences : indique une ou plusieurs informations d’identification du serveur de licences (certificat et clé privée) qu’Adobe a émises. Vous pouvez spécifier les informations d’identification du serveur de licences en tant que chemin d’accès à un [!DNL .pfx] fichier et à un mot de passe, ou encore en tant qu’alias pour les informations d’identification stockées sur un HSM. Plusieurs informations d’identification de ce type peuvent être spécifiées ici, par exemple chemins d’accès aux fichiers ou alias clés, ou les deux.

   Voir *Gestion des mises à jour* des certificats dans *Utilisation du SDK DRM d’Adobe Primetime pour la protection du contenu* pour en savoir plus sur les informations d’identification supplémentaires nécessaires.

* *Certificats* de serveur de clés : indiquez éventuellement le certificat de serveur de licences du serveur de clés émis par Adobe. Vous pouvez spécifier le certificat du serveur de licences du serveur de clés comme chemin d’accès à un [!DNL .cer] fichier ou alias d’un certificat stocké sur un HSM. Cette option doit être spécifiée pour émettre des licences pour le contenu fourni avec une stratégie DRM qui requiert une diffusion de clé à distance pour les périphériques iOS.

* *Agents d&#39;autorisation* personnalisés : spécifie éventuellement les classes d&#39;agents d&#39;autorisation personnalisés à appeler pour chaque demande de licence. Si plusieurs agents d’autorisation sont spécifiés, ils sont appelés dans l’ordre indiqué.
* *Liste des Packagers* autorisés : spécifie éventuellement des certificats qui identifient les entités autorisées à compresser du contenu pour ce serveur de licences. Si aucun certificat de packager n’est spécifié, le serveur délivre des licences pour le contenu conditionné par tout packager. Si le serveur reçoit une demande de licence d’un packager non autorisé, la demande est refusée.
* *Version* client minimale prise en charge Voir Utilisation du SDK DRM d’Adobe Primetime pour la protection du contenu.

* *Règles d’utilisation*

   * *Mise en cache* des licences : indique éventuellement la durée pendant laquelle vous pouvez stocker la licence sur le client. Par défaut, la mise en cache des licences est désactivée. Si vous souhaitez activer la mise en cache des licences pendant une période limitée, vous devez définir la date de fin ou le nombre de secondes pendant lesquelles la licence doit être stockée (à partir de la date de délivrance de la licence). La définition du nombre de secondes sur 0 désactive la mise en cache des licences.

      >[!NOTE]
      >
      >Toutes les licences que le serveur de diffusion en flux continu protégé a délivrées comprennent une période d’expiration de 24 heures (86 400 secondes). Cette valeur s’applique implicitement en tant que limite supérieure à la date ou la durée de fin définie pour la mise en cache des licences, avec une valeur maximale de 86 400 secondes, même si le schéma impose des limites plus élevées.

   * *Lecture droite* : un minimum d&#39;un droit doit être spécifié. Si vous spécifiez plusieurs droits, le client utilise alors le premier droit qui répond à toutes les exigences.

      * *Protection* de sortie : contrôle si la sortie sur des périphériques de rendu externes doit être protégée.
      * *Restrictions* des applications AIR et SWF : liste blanche facultative des applications SWF et AIR pouvant lire le contenu (par exemple, seules les applications spécifiées sont autorisées). Les applications SWF sont identifiées par une URL ou par le résumé du fichier SWF et le temps maximal de téléchargement et de vérification du fichier digest.

         Voir Calculateur *de hachage* SWF pour en savoir plus sur la méthode de calcul du digest SWF.

         Un ID d’éditeur et un ID de l&#39;application facultatif, une version minimale et une version maximale identifient les applications AIR et iOS. Si vous ne spécifiez aucune restriction d’application, tout fichier SWF ou toute application AIR peut lire le contenu.

      * *Restrictions* du module DRM et d&#39;exécution : indique le niveau de sécurité minimum requis pour le module DRM/Runtime. Vous pouvez éventuellement inclure une liste noire des versions qui ne sont pas autorisées à lire le contenu. Les versions des modules sont identifiées par des attributs, tels que le système d’exploitation et/ou un numéro de version.

         Les restrictions des modules DRM et les restrictions des modules d’exécution prennent désormais en charge les attributs supplémentaires suivants :

         * `oemVendor`
         * `model`
         * `screenType`
         Les attributs suivants sont désormais facultatifs :

         * `osVersion`
         * `version`
      * *Exigences* en matière de capacités du périphérique : spécifie éventuellement les capacités matérielles requises pour accéder au contenu.
      * *Exigences* de détection de jailbreak : spécifie (facultatif) que la lecture n&#39;est pas autorisée pour les périphériques sur lesquels un jailbreak est détecté.



Pour plus d&#39;informations, consultez les commentaires de l&#39;exemple de fichier de configuration du client.
