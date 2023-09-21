---
title: Questions et réponses sur les certificats
description: Questions et réponses sur les certificats
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# Questions et réponses sur les certificats {#certificates-q}

>[!NOTE]
>
>Le contenu de cette page est fourni à titre d’information uniquement. L’utilisation de cette API nécessite une licence actuelle de Adobe. Aucune utilisation non autorisée n’est autorisée.

</br>

**Q1 :** Est-il possible d’enregistrer des certificats sur iOS et Android ?

**A :** Le certificat pour iOS et Android est le même dans la configuration actuelle. Le certificat natif est utilisé pour les deux plateformes.

</br>

**Q2 :** Les mêmes certificats iOS peuvent-ils être utilisés comme certificats de Principal et de sauvegarde dans les environnements de production et d’évaluation ? Si ce n’est pas recommandé, pouvez-vous fournir une explication ?

**A :** Il n’est pas utile de configurer le même certificat que le certificat de Principal et le certificat de sauvegarde. Nous avons le concept de certificats de Principal et de sauvegarde afin de pouvoir configurer plusieurs certificats pour un programmeur en cas d’expiration ou de révocation du certificat du Principal. Disposer d’un certificat de sauvegarde donnera aux programmeurs le temps de modifier le Principal sans affecter l’environnement de publication. Vous pouvez toutefois utiliser le même ensemble de certificats de Principal et de sauvegarde pour les profils de production et d’évaluation.

</br>

**Q3 :** Un nouveau certificat est-il nécessaire pour les pages web qui utiliseront le nouveau TempPass flexible ?

**A :** Le certificat (et tout certificat en fait) est configuré au niveau de Media Company &amp; Programmer. FlexibleTempPass est un MVPD. Vous n’avez pas besoin de configurer de certificat pour celui-ci. Par conséquent, si vous intégrez un programmeur existant avec un TempPass flexible, le certificat qui est déjà configuré au niveau de Programmer/Media Company sera utilisé.
