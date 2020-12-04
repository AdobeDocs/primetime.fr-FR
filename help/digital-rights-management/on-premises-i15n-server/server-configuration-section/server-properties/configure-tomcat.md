---
seo-title: Configurer Tomcat
title: Configurer Tomcat
uuid: 5f23aa33-29d7-4b41-87a4-59dc5b433de4
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---


# Configurer Tomcat{#configure-tomcat}

Sur le serveur d’individualisation, modifiez le fichier [!DNL conf/server.xml] de Tomcat afin d’inclure des informations supplémentaires dans le journal d’accès. Vous pouvez utiliser ces informations à des fins de rapports.

1. Recherchez la configuration de `AccessLogValve` dans [!DNL server.xml] et modifiez le modèle comme indiqué ci-dessous :

   ```
   <Valve className="org.apache.catalina.valves.AccessLogValve" 
   directory="logs" prefix="localhost_access_log." suffix=".txt" 
   pattern="%h %{x-forwarded-for}i %l %u %t &quot;%r&quot; %s %b 
   %{request-id}r" resolveHosts="false"/>
   ```

   `%{x-forwarded-for}i` enregistre la valeur de l&#39; `x-forwarded-for` en-tête. Si vous utilisez un proxy inverse Apache pour transférer des requêtes au serveur Tomcat, cet en-tête contient l’adresse IP du client d’origine, alors que `%h` enregistre l’adresse IP du serveur Apache. `%{request-id}r` enregistrera l’identifiant de demande, qui correspond à l’identifiant de demande contenu dans le journal de l’application d’individualisation.

1. Modifiez [!DNL conf/server.xml] et définissez la propriété `unpackwars` sur false.

   Pour les serveurs Individualisation et Génération de clés, il est recommandé de modifier [!DNL conf/server.xml] et de définir la propriété `unpackwars` sur `false`. Sinon, lorsque vous mettez à jour les fichiers WAR, vous devrez peut-être nettoyer les dossiers WAR non emballés.

>[!NOTE]
>
>Les futurs clients DRM devront activer et configurer le filtre CORS (partage de ressources entre Origines) disponible pour Tomcat. Actuellement, aucun client DRM n&#39;a cette exigence.

