---
title: 'Procédure : créer des certificats temporaires à utiliser pendant le développement'
description: Découvrez comment utiliser une applet de commande PowerShell pour créer deux certificats X. 509 temporaires à utiliser lors du développement d’un client ou service WCF sécurisé.
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
ms.openlocfilehash: a249f0de00c45b1588762ffa0f826e890f961334
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91607770"
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a>Procédure : créer des certificats temporaires à utiliser pendant le développement

Lors du développement d’un service ou d’un client sécurisé à l’aide de Windows Communication Foundation (WCF), il est souvent nécessaire de fournir un certificat X. 509 à utiliser comme informations d’identification. Le certificat fait en général partie d'une chaîne de certificats dont l'autorité racine est présente dans le magasin d'Autorités de certification racines de confiance de l'ordinateur. Une chaîne de certificats vous permet de définir la portée d'un jeu de certificats où en général l'autorité racine provient de votre organisation ou votre division. Pour émuler ce scénario au moment du développement, vous pouvez créer deux certificats pour satisfaire les conditions de sécurité. Le premier est un certificat auto-signé placé dans le magasin d'Autorités de certification racines de confiance. Le deuxième certificat est créé à partir du premier et placé dans le magasin personnel de l'emplacement de l'ordinateur local ou dans le magasin personnel de l'emplacement de l'utilisateur actif. Cette rubrique décrit les étapes permettant de créer ces deux certificats à l’aide de l’applet de commande PowerShell [New-SelfSignedCertificate)](/powershell/module/pkiclient/new-selfsignedcertificate) .

> [!IMPORTANT]
> Les certificats générés par l’applet de commande New-SelfSignedCertificate sont fournis à des fins de test uniquement. Lorsque vous déployez un service ou un client, veillez à utiliser un certificat approprié fourni par une autorité de certification. Il peut s’agir d’un serveur de certificats Windows Server dans votre organisation ou d’un tiers.
>
> Par défaut, l’applet [de commande New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) crée des certificats auto-signés et ces certificats ne sont pas sécurisés. Le fait de placer les certificats auto-signés dans le magasin autorités de certification racines de confiance vous permet de créer un environnement de développement qui simule plus fidèlement votre environnement de déploiement.

 Pour plus d’informations sur la création et l’utilisation de certificats, consultez [utilisation des certificats](working-with-certificates.md). Pour plus d’informations sur l’utilisation d’un certificat en tant qu’informations d’identification, consultez [sécurisation des services et des clients](securing-services-and-clients.md). Pour obtenir un didacticiel à propos de l’utilisation de la technologie Authenticode de Microsoft, consultez [Authenticode Overviews and Tutorials](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537360(v=vs.85))(Vues d’ensemble et didacticiels relatifs à Authenticode).

## <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a>Pour créer un certificat d'autorité racine auto-signé et exporter la clé privée

La commande suivante crée un certificat auto-signé avec le nom de sujet « RootCA » dans le magasin personnel de l’utilisateur actuel.

```powershell
$rootcert = New-SelfSignedCertificate -CertStoreLocation Cert:\CurrentUser\My -DnsName "RootCA" -TextExtension @("2.5.29.19={text}CA=true") -KeyUsage CertSign,CrlSign,DigitalSignature
```

Nous devons exporter le certificat vers un fichier PFX afin qu’il puisse être importé dans où il est nécessaire dans une étape ultérieure. Lors de l’exportation d’un certificat avec la clé privée, un mot de passe est nécessaire pour le protéger. Nous enregistrons le mot de passe dans un `SecureString` et utilisons l’applet de commande [Export-PfxCertificate](/powershell/module/pkiclient/export-pfxcertificate) pour exporter le certificat avec la clé privée associée dans un fichier PFX. Nous enregistrons également simplement le certificat public dans un fichier CRT à l’aide de l’applet de commande [Export-Certificate](/powershell/module/pkiclient/export-certificate) .

```powershell
[System.Security.SecureString]$rootcertPassword = ConvertTo-SecureString -String "password" -Force -AsPlainText
[String]$rootCertPath = Join-Path -Path 'cert:\CurrentUser\My\' -ChildPath "$($rootcert.Thumbprint)"
Export-PfxCertificate -Cert $rootCertPath -FilePath 'RootCA.pfx' -Password $rootcertPassword
Export-Certificate -Cert $rootCertPath -FilePath 'RootCA.crt'
```

## <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a>Pour créer un nouveau certificat signé par un certificat d'autorité racine

La commande suivante crée un certificat signé par le `RootCA` avec le nom d’objet « SignedByRootCA » à l’aide de la clé privée de l’émetteur.

```powershell
$testCert = New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "SignedByRootCA" -KeyExportPolicy Exportable -KeyLength 2048 -KeyUsage DigitalSignature,KeyEncipherment -Signer $rootCert
```

De même, nous enregistrons le certificat signé avec une clé privée dans un fichier PFX et juste la clé publique dans un fichier CRT.

```powershell
[String]$testCertPath = Join-Path -Path 'cert:\LocalMachine\My\' -ChildPath "$($testCert.Thumbprint)"
Export-PfxCertificate -Cert $testCertPath -FilePath testcert.pfx -Password $rootcertPassword
Export-Certificate -Cert $testCertPath -FilePath testcert.crt
```

## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a>Installation d'un certificat dans le magasin d'Autorités de certification racines de confiance

Une fois qu'un certificat auto-signé est créé, vous pouvez l'installer dans le magasin d'Autorités de certification racines de confiance. Tous les certificats signés à ce stade avec le certificat sont approuvés par l'ordinateur. Pour cette raison, supprimez le certificat du magasin dès que vous n'en avez plus besoin. Lorsque vous supprimez ce certificat d'autorité racine, tous les autres certificats ayant signé à l'aide de ce dernier ne sont plus autorisés. Les certificats d'autorité racines sont un simple mécanisme qui permet de définir la portée d'un groupe de certificats selon les besoins. Par exemple, dans les applications d'égal à égal, l'autorité racine n'est pas nécessaire le plus souvent dans la mesure où l'identité d'un individu est garantie par le certificat qu'il fournit.

### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a>Pour installer un certificat auto-signé dans les Autorités de certification racines de confiance

1. Ouvrez le composant logiciel enfichable Certificat. Pour plus d’informations, consultez la page [Affichage de certificats à l’aide du composant logiciel enfichable MMC](how-to-view-certificates-with-the-mmc-snap-in.md).

2. Ouvrez le dossier pour stocker le certificat, soit **Ordinateur local** , soit **Utilisateur actuel**.

3. Ouvrez le dossier **Autorités de certification racines de confiance** .

4. Cliquez avec le bouton droit sur le dossier **Certificats** et cliquez sur **Toutes les tâches**, puis cliquez sur **Importer**.

5. Suivez les instructions de l’Assistant à l’écran pour importer RootCA. pfx dans le magasin.

## <a name="using-certificates-with-wcf"></a>Utilisation de certificats avec WCF

Une fois que vous avez configuré les certificats temporaires, vous pouvez les utiliser pour développer des solutions WCF qui spécifient des certificats comme un type d'informations d'identification du client. Par exemple, la configuration XML suivante spécifie la sécurité du message et un certificat comme type d'informations d'identification du client.

### <a name="to-specify-a-certificate-as-the-client-credential-type"></a>Pour spécifier un certificat comme type d'informations d'identification du client

1. Dans le fichier de configuration d'un service, utilisez le XML suivant pour affecter au mode de sécurité la valeur Message, et au type d'informations d'identification du client la valeur Certificat.

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

2. Dans le fichier de configuration d’un client, utilisez le code XML suivant pour spécifier que le certificat se trouve dans le magasin de l’utilisateur et peut être trouvé en recherchant dans le champ SubjectName la valeur « CohoWinery ».

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

Pour plus d’informations sur l’utilisation des certificats dans WCF, consultez [Working with Certificates](working-with-certificates.md).

## <a name="net-framework-security"></a>sécurité du .NET Framework

Veillez à supprimer tous les certificats d'autorité racines temporaires des dossiers **Autorités de certification racines de confiance** et **Personnel** en cliquant avec le bouton droit sur le certificat, en cliquant sur ensuite **Supprimer**.

## <a name="see-also"></a>Voir aussi

- [Utilisation des certificats](working-with-certificates.md)
- [Procédure : voir les certificats avec le composant logiciel enfichable MMC](how-to-view-certificates-with-the-mmc-snap-in.md)
- [Sécurisation des services et des clients](securing-services-and-clients.md)
