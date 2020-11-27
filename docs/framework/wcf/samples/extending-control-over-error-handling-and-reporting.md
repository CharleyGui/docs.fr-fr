---
title: Extending Control Over Error Handling and Reporting
ms.date: 03/30/2017
ms.assetid: 45f996a7-fa00-45cb-9d6f-b368f5778aaa
ms.openlocfilehash: 2e9298c6a282b9df8499458ad166e320d41e63a9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283326"
---
# <a name="extending-control-over-error-handling-and-reporting"></a><span data-ttu-id="9dd9f-102">Extending Control Over Error Handling and Reporting</span><span class="sxs-lookup"><span data-stu-id="9dd9f-102">Extending Control Over Error Handling and Reporting</span></span>

<span data-ttu-id="9dd9f-103">Cet exemple montre comment étendre le contrôle sur la gestion des erreurs et le rapport d’erreurs dans un service Windows Communication Foundation (WCF) à l’aide de l' <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span><span class="sxs-lookup"><span data-stu-id="9dd9f-103">This sample demonstrates how to extend control over error handling and error reporting in a Windows Communication Foundation (WCF) service using the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="9dd9f-104">L’exemple est basé sur le [prise en main](getting-started-sample.md) avec un code supplémentaire ajouté au service pour gérer les erreurs.</span><span class="sxs-lookup"><span data-stu-id="9dd9f-104">The sample is based on the [Getting Started](getting-started-sample.md) with some additional code added to the service to handle errors.</span></span> <span data-ttu-id="9dd9f-105">Le client force plusieurs conditions d'erreur.</span><span class="sxs-lookup"><span data-stu-id="9dd9f-105">The client forces several error conditions.</span></span> <span data-ttu-id="9dd9f-106">Le service intercepte les erreurs et les enregistre dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="9dd9f-106">The service intercepts the errors and logs them in a file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9dd9f-107">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="9dd9f-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="9dd9f-108">Les services peuvent intercepter des erreurs, effectuez le traitement, et avoir une influence sur la manière dont les erreurs sont signalées à l'aide de l'interface <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span><span class="sxs-lookup"><span data-stu-id="9dd9f-108">Services can intercept errors, perform processing, and affect how errors are reported using the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="9dd9f-109">L'interface possède deux méthodes qui peuvent être implémentées : <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> et <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>.</span><span class="sxs-lookup"><span data-stu-id="9dd9f-109">The interface has two methods that can be implemented: <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> and <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>.</span></span> <span data-ttu-id="9dd9f-110">La méthode <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> vous permet d'ajouter, de modifier ou de supprimer un message d'erreur généré en réponse à une exception.</span><span class="sxs-lookup"><span data-stu-id="9dd9f-110">The <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> method allows you to add, modify, or suppress a fault message that is generated in response to an exception.</span></span> <span data-ttu-id="9dd9f-111">La méthode <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> permet au traitement des erreurs d'avoir lieu dans l'événement d'une erreur et contrôle l'exécution possible d'autres activités de gestion des erreurs.</span><span class="sxs-lookup"><span data-stu-id="9dd9f-111">The <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> method allows error processing to take place in the event of an error and controls whether additional error handling can run.</span></span>  
  
 <span data-ttu-id="9dd9f-112">Dans cet exemple, le type `CalculatorErrorHandler` implémente l'interface <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span><span class="sxs-lookup"><span data-stu-id="9dd9f-112">In this sample, the `CalculatorErrorHandler` type implements the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="9dd9f-113">Dans la</span><span class="sxs-lookup"><span data-stu-id="9dd9f-113">In the</span></span>  
  
 <span data-ttu-id="9dd9f-114">méthode <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>, le `CalculatorErrorHandler` écrit l'erreur dans un fichier texte Error.txt dans c:\logs.</span><span class="sxs-lookup"><span data-stu-id="9dd9f-114"><xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> method, the `CalculatorErrorHandler` writes a log of the error to an Error.txt text file in c:\logs.</span></span> <span data-ttu-id="9dd9f-115">Notez que l'exemple enregistre l'erreur et ne la supprime pas, ce qui permet de la signaler au client.</span><span class="sxs-lookup"><span data-stu-id="9dd9f-115">Note that the sample logs the fault and does not suppress it, allowing it to be reported back to the client.</span></span>  
  
```csharp
public class CalculatorErrorHandler : IErrorHandler
{
    // Provide a fault. The Message fault parameter can be replaced, or set to
    // null to suppress reporting a fault.

    public void ProvideFault(Exception error, MessageVersion version, ref Message fault)
    {
    }

    // HandleError. Log an error, then allow the error to be handled as usual.
    // Return true if the error is considered as already handled

    public bool HandleError(Exception error)
    {
        using (TextWriter tw = File.AppendText(@"c:\logs\error.txt"))
        {
            if (error != null)
            {
                tw.WriteLine("Exception: " + error.GetType().Name + " - " + error.Message);
            }
            tw.Close();
        }
        return true;
    }
}  
```  
  
 <span data-ttu-id="9dd9f-116">L'`ErrorBehaviorAttribute` existe en tant que mécanisme d'enregistrement d'un gestionnaire d'erreurs avec un service.</span><span class="sxs-lookup"><span data-stu-id="9dd9f-116">The `ErrorBehaviorAttribute` exists as a mechanism to register an error handler with a service.</span></span> <span data-ttu-id="9dd9f-117">Cet attribut prend un paramètre de type unique.</span><span class="sxs-lookup"><span data-stu-id="9dd9f-117">This attribute takes a single type parameter.</span></span> <span data-ttu-id="9dd9f-118">Ce type doit implémenter l'interface <xref:System.ServiceModel.Dispatcher.IErrorHandler> et doit avoir un constructeur vide public.</span><span class="sxs-lookup"><span data-stu-id="9dd9f-118">That type should implement the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface and should have a public, empty constructor.</span></span> <span data-ttu-id="9dd9f-119">L'attribut instancie ensuite une instance de ce type de gestionnaire d'erreurs et l'installe dans le service.</span><span class="sxs-lookup"><span data-stu-id="9dd9f-119">The attribute then instantiates an instance of that error handler type and installs it into the service.</span></span> <span data-ttu-id="9dd9f-120">Il fait ceci en implémentant l'interface <xref:System.ServiceModel.Description.IServiceBehavior> puis en utilisant la méthode <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> pour ajouter des instances du gestionnaire d'erreurs au service.</span><span class="sxs-lookup"><span data-stu-id="9dd9f-120">It does this by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface and then using the <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> method to add instances of the error handler to the service.</span></span>  
  
```csharp
// This attribute can be used to install a custom error handler for a service.  
public class ErrorBehaviorAttribute : Attribute, IServiceBehavior  
{  
    Type errorHandlerType;  
  
    public ErrorBehaviorAttribute(Type errorHandlerType)  
    {  
        this.errorHandlerType = errorHandlerType;  
    }  
  
    void IServiceBehavior.Validate(ServiceDescription description, ServiceHostBase serviceHostBase)  
    {  
    }  
  
    void IServiceBehavior.AddBindingParameters(ServiceDescription description, ServiceHostBase serviceHostBase, System.Collections.ObjectModel.Collection<ServiceEndpoint> endpoints, BindingParameterCollection parameters)  
    {  
    }  
  
    void IServiceBehavior.ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
    {  
        IErrorHandler errorHandler;  
  
        try  
        {  
            errorHandler = (IErrorHandler)Activator.CreateInstance(errorHandlerType);  
        }  
        catch (MissingMethodException e)  
        {  
            throw new ArgumentException("The errorHandlerType specified in the ErrorBehaviorAttribute constructor must have a public empty constructor.", e);  
        }  
        catch (InvalidCastException e)  
        {  
            throw new ArgumentException("The errorHandlerType specified in the ErrorBehaviorAttribute constructor must implement System.ServiceModel.Dispatcher.IErrorHandler.", e);  
        }  
  
        foreach (ChannelDispatcherBase channelDispatcherBase in serviceHostBase.ChannelDispatchers)  
        {  
            ChannelDispatcher channelDispatcher = channelDispatcherBase as ChannelDispatcher;  
            channelDispatcher.ErrorHandlers.Add(errorHandler);  
        }
    }  
}  
```  
  
 <span data-ttu-id="9dd9f-121">L'exemple implémente un service de calculatrice.</span><span class="sxs-lookup"><span data-stu-id="9dd9f-121">The sample implements a calculator service.</span></span> <span data-ttu-id="9dd9f-122">Le client provoque délibérément deux erreurs sur le service en fournissant des paramètres avec des valeurs illégales.</span><span class="sxs-lookup"><span data-stu-id="9dd9f-122">The client deliberately causes two errors to occur on the service by providing parameters with illegal values.</span></span> <span data-ttu-id="9dd9f-123">Le `CalculatorErrorHandler` utilise l'interface <xref:System.ServiceModel.Dispatcher.IErrorHandler> pour enregistrer les erreurs dans un fichier local puis leur permet d'être signalées au client.</span><span class="sxs-lookup"><span data-stu-id="9dd9f-123">The `CalculatorErrorHandler` uses the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface to log the errors to a local file and then allows them to be reported back to the client.</span></span> <span data-ttu-id="9dd9f-124">Le client force une division par zéro et une condition d’argument hors limites.</span><span class="sxs-lookup"><span data-stu-id="9dd9f-124">The client forces a divide by zero and an argument-out-of-range condition.</span></span>  
  
```csharp
try
{  
    Console.WriteLine("Forcing an error in Divide");  
    // Call the Divide service operation - trigger a divide by 0 error.  
    value1 = 22;  
    value2 = 0;  
    result = proxy.Divide(value1, value2);  
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
}  
catch (FaultException e)  
{  
    Console.WriteLine("FaultException: " + e.GetType().Name + " - " + e.Message);  
}  
catch (Exception e)  
{  
    Console.WriteLine("Exception: " + e.GetType().Name + " - " + e.Message);  
}  
```  
  
 <span data-ttu-id="9dd9f-125">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="9dd9f-125">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="9dd9f-126">Vous voyez la division par zéro et les conditions d’argument hors limites qui sont signalées comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="9dd9f-126">You see the division by zero and the argument-out-of-range conditions being reported as faults.</span></span> <span data-ttu-id="9dd9f-127">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="9dd9f-127">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
Forcing an error in Divide  
FaultException: FaultException - Invalid Argument: The second argument must not be zero.  
Forcing an error in Factorial  
FaultException: FaultException - Invalid Argument: The argument must be greater than zero.  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="9dd9f-128">Le fichier c:\logs\errors.txt contient les informations enregistrées à propos des erreurs par le service.</span><span class="sxs-lookup"><span data-stu-id="9dd9f-128">The file c:\logs\errors.txt contains the information logged about the errors by the service.</span></span> <span data-ttu-id="9dd9f-129">Notez que pour que le service écrive dans le répertoire, vous devez vous assurer que le processus sous lequel le service est en cours d’exécution (généralement ASP.NET ou service réseau) a l’autorisation d’écrire dans le répertoire.</span><span class="sxs-lookup"><span data-stu-id="9dd9f-129">Note that for the service to write to the directory you must make sure that the process under which the service is running (typically ASP.NET or Network Service) has permission to write to the directory.</span></span>  
  
```txt
Fault: Reason = Invalid Argument: The second argument must not be zero.  
Fault: Reason = Invalid Argument: The argument must be greater than zero.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9dd9f-130">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="9dd9f-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="9dd9f-131">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9dd9f-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="9dd9f-132">Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9dd9f-132">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="9dd9f-133">Assurez-vous d'avoir créé le répertoire c:\logs pour le fichier error.txt.</span><span class="sxs-lookup"><span data-stu-id="9dd9f-133">Ensure you have created the c:\logs directory for the error.txt file.</span></span> <span data-ttu-id="9dd9f-134">Ou modifiez le nom du fichier utilisé dans `CalculatorErrorHandler.HandleError`.</span><span class="sxs-lookup"><span data-stu-id="9dd9f-134">Or modify the file name used in `CalculatorErrorHandler.HandleError`.</span></span>  
  
4. <span data-ttu-id="9dd9f-135">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9dd9f-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9dd9f-136">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9dd9f-136">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9dd9f-137">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="9dd9f-137">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="9dd9f-138">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9dd9f-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9dd9f-139">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="9dd9f-139">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\ErrorHandling`  
