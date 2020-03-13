---
seo-title: Configuration de Tomcat
title: Configuration de Tomcat
uuid: 5f23aa33-29d7-4b41-87a4-59dc5b433de4
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Configuration de Tomcat{#configure-tomcat}

Sur le serveur d’individualisation, modifiez le [!DNL conf/server.xml] fichier de Tomcat afin d’inclure des informations supplémentaires dans le journal d’accès. Vous pouvez utiliser ces informations à des fins de .

1. Localisez la configuration de la `AccessLogValve` dans [!DNL server.xml] et modifiez le modèle comme illustré ci-dessous :

   ```
   <Valve className="org.apache.catalina.valves.AccessLogValve" 
   directory="logs" prefix="localhost_access_log." suffix=".txt" 
   pattern="%h %{x-forwarded-for}i %l %u %t &quot;%r&quot; %s %b 
   %{request-id}r" resolveHosts="false"/>
   ```

   `%{x-forwarded-for}i` enregistre la valeur de l&#39; `x-forwarded-for` en-tête. Si vous utilisez un proxy inverse Apache pour transférer des requêtes au serveur Tomcat, cet en-tête contiendra l’adresse IP du client d’origine, alors `%h` qu’il enregistre l’adresse IP du serveur Apache. `%{request-id}r` enregistre l’identifiant de requête, qui correspond à l’identifiant de requête contenu dans le journal de l’application d’individualisation.

1. Modifiez [!DNL conf/server.xml] et définissez la `unpackwars` propriété sur false.

   Pour les serveurs d’individualisation et de génération de clés, il est conseillé de modifier [!DNL conf/server.xml] et de définir la `unpackwars` propriété sur `false`. Sinon, lorsque vous mettez à jour les fichiers WAR, vous devrez peut-être nettoyer les dossiers WAR non compressés.

>[!NOTE]
>
>Les futurs clients DRM vous demanderont d’activer et de configurer le filtre CORS (Cross-  Resource Sharing) disponible pour Tomcat. À l’heure actuelle, aucun client DRM n’a cette exigence.

