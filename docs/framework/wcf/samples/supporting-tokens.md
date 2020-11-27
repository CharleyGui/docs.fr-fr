---
title: Supporting Tokens
ms.date: 03/30/2017
ms.assetid: 65a8905d-92cc-4ab0-b6ed-1f710e40784e
ms.openlocfilehash: d7e2a824060f4be05e0b0e9d1765fcf271eacbd3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293661"
---
# <a name="supporting-tokens"></a><span data-ttu-id="f5deb-102">Supporting Tokens</span><span class="sxs-lookup"><span data-stu-id="f5deb-102">Supporting Tokens</span></span>

<span data-ttu-id="f5deb-103">Cet exemple montre comment ajouter des jetons supplémentaires à un message qui utilise WS-Security.</span><span class="sxs-lookup"><span data-stu-id="f5deb-103">The Supporting Tokens sample demonstrates how to add additional tokens to a message that uses WS-Security.</span></span> <span data-ttu-id="f5deb-104">L'exemple ajoute un jeton de sécurité binaire X.509 outre un jeton de sécurité de nom d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f5deb-104">The example adds an X.509 binary security token in addition to a username security token.</span></span> <span data-ttu-id="f5deb-105">Le jeton est passé dans un en-tête de message WS-Security du client au service et une partie du message est signée avec la clé privée associée au jeton de sécurité X.509 pour prouver la possession du certificat X.509 au récepteur.</span><span class="sxs-lookup"><span data-stu-id="f5deb-105">The token is passed in a WS-Security message header from the client to the service and part of the message is signed with the private key associated with the X.509 security token to prove the possession of the X.509 certificate to the receiver.</span></span> <span data-ttu-id="f5deb-106">Cela s’avère utile dans le cas où plusieurs revendications doivent être associées à un message pour authentifier ou autoriser l’expéditeur.</span><span class="sxs-lookup"><span data-stu-id="f5deb-106">This is useful in the case when there is a requirement to have multiple claims associated with a message to authenticate or authorize the sender.</span></span> <span data-ttu-id="f5deb-107">Le service implémente un contrat qui définit un modèle de communication demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="f5deb-107">The service implements a contract that defines a request-reply communication pattern.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="f5deb-108">Illustre le</span><span class="sxs-lookup"><span data-stu-id="f5deb-108">Demonstrates</span></span>

 <span data-ttu-id="f5deb-109">L'exemple montre :</span><span class="sxs-lookup"><span data-stu-id="f5deb-109">The sample demonstrates:</span></span>

- <span data-ttu-id="f5deb-110">Comment un client peut passer des jetons de sécurité supplémentaires à un service.</span><span class="sxs-lookup"><span data-stu-id="f5deb-110">How a client can pass additional security tokens to a service.</span></span>

- <span data-ttu-id="f5deb-111">Comment le serveur peut accéder aux revendications associées aux jetons de sécurité supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="f5deb-111">How the server can access claims associated with additional security tokens.</span></span>

- <span data-ttu-id="f5deb-112">Comment le certificat X.509 du serveur permet de protéger la clé symétrique utilisée pour la signature et le chiffrement des messages.</span><span class="sxs-lookup"><span data-stu-id="f5deb-112">How the server's X.509 certificate is used to protect the symmetric key used for message encryption and signature.</span></span>

> [!NOTE]
> <span data-ttu-id="f5deb-113">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="f5deb-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

## <a name="client-authenticates-with-username-token-and-supporting-x509-security-token"></a><span data-ttu-id="f5deb-114">Le client s'authentifie à l'aide du jeton de nom d'utilisateur et du jeton de sécurité X.509 de prise en charge</span><span class="sxs-lookup"><span data-stu-id="f5deb-114">Client Authenticates with Username Token and Supporting X.509 Security Token</span></span>

 <span data-ttu-id="f5deb-115">Le service expose un point de terminaison unique de communication qui est créé par programme à l'aide des classes `BindingHelper` et `EchoServiceHost`.</span><span class="sxs-lookup"><span data-stu-id="f5deb-115">The service exposes a single endpoint for communicating that is programmatically created using the `BindingHelper` and `EchoServiceHost` classes.</span></span> <span data-ttu-id="f5deb-116">Le point de terminaison se compose d'une adresse, d'une liaison et d'un contrat.</span><span class="sxs-lookup"><span data-stu-id="f5deb-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="f5deb-117">La liaison est configurée avec une liaison personnalisé à l'aide de `SymmetricSecurityBindingElement` et `HttpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="f5deb-117">The binding is configured with a custom binding using `SymmetricSecurityBindingElement` and `HttpTransportBindingElement`.</span></span> <span data-ttu-id="f5deb-118">Cet exemple oblige `SymmetricSecurityBindingElement` à utiliser un certificat X.509 du service pour protéger la clé symétrique pendant la transmission et à passer un `UserNameToken` avec le `X509SecurityToken` de prise en charge dans un en-tête de message WS-Security.</span><span class="sxs-lookup"><span data-stu-id="f5deb-118">This sample sets the `SymmetricSecurityBindingElement` to use a service X.509 certificate to protect the symmetric key during transmission and to pass a `UserNameToken` along with the supporting `X509SecurityToken` in a WS-Security message header.</span></span> <span data-ttu-id="f5deb-119">La clé symétrique permet de chiffrer le corps du message et le jeton de sécurité de nom d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f5deb-119">The symmetric key is used to encrypt the message body and the username security token.</span></span> <span data-ttu-id="f5deb-120">Le jeton de prise en charge est passé comme jeton de sécurité binaire supplémentaire dans l'en-tête de message WS-Security.</span><span class="sxs-lookup"><span data-stu-id="f5deb-120">The supporting token is passed as an additional binary security token in the WS-Security message header.</span></span> <span data-ttu-id="f5deb-121">L'authenticité du jeton de prise en charge est prouvée en signant une partie du message avec la clé privée associée au jeton de sécurité X.509 de prise en charge.</span><span class="sxs-lookup"><span data-stu-id="f5deb-121">The authenticity of the supporting token is proved by signing part of the message with the private key associated with the supporting X.509 security token.</span></span>

```csharp
public static Binding CreateMultiFactorAuthenticationBinding()
{
    HttpTransportBindingElement httpTransport = new HttpTransportBindingElement();

    // the message security binding element will be configured to require 2 tokens:
    // 1) A username-password encrypted with the service token
    // 2) A client certificate used to sign the message

    // Instantiate a binding element that will require the username/password token in the message (encrypted with the server cert)
    SymmetricSecurityBindingElement messageSecurity = SecurityBindingElement.CreateUserNameForCertificateBindingElement();

    // Create supporting token parameters for the client X509 certificate.
    X509SecurityTokenParameters clientX509SupportingTokenParameters = new X509SecurityTokenParameters();
    // Specify that the supporting token is passed in message send by the client to the service
    clientX509SupportingTokenParameters.InclusionMode = SecurityTokenInclusionMode.AlwaysToRecipient;
    // Turn off derived keys
    clientX509SupportingTokenParameters.RequireDerivedKeys = false;
    // Augment the binding element to require the client's X509 certificate as an endorsing token in the message
    messageSecurity.EndpointSupportingTokenParameters.Endorsing.Add(clientX509SupportingTokenParameters);

    // Create a CustomBinding based on the constructed security binding element.
    return new CustomBinding(messageSecurity, httpTransport);
}
```

 <span data-ttu-id="f5deb-122">Le comportement spécifie les informations d'identification du service qui doivent être utilisées pour l'authentification du client ainsi que les informations sur le certificat X.509 du service.</span><span class="sxs-lookup"><span data-stu-id="f5deb-122">The behavior specifies the service credentials that are to be used for client authentication and also information about the service X.509 certificate.</span></span> <span data-ttu-id="f5deb-123">L'exemple utilise `CN=localhost` comme nom du sujet dans le certificat X.509 du service.</span><span class="sxs-lookup"><span data-stu-id="f5deb-123">The sample uses `CN=localhost` as a subject name in the service X.509 certificate.</span></span>

```csharp
override protected void InitializeRuntime()
{
    // Extract the ServiceCredentials behavior or create one.
    ServiceCredentials serviceCredentials =
        this.Description.Behaviors.Find<ServiceCredentials>();
    if (serviceCredentials == null)
    {
        serviceCredentials = new ServiceCredentials();
        this.Description.Behaviors.Add(serviceCredentials);
    }

    // Set the service certificate
    serviceCredentials.ServiceCertificate.SetCertificate(
                                       "CN=localhost");

/*
Setting the CertificateValidationMode to PeerOrChainTrust means that if the certificate is in the Trusted People store, then it will be trusted without performing a validation of the certificate's issuer chain. This setting is used here for convenience so that the sample can be run without having to have certificates issued by a certification authority (CA).
This setting is less secure than the default, ChainTrust. The security implications of this setting should be carefully considered before using PeerOrChainTrust in production code.
*/
    serviceCredentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;

    // Create the custom binding and add an endpoint to the service.
    Binding multipleTokensBinding =
         BindingHelper.CreateMultiFactorAuthenticationBinding();
    this.AddServiceEndpoint(typeof(IEchoService),
                          multipleTokensBinding, string.Empty);
    base.InitializeRuntime();
}
```

 <span data-ttu-id="f5deb-124">Code de service :</span><span class="sxs-lookup"><span data-stu-id="f5deb-124">Service code:</span></span>

```csharp
[ServiceBehavior(IncludeExceptionDetailInFaults = true)]
public class EchoService : IEchoService
{
    public string Echo()
    {
        string userName;
        string certificateSubjectName;
        GetCallerIdentities(
            OperationContext.Current.ServiceSecurityContext,
            out userName,
            out certificateSubjectName);
            return $"Hello {userName}, {certificateSubjectName}";
    }

    public void Dispose()
    {
    }

    bool TryGetClaimValue<TClaimResource>(ClaimSet claimSet,
            string claimType, out TClaimResource resourceValue)
            where TClaimResource : class
    {
        resourceValue = default(TClaimResource);
        IEnumerable<Claim> matchingClaims =
            claimSet.FindClaims(claimType, Rights.PossessProperty);
        if(matchingClaims == null)
            return false;
        IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();
        if (enumerator.MoveNext())
        {
            resourceValue =
              (enumerator.Current.Resource == null) ? null :
              (enumerator.Current.Resource as TClaimResource);
            return true;
        }
        else
        {
            return false;
        }
    }

    // Returns the username and certificate subject name provided by
    //the client
    void GetCallerIdentities(ServiceSecurityContext
        callerSecurityContext,
        out string userName, out string certificateSubjectName)
    {
        userName = null;
        certificateSubjectName = null;

       // Look in all the claimsets in the authorization context
       foreach (ClaimSet claimSet in
               callerSecurityContext.AuthorizationContext.ClaimSets)
       {
            if (claimSet is WindowsClaimSet)
            {
                // Try to find a Name claim. This will have been
                // generated from the windows username.
                string tmpName;
                if (TryGetClaimValue<string>(claimSet, ClaimTypes.Name,
                                                      out tmpName))
                {
                    userName = tmpName;
                }
            }
            else if (claimSet is X509CertificateClaimSet)
            {
                // Try to find an X500DistinguishedName claim. This will
                // have been generated from the client certificate.
                X500DistinguishedName tmpDistinguishedName;
                if (TryGetClaimValue<X500DistinguishedName>(claimSet,
                               ClaimTypes.X500DistinguishedName,
                               out tmpDistinguishedName))
                {
                    certificateSubjectName = tmpDistinguishedName.Name;
                }
            }
        }
    }
}
```

 <span data-ttu-id="f5deb-125">Le point de terminaison client est configuré de la même manière que le point de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="f5deb-125">The client endpoint is configured in a similar way to the service endpoint.</span></span> <span data-ttu-id="f5deb-126">Le client utilise une classe `BindingHelper` identique pour créer sa liaison.</span><span class="sxs-lookup"><span data-stu-id="f5deb-126">The client uses the same `BindingHelper` class to create a binding.</span></span> <span data-ttu-id="f5deb-127">La suite de la configuration s'effectue dans classe `Client`.</span><span class="sxs-lookup"><span data-stu-id="f5deb-127">The rest of the setup is located in `Client` class.</span></span> <span data-ttu-id="f5deb-128">Le client définit les formations sur le jeton de sécurité de nom d’utilisateur, le jeton de sécurité X.509 de prise en charge et les informations sur le certificat X.509 du service dans le code d’installation vers la collection de comportements de point de terminaison client.</span><span class="sxs-lookup"><span data-stu-id="f5deb-128">The client sets information about the user name security token, the supporting X.509 security token and information about the service X.509 certificate in the setup code to the client endpoint behaviors collection.</span></span>

```csharp
 static void Main()
 {
     // Create the custom binding and an endpoint address for
     // the service.
     Binding multipleTokensBinding =
         BindingHelper.CreateMultiFactorAuthenticationBinding();
         EndpointAddress serviceAddress = new EndpointAddress(
         "http://localhost/servicemodelsamples/service.svc");
       ChannelFactory<IEchoService> channelFactory = null;
       IEchoService client = null;

       Console.WriteLine("Username authentication required.");
       Console.WriteLine(
         "Provide a valid machine or domain account. [domain\\user]");
       Console.WriteLine("   Enter username:");
       string username = Console.ReadLine();
       Console.WriteLine("   Enter password:");
       string password = "";
       ConsoleKeyInfo info = Console.ReadKey(true);
       while (info.Key != ConsoleKey.Enter)
       {
           if (info.Key != ConsoleKey.Backspace)
           {
               if (info.KeyChar != '\0')
               {
                   password += info.KeyChar;
                }
                info = Console.ReadKey(true);
            }
            else if (info.Key == ConsoleKey.Backspace)
            {
                if (password != "")
                {
                    password =
                       password.Substring(0, password.Length - 1);
                }
                info = Console.ReadKey(true);
            }
         }
         for (int i = 0; i < password.Length; i++)
            Console.Write("*");
         Console.WriteLine();
         try
         {
           // Create a proxy with the previously create binding and
           // endpoint address
              channelFactory =
                 new ChannelFactory<IEchoService>(
                     multipleTokensBinding, serviceAddress);
           // configure the username credentials, the client
           // certificate and the server certificate on the channel
           // factory
           channelFactory.Credentials.UserName.UserName = username;
           channelFactory.Credentials.UserName.Password = password;
           channelFactory.Credentials.ClientCertificate.SetCertificate(
           "CN=client.com", StoreLocation.CurrentUser, StoreName.My);
              channelFactory.Credentials.ServiceCertificate.SetDefaultCertificate(
           "CN=localhost", StoreLocation.LocalMachine, StoreName.My);
           client = channelFactory.CreateChannel();
           Console.WriteLine("Echo service returned: {0}",
                                           client.Echo());

           ((IChannel)client).Close();
           channelFactory.Close();
        }
        catch (CommunicationException e)
        {
         Abort((IChannel)client, channelFactory);
         // if there is a fault then print it out
         FaultException fe = null;
         Exception tmp = e;
         while (tmp != null)
         {
            fe = tmp as FaultException;
            if (fe != null)
            {
                break;
            }
            tmp = tmp.InnerException;
        }
        if (fe != null)
        {
           Console.WriteLine("The server sent back a fault: {0}",
         fe.CreateMessageFault().Reason.GetMatchingTranslation().Text);
        }
        else
        {
         Console.WriteLine("The request failed with exception: {0}",e);
        }
    }
    catch (TimeoutException)
    {
        Abort((IChannel)client, channelFactory);
        Console.WriteLine("The request timed out");
    }
    catch (Exception e)
    {
         Abort((IChannel)client, channelFactory);
          Console.WriteLine(
          "The request failed with unexpected exception: {0}", e);
    }
    Console.WriteLine();
    Console.WriteLine("Press <ENTER> to terminate client.");
    Console.ReadLine();
}
```

## <a name="displaying-callers-information"></a><span data-ttu-id="f5deb-129">Affichage des informations sur les appelants</span><span class="sxs-lookup"><span data-stu-id="f5deb-129">Displaying Callers' Information</span></span>

 <span data-ttu-id="f5deb-130">Pour afficher les informations sur l'appelant, vous pouvez utiliser `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets`, tel qu'indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="f5deb-130">To display the caller's information, you can use the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` as shown in the following code.</span></span> <span data-ttu-id="f5deb-131">`ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contient les revendications d'autorisation associées à l'appelant actuel.</span><span class="sxs-lookup"><span data-stu-id="f5deb-131">The `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contains authorization claims associated with the current caller.</span></span> <span data-ttu-id="f5deb-132">Ces revendications sont fournies automatiquement par Windows Communication Foundation (WCF) pour chaque jeton reçu dans le message.</span><span class="sxs-lookup"><span data-stu-id="f5deb-132">Those claims are supplied automatically by Windows Communication Foundation (WCF) for every token received in the message.</span></span>

```csharp
bool TryGetClaimValue<TClaimResource>(ClaimSet claimSet, string
                         claimType, out TClaimResource resourceValue)
    where TClaimResource : class
{
    resourceValue = default(TClaimResource);
    IEnumerable<Claim> matchingClaims =
    claimSet.FindClaims(claimType, Rights.PossessProperty);
    if (matchingClaims == null)
          return false;
    IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();
    if (enumerator.MoveNext())
    {
        resourceValue = (enumerator.Current.Resource == null) ? null : (enumerator.Current.Resource as TClaimResource);
        return true;
    }
    else
    {
         return false;
    }
}

// Returns the username and certificate subject name provided by the client
void GetCallerIdentities(ServiceSecurityContext callerSecurityContext, out string userName, out string certificateSubjectName)
{
    userName = null;
    certificateSubjectName = null;

    // Look in all the claimsets in the authorization context
    foreach (ClaimSet claimSet in
      callerSecurityContext.AuthorizationContext.ClaimSets)
    {
        if (claimSet is WindowsClaimSet)
        {
            // Try to find a Name claim. This will have been generated
            //from the windows username.
            string tmpName;
            if (TryGetClaimValue<string>(claimSet, ClaimTypes.Name,
                                                     out tmpName))
            {
                userName = tmpName;
            }
        }
        else if (claimSet is X509CertificateClaimSet)
         {
            //Try to find an X500DistinguishedName claim.
            //This will have been generated from the client
            //certificate.
            X500DistinguishedName tmpDistinguishedName;
            if (TryGetClaimValue<X500DistinguishedName>(claimSet,
               ClaimTypes.X500DistinguishedName,
               out tmpDistinguishedName))
            {
                    certificateSubjectName = tmpDistinguishedName.Name;
            }
        }
    }
}
```

## <a name="running-the-sample"></a><span data-ttu-id="f5deb-133">Exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="f5deb-133">Running the Sample</span></span>

 <span data-ttu-id="f5deb-134">Lorsque vous exécutez l'exemple, le client vous invite d'abord à fournir un nom d'utilisateur et un mot de passe pour le jeton de nom d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f5deb-134">When you run the sample, the client first prompts you to provide user name and password for the user name token.</span></span> <span data-ttu-id="f5deb-135">Veillez à fournir les valeurs correctes pour votre compte système, car WCF sur le service mappe les valeurs fournies dans le jeton de nom d’utilisateur à l’identité fournie par le système.</span><span class="sxs-lookup"><span data-stu-id="f5deb-135">Be sure to provide correct values for your system account, because WCF on the service maps the values supplied in the user name token into the identity provided by the system.</span></span> <span data-ttu-id="f5deb-136">Ceci fait, le client affiche la réponse provenant du service.</span><span class="sxs-lookup"><span data-stu-id="f5deb-136">After that, the client displays the response from the service.</span></span> <span data-ttu-id="f5deb-137">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="f5deb-137">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="f5deb-138">Fichier de commandes d'installation</span><span class="sxs-lookup"><span data-stu-id="f5deb-138">Setup Batch File</span></span>

 <span data-ttu-id="f5deb-139">Le fichier de commandes Setup.bat inclus avec cet exemple vous permet de configurer le serveur avec les certificats appropriés pour exécuter l'application hébergée IIS (Internet Information Services) qui requiert une sécurité basée sur le certificat du serveur.</span><span class="sxs-lookup"><span data-stu-id="f5deb-139">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run Internet Information Services (IIS) hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="f5deb-140">Ce fichier de commandes doit être modifié pour fonctionner sur plusieurs ordinateurs ou sans hébergement.</span><span class="sxs-lookup"><span data-stu-id="f5deb-140">This batch file must be modified to work across machines or to work in a non-hosted case.</span></span>

 <span data-ttu-id="f5deb-141">Les éléments suivants fournissent une vue d'ensemble des différentes sections des fichiers de commandes afin qu'ils puissent être modifiés pour s'exécuter dans la configuration appropriée.</span><span class="sxs-lookup"><span data-stu-id="f5deb-141">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration.</span></span>

### <a name="creating-the-client-certificate"></a><span data-ttu-id="f5deb-142">Création du certificat client</span><span class="sxs-lookup"><span data-stu-id="f5deb-142">Creating the Client Certificate</span></span>

 <span data-ttu-id="f5deb-143">Les lignes suivantes du fichier de commandes Setup.bat créent le certificat client à utiliser.</span><span class="sxs-lookup"><span data-stu-id="f5deb-143">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="f5deb-144">La variable `%CLIENT_NAME%` spécifie le sujet du certificat client.</span><span class="sxs-lookup"><span data-stu-id="f5deb-144">The `%CLIENT_NAME%` variable specifies the subject of the client certificate.</span></span> <span data-ttu-id="f5deb-145">Cet exemple utilise "client.com" comme nom du sujet.</span><span class="sxs-lookup"><span data-stu-id="f5deb-145">This sample uses "client.com" as the subject name.</span></span>

 <span data-ttu-id="f5deb-146">Le certificat est stocké dans le magasin My (personnel) sous l'emplacement de magasin `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="f5deb-146">The certificate is stored in My (Personal) store under the `CurrentUser` store location.</span></span>

```console
echo ************
echo making client cert
echo ************
makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
```

### <a name="installing-the-client-certificate-into-the-servers-trusted-store"></a><span data-ttu-id="f5deb-147">Installation du certificat client dans le magasin approuvé du serveur :</span><span class="sxs-lookup"><span data-stu-id="f5deb-147">Installing the Client Certificate into the Server's Trusted Store</span></span>

 <span data-ttu-id="f5deb-148">La ligne suivante du fichier de commandes Setup.bat copie le certificat client dans le magasin de personnes de confiance du serveur.</span><span class="sxs-lookup"><span data-stu-id="f5deb-148">The following line in the Setup.bat batch file copies the client certificate into the server’s trusted people store.</span></span> <span data-ttu-id="f5deb-149">Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système du serveur.</span><span class="sxs-lookup"><span data-stu-id="f5deb-149">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the server’s system.</span></span> <span data-ttu-id="f5deb-150">Si vous disposez déjà d'un certificat associé à un certificat racine approuvé du client, par exemple un certificat émis par Microsoft, cette étape de remplissage du magasin de certificats client avec le certificat de serveur n'est pas requise.</span><span class="sxs-lookup"><span data-stu-id="f5deb-150">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

```console
echo ************
echo copying client cert to server's CurrentUserstore
echo ************
certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
```

### <a name="creating-the-server-certificate"></a><span data-ttu-id="f5deb-151">Création du certificat de serveur</span><span class="sxs-lookup"><span data-stu-id="f5deb-151">Creating the Server Certificate</span></span>

 <span data-ttu-id="f5deb-152">Les lignes suivantes du fichier de commandes Setup.bat créent le certificat de serveur à utiliser.</span><span class="sxs-lookup"><span data-stu-id="f5deb-152">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="f5deb-153">La variable `%SERVER_NAME%` spécifie le nom du serveur.</span><span class="sxs-lookup"><span data-stu-id="f5deb-153">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="f5deb-154">Modifiez cette variable pour spécifier votre propre nom de serveur.</span><span class="sxs-lookup"><span data-stu-id="f5deb-154">Change this variable to specify your own server name.</span></span> <span data-ttu-id="f5deb-155">La valeur par défaut dans ce fichier de commandes est localhost.</span><span class="sxs-lookup"><span data-stu-id="f5deb-155">The default in this batch file is localhost.</span></span>

 <span data-ttu-id="f5deb-156">Le certificat est stocké dans le magasin My (personnel) sous l'emplacement de magasins LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="f5deb-156">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span> <span data-ttu-id="f5deb-157">Le certificat est stocké dans le magasin LocalMachine pour les services hébergés par IIS.</span><span class="sxs-lookup"><span data-stu-id="f5deb-157">The certificate is stored in the LocalMachine store for the IIS-hosted services.</span></span> <span data-ttu-id="f5deb-158">Pour les services auto-hébergés, vous devez modifier le fichier de commandes afin de stocker le certificat de serveur dans l'emplacement de magasin CurrentUser en remplaçant la chaîne LocalMachine par CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="f5deb-158">For self-hosted services, you should modify the batch file to store the server certificate in the CurrentUser store location by replacing the string LocalMachine with CurrentUser.</span></span>

```console
echo ************
echo Server cert setup starting
echo %SERVER_NAME%
echo ************
echo making server cert
echo ************
makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
```

### <a name="installing-server-certificate-into-clients-trusted-certificate-store"></a><span data-ttu-id="f5deb-159">Installation du certificat de serveur dans le magasin de certificats approuvé du client :</span><span class="sxs-lookup"><span data-stu-id="f5deb-159">Installing Server Certificate into Client's Trusted Certificate Store</span></span>

 <span data-ttu-id="f5deb-160">Les lignes suivantes du fichier de commandes Setup.bat copient le certificat de serveur dans le magasin de personnes de confiance du client.</span><span class="sxs-lookup"><span data-stu-id="f5deb-160">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="f5deb-161">Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système client.</span><span class="sxs-lookup"><span data-stu-id="f5deb-161">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="f5deb-162">Si vous disposez déjà d'un certificat associé à un certificat racine approuvé du client, par exemple un certificat émis par Microsoft, cette étape de remplissage du magasin de certificats client avec le certificat de serveur n'est pas requise.</span><span class="sxs-lookup"><span data-stu-id="f5deb-162">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

```console
echo ************
echo copying server cert to client's TrustedPeople store
echo ************certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
```

### <a name="enabling-access-to-the-certificates-private-key"></a><span data-ttu-id="f5deb-163">Activation de l'accès à la clé privée du certificat</span><span class="sxs-lookup"><span data-stu-id="f5deb-163">Enabling Access to the Certificate's Private Key</span></span>

 <span data-ttu-id="f5deb-164">Pour activer l'accès à la clé privée du certificat à partir du service hébergé par IIS, le compte d'utilisateur sous lequel le processus hébergé par IIS s'exécute doit disposer des autorisations permettant d'y accéder.</span><span class="sxs-lookup"><span data-stu-id="f5deb-164">To enable access to the certificate private key from the IIS-hosted service, the user account under which the IIS-hosted process is running must be granted appropriate permissions for the private key.</span></span> <span data-ttu-id="f5deb-165">Cette opération est effectuée par les dernières étapes du script Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="f5deb-165">This is accomplished by last steps in the Setup.bat script.</span></span>

```console
echo ************
echo setting privileges on server certificates
echo ************
for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i
set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE
(ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET
echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R
iisreset
```

##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f5deb-166">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="f5deb-166">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="f5deb-167">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f5deb-167">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="f5deb-168">Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f5deb-168">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="f5deb-169">Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, utilisez les instructions suivantes.</span><span class="sxs-lookup"><span data-stu-id="f5deb-169">To run the sample in a single- or cross-machine configuration, use the following instructions.</span></span>

##### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="f5deb-170">Pour exécuter l'exemple sur le même ordinateur</span><span class="sxs-lookup"><span data-stu-id="f5deb-170">To run the sample on the same machine</span></span>

1. <span data-ttu-id="f5deb-171">Exécutez Setup.bat à partir du dossier d’installation de l’exemple à l’aide de l’invite de commandes de Visual Studio 2012 avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="f5deb-171">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt run with administrator privileges.</span></span> <span data-ttu-id="f5deb-172">Tous les certificats requis à l'exécution de l'exemple sont ainsi installés.</span><span class="sxs-lookup"><span data-stu-id="f5deb-172">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f5deb-173">Le fichier de commandes Setup.bat est conçu pour être exécuté à partir d’une invite de commandes de Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="f5deb-173">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="f5deb-174">La variable d’environnement PATH définie dans l’invite de commandes de Visual Studio 2012 pointe vers le répertoire qui contient les exécutables requis par le script Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="f5deb-174">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span> <span data-ttu-id="f5deb-175">Assurez-vous de supprimer les certificats en exécutant Cleanup.bat une fois l'exemple terminé.</span><span class="sxs-lookup"><span data-stu-id="f5deb-175">Be sure to remove the certificates by running Cleanup.bat when finished with the sample.</span></span> <span data-ttu-id="f5deb-176">D'autres exemples de sécurité utilisent ces mêmes certificats.</span><span class="sxs-lookup"><span data-stu-id="f5deb-176">Other security samples use the same certificates.</span></span>  
  
2. <span data-ttu-id="f5deb-177">Lancez Client.exe à partir de \client\bin.</span><span class="sxs-lookup"><span data-stu-id="f5deb-177">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="f5deb-178">L'activité du client s'affiche sur son application de console.</span><span class="sxs-lookup"><span data-stu-id="f5deb-178">Client activity is displayed on the client console application.</span></span>  
  
3. <span data-ttu-id="f5deb-179">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="f5deb-179">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
##### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="f5deb-180">Pour exécuter l'exemple sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="f5deb-180">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="f5deb-181">Créez un répertoire sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="f5deb-181">Create a directory on the service machine.</span></span> <span data-ttu-id="f5deb-182">Créez une application virtuelle appelée servicemodelsamples pour ce répertoire à l'aide de l'outil de gestion IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="f5deb-182">Create a virtual application named servicemodelsamples for this directory using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="f5deb-183">Copiez les fichiers du programme de service figurant dans le dossier \inetpub\wwwroot\servicemodelsamples dans ce répertoire virtuel.</span><span class="sxs-lookup"><span data-stu-id="f5deb-183">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service machine.</span></span> <span data-ttu-id="f5deb-184">Assurez-vous de copier les fichiers dans le sous-répertoire \bin.</span><span class="sxs-lookup"><span data-stu-id="f5deb-184">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="f5deb-185">Copiez également les fichiers Setup.bat, Cleanup.bat et ImportClientCert.bat sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="f5deb-185">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service machine.</span></span>  
  
3. <span data-ttu-id="f5deb-186">Créez un répertoire sur l'ordinateur client pour les fichiers binaires du client.</span><span class="sxs-lookup"><span data-stu-id="f5deb-186">Create a directory on the client machine for the client binaries.</span></span>  
  
4. <span data-ttu-id="f5deb-187">Copiez les fichiers programme du client dans le répertoire client de l'ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="f5deb-187">Copy the client program files to the client directory on the client machine.</span></span> <span data-ttu-id="f5deb-188">Copiez également les fichiers Setup.bat, Cleanup.bat et ImportServiceCert.bat sur le client.</span><span class="sxs-lookup"><span data-stu-id="f5deb-188">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="f5deb-189">Sur le serveur, exécutez `setup.bat service` dans un invite de commandes développeur pour Visual Studio ouvert avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="f5deb-189">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="f5deb-190">`setup.bat`L’exécution avec l' `service` argument crée un certificat de service avec le nom de domaine complet de l’ordinateur et exporte le certificat de service dans un fichier nommé service. cer.</span><span class="sxs-lookup"><span data-stu-id="f5deb-190">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="f5deb-191">Modifiez Web.config pour refléter le nouveau nom de certificat (dans l' `findValue` attribut dans [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ) qui est le même que le nom de domaine complet de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f5deb-191">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the machine.</span></span>  
  
7. <span data-ttu-id="f5deb-192">Copiez le fichier Service.cer du répertoire de service dans le répertoire client sur l'ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="f5deb-192">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
8. <span data-ttu-id="f5deb-193">Sur le client, exécutez `setup.bat client` dans un invite de commandes développeur pour Visual Studio ouvert avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="f5deb-193">On the client, run `setup.bat client` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="f5deb-194">L'exécution de `setup.bat` à l'aide de l'argument `client` crée un certificat client appelé client.com, puis exporte ce certificat vers un fichier nommé Client.cer.</span><span class="sxs-lookup"><span data-stu-id="f5deb-194">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="f5deb-195">Dans le fichier Client.exe.config sur l'ordinateur client, modifiez la valeur d'adresse du point de terminaison pour qu'il corresponde à la nouvelle adresse de votre service.</span><span class="sxs-lookup"><span data-stu-id="f5deb-195">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="f5deb-196">Pour ce faire, remplacez localhost par le nom de domaine complet du serveur.</span><span class="sxs-lookup"><span data-stu-id="f5deb-196">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="f5deb-197">Copiez le fichier Client.cer du répertoire client dans le répertoire de service sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="f5deb-197">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="f5deb-198">Sur le client, exécutez ImportServiceCert.bat.</span><span class="sxs-lookup"><span data-stu-id="f5deb-198">On the client, run ImportServiceCert.bat.</span></span> <span data-ttu-id="f5deb-199">Cette opération importe le certificat de service du fichier Service.cer dans le magasin CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="f5deb-199">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="f5deb-200">Sur le serveur, exécutez ImportClientCert.bat. Cette opération importe le certificat client du fichier Client.cer dans le magasin LocalMachine - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="f5deb-200">On the server, run ImportClientCert.bat, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="f5deb-201">Sur l'ordinateur du client, lancez Client.exe à partir d'une fenêtre d'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="f5deb-201">On the client machine, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="f5deb-202">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="f5deb-202">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
##### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="f5deb-203">Pour procéder au nettoyage après exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="f5deb-203">To clean up after the sample</span></span>  
  
- <span data-ttu-id="f5deb-204">Exécutez Cleanup.bat dans le dossier d'exemples après avoir exécuté l'exemple.</span><span class="sxs-lookup"><span data-stu-id="f5deb-204">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f5deb-205">Ce script ne supprime pas les certificats de service figurant sur le client lorsque l'exemple est exécuté sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="f5deb-205">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="f5deb-206">Si vous avez exécuté des exemples WCF qui utilisent des certificats sur des ordinateurs, veillez à effacer les certificats de service qui ont été installés dans le magasin CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="f5deb-206">If you have run WCF samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="f5deb-207">Pour ce faire, utilisez la commande suivante : `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`, par exemple : `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="f5deb-207">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
