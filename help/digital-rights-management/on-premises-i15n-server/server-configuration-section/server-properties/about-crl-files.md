---
title: À propos des fichiers CRL
description: À propos des fichiers CRL
copied-description: true
exl-id: 126a323d-9433-4a1e-a617-2d3bbf717cce
source-git-commit: 6a00df9c061da43f6efa49d927873db629568597
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# À propos des fichiers CRL {#about-crl-files}

Pour fonctionner correctement, les serveurs d’individualisation et de licence doivent disposer de plusieurs fichiers de liste de révocation des certificats (CRL) mis en cache sur le disque sur le serveur d’applications en cours d’exécution (Tomcat, par exemple). Les nouveaux fichiers CRL doivent être téléchargés et mis en cache sur le disque de manière régulière. Si la période de validité des fichiers CRL sur le disque est annulée, le serveur d’individualisation refuse d’individualiser les clients et le serveur de licences refuse d’émettre des licences.

Les CRL mises en cache sur le disque doivent avoir des noms de fichier correspondant aux URL correspondantes. Les caractères spéciaux tels que les barres obliques &#39;:&#39; et &#39;/&#39; sont convertis en traits de soulignement &#39;_&#39; dans les noms de fichier.

Voici une liste des listes CRL hébergées en externe qui sont utilisées par les serveurs d’individualisation et de licence :

* **CRL intermédiaire :**

   * URL : [!DNL <ht<span></span>tps://crl2.adobe.com/Adobe/FlashAccessIntermediateCA.crl>]
   * Fichier : [!DNL http___crl2.adobe.com_Adobe_FlashAccessIntermediateCA.crl]
   * Validité : Bon pour environ 12 mois à partir de la création

* **CRL racine :**

   * URL : [!DNL <ht<span></span>tps://crl2.adobe.com/Adobe/FlashAccessRootCA.crl>]
   * Fichier : [!DNL http___crl2.adobe.com_Adobe_FlashAccessRootCA.crl]
   * Validité : Bon pour environ 5 ans à partir de la création

* **Dernière CRL :**

   * URL : [!DNL <ht<span></span>tps://crl3.adobe.com/AdobeSystemsIncorporatedFlashAccessRuntime/LatestCRL.crl>]
   * Fichier : [!DNL http___crl3.adobe.com_AdobeSystemsIncorporatedFlashAccessRuntime_LatestCRL.crl]
   * Validité : Bon pour environ 3 mois à partir de la création

Pour en savoir plus sur les listes CRL hébergées en externe qui peuvent être utilisées par les serveurs de licences, contactez le support Adobe.

<!---

Commenting out because of a security vulnerability reported in Jira PSIRT-20689. 

The following are externally hosted CRLs that are used only by the License Servers:

* URL: `https://crl2.adobe.com/Adobe/FlashAccessIndividualizationCA.crl`

* File: `http___crl2.adobe.com_Adobe_FlashAccessIndividualizationCA.crl`

* Validity: Good for approximately 3 months from creation

* URL: `https://individualization-crl.primetime.adobe.com/FlashAccessIndividualizationCA.crl`

* File: `http___individualization-crl.primetime.adobe.com_FlashAccessIndividualizationCA.crl`

* Validity: Good for approximately 3 months from creation

* URL: `https://individualization-crl.s3-website-us-east-1.amazonaws.com/FlashAccessIndividualizationCA.crl`

* File: `http___individualization-crl.s3-website-us-east-1.amazonaws.com_FlashAccessIndividualizationCA.crl`

* Validity: Good for approximately 3 months from creation

--->

Outre les listes CRL hébergées en externe, vous pouvez créer et gérer une liste CRL supplémentaire. Il s’agit de la liste de révocation des certificats de l’autorité de certification de l’individualisation, comme indiqué dans la section [Création d’une liste CRL d’autorité de certification d’individualisation](../../../on-premises-i15n-server/server-configuration-section/server-properties/create-i15n-ca-crl.md) de ce document.

Les listes CRL doivent être mises à jour 45 jours avant leur expiration. Cela devrait vous donner le temps d’acquérir et d’installer des listes CRL nouvellement générées à partir d’Internet. Vous devez veiller à mettre à jour les fichiers CRL avant leur expiration.
