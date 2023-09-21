---
title: Authentification Adobe Primetime et nouveau modèle d’autorisations Android 6 "Marshmallow"
description: Authentification Adobe Primetime et nouveau modèle d’autorisations Android 6 "Marshmallow"
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# Authentification Adobe Primetime et nouveau modèle d’autorisations Android 6 &quot;Marshmallow&quot; {#adobe-primetime-authentication-and-the-android-6-marshmallow-new-permissions-model}

>[!NOTE]
>
>Le contenu de cette page est fourni à titre d’information uniquement. L’utilisation de cette API nécessite une licence actuelle de Adobe. Aucune utilisation non autorisée n’est autorisée.

</br>

La nouvelle version d’Android 6 Marshmallow introduit quelques mises à jour du modèle des autorisations, ce qui peut avoir une incidence sur le comportement des applications qui utilisent le SDK d’authentification Adobe Primetime version 1.8 et antérieure.

La nouvelle fonctionnalité Android OS offre [contrôle granulaire sur les autorisations dont les applications ont besoin au moment de l’installation et de l’exécution.](https://developer.android.com/about/versions/marshmallow/android-6.0-changes.html).

>[!IMPORTANT]
>
>Les modifications décrites ci-dessous seront **concerne uniquement les applications développées spécifiquement pour Android 6.0.** (targetSdkVersion=23). Elles n’affectent pas les anciennes applications déjà installées sur l’appareil de l’utilisateur lors de la mise à niveau vers Android 6.0.


Plus précisément, pour les applications développées dans Android Studio à l’aide de [Niveau d’API 23](http://developer.android.com/sdk/api_diff/23/changes.html) et qui utilisent le SDK d’authentification Adobe Primetime, le développeur devra écrire du code personnalisé (voir le fragment de code ci-dessous). [pour déclencher la boîte de dialogue d’autorisation/de refus](https://developer.android.com/training/permissions/requesting.html).

Voici l’extrait de code utilisé pour demander l’accès en écriture au stockage externe de l’appareil :

```java
// Here, thisActivity is the current activity
if (ContextCompat.checkSelfPermission(thisActivity,
                Manifest.permission.WRITE_EXTERNAL_STORAGE)
        != PackageManager.WRITE_EXTERNAL_STORAGE) {

    // Should we show an explanation?
    if (ActivityCompat.shouldShowRequestPermissionRationale(thisActivity,
            Manifest.permission.WRITE_EXTERNAL_STORAGE)) {

        // Show an expanation to the user *asynchronously* -- don't block
        // this thread waiting for the user's response! After the user
        // sees the explanation, try again to request the permission.

    } else {

        // No explanation needed, we can request the permission.

        ActivityCompat.requestPermissions(thisActivity,
                new String[]{Manifest.permission.WRITE_EXTERNAL_STORAGE},
                MY_PERMISSIONS_REQUEST_WRITE_EXTERNAL_STORAGE);

        // MY_PERMISSIONS_REQUEST_WRITE_EXTERNAL_STORAGE is an
        // app-defined int constant. The callback method gets the
        // result of the request.
    }
}
```




**Du point de vue des utilisateurs**, lors de l’installation, les utilisateurs sont accueillis par une fenêtre les invitant à confirmer les autorisations de lecture/écriture des fichiers (voir la figure 2 ci-dessous). Cela conduit à l’un des deux résultats suivants :

1. Si l’utilisateur **confirme** les autorisations, le flux d’authentification régulier sera conservé et les jetons seront stockés dans le stockage global. Les utilisateurs restent authentifiés dans l’application et dans les applications à l’aide de l’authentification Adobe Primetime tant que les jetons sont valides.
1. Si l’utilisateur **démenti** les autorisations, les actions d’écriture dans le stockage échouent et les utilisateurs ne sont authentifiés que lorsqu’ils quittent l’application. Certaines applications se réinitialisent lors du basculement entre le premier plan et l’arrière-plan, de sorte que les utilisateurs soient déconnectés lors de l’exécution de cette action. Les jetons ne sont PAS stockés et les utilisateurs devront s’authentifier chaque fois qu’ils utilisent l’application.


>[!TIP]
>
>Une fonctionnalité qui introduit la résilience du stockage est actuellement en cours de développement pour le SDK d’authentification Adobe Primetime 1.9. Le nouveau SDK est ciblé pour **dans la dernière semaine d’octobre**. L’application revient à écrire dans le stockage sandbox de l’application chaque fois que le stockage général ne peut pas être utilisé. Cela couvre le cas où, pour les applications développées dans l’API niveau 23, les utilisateurs n’acceptent PAS les autorisations de lecture/écriture dans le stockage global. Les jetons sont stockés individuellement par application, ce qui signifie que l’authentification unique entre les applications utilisant l’authentification Adobe Primetime sera désactivée.


![](assets/android-permissions-request.png)

*Figure : Dialogue de demande d’autorisation pour les applications écrites avec l’API de ciblage niveau 23*

>[!IMPORTANT]
>
> Conseils à l’Adobe **ses partenaires pour développer des applications à l’aide du niveau d’API 2 (targetSdkVersion=22) ou plus afin de garantir la meilleure expérience utilisateur possible dans le processus d’authentification.**.
