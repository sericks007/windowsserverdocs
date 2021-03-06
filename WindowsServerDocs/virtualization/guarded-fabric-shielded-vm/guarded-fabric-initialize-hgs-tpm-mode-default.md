---
title: Initialize the HGS cluster using TPM mode in a new dedicated forest (default)
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 07/05/2017
---

# Initialize the HGS cluster using TPM mode in a new dedicated forest (default)

>Applies To: Windows Server 2016

>[!div class="step-by-step"]
[« Install HGS in a new forest](guarded-fabric-install-hgs-default.md)
[Install trusted TPM root certificates »](guarded-fabric-install-trusted-tpm-root-certificates.md)

1.  [!INCLUDE [Initialize HGS](../../../includes/guarded-fabric-initialize-hgs-default-step-one.md)]

2.  [!INCLUDE [Obtain certificates for HGS](../../../includes/guarded-fabric-initialize-hgs-default-step-two.md)]

3.  Run [Initialize-HgsServer](https://technet.microsoft.com/library/mt652185.aspx) in an elevated PowerShell window on the first HGS node. The syntax of this cmdlet supports many different inputs, but the 2 most common invocations are below:

    -   If you are using PFX files for your signing and encryption certificates, run the following commands:

        ```powershell
        $signingCertPass = Read-Host -AsSecureString -Prompt "Signing certificate password"
        $encryptionCertPass = Read-Host -AsSecureString -Prompt "Encryption certificate password"

        Initialize-HgsServer -HgsServiceName 'MyHgsDNN' -SigningCertificatePath '.\signCert.pfx' -SigningCertificatePassword $signingCertPass -EncryptionCertificatePath '.\encCert.pfx' -EncryptionCertificatePassword $encryptionCertPass -TrustTpm
        ```

    -   If you are using non-exportable certificates that are installed in the local certificate store, run the following command. If you do not know the thumbprints of your certificates, you can list available certificates by running `Get-ChildItem Cert:\LocalMachine\My`.

        ```powershell
        Initialize-HgsServer -HgsServiceName 'MyHgsDNN' -SigningCertificateThumbprint '1A2B3C4D5E6F...' -EncryptionCertificateThumbprint '0F9E8D7C6B5A...' -TrustTpm
        ```

4.  [!INCLUDE [Initialize HGS](../../../includes/guarded-fabric-initialize-hgs-default-step-four.md)]

5.  [!INCLUDE [Initialize HGS](../../../includes/guarded-fabric-initialize-hgs-default-step-five.md)]
  