---
title: Point de terminaison de métadonnées sécurisé personnalisée
ms.date: 03/30/2017
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
ms.openlocfilehash: d699c8dedfec3068bf0fc1504b47d78fde1988dc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96240899"
---
# <a name="custom-secure-metadata-endpoint"></a><span data-ttu-id="d5d0c-102">Point de terminaison de métadonnées sécurisé personnalisée</span><span class="sxs-lookup"><span data-stu-id="d5d0c-102">Custom Secure Metadata Endpoint</span></span>

<span data-ttu-id="d5d0c-103">Cet exemple montre comment implémenter un service avec un point de terminaison de métadonnées sécurisé qui utilise l’une des liaisons d’échange non-métadonnées et comment configurer [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) ou des clients pour extraire les métadonnées d’un tel point de terminaison de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-103">This sample demonstrates how to implement a service with a secure metadata endpoint that uses one of the non-metadata exchange bindings, and how to configure [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) or clients to fetch the metadata from such a metadata endpoint.</span></span> <span data-ttu-id="d5d0c-104">Il existe deux liaisons fournies par le système pour exposer des points de terminaison de métadonnées : mexHttpBinding et mexHttpsBinding.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-104">There are two system-provided bindings available for exposing metadata endpoints: mexHttpBinding and mexHttpsBinding.</span></span> <span data-ttu-id="d5d0c-105">mexHttpBinding est utilisé pour exposer un point de terminaison de métadonnées sur HTTP de façon non sécurisée.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-105">mexHttpBinding is used to expose a metadata endpoint over HTTP in a non-secure manner.</span></span> <span data-ttu-id="d5d0c-106">mexHttpsBinding est utilisé pour exposer un point de terminaison de métadonnées sur HTTPS de façon sécurisée.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-106">mexHttpsBinding is used to expose a metadata endpoint over HTTPS in a secure manner.</span></span> <span data-ttu-id="d5d0c-107">Cet exemple montre comment exposer un point de terminaison de métadonnées sécurisé à l'aide du <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-107">This sample illustrates how to expose a secure metadata endpoint using the <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="d5d0c-108">Cette opération peut être utile lorsque vous souhaitez modifier les paramètres de sécurité de la liaison sans devoir utiliser HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-108">You would want to do this when you want to change the security settings on the binding, but you do not want to use HTTPS.</span></span> <span data-ttu-id="d5d0c-109">Si vous utilisez mexHttpsBinding, votre point de terminaison de métadonnées sera sécurisé, mais il n'existe aucun moyen de modifier les paramètres de la liaison.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-109">If you use the mexHttpsBinding your metadata endpoint will be secure, but there is no way to modify the binding settings.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d5d0c-110">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="d5d0c-111">Service</span><span class="sxs-lookup"><span data-stu-id="d5d0c-111">Service</span></span>  

 <span data-ttu-id="d5d0c-112">Dans cet exemple, le service dispose de deux points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-112">The service in this sample has two endpoints.</span></span> <span data-ttu-id="d5d0c-113">Le point de terminaison d'application sert le contrat `ICalculator` d'une liaison `WSHttpBinding`, `ReliableSession` étant activée et la sécurité `Message` utilisant des certificats.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-113">The application endpoint serves the `ICalculator` contract on a `WSHttpBinding` with `ReliableSession` enabled and `Message` security using certificates.</span></span> <span data-ttu-id="d5d0c-114">Le point de terminaison de métadonnées utilise également une liaison `WSHttpBinding`, avec les mêmes paramètres de sécurité mais sans `ReliableSession`.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-114">The metadata endpoint also uses `WSHttpBinding`, with the same security settings but with no `ReliableSession`.</span></span> <span data-ttu-id="d5d0c-115">Le code suivant contient la configuration requise :</span><span class="sxs-lookup"><span data-stu-id="d5d0c-115">Here is the relevant configuration:</span></span>  
  
```xml  
<services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- use base address provided by host -->  
     <endpoint address=""  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding2"  
       contract="Microsoft.ServiceModel.Samples.ICalculator" />  
     <endpoint address="mex"  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding1"  
       contract="IMetadataExchange" />  
     </service>  
 </services>  
 <bindings>  
   <wsHttpBinding>  
     <binding name="Binding1">  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
     <binding name="Binding2">  
       <reliableSession inactivityTimeout="00:01:00" enabled="true" />  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
   </wsHttpBinding>  
 </bindings>  
```  
  
 <span data-ttu-id="d5d0c-116">Dans de nombreux autres exemples, le point de terminaison de métadonnées utilise la liaison par défaut `mexHttpBinding`, laquelle n'est pas sécurisée.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-116">In many of the other samples, the metadata endpoint uses the default `mexHttpBinding`, which is not secure.</span></span> <span data-ttu-id="d5d0c-117">Dans cet exemple, les métadonnées sont sécurisées grâce à l'utilisation conjointe de la liaison `WSHttpBinding` et de la sécurité `Message`.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-117">Here the metadata is secured using `WSHttpBinding` with `Message` security.</span></span> <span data-ttu-id="d5d0c-118">Pour que des clients de métadonnées puissent récupérer ces métadonnées, ils doivent être configurés à l'aide d'une liaison similaire.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-118">In order for metadata clients to retrieve this metadata, they must be configured with a matching binding.</span></span> <span data-ttu-id="d5d0c-119">Cet exemple contient deux clients configurés à l'aide d'une telle liaison.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-119">This sample demonstrates two such clients.</span></span>  
  
 <span data-ttu-id="d5d0c-120">Le premier client utilise Svcutil.exe pour extraire les métadonnées et générer le code client ainsi que la configuration pendant la conception.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-120">The first client uses Svcutil.exe to fetch the metadata and generate client code and configuration at design time.</span></span> <span data-ttu-id="d5d0c-121">Le service utilisant une liaison non définie par défaut pour les métadonnées, l'outil Svcutil.exe doit être configuré de manière spécifique, c'est-à-dire de sorte à pouvoir obtenir les métadonnées de ce service en utilisant une telle liaison.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-121">Because the service uses a non-default binding for the metadata, the Svcutil.exe tool must be specifically configured so that it can get the metadata from the service using that binding.</span></span>  
  
 <span data-ttu-id="d5d0c-122">Le deuxième client utilise le `MetadataResolver` pour extraire dynamiquement les métadonnées d'un contrat connu, puis pour appeler des opérations sur le client généré dynamiquement.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-122">The second client uses the `MetadataResolver` to dynamically fetch the metadata for a known contract and then invoke operations on the dynamically generated client.</span></span>  
  
## <a name="svcutil-client"></a><span data-ttu-id="d5d0c-123">Client Svcutil</span><span class="sxs-lookup"><span data-stu-id="d5d0c-123">Svcutil client</span></span>  

 <span data-ttu-id="d5d0c-124">Lorsque la liaison par défaut héberge votre point de terminaison `IMetadataExchange`, vous pouvez exécuter Svcutil.exe en utilisant l’adresse de ce point de terminaison :</span><span class="sxs-lookup"><span data-stu-id="d5d0c-124">When using the default binding to host your `IMetadataExchange` endpoint, you can run Svcutil.exe with the address of that endpoint:</span></span>  
  
```console  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="d5d0c-125">ce qui fonctionnera parfaitement.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-125">and it works.</span></span> <span data-ttu-id="d5d0c-126">Cependant, dans cet exemple, le serveur n'utilise pas de point de terminaison défini par défaut pour héberger les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-126">But in this sample, the server uses a non-default endpoint to host the metadata.</span></span> <span data-ttu-id="d5d0c-127">Vous devez donc indiquer à l’outil Svcutil.exe quelle liaison il doit utiliser.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-127">So Svcutil.exe must be instructed to use the correct binding.</span></span> <span data-ttu-id="d5d0c-128">Pour ce faire, vous pouvez notamment utiliser un fichier Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-128">This can be done using a Svcutil.exe.config file.</span></span>  
  
 <span data-ttu-id="d5d0c-129">Ce fichier ressemble à un fichier de configuration client standard.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-129">The Svcutil.exe.config file looks like a normal client configuration file.</span></span> <span data-ttu-id="d5d0c-130">Le nom et le contrat de point de terminaison client qui y figurent sont les deux seuls points qui diffèrent :</span><span class="sxs-lookup"><span data-stu-id="d5d0c-130">The only unusual aspects are the client endpoint name and contract:</span></span>  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 <span data-ttu-id="d5d0c-131">Le nom de point de terminaison doit correspondre au nom du schéma de l'adresse où sont hébergées les métadonnées et le contrat de point de terminaison doit correspondre à `IMetadataExchange`.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-131">The endpoint name must be the name of the scheme of the address where the metadata is hosted and the endpoint contract must be `IMetadataExchange`.</span></span> <span data-ttu-id="d5d0c-132">Par conséquent, lorsque Svcutil.exe est exécuté à l'aide d'une ligne de commande telle que celle présentée ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="d5d0c-132">Thus, when Svcutil.exe is run with a command-line such as the following:</span></span>  
  
```console  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="d5d0c-133">il recherche le point de terminaison nommé « http » et le contrat `IMetadataExchange` pour configurer la liaison et le comportement de l’échange de communication à l’aide du point de terminaison de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-133">it looks for the endpoint named "http" and contract `IMetadataExchange` to configure the binding and behavior of the communication exchange with the metadata endpoint.</span></span> <span data-ttu-id="d5d0c-134">Le reste du fichier Svcutil.exe.config (dans cet exemple) spécifie la configuration de la liaison et les informations d’identification du comportement de sorte à ce qu’elles correspondent à la configuration du point de terminaison de métadonnées côté serveur.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-134">The rest of the Svcutil.exe.config file in the sample specifies the binding configuration and behavior credentials to match the server's configuration of the metadata endpoint.</span></span>  
  
 <span data-ttu-id="d5d0c-135">Pour que l'outil Svcutil.exe puisse récupérer la configuration spécifiée dans le fichier Svcutil.exe.config, ils doivent tous deux se trouver dans le même répertoire.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-135">In order for Svcutil.exe to pick up the configuration in Svcutil.exe.config, Svcutil.exe must be in the same directory as the configuration file.</span></span> <span data-ttu-id="d5d0c-136">Vous devez copier l'outil Svcutil.exe depuis son emplacement d'installation vers le répertoire qui contient le fichier Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-136">As a result, you must copy Svcutil.exe from its install location to the directory that contains the Svcutil.exe.config file.</span></span> <span data-ttu-id="d5d0c-137">À partir de ce répertoire, exécutez ensuite la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="d5d0c-137">Then from that directory, run the following command:</span></span>  
  
```console  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="d5d0c-138">Le « . » de début \\ garantit que la copie de Svcutil.exe dans ce répertoire (celui qui a un Svcutil.exe.config correspondant) est exécutée.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-138">The leading ".\\" ensures that the copy of Svcutil.exe in this directory (the one which has a corresponding Svcutil.exe.config) is run.</span></span>  
  
## <a name="metadataresolver-client"></a><span data-ttu-id="d5d0c-139">Client MetadataResolver</span><span class="sxs-lookup"><span data-stu-id="d5d0c-139">MetadataResolver client</span></span>  

 <span data-ttu-id="d5d0c-140">Si le client connaît le contrat et sait comment s’adresser aux métadonnées pendant la conception, il peut trouver dynamiquement la liaison et l’adresse des points de terminaison d’application à l’aide du `MetadataResolver`.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-140">If the client knows the contract and how to talk to the metadata at design time, the client can dynamically find out the binding and address of application endpoints using the `MetadataResolver`.</span></span> <span data-ttu-id="d5d0c-141">Cet exemple de client démontre comme cela est possible en indiquant comment configurer la liaison et les informations d’identification utilisées par `MetadataResolver` en créant et configurant un `MetadataExchangeClient`.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-141">This sample client demonstrates this, showing how to configure the binding and credentials used by `MetadataResolver` by creating and configuring a `MetadataExchangeClient`.</span></span>  
  
 <span data-ttu-id="d5d0c-142">La liaison ainsi que les informations de certificat apparues dans Svcutil.exe.config peuvent également être spécifiées à l'identique et de manière impérative sur le `MetadataExchangeClient` :</span><span class="sxs-lookup"><span data-stu-id="d5d0c-142">The same binding and certificate information that appeared in Svcutil.exe.config can be specified imperatively on the `MetadataExchangeClient`:</span></span>  
  
```csharp  
// Specify the Metadata Exchange binding and its security mode  
WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a MetadataExchangeClient for retrieving metadata, and set the // certificate details  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
mexClient.SoapCredentials.ClientCertificate.SetCertificate(    StoreLocation.CurrentUser, StoreName.My,  
    X509FindType.FindBySubjectName, "client.com");  
mexClient.SoapCredentials.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(    StoreLocation.CurrentUser, StoreName.TrustedPeople,  
    X509FindType.FindBySubjectName, "localhost");  
```  
  
 <span data-ttu-id="d5d0c-143">Grâce au `mexClient` configuré, nous pouvons énumérer les contrats auxquels nous nous intéressons et utiliser un `MetadataResolver` pour récupérer une liste des points de terminaison correspondant à ces contrats :</span><span class="sxs-lookup"><span data-stu-id="d5d0c-143">With the `mexClient` configured, we can enumerate the contracts we are interested in, and use `MetadataResolver` to fetch a list of endpoints with those contracts:</span></span>  
  
```csharp  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts = new Collection<ContractDescription>();  
ContractDescription contract = ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints = MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 <span data-ttu-id="d5d0c-144">Enfin, nous pouvons utiliser les informations de ces points de terminaison pour initialiser la liaison et l’adresse de la fabrication `ChannelFactory` utilisée pour créer les canaux assurant la communication avec les points de terminaison d’application.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-144">Finally we can use the information from those endpoints to initialize the binding and address of a `ChannelFactory` used to create channels to communicate with the application endpoints.</span></span>  
  
```csharp  
ChannelFactory<ICalculator> cf = new ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 <span data-ttu-id="d5d0c-145">L’objectif premier de cet exemple de client est de démontrer que si vous utilisez un `MetadataResolver` et que vous devez spécifier des liaisons ou comportements personnalisés pour la communication d’échange de métadonnées, vous pouvez utiliser un `MetadataExchangeClient` pour ce faire.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-145">The key point of this sample client is to demonstrate that, if you are using `MetadataResolver`, and you must specify custom bindings or behaviors for the metadata exchange communication, you can use a `MetadataExchangeClient` to specify those custom settings.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="d5d0c-146">Pour configurer et générer l'exemple</span><span class="sxs-lookup"><span data-stu-id="d5d0c-146">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="d5d0c-147">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d5d0c-147">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d5d0c-148">Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d5d0c-148">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="d5d0c-149">Pour exécuter l'exemple sur le même ordinateur</span><span class="sxs-lookup"><span data-stu-id="d5d0c-149">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="d5d0c-150">Exécutez Setup.bat à partir du dossier d'installation de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-150">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="d5d0c-151">Tous les certificats requis à l'exécution de l'exemple sont ainsi installés.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-151">This installs all the certificates required for running the sample.</span></span> <span data-ttu-id="d5d0c-152">Notez que Setup.bat utilise l’outil FindPrivateKey.exe, qui est installé en exécutant setupCertTool.bat à partir d' [une procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d5d0c-152">Note that Setup.bat uses the FindPrivateKey.exe tool, which is installed by running setupCertTool.bat from [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d5d0c-153">Exécutez l'application cliente à partir du dossier \MetadataResolverClient\bin ou du dossier \SvcutilClient\bin.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-153">Run the client application from \MetadataResolverClient\bin or \SvcutilClient\bin.</span></span> <span data-ttu-id="d5d0c-154">L'activité du client s'affiche sur son application de console.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-154">Client activity is displayed on the client console application.</span></span>  
  
3. <span data-ttu-id="d5d0c-155">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="d5d0c-155">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
4. <span data-ttu-id="d5d0c-156">Supprimez les certificats en exécutant Cleanup.bat une fois l'exemple terminé.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-156">Remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="d5d0c-157">D'autres exemples de sécurité utilisent ces mêmes certificats.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-157">Other security samples use the same certificates.</span></span>  
  
#### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="d5d0c-158">Pour exécuter l'exemple sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="d5d0c-158">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="d5d0c-159">Sur le serveur, exécutez `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-159">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="d5d0c-160">`setup.bat`L’exécution avec l' `service` argument crée un certificat de service avec le nom de domaine complet de l’ordinateur et exporte le certificat de service dans un fichier nommé service. cer.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-160">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
2. <span data-ttu-id="d5d0c-161">Sur le serveur, modifiez Web.config en fonction du nouveau nom de ce certificat.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-161">On the server, edit Web.config to reflect the new certificate name.</span></span> <span data-ttu-id="d5d0c-162">Autrement dit, remplacez l' `findValue` attribut de l' [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) élément par le nom de domaine complet de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-162">That is, change the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) element to the fully-qualified domain name of the machine.</span></span>  
  
3. <span data-ttu-id="d5d0c-163">Copiez le fichier Service.cer du répertoire de service dans le répertoire client sur l'ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-163">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
4. <span data-ttu-id="d5d0c-164">Sur le client, exécutez `setup.bat client`.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-164">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="d5d0c-165">`setup.bat`L’exécution avec l' `client` argument crée un certificat client nommé client.com et exporte le certificat client vers un fichier nommé client. cer.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-165">Running `setup.bat` with the `client` argument creates a client certificate named Client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
5. <span data-ttu-id="d5d0c-166">Dans le fichier App.config du `MetadataResolverClient` de l'ordinateur client, modifiez la valeur d'adresse du point de terminaison mex en fonction de la nouvelle adresse de votre service.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-166">In the App.config file of the `MetadataResolverClient` on the client machine, change the address value of the mex endpoint to match the new address of your service.</span></span> <span data-ttu-id="d5d0c-167">Pour ce faire, remplacez localhost par le nom de domaine complet du serveur.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-167">You do this by replacing localhost with the fully-qualified domain name of the server.</span></span> <span data-ttu-id="d5d0c-168">Remplacez également l'occurrence de « localhost » dans le fichier metadataResolverClient.cs par le nouveau nom du certificat de service (c'est-à-dire par le nom de domaine complet du serveur).</span><span class="sxs-lookup"><span data-stu-id="d5d0c-168">Also change the occurrence of "localhost" in the metadataResolverClient.cs file to the new service certificate name (the fully-qualified domain name of the server).</span></span> <span data-ttu-id="d5d0c-169">Effectuez la même opération pour l'App.config du projet SvcutilClient.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-169">Do the same thing for the App.config of the SvcutilClient project.</span></span>  
  
6. <span data-ttu-id="d5d0c-170">Copiez le fichier Client.cer du répertoire client dans le répertoire de service sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-170">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
7. <span data-ttu-id="d5d0c-171">Sur le client, exécutez `ImportServiceCert.bat`.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-171">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="d5d0c-172">Cette opération importe le certificat de service du fichier Service.cer dans le magasin CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-172">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
8. <span data-ttu-id="d5d0c-173">Sur le serveur, exécutez `ImportClientCert.bat`. Cette opération importe le certificat client du fichier Client.cer dans le magasin LocalMachine - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-173">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
9. <span data-ttu-id="d5d0c-174">Sur l'ordinateur de service, générez le projet de service à l'aide de Visual Studio, puis sélectionnez la page d'aide d'un navigateur Web afin de vous assurer que ce projet s'exécute.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-174">On the service machine, build the service project in Visual Studio and select the help page in a web browser to verify that it is running.</span></span>  
  
10. <span data-ttu-id="d5d0c-175">Sur l'ordinateur client, exécutez le MetadataResolverClient ou le SvcutilClient depuis VS.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-175">On the client machine, run the MetadataResolverClient or the SvcutilClient from VS.</span></span>  
  
    1. <span data-ttu-id="d5d0c-176">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="d5d0c-176">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="d5d0c-177">Pour procéder au nettoyage après exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="d5d0c-177">To clean up after the sample</span></span>  
  
- <span data-ttu-id="d5d0c-178">Exécutez Cleanup.bat dans le dossier d'exemples après avoir exécuté l'exemple.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-178">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d5d0c-179">Ce script ne supprime pas les certificats de service figurant sur le client lorsque l'exemple est exécuté sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-179">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="d5d0c-180">Si vous avez exécuté des exemples de Windows Communication Foundation (WCF) qui utilisent des certificats sur des ordinateurs, veillez à effacer les certificats de service qui ont été installés dans le magasin CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-180">If you have run Windows Communication Foundation (WCF) samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="d5d0c-181">Pour ce faire, utilisez la ligne de commande suivante : `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-181">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`.</span></span> <span data-ttu-id="d5d0c-182">Par exemple : `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-182">For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d5d0c-183">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-183">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d5d0c-184">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-184">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d5d0c-185">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="d5d0c-185">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d5d0c-186">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-186">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`
