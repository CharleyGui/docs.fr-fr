---
title: "Comment : authentifier à l'aide d'un nom d'utilisateur et d'un mot de passe"
description: Découvrez comment permettre à un service WCF d’authentifier un client à l’aide d’un nom d’utilisateur et d’un mot de passe de domaine Windows, avec des exemples de code.
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
ms.openlocfilehash: 1f938f8041b2577b3705266948f29b42f23a6fd7
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247245"
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a>Comment : authentifier à l'aide d'un nom d'utilisateur et d'un mot de passe

Cette rubrique montre comment permettre à un service Windows Communication Foundation (WCF) d’authentifier un client avec un nom d’utilisateur et un mot de passe de domaine Windows. Elle suppose que vous disposez d'un service WCF auto-hébergé fonctionnel. Pour obtenir un exemple de création d’un service WCF auto-hébergé de base, consultez le [didacticiel prise en main](../getting-started-tutorial.md). Cette rubrique suppose que le service est configuré dans le code. Si vous souhaitez voir un exemple de configuration d’un service similaire à l’aide d’un fichier de configuration, consultez [nom d’utilisateur de sécurité du message](../samples/message-security-user-name.md).

Pour configurer un service afin d'authentifier ses clients à l'aide du nom d'utilisateur et du mot de passe de domaine Windows, utilisez <xref:System.ServiceModel.WSHttpBinding> et affectez la valeur `Security.Mode` à sa propriété `Message`. En outre, vous devez spécifier un certificat X509 qui sera utilisé pour chiffrer le nom d'utilisateur et le mot de passe lors de leur envoi du client au service.

Sur le client, vous devez demander à l'utilisateur le nom d'utilisateur et le mot de passe et spécifier les informations d'identification de l'utilisateur sur le proxy WCF.

## <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a>Pour configurer un service WCF pour l’authentification à l’aide du nom d’utilisateur et du mot de passe de domaine Windows

1. Créez une instance de <xref:System.ServiceModel.WSHttpBinding>, définissez le mode de sécurité de liaison à <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType>, définissez le `ClientCredentialType` de liaison à <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType>, et ajoutez un point de terminaison de service à l'aide de la liaison configurée à l'hôte de service comme indiqué dans le code suivant :

    ```csharp
    // ...
    var userNameBinding = new WSHttpBinding();
    userNameBinding.Security.Mode = SecurityMode.Message;
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");
    // ...
    ```

2. Spécifiez le certificat de serveur utilisé pour chiffrer les informations de nom d'utilisateur et mot de passe envoyées sur le réseau. Ce code doit suivre immédiatement le code ci-dessus. L’exemple suivant utilise le certificat créé par le fichier setup.bat à partir de l’exemple de [nom d’utilisateur de sécurité de message](../samples/message-security-user-name.md) :

    ```csharp
    // ...
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");
    // ...
    ```

    Vous pouvez utiliser votre propre certificat ; il vous suffit de modifier le code pour faire référence à votre certificat. Pour plus d’informations sur la création et l’utilisation de certificats, consultez [utilisation des certificats](working-with-certificates.md). Assurez-vous que le certificat se trouve dans le magasin de certificats Personnes approuvées de l'ordinateur local. Pour ce faire, vous pouvez exécuter mmc.exe et sélectionner l’élément de menu **fichier**, **Ajouter/supprimer un composant logiciel enfichable...** . Dans la boîte de dialogue **Ajouter ou supprimer des composants logiciels enfichables** , sélectionnez le **composant logiciel enfichable Certificats** , puis cliquez sur **Ajouter**. Dans la boîte de dialogue composant logiciel enfichable Certificats, sélectionnez **compte d’ordinateur**. Par défaut, le certificat généré à partir de l'exemple de nom d'utilisateur de sécurité du message se trouve dans le dossier Personal/Certificates.  Elle est indiquée comme « localhost » sous la colonne délivré à dans la fenêtre MMC. Glissez-déposez le certificat dans le dossier **personnes autorisées** . Cela permettra à WCF de traiter le certificat comme un certificat approuvé lorsque vous effectuez l'authentification.

## <a name="to-call-the-service-passing-username-and-password"></a>Pour appeler le service en passant le nom d'utilisateur et le mot de passe

1. L'application cliente doit demander à l'utilisateur d'entrer son nom d'utilisateur et son mot de passe. Le code suivant demande à l’utilisateur le nom d’utilisateur et le mot de passe :

    > [!WARNING]
    > Ce code ne doit pas être utilisé en production, car le mot de passe s'affiche lorsqu'il est entré.

    ```csharp
    public static void GetPassword(out string username, out string password)
    {
        Console.WriteLine("Provide a valid machine or domain account. [domain\\user]");
        Console.WriteLine("   Enter username:");
        username = Console.ReadLine();
        Console.WriteLine("   Enter password:");
        password = Console.ReadLine();
    }
    ```

2. Créez une instance du proxy client en spécifiant les informations d’identification du client, comme indiqué dans le code suivant :

    ```csharp
    string username;
    string password;

    // Instantiate the proxy.
    var proxy = new Service1Client();

    // Prompt the user for username & password.
    GetPassword(out username, out password);

    // Set the user's credentials on the proxy.
    proxy.ClientCredentials.UserName.UserName = username;
    proxy.ClientCredentials.UserName.Password = password;

    // Treat the test certificate as trusted.
    proxy.ClientCredentials.ServiceCertificate.Authentication.CertificateValidationMode = System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust;
    // Call the service operation using the proxy
    ```

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.SecurityMode>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>
- <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>
- [Sécurité de transport avec l'authentification de base](transport-security-with-basic-authentication.md)
- [Sécurité des applications distribuées](distributed-application-security.md)
- [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)
