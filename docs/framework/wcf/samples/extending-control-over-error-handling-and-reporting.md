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
# <a name="extending-control-over-error-handling-and-reporting"></a>Extending Control Over Error Handling and Reporting

Cet exemple montre comment étendre le contrôle sur la gestion des erreurs et le rapport d’erreurs dans un service Windows Communication Foundation (WCF) à l’aide de l' <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface. L’exemple est basé sur le [prise en main](getting-started-sample.md) avec un code supplémentaire ajouté au service pour gérer les erreurs. Le client force plusieurs conditions d'erreur. Le service intercepte les erreurs et les enregistre dans un fichier.  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Les services peuvent intercepter des erreurs, effectuez le traitement, et avoir une influence sur la manière dont les erreurs sont signalées à l'aide de l'interface <xref:System.ServiceModel.Dispatcher.IErrorHandler>. L'interface possède deux méthodes qui peuvent être implémentées : <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> et <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>. La méthode <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> vous permet d'ajouter, de modifier ou de supprimer un message d'erreur généré en réponse à une exception. La méthode <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> permet au traitement des erreurs d'avoir lieu dans l'événement d'une erreur et contrôle l'exécution possible d'autres activités de gestion des erreurs.  
  
 Dans cet exemple, le type `CalculatorErrorHandler` implémente l'interface <xref:System.ServiceModel.Dispatcher.IErrorHandler>. Dans la  
  
 méthode <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>, le `CalculatorErrorHandler` écrit l'erreur dans un fichier texte Error.txt dans c:\logs. Notez que l'exemple enregistre l'erreur et ne la supprime pas, ce qui permet de la signaler au client.  
  
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
  
 L'`ErrorBehaviorAttribute` existe en tant que mécanisme d'enregistrement d'un gestionnaire d'erreurs avec un service. Cet attribut prend un paramètre de type unique. Ce type doit implémenter l'interface <xref:System.ServiceModel.Dispatcher.IErrorHandler> et doit avoir un constructeur vide public. L'attribut instancie ensuite une instance de ce type de gestionnaire d'erreurs et l'installe dans le service. Il fait ceci en implémentant l'interface <xref:System.ServiceModel.Description.IServiceBehavior> puis en utilisant la méthode <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> pour ajouter des instances du gestionnaire d'erreurs au service.  
  
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
  
 L'exemple implémente un service de calculatrice. Le client provoque délibérément deux erreurs sur le service en fournissant des paramètres avec des valeurs illégales. Le `CalculatorErrorHandler` utilise l'interface <xref:System.ServiceModel.Dispatcher.IErrorHandler> pour enregistrer les erreurs dans un fichier local puis leur permet d'être signalées au client. Le client force une division par zéro et une condition d’argument hors limites.  
  
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
  
 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client. Vous voyez la division par zéro et les conditions d’argument hors limites qui sont signalées comme des erreurs. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.  
  
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
  
 Le fichier c:\logs\errors.txt contient les informations enregistrées à propos des erreurs par le service. Notez que pour que le service écrive dans le répertoire, vous devez vous assurer que le processus sous lequel le service est en cours d’exécution (généralement ASP.NET ou service réseau) a l’autorisation d’écrire dans le répertoire.  
  
```txt
Fault: Reason = Invalid Argument: The second argument must not be zero.  
Fault: Reason = Invalid Argument: The argument must be greater than zero.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).  
  
3. Assurez-vous d'avoir créé le répertoire c:\logs pour le fichier error.txt. Ou modifiez le nom du fichier utilisé dans `CalculatorErrorHandler.HandleError`.  
  
4. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\ErrorHandling`  
