---
title: Licences pré-générées
description: Licences pré-générées
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# Licences pré-générées{#pre-generating-licenses}

Pour prégénérer des licences, utilisez `com.adobe.flashaccess.sdk.license.pregen.LicenseFactory.getInstance()` pour obtenir une instance de `LicenseFactory`. Les informations d’identification du serveur de licences doivent être spécifiées pour signer les licences générées par cette fabrique. Cette classe prend en charge la génération de licences Leaf sans chaînage de licence et de licences Leaf et Root avec la variable [Amélioration de la chaîne de licence](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-other-policy-options/content-enhanced-license-chaining.md).

Lors de la génération d’une licence Leaf, les métadonnées de contenu doivent être spécifiées à l’aide de `initContentInfo()`. Si les métadonnées contiennent plusieurs stratégies, ou si vous souhaitez utiliser une stratégie qui ne figurait pas dans les métadonnées, utilisez `setSelectedPolicy()` pour spécifier la stratégie à utiliser pour générer la licence. Si vous utilisez une liste de mise à jour de stratégie pour suivre les mises à jour des stratégies, vous pouvez fournir la liste de mise à jour de stratégie à la fabrique de licences avant d’initialiser les métadonnées à l’aide de `setPolicyUpdateList()`.

Lors de la génération d’une licence racine, les métadonnées de contenu peuvent être spécifiées comme décrit ci-dessus. Vous pouvez également générer une licence racine à l’aide d’une stratégie ( `setSelectedPolicy()`) et l’URL du serveur de licences ( `setLicenseServerURL()`) au lieu des métadonnées.

>[!NOTE]
>
>Une URL de serveur de licences est requise même s’il n’existe pas de serveur de licences d’accès Adobe à partir duquel les clients peuvent demander une licence. Dans ce cas, l’URL du serveur de licences doit spécifier une URL identifiant l’émetteur de la licence.

Si la stratégie utilise le chaînage de licences amélioré, des informations d’identification du serveur de licences doivent être spécifiées afin de déchiffrer la clé de chiffrement racine dans la stratégie ( `setRootKeyRetrievalInfo()`).

Si la stratégie nécessite une licence liée à un domaine, utilisez `setDomainCAs()` pour spécifier les émetteurs de domaine à partir desquels le serveur de licences acceptera les jetons de domaine. Un ou plusieurs certificats d’autorité de certification de domaine doivent être fournis pour valider le destinataire de la licence.

Si la stratégie nécessite une diffusion à distance par clé pour les appareils iOS, le certificat du serveur de clé doit être fourni à l’aide de la fonction `setKeyServerCertificate()`, sauf si une feuille liée est générée.

Pour générer une licence, appelez `generateLicense()` et indiquez le type de licence (Leaf ou Root) et un ou plusieurs certificats de destinataire. Le certificat du destinataire sera soit un certificat de machine, soit un certificat de domaine, selon les exigences spécifiées dans la stratégie. Si vous générez une feuille enchaînée, aucun destinataire n’est requis. Une fois la licence générée, il est possible de remplacer les règles d’utilisation spécifiées dans la stratégie. Enfin, appelez `signLicense()` pour signer la licence et obtenir une instance de `PreGeneratedLicense`. La licence peut désormais être enregistrée dans un fichier (utilisez `getBytes()` pour récupérer la licence sérialisée) ou incorporée dans du contenu chiffré. Voir [Incorporation de licences](../../aaxs-protecting-content/content-pre-generating-and-embedded-licenses/content-embedding-licenses.md).

Pour obtenir un exemple de code présentant les licences prégénérées, reportez-vous à la section `com.adobe.flashaccess.samples.licensegen.GenerateLicense` dans le répertoire &quot;Exemples&quot; des outils de ligne de commande de mise en oeuvre de référence.
