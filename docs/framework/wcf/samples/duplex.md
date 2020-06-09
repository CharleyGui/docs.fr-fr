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
# <a name="duplex"></a><span data-ttu-id="f8aa3-102">Duplex</span><span class="sxs-lookup"><span data-stu-id="f8aa3-102">Duplex</span></span>

<span data-ttu-id="f8aa3-103">L'exemple illustre comment définir et implémenter un contrat duplex.</span><span class="sxs-lookup"><span data-stu-id="f8aa3-103">The Duplex sample demonstrates how to define and implement a duplex contract.</span></span> <span data-ttu-id="f8aa3-104">Une communication duplex intervient lorsqu'un client établit une session avec un service et lui fournit un canal lui permettant de lui renvoyer des messages.</span><span class="sxs-lookup"><span data-stu-id="f8aa3-104">Duplex communication occurs when a client establishes a session with a service and gives the service a channel on which the service can send messages back to the client.</span></span> <span data-ttu-id="f8aa3-105">Cet exemple est basé sur le [prise en main](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="f8aa3-105">This sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="f8aa3-106">Un contrat duplex est défini sous la forme de deux interfaces : l'interface principale pour les communications du client vers le service et l'interface de rappel pour les communications du service vers le client.</span><span class="sxs-lookup"><span data-stu-id="f8aa3-106">A duplex contract is defined as a pair of interfaces—a primary interface from the client to the service and a callback interface from the service to the client.</span></span> <span data-ttu-id="f8aa3-107">Dans cet exemple, l'interface `ICalculatorDuplex` permet au client d'effectuer des opérations mathématiques, notamment de calculer le résultat sur une session.</span><span class="sxs-lookup"><span data-stu-id="f8aa3-107">In this sample, the `ICalculatorDuplex` interface allows the client to perform math operations, calculating the result over a session.</span></span> <span data-ttu-id="f8aa3-108">Le service retourne des résultats sur l'interface `ICalculatorDuplexCallback`.</span><span class="sxs-lookup"><span data-stu-id="f8aa3-108">The service returns results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="f8aa3-109">Un contrat duplex requiert une session, un contexte devant être établi pour mettre en relation l'ensemble des messages échangés entre le client et le service.</span><span class="sxs-lookup"><span data-stu-id="f8aa3-109">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between the client and the service.</span></span>

> [!NOTE]
> <span data-ttu-id="f8aa3-110">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="f8aa3-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="f8aa3-111">Dans cet exemple, le client est une application console (.exe) et le service est hébergé par les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="f8aa3-111">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="f8aa3-112">Le contrat duplex est défini comme suit :</span><span class="sxs-lookup"><span data-stu-id="f8aa3-112">The duplex contract is defined as follows:</span></span>

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

<span data-ttu-id="f8aa3-113">La classe `CalculatorService` implémente l'interface `ICalculatorDuplex` principale.</span><span class="sxs-lookup"><span data-stu-id="f8aa3-113">The `CalculatorService` class implements the primary `ICalculatorDuplex` interface.</span></span> <span data-ttu-id="f8aa3-114">Le service utilise le mode d'instance <xref:System.ServiceModel.InstanceContextMode.PerSession> pour conserver le résultat de chaque session.</span><span class="sxs-lookup"><span data-stu-id="f8aa3-114">The service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the result for each session.</span></span> <span data-ttu-id="f8aa3-115">Une propriété privée appelée `Callback` est utilisée pour accéder au canal de rappel permettant de communiquer avec le client.</span><span class="sxs-lookup"><span data-stu-id="f8aa3-115">A private property named `Callback` is used to access the callback channel to the client.</span></span> <span data-ttu-id="f8aa3-116">Le service utilise le canal de rappel de l'interface de rappel pour répondre aux messages du client.</span><span class="sxs-lookup"><span data-stu-id="f8aa3-116">The service uses the callback for sending messages back to the client through the callback interface.</span></span>

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

<span data-ttu-id="f8aa3-117">Le client doit fournir une classe qui implémente l'interface de rappel du contrat duplex pour permettre la réception des messages envoyés par le service.</span><span class="sxs-lookup"><span data-stu-id="f8aa3-117">The client must provide a class that implements the callback interface of the duplex contract, for receiving messages from the service.</span></span> <span data-ttu-id="f8aa3-118">Dans l'exemple, une classe `CallbackHandler` est définie pour implémenter l'interface `ICalculatorDuplexCallback`.</span><span class="sxs-lookup"><span data-stu-id="f8aa3-118">In the sample, a `CallbackHandler` class is defined to implement the `ICalculatorDuplexCallback` interface.</span></span>

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

<span data-ttu-id="f8aa3-119">Le proxy généré pour le contrat duplex requiert un <xref:System.ServiceModel.InstanceContext> qui doit être fourni lors de la construction.</span><span class="sxs-lookup"><span data-stu-id="f8aa3-119">The proxy that is generated for a duplex contract requires a <xref:System.ServiceModel.InstanceContext> to be provided upon construction.</span></span> <span data-ttu-id="f8aa3-120">La classe <xref:System.ServiceModel.InstanceContext> est utilisée comme site pour l'objet qui implémente l'interface de rappel et gère les messages envoyés par le service.</span><span class="sxs-lookup"><span data-stu-id="f8aa3-120">This <xref:System.ServiceModel.InstanceContext> is used as the site for an object that implements the callback interface and handles messages that are sent back from the service.</span></span> <span data-ttu-id="f8aa3-121">Une classe <xref:System.ServiceModel.InstanceContext> est construite avec une instance de la classe `CallbackHandler`.</span><span class="sxs-lookup"><span data-stu-id="f8aa3-121">An <xref:System.ServiceModel.InstanceContext> is constructed with an instance of the `CallbackHandler` class.</span></span> <span data-ttu-id="f8aa3-122">Cet objet gère les messages envoyés par le service au client sur l'interface de rappel.</span><span class="sxs-lookup"><span data-stu-id="f8aa3-122">This object handles messages sent from the service to the client on the callback interface.</span></span>

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

<span data-ttu-id="f8aa3-123">La configuration a été modifiée pour fournir une liaison prenant en charge à la fois la communication de session et la communication duplex.</span><span class="sxs-lookup"><span data-stu-id="f8aa3-123">The configuration has been modified to provide a binding that supports both session communication and duplex communication.</span></span> <span data-ttu-id="f8aa3-124">La liaison `wsDualHttpBinding` prend en charge la communication de session et permet la communication duplex en fournissant des connexions HTTP doubles, dans les deux sens de la communication.</span><span class="sxs-lookup"><span data-stu-id="f8aa3-124">The `wsDualHttpBinding` supports session communication and allows duplex communication by providing dual HTTP connections, one for each direction.</span></span> <span data-ttu-id="f8aa3-125">Sur le service, la seule différence au niveau de la configuration réside dans la liaison utilisée.</span><span class="sxs-lookup"><span data-stu-id="f8aa3-125">On the service, the only difference in configuration is the binding that is used.</span></span> <span data-ttu-id="f8aa3-126">Sur le client, vous devez configurer une adresse que le serveur peut utiliser afin de se connecter au client, tel qu'illustré dans l'exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="f8aa3-126">On the client, you must configure an address that the server can use to connect to the client as shown in the following sample configuration.</span></span>

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

<span data-ttu-id="f8aa3-127">Lorsque vous exécutez l'exemple, vous pouvez voir les messages retournés au client sur l'interface de rappel transmise par le service.</span><span class="sxs-lookup"><span data-stu-id="f8aa3-127">When you run the sample, you see the messages that are returned to the client on the callback interface that is sent from the service.</span></span> <span data-ttu-id="f8aa3-128">Tous les résultats intermédiaires sont affichés, suivis de l'équation dans son entier une fois toutes les opérations terminées.</span><span class="sxs-lookup"><span data-stu-id="f8aa3-128">Each intermediate result is displayed, followed by the entire equation upon the completion of all operations.</span></span> <span data-ttu-id="f8aa3-129">Appuyez sur ENTER pour arrêter le client.</span><span class="sxs-lookup"><span data-stu-id="f8aa3-129">Press ENTER to shut down the client.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f8aa3-130">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="f8aa3-130">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="f8aa3-131">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f8aa3-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="f8aa3-132">Pour générer l’édition C#, C++ ou Visual Basic .NET de la solution, suivez les instructions de la [création des exemples de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f8aa3-132">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="f8aa3-133">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f8aa3-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="f8aa3-134">Quand vous exécutez le client dans une configuration inter-ordinateurs, veillez à remplacer « localhost » dans l' `address` attribut de l’élément [ \<endpoint> \<client> de](../../configure-apps/file-schema/wcf/endpoint-of-client.md) et l' `clientBaseAddress` attribut de l' [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) élément de l' [\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md) élément par le nom de l’ordinateur approprié, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="f8aa3-134">When running the client in a cross-machine configuration, be sure to replace "localhost" in both the `address` attribute of the [\<endpoint> of \<client>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element and the `clientBaseAddress` attribute of the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element of the [\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md) element with the name of the appropriate machine, as shown in the following:</span></span>

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
> <span data-ttu-id="f8aa3-135">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f8aa3-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f8aa3-136">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="f8aa3-136">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="f8aa3-137">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f8aa3-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f8aa3-138">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="f8aa3-138">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Duplex`
