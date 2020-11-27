---
title: Retrieve Metadata
ms.date: 03/30/2017
ms.assetid: e8a6ef8c-a195-495a-a15e-7d92bdf0b28c
ms.openlocfilehash: a7a30fee36b14d0414f2f5bed513c21a694f3484
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255401"
---
# <a name="retrieve-metadata"></a><span data-ttu-id="753a1-102">Retrieve Metadata</span><span class="sxs-lookup"><span data-stu-id="753a1-102">Retrieve Metadata</span></span>

<span data-ttu-id="753a1-103">Cet exemple montre comment implémenter un client qui récupère dynamiquement les métadonnées d'un service afin de choisir un point de terminaison avec lequel communiquer.</span><span class="sxs-lookup"><span data-stu-id="753a1-103">This sample demonstrates how to implement a client that dynamically retrieves metadata from a service to choose an endpoint with which to communicate.</span></span> <span data-ttu-id="753a1-104">Cet exemple est basé sur le [prise en main](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="753a1-104">This sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="753a1-105">Le service a été modifié pour exposer deux points de terminaison : un point de terminaison à l’adresse de base à l’aide de la `basicHttpBinding` liaison et un point de terminaison sécurisé à {*BaseAddress*}/Secure à l’aide de la `wsHttpBinding` liaison.</span><span class="sxs-lookup"><span data-stu-id="753a1-105">The service has been modified to expose two endpoints—an endpoint at the base address using the `basicHttpBinding` binding, and a secure endpoint at {*baseaddress*}/secure using the `wsHttpBinding` binding.</span></span> <span data-ttu-id="753a1-106">Au lieu de configurer le client avec les adresses et liaisons du point de terminaison, le client récupère dynamiquement les métadonnées du service à l'aide de la classe <xref:System.ServiceModel.Description.MetadataExchangeClient> puis importe ces métadonnées en tant que classe <xref:System.ServiceModel.Description.ServiceEndpointCollection> à l'aide de la classe <xref:System.ServiceModel.Description.WsdlImporter>.</span><span class="sxs-lookup"><span data-stu-id="753a1-106">Instead of configuring the client with the endpoint addresses and bindings, the client dynamically retrieves the metadata for the service using the <xref:System.ServiceModel.Description.MetadataExchangeClient> class and then imports the metadata as a <xref:System.ServiceModel.Description.ServiceEndpointCollection> using the <xref:System.ServiceModel.Description.WsdlImporter> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="753a1-107">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="753a1-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="753a1-108">L'application cliente utilise la classe <xref:System.ServiceModel.Description.ServiceEndpointCollection> importée pour créer des clients qui communiquent avec le service.</span><span class="sxs-lookup"><span data-stu-id="753a1-108">The client application uses the imported <xref:System.ServiceModel.Description.ServiceEndpointCollection> to create clients to communicate with the service.</span></span> <span data-ttu-id="753a1-109">L'application cliente parcourt chaque point de terminaison récupéré et communique avec chaque point de terminaison qui implémente le contrat `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="753a1-109">The client application iterates through each retrieved endpoint and communicates with each endpoint that implements the `ICalculator` contract.</span></span> <span data-ttu-id="753a1-110">L'adresse et la liaison appropriées sont fournies avec le point de terminaison récupéré ; le client est ainsi configuré pour communiquer avec chaque point de terminaison, comme indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="753a1-110">The appropriate address and binding are provided with the retrieved endpoint, so that the client is configured to communicate with each endpoint, as shown in the following sample code.</span></span>  
  
```csharp
// Create a MetadataExchangeClient for retrieving metadata.  
EndpointAddress mexAddress = new EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexAddress);  
  
// Retrieve the metadata for all endpoints using metadata exchange protocol (mex).  
MetadataSet metadataSet = mexClient.GetMetadata();  
  
//Convert the metadata into endpoints.  
WsdlImporter importer = new WsdlImporter(metadataSet);  
ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
  
CalculatorClient client = null;  
ContractDescription contract = ContractDescription.GetContract(typeof(ICalculator));  
// Communicate with each endpoint that supports the ICalculator contract.  
foreach (ServiceEndpoint ep in endpoints)  
{  
    if (ep.Contract.Namespace.Equals(contract.Namespace) && ep.Contract.Name.Equals(contract.Name))  
    {  
        // Create a client using the endpoint address and binding.  
        client = new CalculatorClient(ep.Binding, new EndpointAddress(ep.Address.Uri));  
        Console.WriteLine("Communicate with endpoint: ");  
        Console.WriteLine("   AddressPath={0}", ep.Address.Uri.PathAndQuery);  
        Console.WriteLine("   Binding={0}", ep.Binding.Name);  
        // Call operations.  
        DoCalculations(client);  
  
        //Closing the client gracefully closes the connection and cleans up resources.  
        client.Close();  
    }  
}  
```  
  
 <span data-ttu-id="753a1-111">La fenêtre de console cliente affiche les opérations envoyées à chacun des points de terminaison, en indiquant le chemin d'accès et le nom de la liaison.</span><span class="sxs-lookup"><span data-stu-id="753a1-111">The client console window displays the operations sent to each of the endpoints, displaying the address path and binding name.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="753a1-112">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="753a1-112">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="753a1-113">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="753a1-113">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="753a1-114">Pour générer l’édition C#, C++ ou Visual Basic .NET de la solution, suivez les instructions de la [création des exemples de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="753a1-114">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="753a1-115">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="753a1-115">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="753a1-116">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="753a1-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="753a1-117">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="753a1-117">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="753a1-118">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="753a1-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="753a1-119">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="753a1-119">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\RetrieveMetadata`  
