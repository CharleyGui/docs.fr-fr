---
title: 'Transport: Custom Transactions over UDP Sample'
ms.date: 03/30/2017
ms.assetid: 6cebf975-41bd-443e-9540-fd2463c3eb23
ms.openlocfilehash: 1a5b6afd7dc078b0e6e270888973b34a91bfdb9f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295663"
---
# <a name="transport-custom-transactions-over-udp-sample"></a><span data-ttu-id="62fe6-102">Transport: Custom Transactions over UDP Sample</span><span class="sxs-lookup"><span data-stu-id="62fe6-102">Transport: Custom Transactions over UDP Sample</span></span>

<span data-ttu-id="62fe6-103">Cet exemple est basé sur l’exemple [transport : UDP](transport-udp.md) dans l'[extensibilité du transport](transport-extensibility.md)Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="62fe6-103">This sample is based on the [Transport: UDP](transport-udp.md) sample in the Windows Communication Foundation (WCF)[Transport Extensibility](transport-extensibility.md).</span></span> <span data-ttu-id="62fe6-104">Il étend l’exemple UDP Transport afin de prendre en charge le flux de transactions personnalisé et présente l’utilisation de la propriété <xref:System.ServiceModel.Channels.TransactionMessageProperty>.</span><span class="sxs-lookup"><span data-stu-id="62fe6-104">It extends the UDP Transport sample to support custom transaction flow and demonstrates the use of the <xref:System.ServiceModel.Channels.TransactionMessageProperty> property.</span></span>  
  
## <a name="code-changes-in-the-udp-transport-sample"></a><span data-ttu-id="62fe6-105">Modifications du code dans l'exemple UDP Transport</span><span class="sxs-lookup"><span data-stu-id="62fe6-105">Code Changes in the UDP Transport Sample</span></span>  

 <span data-ttu-id="62fe6-106">Pour illustrer le flux de transactions, l'exemple modifie le contrat de service de `ICalculatorContract` afin qu'une portée de transaction soit requise pour `CalculatorService.Add()`.</span><span class="sxs-lookup"><span data-stu-id="62fe6-106">To demonstrate transaction flow, the sample changes the service contract for `ICalculatorContract` to require a transaction scope for `CalculatorService.Add()`.</span></span> <span data-ttu-id="62fe6-107">L'exemple ajoute également un paramètre `System.Guid` supplémentaire au contrat de l'opération `Add`.</span><span class="sxs-lookup"><span data-stu-id="62fe6-107">The sample also adds an extra `System.Guid` parameter to the contract of the `Add` operation.</span></span> <span data-ttu-id="62fe6-108">Ce paramètre permet de transmettre l’identificateur de la transaction cliente au service.</span><span class="sxs-lookup"><span data-stu-id="62fe6-108">This parameter is used to pass the identifier of the client transaction to the service.</span></span>  
  
```csharp  
class CalculatorService : IDatagramContract, ICalculatorContract  
{  
    [OperationBehavior(TransactionScopeRequired=true)]  
    public int Add(int x, int y, Guid clientTransactionId)  
    {  
        if(Transaction.Current.TransactionInformation.DistributedIdentifier == clientTransactionId)  
    {  
        Console.WriteLine("The client transaction has flowed to the service");  
    }  
    else  
    {  
     Console.WriteLine("The client transaction has NOT flowed to the service");  
    }  
  
    Console.WriteLine("   adding {0} + {1}", x, y);
    return (x + y);  
    }  
  
    [...]  
}  
```  
  
 <span data-ttu-id="62fe6-109">L’exemple [transport : UDP](transport-udp.md) utilise des paquets UDP pour transmettre des messages entre un client et un service.</span><span class="sxs-lookup"><span data-stu-id="62fe6-109">The [Transport: UDP](transport-udp.md) sample uses UDP packets to pass messages between a client and a service.</span></span> <span data-ttu-id="62fe6-110">L' [exemple transport : Custom transport](transport-custom-transactions-over-udp-sample.md) utilise le même mécanisme pour transporter les messages, mais lorsqu’une transaction est passée, elle est insérée dans le paquet UDP avec le message encodé.</span><span class="sxs-lookup"><span data-stu-id="62fe6-110">The [Transport: Custom Transport Sample](transport-custom-transactions-over-udp-sample.md) uses the same mechanism to transport messages, but when a transaction is flowed, it is inserted into the UDP packet along with the encoded message.</span></span>  
  
```csharp  
byte[] txmsgBuffer = TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 <span data-ttu-id="62fe6-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer` est une méthode d'assistance qui contient de nouvelles fonctionnalités permettant de fusionner le jeton de propagation de la transaction actuelle avec l'entité de message, et de le placer dans une mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="62fe6-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer` is a helper method that contains new functionality to merge the propagation token for the current transaction with the message entity and place it into a buffer.</span></span>  
  
 <span data-ttu-id="62fe6-112">Pour le transport de workflow de transaction personnalisé, l’implémentation du client doit connaître les opérations de service qui nécessitent un workflow de transaction et transmettre ces informations à WCF.</span><span class="sxs-lookup"><span data-stu-id="62fe6-112">For custom transaction flow transport, the client implementation must know what service operations require transaction flow and to pass this information to WCF.</span></span> <span data-ttu-id="62fe6-113">Un mécanisme doit également permettre de transmettre la transaction utilisateur à la couche de transport.</span><span class="sxs-lookup"><span data-stu-id="62fe6-113">There should also be a mechanism for transmitting the user transaction to the transport layer.</span></span> <span data-ttu-id="62fe6-114">Cet exemple utilise des « inspecteurs de messages WCF » pour obtenir ces informations.</span><span class="sxs-lookup"><span data-stu-id="62fe6-114">This sample uses "WCF message inspectors" to obtain this information.</span></span> <span data-ttu-id="62fe6-115">L’inspecteur de message client implémenté ici et appelé `TransactionFlowInspector` effectue les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="62fe6-115">The client message inspector implemented here, which is called `TransactionFlowInspector`, performs the following tasks:</span></span>  
  
- <span data-ttu-id="62fe6-116">Il détermine si une transaction doit être transmise pour une action de message donnée (cette opération a lieu dans `IsTxFlowRequiredForThisOperation()`).</span><span class="sxs-lookup"><span data-stu-id="62fe6-116">Determines whether a transaction must be flowed for a given message action (this takes place in `IsTxFlowRequiredForThisOperation()`).</span></span>  
  
- <span data-ttu-id="62fe6-117">Il joint la transaction ambiante actuelle au message à l’aide de `TransactionFlowProperty`, si une transaction doit être transmise (cette opération s’effectue dans `BeforeSendRequest()`).</span><span class="sxs-lookup"><span data-stu-id="62fe6-117">Attaches the current ambient transaction to the message using `TransactionFlowProperty`, if a transaction is required to be flowed (this is done in `BeforeSendRequest()`).</span></span>  
  
```csharp  
public class TransactionFlowInspector : IClientMessageInspector  
{  
   void IClientMessageInspector.AfterReceiveReply(ref           System.ServiceModel.Channels.Message reply, object correlationState)  
  {  
  }  
  
   public object BeforeSendRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel)  
   {  
       // obtain the tx propagation token  
       byte[] propToken = null;
       if (Transaction.Current != null && IsTxFlowRequiredForThisOperation(request.Headers.Action))  
       {  
           try  
           {  
               propToken = TransactionInterop.GetTransmitterPropagationToken(Transaction.Current);  
           }  
           catch (TransactionException e)  
           {  
              throw new CommunicationException("TransactionInterop.GetTransmitterPropagationToken failed.", e);  
           }  
       }  
  
      // set the propToken on the message in a TransactionFlowProperty  
       TransactionFlowProperty.Set(propToken, request);  
  
       return null;
    }  
  }  
  
  static bool IsTxFlowRequiredForThisOperation(String action)  
 {  
       // In general, this should contain logic to identify which operations (actions)      require transaction flow.  
      [...]  
 }  
}  
```  
  
 <span data-ttu-id="62fe6-118">Le `TransactionFlowInspector` lui-même est passé à l'infrastructure à l'aide d'un comportement personnalisé : `TransactionFlowBehavior`.</span><span class="sxs-lookup"><span data-stu-id="62fe6-118">The `TransactionFlowInspector` itself is passed to the framework using a custom behavior: the `TransactionFlowBehavior`.</span></span>  
  
```csharp  
public class TransactionFlowBehavior : IEndpointBehavior  
{  
       public void AddBindingParameters(ServiceEndpoint endpoint,            System.ServiceModel.Channels.BindingParameterCollection bindingParameters)  
      {  
      }  
  
       public void ApplyClientBehavior(ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.ClientRuntime clientRuntime)  
      {  
            TransactionFlowInspector inspector = new TransactionFlowInspector();  
            clientRuntime.MessageInspectors.Add(inspector);  
      }  
  
      public void ApplyDispatchBehavior(ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.EndpointDispatcher endpointDispatcher)  
     {  
     }  
  
      public void Validate(ServiceEndpoint endpoint)  
      {  
      }  
}  
```  
  
 <span data-ttu-id="62fe6-119">Le mécanisme précédent étant en place, le code utilisateur crée un `TransactionScope` avant d'appeler l'opération de service.</span><span class="sxs-lookup"><span data-stu-id="62fe6-119">With the preceding mechanism in place, the user code creates a `TransactionScope` before calling the service operation.</span></span> <span data-ttu-id="62fe6-120">L'inspecteur de message veille à ce que la transaction soit passée au transport si elle doit être transmise à l'opération de service.</span><span class="sxs-lookup"><span data-stu-id="62fe6-120">The message inspector ensures that the transaction is passed to the transport in case it is required to be flowed to the service operation.</span></span>  
  
```csharp  
CalculatorContractClient calculatorClient = new CalculatorContractClient("SampleProfileUdpBinding_ICalculatorContract");  
calculatorClient.Endpoint.Behaviors.Add(new TransactionFlowBehavior());
  
try  
{  
       for (int i = 0; i < 5; ++i)  
      {  
              // call the 'Add' service operation under a transaction scope  
             using (TransactionScope ts = new TransactionScope())  
             {  
        [...]  
        Console.WriteLine(calculatorClient.Add(i, i * 2));  
         }  
      }
       calculatorClient.Close();  
}  
catch (TimeoutException)  
{  
    calculatorClient.Abort();  
}  
catch (CommunicationException)  
{  
    calculatorClient.Abort();  
}  
catch (Exception)  
{  
    calculatorClient.Abort();  
    throw;  
}  
```  
  
 <span data-ttu-id="62fe6-121">Après réception d'un paquet UDP émanant du client, le service désérialise ce paquet afin d'extraire le message et éventuellement une transaction.</span><span class="sxs-lookup"><span data-stu-id="62fe6-121">Upon receiving a UDP packet from the client, the service deserializes it to extract the message and possibly a transaction.</span></span>  
  
```csharp  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 <span data-ttu-id="62fe6-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` est la méthode d'assistance qui annule le processus de sérialisation effectué par `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.</span><span class="sxs-lookup"><span data-stu-id="62fe6-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` is the helper method that reverses the serialization process performed by `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.</span></span>  
  
 <span data-ttu-id="62fe6-123">Si une transaction a été transmise, elle est ajoutée au message dans `TransactionMessageProperty`.</span><span class="sxs-lookup"><span data-stu-id="62fe6-123">If a transaction was flowed in, it is appended to the message in the `TransactionMessageProperty`.</span></span>  
  
```csharp  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 <span data-ttu-id="62fe6-124">Cela garantit que le répartiteur sélectionne la transaction au moment de la distribution et l’utilise lors de l’appel de l’opération de service traitée par le message.</span><span class="sxs-lookup"><span data-stu-id="62fe6-124">This ensures that the dispatcher picks up the transaction at dispatch time and uses it when calling the service operation addressed by the message.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="62fe6-125">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="62fe6-125">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="62fe6-126">Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="62fe6-126">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="62fe6-127">L’exemple actuel doit être exécuté de la même façon que l’exemple [transport : UDP](transport-udp.md) .</span><span class="sxs-lookup"><span data-stu-id="62fe6-127">The current sample should be run similarly to the [Transport: UDP](transport-udp.md) sample.</span></span> <span data-ttu-id="62fe6-128">Pour l'exécuter, démarrez le service avec UdpTestService.exe.</span><span class="sxs-lookup"><span data-stu-id="62fe6-128">To run it, start the service with UdpTestService.exe.</span></span> <span data-ttu-id="62fe6-129">Si vous exécutez Windows Vista, vous devez démarrer le service avec des privilèges élevés.</span><span class="sxs-lookup"><span data-stu-id="62fe6-129">If you are running Windows Vista, you must start the service with elevated privileges.</span></span> <span data-ttu-id="62fe6-130">Pour ce faire, cliquez avec le bouton droit sur UdpTestService.exe dans l’Explorateur de fichiers, puis cliquez sur **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="62fe6-130">To do so, right-click UdpTestService.exe in File Explorer and click **Run as administrator**.</span></span>  
  
3. <span data-ttu-id="62fe6-131">La sortie suivante est alors générée.</span><span class="sxs-lookup"><span data-stu-id="62fe6-131">This produces the following output.</span></span>  
  
    ```console  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4. <span data-ttu-id="62fe6-132">À ce stade, vous pouvez démarrer le client en exécutant UdpTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="62fe6-132">At this time, you can start the client by running UdpTestClient.exe.</span></span> <span data-ttu-id="62fe6-133">La sortie générée par le client se présente comme suit.</span><span class="sxs-lookup"><span data-stu-id="62fe6-133">The output produced by the client is as follows.</span></span>  
  
    ```console
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5. <span data-ttu-id="62fe6-134">La sortie du service se présente comme suit.</span><span class="sxs-lookup"><span data-stu-id="62fe6-134">The service output is as follows.</span></span>  
  
    ```console
    Hello, world!  
    Hello, world!  
    Hello, world!  
    Hello, world!  
    Hello, world!  
    The client transaction has flowed to the service  
       adding 0 + 0  
    The client transaction has flowed to the service  
       adding 1 + 2  
    The client transaction has flowed to the service  
       adding 2 + 4  
    The client transaction has flowed to the service  
       adding 3 + 6  
    The client transaction has flowed to the service  
       adding 4 + 8  
    ```  
  
6. <span data-ttu-id="62fe6-135">L’application de service affiche le message `The client transaction has flowed to the service` si elle peut faire correspondre l’identificateur de transaction envoyé par le client (dans le paramètre `clientTransactionId` de l’opération `CalculatorService.Add()`) à l’identificateur de la transaction de service.</span><span class="sxs-lookup"><span data-stu-id="62fe6-135">The service application displays the message `The client transaction has flowed to the service` if it can match the transaction identifier sent by the client, in the `clientTransactionId` parameter of the `CalculatorService.Add()` operation, to the identifier of the service transaction.</span></span> <span data-ttu-id="62fe6-136">Une correspondance est obtenue uniquement si la transaction cliente est transmise au service.</span><span class="sxs-lookup"><span data-stu-id="62fe6-136">A match is obtained only if the client transaction has flowed to the service.</span></span>  
  
7. <span data-ttu-id="62fe6-137">Pour exécuter l'application cliente sur des points de terminaison publiés à l'aide de la configuration, appuyez sur ENTRÉE dans la fenêtre d'application de service, puis réexécutez le client test.</span><span class="sxs-lookup"><span data-stu-id="62fe6-137">To run the client application against endpoints published using configuration, press ENTER on the service application window and then run the test client again.</span></span> <span data-ttu-id="62fe6-138">La sortie suivante doit s'afficher sur le service.</span><span class="sxs-lookup"><span data-stu-id="62fe6-138">You should see the following output on the service.</span></span>  
  
    ```console  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8. <span data-ttu-id="62fe6-139">L'exécution du client sur le service génère maintenant une sortie similaire à la précédente.</span><span class="sxs-lookup"><span data-stu-id="62fe6-139">Running the client against the service now produces similar output as before.</span></span>  
  
9. <span data-ttu-id="62fe6-140">Pour régénérer la configuration et le code client à l'aide de Svcutil.exe, démarrez l'application de service, puis exécutez la commande Svcutil.exe suivante à partir du répertoire racine de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="62fe6-140">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe command from the root directory of the sample.</span></span>  
  
    ```console  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. <span data-ttu-id="62fe6-141">Svcutil.exe ne générant pas de configuration d’extension de liaison pour `sampleProfileUdpBinding`, vous devez donc l’ajouter manuellement.</span><span class="sxs-lookup"><span data-stu-id="62fe6-141">Note that Svcutil.exe does not generate the binding extension configuration for the `sampleProfileUdpBinding`; you must add it manually.</span></span>  
  
    ```xml  
    <configuration>  
        <system.serviceModel>
            …  
            <extensions>  
                <!-- This was added manually because svcutil.exe does not add this extension to the file -->  
                <bindingExtensions>  
                    <add name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
                </bindingExtensions>  
            </extensions>  
        </system.serviceModel>  
    </configuration>  
    ```  
  
> [!IMPORTANT]
> <span data-ttu-id="62fe6-142">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="62fe6-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="62fe6-143">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="62fe6-143">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="62fe6-144">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="62fe6-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="62fe6-145">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="62fe6-145">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a><span data-ttu-id="62fe6-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62fe6-146">See also</span></span>

- [<span data-ttu-id="62fe6-147">Transport : UDP</span><span class="sxs-lookup"><span data-stu-id="62fe6-147">Transport: UDP</span></span>](transport-udp.md)
