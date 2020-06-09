---
title: Duplex
ms.date: 03/30/2017
helpviewer_keywords:
- Duplex Service Contract
ms.assetid: bc5de6b6-1a63-42a3-919a-67d21bae24e0
ms.openlocfilehash: 77eab6a4975fc67c20558a53f399c7e709215587
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575197"
---
# <a name="duplex"></a>Duplex

L'exemple illustre comment définir et implémenter un contrat duplex. Une communication duplex intervient lorsqu'un client établit une session avec un service et lui fournit un canal lui permettant de lui renvoyer des messages. Cet exemple est basé sur le [prise en main](getting-started-sample.md). Un contrat duplex est défini sous la forme de deux interfaces : l'interface principale pour les communications du client vers le service et l'interface de rappel pour les communications du service vers le client. Dans cet exemple, l'interface `ICalculatorDuplex` permet au client d'effectuer des opérations mathématiques, notamment de calculer le résultat sur une session. Le service retourne des résultats sur l'interface `ICalculatorDuplexCallback`. Un contrat duplex requiert une session, un contexte devant être établi pour mettre en relation l'ensemble des messages échangés entre le client et le service.

> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.

Dans cet exemple, le client est une application console (.exe) et le service est hébergé par les services IIS (Internet Information Services). Le contrat duplex est défini comme suit :

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required,
                 CallbackContract=typeof(ICalculatorDuplexCallback))]
public interface ICalculatorDuplex
{
    [OperationContract(IsOneWay = true)]
    void Clear();
    [OperationContract(IsOneWay = true)]
    void AddTo(double n);
    [OperationContract(IsOneWay = true)]
    void SubtractFrom(double n);
    [OperationContract(IsOneWay = true)]
    void MultiplyBy(double n);
    [OperationContract(IsOneWay = true)]
    void DivideBy(double n);
}

public interface ICalculatorDuplexCallback
{
    [OperationContract(IsOneWay = true)]
    void Result(double result);
    [OperationContract(IsOneWay = true)]
    void Equation(string eqn);
}
```

La classe `CalculatorService` implémente l'interface `ICalculatorDuplex` principale. Le service utilise le mode d'instance <xref:System.ServiceModel.InstanceContextMode.PerSession> pour conserver le résultat de chaque session. Une propriété privée appelée `Callback` est utilisée pour accéder au canal de rappel permettant de communiquer avec le client. Le service utilise le canal de rappel de l'interface de rappel pour répondre aux messages du client.

```csharp
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]
public class CalculatorService : ICalculatorDuplex
{
    double result = 0.0D;
    string equation;

    public CalculatorService()
    {
        equation = result.ToString();
    }

    public void Clear()
    {
        Callback.Equation($"{equation} = {result}");
        equation = result.ToString();
    }

    public void AddTo(double n)
    {
        result += n;
        equation += $" + {n}";
        Callback.Result(result);
    }

    //...

    ICalculatorDuplexCallback Callback
    {
        get
        {
            return OperationContext.Current.GetCallbackChannel<ICalculatorDuplexCallback>();
        }
    }
}
```

Le client doit fournir une classe qui implémente l'interface de rappel du contrat duplex pour permettre la réception des messages envoyés par le service. Dans l'exemple, une classe `CallbackHandler` est définie pour implémenter l'interface `ICalculatorDuplexCallback`.

```csharp
public class CallbackHandler : ICalculatorDuplexCallback
{
   public void Result(double result)
   {
      Console.WriteLine("Result({0})", result);
   }

   public void Equation(string equation)
   {
      Console.WriteLine("Equation({0}", equation);
   }
}
```

Le proxy généré pour le contrat duplex requiert un <xref:System.ServiceModel.InstanceContext> qui doit être fourni lors de la construction. La classe <xref:System.ServiceModel.InstanceContext> est utilisée comme site pour l'objet qui implémente l'interface de rappel et gère les messages envoyés par le service. Une classe <xref:System.ServiceModel.InstanceContext> est construite avec une instance de la classe `CallbackHandler`. Cet objet gère les messages envoyés par le service au client sur l'interface de rappel.

```csharp
// Construct InstanceContext to handle messages on callback interface.
InstanceContext instanceContext = new InstanceContext(new CallbackHandler());

// Create a client.
CalculatorDuplexClient client = new CalculatorDuplexClient(instanceContext);

Console.WriteLine("Press <ENTER> to terminate client once the output is displayed.");
Console.WriteLine();

// Call the AddTo service operation.
double value = 100.00D;
client.AddTo(value);

// Call the SubtractFrom service operation.
value = 50.00D;
client.SubtractFrom(value);

// Call the MultiplyBy service operation.
value = 17.65D;
client.MultiplyBy(value);

// Call the DivideBy service operation.
value = 2.00D;
client.DivideBy(value);

// Complete equation.
client.Clear();

Console.ReadLine();

//Closing the client gracefully closes the connection and cleans up resources.
client.Close();
```

La configuration a été modifiée pour fournir une liaison prenant en charge à la fois la communication de session et la communication duplex. La liaison `wsDualHttpBinding` prend en charge la communication de session et permet la communication duplex en fournissant des connexions HTTP doubles, dans les deux sens de la communication. Sur le service, la seule différence au niveau de la configuration réside dans la liaison utilisée. Sur le client, vous devez configurer une adresse que le serveur peut utiliser afin de se connecter au client, tel qu'illustré dans l'exemple de configuration suivant.

```xml
<client>
  <endpoint name=""
            address="http://localhost/servicemodelsamples/service.svc"
            binding="wsDualHttpBinding"
            bindingConfiguration="DuplexBinding"
            contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />
</client>

<bindings>
  <!-- Configure a binding that support duplex communication. -->
  <wsDualHttpBinding>
    <binding name="DuplexBinding"
             clientBaseAddress="http://localhost:8000/myClient/">
    </binding>
  </wsDualHttpBinding>
</bindings>
```

Lorsque vous exécutez l'exemple, vous pouvez voir les messages retournés au client sur l'interface de rappel transmise par le service. Tous les résultats intermédiaires sont affichés, suivis de l'équation dans son entier une fois toutes les opérations terminées. Appuyez sur ENTER pour arrêter le client.

### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple

1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Pour générer l’édition C#, C++ ou Visual Basic .NET de la solution, suivez les instructions de la [création des exemples de Windows Communication Foundation](building-the-samples.md).

3. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).

    > [!IMPORTANT]
    > Quand vous exécutez le client dans une configuration inter-ordinateurs, veillez à remplacer « localhost » dans l' `address` attribut de l’élément [ \<endpoint> \<client> de](../../configure-apps/file-schema/wcf/endpoint-of-client.md) et l' `clientBaseAddress` attribut de l' [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) élément de l' [\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md) élément par le nom de l’ordinateur approprié, comme indiqué dans l’exemple suivant :

    ```xml
    <client>
        <endpoint name = ""
        address="http://service_machine_name/servicemodelsamples/service.svc"
        ... />
    </client>
    ...
    <wsDualHttpBinding>
        <binding name="DuplexBinding" clientBaseAddress="http://client_machine_name:8000/myClient/">
        </binding>
    </wsDualHttpBinding>
    ```

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Duplex`
