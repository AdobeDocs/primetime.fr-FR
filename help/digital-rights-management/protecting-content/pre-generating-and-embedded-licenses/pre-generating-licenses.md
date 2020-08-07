---
description: Si vous utilisez Adobe Primetime DRM Professional, vous pouvez prégénérer des licences et incorporer des licences dans le contenu. Cette fonctionnalité peut être combinée avec le chaînage de licences amélioré, de sorte qu’une licence Leaf soit prégénérée et incorporée dans le contenu, et que le client puisse demander une licence Root (liée à un ordinateur ou un domaine) à un serveur de licences. Les applications clientes peuvent également mettre en oeuvre un processus dans lequel le périphérique s’enregistre préalablement auprès d’un serveur, où le serveur génère automatiquement des licences liées à ce périphérique, et où le client récupère ses licences auprès d’un serveur Web HTTP simple.
seo-description: Si vous utilisez Adobe Primetime DRM Professional, vous pouvez prégénérer des licences et incorporer des licences dans le contenu. Cette fonctionnalité peut être combinée avec le chaînage de licences amélioré, de sorte qu’une licence Leaf soit prégénérée et incorporée dans le contenu, et que le client puisse demander une licence Root (liée à un ordinateur ou un domaine) à un serveur de licences. Les applications clientes peuvent également mettre en oeuvre un processus dans lequel le périphérique s’enregistre préalablement auprès d’un serveur, où le serveur génère automatiquement des licences liées à ce périphérique, et où le client récupère ses licences auprès d’un serveur Web HTTP simple.
seo-title: Licences pré-générées
title: Licences pré-générées
uuid: aa7d5038-5a9b-40a2-a240-266622158b43
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 0%

---


# Licences pré-générées {#pre-generating-licenses}

Si vous utilisez Adobe Primetime DRM Professional, vous pouvez prégénérer des licences et incorporer des licences dans le contenu. Cette fonctionnalité peut être combinée avec le chaînage de licences amélioré, de sorte qu’une licence Leaf soit prégénérée et incorporée dans le contenu, et que le client puisse demander une licence Root (liée à un ordinateur ou un domaine) à un serveur de licences. Les applications clientes peuvent également mettre en oeuvre un processus dans lequel le périphérique s’enregistre préalablement auprès d’un serveur, où le serveur génère automatiquement des licences liées à ce périphérique, et où le client récupère ses licences auprès d’un serveur Web HTTP simple.

Si vous souhaitez prégénérer des licences, vous devez utiliser `com.adobe.flashaccess.sdk.license.pregen.LicenseFactory.getInstance()` pour obtenir une instance de `LicenseFactory`. Vous devez spécifier des informations d’identification de serveur de licences pour signer les licences générées par cette fabrique. Cette classe prend en charge la génération de licences Leaf sans chaînage de licences et de licences Leaf et Root avec le chaînage de licences [Enhanced](../../protecting-content/implementing-the-license-server/license-chaining/gen-enhanced-license-chaining.md).

Lorsque vous générez une licence Feuille, vous devez spécifier les métadonnées de contenu qui s’appliquent `initContentInfo()`. Si les métadonnées comportent plusieurs stratégies DRM ou si vous souhaitez utiliser une stratégie DRM qui n&#39;a pas été incluse dans les métadonnées, vous devez utiliser `setSelectedPolicy()` pour spécifier la stratégie DRM pour générer une licence. Si vous utilisez une Liste de mise à jour de stratégie DRM pour effectuer le suivi des mises à jour des stratégies DRM, vous pouvez fournir la Liste de mise à jour de stratégie DRM à la fabrique de licences avant d&#39;initialiser les métadonnées avec `setPolicyUpdateList()`.

Lorsque vous générez une licence racine, vous devez spécifier les métadonnées de contenu comme décrit ci-dessus. Vous pouvez également générer une licence racine en appliquant une stratégie DRM ( `setSelectedPolicy()`) et une URL de serveur de licences ( `setLicenseServerURL()`) plutôt que des métadonnées.

>[!NOTE]
>
>Une URL de serveur de licences est requise même s’il n’existe aucun serveur de licences DRM Adobe Primetime à partir duquel les clients peuvent demander une licence. Dans ce cas, l’URL du serveur de licences doit spécifier une URL identifiant l’émetteur de la licence.

Si la stratégie DRM utilise le chaînage de licences amélioré, vous devez spécifier des informations d’identification de serveur de licences pour déchiffrer la clé de chiffrement racine dans la stratégie DRM ( `setRootKeyRetrievalInfo()`).

Si la stratégie DRM requiert une licence liée au domaine, vous devez utiliser `setDomainCAs()` pour spécifier les émetteurs de domaines à partir desquels le serveur de licences accepte les jetons de domaine. Un ou plusieurs certificats d’autorité de certification de domaine doivent être fournis pour valider le destinataire de licence.

Si la stratégie DRM requiert une diffusion de clé à distance pour les périphériques iOS, vous devez fournir le certificat du serveur de clés en appliquant `setKeyServerCertificate()` une demande à moins qu’une feuille chaînée ne soit générée.

Si vous souhaitez générer une licence, vous devez appeler `generateLicense()` et spécifier le type de licence (Feuille ou Racine) et un ou plusieurs certificats destinataires. Le certificat du destinataire représente un certificat d&#39;ordinateur ou un certificat de domaine, selon les exigences spécifiées dans la stratégie DRM. Si vous générez une feuille chaînée, aucun destinataire n’est nécessaire. Une fois la licence générée, vous pouvez remplacer les règles d’utilisation spécifiées dans la stratégie DRM. Enfin, vous devez appeler `signLicense()` pour signer la licence et obtenir une instance de `PreGeneratedLicense`. La licence peut désormais être enregistrée (à utiliser `getBytes()` pour récupérer la licence sérialisée ou incorporée dans du contenu chiffré).

Voir [Incorporation de licences](../../protecting-content/pre-generating-and-embedded-licenses/embedding-licenses.md).

Voir `com.adobe.flashaccess.samples.licensegen.GenerateLicense` dans le répertoire &quot;samples&quot; des outils de ligne de commande d’implémentation de référence pour obtenir un exemple de code sur la façon de démontrer les licences pré-générées.
