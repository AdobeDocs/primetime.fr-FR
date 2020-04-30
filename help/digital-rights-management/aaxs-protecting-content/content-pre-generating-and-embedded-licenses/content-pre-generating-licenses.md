---
seo-title: Licences pré-générées
title: Licences pré-générées
uuid: 31430753-11f1-4ce5-b402-cf4279119a05
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Licences pré-générées{#pre-generating-licenses}

Pour prégénérer des licences, utilisez `com.adobe.flashaccess.sdk.license.pregen.LicenseFactory.getInstance()` pour obtenir une instance de `LicenseFactory`. Les informations d’identification du serveur de licences doivent être spécifiées pour pouvoir signer les licences générées par cette fabrique. Cette classe prend en charge la génération de licences Leaf sans chaînage de licences et de licences Leaf et Root avec le chaînage de licences [Enhanced](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-other-policy-options/content-enhanced-license-chaining.md).

Lors de la création d’une licence Feuille, les métadonnées de contenu doivent être spécifiées à l’aide de `initContentInfo()`. Si les métadonnées comportent plusieurs stratégies ou si vous souhaitez utiliser une stratégie qui ne se trouvait pas dans les métadonnées, utilisez `setSelectedPolicy()` pour spécifier la stratégie à utiliser pour générer la licence. Si vous utilisez une Liste de mise à jour de stratégie pour effectuer le suivi des mises à jour des stratégies, vous pouvez fournir la Liste de mise à jour de stratégie à la fabrique de licences avant d’initialiser les métadonnées à l’aide de `setPolicyUpdateList()`.

Lors de la génération d’une licence racine, les métadonnées de contenu peuvent être spécifiées comme décrit ci-dessus. Vous pouvez également générer une licence racine à l’aide d’une stratégie ( `setSelectedPolicy()`) et d’une URL de serveur de licences ( `setLicenseServerURL()`) au lieu des métadonnées.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Une URL de serveur de licences est requise même s’il n’existe pas de serveur de licences Adobe Access à partir duquel les clients peuvent demander une licence. Dans ce cas, l’URL du serveur de licences doit spécifier une URL identifiant l’émetteur de la licence.

Si la stratégie utilise le chaînage de licences amélioré, les informations d’identification du serveur de licences doivent être spécifiées afin de déchiffrer la clé de chiffrement racine dans la stratégie ( `setRootKeyRetrievalInfo()`).

Si la stratégie requiert une licence liée au domaine, utilisez `setDomainCAs()` pour spécifier les émetteurs de domaines à partir desquels le serveur de licences acceptera les jetons de domaine. Un ou plusieurs certificats d’autorité de certification de domaine doivent être fournis pour valider le destinataire de licence.

Si la stratégie requiert une diffusion de clés distantes pour les périphériques iOS, le certificat du serveur de clés doit être fourni à l’aide `setKeyServerCertificate()`, sauf si une feuille chaînée est générée.

Pour générer une licence, appelez `generateLicense()` et spécifiez le type de licence (Feuille ou Racine) et un ou plusieurs certificats destinataires. Le certificat du destinataire sera soit un certificat d’ordinateur, soit un certificat de domaine, selon les exigences spécifiées dans la stratégie. Si vous générez une feuille chaînée, aucun destinataire n’est nécessaire. Une fois la licence générée, il est possible de remplacer les règles d’utilisation spécifiées dans la stratégie. Enfin, appelez `signLicense()` pour signer la licence et obtenir une instance de `PreGeneratedLicense`. La licence peut désormais être enregistrée dans un fichier (à utiliser `getBytes()` pour récupérer la licence sérialisée) ou incorporée dans du contenu chiffré. Voir [Incorporation de licences](../../aaxs-protecting-content/content-pre-generating-and-embedded-licenses/content-embedding-licenses.md).

Pour obtenir un exemple de code démontrant les licences prégénérées, voir `com.adobe.flashaccess.samples.licensegen.GenerateLicense` dans le répertoire &quot;samples&quot; des outils de ligne de commande de mise en oeuvre de référence.
