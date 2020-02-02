---
title: Getting Started, exemple
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- basic samples [WCF], getting started
ms.assetid: 967a3d94-0261-49ff-b85a-20bb07f1af20
ms.openlocfilehash: 7bfef2c3fa5d0d3c6dafad5a6015eb9f5ca2b5c6
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921318"
---
# <a name="getting-started-sample"></a><span data-ttu-id="aa5c3-102">Getting Started, exemple</span><span class="sxs-lookup"><span data-stu-id="aa5c3-102">Getting Started Sample</span></span>

<span data-ttu-id="aa5c3-103">L’exemple Prise en main montre comment implémenter un service classique et un client standard à l’aide de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="aa5c3-103">The Getting Started sample demonstrates how to implement a typical service and a typical client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="aa5c3-104">Cet exemple constitue la base de tous les autres exemples de technologie de base.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-104">This sample is the basis for all other basic technology samples.</span></span>

> [!NOTE]
> <span data-ttu-id="aa5c3-105">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa5c3-106">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="aa5c3-107">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="aa5c3-108">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aa5c3-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="aa5c3-109">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\GettingStarted\GettingStarted`

<span data-ttu-id="aa5c3-110">Le service décrit les opérations qu'il effectue dans un contrat de service qu'il expose publiquement sous forme de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-110">The service describes the operations it performs in a service contract that it exposes publicly as metadata.</span></span> <span data-ttu-id="aa5c3-111">Le service contient également le code pour implémenter les opérations.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-111">The service also contains the code to implement the operations.</span></span>

<span data-ttu-id="aa5c3-112">Le client contient une définition du contrat de service et une classe proxy permettant d'accéder au service.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-112">The client contains a definition of the service contract and a proxy class for accessing the service.</span></span> <span data-ttu-id="aa5c3-113">Le code proxy est généré à partir des métadonnées du service à l’aide de l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="aa5c3-113">The proxy code is generated from the service metadata using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>

<span data-ttu-id="aa5c3-114">Sur Windows Vista, le service est hébergé dans le service d’activation Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="aa5c3-114">On Windows Vista, the service is hosted in the Windows Activation Service (WAS).</span></span> <span data-ttu-id="aa5c3-115">Sur Windows XP et Windows Server 2003, il est hébergé par Internet Information Services (IIS) et ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-115">On Windows XP and Windows Server 2003, it is hosted by Internet Information Services (IIS) and ASP.NET.</span></span> <span data-ttu-id="aa5c3-116">L'hébergement d'un service dans les services IIS ou WAS lui permet d'être activé automatiquement lorsqu'il est accédé pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-116">Hosting a service in IIS or WAS allows the service to be activated automatically when it is accessed for the first time.</span></span>

> [!NOTE]
> <span data-ttu-id="aa5c3-117">Si vous préférez prendre en main un exemple qui héberge le service dans une application console au lieu d’IIS, consultez l’exemple [auto-hôte](../../../../docs/framework/wcf/samples/self-host.md) .</span><span class="sxs-lookup"><span data-stu-id="aa5c3-117">If you would prefer to get started with a sample that hosts the service in a console application instead of IIS, see the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span>

<span data-ttu-id="aa5c3-118">Le service et le client spécifient les détails d'accès dans les paramètres du fichier de configuration, qui fournissent la souplesse au moment du déploiement.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-118">The service and client specify access details in configuration file settings, which provide flexibility at the time of deployment.</span></span> <span data-ttu-id="aa5c3-119">Cela inclut une définition de point de terminaison qui spécifie une adresse, une liaison et un contrat.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-119">This includes an endpoint definition that specifies an address, binding, and contract.</span></span> <span data-ttu-id="aa5c3-120">La liaison spécifie des détails de sécurité et de transport sur la manière dont le service doit être accédé.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-120">The binding specifies transport and security details for how the service is to be accessed.</span></span>

<span data-ttu-id="aa5c3-121">Le service configure un comportement au moment de l'exécution pour publier ses métadonnées.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-121">The service configures a run-time behavior to publish its metadata.</span></span>

<span data-ttu-id="aa5c3-122">Le service implémente un contrat qui définit un modèle de communication demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-122">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="aa5c3-123">Le contrat est défini par l'interface `ICalculator`, laquelle expose les opérations mathématiques suivantes : addition, soustraction, multiplication et division.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-123">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="aa5c3-124">Le client adresse des demandes à une opération mathématique donnée et le service répond avec le résultat.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-124">The client makes requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="aa5c3-125">Le service implémente un contrat `ICalculator` qui est défini dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-125">The service implements an `ICalculator` contract that is defined in the following code.</span></span>

```vb
' Define a service contract.
    <ServiceContract(Namespace:="http://Microsoft.Samples.GettingStarted")>
     Public Interface ICalculator
        <OperationContract()>
        Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()>
        Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()>
        Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()>
        Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double
    End Interface
```

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

<span data-ttu-id="aa5c3-126">L'implémentation de service calcule et retourne le résultat approprié, tel qu'indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-126">The service implementation calculates and returns the appropriate result, as shown in the following example code.</span></span>

```vb
' Service class which implements the service contract.
Public Class CalculatorService
Implements ICalculator
Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add
Return n1 + n2
End Function

Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract
Return n1 - n2
End Function

Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply
Return n1 * n2
End Function

Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide
Return n1 / n2
End Function
End Class
```

```csharp
// Service class that implements the service contract.
public class CalculatorService : ICalculator
{
    public double Add(double n1, double n2)
    {
        return n1 + n2;
    }
    public double Subtract(double n1, double n2)
    {
        return n1 - n2;
    }
    public double Multiply(double n1, double n2)
    {
        return n1 * n2;
    }
    public double Divide(double n1, double n2)
    {
        return n1 / n2;
    }
}
```

<span data-ttu-id="aa5c3-127">Le service expose un point de terminaison permettant de communiquer avec le service, défini à l'aide d'un fichier de configuration (Web.config), tel qu'indiqué dans l'exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-127">The service exposes an endpoint for communicating with the service, defined using a configuration file (Web.config), as shown in the following sample configuration.</span></span>

```xaml
<services>
    <service
        name="Microsoft.ServiceModel.Samples.CalculatorService"
        behaviorConfiguration="CalculatorServiceBehavior">
        <!-- ICalculator is exposed at the base address provided by
         host: http://localhost/servicemodelsamples/service.svc.  -->
       <endpoint address=""
              binding="wsHttpBinding"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />
       ...
    </service>
</services>
```

<span data-ttu-id="aa5c3-128">Le service expose le point de terminaison au niveau de l'adresse de base fournie par l'hôte IIS ou WAS.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-128">The service exposes the endpoint at the base address provided by the IIS or WAS host.</span></span> <span data-ttu-id="aa5c3-129">La liaison est configurée avec un <xref:System.ServiceModel.WSHttpBinding> standard, qui fournit la communication HTTP et les protocoles de service Web standard pour l’adressage et la sécurité.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-129">The binding is configured with a standard <xref:System.ServiceModel.WSHttpBinding>, which provides HTTP communication and standard Web service protocols for addressing and security.</span></span> <span data-ttu-id="aa5c3-130">Le contrat correspond au `ICalculator` implémenté par le service.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-130">The contract is the `ICalculator` implemented by the service.</span></span>

<span data-ttu-id="aa5c3-131">Comme configuré, le service est accessible à `http://localhost/servicemodelsamples/service.svc` par un client sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-131">As configured, the service can be accessed at `http://localhost/servicemodelsamples/service.svc` by a client on the same computer.</span></span> <span data-ttu-id="aa5c3-132">Pour que les clients installés sur des ordinateurs distants puissent accéder au service, un nom de domaine complet doit être spécifié au lieu de localhost.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-132">For clients on remote computers to access the service, a fully-qualified domain name must be specified instead of localhost.</span></span>

<span data-ttu-id="aa5c3-133">Par défaut, l'infrastructure n'expose pas de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-133">The framework does not expose metadata by default.</span></span> <span data-ttu-id="aa5c3-134">Par conséquent, le service Active la <xref:System.ServiceModel.Description.ServiceMetadataBehavior> et expose un point de terminaison MEX (Metadata Exchange) à `http://localhost/servicemodelsamples/service.svc/mex`.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-134">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> and exposes a metadata exchange (MEX) endpoint at `http://localhost/servicemodelsamples/service.svc/mex`.</span></span> <span data-ttu-id="aa5c3-135">La configuration suivante montre comment procéder.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-135">The following configuration demonstrates this.</span></span>

```xaml
<system.serviceModel>
  <services>
    <service
        name="Microsoft.ServiceModel.Samples.CalculatorService"
        behaviorConfiguration="CalculatorServiceBehavior">
      ...
      <!-- the mex endpoint is exposed at
       http://localhost/servicemodelsamples/service.svc/mex -->
      <endpoint address="mex"
                binding="mexHttpBinding"
                contract="IMetadataExchange" />
    </service>
  </services>

  <!--For debugging purposes set the includeExceptionDetailInFaults
   attribute to true-->
  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceMetadata httpGetEnabled="True"/>
        <serviceDebug includeExceptionDetailInFaults="False" />
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```

<span data-ttu-id="aa5c3-136">Le client communique à l’aide d’un type de contrat donné à l’aide d’une classe de client générée par l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="aa5c3-136">The client communicates using a given contract type by using a client class that is generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="aa5c3-137">Ce client généré est contenu dans le fichier generatedClient.cs ou generatedClient.vb.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-137">This generated client is contained in the file generatedClient.cs or generatedClient.vb.</span></span> <span data-ttu-id="aa5c3-138">Cet utilitaire récupère les métadonnées pour un service donné et génère un client destiné à être utilisé par l'application cliente pour communiquer à l'aide d'un type de contrat donné.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-138">This utility retrieves metadata for a given service and generates a client for use by the client application to communicate using a given contract type.</span></span> <span data-ttu-id="aa5c3-139">Le service hébergé doit être disponible pour générer le code client, car il permet de récupérer les métadonnées mises à jour.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-139">The hosted service must be available to generate the client code, because the service is used to retrieve the updated metadata.</span></span>

 <span data-ttu-id="aa5c3-140">Exécutez la commande suivante à partir de l'invite de commandes du Kit de développement SDK du répertoire client pour générer le proxy typé :</span><span class="sxs-lookup"><span data-stu-id="aa5c3-140">Run the following command from the SDK command prompt in the client directory to generate the typed proxy:</span></span>

```console
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs
```

<span data-ttu-id="aa5c3-141">Pour générer le client en Visual Basic, tapez la commande suivante à partir de l'invite de commandes du Kit de développement SDK :</span><span class="sxs-lookup"><span data-stu-id="aa5c3-141">To generate client in Visual Basic type the following from the SDK command prompt:</span></span>

`Svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb`

<span data-ttu-id="aa5c3-142">En utilisant le client généré, le client peut accéder à un point de terminaison de service donné en configurant l’adresse et la liaison appropriées.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-142">By using the generated client, the client can access a given service endpoint by configuring the appropriate address and binding.</span></span> <span data-ttu-id="aa5c3-143">À l'instar du service, le client utilise un fichier de configuration (App.config) pour spécifier le point de terminaison avec lequel il souhaite communiquer.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-143">Like the service, the client uses a configuration file (App.config) to specify the endpoint with which it wants to communicate.</span></span> <span data-ttu-id="aa5c3-144">La configuration de point de terminaison client se compose d'une adresse absolue pour le point de terminaison de service, de la liaison et du contrat, tel qu'indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-144">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract, as shown in the following example.</span></span>

```xaml
<client>
     <endpoint
         address="http://localhost/servicemodelsamples/service.svc"
         binding="wsHttpBinding"
         contract=" Microsoft.ServiceModel.Samples.ICalculator" />
</client>
```

<span data-ttu-id="aa5c3-145">L'implémentation cliente instancie le client et utilise l'interface typée pour commencer à communiquer avec le service, tel qu'indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-145">The client implementation instantiates the client and uses the typed interface to begin communicating with the service, as shown in the following example code.</span></span>

```vb
' Create a client
Dim client As New CalculatorClient()

' Call the Add service operation.
            Dim value1 = 100.0R
            Dim value2 = 15.99R
            Dim result = client.Add(value1, value2)
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)

' Call the Subtract service operation.
value1 = 145.00R
value2 = 76.54R
result = client.Subtract(value1, value2)
Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)

' Call the Multiply service operation.
value1 = 9.00R
value2 = 81.25R
result = client.Multiply(value1, value2)
Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)

' Call the Divide service operation.
value1 = 22.00R
value2 = 7.00R
result = client.Divide(value1, value2)
Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)

'Closing the client gracefully closes the connection and cleans up resources
```

```csharp
// Create a client.
CalculatorClient client = new CalculatorClient();

// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = client.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

// Call the Subtract service operation.
value1 = 145.00D;
value2 = 76.54D;
result = client.Subtract(value1, value2);
Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

// Call the Multiply service operation.
value1 = 9.00D;
value2 = 81.25D;
result = client.Multiply(value1, value2);
Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

// Call the Divide service operation.
value1 = 22.00D;
value2 = 7.00D;
result = client.Divide(value1, value2);
Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);

//Closing the client releases all communication resources.
client.Close();
```

<span data-ttu-id="aa5c3-146">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-146">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="aa5c3-147">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-147">Press ENTER in the client window to shut down the client.</span></span>

```output
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

<span data-ttu-id="aa5c3-148">Cet exemple présente la méthode standard utilisée pour créer un service et un client.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-148">The Getting Started sample shows the standard way to create a service and client.</span></span> <span data-ttu-id="aa5c3-149">L’autre version de [base](../../../../docs/framework/wcf/samples/basic-sample.md) de cet exemple pour illustrer des fonctionnalités spécifiques du produit.</span><span class="sxs-lookup"><span data-stu-id="aa5c3-149">The other [Basic](../../../../docs/framework/wcf/samples/basic-sample.md) build on this sample to demonstrate specific product features.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="aa5c3-150">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="aa5c3-150">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="aa5c3-151">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="aa5c3-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="aa5c3-152">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="aa5c3-152">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="aa5c3-153">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="aa5c3-153">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="aa5c3-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa5c3-154">See also</span></span>

- [<span data-ttu-id="aa5c3-155">Guide pratique pour héberger un service WCF dans une application managée</span><span class="sxs-lookup"><span data-stu-id="aa5c3-155">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [<span data-ttu-id="aa5c3-156">How to: Host a WCF Service in IIS (Comment : héberger un service WCF dans IIS)</span><span class="sxs-lookup"><span data-stu-id="aa5c3-156">How to: Host a WCF Service in IIS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
