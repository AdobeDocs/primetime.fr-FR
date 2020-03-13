---
description: 'null'
seo-description: 'null'
seo-title: Approuver un certificat (compte ou administrateur secondaire)
title: Approuver un certificat (compte ou administrateur secondaire)
uuid: 5b95e2e8-abe9-4aef-bcb4-9b98ba6604d1
translation-type: tm+mt
source-git-commit: b4b50471ab0ba98329862322a61bf73aa9e471d5

---


# Approuver un certificat (compte ou administrateur secondaire){#approve-a-certificate-account-or-secondary-administrator}

1. Connectez-vous au site d’inscription aux certificats.
1. Sélectionnez l’ **[!UICONTROL Certificates]** onglet.
1. Vérifiez que la requête est valide.
1. Si la requête est valide, cliquez sur **[!UICONTROL Approve]**.

   Vous pouvez également ajouter un commentaire. Un e-mail est envoyé au demandeur pour lui indiquer que la demande a été approuvée par l’un des administrateurs . Une copie de cet e-mail est envoyée aux  et aux administrateurs Adobe.

1. Si la requête n’est pas valide, cliquez **[!UICONTROL Reject]** et saisissez un commentaire dans la boîte de dialogue de confirmation.

   Un e-mail est envoyé au demandeur pour lui indiquer que la demande a été rejetée par l’un des administrateurs . Une copie de cet e-mail est envoyée aux administrateurs .

Lorsqu’un administrateur approuve une demande de certificat, Adobe vérifie l’identité du demandeur. Adobe contacte le demandeur au numéro de téléphone indiqué dans son  de.

L’administrateur Adobe tente de contacter le demandeur deux fois dans un délai de trois jours. Si l’administrateur Adobe ne parvient pas à contacter le demandeur, il laisse un message demandant un rappel ou indique une heure à laquelle il fera à nouveau appel. Si l’administrateur Adobe n’est pas en mesure de contacter le demandeur, un courrier électronique est envoyé aux administrateurs.

>[!NOTE]
>
>Seuls les administrateurs de compte et les administrateurs secondaires peuvent modifier le numéro de téléphone  du et la phrase de défi du demandeur.

Si l&#39;identité du demandeur est vérifiée, le demandeur reçoit un courriel contenant le fichier PKCS#7 ( [!DNL p7b]).

Le demandeur peut copier le contenu PKCS#7 du corps du courrier électronique et l’enregistrer dans un fichier ou utiliser le fichier joint au courrier électronique. Adobe recommande que lorsque vous enregistrez le fichier PKSC#7, vous utilisiez le nom de base utilisé pour générer la clé privée et le fichier CSR.

>[!NOTE]
>
>Le fichier envoyé au demandeur contient uniquement le certificat. Le fichier ne contient aucune information de clé privée.

