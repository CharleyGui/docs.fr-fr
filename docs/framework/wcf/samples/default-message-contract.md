---
title: Default Message Contract
ms.date: 03/30/2017
helpviewer_keywords:
- Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
ms.openlocfilehash: 404fd9ddc911327bbc09c65d74da22bd88d08e2e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602568"
---
# <a name="default-message-contract"></a><span data-ttu-id="3ab1e-102">Default Message Contract</span><span class="sxs-lookup"><span data-stu-id="3ab1e-102">Default Message Contract</span></span>
<span data-ttu-id="3ab1e-103">Cet exemple présente un service dans lequel un message personnalisé défini par l'utilisateur est passé à et depuis des opérations de service.</span><span class="sxs-lookup"><span data-stu-id="3ab1e-103">The Default Message Contract sample demonstrates a service where a custom user-defined message is passed to and from service operations.</span></span> <span data-ttu-id="3ab1e-104">Cet exemple est basé sur le [prise en main](getting-started-sample.md) qui implémente une interface de calculatrice en tant que service typé.</span><span class="sxs-lookup"><span data-stu-id="3ab1e-104">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator interface as a typed service.</span></span> <span data-ttu-id="3ab1e-105">Au lieu des opérations de service individuelles pour l’addition, la soustraction, la multiplication et la Division utilisées dans le [prise en main](getting-started-sample.md), cet exemple passe un message personnalisé qui contient à la fois les opérandes et l’opérateur, et retourne le résultat du calcul arithmétique.</span><span class="sxs-lookup"><span data-stu-id="3ab1e-105">Instead of the individual service operations for addition, subtraction, multiplication, and division used in the [Getting Started](getting-started-sample.md), this sample passes a custom message that contains both the operands and the operator, and returns the result of the arithmetic calculation.</span></span>  
  
 <span data-ttu-id="3ab1e-106">Le client est un programme de console (.exe) et la bibliothèque de service (.dll) est hébergée par les services IIS.</span><span class="sxs-lookup"><span data-stu-id="3ab1e-106">The client is a console program (.exe) and the service library (.dll) is hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="3ab1e-107">L'activité du client est affichée dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="3ab1e-107">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3ab1e-108">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="3ab1e-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="3ab1e-109">Dans le service, une opération de service unique est définie et elle accepte et retourne des messages personnalisés de type `MyMessage`.</span><span class="sxs-lookup"><span data-stu-id="3ab1e-109">In the service, a single service operation is defined that accepts and returns custom messages of type `MyMessage`.</span></span> <span data-ttu-id="3ab1e-110">Même si dans cet exemple les messages de demande et de réponse sont du même type, elles peuvent bien évidemment être des contrats de message différents, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="3ab1e-110">Although in this sample the request and response messages are of the same type, they could of course be different message contracts if necessary.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 <span data-ttu-id="3ab1e-111">Le message personnalisé `MyMessage` est défini dans une classe annotée avec les attributs <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> et <xref:System.ServiceModel.MessageBodyMemberAttribute>.</span><span class="sxs-lookup"><span data-stu-id="3ab1e-111">The custom message `MyMessage` is defined in a class annotated with <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="3ab1e-112">Seul le troisième constructeur est utilisé dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="3ab1e-112">Only the third constructor is used in this sample.</span></span> <span data-ttu-id="3ab1e-113">L'utilisation de contrats de message vous permet d'exercer un contrôle total sur le message SOAP.</span><span class="sxs-lookup"><span data-stu-id="3ab1e-113">Using message contracts allows you to exercise full control over the SOAP message.</span></span> <span data-ttu-id="3ab1e-114">Dans cet exemple, l'attribut <xref:System.ServiceModel.MessageHeaderAttribute> permet de placer `Operation` dans un en-tête SOAP.</span><span class="sxs-lookup"><span data-stu-id="3ab1e-114">In this sample, the <xref:System.ServiceModel.MessageHeaderAttribute> attribute is used to put `Operation` in a SOAP header.</span></span> <span data-ttu-id="3ab1e-115">Les opérandes `N1`, `N2` et `Result` apparaissent dans le corps SOAP car ils l’attribut <xref:System.ServiceModel.MessageBodyMemberAttribute> leur est appliqué.</span><span class="sxs-lookup"><span data-stu-id="3ab1e-115">The operands `N1`, `N2` and the `Result` appear within the SOAP body because they have the <xref:System.ServiceModel.MessageBodyMemberAttribute> attribute applied.</span></span>  
  
```csharp
[MessageContract]  
public class MyMessage  
{  
    private string operation;  
    private double n1;  
    private double n2;  
    private double result;  
  
    //Constructor - create an empty message.  
  
    public MyMessage() {}  
  
    //Constructor - create a message and populate its members.  
  
    public MyMessage(double n1, double n2, string operation,
                     double result)  
    {  
        this.n1 = n1;  
        this.n2 = n2;  
        this.operation = operation;  
        this.result = result;  
    }  
  
    //Constructor - create a message from another message.  
  
    public MyMessage(MyMessage message)  
    {  
        this.n1 = message.n1;  
        this.n2 = message.n2;  
        this.operation = message.operation;  
        this.result = message.result;  
    }  
  
    [MessageHeader]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [MessageBodyMember]  
    public double N1  
    {  
        get { return n1; }  
        set { n1 = value; }  
    }  
  
    [MessageBodyMember]  
    public double N2  
    {  
        get { return n2; }  
        set { n2 = value; }  
    }  
  
    [MessageBodyMember]  
    public double Result  
    {  
        get { return result; }  
        set { result = value; }  
    }  
}  
```  
  
 <span data-ttu-id="3ab1e-116">La classe d'implémentation contient le code pour l'opération de service `Calculate`.</span><span class="sxs-lookup"><span data-stu-id="3ab1e-116">The implementation class contains the code for the `Calculate` service operation.</span></span> <span data-ttu-id="3ab1e-117">La classe `CalculateService` obtient les opérandes et l'opérateur à partir du message de demande et crée un message de réponse qui contient le résultat du calcul demandé, tel qu'indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="3ab1e-117">The `CalculateService` class obtains the operands and operator from the request message and creates a response message that contains the result of the requested calculation, as shown in the following sample code.</span></span>  
  
```csharp
// Service class which implements the service contract.  
public class CalculatorService : ICalculator  
{  
    // Perform a calculation.  
  
    public MyMessage Calculate(MyMessage request)  
    {  
        MyMessage response = new MyMessage(request);  
        switch (request.Operation)  
        {  
            case "+":  
                response.Result = request.N1 + request.N2;  
                break;  
            case "-":  
                response.Result = request.N1 - request.N2;  
                break;  
            case "*":  
                response.Result = request.N1 * request.N2;  
                break;  
            case "/":  
                response.Result = request.N1 / request.N2;  
                break;  
            default:  
                response.Result = 0.0D;  
                break;  
        }  
        return response;  
    }  
}  
```  
  
 <span data-ttu-id="3ab1e-118">Le code client généré pour le client a été créé à l’aide de l’outil [ServiceModel Metadata Utility Tool (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) .</span><span class="sxs-lookup"><span data-stu-id="3ab1e-118">The generated client code for the client was created with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span> <span data-ttu-id="3ab1e-119">L'outil crée automatiquement des types de contrats de message dans le code client généré si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="3ab1e-119">The tool automatically creates message contract types in the generated client code if necessary.</span></span> <span data-ttu-id="3ab1e-120">L'option de commande `/messageContract` peut être spécifiée pour forcer la génération de contrats de message.</span><span class="sxs-lookup"><span data-stu-id="3ab1e-120">The `/messageContract` command option may be specified to force the generation of message contracts.</span></span>  
  
```console  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="3ab1e-121">L'exemple de code suivant présente le client utilisant le message `MyMessage`.</span><span class="sxs-lookup"><span data-stu-id="3ab1e-121">The following sample code demonstrates the client using the `MyMessage` message.</span></span>  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
// Perform addition using a typed message.  
  
MyMessage request = new MyMessage()
                    {  
                        N1 = 100D,  
                        N2 = 15.99D,  
                        Operation = "+"  
                    };
MyMessage response = ((ICalculator)client).Calculate(request);  
Console.WriteLine("Add({0},{1}) = {2}", request.N1, request.N2, response.Result);  
```  
  
 <span data-ttu-id="3ab1e-122">Lorsque vous exécutez l'exemple, les calculs s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="3ab1e-122">When you run the sample, the calculations are displayed in the client console window.</span></span> <span data-ttu-id="3ab1e-123">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="3ab1e-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="3ab1e-124">À ce stade, les messages personnalisés définis par l'utilisateur sont passés entre le client et l'opération de service.</span><span class="sxs-lookup"><span data-stu-id="3ab1e-124">At this point, custom user-defined messages have passed between the client and the service operation.</span></span> <span data-ttu-id="3ab1e-125">Le contrat de message a défini que les opérandes et les résultats étaient dans le corps du message et que l'opérateur était dans un en-tête de message.</span><span class="sxs-lookup"><span data-stu-id="3ab1e-125">The message contract defined that the operands and results were in the message body and that the operator was in a message header.</span></span> <span data-ttu-id="3ab1e-126">L'enregistrement des messages peut être configuré afin d'observer cette structure de message.</span><span class="sxs-lookup"><span data-stu-id="3ab1e-126">Message logging can be configured to observe this message structure.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3ab1e-127">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="3ab1e-127">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3ab1e-128">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3ab1e-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3ab1e-129">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3ab1e-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="3ab1e-130">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3ab1e-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3ab1e-131">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3ab1e-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3ab1e-132">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="3ab1e-132">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3ab1e-133">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3ab1e-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3ab1e-134">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="3ab1e-134">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
