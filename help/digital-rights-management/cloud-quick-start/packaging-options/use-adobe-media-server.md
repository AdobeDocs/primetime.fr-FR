---
seo-title: Utiliser Adobe Media Server
title: Utiliser Adobe Media Server
uuid: 272b9919-6ae4-4adb-aab5-28b1f92aa9fe
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5

---


# Utiliser Adobe Media Server {#use-adobe-media-server}

Certains clients utilisent peut-être déjà Adobe Media Server et souhaitent conserver ce modèle de diffusion de contenu. Si tel est le cas, les données spécifiques à Primetime Cloud DRM requises peuvent être extraites de l’un des fichiers de configuration inclus dans ce kit pour renseigner la configuration XML JIT (Just In Time) pour AMS.

Par exemple :

```xml
<?xml version="1.0"?>
<Application>
  <HDS>
    <HLS>
      <Encryption enabled="true" protection-scheme="AdobeAccessV4">
        <AdobeAccessV4>
          <ContentID>SampleVideo</ContentID>
          <CommonKeyPath>common-key.bin</CommonKeyPath>
          <LicenseServerURL>
            https://access.adobeprimetime.com/flashaccessserver/axs_prod
          </LicenseServerURL>
          <KeyServerURL>
            https://access.adobeprimetime.com:443/faxsks/axs_prod/key
          </KeyServerURL>
          <TransportCertPath>cert/Cloud DRM-transport.cer</TransportCertPath>
          <LicenseServerCertPath>cert/Cloud DRM-license.cer</LicenseServerCertPath>
          <PackagerCredentialPath>cert-from-adobe.pfx</PackagerCredentialPath>
          <PackagerCredentialPwd>pass-for-cert-from-adobe</PackagerCredentialPwd>
          <PolicyPath>policy_ios_localkeyserver.pol</PolicyPath>
        </AdobeAccessV4>
      </Encryption>
    </HLS>
  </HDS>
</Application>
```

