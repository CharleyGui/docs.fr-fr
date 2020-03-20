---
title: One-Way
ms.date: 03/30/2017
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
ms.openlocfilehash: 3203762e05c794ed28b65d8fded6972fac1f5820
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183439"
---
# <a name="one-way"></a>One-Way
Cet exemple présente un contact de service avec des opérations de service monodirectionnelles. Le client n'attend pas que les opérations de service se terminent comme c'est le cas avec les opérations de service bidirectionnelles. Cet échantillon est basé sur le `wsHttpBinding` Getting [Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) et utilise la liaison. Le service dans cet exemple est une application console auto-hébergée vous permettant d'observer le service qui reçoit et traite des demandes. Le client est également une application console.  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Pour créer un contrat de service monodirectionnel, définissez votre contrat de service, appliquez la classe <xref:System.ServiceModel.OperationContractAttribute> à chaque opération et affectez <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> à `true`, tel qu'indiqué dans l'exemple de code suivant :  
  
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
  
 Pour montrer que le client n'attend pas que les opérations de service se terminent, le code de service dans cet exemple implémente un délai de cinq secondes, tel qu'indiqué dans l'exemple de code suivant :  
  
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
  
 Lorsque le client appelle le service, l'appel retourne sans attendre que l'opération de service se termine.  
  
 Lorsque vous exécutez l'exemple, les activités du client et du service s'affichent dans leurs fenêtres de console respectives. Vous pouvez voir le service recevoir des messages du client. Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client.  
  
 Le client s'arrête avant le service, ce qui montre qu'un client n'attend pas que les opérations de service monodirectionnelles se terminent. La sortie du client se présente comme suit :  
  
```console  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Press <ENTER> to terminate client.  
```  
  
 La sortie du service se présente comme suit :  
  
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
> HTTP est, par définition, un protocole de demande/réponse ; lorsqu'une demande est effectuée, une réponse est retournée. Cela se vérifie même pour une opération de service monodirectionnelle qui est exposée sur HTTP. Lorsque l'opération est appelée, le service retourne un code d'état HTTP 202 avant que l'opération de service s'exécute. Ce code d'état signifie que la demande a été acceptée pour traitement, mais que le traitement n'est pas encore terminé. Le client qui a appelé l'opération se bloque jusqu'à ce qu'il reçoive la réponse 202 du service. Cela peut provoquer des comportements inattendus lorsque plusieurs messages unidirectionnels sont envoyés à l’aide d’une liaison configurée pour utiliser des sessions. La liaison `wsHttpBinding` utilisée dans cet exemple est configurée pour utiliser des sessions par défaut pour établir un contexte de sécurité. Par défaut, les messages d'une session sont assurés d'arriver dans l'ordre dans lequel ils sont envoyés. De ce fait, lorsque le deuxième message d'une session est envoyé, il n'est pas traité tant que le premier message ne l'a pas été. Il en résulte que le client ne reçoit pas de réponse 202 pour un message tant que le traitement du message précédent n'est pas terminé. Par conséquent, le client se bloque à chaque appel d'opération suivant. Pour éviter ce comportement, cet exemple configure l'exécution pour distribuer les messages simultanément aux différentes instances pour traitement. L'exemple définit <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> à `PerCall` afin que chaque message puisse être traité par une autre instance. <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> est défini à `Multiple` pour permettre à plusieurs threads de distribuer des messages simultanément.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Pour exécuter l’échantillon dans une configuration mono-ou cross-machine, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
> Exécutez le service avant le client et arrêtez le client avant le service. Cela évite au client de lever une exception lorsqu'il ne parvient pas à fermer la session de sécurité correctement du fait que le service a été arrêté.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  
