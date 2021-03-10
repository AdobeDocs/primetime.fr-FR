---
description: Vous pouvez configurer votre lecteur pour lire les statistiques de lecture et de périphérique à partir de QoSProvider aussi souvent que nécessaire.
title: Affichage des statistiques de lecture de la qualité de service et des périphériques
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---


# Afficher les statistiques de lecture et de périphérique de la qualité de service {#display-qos-playback-and-device-statistics}

Vous pouvez configurer votre lecteur pour lire les statistiques de lecture et de périphérique à partir de QoSProvider aussi souvent que nécessaire.

La classe `QoSProvider` fournit diverses statistiques, notamment la fréquence d’images, le débit profil, le temps total passé en mémoire tampon, le nombre de tentatives de mise en mémoire tampon, le temps nécessaire pour obtenir le premier octet à partir du premier fragment vidéo, le temps nécessaire pour effectuer le rendu de la première image, la longueur actuellement mise en mémoire tampon et le temps de mise en mémoire tampon.

L’implémentation de référence fournit une classe `QoSManager` dans laquelle vous pouvez activer l’affichage de l’incrustation QoS. Vous pouvez également activer la visibilité de la qualité de service dans l’interface utilisateur des paramètres :

![](assets/qos-configuration.jpg)

`QoSManager` effectue le suivi des statistiques de la qualité de service en obtenant des informations sur le périphérique, en les associant au lecteur multimédia et en les mettant à jour avec les dernières informations de la qualité de service.

**Activation ou désactivation du rapports de statistiques QoS**

1. Créez un QosManager ou activez le rapports QoS à l’aide de ManagerFactory.

   * Pour créer un QosManager :
      * Cette application doit utiliser la fonction de processus publicitaire

   QoSManager qosManager = new QosManagerOn();

   * Pour utiliser ManagerFactory pour activer l’affichage des statistiques de qualité de service :

   qosManager = ManagerFactory.getQosManager(
   <b>true</b>, config, mediaPlayer);

   >[!NOTE]
   >
   >La modification de la valeur booléenne `false` désactive le rapports QoS.

2. Ajouter les auditeurs de événement :

   `qosManager.addEventListener(qosManagerEventListener);`

3. Créez le fournisseur QoS et joignez-le au contexte d’activité du lecteur :

   `qosManager.createQOSProvider(getActivity());`

   >[!NOTE]
   >
   >Lorsque l&#39;activité du lecteur sera détruite, veillez à appeler [qosManager.destroyQOSProvider](https://help.adobe.com/en_US/primetime/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.html#destroyQOSProvider()) pour nettoyer le fournisseur QOS en le détachant du lecteur multimédia.

**Documentation sur les API connexes**

* [Classe QosManager](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.html)
* [Classe QosManagerOn](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManagerOn.html)
* [QuosManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.QosManagerEventListener.html)
* [QosItem](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.QosItem.html)
