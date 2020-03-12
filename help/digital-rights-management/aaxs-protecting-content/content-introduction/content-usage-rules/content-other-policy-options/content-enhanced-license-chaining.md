---
seo-title: Chaîne de licence améliorée
title: Chaîne de licence améliorée
uuid: d11b0631-5dfb-42b8-b7ba-cfeb1da488be
translation-type: tm+mt
source-git-commit: 53654b740b03c6a79394d30704a41186d4655237

---


# Chaîne de licence améliorée {#enhanced-license-chaining}

Permet de mettre à jour une licence à l’aide d’une licence racine parent pour la mise à jour par lots des licences.

Adobe Access 2.0 prend en charge le chaînage de licences dans lequel les licences feuille et racine sont liées à un ordinateur spécifique. Adobe Access 3.0 prend en charge le chaînage de licences amélioré, dans lequel une feuille est liée à une licence racine et où seule la licence racine est liée à un ordinateur ou à un domaine spécifique. Le chaînage de licences amélioré prend en charge l’incorporation de la licence feuille au contenu, et le client doit uniquement acquérir la licence racine auprès du serveur de licences pour pouvoir consommer le contenu protégé.

Pour activer le chaînage de licences amélioré, une clé de chiffrement racine est affectée à la stratégie. La clé de chiffrement racine est utilisée pour lier de manière cryptographique la licence feuille à la licence racine.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Le chaînage de licences amélioré est pris en charge par les clients Adobe Access versions 3.0 et ultérieures. Si un client plus âgé demande une licence pour le contenu prenant en charge le chaînage de licences amélioré, le serveur de licences peut toujours délivrer une licence à ce client à l’aide du chaînage de licences pris en charge par Adobe Access 2.0.

Exemple de cas d’utilisation : Utilisez cette option pour mettre à jour les licences liées en téléchargeant une licence racine unique. Par exemple, mettez en oeuvre   modèles de dans lesquels le contenu peut être lu tant que l’utilisateur renouvelle le le  chaque mois. L’avantage de cette approche est que les utilisateurs ne doivent acquérir qu’une seule licence pour mettre à jour toutes leurs  licences .
