---
title: Avantages de l’utilisation du paramètre deviceType sans client dans les mesures d’authentification Primetime
description: Avantages de l’utilisation du paramètre deviceType sans client dans les mesures d’authentification Primetime
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# Avantages de l’utilisation du paramètre deviceType sans client dans les mesures d’authentification Primetime {#benefits-of-using-the-clientless-devicetype-parameter-in-primetime-authentication-metrics}

>[!NOTE]
>
>Le contenu de cette page est fourni à titre d’information uniquement. L’utilisation de cette API nécessite une licence actuelle de Adobe. Aucune utilisation non autorisée n’est autorisée.

</br>

## Contexte

Bien que facultatif, le paramètre `deviceType` L’API sans client, lorsqu’elle est présente, est utilisée dans les mesures d’authentification Primetime qui sont exposées par le biais de [Surveillance du service de droits](/help/authentication/entitlement-service-monitoring-overview.md).

En considérant que la connexion entre la variable `deviceType` et son **avantages** sur les mesures d’authentification Primetime n’ont pas été initialement spécifiées, le but de cette note technique est d’ajouter plus d’informations à leur sujet.

## Explication

La variable `deviceType` était présent dans l’API sans client depuis la première version, mais ses implications sur les mesures d’authentification Primetime ont été ajoutées dans une version plus récente.



>[!IMPORTANT]
>
>Si le paramètre `deviceType` est défini correctement, puis il a les éléments suivants : **avantage** dans la surveillance du service de droits : il propose des mesures qui sont [ventilation par type d’appareil](/help/authentication/entitlement-service-monitoring-overview.md#clientless_device_type) lors de l’utilisation de Clientless, de sorte que différents types d’analyses puissent être effectués pour Roku, Apple TV, Xbox, etc.


Pour plus d’informations sur l’API de surveillance du service de droits, reportez-vous au [descendre dans l&#39;arborescence,](/help/authentication/entitlement-service-monitoring-api.md#drill-down_tree) qui illustre le [dimensions](/help/authentication/entitlement-service-monitoring-overview.md#esm_dimensions) (ressources) disponibles dans ESM 2.0.

>[!NOTE]
>
>Le contenu de cette note technique a également été ajouté au [API sans client](#clientless_device_type).




## Implémentation

Pour tirer pleinement parti des mesures d’authentification Primetime, il existe deux types de [API sans client](#web_srvs_summary) qui sont actuellement utilisés et qui doivent avoir la valeur `deviceType` set :

1. API qui possèdent des `regcode` comme paramètre requis et utilisera la variable `deviceType` qui a été défini lors de la création de la variable `regcode`, avec l’appel API suivant :
   - [\&lt;reggie _fqdn=&quot;&quot;>/reggie/v1/{requestorId}/regcode](#reg_serv)

1. Les API qui comportent la variable `deviceType` comme paramètre facultatif :
   - [\&lt;sp _fqdn=&quot;&quot;>/api/v1/checkauthn](#check_authn_token)
   - [&lt;span class=&quot;s1&quot;>](#retrieve_authn_token)
   - [\&lt;sp _fqdn=&quot;&quot;>/api/v1/authorized](#init_authz)
   - [\&lt;sp _fqdn=&quot;&quot;>/api/v1/tokens/authz](#retrieve_authz_token)
   - [\&lt;sp _fqdn=&quot;&quot;>/api/v1/tokens/media](#short_media)
   - [\&lt;sp _fqdn=&quot;&quot;>/api/v1/mediatoken](#short_media)
   - [\&lt;sp _fqdn=&quot;&quot;>/api/v1/preauthorized](#PreAuthZ_Resources)
   - [\&lt;sp _fqdn=&quot;&quot;>/api/v1/logout](#init_logout)

Nous vous recommandons d’utiliser la variable `deviceType` et transmettez le type d’appareil sans client approprié pour toutes les API.
