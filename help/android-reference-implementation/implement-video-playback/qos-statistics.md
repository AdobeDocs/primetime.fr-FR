---
description: Vous pouvez configurer votre lecteur pour lire les statistiques de lecture et de périphérique à partir de QoSProvider aussi souvent que nécessaire.
seo-description: Vous pouvez configurer votre lecteur pour lire les statistiques de lecture et de périphérique à partir de QoSProvider aussi souvent que nécessaire.
seo-title: Affichage des statistiques de lecture de la qualité de service et des périphériques
title: Affichage des statistiques de lecture de la qualité de service et des périphériques
uuid: 8fc45a2f-03d4-4fa0-979b-eb816419c4f7
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Affichage des statistiques de lecture de la qualité de service et des périphériques {#display-qos-playback-and-device-statistics}

Vous pouvez configurer votre lecteur pour lire les statistiques de lecture et de périphérique à partir de QoSProvider aussi souvent que nécessaire.

La `QoSProvider` classe fournit diverses statistiques, notamment la fréquence d’images, le débit  du, le temps total passé dans la mise en mémoire tampon, le nombre de tentatives de mise en mémoire tampon, le temps nécessaire pour obtenir le premier octet à partir du premier fragment vidéo, le temps nécessaire pour effectuer le rendu de la première image, la longueur actuellement mise en mémoire tampon et le temps de mise en mémoire tampon.

L’implémentation de référence fournit une `QoSManager` classe dans laquelle vous pouvez activer l’affichage de l’incrustation QoS. Vous pouvez également activer la visibilité de la qualité de service dans l’interface utilisateur des paramètres :

![](assets/qos-configuration.jpg)

Il `QoSManager` effectue le suivi des statistiques de la qualité de service en obtenant des informations sur le périphérique, en les associant au lecteur multimédia et en les mettant à jour avec les dernières informations de qualité de service.

**Activation ou désactivation du de statistiques QoS**

1. Créez un  QosManager ou activez le QoS à l’aide de ManagerFactory.

   * Pour créer une instance de QosManager :
      * Cette application doit utiliser la fonction de flux de travail publicitaire
   QoSManager qosManager = new QosManagerOn();

   * Pour utiliser ManagerFactory afin d’activer l’affichage des statistiques de qualité de service :
   qosManager = ManagerFactory.getQosManager()
   <b>true</b>, config, mediaPlayer);

   >[!NOTE]
   >
   >La modification de la valeur booléenne `false` désactive les  QoS.

2. Ajouter  :

   `qosManager.addEventListener(qosManagerEventListener);`

3. Créez le fournisseur QoS et joignez-le au lecteur   contexte du :

   `qosManager.createQOSProvider(getActivity());`

   >[!NOTE]
   >
   >Lorsque le lecteur   sera détruit, veillez à appeler [qosManager.destroyQOSProvider](https://help.adobe.com/en_US/primetime/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.html#destroyQOSProvider()) pour nettoyer le fournisseur QOS en le détachant du lecteur multimédia.

**Documentation sur les API connexes**

* [Classe QosManager](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.html)
* [Classe QosManagerOn](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManagerOn.html)
* [QosManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.QosManagerEventListener.html)
* [QosItem](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.QosItem.html)
