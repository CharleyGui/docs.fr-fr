---
title: One-Way
ms.date: 03/30/2017
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
ms.openlocfilehash: 07fc4ecf981acbad577758c943aa22405f528a52
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575250"
---
# <a name="one-way"></a><span data-ttu-id="ac6a8-102">One-Way</span><span class="sxs-lookup"><span data-stu-id="ac6a8-102">One-Way</span></span>
<span data-ttu-id="ac6a8-103">Cet exemple présente un contact de service avec des opérations de service monodirectionnelles.</span><span class="sxs-lookup"><span data-stu-id="ac6a8-103">This sample demonstrates a service contact with one-way service operations.</span></span> <span data-ttu-id="ac6a8-104">Le client n'attend pas que les opérations de service se terminent comme c'est le cas avec les opérations de service bidirectionnelles.</span><span class="sxs-lookup"><span data-stu-id="ac6a8-104">The client does not wait for service operations to complete as is the case with two-way service operations.</span></span> <span data-ttu-id="ac6a8-105">Cet exemple est basé sur le [prise en main](getting-started-sample.md) et utilise la `wsHttpBinding` liaison.</span><span class="sxs-lookup"><span data-stu-id="ac6a8-105">This sample is based on the [Getting Started](getting-started-sample.md) and uses the `wsHttpBinding` binding.</span></span> <span data-ttu-id="ac6a8-106">Le service dans cet exemple est une application console auto-hébergée vous permettant d'observer le service qui reçoit et traite des demandes.</span><span class="sxs-lookup"><span data-stu-id="ac6a8-106">The service in this sample is a self-hosted console application to enable you to observe the service that receives and processes requests.</span></span> <span data-ttu-id="ac6a8-107">Le client est également une application console.</span><span class="sxs-lookup"><span data-stu-id="ac6a8-107">The client is also a console application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ac6a8-108">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="ac6a8-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ac6a8-109">Pour créer un contrat de service monodirectionnel, définissez votre contrat de service, appliquez la classe <xref:System.ServiceModel.OperationContractAttribute> à chaque opération et affectez <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> à `true`, tel qu'indiqué dans l'exemple de code suivant :</span><span class="sxs-lookup"><span data-stu-id="ac6a8-109">To create a one-way service contract, define your service contract, apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, and set <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> to `true` as shown in the following sample code:</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOneWayCalculator  
{  
    [OperationContract(IsOneWay=true)]  
    void Add(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Subtract(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Multiply(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Divide(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="ac6a8-110">Pour montrer que le client n'attend pas que les opérations de service se terminent, le code de service dans cet exemple implémente un délai de cinq secondes, tel qu'indiqué dans l'exemple de code suivant :</span><span class="sxs-lookup"><span data-stu-id="ac6a8-110">To demonstrate that the client does not wait for the service operations to complete, the service code in this sample implements a five-second delay, as shown in the following sample code:</span></span>  
  
```csharp
// This service class implements the service contract.  
// This code writes output to the console window.  
 [ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple,  
    InstanceContextMode = InstanceContextMode.PerCall)]  
public class CalculatorService : IOneWayCalculator  
{  
    public void Add(double n1, double n2)  
    {  
        Console.WriteLine("Received Add({0},{1}) - sleeping", n1, n2);  
        System.Threading.Thread.Sleep(1000 * 5);  
        double result = n1 + n2;  
        Console.WriteLine("Processing Add({0},{1}) - result: {2}", n1, n2, result);  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="ac6a8-111">Lorsque le client appelle le service, l'appel retourne sans attendre que l'opération de service se termine.</span><span class="sxs-lookup"><span data-stu-id="ac6a8-111">When the client calls the service, the call returns without waiting for the service operation to complete.</span></span>  
  
 <span data-ttu-id="ac6a8-112">Lorsque vous exécutez l'exemple, les activités du client et du service s'affichent dans leurs fenêtres de console respectives.</span><span class="sxs-lookup"><span data-stu-id="ac6a8-112">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="ac6a8-113">Vous pouvez voir le service recevoir des messages du client.</span><span class="sxs-lookup"><span data-stu-id="ac6a8-113">You can see the service receive messages from the client.</span></span> <span data-ttu-id="ac6a8-114">Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client.</span><span class="sxs-lookup"><span data-stu-id="ac6a8-114">Press ENTER in each console window to shut down both the service and the client.</span></span>  
  
 <span data-ttu-id="ac6a8-115">Le client s'arrête avant le service, ce qui montre qu'un client n'attend pas que les opérations de service monodirectionnelles se terminent.</span><span class="sxs-lookup"><span data-stu-id="ac6a8-115">The client finishes ahead of the service, demonstrating that a client does not wait for one-way service operations to complete.</span></span> <span data-ttu-id="ac6a8-116">La sortie du client se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="ac6a8-116">The client output is as follows:</span></span>  
  
```console  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="ac6a8-117">La sortie du service se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="ac6a8-117">The following service output is shown:</span></span>  
  
```console  
The service is ready.  
Press <ENTER> to terminate service.  
  
Received Add(100,15.99) - sleeping  
Received Subtract(145,76.54) - sleeping  
Received Multiply(9,81.25) - sleeping  
Received Divide(22,7) - sleeping  
Processing Add(100,15.99) - result: 115.99  
Processing Subtract(145,76.54) - result: 68.46  
Processing Multiply(9,81.25) - result: 731.25  
Processing Divide(22,7) - result: 3.14285714285714  
```  
  
> [!NOTE]
> <span data-ttu-id="ac6a8-118">HTTP est, par définition, un protocole de demande/réponse ; lorsqu'une demande est effectuée, une réponse est retournée.</span><span class="sxs-lookup"><span data-stu-id="ac6a8-118">HTTP is, by definition, a request/response protocol; when a request is made, a response is returned.</span></span> <span data-ttu-id="ac6a8-119">Cela se vérifie même pour une opération de service monodirectionnelle qui est exposée sur HTTP.</span><span class="sxs-lookup"><span data-stu-id="ac6a8-119">This is true even for a one-way service operation that is exposed over HTTP.</span></span> <span data-ttu-id="ac6a8-120">Lorsque l'opération est appelée, le service retourne un code d'état HTTP 202 avant que l'opération de service s'exécute.</span><span class="sxs-lookup"><span data-stu-id="ac6a8-120">When the operation is called, the service returns an HTTP status code of 202 before the service operation has executed.</span></span> <span data-ttu-id="ac6a8-121">Ce code d'état signifie que la demande a été acceptée pour traitement, mais que le traitement n'est pas encore terminé.</span><span class="sxs-lookup"><span data-stu-id="ac6a8-121">This status code means that the request has been accepted for processing, but the processing has not yet been completed.</span></span> <span data-ttu-id="ac6a8-122">Le client qui a appelé l'opération se bloque jusqu'à ce qu'il reçoive la réponse 202 du service.</span><span class="sxs-lookup"><span data-stu-id="ac6a8-122">The client that called the operation blocks until it receives the 202 response from the service.</span></span> <span data-ttu-id="ac6a8-123">Cela peut provoquer des comportements inattendus lorsque plusieurs messages unidirectionnels sont envoyés à l’aide d’une liaison configurée pour utiliser des sessions.</span><span class="sxs-lookup"><span data-stu-id="ac6a8-123">This can cause some unexpected behavior when multiple one-way messages are sent using a binding that is configured to use sessions.</span></span> <span data-ttu-id="ac6a8-124">La liaison `wsHttpBinding` utilisée dans cet exemple est configurée pour utiliser des sessions par défaut pour établir un contexte de sécurité.</span><span class="sxs-lookup"><span data-stu-id="ac6a8-124">The `wsHttpBinding` binding used in this sample is configured to use sessions by default to establish a security context.</span></span> <span data-ttu-id="ac6a8-125">Par défaut, les messages d'une session sont assurés d'arriver dans l'ordre dans lequel ils sont envoyés.</span><span class="sxs-lookup"><span data-stu-id="ac6a8-125">By default, messages in a session are guaranteed to arrive in the order in which they are sent.</span></span> <span data-ttu-id="ac6a8-126">De ce fait, lorsque le deuxième message d'une session est envoyé, il n'est pas traité tant que le premier message ne l'a pas été.</span><span class="sxs-lookup"><span data-stu-id="ac6a8-126">Because of this, when the second message in a session is sent, it is not processed until the first message has been processed.</span></span> <span data-ttu-id="ac6a8-127">Il en résulte que le client ne reçoit pas de réponse 202 pour un message tant que le traitement du message précédent n'est pas terminé.</span><span class="sxs-lookup"><span data-stu-id="ac6a8-127">The result of this is that the client does not receive the 202 response for a message until the processing of the previous message has been completed.</span></span> <span data-ttu-id="ac6a8-128">Par conséquent, le client se bloque à chaque appel d'opération suivant.</span><span class="sxs-lookup"><span data-stu-id="ac6a8-128">The client therefore appears to block on each subsequent operation call.</span></span> <span data-ttu-id="ac6a8-129">Pour éviter ce comportement, cet exemple configure l'exécution pour distribuer les messages simultanément aux différentes instances pour traitement.</span><span class="sxs-lookup"><span data-stu-id="ac6a8-129">To avoid this behavior, this sample configures the runtime to dispatch messages concurrently to distinct instances for processing.</span></span> <span data-ttu-id="ac6a8-130">L'exemple définit <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> à `PerCall` afin que chaque message puisse être traité par une autre instance.</span><span class="sxs-lookup"><span data-stu-id="ac6a8-130">The sample sets <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> to `PerCall` so that each message can be processed by a different instance.</span></span> <span data-ttu-id="ac6a8-131"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> est défini à `Multiple` pour permettre à plusieurs threads de distribuer des messages simultanément.</span><span class="sxs-lookup"><span data-stu-id="ac6a8-131"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to `Multiple` to allow more than one thread to dispatch messages at a time.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ac6a8-132">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="ac6a8-132">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ac6a8-133">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ac6a8-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ac6a8-134">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ac6a8-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="ac6a8-135">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ac6a8-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ac6a8-136">Exécutez le service avant le client et arrêtez le client avant le service.</span><span class="sxs-lookup"><span data-stu-id="ac6a8-136">Run the service before you run the client and shut down the client before shutting down the service.</span></span> <span data-ttu-id="ac6a8-137">Cela évite au client de lever une exception lorsqu'il ne parvient pas à fermer la session de sécurité correctement du fait que le service a été arrêté.</span><span class="sxs-lookup"><span data-stu-id="ac6a8-137">This avoids a client exception when the client cannot close the security session cleanly because the service is gone.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ac6a8-138">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ac6a8-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ac6a8-139">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="ac6a8-139">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ac6a8-140">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ac6a8-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ac6a8-141">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="ac6a8-141">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  
