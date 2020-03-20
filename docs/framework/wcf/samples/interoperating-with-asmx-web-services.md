---
title: Interoperating with ASMX Web Services
ms.date: 03/30/2017
ms.assetid: a7c11f0a-9e68-4f03-a6b1-39cf478d1a89
ms.openlocfilehash: b5af8f15d38f730d2243c642d4623c0bc6e1343c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183589"
---
# <a name="interoperating-with-asmx-web-services"></a><span data-ttu-id="3c14f-102">Interoperating with ASMX Web Services</span><span class="sxs-lookup"><span data-stu-id="3c14f-102">Interoperating with ASMX Web Services</span></span>
<span data-ttu-id="3c14f-103">Cet exemple montre comment intégrer une application client de la Windows Communication Foundation (WCF) avec un service Web ASMX existant.</span><span class="sxs-lookup"><span data-stu-id="3c14f-103">This sample demonstrates how to integrate a Windows Communication Foundation (WCF) client application with an existing ASMX Web service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3c14f-104">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="3c14f-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="3c14f-105">Cet exemple se compose d'un programme de console client (.exe) et d'une bibliothèque de service (.dll) hébergés par les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="3c14f-105">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="3c14f-106">Le service correspond à un service Web ASMX qui implémente un contrat définissant un modèle de communication demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="3c14f-106">The service is an ASMX Web Service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="3c14f-107">Ce service expose les opérations mathématiques suivantes :`Add`, `Subtract`, `Multiply` et `Divide`.</span><span class="sxs-lookup"><span data-stu-id="3c14f-107">The service exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="3c14f-108">Le client adresse des demandes synchrones à une opération mathématique et le service répond avec le résultat.</span><span class="sxs-lookup"><span data-stu-id="3c14f-108">The client makes synchronous requests to a math operation and the service replies with the result.</span></span> <span data-ttu-id="3c14f-109">L'activité du client est affichée dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="3c14f-109">Client activity is visible in the console window.</span></span>  
  
 <span data-ttu-id="3c14f-110">L'implémentation de service Web ASMX, telle qu'illustrée dans l'exemple de code suivant, calcule, puis retourne le résultat approprié.</span><span class="sxs-lookup"><span data-stu-id="3c14f-110">The ASMX Web service implementation shown in the following sample code calculates and returns the appropriate result.</span></span>  
  
```csharp  
[WebService(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class CalculatorService : System.Web.Services.WebService  
    {  
        [WebMethod]  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
        [WebMethod]  
        public double Subtract(double n1, double n2)  
        {  
            return n1 - n2;  
        }  
        [WebMethod]  
        public double Multiply(double n1, double n2)  
        {  
            return n1 * n2;  
        }  
        [WebMethod]  
        public double Divide(double n1, double n2)  
        {  
            return n1 / n2;  
        }  
    }  
```  
  
 <span data-ttu-id="3c14f-111">Tel que configuré, le `http://localhost/servicemodelsamples/service.asmx` service peut être consulté par un client sur la même machine.</span><span class="sxs-lookup"><span data-stu-id="3c14f-111">As configured, the service can be accessed at `http://localhost/servicemodelsamples/service.asmx` by a client on the same machine.</span></span> <span data-ttu-id="3c14f-112">Pour que les clients installés sur des ordinateurs distants puissent accéder au service, un nom de domaine complet doit être spécifié au lieu de localhost.</span><span class="sxs-lookup"><span data-stu-id="3c14f-112">For clients on remote machines to access the service, a qualified domain name must be specified instead of localhost.</span></span>  
  
 <span data-ttu-id="3c14f-113">La communication se fait par l’intermédiaire d’un client généré par [l’outil utilitaire De métadonnées De ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="3c14f-113">Communication is done through a client generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="3c14f-114">Le client figure dans le fichier generatedClient.cs.</span><span class="sxs-lookup"><span data-stu-id="3c14f-114">The client is contained in the file generatedClient.cs.</span></span> <span data-ttu-id="3c14f-115">Le service ASMX doit être disponible pour générer le code proxy, ce dernier permettant de récupérer les métadonnées mises à jour.</span><span class="sxs-lookup"><span data-stu-id="3c14f-115">The ASMX service must be available to generate the proxy code, because it is used to retrieve the updated metadata.</span></span> <span data-ttu-id="3c14f-116">Exécutez la commande suivante à partir d'une invite de commandes dans le répertoire client pour générer le proxy typé.</span><span class="sxs-lookup"><span data-stu-id="3c14f-116">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```console  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedClient.cs  
```  
  
 <span data-ttu-id="3c14f-117">Le client généré vous permet d’accéder à un point de terminaison de service. Il vous suffit de configurer l’adresse et la liaison appropriées.</span><span class="sxs-lookup"><span data-stu-id="3c14f-117">By using the generated client, you can access a service endpoint by configuring the appropriate address and binding.</span></span> <span data-ttu-id="3c14f-118">À l'instar du service, le client utilise un fichier de configuration (App.config) pour spécifier le point de terminaison avec lequel il communique.</span><span class="sxs-lookup"><span data-stu-id="3c14f-118">Like the service, the client uses a configuration file (App.config) to specify the endpoint to communicate with.</span></span> <span data-ttu-id="3c14f-119">La configuration de point de terminaison client se compose d’une adresse absolue pour le point de terminaison de service, de la liaison et du contrat, tel qu’indiqué dans l’exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="3c14f-119">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract, as shown in the following sample configuration.</span></span>  
  
```xml  
<client>  
   <endpoint
      address="http://localhost/ServiceModelSamples/service.asmx"
      binding="basicHttpBinding"
      contract="Microsoft.ServiceModel.Samples.CalculatorServiceSoap" />  
</client>  
```  
  
 <span data-ttu-id="3c14f-120">L'implémentation cliente construit une instance du client généré.</span><span class="sxs-lookup"><span data-stu-id="3c14f-120">The client implementation constructs an instance of the generated client.</span></span> <span data-ttu-id="3c14f-121">Le client généré peut ensuite être utilisé pour communiquer avec le service.</span><span class="sxs-lookup"><span data-stu-id="3c14f-121">The generated client can then be used to communicate with the service.</span></span>  
  
```csharp  
// Create a client.  
CalculatorServiceSoapClient client = new CalculatorServiceSoapClient();  
  
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
  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
  
Console.WriteLine();  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```  
  
 <span data-ttu-id="3c14f-122">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="3c14f-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="3c14f-123">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="3c14f-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3c14f-124">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="3c14f-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3c14f-125">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)</span><span class="sxs-lookup"><span data-stu-id="3c14f-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3c14f-126">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3c14f-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="3c14f-127">Pour exécuter l’échantillon dans une configuration mono-ou cross-machine, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3c14f-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3c14f-128">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3c14f-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3c14f-129">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="3c14f-129">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3c14f-130">Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons.</span><span class="sxs-lookup"><span data-stu-id="3c14f-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3c14f-131">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="3c14f-131">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\Interop\ASMX`  
