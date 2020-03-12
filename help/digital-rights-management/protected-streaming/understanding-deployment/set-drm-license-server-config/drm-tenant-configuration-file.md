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

Chaque client prend en charge sa propre instance de ce fichier de configuration situé dans [!DNL &lt;LicenseServer.ConfigRoot>/flashaccessoserver/tenants/<tenantname>]. Voir le [!DNL configs/flashaccessserver/tenants/sampletenant] répertoire pour consulter un exemple de fichier de configuration de client.

Vous pouvez spécifier tous les chemins d’accès aux fichiers dans le fichier de configuration du client sous forme de chemins absolus ou de chemins relatifs au répertoire de configuration du client ( [!DNL &lt;LicenseServer.ConfigRoot>/flashaccessoserver/tenants/<tenantname>]).

Le fichier de configuration du client inclut :

* *Informations d&#39;identification* de transport — Spécifie une ou plusieurs informations d’identification de transport (certificat et clé privée) émises par Adobe. Peut être spécifié sous la forme d’un chemin d’accès à un [!DNL .pfx] fichier et d’un mot de passe ou d’un alias pour des informations d’identification stockées sur un HSM. Plusieurs informations d’identification de ce type peuvent être spécifiées ici, comme des chemins d’accès aux fichiers ou des alias clés, ou les deux.

   Voir *Gestion des mises à jour* de certificat dans *Utilisation du SDK DRM Adobe Primetime pour la protection du contenu* pour en savoir plus sur les informations d’identification supplémentaires nécessaires.

* *Informations d’identification* du serveur de licences — Spécifie une ou plusieurs informations d’identification de serveur de licences (certificat et clé privée) qu’Adobe a émises. Vous pouvez spécifier les informations d’identification du serveur de licences comme chemin d’accès à un [!DNL .pfx] fichier et à un mot de passe, ou comme alias pour les informations d’identification stockées sur un HSM. Plusieurs informations d’identification de ce type peuvent être spécifiées ici, comme des chemins d’accès aux fichiers ou des alias clés, ou les deux.

   Voir *Gestion des mises à jour* de certificat dans *Utilisation du SDK DRM Adobe Primetime pour la protection du contenu* pour en savoir plus sur les informations d’identification supplémentaires nécessaires.

* *Certificats* de serveur clé — Vous pouvez également spécifier le certificat du serveur de licences du serveur de clés émis par Adobe. Vous pouvez spécifier le certificat du serveur de licences du serveur de clés en tant que chemin d’accès à un [!DNL .cer] fichier ou alias d’un certificat stocké sur un HSM. Cette option doit être spécifiée pour émettre des licences pour le contenu fourni avec une stratégie DRM qui requiert un de clés distantes pour les périphériques iOS.

* *Autorisations* personnalisées — Le cas échéant, spécifie les classes d’autorisation personnalisées à appeler pour chaque demande de licence. Si plusieurs autorités sont spécifiées, elles sont appelées dans l’ordre indiqué.
* *des conditionneurs* autorisés — Vous pouvez éventuellement spécifier des certificats qui identifient les entités autorisées à assembler du contenu pour ce serveur de licences. Si aucun certificat Packager n’est spécifié, le serveur délivre des licences pour le contenu compressé par un quelconque gestionnaire de package. Si le serveur reçoit une demande de licence d’un gestionnaire de package non autorisé, la demande est refusée.
* *Version* client minimale prise en charge Voir Utilisation du SDK DRM d’Adobe Primetime pour la protection du contenu.

* *Règles d’utilisation*

   * *Mise en cache* des licences — Le cas échéant, indique la durée pendant laquelle vous pouvez stocker la licence sur le client. Par défaut, la mise en cache des licences est désactivée. Si vous souhaitez activer la mise en cache des licences pendant une période limitée, vous devez définir la date de fin ou le nombre de secondes pendant lesquelles la licence doit être stockée (à partir du moment où la licence est délivrée). La définition du nombre de secondes sur 0 désactive la mise en cache des licences.

      >[!NOTE]
      >
      >Toutes les licences que le serveur pour la diffusion en flux continu protégée a délivrées comprennent une période d’expiration de 24 heures (86 400 secondes). Cette valeur s’applique implicitement en tant que limite supérieure à la date ou la durée de fin définie pour la mise en cache de la licence, avec une valeur maximale de 86 400 secondes, même si le impose des limites plus élevées.

   * *Lecture droite* — Un minimum d&#39;un droit doit être spécifié. Si vous spécifiez plusieurs droits, le client utilise alors le premier droit qui répond à toutes les exigences.

      * *Protection* de sortie — Contrôle si la sortie vers des périphériques de rendu externes doit être protégée.
      * *Restrictions* des applications AIR et SWF — Liste blanche facultative des applications SWF et AIR pouvant lire le contenu (par exemple, seules les applications spécifiées sont autorisées). Les applications SWF sont identifiées par une URL ou par le résumé du fichier SWF et le temps maximal pour permettre le téléchargement et la vérification du fichier digest.

         Pour plus d’informations sur le calcul du condensé SWF, reportez-vous à la section Calculateur *de hachage* SWF.

         Un ID d’éditeur et des  facultatifs, une version minimale et une version maximale identifient les applications AIR et iOS. Si vous ne spécifiez aucune restriction d’application, tout fichier SWF ou toute application AIR peut lire le contenu.

      * *Restrictions* de DRM et de module d&#39;exécution — Spécifie le niveau de sécurité minimal requis pour le module DRM/Runtime. Vous pouvez éventuellement inclure une liste noire des versions qui ne sont pas autorisées à lire le contenu. Les versions des modules sont identifiées par des attributs, tels que le système d’exploitation et/ou un numéro de version.

         Les restrictions des modules DRM et les restrictions des modules d’exécution prennent désormais en charge les attributs supplémentaires suivants :

         * `oemVendor`
         * `model`
         * `screenType`
         Les attributs suivants sont désormais facultatifs :

         * `osVersion`
         * `version`
      * *Exigences* en matière de capacité de l&#39;appareil — Le cas échéant, indique les capacités matérielles requises pour accéder au contenu.
      * *Exigences* en matière de détection des sauts de chasse — Le cas échéant, cette option indique que la lecture n’est pas autorisée pour les périphériques sur lesquels le jailbreak est détecté.



Voir les commentaires dans l&#39;exemple de fichier de configuration du client pour plus d&#39;informations.
