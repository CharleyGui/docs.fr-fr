---
title: ASMX Client with a WCF Service
ms.date: 03/30/2017
ms.assetid: 3ea381ee-ac7d-4d62-8c6c-12dc3650879f
ms.openlocfilehash: fd13d4907f1be09440387a36e14ecdc4926ba7e7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594775"
---
# <a name="asmx-client-with-a-wcf-service"></a><span data-ttu-id="8c061-102">ASMX Client with a WCF Service</span><span class="sxs-lookup"><span data-stu-id="8c061-102">ASMX Client with a WCF Service</span></span>

<span data-ttu-id="8c061-103">Cet exemple montre comment créer un service à l’aide d’Windows Communication Foundation (WCF), puis accéder au service à partir d’un client non-WCF, tel qu’un client ASMX.</span><span class="sxs-lookup"><span data-stu-id="8c061-103">This sample demonstrates how to create a service using Windows Communication Foundation (WCF) and then access the service from a non-WCF client, such as an ASMX client.</span></span>

> [!NOTE]
> <span data-ttu-id="8c061-104">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="8c061-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="8c061-105">Cet exemple se compose d'un programme de console client (.exe) et d'une bibliothèque de service (.dll) hébergés par les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="8c061-105">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="8c061-106">Le service implémente un contrat qui définit un modèle de communication demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="8c061-106">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="8c061-107">Le contrat est défini par l'interface `ICalculator`, qui expose des opérations mathématiques (`Add`, `Subtract`, `Multiply` et `Divide`).</span><span class="sxs-lookup"><span data-stu-id="8c061-107">The contract is defined by the `ICalculator` interface, which exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="8c061-108">Le client ASMX adresse des demandes synchrones à une opération mathématique et le service répond avec le résultat.</span><span class="sxs-lookup"><span data-stu-id="8c061-108">The ASMX client makes synchronous requests to a math operation and the service replies with the result.</span></span>

<span data-ttu-id="8c061-109">Le service implémente un contrat `ICalculator` tel que défini dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="8c061-109">The service implements an `ICalculator` contract as defined in the following code.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"), XmlSerializerFormat]
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

<span data-ttu-id="8c061-110">Le <xref:System.Runtime.Serialization.DataContractSerializer> et le <xref:System.Xml.Serialization.XmlSerializer> mappent des types CLR à une représentation XML.</span><span class="sxs-lookup"><span data-stu-id="8c061-110">The <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Xml.Serialization.XmlSerializer> map CLR types to an XML representation.</span></span> <span data-ttu-id="8c061-111">Le <xref:System.Runtime.Serialization.DataContractSerializer> interprète des représentations XML différemment du XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="8c061-111">The <xref:System.Runtime.Serialization.DataContractSerializer> interprets some XML representations differently than XmlSerializer.</span></span> <span data-ttu-id="8c061-112">Les générateurs de proxy non-WCF, tels que WSDL. exe, génèrent une interface plus utilisable lorsque le XmlSerializer est utilisé.</span><span class="sxs-lookup"><span data-stu-id="8c061-112">Non-WCF proxy generators, such as Wsdl.exe, generate a more usable interface when the XmlSerializer is being used.</span></span> <span data-ttu-id="8c061-113">Le <xref:System.ServiceModel.XmlSerializerFormatAttribute> est appliqué à l' `ICalculator` interface, pour s’assurer que le XmlSerializer est utilisé pour le mappage des types CLR au format XML.</span><span class="sxs-lookup"><span data-stu-id="8c061-113">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> is applied to the `ICalculator` interface, to ensure that the XmlSerializer is used for mapping CLR types to XML.</span></span> <span data-ttu-id="8c061-114">L'implémentation de service calcule et retourne le résultat approprié.</span><span class="sxs-lookup"><span data-stu-id="8c061-114">The service implementation calculates and returns the appropriate result.</span></span>

<span data-ttu-id="8c061-115">Le service expose un point de terminaison unique de communication avec le service, lequel est défini à l'aide du fichier de configuration Web.config.</span><span class="sxs-lookup"><span data-stu-id="8c061-115">The service exposes a single endpoint for communicating with the service, defined using a configuration file (Web.config).</span></span> <span data-ttu-id="8c061-116">Le point de terminaison se compose d'une adresse, d'une liaison et d'un contrat.</span><span class="sxs-lookup"><span data-stu-id="8c061-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="8c061-117">Le service expose le point de terminaison à l'adresse de base fournie par l'hôte IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="8c061-117">The service exposes the endpoint at the base address provided by the Internet Information Services (IIS) host.</span></span> <span data-ttu-id="8c061-118">L'attribut `binding` a la valeur basicHttpBinding, qui fournit des communications HTTP à l'aide de SOAP 1.1, qui est conforme à WS-BasicProfile 1.1, comme le montre l'exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="8c061-118">The `binding` attribute is set to basicHttpBinding that provides HTTP communications using SOAP 1.1, which is compliant with WS-I BasicProfile 1.1 as shown in the following sample configuration.</span></span>

```xml
<services>
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc.  -->
    <endpoint address=""
              binding="basicHttpBinding"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />
  </service>
</services>
```

<span data-ttu-id="8c061-119">Le client ASMX communique avec le service WCF à l’aide d’un proxy typé généré par l’utilitaire Web Services Description Language (WSDL) (WSDL. exe).</span><span class="sxs-lookup"><span data-stu-id="8c061-119">The ASMX client communicates with the WCF service using a typed proxy that is generated by the Web Services Description Language (WSDL) utility (Wsdl.exe).</span></span> <span data-ttu-id="8c061-120">Le proxy typé est contenu dans le fichier generatedClient.cs.</span><span class="sxs-lookup"><span data-stu-id="8c061-120">The typed proxy is contained in the file generatedClient.cs.</span></span> <span data-ttu-id="8c061-121">L'utilitaire WSDL récupère les métadonnées pour le service spécifié et génère un proxy typé qui sera utilisé par un client pour communiquer.</span><span class="sxs-lookup"><span data-stu-id="8c061-121">The WSDL utility retrieves metadata for the specified service and generates a typed proxy for use by a client to communicate.</span></span> <span data-ttu-id="8c061-122">Par défaut, l'infrastructure n'expose pas de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="8c061-122">By default, the framework does not expose any metadata.</span></span> <span data-ttu-id="8c061-123">Pour exposer les métadonnées requises pour générer le proxy, vous devez ajouter un [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md) et affecter `httpGetEnabled` à son attribut la valeur, `True` comme indiqué dans la configuration suivante.</span><span class="sxs-lookup"><span data-stu-id="8c061-123">To expose the metadata required to generate the proxy, you must add a [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md) and set its `httpGetEnabled` attribute to `True` as shown in the following configuration.</span></span>

```xml
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <!-- Setting httpGetEnabled to True on the serviceMetadata
           behavior exposes the service's wsdl at <base address>?wsdl :
           http://localhost/servicemodelsamples/service.svc?wsdl -->
      <serviceMetadata httpGetEnabled="True"/>
      <serviceDebug includeExceptionDetailInFaults="False" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```

<span data-ttu-id="8c061-124">Exécutez la commande suivante à partir d'une invite de commandes dans le répertoire client pour générer le proxy typé.</span><span class="sxs-lookup"><span data-stu-id="8c061-124">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>

```console
wsdl /n:Microsoft.ServiceModel.Samples /o:generatedClient.cs /urlkey:CalculatorServiceAddress http://localhost/servicemodelsamples/service.svc?wsdl
```

<span data-ttu-id="8c061-125">En utilisant le proxy typé généré, le client peut accéder à un point de terminaison de service donné en configurant l'adresse appropriée.</span><span class="sxs-lookup"><span data-stu-id="8c061-125">By using the generated typed proxy, the client can access a given service endpoint by configuring the appropriate address.</span></span> <span data-ttu-id="8c061-126">Le client utilise un fichier de configuration (App.config) pour spécifier le point de terminaison avec lequel communiquer.</span><span class="sxs-lookup"><span data-stu-id="8c061-126">The client uses a configuration file (App.config) to specify the endpoint to communicate with.</span></span>

```xml
<appSettings>
  <add key="CalculatorServiceAddress"
       value="http://localhost/ServiceModelSamples/service.svc"/>
</appSettings>
```

<span data-ttu-id="8c061-127">L'implémentation cliente génère une instance du proxy typé pour commencer à communiquer avec le service.</span><span class="sxs-lookup"><span data-stu-id="8c061-127">The client implementation constructs an instance of the typed proxy to begin communicating with the service.</span></span>

```csharp
// Create a client to the CalculatorService.
using (CalculatorService client = new CalculatorService())
{
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

}

Console.WriteLine();
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

<span data-ttu-id="8c061-128">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="8c061-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="8c061-129">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="8c061-129">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8c061-130">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="8c061-130">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="8c061-131">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8c061-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="8c061-132">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8c061-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="8c061-133">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8c061-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!NOTE]
> <span data-ttu-id="8c061-134">Pour plus d’informations sur le passage et le retour de types de données complexes, consultez : [liaison de données dans un client Windows Forms](data-binding-in-a-windows-forms-client.md), [liaison de données dans un client Windows Presentation Foundation](data-binding-in-a-wpf-client.md)et [liaison de données dans un client ASP.net](data-binding-in-an-aspnet-client.md)</span><span class="sxs-lookup"><span data-stu-id="8c061-134">For more information about passing and returning complex data types see: [Data Binding in a Windows Forms Client](data-binding-in-a-windows-forms-client.md), [Data Binding in a Windows Presentation Foundation Client](data-binding-in-a-wpf-client.md), and [Data Binding in an ASP.NET Client](data-binding-in-an-aspnet-client.md)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8c061-135">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8c061-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8c061-136">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="8c061-136">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="8c061-137">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="8c061-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8c061-138">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="8c061-138">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\ASMX`
