---
title: 'Procédure : créer des certificats temporaires à utiliser pendant le développement'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
ms.openlocfilehash: 4223ee8c8790ad4d0ae2275b347c4f974eeb4158
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877961"
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a>Procédure : créer des certificats temporaires à utiliser pendant le développement

Lorsque vous développez un service sécurisé ou un client à l’aide de Windows Communication Foundation (WCF), il est souvent nécessaire de fournir un certificat X.509 à utiliser comme informations d’identification. Le certificat fait en général partie d'une chaîne de certificats dont l'autorité racine est présente dans le magasin d'Autorités de certification racines de confiance de l'ordinateur. Une chaîne de certificats vous permet de définir la portée d'un jeu de certificats où en général l'autorité racine provient de votre organisation ou votre division. Pour émuler ce scénario au moment du développement, vous pouvez créer deux certificats pour satisfaire les conditions de sécurité. Le premier est un certificat auto-signé placé dans le magasin d'Autorités de certification racines de confiance. Le deuxième certificat est créé à partir du premier et placé dans le magasin personnel de l'emplacement de l'ordinateur local ou dans le magasin personnel de l'emplacement de l'utilisateur actif. Cette rubrique décrit les étapes pour créer ces deux certificats à l’aide de la commande Powershell [New-SelfSignedCertificate)](/powershell/module/pkiclient/new-selfsignedcertificate) applet de commande.

> [!IMPORTANT]
> Les certificats qui génère l’applet de commande New-SelfSignedCertificate sont fournis uniquement à des fins de test. Lorsque vous déployez un service ou un client, veillez à utiliser un certificat approprié fourni par une autorité de certification. Cela peut provenir d’un serveur de certificats Windows Server dans votre organisation ou un tiers.
>
> Par défaut, le [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) applet de commande crée des certificats auto-signés et ces certificats ne sont pas sécurisés. Placer les certificats auto-signés dans Trusted Root Certification Authorities store vous permet de créer un environnement de développement plus fidèlement votre environnement de déploiement.

 Pour plus d’informations sur la création et l’utilisation de certificats, consultez [utilisation des certificats](working-with-certificates.md). Pour plus d’informations sur l’utilisation d’un certificat comme information d’identification, consultez [Securing Services and Clients](securing-services-and-clients.md). Pour obtenir un didacticiel à propos de l’utilisation de la technologie Authenticode de Microsoft, consultez [Authenticode Overviews and Tutorials](https://go.microsoft.com/fwlink/?LinkId=88919)(Vues d’ensemble et didacticiels relatifs à Authenticode).

## <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a>Pour créer un certificat d'autorité racine auto-signé et exporter la clé privée

La commande suivante crée un certificat auto-signé avec le nom du sujet du « RootCA » dans le magasin utilisateur actuel personnel.

```powershell
$rootCert = New-SelfSignedCertificate -CertStoreLocation cert:\CurrentUser\My -DnsName "RootCA" -TextExtension @("2.5.29.37={text}1.3.6.1.5.5.7.3.1,1.3.6.1.5.5.7.3.2") -KeyUsage CertSign,DigitalSignature
```

Nous avons besoin d’exporter le certificat vers un fichier PFX afin qu’il puisse être importé à là où cela est nécessaire dans une étape ultérieure. Lorsque vous exportez un certificat avec la clé privée, un mot de passe est nécessaire pour les protéger. Nous enregistrons le mot de passe dans un `SecureString` et utiliser le [Export-PfxCertificate](/powershell/module/pkiclient/export-pfxcertificate) applet de commande pour exporter le certificat avec la clé privée associée à un fichier PFX. Nous enregistrons également simplement le certificat public dans un fichier de bibliothèque CRT, en utilisant le [Export-Certificate](/powershell/module/pkiclient/export-certificate) applet de commande.

```powershell
[System.Security.SecureString]$rootcertPassword = ConvertTo-SecureString -String "password" -Force -AsPlainText
[String]$rootCertPath = Join-Path -Path 'cert:\CurrentUser\My\' -ChildPath "$($rootcert.Thumbprint)"
Export-PfxCertificate -Cert $rootCertPath -FilePath 'RootCA.pfx' -Password $rootcertPassword
Export-Certificate -Cert $rootCertPath -FilePath 'RootCA.crt'
```

## <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a>Pour créer un nouveau certificat signé par un certificat d'autorité racine

La commande suivante crée un certificat signé par le `RootCA` avec un nom de sujet de « SignedByRootCA » à l’aide de la clé privée de l’émetteur.

```powershell
$testCert = New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "SignedByRootCA" -KeyExportPolicy Exportable -KeyLength 2048 -KeyUsage DigitalSignature,KeyEncipherment -Signer $rootCert
```

De même, nous enregistrons le certificat signé avec la clé privée dans un fichier PFX et uniquement la clé publique dans un fichier de bibliothèque CRT.

```powershell
[String]$testCertPath = Join-Path -Path 'cert:\LocalMachine\My\' -ChildPath "$($testCert.Thumbprint)"
Export-PfxCertificate -Cert $testCertPath -FilePath testcert.pfx -Password $rootcertPassword
Export-Certificate -Cert $testCertPath -FilePath testcert.crt
```

## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a>Installation d'un certificat dans le magasin d'Autorités de certification racines de confiance

Une fois qu'un certificat auto-signé est créé, vous pouvez l'installer dans le magasin d'Autorités de certification racines de confiance. Tous les certificats signés à ce stade avec le certificat sont approuvés par l'ordinateur. Pour cette raison, supprimez le certificat du magasin dès que vous n'en avez plus besoin. Lorsque vous supprimez ce certificat d'autorité racine, tous les autres certificats ayant signé à l'aide de ce dernier ne sont plus autorisés. Les certificats d'autorité racines sont un simple mécanisme qui permet de définir la portée d'un groupe de certificats selon les besoins. Par exemple, dans les applications d'égal à égal, l'autorité racine n'est pas nécessaire le plus souvent dans la mesure où l'identité d'un individu est garantie par le certificat qu'il fournit.

### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a>Pour installer un certificat auto-signé dans les Autorités de certification racines de confiance

1. Ouvrez le composant logiciel enfichable Certificat. Pour plus d'informations, voir [Procédure : Afficher les certificats avec le composant logiciel enfichable MMC](how-to-view-certificates-with-the-mmc-snap-in.md).

2. Ouvrez le dossier pour stocker le certificat, soit **Ordinateur local** , soit **Utilisateur actuel**.

3. Ouvrez le dossier **Autorités de certification racines de confiance** .

4. Cliquez avec le bouton droit sur le dossier **Certificats** et cliquez sur **Toutes les tâches**, puis cliquez sur **Importer**.

5. Suivez l’Assistant à l’écran des instructions pour importer le RootCA.pfx dans le magasin.

## <a name="using-certificates-with-wcf"></a>L’utilisation de certificats avec WCF

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

2. Dans le fichier de configuration pour un client, utilisez le code XML suivant pour spécifier que le certificat est trouvé dans le magasin de l’utilisateur et peut être trouvé en recherchant le champ SubjectName pour la valeur « CohoWinery ».

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
- [Guide pratique pour Afficher les certificats avec le composant logiciel enfichable MMC](how-to-view-certificates-with-the-mmc-snap-in.md)
- [Sécurisation des services et des clients](securing-services-and-clients.md)
