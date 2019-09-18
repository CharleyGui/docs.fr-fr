---
title: 'Procédure : créer des certificats temporaires à utiliser pendant le développement'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
ms.openlocfilehash: e2df35959f9821c65d694079aefa0ae6ba01897f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053296"
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a><span data-ttu-id="8d810-102">Procédure : créer des certificats temporaires à utiliser pendant le développement</span><span class="sxs-lookup"><span data-stu-id="8d810-102">How to: Create Temporary Certificates for Use During Development</span></span>

<span data-ttu-id="8d810-103">Lors du développement d’un service ou d’un client sécurisé à l’aide de Windows Communication Foundation (WCF), il est souvent nécessaire de fournir un certificat X. 509 à utiliser comme informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="8d810-103">When developing a secure service or client using Windows Communication Foundation (WCF), it is often necessary to supply an X.509 certificate to be used as a credential.</span></span> <span data-ttu-id="8d810-104">Le certificat fait en général partie d'une chaîne de certificats dont l'autorité racine est présente dans le magasin d'Autorités de certification racines de confiance de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8d810-104">The certificate typically is part of a chain of certificates with a root authority found in the Trusted Root Certification Authorities store of the computer.</span></span> <span data-ttu-id="8d810-105">Une chaîne de certificats vous permet de définir la portée d'un jeu de certificats où en général l'autorité racine provient de votre organisation ou votre division.</span><span class="sxs-lookup"><span data-stu-id="8d810-105">Having a certificate chain enables you to scope a set of certificates where typically the root authority is from your organization or business unit.</span></span> <span data-ttu-id="8d810-106">Pour émuler ce scénario au moment du développement, vous pouvez créer deux certificats pour satisfaire les conditions de sécurité.</span><span class="sxs-lookup"><span data-stu-id="8d810-106">To emulate this at development time, you can create two certificates to satisfy the security requirements.</span></span> <span data-ttu-id="8d810-107">Le premier est un certificat auto-signé placé dans le magasin d'Autorités de certification racines de confiance. Le deuxième certificat est créé à partir du premier et placé dans le magasin personnel de l'emplacement de l'ordinateur local ou dans le magasin personnel de l'emplacement de l'utilisateur actif.</span><span class="sxs-lookup"><span data-stu-id="8d810-107">The first is a self-signed certificate that is placed in the Trusted Root Certification Authorities store, and the second certificate is created from the first and is placed in either the Personal store of the Local Machine location, or the Personal store of the Current User location.</span></span> <span data-ttu-id="8d810-108">Cette rubrique décrit les étapes permettant de créer ces deux certificats à l’aide de l’applet de commande PowerShell [New-SelfSignedCertificate)](/powershell/module/pkiclient/new-selfsignedcertificate) .</span><span class="sxs-lookup"><span data-stu-id="8d810-108">This topic walks through the steps to create these two certificates using the Powershell [New-SelfSignedCertificate)](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8d810-109">Les certificats générés par l’applet de commande New-SelfSignedCertificate sont fournis à des fins de test uniquement.</span><span class="sxs-lookup"><span data-stu-id="8d810-109">The certificates that the New-SelfSignedCertificate cmdlet generates are provided for testing purposes only.</span></span> <span data-ttu-id="8d810-110">Lorsque vous déployez un service ou un client, veillez à utiliser un certificat approprié fourni par une autorité de certification.</span><span class="sxs-lookup"><span data-stu-id="8d810-110">When deploying a service or client, be sure to use an appropriate certificate provided by a certification authority.</span></span> <span data-ttu-id="8d810-111">Il peut s’agir d’un serveur de certificats Windows Server dans votre organisation ou d’un tiers.</span><span class="sxs-lookup"><span data-stu-id="8d810-111">This could either be from a Windows Server certificate server in your organization or a third party.</span></span>
>
> <span data-ttu-id="8d810-112">Par défaut, l’applet [de commande New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) crée des certificats auto-signés et ces certificats ne sont pas sécurisés.</span><span class="sxs-lookup"><span data-stu-id="8d810-112">By default, the [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet creates certificates that are self-signed and these certificates are insecure.</span></span> <span data-ttu-id="8d810-113">Le fait de placer les certificats auto-signés dans le magasin autorités de certification racines de confiance vous permet de créer un environnement de développement qui simule plus fidèlement votre environnement de déploiement.</span><span class="sxs-lookup"><span data-stu-id="8d810-113">Placing the self-signed certificates in the Trusted Root Certification Authorities store enables you to create a development environment that more closely simulates your deployment environment.</span></span>

 <span data-ttu-id="8d810-114">Pour plus d’informations sur la création et l’utilisation de certificats, consultez [utilisation des certificats](working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="8d810-114">For more information about creating and using certificates, see [Working with Certificates](working-with-certificates.md).</span></span> <span data-ttu-id="8d810-115">Pour plus d’informations sur l’utilisation d’un certificat en tant qu’informations d’identification, consultez [sécurisation des services et des clients](securing-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="8d810-115">For more information about using a certificate as a credential, see [Securing Services and Clients](securing-services-and-clients.md).</span></span> <span data-ttu-id="8d810-116">Pour obtenir un didacticiel à propos de l’utilisation de la technologie Authenticode de Microsoft, consultez [Authenticode Overviews and Tutorials](https://go.microsoft.com/fwlink/?LinkId=88919)(Vues d’ensemble et didacticiels relatifs à Authenticode).</span><span class="sxs-lookup"><span data-stu-id="8d810-116">For a tutorial about using Microsoft Authenticode technology, see [Authenticode Overviews and Tutorials](https://go.microsoft.com/fwlink/?LinkId=88919).</span></span>

## <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a><span data-ttu-id="8d810-117">Pour créer un certificat d'autorité racine auto-signé et exporter la clé privée</span><span class="sxs-lookup"><span data-stu-id="8d810-117">To create a self-signed root authority certificate and export the private key</span></span>

<span data-ttu-id="8d810-118">La commande suivante crée un certificat auto-signé avec le nom de sujet « RootCA » dans le magasin personnel de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="8d810-118">The following command creates a self-signed certificate with a subject name of "RootCA" in the Current User Personal store.</span></span>

```powershell
$rootcert = New-SelfSignedCertificate -CertStoreLocation Cert:\CurrentUser\My -DnsName "RootCA" -TextExtension @("2.5.29.19={text}CA=true") -KeyUsage CertSign,CrlSign,DigitalSignature
```

<span data-ttu-id="8d810-119">Nous devons exporter le certificat vers un fichier PFX afin qu’il puisse être importé dans où il est nécessaire dans une étape ultérieure.</span><span class="sxs-lookup"><span data-stu-id="8d810-119">We need to export the certificate to a PFX file so that it can be imported to where it's needed in a later step.</span></span> <span data-ttu-id="8d810-120">Lors de l’exportation d’un certificat avec la clé privée, un mot de passe est nécessaire pour le protéger.</span><span class="sxs-lookup"><span data-stu-id="8d810-120">When exporting a certificate with the private key, a password is needed to protect it.</span></span> <span data-ttu-id="8d810-121">Nous enregistrons le mot de `SecureString` passe dans un et utilisons l’applet de commande [Export-PfxCertificate](/powershell/module/pkiclient/export-pfxcertificate) pour exporter le certificat avec la clé privée associée dans un fichier PFX.</span><span class="sxs-lookup"><span data-stu-id="8d810-121">We save the password in a `SecureString` and use the [Export-PfxCertificate](/powershell/module/pkiclient/export-pfxcertificate) cmdlet to export the certificate with the associated private key to a PFX file.</span></span> <span data-ttu-id="8d810-122">Nous enregistrons également simplement le certificat public dans un fichier CRT à l’aide de l’applet de commande [Export-Certificate](/powershell/module/pkiclient/export-certificate) .</span><span class="sxs-lookup"><span data-stu-id="8d810-122">We also save just the public certificate into a CRT file using the [Export-Certificate](/powershell/module/pkiclient/export-certificate) cmdlet.</span></span>

```powershell
[System.Security.SecureString]$rootcertPassword = ConvertTo-SecureString -String "password" -Force -AsPlainText
[String]$rootCertPath = Join-Path -Path 'cert:\CurrentUser\My\' -ChildPath "$($rootcert.Thumbprint)"
Export-PfxCertificate -Cert $rootCertPath -FilePath 'RootCA.pfx' -Password $rootcertPassword
Export-Certificate -Cert $rootCertPath -FilePath 'RootCA.crt'
```

## <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a><span data-ttu-id="8d810-123">Pour créer un nouveau certificat signé par un certificat d'autorité racine</span><span class="sxs-lookup"><span data-stu-id="8d810-123">To create a new certificate signed by a root authority certificate</span></span>

<span data-ttu-id="8d810-124">La commande suivante crée un certificat signé par le `RootCA` avec le nom d’objet « SignedByRootCA » à l’aide de la clé privée de l’émetteur.</span><span class="sxs-lookup"><span data-stu-id="8d810-124">The following command creates a certificate signed by the `RootCA` with a subject name of "SignedByRootCA" using the private key of the issuer.</span></span>

```powershell
$testCert = New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "SignedByRootCA" -KeyExportPolicy Exportable -KeyLength 2048 -KeyUsage DigitalSignature,KeyEncipherment -Signer $rootCert
```

<span data-ttu-id="8d810-125">De même, nous enregistrons le certificat signé avec une clé privée dans un fichier PFX et juste la clé publique dans un fichier CRT.</span><span class="sxs-lookup"><span data-stu-id="8d810-125">Similarly, we save the signed certificate with private key into a PFX file and just the public key into a CRT file.</span></span>

```powershell
[String]$testCertPath = Join-Path -Path 'cert:\LocalMachine\My\' -ChildPath "$($testCert.Thumbprint)"
Export-PfxCertificate -Cert $testCertPath -FilePath testcert.pfx -Password $rootcertPassword
Export-Certificate -Cert $testCertPath -FilePath testcert.crt
```

## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a><span data-ttu-id="8d810-126">Installation d'un certificat dans le magasin d'Autorités de certification racines de confiance</span><span class="sxs-lookup"><span data-stu-id="8d810-126">Installing a Certificate in the Trusted Root Certification Authorities Store</span></span>

<span data-ttu-id="8d810-127">Une fois qu'un certificat auto-signé est créé, vous pouvez l'installer dans le magasin d'Autorités de certification racines de confiance.</span><span class="sxs-lookup"><span data-stu-id="8d810-127">Once a self-signed certificate is created, you can install it in the Trusted Root Certification Authorities store.</span></span> <span data-ttu-id="8d810-128">Tous les certificats signés à ce stade avec le certificat sont approuvés par l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8d810-128">Any certificates that are signed with the certificate at this point are trusted by the computer.</span></span> <span data-ttu-id="8d810-129">Pour cette raison, supprimez le certificat du magasin dès que vous n'en avez plus besoin.</span><span class="sxs-lookup"><span data-stu-id="8d810-129">For this reason, delete the certificate from the store as soon as you no longer need it.</span></span> <span data-ttu-id="8d810-130">Lorsque vous supprimez ce certificat d'autorité racine, tous les autres certificats ayant signé à l'aide de ce dernier ne sont plus autorisés.</span><span class="sxs-lookup"><span data-stu-id="8d810-130">When you delete this root authority certificate, all other certificates that signed with it become unauthorized.</span></span> <span data-ttu-id="8d810-131">Les certificats d'autorité racines sont un simple mécanisme qui permet de définir la portée d'un groupe de certificats selon les besoins.</span><span class="sxs-lookup"><span data-stu-id="8d810-131">Root authority certificates are simply a mechanism whereby a group of certificates can be scoped as necessary.</span></span> <span data-ttu-id="8d810-132">Par exemple, dans les applications d'égal à égal, l'autorité racine n'est pas nécessaire le plus souvent dans la mesure où l'identité d'un individu est garantie par le certificat qu'il fournit.</span><span class="sxs-lookup"><span data-stu-id="8d810-132">For example, in peer-to-peer applications, there is typically no need for a root authority because you simply trust the identity of an individual by its supplied certificate.</span></span>

### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a><span data-ttu-id="8d810-133">Pour installer un certificat auto-signé dans les Autorités de certification racines de confiance</span><span class="sxs-lookup"><span data-stu-id="8d810-133">To install a self-signed certificate in the Trusted Root Certification Authorities</span></span>

1. <span data-ttu-id="8d810-134">Ouvrez le composant logiciel enfichable Certificat.</span><span class="sxs-lookup"><span data-stu-id="8d810-134">Open the certificate snap-in.</span></span> <span data-ttu-id="8d810-135">Pour plus d’informations, consultez [Guide pratique pour Affichez les certificats avec le composant logiciel](how-to-view-certificates-with-the-mmc-snap-in.md)enfichable MMC.</span><span class="sxs-lookup"><span data-stu-id="8d810-135">For more information, see [How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>

2. <span data-ttu-id="8d810-136">Ouvrez le dossier pour stocker le certificat, soit **Ordinateur local** , soit **Utilisateur actuel**.</span><span class="sxs-lookup"><span data-stu-id="8d810-136">Open the folder to store the certificate, either the **Local Computer** or the **Current User**.</span></span>

3. <span data-ttu-id="8d810-137">Ouvrez le dossier **Autorités de certification racines de confiance** .</span><span class="sxs-lookup"><span data-stu-id="8d810-137">Open the **Trusted Root Certification Authorities** folder.</span></span>

4. <span data-ttu-id="8d810-138">Cliquez avec le bouton droit sur le dossier **Certificats** et cliquez sur **Toutes les tâches**, puis cliquez sur **Importer**.</span><span class="sxs-lookup"><span data-stu-id="8d810-138">Right-click the **Certificates** folder and click **All Tasks**, then click **Import**.</span></span>

5. <span data-ttu-id="8d810-139">Suivez les instructions de l’Assistant à l’écran pour importer RootCA. pfx dans le magasin.</span><span class="sxs-lookup"><span data-stu-id="8d810-139">Follow the on-screen wizard instructions to import the RootCA.pfx into the store.</span></span>

## <a name="using-certificates-with-wcf"></a><span data-ttu-id="8d810-140">Utilisation de certificats avec WCF</span><span class="sxs-lookup"><span data-stu-id="8d810-140">Using certificates With WCF</span></span>

<span data-ttu-id="8d810-141">Une fois que vous avez configuré les certificats temporaires, vous pouvez les utiliser pour développer des solutions WCF qui spécifient des certificats comme un type d'informations d'identification du client.</span><span class="sxs-lookup"><span data-stu-id="8d810-141">Once you have set up the temporary certificates, you can use them to develop WCF solutions that specify certificates as a client credential type.</span></span> <span data-ttu-id="8d810-142">Par exemple, la configuration XML suivante spécifie la sécurité du message et un certificat comme type d'informations d'identification du client.</span><span class="sxs-lookup"><span data-stu-id="8d810-142">For example, the following XML configuration specifies message security and a certificate as the client credential type.</span></span>

### <a name="to-specify-a-certificate-as-the-client-credential-type"></a><span data-ttu-id="8d810-143">Pour spécifier un certificat comme type d'informations d'identification du client</span><span class="sxs-lookup"><span data-stu-id="8d810-143">To specify a certificate as the client credential type</span></span>

1. <span data-ttu-id="8d810-144">Dans le fichier de configuration d'un service, utilisez le XML suivant pour affecter au mode de sécurité la valeur Message, et au type d'informations d'identification du client la valeur Certificat.</span><span class="sxs-lookup"><span data-stu-id="8d810-144">In the configuration file for a service, use the following XML to set the security mode to message, and the client credential type to certificate.</span></span>

    ```xml
    <bindings>
      <wsHttpBinding>
        <binding name="CertificateForClient">
          <security>
            <message clientCredentialType="Certificate" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    ```

2. <span data-ttu-id="8d810-145">Dans le fichier de configuration d’un client, utilisez le code XML suivant pour spécifier que le certificat se trouve dans le magasin de l’utilisateur et peut être trouvé en recherchant dans le champ SubjectName la valeur « CohoWinery ».</span><span class="sxs-lookup"><span data-stu-id="8d810-145">In the configuration file for a client, use the following XML to specify that the certificate is found in the user’s store, and can be found by searching the SubjectName field for the value "CohoWinery."</span></span>

    ```xml
    <behaviors>
      <endpointBehaviors>
        <behavior name="CertForClient">
          <clientCredentials>
            <clientCertificate findValue="CohoWinery" x509FindType="FindBySubjectName" />
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>
    ```

<span data-ttu-id="8d810-146">Pour plus d’informations sur l’utilisation des certificats dans WCF, consultez [Working with Certificates](working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="8d810-146">For more information about using certificates in WCF, see [Working with Certificates](working-with-certificates.md).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="8d810-147">sécurité du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8d810-147">.NET Framework security</span></span>

<span data-ttu-id="8d810-148">Veillez à supprimer tous les certificats d'autorité racines temporaires des dossiers **Autorités de certification racines de confiance** et **Personnel** en cliquant avec le bouton droit sur le certificat, en cliquant sur ensuite **Supprimer**.</span><span class="sxs-lookup"><span data-stu-id="8d810-148">Be sure to delete any temporary root authority certificates from the **Trusted Root Certification Authorities** and **Personal** folders by right-clicking the certificate, then clicking **Delete**.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d810-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d810-149">See also</span></span>

- [<span data-ttu-id="8d810-150">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="8d810-150">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="8d810-151">Guide pratique : Afficher les certificats avec le composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="8d810-151">How to: View Certificates with the MMC Snap-in</span></span>](how-to-view-certificates-with-the-mmc-snap-in.md)
- [<span data-ttu-id="8d810-152">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="8d810-152">Securing Services and Clients</span></span>](securing-services-and-clients.md)
