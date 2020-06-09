---
title: Retrieve Metadata
ms.date: 03/30/2017
ms.assetid: e8a6ef8c-a195-495a-a15e-7d92bdf0b28c
ms.openlocfilehash: 4763686485dfe97844fad78cf0bb279113c0ce08
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594606"
---
# <a name="retrieve-metadata"></a>Retrieve Metadata
Cet exemple montre comment implémenter un client qui récupère dynamiquement les métadonnées d'un service afin de choisir un point de terminaison avec lequel communiquer. Cet exemple est basé sur le [prise en main](getting-started-sample.md). Le service a été modifié pour exposer deux points de terminaison : un point de terminaison à l’adresse de base à l’aide de la `basicHttpBinding` liaison et un point de terminaison sécurisé à {*BaseAddress*}/Secure à l’aide de la `wsHttpBinding` liaison. Au lieu de configurer le client avec les adresses et liaisons du point de terminaison, le client récupère dynamiquement les métadonnées du service à l'aide de la classe <xref:System.ServiceModel.Description.MetadataExchangeClient> puis importe ces métadonnées en tant que classe <xref:System.ServiceModel.Description.ServiceEndpointCollection> à l'aide de la classe <xref:System.ServiceModel.Description.WsdlImporter>.  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 L'application cliente utilise la classe <xref:System.ServiceModel.Description.ServiceEndpointCollection> importée pour créer des clients qui communiquent avec le service. L'application cliente parcourt chaque point de terminaison récupéré et communique avec chaque point de terminaison qui implémente le contrat `ICalculator`. L'adresse et la liaison appropriées sont fournies avec le point de terminaison récupéré ; le client est ainsi configuré pour communiquer avec chaque point de terminaison, comme indiqué dans l'exemple de code suivant.  
  
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
  
 La fenêtre de console cliente affiche les opérations envoyées à chacun des points de terminaison, en indiquant le chemin d'accès et le nom de la liaison.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer l’édition C#, C++ ou Visual Basic .NET de la solution, suivez les instructions de la [création des exemples de Windows Communication Foundation](building-the-samples.md).  
  
3. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\RetrieveMetadata`  
