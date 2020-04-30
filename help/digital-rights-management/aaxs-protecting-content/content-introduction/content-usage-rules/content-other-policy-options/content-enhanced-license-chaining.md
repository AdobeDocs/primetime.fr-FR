---
seo-title: Chaîne améliorée de licence
title: Chaîne améliorée de licence
uuid: d11b0631-5dfb-42b8-b7ba-cfeb1da488be
translation-type: tm+mt
source-git-commit: 53654b740b03c6a79394d30704a41186d4655237

---


# Chaîne améliorée de licence {#enhanced-license-chaining}

Permet la mise à jour d’une licence à l’aide d’une licence racine parent pour la mise à jour par lots des licences.

Adobe Access 2.0 prend en charge le chaînage des licences dans lequel les licences feuille et racine sont liées à un ordinateur spécifique. Adobe Access 3.0 prend en charge le chaînage de licences amélioré, dans lequel une feuille est liée à une licence racine et seule la licence racine est liée à un ordinateur ou domaine spécifique. Le chaînage de licences amélioré prend en charge l’intégration de la licence feuille au contenu, et le client doit uniquement acquérir la licence racine auprès du serveur de licences afin de consommer le contenu protégé.

Pour activer la chaîne de licence améliorée, une clé de chiffrement racine est affectée à la stratégie. La clé de chiffrement racine est utilisée pour lier de façon cryptographique la licence feuille à la licence racine.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Le chaînage de licences amélioré est pris en charge par les clients Adobe Access versions 3.0 et ultérieures. Si un client plus âgé demande une licence pour un contenu prenant en charge le chaînage de licences amélioré, le serveur de licences peut toujours émettre une licence pour ce client à l’aide du chaînage de licences pris en charge par Adobe Access 2.0.

Exemple de cas d’utilisation : Utilisez cette option pour mettre à jour les licences liées en téléchargeant une licence racine unique. Par exemple, implémentez des modèles d’abonnement dans lesquels le contenu peut être lu tant que l’utilisateur renouvelle l’abonnement sur une base mensuelle. L’avantage de cette approche est que les utilisateurs ne doivent acquérir qu’une seule licence pour mettre à jour toutes leurs licences d’abonnement.
