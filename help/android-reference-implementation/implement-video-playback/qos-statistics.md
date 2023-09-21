---
description: Vous pouvez configurer votre lecteur pour lire les statistiques de lecture et d’appareil de QoSProvider aussi souvent que nécessaire.
title: Affichage des statistiques de lecture QoS et d’appareil
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# Affichage des statistiques de lecture QoS et d’appareil {#display-qos-playback-and-device-statistics}

Vous pouvez configurer votre lecteur pour lire les statistiques de lecture et d’appareil de QoSProvider aussi souvent que nécessaire.

La variable `QoSProvider` fournit diverses statistiques, notamment la fréquence d’image, la vitesse en bits du profil, la durée totale passée en mémoire tampon, le nombre de tentatives de mise en mémoire tampon, le temps nécessaire pour obtenir le premier octet du premier fragment vidéo, le temps nécessaire au rendu de la première image, la durée actuellement mise en mémoire tampon et le temps de mise en mémoire tampon.

L’implémentation de référence fournit une `QoSManager` où vous pouvez activer l’affichage de la superposition QoS. Vous pouvez également activer la visibilité QoS dans l’interface utilisateur de Paramètres :

![](assets/qos-configuration.jpg)

La variable `QoSManager` effectue le suivi des statistiques QoS en obtenant des informations sur les appareils, en les joignant au lecteur multimédia et en les mettant à jour avec les dernières informations QoS.

**Activation ou désactivation du reporting de statistiques QoS**

1. Créez un QosManager ou activez la création de rapports QoS à l’aide de ManagerFactory.

   * Pour créer un QosManager :
      * Cette application doit utiliser la fonction de workflow publicitaire.

   QoSManager qosManager = new QosManagerOn();

   * Pour utiliser ManagerFactory afin d’activer l’affichage des statistiques QoS :

   qosManager = ManagerFactory.getQosManager(
   <b>true</b>, config, mediaPlayer);

   >[!NOTE]
   >
   >Remplacer la valeur booléenne par `false` désactive les rapports QoS.

2. Ajoutez des écouteurs d’événement :

   `qosManager.addEventListener(qosManagerEventListener);`

3. Créez le fournisseur QoS et joignez-le au contexte d’activité du lecteur :

   `qosManager.createQOSProvider(getActivity());`

   >[!NOTE]
   >
   >Lorsque l’activité du lecteur va être détruite, veillez à appeler [qosManager.destructionQOSProvider](https://help.adobe.com/en_US/primetime/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.html#destroyQOSProvider()) pour nettoyer le fournisseur QOS en le détachant du lecteur multimédia.

**Documentation sur les API connexe**

* [Classe QosManager](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.html)
* [Classe QosManagerOn](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManagerOn.html)
* [QosManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.QosManagerEventListener.html)
* [QosItem](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.QosItem.html)
