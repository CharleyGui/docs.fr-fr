---
title: Self-Host
ms.date: 03/30/2017
helpviewer_keywords:
- Self hosted service
- Self Host Sample [Windows Communication Foundation]
ms.assetid: 05e68661-1ddf-4abf-a899-9bb1b8272a5b
ms.openlocfilehash: 9077f2b00c97ae2a2106a50780cfd2cd9596c1ec
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716319"
---
# <a name="self-host"></a><span data-ttu-id="e42ce-102">Self-Host</span><span class="sxs-lookup"><span data-stu-id="e42ce-102">Self-Host</span></span>
<span data-ttu-id="e42ce-103">Cet exemple montre comment implémenter un service auto-hébergé dans une application console.</span><span class="sxs-lookup"><span data-stu-id="e42ce-103">This sample demonstrates how to implement a self-hosted service in a console application.</span></span> <span data-ttu-id="e42ce-104">Cet exemple est basé sur le [prise en main](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="e42ce-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="e42ce-105">Le fichier de configuration de service Web.config a été renommé App.config et modifié pour configurer une adresse de base que l'hôte utilise.</span><span class="sxs-lookup"><span data-stu-id="e42ce-105">The service configuration file has been renamed from Web.config to App.config and modified to configure a base address, which the host uses.</span></span> <span data-ttu-id="e42ce-106">Le code source du service a été modifié pour implémenter une fonction `Main` statique qui crée et ouvre un hôte de service qui fournit l'adresse de base configurée.</span><span class="sxs-lookup"><span data-stu-id="e42ce-106">The service source code has been modified to implement a static `Main` function that creates and opens a service host that provides the configured base address.</span></span> <span data-ttu-id="e42ce-107">L'implémentation du service a été modifiée pour écrire la sortie dans la console à chaque opération.</span><span class="sxs-lookup"><span data-stu-id="e42ce-107">The service implementation has been modified to write output to the console for each operation.</span></span> <span data-ttu-id="e42ce-108">Le client n'a été pas modifié, excepté pour configurer l'adresse de point de terminaison correcte du service.</span><span class="sxs-lookup"><span data-stu-id="e42ce-108">The client has been unmodified, except for configuring the correct endpoint address of the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e42ce-109">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="e42ce-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e42ce-110">L'exemple implémente une fonction principale statique pour créer un <xref:System.ServiceModel.ServiceHost> pour le type `CalculatorService` donné, comme le montre l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="e42ce-110">The sample implements a static main function to create a <xref:System.ServiceModel.ServiceHost> for the given `CalculatorService` type, as shown in the following sample code.</span></span>  
  
```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Create a ServiceHost for the CalculatorService type.  
    using (ServiceHost serviceHost =   
           new ServiceHost(typeof(CalculatorService)))  
    {  
        // Open the ServiceHost to create listeners   
        // and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
    }  
}  
```  
  
 <span data-ttu-id="e42ce-111">Lorsqu'un service est hébergé par IIS (Internet Information Services) ou WAS (Windows Process Activation Service), l'adresse de base du service est fournie par l'environnement d'hébergement.</span><span class="sxs-lookup"><span data-stu-id="e42ce-111">When a service is hosted in Internet Information Services (IIS) or Windows Process Activation Service (WAS), the base address of the service is provided by the hosting environment.</span></span> <span data-ttu-id="e42ce-112">En cas d'auto-hébergement, vous devez spécifier l'adresse de base vous-même.</span><span class="sxs-lookup"><span data-stu-id="e42ce-112">In the self-hosted case, you must specify the base address yourself.</span></span> <span data-ttu-id="e42ce-113">Cette opération s’effectue à l’aide de l’élément `add`, de l’enfant de [\<baseAddresses >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), de l’enfant de [\<> d’hôte](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), de l’enfant de\<[service](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) >, comme illustré dans l’exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="e42ce-113">This is done using the `add` element, child of [\<baseAddresses>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), child of [\<host>](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), child of [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) as demonstrated in the following sample configuration.</span></span>  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
  ...  
</service>  
```  
  
 <span data-ttu-id="e42ce-114">Lorsque vous exécutez l'exemple, les requêtes et réponses de l'opération s'affichent dans les fenêtres de console du service et du client.</span><span class="sxs-lookup"><span data-stu-id="e42ce-114">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="e42ce-115">Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client.</span><span class="sxs-lookup"><span data-stu-id="e42ce-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e42ce-116">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="e42ce-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e42ce-117">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e42ce-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e42ce-118">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e42ce-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="e42ce-119">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e42ce-119">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e42ce-120">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e42ce-120">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e42ce-121">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="e42ce-121">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="e42ce-122">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e42ce-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e42ce-123">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="e42ce-123">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\SelfHost`  
  
## <a name="see-also"></a><span data-ttu-id="e42ce-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e42ce-124">See also</span></span>

- [<span data-ttu-id="e42ce-125">Hébergement AppFabric et exemples de persistance</span><span class="sxs-lookup"><span data-stu-id="e42ce-125">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
