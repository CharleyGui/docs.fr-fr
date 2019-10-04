---
title: 'Procédure : s’authentifier avec un nom d’utilisateur et un mot de passe'
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
ms.openlocfilehash: 33205f9e12fcee53f2f29b63b836ea0cbc792025
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834735"
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a><span data-ttu-id="8f2eb-102">Procédure : s’authentifier avec un nom d’utilisateur et un mot de passe</span><span class="sxs-lookup"><span data-stu-id="8f2eb-102">How to: Authenticate with a User Name and Password</span></span>

<span data-ttu-id="8f2eb-103">Cette rubrique montre comment permettre à un service Windows Communication Foundation (WCF) d’authentifier un client avec un nom d’utilisateur et un mot de passe de domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="8f2eb-103">This topic demonstrates how to enable a Windows Communication Foundation (WCF) service to authenticate a client with a Windows domain username and password.</span></span> <span data-ttu-id="8f2eb-104">Elle suppose que vous disposez d'un service WCF auto-hébergé fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="8f2eb-104">It assumes you have a working, self-hosted WCF service.</span></span> <span data-ttu-id="8f2eb-105">Pour obtenir un exemple de création d’un service WCF auto-hébergé de base, consultez le [didacticiel prise en main](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="8f2eb-105">For an example of creating a basic self-hosted WCF service see, [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span> <span data-ttu-id="8f2eb-106">Cette rubrique suppose que le service est configuré dans le code.</span><span class="sxs-lookup"><span data-stu-id="8f2eb-106">This topic assumes the service is configured in code.</span></span> <span data-ttu-id="8f2eb-107">Si vous souhaitez voir un exemple de configuration d’un service similaire à l’aide d’un fichier de configuration, consultez [nom d’utilisateur de sécurité du message](../samples/message-security-user-name.md).</span><span class="sxs-lookup"><span data-stu-id="8f2eb-107">If you would like to see an example of configuring a similar service using a configuration file, see [Message Security User Name](../samples/message-security-user-name.md).</span></span>

<span data-ttu-id="8f2eb-108">Pour configurer un service afin d'authentifier ses clients à l'aide du nom d'utilisateur et du mot de passe de domaine Windows, utilisez <xref:System.ServiceModel.WSHttpBinding> et affectez la valeur `Security.Mode` à sa propriété `Message`.</span><span class="sxs-lookup"><span data-stu-id="8f2eb-108">To configure a service to authenticate its clients using Windows Domain username and passwords use the <xref:System.ServiceModel.WSHttpBinding> and set its `Security.Mode` property to `Message`.</span></span> <span data-ttu-id="8f2eb-109">En outre, vous devez spécifier un certificat X509 qui sera utilisé pour chiffrer le nom d'utilisateur et le mot de passe lors de leur envoi du client au service.</span><span class="sxs-lookup"><span data-stu-id="8f2eb-109">In addition you must specify an X509 certificate that will be used to encrypt the username and password as they are sent from the client to the service.</span></span>

<span data-ttu-id="8f2eb-110">Sur le client, vous devez demander à l'utilisateur le nom d'utilisateur et le mot de passe et spécifier les informations d'identification de l'utilisateur sur le proxy WCF.</span><span class="sxs-lookup"><span data-stu-id="8f2eb-110">On the client, you must prompt the user for the username and password and specify the user’s credentials on the WCF client proxy.</span></span>

## <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a><span data-ttu-id="8f2eb-111">Pour configurer un service WCF pour l’authentification à l’aide du nom d’utilisateur et du mot de passe de domaine Windows</span><span class="sxs-lookup"><span data-stu-id="8f2eb-111">To configure a WCF service to authenticate using Windows domain username and password</span></span>

1. <span data-ttu-id="8f2eb-112">Créez une instance de <xref:System.ServiceModel.WSHttpBinding>, définissez le mode de sécurité de liaison à <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType>, définissez le `ClientCredentialType` de liaison à <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType>, et ajoutez un point de terminaison de service à l'aide de la liaison configurée à l'hôte de service comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="8f2eb-112">Create an instance of the <xref:System.ServiceModel.WSHttpBinding>, set the security mode of the binding to <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType>, set the `ClientCredentialType` of the binding to <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType>, and add a service endpoint using the configured binding to the service host as shown in the following code:</span></span>

    ```csharp
    // ...
    var userNameBinding = new WSHttpBinding();
    userNameBinding.Security.Mode = SecurityMode.Message;
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");
    // ...
    ```

2. <span data-ttu-id="8f2eb-113">Spécifiez le certificat de serveur utilisé pour chiffrer les informations de nom d'utilisateur et mot de passe envoyées sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="8f2eb-113">Specify the server certificate used to encrypt the username and password information sent over the wire.</span></span> <span data-ttu-id="8f2eb-114">Ce code doit suivre immédiatement le code ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="8f2eb-114">This code should immediately follow the code above.</span></span> <span data-ttu-id="8f2eb-115">L’exemple suivant utilise le certificat créé par le fichier Setup. bat à partir de l’exemple de [nom d’utilisateur de sécurité de message](../samples/message-security-user-name.md) :</span><span class="sxs-lookup"><span data-stu-id="8f2eb-115">The following example uses the certificate that is created by the setup.bat file from the [Message Security User Name](../samples/message-security-user-name.md) sample:</span></span>

    ```csharp
    // ...
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");
    // ...
    ```

    <span data-ttu-id="8f2eb-116">Vous pouvez utiliser votre propre certificat ; il vous suffit de modifier le code pour faire référence à votre certificat.</span><span class="sxs-lookup"><span data-stu-id="8f2eb-116">You can use your own certificate, just modify the code to refer to your certificate.</span></span> <span data-ttu-id="8f2eb-117">Pour plus d’informations sur la création et l’utilisation de certificats, consultez [utilisation des certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="8f2eb-117">For more information about creating and using certificates see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="8f2eb-118">Assurez-vous que le certificat se trouve dans le magasin de certificats Personnes approuvées de l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8f2eb-118">Make sure the certificate is in the Trusted People certificate store for the Local Machine.</span></span> <span data-ttu-id="8f2eb-119">Pour ce faire, vous pouvez exécuter MMC. exe et sélectionner l’élément de menu **fichier**, **Ajouter/supprimer un composant logiciel enfichable..** ..</span><span class="sxs-lookup"><span data-stu-id="8f2eb-119">You can do this by running mmc.exe and selecting the **File**, **Add/Remove Snap-in...** menu item.</span></span> <span data-ttu-id="8f2eb-120">Dans la boîte de dialogue **Ajouter ou supprimer des composants logiciels enfichables** , sélectionnez le **composant logiciel enfichable Certificats** , puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="8f2eb-120">In the **Add or Remove Snap-ins** dialog, select the **Certificates snap-in** and click **Add**.</span></span> <span data-ttu-id="8f2eb-121">Dans la boîte de dialogue composant logiciel enfichable Certificats, sélectionnez **compte d’ordinateur**.</span><span class="sxs-lookup"><span data-stu-id="8f2eb-121">In the Certificates Snap-in dialog select **Computer account**.</span></span> <span data-ttu-id="8f2eb-122">Par défaut, le certificat généré à partir de l'exemple de nom d'utilisateur de sécurité du message se trouve dans le dossier Personal/Certificates.</span><span class="sxs-lookup"><span data-stu-id="8f2eb-122">By default the certificate generated from the Message Security User name sample will be located in the Personal/Certificates folder.</span></span>  <span data-ttu-id="8f2eb-123">Elle est indiquée comme « localhost » sous la colonne délivré à dans la fenêtre MMC.</span><span class="sxs-lookup"><span data-stu-id="8f2eb-123">It will be listed as "localhost" under the Issued to column in the MMC window.</span></span> <span data-ttu-id="8f2eb-124">Glissez-déposez le certificat dans le dossier **personnes autorisées** .</span><span class="sxs-lookup"><span data-stu-id="8f2eb-124">Drag and drop the certificate into the **Trusted People** folder.</span></span> <span data-ttu-id="8f2eb-125">Cela permettra à WCF de traiter le certificat comme un certificat approuvé lorsque vous effectuez l'authentification.</span><span class="sxs-lookup"><span data-stu-id="8f2eb-125">This will allow WCF to treat the certificate as a trusted certificate when performing authentication.</span></span>

## <a name="to-call-the-service-passing-username-and-password"></a><span data-ttu-id="8f2eb-126">Pour appeler le service en passant le nom d'utilisateur et le mot de passe</span><span class="sxs-lookup"><span data-stu-id="8f2eb-126">To call the service passing username and password</span></span>

1. <span data-ttu-id="8f2eb-127">L'application cliente doit demander à l'utilisateur d'entrer son nom d'utilisateur et son mot de passe.</span><span class="sxs-lookup"><span data-stu-id="8f2eb-127">The client application must prompt the user for their username and password.</span></span> <span data-ttu-id="8f2eb-128">Le code suivant demande à l’utilisateur le nom d’utilisateur et le mot de passe :</span><span class="sxs-lookup"><span data-stu-id="8f2eb-128">The following code asks the user for username and password:</span></span>

    > [!WARNING]
    > <span data-ttu-id="8f2eb-129">Ce code ne doit pas être utilisé en production, car le mot de passe s'affiche lorsqu'il est entré.</span><span class="sxs-lookup"><span data-stu-id="8f2eb-129">This code should not be used in production as the password is displayed while being entered.</span></span>

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

2. <span data-ttu-id="8f2eb-130">Créez une instance du proxy client en spécifiant les informations d’identification du client, comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="8f2eb-130">Create an instance of the client proxy specifying the client's credentials as shown in the following code:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8f2eb-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f2eb-131">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.SecurityMode>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>
- <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>
- [<span data-ttu-id="8f2eb-132">Sécurité de transport avec authentification de base</span><span class="sxs-lookup"><span data-stu-id="8f2eb-132">Transport Security with Basic Authentication</span></span>](transport-security-with-basic-authentication.md)
- [<span data-ttu-id="8f2eb-133">Sécurité des applications distribuées</span><span class="sxs-lookup"><span data-stu-id="8f2eb-133">Distributed Application Security</span></span>](distributed-application-security.md)
- [<span data-ttu-id="8f2eb-134">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="8f2eb-134">\<wsHttpBinding></span></span>](../../configure-apps/file-schema/wcf/wshttpbinding.md)
