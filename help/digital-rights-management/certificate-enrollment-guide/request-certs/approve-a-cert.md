---
description: 'null'
seo-description: 'null'
seo-title: Approuver un certificat (compte ou administrateur Secondaire)
title: Approuver un certificat (compte ou administrateur Secondaire)
uuid: 5b95e2e8-abe9-4aef-bcb4-9b98ba6604d1
translation-type: tm+mt
source-git-commit: b4b50471ab0ba98329862322a61bf73aa9e471d5
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---


# Approuver un certificat (compte ou administrateur Secondaire){#approve-a-certificate-account-or-secondary-administrator}

1. Connectez-vous au site d’inscription aux certificats.
1. Sélectionnez l&#39;onglet **[!UICONTROL Certificates]**.
1. Examinez la demande pour vérifier qu’elle est valide.
1. Si la requête est valide, cliquez sur **[!UICONTROL Approve]**.

   Vous pouvez également ajouter un commentaire. Un e-mail est envoyé au demandeur pour lui indiquer que la demande a été approuvée par l&#39;un des administrateurs de la société. Une copie de cet e-mail est envoyée aux administrateurs de société et d&#39;Adobe.

1. Si la requête n’est pas valide, cliquez sur **[!UICONTROL Reject]** et saisissez un commentaire dans la boîte de dialogue de confirmation.

   Un e-mail est envoyé au demandeur pour lui indiquer que la demande a été rejetée par l&#39;un des administrateurs de la société. Une copie de ce courrier électronique est envoyée aux administrateurs de société.

Lorsqu&#39;un administrateur approuve une demande de certificat, l&#39;Adobe vérifie l&#39;identité du demandeur. L&#39;Adobe contacte le demandeur au numéro de téléphone indiqué dans son profil.

L&#39;administrateur d&#39;Adobe tente de contacter le demandeur deux fois dans un délai de trois jours. Si l&#39;administrateur de l&#39;Adobe ne peut pas contacter le demandeur, il laisse un message demandant un rappel ou il lui donne une heure où il fera de nouveau appel. Si l&#39;administrateur d&#39;Adobe n&#39;est pas en mesure de contacter le demandeur, un e-mail est envoyé aux administrateurs.

>[!NOTE]
>
>Seuls les administrateurs de compte et les administrateurs Secondaires peuvent modifier le numéro de téléphone de la société et l&#39;expression de défi du demandeur.

Si l&#39;identité du demandeur est vérifiée, le demandeur reçoit un courriel contenant le fichier PKCS#7 ( [!DNL p7b]).

Le demandeur peut copier le contenu PKCS#7 du corps du courriel et l&#39;enregistrer dans un fichier ou utiliser le fichier joint au courriel. Adobe recommande que lorsque vous enregistrez le fichier PKSC#7, vous utilisiez le nom de base utilisé pour générer la clé privée et le fichier CSR.

>[!NOTE]
>
>Le fichier envoyé au demandeur contient uniquement le certificat. Le fichier ne contient aucune information de clé privée.

