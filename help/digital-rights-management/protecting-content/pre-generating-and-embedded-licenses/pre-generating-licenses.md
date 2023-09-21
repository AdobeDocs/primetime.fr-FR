---
description: Si vous utilisez Adobe Primetime DRM Professional, vous pouvez prégénérer des licences et incorporer des licences dans le contenu. Cette fonctionnalité peut être combinée avec le chaînage de licences amélioré, de sorte qu’une licence Leaf est pré-générée et incorporée dans le contenu. Le client peut demander une licence Root (liée à un ordinateur ou à un domaine) à un serveur de licences. Les applications clientes peuvent également mettre en oeuvre un workflow dans lequel le périphérique s’pré-enregistre auprès d’un serveur, le serveur pré-génère les licences liées à cet appareil, et le client récupère ses licences à partir d’un serveur web HTTP simple.
title: Licences pré-générées
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 0%

---

# Licences pré-générées {#pre-generating-licenses}

Si vous utilisez Adobe Primetime DRM Professional, vous pouvez prégénérer des licences et incorporer des licences dans le contenu. Cette fonctionnalité peut être combinée avec le chaînage de licences amélioré, de sorte qu’une licence Leaf est pré-générée et incorporée dans le contenu. Le client peut demander une licence Root (liée à un ordinateur ou à un domaine) à un serveur de licences. Les applications clientes peuvent également mettre en oeuvre un workflow dans lequel le périphérique s’pré-enregistre auprès d’un serveur, le serveur pré-génère les licences liées à cet appareil, et le client récupère ses licences à partir d’un serveur web HTTP simple.

Si vous souhaitez prégénérer des licences, vous devez utiliser `com.adobe.flashaccess.sdk.license.pregen.LicenseFactory.getInstance()` pour obtenir une instance de `LicenseFactory`. Vous devez spécifier des informations d’identification du serveur de licences pour signer les licences générées par cette fabrique. Cette classe prend en charge la génération de licences Leaf sans chaînage de licence et de licences Leaf et Root avec la variable [Amélioration de la chaîne de licence](../../protecting-content/implementing-the-license-server/license-chaining/gen-enhanced-license-chaining.md).

Lorsque vous générez une licence Leaf, vous devez spécifier les métadonnées de contenu qui s’appliquent `initContentInfo()`. Si les métadonnées incluent plusieurs stratégies DRM, ou si vous souhaitez utiliser une stratégie DRM qui n’a pas été incluse dans les métadonnées, vous devez utiliser `setSelectedPolicy()` pour spécifier la stratégie DRM afin de générer une licence. Si vous utilisez une liste de mise à jour de stratégie DRM pour suivre les mises à jour des stratégies DRM, vous pouvez fournir la liste de mise à jour de stratégie DRM à la fabrique de licences avant d’initialiser les métadonnées avec `setPolicyUpdateList()`.

Lorsque vous générez une licence racine, vous devez spécifier les métadonnées de contenu comme décrit ci-dessus. Vous pouvez également générer une licence racine en appliquant une stratégie DRM ( `setSelectedPolicy()`) et une URL de serveur de licences ( `setLicenseServerURL()`) plutôt que des métadonnées.

>[!NOTE]
>
>Une URL de serveur de licences est requise même s’il n’existe pas de serveur de licences Adobe Primetime DRM à partir duquel les clients peuvent demander une licence. Dans ce cas, l’URL du serveur de licences doit spécifier une URL identifiant l’émetteur de la licence.

Si la stratégie DRM utilise le chaînage de licences amélioré, vous devez spécifier des informations d’identification du serveur de licences pour déchiffrer la clé de chiffrement racine dans la stratégie DRM ( `setRootKeyRetrievalInfo()`).

Si la stratégie DRM nécessite une licence liée à un domaine, vous devez utiliser `setDomainCAs()` pour spécifier les émetteurs de domaine à partir desquels le serveur de licences accepte les jetons de domaine. Un ou plusieurs certificats d’autorité de certification de domaine doivent être fournis pour valider le destinataire de la licence.

Si la stratégie DRM nécessite une diffusion à distance par clé pour les appareils iOS, vous devez fournir le certificat du serveur de clés en appliquant `setKeyServerCertificate()` à moins qu’une feuille liée ne soit générée.

Pour générer une licence, vous devez appeler `generateLicense()` et indiquez le type de licence (Leaf ou Root) et un ou plusieurs certificats de destinataire. Le certificat du destinataire représente un certificat de machine ou de domaine, selon les exigences spécifiées dans la stratégie DRM. Si vous générez une feuille liée, aucun destinataire n’est requis. Une fois la licence générée, vous pouvez remplacer les règles d’utilisation qui ont été spécifiées dans la stratégie DRM. Enfin, vous devez appeler `signLicense()` pour signer la licence et obtenir une instance de `PreGeneratedLicense`. La licence peut maintenant être enregistrée (utilisez `getBytes()` pour récupérer la licence sérialisée ou incorporée dans du contenu chiffré.

Voir [Incorporation de licences](../../protecting-content/pre-generating-and-embedded-licenses/embedding-licenses.md).

Voir `com.adobe.flashaccess.samples.licensegen.GenerateLicense` dans le répertoire des outils de ligne de commande d’implémentation de référence &quot;samples&quot; pour obtenir un exemple de code sur la démonstration des licences prégénérées.
