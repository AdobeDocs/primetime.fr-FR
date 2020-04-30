---
seo-title: A propos des fichiers CRL
title: A propos des fichiers CRL
uuid: 672c3ca0-5c5d-4ec7-83b1-f0f8e34c8d09
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# A propos des fichiers CRL {#about-crl-files}

Pour fonctionner correctement, les serveurs d’individualisation et de licence doivent disposer de plusieurs fichiers CRL (Certificate Revocation Liste) mis en cache sur le disque sur le serveur d’applications en cours d’exécution (Tomcat, par exemple). Les nouveaux fichiers CRL doivent être téléchargés et mis en cache sur le disque sur une base régulièrement planifiée. Si la période de validité des fichiers CRL sur le disque est interrompue, le serveur d’individualisation refuse d’individualiser les clients et le serveur de licences refuse d’émettre des licences.

Les listes CRL mises en cache sur le disque doivent avoir des noms de fichier correspondant aux URL correspondantes. Les caractères spéciaux tels que les barres obliques &quot;:&quot; et &quot;/&quot; sont convertis en traits de soulignement &quot;_&quot; dans les noms de fichier.

Voici une liste de listes CRL hébergées en externe qui sont utilisées par les serveurs d’individualisation et de licence :

* **CRL intermédiaire :**

   * URL : [!DNL <ht<span></span>tps://crl2.adobe.com/Adobe/FlashAccessIntermediateCA.crl>]
   * Fichier : [!DNL http___crl2.adobe.com_Adobe_FlashAccessIntermediateCA.crl]
   * Validité : Bon pour environ 12 mois après la création

* **CRL racine :**

   * URL : [!DNL <ht<span></span>tps://crl2.adobe.com/Adobe/FlashAccessRootCA.crl>]
   * Fichier : [!DNL http___crl2.adobe.com_Adobe_FlashAccessRootCA.crl]
   * Validité : Bon pour environ 5 ans après la création

* **Dernière CRL :**

   * URL : [!DNL <ht<span></span>tps://crl3.adobe.com/AdobeSystemsIncorporatedFlashAccessRuntime/LatestCRL.crl>]
   * Fichier : [!DNL http___crl3.adobe.com_AdobeSystemsIncorporatedFlashAccessRuntime_LatestCRL.crl]
   * Validité : Bon pour environ 3 mois après la création

Les listes CRL hébergées en externe et utilisées uniquement par les serveurs de licence sont les suivantes :

* URL : [!DNL <ht<span></span>tps://crl2.adobe.com/Adobe/FlashAccessIndividualizationCA.crl>]
* Fichier : [!DNL http___crl2.adobe.com_Adobe_FlashAccessIndividualizationCA.crl]
* Validité : Bon pour environ 3 mois après la création

* URL : [!DNL <ht<span></span>tps://individualization-crl.primetime.adobe.com/FlashAccessIndividualizationCA.crl>]
* Fichier : [!DNL http___individualization-crl.primetime.adobe.com_FlashAccessIndividualizationCA.crl]
* Validité : Bon pour environ 3 mois après la création

* URL : [!DNL <ht<span></span>tps://individualization-crl.s3-website-us-east-1.amazonaws.com/FlashAccessIndividualizationCA.crl]>
* Fichier : [!DNL http___individualization-crl.s3-website-us-east-1.amazonaws.com_FlashAccessIndividualizationCA.crl]
* Validité : Bon pour environ 3 mois après la création

Outre les listes CRL susmentionnées, vous devez créer et gérer une liste CRL supplémentaire. Il s’agit de la liste de révocation des certificats de l’autorité de certification d’individualisation, comme indiqué dans la section [Créer une liste de révocation des certificats d’autorité de certification d’individualisation](../../../on-premises-i15n-server/server-configuration-section/server-properties/create-i15n-ca-crl.md) de ce document.

Les listes CRL doivent être mises à jour 45 jours avant leur expiration. Cela devrait vous donner le temps d’acquérir et d’installer des listes CRL nouvellement générées à partir d’Internet. Vous devez veiller à mettre à jour les fichiers CRL avant qu’ils ne soient expirés.
