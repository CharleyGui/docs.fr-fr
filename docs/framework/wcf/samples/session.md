---
title: session
ms.date: 03/30/2017
helpviewer_keywords:
- Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
ms.openlocfilehash: 85f1034999fc4cd36075c49bd8f4631bbd283679
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183366"
---
# <a name="session"></a><span data-ttu-id="82e71-102">session</span><span class="sxs-lookup"><span data-stu-id="82e71-102">Session</span></span>
<span data-ttu-id="82e71-103">L'exemple Session montre comment implémenter un contrat qui requiert une session.</span><span class="sxs-lookup"><span data-stu-id="82e71-103">The Session sample demonstrates how to implement a contract that requires a session.</span></span> <span data-ttu-id="82e71-104">Une session fournit le contexte pour effectuer plusieurs opérations.</span><span class="sxs-lookup"><span data-stu-id="82e71-104">A session provides context for performing multiple operations.</span></span> <span data-ttu-id="82e71-105">Cela permet à un service d'associer l'état à une session donnée ; ainsi les opérations suivantes peuvent utiliser l'état d'une opération précédente.</span><span class="sxs-lookup"><span data-stu-id="82e71-105">This allows a service to associate state with a given session, such that subsequent operations can use the state of a previous operation.</span></span> <span data-ttu-id="82e71-106">Cet échantillon est basé sur le [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), qui met en œuvre un service de calculatrice.</span><span class="sxs-lookup"><span data-stu-id="82e71-106">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="82e71-107">Le contrat `ICalculator` a été modifié afin de permettre l'exécution d'un ensemble d'opérations arithmétiques, tout en conservant un résultat en cours.</span><span class="sxs-lookup"><span data-stu-id="82e71-107">The `ICalculator` contract has been modified to allow a set of arithmetic operations to be performed, while keeping a running result.</span></span> <span data-ttu-id="82e71-108">Cette fonctionnalité est définie par le contrat `ICalculatorSession`.</span><span class="sxs-lookup"><span data-stu-id="82e71-108">This functionality is defined by the `ICalculatorSession` contract.</span></span> <span data-ttu-id="82e71-109">Le service maintient l'état pou un client tandis que plusieurs opérations de service sont appelées pour effectuer un calcul.</span><span class="sxs-lookup"><span data-stu-id="82e71-109">The service maintains the state for a client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="82e71-110">Le client peut récupérer le résultat actuel en appelant `Result()` et remettre le résultat à zéro en appelant `Clear()`.</span><span class="sxs-lookup"><span data-stu-id="82e71-110">The client can retrieve the current result by calling `Result()` and clear the result to zero by calling `Clear()`.</span></span>  
  
 <span data-ttu-id="82e71-111">Dans cet exemple, le client est une application console (.exe) et le service est hébergé par les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="82e71-111">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82e71-112">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="82e71-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="82e71-113">Le fait de définir le mode <xref:System.ServiceModel.SessionMode> pour  le contrat `Required` garantit que lorsque le contrat est exposé sur une liaison particulière, la liaison prend en charge les sessions.</span><span class="sxs-lookup"><span data-stu-id="82e71-113">Setting the <xref:System.ServiceModel.SessionMode> of the contract to `Required` ensures that when the contract is exposed over a particular binding, the binding supports sessions.</span></span> <span data-ttu-id="82e71-114">Si la liaison ne prend pas en charge les sessions, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="82e71-114">If the binding does not support sessions an exception is thrown.</span></span> <span data-ttu-id="82e71-115">L'interface `ICalculatorSession` est définie de telle sorte qu'une ou plusieurs opérations puissent être appelées, ce qui modifie le résultat en cours, comme le montre l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="82e71-115">The `ICalculatorSession` interface is defined such that one or more operations can be called, which modifies a running result, as shown in the following sample code.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required)]  
public interface ICalculatorSession  
{  
    [OperationContract(IsOneWay=true)]  
    void Clear();  
    [OperationContract(IsOneWay = true)]  
    void AddTo(double n);  
    [OperationContract(IsOneWay = true)]  
    void SubtractFrom(double n);  
    [OperationContract(IsOneWay = true)]  
    void MultiplyBy(double n);  
    [OperationContract(IsOneWay = true)]  
    void DivideBy(double n);  
    [OperationContract]  
    double Result();  
}  
```  
  
 <span data-ttu-id="82e71-116">Le service utilise le <xref:System.ServiceModel.InstanceContextMode><xref:System.ServiceModel.InstanceContextMode.PerSession> pour lier un contexte d'instance de service donné à chaque session entrante.</span><span class="sxs-lookup"><span data-stu-id="82e71-116">The service uses a <xref:System.ServiceModel.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.PerSession> to bind a given service instance context to each incoming session.</span></span> <span data-ttu-id="82e71-117">Cela permet au service de maintenir le résultat en cours pour chaque session dans une variable membre locale.</span><span class="sxs-lookup"><span data-stu-id="82e71-117">This allows the service to maintain the running result for each session in a local member variable.</span></span>  
  
```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class CalculatorService : ICalculatorSession  
{  
    double result = 0.0D;  
  
    public void Clear()  
    {  result = 0.0D; }  
  
    public void AddTo(double n)  
    {  result += n;   }  
  
    public void SubtractFrom(double n)  
    {  result -= n;   }  
  
    public void MultiplyBy(double n)  
    {  result *= n;   }  
  
    public void DivideBy(double n)  
    {  result /= n;   }  
  
    public double Result()  
    {  return result; }  
}  
```  
  
 <span data-ttu-id="82e71-118">Lorsque vous exécutez l'exemple, le client fait plusieurs demandes au serveur et demande le résultat, qu'il affiche ensuite dans la fenêtre de console cliente.</span><span class="sxs-lookup"><span data-stu-id="82e71-118">When you run the sample, the client makes several requests to the server and requests the result, which it then displays in the client console window.</span></span> <span data-ttu-id="82e71-119">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="82e71-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
(((0 + 100) - 50) * 17.65) / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="82e71-120">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="82e71-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="82e71-121">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)</span><span class="sxs-lookup"><span data-stu-id="82e71-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="82e71-122">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="82e71-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="82e71-123">Pour exécuter l’échantillon dans une configuration mono-ou cross-machine, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="82e71-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="82e71-124">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="82e71-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="82e71-125">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="82e71-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="82e71-126">Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons.</span><span class="sxs-lookup"><span data-stu-id="82e71-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="82e71-127">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="82e71-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  
