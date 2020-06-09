---
title: Addressing
ms.date: 03/30/2017
ms.assetid: d438e6f2-d0f3-43aa-b259-b51b5bda2e64
ms.openlocfilehash: 3221a12a21aebe20e0f6822554937623dc3fbb8d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575964"
---
# <a name="addressing"></a><span data-ttu-id="1856f-102">Addressing</span><span class="sxs-lookup"><span data-stu-id="1856f-102">Addressing</span></span>
<span data-ttu-id="1856f-103">Cet exemple illustre les divers aspects et fonctionnalités des adresses de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="1856f-103">The Addressing sample demonstrates various aspects and features of endpoint addresses.</span></span> <span data-ttu-id="1856f-104">L’exemple est basé sur le [prise en main](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="1856f-104">The sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="1856f-105">Dans cet exemple, le service est auto-hébergé.</span><span class="sxs-lookup"><span data-stu-id="1856f-105">In this sample the service is self-hosted.</span></span> <span data-ttu-id="1856f-106">Le client et le service sont tous les deux des applications console.</span><span class="sxs-lookup"><span data-stu-id="1856f-106">Both the service and the client are console applications.</span></span> <span data-ttu-id="1856f-107">Le service définit plusieurs points de terminaison en utilisant à la fois des adresses de point de terminaison absolues et relatives.</span><span class="sxs-lookup"><span data-stu-id="1856f-107">The service defines multiple endpoints using a combination of relative and absolute endpoint addresses.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1856f-108">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="1856f-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="1856f-109">Le fichier de configuration du service spécifie une adresse de base et quatre points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="1856f-109">The service configuration file specifies a base address and four endpoints.</span></span> <span data-ttu-id="1856f-110">L'adresse de base est spécifiée à l'aide de l'élément Add, sous service/host/baseAddresses, tel qu'illustré dans l'exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="1856f-110">The base address is specified using the add element, under service/host/baseAddresses as demonstrated in the following sample configuration.</span></span>  
  
```xml  
<service name="Microsoft.ServiceModel.Samples.CalculatorService"  
         behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />  
    </baseAddresses>  
  </host>  
</service>  
```  
  
 <span data-ttu-id="1856f-111">La première définition de point de terminaison contenue dans l'exemple de configuration suivant spécifie une adresse relative, ce qui signifie que l'adresse de point de terminaison est une combinaison entre l'adresse de base et l'adresse relative conformément aux règles de composition d'URI.</span><span class="sxs-lookup"><span data-stu-id="1856f-111">The first endpoint definition shown in the following sample configuration specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of URI composition.</span></span>  
  
```xml
<!-- Empty relative address specified:   
     use the base address provided by the host. -->  
<!-- The endpoint address is  
     http://localhost:8000/ServiceModelSamples/service. -->  
<endpoint address=""  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="1856f-112">Dans ce cas de figure, l'adresse relative est vide (""). Par conséquent, l'adresse de point de terminaison correspond à l'adresse de base.</span><span class="sxs-lookup"><span data-stu-id="1856f-112">In this case, the relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="1856f-113">L’adresse du point de terminaison réel est `http://localhost:8000/servicemodelsamples/service` .</span><span class="sxs-lookup"><span data-stu-id="1856f-113">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service`.</span></span>
  
 <span data-ttu-id="1856f-114">La deuxième définition de point de terminaison spécifie également une adresse relative, comme affiché dans l'exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="1856f-114">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span>  
  
```xml  
<!-- The relative address specified: use the base address -->  
<!-- provided by the host + path. The endpoint address is -->  
<!-- http://localhost:8000/servicemodelsamples/service/test. -->  
<endpoint address="/test"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="1856f-115">L'adresse relative, "test", est ajoutée à l'adresse de base.</span><span class="sxs-lookup"><span data-stu-id="1856f-115">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="1856f-116">L’adresse du point de terminaison réel est `http://localhost:8000/servicemodelsamples/service/test` .</span><span class="sxs-lookup"><span data-stu-id="1856f-116">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service/test`.</span></span>
  
 <span data-ttu-id="1856f-117">La troisième définition de point de terminaison spécifie une adresse absolue, comme affiché dans l'exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="1856f-117">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="1856f-118">L'adresse de base ne joue aucun rôle dans l'adresse.</span><span class="sxs-lookup"><span data-stu-id="1856f-118">The base address plays no role in the address.</span></span> <span data-ttu-id="1856f-119">L’adresse du point de terminaison réel est `http://localhost:8001/hello/servicemodelsamples` .</span><span class="sxs-lookup"><span data-stu-id="1856f-119">The actual endpoint address is `http://localhost:8001/hello/servicemodelsamples`.</span></span>
  
 <span data-ttu-id="1856f-120">La quatrième adresse de point de terminaison spécifie une adresse absolue et un transport différent - TCP.</span><span class="sxs-lookup"><span data-stu-id="1856f-120">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="1856f-121">L'adresse de base ne joue aucun rôle dans l'adresse.</span><span class="sxs-lookup"><span data-stu-id="1856f-121">The base address plays no role in the address.</span></span> <span data-ttu-id="1856f-122">L’adresse du point de terminaison réel est `net.tcp://localhost:9000/servicemodelsamples/service` .</span><span class="sxs-lookup"><span data-stu-id="1856f-122">The actual endpoint address is `net.tcp://localhost:9000/servicemodelsamples/service`.</span></span>
  
```xml  
<!-- The absolute address specified, different transport: -->  
<!-- use the specified address, and ignore the base address. -->  
<!-- The endpoint address is -->  
<!-- net.tcp://localhost:9000/servicemodelsamples/service. -->  
<endpoint address=  
          "net.tcp://localhost:9000/servicemodelsamples/service"  
          binding="netTcpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="1856f-123">Le client accède uniquement à un seul des quatre points de terminaison du service, mais les quatre sont définis dans son fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="1856f-123">The client accesses just one of the four service endpoints, but all four are defined in its configuration file.</span></span> <span data-ttu-id="1856f-124">Le client sélectionne un point de terminaison lorsqu'il crée l'objet `CalculatorProxy`.</span><span class="sxs-lookup"><span data-stu-id="1856f-124">The client selects an endpoint when it creates the `CalculatorProxy` object.</span></span> <span data-ttu-id="1856f-125">En modifiant le nom de configuration de `CalculatorEndpoint1` jusqu'à `CalculatorEndpoint4`, vous pouvez exécuter chacun des points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="1856f-125">By changing the configuration name from `CalculatorEndpoint1` through `CalculatorEndpoint4`, you can exercise each of the endpoints.</span></span>  
  
 <span data-ttu-id="1856f-126">Lorsque vous exécutez l’exemple, le service énumère l’adresse, le nom de la liaison et le nom du contrat pour chacun de ses points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="1856f-126">When you run the sample, the service enumerates the address, binding name and contract name for each of its endpoints.</span></span> <span data-ttu-id="1856f-127">Le point de terminaison d'échange de métadonnées (MEX) est considéré comme étant un autre point de terminaison par ServiceHost, c'est pourquoi il apparaît dans la liste.</span><span class="sxs-lookup"><span data-stu-id="1856f-127">The metadata exchange (MEX) endpoint is just another endpoint from the ServiceHost's perspective so it shows up in the list.</span></span>  
  
```console  
Service endpoints:  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service/test  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8001/hello/servicemodelsamples  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  net.tcp://localhost:9000/servicemodelsamples/service  
           binding:  NetTcpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service/mex  
           binding:  MetadataExchangeHttpBinding  
           contract: IMetadataExchange  
  
The service is ready.  
Press <ENTER> to terminate service.  
```  
  
 <span data-ttu-id="1856f-128">Lorsque vous exécutez le client, les demandes et réponses d'opération s'affichent dans les fenêtres de console du service et du client.</span><span class="sxs-lookup"><span data-stu-id="1856f-128">When you run the client, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="1856f-129">Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client.</span><span class="sxs-lookup"><span data-stu-id="1856f-129">Press ENTER in each console window to shut down the service and client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1856f-130">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="1856f-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1856f-131">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1856f-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="1856f-132">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1856f-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="1856f-133">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1856f-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="1856f-134">Si vous utilisez Svcutil.exe pour régénérer la configuration pour cet exemple, assurez-vous de modifier le nom du point de terminaison dans la configuration client afin qu'il corresponde au code client.</span><span class="sxs-lookup"><span data-stu-id="1856f-134">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1856f-135">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1856f-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1856f-136">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="1856f-136">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="1856f-137">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1856f-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1856f-138">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="1856f-138">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Addressing`  
