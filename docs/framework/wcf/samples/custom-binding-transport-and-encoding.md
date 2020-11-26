---
title: Custom Binding Transport and Encoding
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
ms.openlocfilehash: 00af245f49994314ca29e1f5a2debe3af2364999
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241861"
---
# <a name="custom-binding-transport-and-encoding"></a><span data-ttu-id="73ddb-102">Custom Binding Transport and Encoding</span><span class="sxs-lookup"><span data-stu-id="73ddb-102">Custom Binding Transport and Encoding</span></span>

<span data-ttu-id="73ddb-103">Une liaison personnalisée est définie par une liste ordonnée d’éléments de liaison discrets.</span><span class="sxs-lookup"><span data-stu-id="73ddb-103">A custom binding is defined by an ordered list of discrete binding elements.</span></span> <span data-ttu-id="73ddb-104">Cet exemple montre comment configurer une liaison personnalisée avec plusieurs éléments de transport et d'encodage de message.</span><span class="sxs-lookup"><span data-stu-id="73ddb-104">This sample demonstrates how to configure a custom binding with various transport and message encoding elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73ddb-105">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="73ddb-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="73ddb-106">Cet exemple est basé sur l' [auto-hôte](self-host.md)et a été modifié pour configurer trois points de terminaison afin de prendre en charge les transports http, TCP et NamedPipe avec des liaisons personnalisées.</span><span class="sxs-lookup"><span data-stu-id="73ddb-106">This sample is based on the [Self-Host](self-host.md), and has been modified to configure three endpoints to support HTTP, TCP, and NamedPipe transports with custom bindings.</span></span> <span data-ttu-id="73ddb-107">La configuration client a été modifiée de la même façon, et le code client a été modifié pour communiquer avec chacun des trois points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="73ddb-107">The client configuration was similarly modified, and the client code changed to communicate with each of the three endpoints.</span></span>  
  
 <span data-ttu-id="73ddb-108">L'exemple montre comment configurer une liaison personnalisée qui prend en charge un transport et un encodage de message spécifiques.</span><span class="sxs-lookup"><span data-stu-id="73ddb-108">The sample demonstrates a how to configure a custom binding that supports a particular transport and message encoding.</span></span> <span data-ttu-id="73ddb-109">Pour ce faire, configurez un transport et un encodage de message pour l'élément `binding`.</span><span class="sxs-lookup"><span data-stu-id="73ddb-109">This is accomplished by configuring a transport and a message encoding for the `binding` element.</span></span> <span data-ttu-id="73ddb-110">L’ordre des éléments de liaison est important pour la définition d’une liaison personnalisée, car chacun représente une couche dans la pile de canaux (consultez [liaisons personnalisées](../extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="73ddb-110">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../extending/custom-bindings.md)).</span></span> <span data-ttu-id="73ddb-111">Cet exemple configure trois liaisons personnalisées : un transport HTTP avec encodage texte, un transport TCP avec encodage texte et un transport NamedPipe avec encodage binaire.</span><span class="sxs-lookup"><span data-stu-id="73ddb-111">This sample configures three custom bindings: an HTTP transport with text encoding, a TCP transport with text encoding, and a NamedPipe transport with a binary encoding.</span></span>  
  
 <span data-ttu-id="73ddb-112">La configuration du service définit les liaisons personnalisées comme suit :</span><span class="sxs-lookup"><span data-stu-id="73ddb-112">The service configuration defines the custom bindings as follows:</span></span>  
  
```xml  
<bindings>  
    <customBinding>  
        <binding name="HttpBinding" >  
            <textMessageEncoding
                messageVersion="Soap12Addressing10"/>  
            <httpTransport />  
        </binding>  
        <binding name="TcpBinding" >  
            <textMessageEncoding />  
            <tcpTransport />  
        </binding>  
        <binding name="NamedPipeBinding" >  
            <binaryMessageEncoding />  
            <namedPipeTransport />  
        </binding>  
    </customBinding>  
</bindings>  
```  
  
 <span data-ttu-id="73ddb-113">Lorsque vous exécutez l'exemple, les demandes et réponses de l'opération s'affichent dans les fenêtres de console du service et du client.</span><span class="sxs-lookup"><span data-stu-id="73ddb-113">When you run the sample, the operation requests and responses are displayed in both the service and client console window.</span></span> <span data-ttu-id="73ddb-114">Le client communique avec chacun des trois points de terminaison, en accédant d'abord à HTTP, puis à TCP et enfin à NamedPipe.</span><span class="sxs-lookup"><span data-stu-id="73ddb-114">The client communicates with each of the three endpoints, accessing first HTTP, then TCP, and finally NamedPipe.</span></span> <span data-ttu-id="73ddb-115">Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client.</span><span class="sxs-lookup"><span data-stu-id="73ddb-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="73ddb-116">La liaison `namedPipeTransport` ne prend pas en charge les opérations d’un ordinateur à un autre.</span><span class="sxs-lookup"><span data-stu-id="73ddb-116">The `namedPipeTransport` binding does not support machine-to-machine operations.</span></span> <span data-ttu-id="73ddb-117">Elle est uniquement utilisée pour la communication sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="73ddb-117">It is used only for communication on the same machine.</span></span> <span data-ttu-id="73ddb-118">Par conséquent, lorsque vous exécutez l'exemple sur plusieurs ordinateurs, mettez en commentaire les lignes suivantes dans le fichier de code client :</span><span class="sxs-lookup"><span data-stu-id="73ddb-118">Therefore, when running the sample in a cross-machine scenario, comment out the following lines in the client code file:</span></span>  
  
```csharp  
CalculatorClient client = new CalculatorClient("default");  
Console.WriteLine("Communicate with named pipe endpoint.");  
// Call operations.  
DoCalculations(client);  
//Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```  
  
```vb  
Dim client As New CalculatorClient("default")  
Console.WriteLine("Communicate with named pipe endpoint.")  
' call operations  
DoCalculations(client)  
'Closing the client gracefully closes the connection and cleans up resources  
client.Close()  
```  
  
> [!NOTE]
> <span data-ttu-id="73ddb-119">Si vous utilisez Svcutil.exe pour régénérer la configuration pour cet exemple, assurez-vous de modifier le nom du point de terminaison dans la configuration client afin qu'il corresponde au code client.</span><span class="sxs-lookup"><span data-stu-id="73ddb-119">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="73ddb-120">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="73ddb-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="73ddb-121">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="73ddb-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="73ddb-122">Pour générer l’édition C#, C++ ou Visual Basic .NET de la solution, suivez les instructions de la [création des exemples de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="73ddb-122">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="73ddb-123">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="73ddb-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="73ddb-124">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="73ddb-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="73ddb-125">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="73ddb-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="73ddb-126">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="73ddb-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="73ddb-127">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="73ddb-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
