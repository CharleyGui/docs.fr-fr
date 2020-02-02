---
title: Service Identity, exemple
ms.date: 03/30/2017
ms.assetid: 79fa8c1c-85bb-4b67-bc67-bfaf721303f8
ms.openlocfilehash: 868bd6e0ac7429224462c973c1c48132ec3860ba
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76919366"
---
# <a name="service-identity-sample"></a><span data-ttu-id="73ced-102">Service Identity, exemple</span><span class="sxs-lookup"><span data-stu-id="73ced-102">Service Identity Sample</span></span>
<span data-ttu-id="73ced-103">Cet exemple montre comment définir l'identité d'un service.</span><span class="sxs-lookup"><span data-stu-id="73ced-103">This service identity sample demonstrates how to set the identity for a service.</span></span> <span data-ttu-id="73ced-104">Au moment du design, un client peut récupérer l'identité à l'aide des métadonnées du service, puis au miment de l'exécution, il peut authentifier l'identité du service.</span><span class="sxs-lookup"><span data-stu-id="73ced-104">At design time, a client can retrieve the identity using the service's metadata and then at runtime the client can authenticate the service's identity.</span></span> <span data-ttu-id="73ced-105">Le concept d'identité de service consiste à permettre à un client d'authentifier un service avant d'appeler l'une de ses opérations, ce qui protège le client contre les appels non authentifiés.</span><span class="sxs-lookup"><span data-stu-id="73ced-105">The concept of service identity is to allow a client to authenticate a service before calling any of its operations, thereby protecting the client from unauthenticated calls.</span></span> <span data-ttu-id="73ced-106">Sur une connexion sécurisée, le service authentifie également les informations d'identification d'un client avant de lui autoriser l'accès, mais ce n'est pas l'objet traité dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="73ced-106">On a secure connection the service also authenticates a client's credentials before allowing it access, but this is not the focus of this sample.</span></span> <span data-ttu-id="73ced-107">Consultez les exemples du [client](../../../../docs/framework/wcf/samples/client.md) qui affichent l’authentification du serveur.</span><span class="sxs-lookup"><span data-stu-id="73ced-107">See the samples in [Client](../../../../docs/framework/wcf/samples/client.md) that show server authentication.</span></span>

> [!NOTE]
> <span data-ttu-id="73ced-108">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="73ced-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="73ced-109">Cet exemple illustre les fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="73ced-109">This sample illustrates the following features:</span></span>

- <span data-ttu-id="73ced-110">Comment définir les divers types d'identité sur différents points de terminaison d'un service.</span><span class="sxs-lookup"><span data-stu-id="73ced-110">How to set the different types of identity on different endpoints for a service.</span></span> <span data-ttu-id="73ced-111">Chaque type d'identité possède des fonctionnalités différentes.</span><span class="sxs-lookup"><span data-stu-id="73ced-111">Each type of identity has different capabilities.</span></span> <span data-ttu-id="73ced-112">Le type d'identité à utiliser dépend du type d'informations d'identification de sécurité utilisé sur la liaison du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="73ced-112">The type of identity to use is dependent on the type of security credentials used on the endpoint's binding.</span></span>

- <span data-ttu-id="73ced-113">L'identité peut être définie de façon déclarative dans la configuration ou de façon impérative dans le code.</span><span class="sxs-lookup"><span data-stu-id="73ced-113">Identity can either be set declaratively in configuration or imperatively in code.</span></span> <span data-ttu-id="73ced-114">Pour le client et le service, vous devez généralement utiliser la configuration.</span><span class="sxs-lookup"><span data-stu-id="73ced-114">Typically for both the client and the service you should use configuration to set the identity.</span></span>

- <span data-ttu-id="73ced-115">Comment définir une identité personnalisée sur le client</span><span class="sxs-lookup"><span data-stu-id="73ced-115">How to set a custom identity on the client.</span></span> <span data-ttu-id="73ced-116">Une identité personnalisée est en général une personnalisation d'un type d'identité existant qui permet au client d'examiner d'autres informations de revendication fournies dans les informations d'identification du service afin de prendre des décisions d'autorisation avant d'appeler le service.</span><span class="sxs-lookup"><span data-stu-id="73ced-116">A custom identity is typically a customization of an existing type of identity that enables the client to examine other claim information provided in the service's credentials to make authorization decisions before calling the service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="73ced-117">Cet exemple vérifie l'identité d'un certificat spécifique appelé identity.com et la clé RSA contenue dans ce certificat.</span><span class="sxs-lookup"><span data-stu-id="73ced-117">This sample checks the identity of a specific certificate called identity.com and the RSA key contained within this certificate.</span></span> <span data-ttu-id="73ced-118">Lors de l'utilisation des types d'identité Certificat et RSA dans la configuration sur le client, l'une des méthodes utilisées pour obtenir facilement ces valeurs consiste à inspecter le WSDL du service dans lequel ces valeurs sont sérialisées.</span><span class="sxs-lookup"><span data-stu-id="73ced-118">When using the Certificate and RSA identity types in configuration on the client, an easy way to get these values is to inspect the WSDL for the service where these values are serialized.</span></span>

 <span data-ttu-id="73ced-119">L'exemple de code suivant montre comment configurer l'identité d'un point de terminaison de service avec le serveur DNS (Domain Name Server) d'un certificat à l'aide de WSHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="73ced-119">The following sample code shows how to configure the identity of a service endpoint with the Domain Name Server (DNS) of a certificate using a WSHttpBinding.</span></span>

```csharp
//Create a service endpoint and set its identity to the certificate's DNS
WSHttpBinding wsAnonbinding = new WSHttpBinding (SecurityMode.Message);
// Client are Anonymous to the service
wsAnonbinding.Security.Message.ClientCredentialType = MessageCredentialType.None;
WServiceEndpoint ep = serviceHost.AddServiceEndpoint(typeof(ICalculator),wsAnonbinding, String.Empty);
EndpointAddress epa = new EndpointAddress(dnsrelativeAddress,EndpointIdentity.CreateDnsIdentity("identity.com"));
ep.Address = epa;
```

 <span data-ttu-id="73ced-120">L'identité peut également être spécifiée dans la configuration dans le fichier App.config.</span><span class="sxs-lookup"><span data-stu-id="73ced-120">The identity can also be specified in configuration in the App.config file.</span></span> <span data-ttu-id="73ced-121">L'exemple suivant montre comment définir l'identité UPN (User Principal Name, nom d'utilisateur principal) pour un point de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="73ced-121">The following example shows how to set the UPN (User Principal Name) identity for a service endpoint.</span></span>

```xml
<endpoint address="upnidentity"
        behaviorConfiguration=""
        binding="wsHttpBinding"
        bindingConfiguration="WSHttpBinding_Windows"
        name="WSHttpBinding_ICalculator_Windows"
        contract="Microsoft.ServiceModel.Samples.ICalculator">
  <!-- Set the UPN identity for this endpoint -->
  <identity>
      <userPrincipalName value="host\myservice.com" />
  </identity >
</endpoint>
```

 <span data-ttu-id="73ced-122">Une identité personnalisée peut être définie sur le client en dérivant des classes <xref:System.ServiceModel.EndpointIdentity> et <xref:System.ServiceModel.Security.IdentityVerifier>.</span><span class="sxs-lookup"><span data-stu-id="73ced-122">A custom identity can be set on the client by deriving from the <xref:System.ServiceModel.EndpointIdentity> and the <xref:System.ServiceModel.Security.IdentityVerifier> classes.</span></span> <span data-ttu-id="73ced-123">D'un point de vue conceptuel, la classe <xref:System.ServiceModel.Security.IdentityVerifier> peut être considérée comme étant l'équivalent client de la classe `AuthorizationManager` du service.</span><span class="sxs-lookup"><span data-stu-id="73ced-123">Conceptually the <xref:System.ServiceModel.Security.IdentityVerifier> class can be considered to be the client equivalent of the service's `AuthorizationManager` class.</span></span> <span data-ttu-id="73ced-124">L'exemple de code suivant présente une implémentation de `OrgEndpointIdentity`, qui stocke un nom d'organisation à faire correspondre au nom du sujet du certificat du serveur.</span><span class="sxs-lookup"><span data-stu-id="73ced-124">The following code example shows an implementation of `OrgEndpointIdentity`, which stores an organization name to match in the subject name of the server's certificate.</span></span> <span data-ttu-id="73ced-125">Le contrôle d'autorisation du nom d'organisation se produit dans la méthode `CheckAccess` sur la classe `CustomIdentityVerifier`.</span><span class="sxs-lookup"><span data-stu-id="73ced-125">The authorization check for the organization name occurs in the `CheckAccess` method on the `CustomIdentityVerifier` class.</span></span>

```csharp
// This custom EndpointIdentity stores an organization name
public class OrgEndpointIdentity : EndpointIdentity
{
    private string orgClaim;
    public OrgEndpointIdentity(string orgName)
    {
        orgClaim = orgName;
    }
    public string OrganizationClaim
    {
        get { return orgClaim; }
        set { orgClaim = value; }
    }
}

//This custom IdentityVerifier uses the supplied OrgEndpointIdentity to
//check that X.509 certificate's distinguished name claim contains
//the organization name e.g. the string value "O=Contoso"
class CustomIdentityVerifier : IdentityVerifier
{
    public override bool CheckAccess(EndpointIdentity identity, AuthorizationContext authContext)
    {
        bool returnvalue = false;
        foreach (ClaimSet claimset in authContext.ClaimSets)
        {
            foreach (Claim claim in claimset)
            {
                if (claim.ClaimType == "http://schemas.microsoft.com/ws/2005/05/identity/claims/x500distinguishedname")
                {
                    X500DistinguishedName name = (X500DistinguishedName)claim.Resource;
                    if (name.Name.Contains(((OrgEndpointIdentity)identity).OrganizationClaim))
                    {
                        Console.WriteLine("Claim Type: {0}",claim.ClaimType);
                        Console.WriteLine("Right: {0}", claim.Right);
                        Console.WriteLine("Resource: {0}",claim.Resource);
                        Console.WriteLine();
                        returnvalue = true;
                    }
                }
            }
        }
        return returnvalue;
    }
}
```

 <span data-ttu-id="73ced-126">Cet exemple utilise un certificat appelé identity.com qui est situé dans le dossier de solution Identity correspondant à votre langue.</span><span class="sxs-lookup"><span data-stu-id="73ced-126">This sample uses a certificate called identity.com which is in the language-specific Identity solution folder.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="73ced-127">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="73ced-127">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="73ced-128">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="73ced-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="73ced-129">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="73ced-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="73ced-130">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="73ced-130">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="73ced-131">Pour exécuter l'exemple sur le même ordinateur</span><span class="sxs-lookup"><span data-stu-id="73ced-131">To run the sample on the same computer</span></span>

1. <span data-ttu-id="73ced-132">Sur Windows XP ou Windows Vista, importez le fichier de certificat Identity. pfx dans le dossier de solution Identity dans le magasin de certificats LocalMachine/My (Personal) à l’aide de l’outil de composant logiciel enfichable MMC.</span><span class="sxs-lookup"><span data-stu-id="73ced-132">On Windows XP or Windows Vista, import the Identity.pfx certificate file in the Identity solution folder into the LocalMachine/My (Personal) certificate store using the MMC snap-in tool.</span></span> <span data-ttu-id="73ced-133">Ce fichier est protégé par mot de passe.</span><span class="sxs-lookup"><span data-stu-id="73ced-133">This file is password protected.</span></span> <span data-ttu-id="73ced-134">Lors de l'importation, un mot de passe vous est demandé.</span><span class="sxs-lookup"><span data-stu-id="73ced-134">During the import you are asked for a password.</span></span> <span data-ttu-id="73ced-135">Tapez `xyz` dans la zone mot de passe.</span><span class="sxs-lookup"><span data-stu-id="73ced-135">Type `xyz` into the password box.</span></span> <span data-ttu-id="73ced-136">Pour plus d’informations, consultez la rubrique [Comment : afficher des certificats à l’aide du composant logiciel enfichable MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) .</span><span class="sxs-lookup"><span data-stu-id="73ced-136">For more information, see the [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) topic.</span></span> <span data-ttu-id="73ced-137">Une fois cette opération effectuée, exécutez Setup. bat dans un Invite de commandes développeur pour Visual Studio avec des privilèges d’administrateur, ce qui a pour effet de copier ce certificat dans le magasin CurrentUser/personnes autorisées pour une utilisation sur le client.</span><span class="sxs-lookup"><span data-stu-id="73ced-137">Once this is done, run Setup.bat in a Developer Command Prompt for Visual Studio with administrator privileges, which copies this certificate to the CurrentUser/Trusted People store for use on the client.</span></span>

2. <span data-ttu-id="73ced-138">Sur Windows Server 2003, exécutez Setup. bat à partir du dossier d’installation de l’exemple à l’intérieur d’une invite de commandes de Visual Studio 2012 avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="73ced-138">On Windows Server 2003, run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt with administrator privileges.</span></span> <span data-ttu-id="73ced-139">Tous les certificats requis à l'exécution de l'exemple sont ainsi installés.</span><span class="sxs-lookup"><span data-stu-id="73ced-139">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="73ced-140">Le fichier de commandes Setup. bat est conçu pour être exécuté à partir d’une invite de commandes de Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="73ced-140">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="73ced-141">La variable d’environnement PATH définie dans l’invite de commandes de Visual Studio 2012 pointe vers le répertoire qui contient les exécutables requis par le script Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="73ced-141">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span> <span data-ttu-id="73ced-142">Assurez-vous d'effacer les certificats en exécutant Cleanup.bat une fois l'exemple terminé.</span><span class="sxs-lookup"><span data-stu-id="73ced-142">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="73ced-143">D'autres exemples de sécurité utilisent ces mêmes certificats.</span><span class="sxs-lookup"><span data-stu-id="73ced-143">Other security samples use the same certificates.</span></span>  
  
3. <span data-ttu-id="73ced-144">Lancez Service.exe à partir du répertoire de \service\bin.</span><span class="sxs-lookup"><span data-stu-id="73ced-144">Launch Service.exe from the \service\bin directory.</span></span> <span data-ttu-id="73ced-145">Assurez-vous que le service indique qu’il est prêt et qu’il affiche une invite d’appui sur \<entrez > pour mettre fin au service.</span><span class="sxs-lookup"><span data-stu-id="73ced-145">Ensure that the service indicates that it is ready and displays a prompt to Press \<Enter> to terminate the service.</span></span>  
  
4. <span data-ttu-id="73ced-146">Lancez Client.exe à partir du répertoire \client\bin ou en appuyant sur F5 dans Visual Studio pour effectuer la génération et l'exécution.</span><span class="sxs-lookup"><span data-stu-id="73ced-146">Launch Client.exe from \client\bin directory or by pressing F5 in Visual Studio to build and run.</span></span> <span data-ttu-id="73ced-147">L'activité du client s'affiche sur son application de console.</span><span class="sxs-lookup"><span data-stu-id="73ced-147">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="73ced-148">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="73ced-148">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="73ced-149">Pour exécuter l'exemple sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="73ced-149">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="73ced-150">Avant de générer la partie cliente de l'exemple, modifiez la valeur de l'adresse de point de terminaison du service du fichier Client.cs dans la méthode `CallServiceCustomClientIdentity`.</span><span class="sxs-lookup"><span data-stu-id="73ced-150">Before building the client part of the sample, be sure to change the value for the service's endpoint address in the Client.cs file in the `CallServiceCustomClientIdentity` method.</span></span> <span data-ttu-id="73ced-151">Puis générez l'exemple.</span><span class="sxs-lookup"><span data-stu-id="73ced-151">Then build the sample.</span></span>  
  
2. <span data-ttu-id="73ced-152">Créez un répertoire sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="73ced-152">Create a directory on the service computer.</span></span>  
  
3. <span data-ttu-id="73ced-153">Copiez les fichiers programme du service de \service\bin dans le répertoire sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="73ced-153">Copy the service program files from service\bin to the directory on the service computer.</span></span> <span data-ttu-id="73ced-154">Copiez également les fichiers Setup.bat et Cleanup.bat sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="73ced-154">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
4. <span data-ttu-id="73ced-155">Créez un répertoire sur l'ordinateur client pour les fichiers binaires du client.</span><span class="sxs-lookup"><span data-stu-id="73ced-155">Create a directory on the client computer for the client binaries.</span></span>  
  
5. <span data-ttu-id="73ced-156">Copiez les fichiers programme du client dans le répertoire client de l'ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="73ced-156">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="73ced-157">Copiez également les fichiers Setup.bat, Cleanup.bat et ImportServiceCert.bat sur le client.</span><span class="sxs-lookup"><span data-stu-id="73ced-157">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
6. <span data-ttu-id="73ced-158">Sur le service, exécutez `setup.bat service` dans un Invite de commandes développeur pour Visual Studio ouvert avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="73ced-158">On the service, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="73ced-159">L’exécution de `setup.bat` avec l’argument `service` crée un certificat de service avec le nom de domaine complet de l’ordinateur et exporte le certificat de service vers un fichier nommé service. cer.</span><span class="sxs-lookup"><span data-stu-id="73ced-159">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
7. <span data-ttu-id="73ced-160">Copiez le fichier Service.cer du répertoire de service vers le répertoire client sur l'ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="73ced-160">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="73ced-161">Dans le fichier Client.exe.config de l'ordinateur client, modifiez la valeur d'adresse du point de terminaison afin qu'elle corresponde à la nouvelle adresse de votre service.</span><span class="sxs-lookup"><span data-stu-id="73ced-161">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="73ced-162">Plusieurs instances doivent être modifiées.</span><span class="sxs-lookup"><span data-stu-id="73ced-162">There are multiple instances that must be changed.</span></span>  
  
9. <span data-ttu-id="73ced-163">Sur le client, exécutez ImportServiceCert. bat dans un Invite de commandes développeur pour Visual Studio ouvert avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="73ced-163">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="73ced-164">Cette opération importe le certificat de service du fichier Service.cer dans le magasin CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="73ced-164">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="73ced-165">Sur l'ordinateur de service, lancez Service.exe à partir d'une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="73ced-165">On the service computer, launch the Service.exe from the command prompt.</span></span>  
  
11. <span data-ttu-id="73ced-166">Sur l'ordinateur client, lancez Client.exe à partir d'une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="73ced-166">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="73ced-167">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="73ced-167">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="73ced-168">Pour procéder au nettoyage après exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="73ced-168">To clean up after the sample</span></span>  
  
- <span data-ttu-id="73ced-169">Exécutez Cleanup.bat dans le dossier d'exemples après avoir exécuté l'exemple.</span><span class="sxs-lookup"><span data-stu-id="73ced-169">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="73ced-170">Ce script ne supprime pas de certificat de service sur un client lors de l'exécution de cet exemple sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="73ced-170">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="73ced-171">Si vous avez exécuté des exemples de Windows Communication Foundation (WCF) qui utilisent des certificats sur des ordinateurs, veillez à effacer les certificats de service qui ont été installés dans le magasin CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="73ced-171">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="73ced-172">Pour ce faire, utilisez la commande suivante : `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`, par exemple : `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="73ced-172">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
