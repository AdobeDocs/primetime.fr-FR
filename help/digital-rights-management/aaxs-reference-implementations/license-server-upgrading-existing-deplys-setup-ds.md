---
seo-title: Configuration d’un serveur de domaine
title: Configuration d’un serveur de domaine
uuid: b262ea86-f465-4ed1-b278-122d4dafc881
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---


# Configurer un serveur de domaine {#set-up-a-domain-server}

Pour configurer le serveur de domaine sur une installation de serveur de licences existante, effectuez les tâches suivantes :

1. Ouvrez le fichier [!DNL flashaccess-refimpl.properties] sous [!DNL tomcat/lib].

1. Sous l&#39;option `Domain CA certificate`, renseignez les détails du certificat de l&#39;autorité de certification de domaine. Ce certificat sera utilisé pour accepter les jetons de domaine.
1. Sous l&#39;option `Domain CA credential`, renseignez les détails `Domain CA credential certificate (PFX)`. Ce certificat sera utilisé pour la signature de certificats de domaine et de jetons.

1. Spécifiez la valeur de `DomainServerlURL`. Si cette valeur est NULL, l’authentification de domaine peut réussir. Cependant, lors de la jonction du domaine, il y aura une erreur de jonction de domaine.

