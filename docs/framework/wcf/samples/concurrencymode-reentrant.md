---
title: ConcurrencyMode Reentrant
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: 613a1ed827173b3915892dda54dd20ebabdf6dcf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183892"
---
# <a name="concurrencymode-reentrant"></a><span data-ttu-id="af9d7-102">ConcurrencyMode Reentrant</span><span class="sxs-lookup"><span data-stu-id="af9d7-102">ConcurrencyMode Reentrant</span></span>
<span data-ttu-id="af9d7-103">Cet exemple illustre la nécessité d'utiliser ConcurrencyMode.Reentrant sur une implémentation de service et les conséquences d'une telle utilisation.</span><span class="sxs-lookup"><span data-stu-id="af9d7-103">This sample demonstrates the necessity and implications of using ConcurrencyMode.Reentrant on a service implementation.</span></span> <span data-ttu-id="af9d7-104">ConcurrencyMode.Reentrant implique que le service (plus exactement l'interface de rappel) traite un seul message à la fois à un instant donné (traitement similaire à celui proposé par le mode `ConcurencyMode.Single`).</span><span class="sxs-lookup"><span data-stu-id="af9d7-104">ConcurrencyMode.Reentrant implies that the service (or callback) processes only one message at a given time (analogous to `ConcurencyMode.Single`).</span></span> <span data-ttu-id="af9d7-105">Pour assurer la sécurité des threads, Windows `InstanceContext` Communication Foundation (WCF) verrouille le traitement d’un message afin qu’aucun autre message ne puisse être traité.</span><span class="sxs-lookup"><span data-stu-id="af9d7-105">To ensure thread safety, Windows Communication Foundation (WCF) locks the `InstanceContext` processing a message so that no other messages can be processed.</span></span> <span data-ttu-id="af9d7-106">En mode ConcurrencyMode.Reentrant, le contexte `InstanceContext` est déverrouillé juste avant que le service n'effectue un appel externe, autorisant ainsi le prochain appel (lequel peut être réentrant tel qu'illustré dans l'exemple) et l'obtention du verrouillage lorsque le service reçoit la réponse à son appel.</span><span class="sxs-lookup"><span data-stu-id="af9d7-106">In case of Reentrant mode, the `InstanceContext` is unlocked just before the service makes an outgoing call thereby allowing the subsequent call, (which can be reentrant as demonstrated in the sample) to get the lock next time it comes in to the service.</span></span> <span data-ttu-id="af9d7-107">L'exemple illustre ce comportement en montrant comment un client et un service peuvent s'envoyer des messages en utilisant un contrat duplex.</span><span class="sxs-lookup"><span data-stu-id="af9d7-107">To demonstrate the behavior, the sample shows how a client and service can send messages between each other using a duplex contract.</span></span>  
  
 <span data-ttu-id="af9d7-108">Le contrat défini correspond à un contrat duplex dans lequel la méthode `Ping` est implémentée par le service et la méthode de rappel `Pong` par le client.</span><span class="sxs-lookup"><span data-stu-id="af9d7-108">The contract defined is a duplex contract with the `Ping` method being implemented by the service and the callback method `Pong` being implemented by the client.</span></span> <span data-ttu-id="af9d7-109">Le client appelle la méthode `Ping` du serveur à l'aide d'un compteur de cycles initiant par la même l'appel.</span><span class="sxs-lookup"><span data-stu-id="af9d7-109">A client invokes the server's `Ping` method with a tick count thereby initiating the call.</span></span> <span data-ttu-id="af9d7-110">Le service s'assure que la valeur du compteur de cycles n'est pas égale à zéro, puis appelle la méthode de rappel `Pong` tout en décrémentant la valeur de ce compteur.</span><span class="sxs-lookup"><span data-stu-id="af9d7-110">The service checks whether the tick count is not equal to 0 and then invokes the callbacks `Pong` method while decrementing the tick count.</span></span> <span data-ttu-id="af9d7-111">Ce processus est illustré par l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="af9d7-111">This is done by the following code in the sample.</span></span>  
  
```csharp
public void Ping(int ticks)  
{  
     Console.WriteLine("Ping: Ticks = " + ticks);  
     //Keep pinging back and forth till Ticks reaches 0.  
     if (ticks != 0)  
     {  
         OperationContext.Current.GetCallbackChannel<IPingPongCallback>().Pong((ticks - 1));  
     }  
}  
```  
  
 L'implémentation de la méthode de rappel `Pong` obéit à la même logique que l'implémentation de la méthode `Ping`. Cela signifie, en d'autres termes, que cette méthode s'assure d'abord que le nombre de cycles n'est pas égal à zéro, puis qu'elle appelle la méthode `Ping` sur le canal de rappel (dans ce cas, il s'agit du canal utilisé pour envoyer le message `Ping` d'origine) tout en décrémentant la valeur du compteur de 1. Lorsque ce nombre atteint zéro, la méthode est retournée, désencapsulant toutes les réponses au premier appel initié par le client. <span data-ttu-id="af9d7-115">Ce processus est illustré dans l'implémentation du rappel.</span><span class="sxs-lookup"><span data-stu-id="af9d7-115">This is shown in the callback implementation.</span></span>  
  
```csharp
public void Pong(int ticks)  
{  
    Console.WriteLine("Pong: Ticks = " + ticks);  
    if (ticks != 0)  
    {  
        //Retrieve the Callback  Channel (in this case the Channel which was used to send the  
        //original message) and make an outgoing call until ticks reaches 0.  
        IPingPong channel = OperationContext.Current.GetCallbackChannel<IPingPong>();  
        channel.Ping((ticks - 1));  
    }  
}  
```  
  
 Les méthodes `Ping` et `Pong` sont toutes deux du type demande-réponse, ce qui signifie que le premier appel de la méthode `Ping` est retourné uniquement une fois l'appel de `CallbackChannel<T>.Pong()` retourné. Sur le client, la méthode `Pong` ne peut pas être retournée tant que le prochain appel de la méthode `Ping` effectué n'est pas retourné. <span data-ttu-id="af9d7-118">Le rappel et le service devant tous deux effectuer des appels externes de type demande-réponse avant de pouvoir répondre à la demande en attente, le comportement ConcurrencyMode.Reentrant doit être spécifié pour leurs implémentations respectives.</span><span class="sxs-lookup"><span data-stu-id="af9d7-118">Because both the callback and the service must make outgoing request/reply calls before they can reply for the pending request, both the implementations must be marked with the ConcurrencyMode.Reentrant behavior.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="af9d7-119">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="af9d7-119">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="af9d7-120">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)</span><span class="sxs-lookup"><span data-stu-id="af9d7-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="af9d7-121">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="af9d7-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="af9d7-122">Pour exécuter l’échantillon dans une configuration mono-ou cross-machine, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="af9d7-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="af9d7-123">Illustre le</span><span class="sxs-lookup"><span data-stu-id="af9d7-123">Demonstrates</span></span>  
 <span data-ttu-id="af9d7-124">Pour exécuter l'exemple et générer les projets de client et de serveur.</span><span class="sxs-lookup"><span data-stu-id="af9d7-124">To run the sample, build the client and server projects.</span></span> <span data-ttu-id="af9d7-125">Ouvrez ensuite deux fenêtres de commande \<et modifiez les répertoires pour l’échantillon \<>-CS-Service-bin-debug et échantillonnez>-CS-Client-bin-debug répertoires.</span><span class="sxs-lookup"><span data-stu-id="af9d7-125">Then open two command windows and change the directories to the \<sample>\CS\Service\bin\debug and \<sample>\CS\Client\bin\debug directories.</span></span> <span data-ttu-id="af9d7-126">Ensuite, commencez le `service.exe` service en tapant, puis invoquez le Client.exe avec la valeur initiale des tiques passées comme un argument d’entrée.</span><span class="sxs-lookup"><span data-stu-id="af9d7-126">Then start the service by typing `service.exe` and then invoke the Client.exe with the initial value of ticks passed as an input argument.</span></span> <span data-ttu-id="af9d7-127">Le code suivant illustre le résultat pour 10 cycles.</span><span class="sxs-lookup"><span data-stu-id="af9d7-127">A sample output for 10 ticks is shown.</span></span>  
  
```console  
Prompt>Service.exe  
ServiceHost Started. Press Enter to terminate service.  
Ping: Ticks = 10  
Ping: Ticks = 8  
Ping: Ticks = 6  
Ping: Ticks = 4  
Ping: Ticks = 2  
Ping: Ticks = 0  
  
Prompt>Client.exe 10  
Pong: Ticks = 9  
Pong: Ticks = 7  
Pong: Ticks = 5  
Pong: Ticks = 3  
Pong: Ticks = 1  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="af9d7-128">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="af9d7-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="af9d7-129">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="af9d7-129">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="af9d7-130">Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons.</span><span class="sxs-lookup"><span data-stu-id="af9d7-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="af9d7-131">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="af9d7-131">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
