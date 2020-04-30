---
seo-title: Chaîne améliorée de licence
title: Chaîne améliorée de licence
uuid: 5e4e825a-de84-4ab2-a652-02cc03153957
translation-type: tm+mt
source-git-commit: 53654b740b03c6a79394d30704a41186d4655237

---


# Chaîne améliorée de licence {#enhanced-license-chaining}

Vous pouvez utiliser le chaînage de licences amélioré pour mettre à jour une licence en utilisant une licence racine parente pour la mise à jour par lots des licences.

Primetime DRM 2.0 prend en charge le chaînage de licences dans lequel les licences feuille et racine sont liées à un ordinateur spécifique. Primetime DRM 3.0 et versions ultérieures prend en charge le chaînage de licences amélioré, dans lequel une feuille est liée à une licence racine, et seule la licence racine est liée à un ordinateur ou domaine spécifique. Le chaînage de licences amélioré prend en charge l’incorporation d’une licence feuille au contenu, et le client doit uniquement acquérir la licence racine auprès du serveur de licences pour pouvoir consommer le contenu protégé.

Si vous souhaitez activer le chaînage amélioré des licences, vous devez alors affecter une clé de chiffrement racine à une stratégie DRM Primetime. La clé de chiffrement racine est utilisée pour lier de façon cryptographique la licence feuille à la licence racine.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Le chaînage de licences amélioré est pris en charge par les clients DRM de Primetime version 3.0 ou ultérieure. Si un client plus âgé demande une licence pour un contenu prenant en charge le chaînage de licences amélioré, le serveur de licences peut toujours émettre une licence pour ce client en utilisant le chaînage de licences qui est pris en charge par Primetime DRM 2.0.

Exemple de cas d’utilisation : Utilisez cette option pour mettre à jour les licences liées en téléchargeant une licence racine unique. Par exemple, implémentez des modèles d’abonnement dans lesquels le contenu peut être lu tant que l’utilisateur renouvelle l’abonnement sur une base mensuelle. L’avantage de cette approche est que les utilisateurs n’ont qu’à acquérir une seule licence pour mettre à jour toutes leurs licences d’abonnement.
