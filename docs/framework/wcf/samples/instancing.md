---
title: instanciation
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, instancing sample
- Instancing Sample [Windows Communication Foundation]
ms.assetid: c290fa54-f6ae-45a1-9186-d9504ebc6ee6
ms.openlocfilehash: 37ffbe36b231737ca10b2dc864ad6e5b304b94bc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648316"
---
# <a name="instancing"></a>instanciation
Cet exemple illustre l'utilisation du comportement d'instanciation qui contrôle la manière dont les instances d'une classe de service sont créées en réponse aux demandes du client. L’exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md), qui implémente le `ICalculator` contrat de service. Cet exemple définit un nouveau contrat, `ICalculatorInstance`, lequel hérite d'`ICalculator`. Le contrat spécifié par `ICalculatorInstance` fournit trois opérations supplémentaires pour l'inspection de l'état de l'instance de service. Lorsque vous modifiez le paramètre d'instanciation, vous pouvez observer les changements au niveau du comportement en exécutant le client.  
  
 Dans cet exemple, le client est une application console (.exe) et le service est hébergé par les services IIS (Internet Information Services).  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Les modes d'instanciation disponibles sont les suivants :  
  
- <xref:System.ServiceModel.InstanceContextMode.PerCall>: Une nouvelle instance de service est créée pour chaque demande du client.  
  
- <xref:System.ServiceModel.InstanceContextMode.PerSession>: Une nouvelle instance est créée pour chaque nouvelle session de client et conservée pendant la durée de vie de cette session (nécessite une liaison qui prend en charge de session).  
  
- <xref:System.ServiceModel.InstanceContextMode.Single>: Une seule instance de la classe de service gère toutes les demandes de client pour la durée de vie de l’application.  
  
 La classe de service spécifie le comportement d'instanciation à l'aide de l'attribut `[ServiceBehavior(InstanceContextMode=<setting>)]`, tel qu'illustré dans l'exemple de code suivant. Pour observer le comportement de chacun des modes d'instance, modifiez les lignes commentées. N'oubliez pas de régénérer le service après avoir modifié le mode d'instanciation. Vous n'avez pas à spécifier de paramètres d'instanciation sur le client.  
  
```csharp
// Enable one of the following instance modes to compare instancing behaviors.  
 [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
  
// PerCall creates a new instance for each operation.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerCall)]  
  
// Singleton creates a single instance for application lifetime.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class CalculatorService : ICalculatorInstance  
{  
    static Object syncObject = new object();  
    static int instanceCount;  
    int instanceId;  
    int operationCount;  
  
    public CalculatorService()  
    {  
        lock (syncObject)  
        {  
            instanceCount++;  
            instanceId = instanceCount;  
        }  
    }  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 / n2;  
    }  
  
    public string GetInstanceContextMode()  
    {   // Return the InstanceContextMode of the service  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.InstanceContextMode.ToString();  
    }  
  
    public int GetInstanceId()  
    {   // Return the id for this instance  
        return instanceId;  
    }  
  
    public int GetOperationCount()  
    {   // Return the number of ICalculator operations performed   
        // on this instance  
        lock (syncObject)  
        {  
            return operationCount;  
        }  
    }  
}  
  
static void Main()  
{  
    // Create a client.  
    CalculatorInstanceClient client = new CalculatorInstanceClient();  
    string instanceMode = client.GetInstanceContextMode();  
    Console.WriteLine("InstanceContextMode: {0}", instanceMode);  
    DoCalculations(client);  
  
    // Create a second client.  
    CalculatorInstanceClient client2 = new CalculatorInstanceClient();  
  
    DoCalculations(client2);  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
}  
```  
  
 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client. Le mode d'instance en fonction duquel le service s'exécute s'affiche. Au terme de chaque opération, l'ID de l'instance et le compteur d'opération s'affichent afin de rendre compte du comportement du mode d'instanciation. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Vérifiez que vous avez effectué la [procédure d’installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Pour exécuter l’exemple dans une configuration unique ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples de Windows Workflow Foundation (WF) pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples. Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Instancing`  
