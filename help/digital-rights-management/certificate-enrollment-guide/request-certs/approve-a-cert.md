---
title: Approuver un certificat (compte ou administrateur Secondaire)
description: Approuver un certificat (compte ou administrateur Secondaire)
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Approuver un certificat (compte ou administrateur Secondaire){#approve-a-certificate-account-or-secondary-administrator}

1. Connectez-vous au site d’inscription aux certificats .
1. Sélectionnez la variable **[!UICONTROL Certificates]** .
1. Vérifiez la requête pour vérifier qu’elle est valide.
1. Si la requête est valide, cliquez sur **[!UICONTROL Approve]**.

   Vous pouvez également ajouter un commentaire. Un e-mail est envoyé au demandeur pour l’informer que la demande a été approuvée par l’un des administrateurs de la société. Une copie de cet e-mail est envoyée aux administrateurs de la société et de l’Adobe.

1. Si la requête n’est pas valide, cliquez sur **[!UICONTROL Reject]** et saisissez un commentaire dans la boîte de dialogue de confirmation.

   Un e-mail est envoyé au demandeur pour l’informer que la demande a été rejetée par l’un des administrateurs de la société. Une copie de cet e-mail est envoyée aux administrateurs de la société.

Lorsqu’un administrateur valide une demande de certificat, Adobe vérifie l’identité du demandeur. Adobe contacte le demandeur au numéro de téléphone indiqué dans son profil.

L’administrateur d’Adobe tente de contacter le demandeur deux fois dans un délai de trois jours. Si l’administrateur de l’Adobe ne peut pas contacter le demandeur, il laisse un message demandant un rappel ou il indique une heure à laquelle il appellera à nouveau. Si l’administrateur de l’Adobe ne parvient pas à joindre le demandeur, un e-mail est envoyé aux administrateurs.

>[!NOTE]
>
>Seuls les administrateurs de compte et Secondaire peuvent modifier le numéro de téléphone de l’entreprise et l’expression du demandeur.

Si l’identité du demandeur est vérifiée, le demandeur reçoit un e-mail contenant le fichier PKCS#7 ( [!DNL p7b]).

Le demandeur peut copier le contenu PKCS#7 à partir du corps de l’e-mail et l’enregistrer dans un fichier ou utiliser le fichier joint au courriel. Adobe recommande que lorsque vous enregistrez le fichier PKSC#7, vous utilisiez le nom de base que vous avez utilisé pour générer la clé privée et le fichier CSR.

>[!NOTE]
>
>Le fichier envoyé au demandeur contient uniquement le certificat. Le fichier ne contient pas d’informations de clé privée.
