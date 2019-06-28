---
title: 'Transport : Transactions personnalisées sur UDP exemple'
ms.date: 03/30/2017
ms.assetid: 6cebf975-41bd-443e-9540-fd2463c3eb23
ms.openlocfilehash: ec6499a8e69c8512c33297ac4477eaafc397d78f
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425524"
---
# <a name="transport-custom-transactions-over-udp-sample"></a>Transport : Transactions personnalisées sur UDP exemple
Cet exemple est basé sur le [Transport : UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemple dans Windows Communication Foundation (WCF)[extensibilité du Transport](../../../../docs/framework/wcf/samples/transport-extensibility.md). Il étend l’exemple UDP Transport afin de prendre en charge le flux de transactions personnalisé et présente l’utilisation de la propriété <xref:System.ServiceModel.Channels.TransactionMessageProperty>.  
  
## <a name="code-changes-in-the-udp-transport-sample"></a>Modifications du code dans l'exemple UDP Transport  
 Pour illustrer le flux de transactions, l'exemple modifie le contrat de service de `ICalculatorContract` afin qu'une portée de transaction soit requise pour `CalculatorService.Add()`. L'exemple ajoute également un paramètre `System.Guid` supplémentaire au contrat de l'opération `Add`. Ce paramètre permet de transmettre l’identificateur de la transaction cliente au service.  
  
```  
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
  
 Le [Transport : UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemple utilise des paquets UDP pour transmettre des messages entre un client et un service. Le [Transport : Exemple de Transport personnalisé](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) utilise le même mécanisme pour transporter des messages, mais lorsqu’une transaction est transmise, elle est insérée dans le paquet UDP avec le message encodé.  
  
```  
byte[] txmsgBuffer =                TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 `TransactionMessageBuffer.WriteTransactionMessageBuffer` est une méthode d'assistance qui contient de nouvelles fonctionnalités permettant de fusionner le jeton de propagation de la transaction actuelle avec l'entité de message, et de le placer dans une mémoire tampon.  
  
 Pour le transport de flux de transaction personnalisée, l’implémentation du client doit connaître les opérations de service nécessitent des flux de transaction et de transmettre ces informations à WCF. Un mécanisme doit également permettre de transmettre la transaction utilisateur à la couche de transport. Cet exemple utilise « Inspecteurs de message WCF » pour obtenir ces informations. L’inspecteur de message client implémenté ici et appelé `TransactionFlowInspector` effectue les tâches suivantes :  
  
- Il détermine si une transaction doit être transmise pour une action de message donnée (cette opération a lieu dans `IsTxFlowRequiredForThisOperation()`).  
  
- Il joint la transaction ambiante actuelle au message à l’aide de `TransactionFlowProperty`, si une transaction doit être transmise (cette opération s’effectue dans `BeforeSendRequest()`).  
  
```  
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
  
 Le `TransactionFlowInspector` lui-même est passé à l'infrastructure à l'aide d'un comportement personnalisé : `TransactionFlowBehavior`.  
  
```  
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
  
 Le mécanisme précédent étant en place, le code utilisateur crée un `TransactionScope` avant d'appeler l'opération de service. L'inspecteur de message veille à ce que la transaction soit passée au transport si elle doit être transmise à l'opération de service.  
  
```  
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
  
 Après réception d'un paquet UDP émanant du client, le service désérialise ce paquet afin d'extraire le message et éventuellement une transaction.  
  
```  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 `TransactionMessageBuffer.ReadTransactionMessageBuffer()` est la méthode d'assistance qui annule le processus de sérialisation effectué par `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.  
  
 Si une transaction a été transmise, elle est ajoutée au message dans `TransactionMessageProperty`.  
  
```  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 Cela garantit que le répartiteur sélectionne la transaction au moment de la distribution et l’utilise lors de l’appel de l’opération de service traitée par le message.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Pour générer la solution, suivez les instructions de [génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. L’exemple actuel doit être exécutée de façon similaire à la [Transport : UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemple. Pour l'exécuter, démarrez le service avec UdpTestService.exe. Si vous exécutez [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], vous devez démarrer le service avec des privilèges élevés. Pour ce faire, cliquez sur UdpTestService.exe dans l’Explorateur de fichiers, puis cliquez sur **exécuter en tant qu’administrateur**.  
  
3. La sortie suivante est alors générée.  
  
    ```  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4. À ce stade, vous pouvez démarrer le client en exécutant UdpTestClient.exe. La sortie générée par le client se présente comme suit.  
  
    ```  
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5. La sortie du service se présente comme suit.  
  
    ```  
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
  
6. L’application de service affiche le message `The client transaction has flowed to the service` si elle peut faire correspondre l’identificateur de transaction envoyé par le client (dans le paramètre `clientTransactionId` de l’opération `CalculatorService.Add()`) à l’identificateur de la transaction de service. Une correspondance est obtenue uniquement si la transaction cliente est transmise au service.  
  
7. Pour exécuter l'application cliente sur des points de terminaison publiés à l'aide de la configuration, appuyez sur ENTRÉE dans la fenêtre d'application de service, puis réexécutez le client test. La sortie suivante doit s'afficher sur le service.  
  
    ```  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8. L'exécution du client sur le service génère maintenant une sortie similaire à la précédente.  
  
9. Pour régénérer la configuration et le code client à l'aide de Svcutil.exe, démarrez l'application de service, puis exécutez la commande Svcutil.exe suivante à partir du répertoire racine de l'exemple.  
  
    ```  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. Svcutil.exe ne générant pas de configuration d’extension de liaison pour `sampleProfileUdpBinding`, vous devez donc l’ajouter manuellement.  
  
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
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples de Windows Workflow Foundation (WF) pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples. Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a>Voir aussi

- [Transport : UDP](../../../../docs/framework/wcf/samples/transport-udp.md)
