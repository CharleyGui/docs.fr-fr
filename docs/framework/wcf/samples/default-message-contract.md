---
title: Default Message Contract
ms.date: 03/30/2017
helpviewer_keywords:
- Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
ms.openlocfilehash: 46b69697616ad7983daed16f8a180a4da7f61a16
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183767"
---
# <a name="default-message-contract"></a>Default Message Contract
Cet exemple présente un service dans lequel un message personnalisé défini par l'utilisateur est passé à et depuis des opérations de service. Cet échantillon est basé sur le [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) qui implémente une interface de calculatrice comme un service dactylographique. Au lieu des opérations de service individuelles pour l’addition, la soustraction, la multiplication et la division utilisée dans le [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), cet échantillon passe un message personnalisé qui contient à la fois les opérands et l’opérateur, et renvoie le résultat du calcul arithmétique.  
  
 Le client est un programme de console (.exe) et la bibliothèque de service (.dll) est hébergée par les services IIS. L'activité du client est affichée dans la fenêtre de console.  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Dans le service, une opération de service unique est définie et elle accepte et retourne des messages personnalisés de type `MyMessage`. Même si dans cet exemple les messages de demande et de réponse sont du même type, elles peuvent bien évidemment être des contrats de message différents, si nécessaire.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 Le message personnalisé `MyMessage` est défini dans une classe annotée avec les attributs <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> et <xref:System.ServiceModel.MessageBodyMemberAttribute>. Seul le troisième constructeur est utilisé dans cet exemple. L'utilisation de contrats de message vous permet d'exercer un contrôle total sur le message SOAP. Dans cet exemple, l'attribut <xref:System.ServiceModel.MessageHeaderAttribute> permet de placer `Operation` dans un en-tête SOAP. Les opérandes `N1`, `N2` et `Result` apparaissent dans le corps SOAP car ils l’attribut <xref:System.ServiceModel.MessageBodyMemberAttribute> leur est appliqué.  
  
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
  
 La classe d'implémentation contient le code pour l'opération de service `Calculate`. La classe `CalculateService` obtient les opérandes et l'opérateur à partir du message de demande et crée un message de réponse qui contient le résultat du calcul demandé, tel qu'indiqué dans l'exemple de code suivant.  
  
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
  
 Le code client généré pour le client a été créé avec [l’outil ServiceModel Metadata Utility Tool (Svcutil.exe).](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) L'outil crée automatiquement des types de contrats de message dans le code client généré si nécessaire. L'option de commande `/messageContract` peut être spécifiée pour forcer la génération de contrats de message.  
  
```console  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 L'exemple de code suivant présente le client utilisant le message `MyMessage`.  
  
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
  
 Lorsque vous exécutez l'exemple, les calculs s'affichent dans la fenêtre de console du client. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 À ce stade, les messages personnalisés définis par l'utilisateur sont passés entre le client et l'opération de service. Le contrat de message a défini que les opérandes et les résultats étaient dans le corps du message et que l'opérateur était dans un en-tête de message. L'enregistrement des messages peut être configuré afin d'observer cette structure de message.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Pour exécuter l’échantillon dans une configuration mono-ou cross-machine, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
