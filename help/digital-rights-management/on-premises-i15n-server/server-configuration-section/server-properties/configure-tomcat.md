---
title: Configurer Tomcat
description: Configurer Tomcat
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# Configurer Tomcat{#configure-tomcat}

Sur le serveur d’individualisation, modifiez le [!DNL conf/server.xml] pour inclure des informations supplémentaires dans le journal des accès. Vous pouvez utiliser ces informations à des fins de création de rapports.

1. Recherchez la configuration de la variable `AccessLogValve` in [!DNL server.xml] et modifiez le modèle comme illustré ci-dessous :

   ```
   <Valve className="org.apache.catalina.valves.AccessLogValve" 
   directory="logs" prefix="localhost_access_log." suffix=".txt" 
   pattern="%h %{x-forwarded-for}i %l %u %t &quot;%r&quot; %s %b 
   %{request-id}r" resolveHosts="false"/>
   ```

   `%{x-forwarded-for}i` enregistre la valeur de la variable `x-forwarded-for` en-tête . Si vous utilisez un proxy inverse Apache pour transférer des requêtes vers le serveur Tomcat, cet en-tête contiendra l’adresse IP du client d’origine, tandis que `%h` enregistre l’adresse IP du serveur Apache. `%{request-id}r` enregistrera l’identifiant de requête, qui correspond à l’identifiant de requête contenu dans le journal de l’application d’individualisation.

1. Modifier [!DNL conf/server.xml] et définissez la variable `unpackwars` sur false.

   Pour les serveurs d’individualisation et de génération de clés, il est préférable de modifier [!DNL conf/server.xml] et définissez la variable `unpackwars` de `false`. Sinon, lorsque vous mettez à jour les fichiers WAR, vous devrez peut-être également nettoyer les dossiers WAR non remplis.

>[!NOTE]
>
>Les futurs clients DRM auront besoin de vous pour activer et configurer le filtre CORS (Cross-Origin Resource Sharing) disponible pour Tomcat. Actuellement, aucun client DRM n’a cette exigence.
