---
title: Poison Message Handling in MSMQ 4,0
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: 4b662094923c85e825edcc9025a73f1a1b42cb9b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144238"
---
# <a name="poison-message-handling-in-msmq-40"></a>Poison Message Handling in MSMQ 4,0
Cet exemple montre comment assurer la gestion des messages incohérents dans un service. Cet échantillon est basé sur l’échantillon [de liaison DE LA MSMQ transigée.](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) Cet exemple utilise `netMsmqBinding`. Le service est une application console auto-hébergée qui permet d'observer le service qui reçoit les messages mis en file d'attente.

 Dans le cadre d'une communication en file d'attente, le client communique avec le service à l'aide d'une file d'attente. Cela signifie que le client envoie ses messages à cette file d'attente. Le service reçoit des messages de la file d'attente. Par conséquent, dans le cadre d'une communication en file d'attente, il n'est pas nécessaire que le service et le client s'exécutent simultanément.

 Un message incohérent est un message qui est lu à plusieurs reprises à partir d’une file d’attente lorsque le service qui le lit ne parvient pas à le traiter et met donc fin à la transaction sous laquelle le message est lu. Dans ce cas, le message est de nouveau réessayé. Cela peut théoriquement continuer indéfiniment en cas de problème avec le message. Cela ne peut se produire que lorsque vous utilisez des transactions pour lire à partir de la file d’attente et invoquer l’opération de service.

 Selon la version de MSMQ, NetMsmqBinding prend en charge la détection limitée ou complète des messages incohérents. Une fois que le message a été détecté comme étant incohérent, il est ensuite traité de plusieurs façons. À nouveau, NetMsmqBinding prend en charge la gestion limitée à la gestion complète de messages incohérents selon la version de MSMQ.

 Cet exemple illustre les installations de poison limitées fournies sur Windows Server 2003 et la plate-forme Windows XP et les installations complètes de poison fournies sur Windows Vista. Dans les deux échantillons, l’objectif est de déplacer le message empoisonné hors de la file d’attente vers une autre file d’attente. Cette file d’attente peut alors être desservie par un service de message empoisonné.

## <a name="msmq-v40-poison-handling-sample"></a>Exemple de gestion de message incohérent dans MSMQ v4.0
 Dans Windows Vista, MSMQ fournit une installation de sous-queue empoisonnée qui peut être utilisée pour stocker les messages empoisonnés. Cet exemple démontre la meilleure pratique de traiter les messages toxiques à l’aide de Windows Vista.

 La détection de messages empoisonnés dans Windows Vista est sophistiquée. Il existe 3 propriétés qui aident à la détection. <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> est nombre de fois qu'un message donné est relu à partir de la file d'attente et est distribué à l'application pour traitement. Un message est relu à partir de la file d'attente lorsqu'il est remis dans celle-ci parce qu'il ne peut pas être distribué à l'application ou l'application restaure la transaction dans l'opération de service. <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> est le nombre de fois où le message est déplacé vers la file d'attente des nouvelles tentatives. Lorsque <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> est atteint, le message est déplacé dans la file d'attente des nouvelles tentatives. La propriété <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> correspond à l'intervalle après lequel le message est déplacé de la file d'attente des nouvelles tentatives vers la file d'attente principale. La propriété <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> est réinitialisée à 0. Le message est réessayé. Si toutes les tentatives de lecture du message ont échoué, le message est alors marqué comme étant incohérent.

 Une fois que le message est marqué comme étant incohérent, il est traité en fonction des paramètres dans l'énumération <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A>. Pour rappeler les valeurs possibles :

- Fault (valeur par défaut) : provoque l'échec de l'écouteur ainsi que de l'hôte de service.

- Drop : permet de supprimer le message.

- Déplacer: Pour déplacer le message vers le sous-que du message empoisonné. Cette valeur n’est disponible que sur Windows Vista.

- Reject : permet de rejeter le message en le renvoyant dans la file d'attente de lettres mortes de l'expéditeur. Cette valeur n’est disponible que sur Windows Vista.

 L'exemple montre comment utiliser la disposition `Move` pour le message incohérent. `Move`provoque le message de se déplacer à la sous-que du poison.

 Le contrat de service est `IOrderProcessor`, qui définit un service monodirectionnel qui peut être utilisé avec des files d'attente.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 L'opération de service affiche un message indiquant qu'elle traite la commande. Pour démontrer la fonctionnalité du `SubmitPurchaseOrder` message empoisonné, l’opération de service fait une exception pour annuler la transaction sur une invocation aléatoire du service. Le message est alors remis dans la file d'attente. Le message est par la suite marqué comme étant incohérent. La configuration est définie pour déplacer le message de poison vers la sous-que de poison.

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
public class OrderProcessorService : IOrderProcessor
{
    static Random r = new Random(137);

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {

        int randomNumber = r.Next(10);

        if (randomNumber % 2 == 0)
        {
            Orders.Add(po);
            Console.WriteLine("Processing {0} ", po);
        }
        else
        {
            Console.WriteLine("Aborting transaction, cannot process purchase order: " + po.PONumber);
            Console.WriteLine();
            throw new Exception("Cannot process purchase order: " + po.PONumber);
        }
    }

    public static void OnServiceFaulted(object sender, EventArgs e)
    {
        Console.WriteLine("Service Faulted");
    }

    // Host the service within this EXE console application.
    public static void Main()
    {
        // Get MSMQ queue name from app settings in configuration.
        string queueName = ConfigurationManager.AppSettings["queueName"];

        // Create the transacted MSMQ queue if necessary.
        if (!System.Messaging.MessageQueue.Exists(queueName))
            System.Messaging.MessageQueue.Create(queueName, true);

        // Get the base address that is used to listen for WS-MetaDataExchange requests.
        // This is useful to generate a proxy for the client.
        string baseAddress = ConfigurationManager.AppSettings["baseAddress"];

        // Create a ServiceHost for the OrderProcessorService type.
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService), new Uri(baseAddress));

        // Hook on to the service host faulted events.
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);

        // Open the ServiceHostBase to create listeners and start listening for messages.
        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        if(serviceHost.State != CommunicationState.Faulted) {
            serviceHost.Close();
        }

    }
}
```

 La configuration du service inclut les propriétés de message incohérent suivantes : `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay` et `receiveErrorHandling`, comme indiqué dans le fichier de configuration suivant.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <appSettings>
    <!-- Use appSetting to configure MSMQ queue name. -->
    <add key="queueName" value=".\private$\ServiceModelSamplesPoison" />
    <add key="baseAddress" value="http://localhost:8000/orderProcessor/poisonSample"/>
  </appSettings>
  <system.serviceModel>
    <services>
      <service
              name="Microsoft.ServiceModel.Samples.OrderProcessorService">
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison"
                  binding="netMsmqBinding"
                  bindingConfiguration="PoisonBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
      </service>
    </services>

    <bindings>
      <netMsmqBinding>
        <binding name="PoisonBinding"
                 receiveRetryCount="0"
                 maxRetryCycles="1"
                 retryCycleDelay="00:00:05"
                 receiveErrorHandling="Move">
        </binding>
      </netMsmqBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```

## <a name="processing-messages-from-the-poison-message-queue"></a>Traitement des messages de la file d'attente de messages incohérents
 Le service de message incohérent lit les messages de la file d'attente finale de messages incohérents et les traite.

 Les messages de la file d'attente de messages incohérents sont adressés au service de traitement, qui peut être différent du point de terminaison de service de message incohérent. Par conséquent, lorsque le service de messages empoisonnés lit les messages de la file d’attente, la couche du canal WCF trouve l’inadéquation dans les points de terminaison et n’envoie pas le message. Dans ce cas, le message est adressé au service de traitement des commandes mais est reçu par le service de message incohérent. Pour continuer à recevoir le message même s'il est adressé à un autre point de terminaison, nous devons ajouter un `ServiceBehavior` pour filtrer les adresses où le critère de correspondance doit correspondre aux points de terminaison de service auxquels le message est adressé. Cela est nécessaire pour pouvoir traiter les messages que vous lisez à partir de la file d'attente de messages incohérents.

 L'implémentation du service de message incohérent elle-même est très similaire à l'implémentation du service. Elle implémente le contrat et traite les commandes. L'exemple de code se présente comme suit :

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
[ServiceBehavior(AddressFilterMode=AddressFilterMode.Any)]
public class OrderProcessorService : IOrderProcessor
{
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Orders.Add(po);
        Console.WriteLine("Processing {0} ", po);
    }

    public static void OnServiceFaulted(object sender, EventArgs e)
    {
        Console.WriteLine("Service Faulted...exiting app");
        Environment.Exit(1);
    }

    // Host the service within this EXE console application.
    public static void Main()
    {

        // Create a ServiceHost for the OrderProcessorService type.
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService));

        // Hook on to the service host faulted events.
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);

        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The poison message service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        // Close the ServiceHostBase to shutdown the service.
        if(serviceHost.State != CommunicationState.Faulted)
        {
            serviceHost.Close();
        }
    }
```

 Contrairement au service de traitement des commandes qui lit les messages de la file d’attente de commande, le service de messages empoisonnés lit les messages de la sous-voie empoisonnée. La file d’attente de poison est une sous-voie de la file d’attente principale, est nommé «poison» et est automatiquement généré par MSMQ. Pour y accéder, fournissez le nom principal de file d’attente suivi d’un ";" et le nom de sous-queue, dans ce cas -"poison", comme indiqué dans la configuration de l’échantillon suivant.

> [!NOTE]
> Dans l'exemple pour MSMQ v3.0, le nom de la file d'attente de messages incohérents n'est pas une sous-file d'attente, mais la file d'attente vers laquelle nous avons déplacé le message.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.OrderProcessorService">
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison;poison"
                  binding="netMsmqBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" >
        </endpoint>
      </service>
    </services>

  </system.serviceModel>
</configuration>
```

 Lorsque vous exécutez l'exemple, les activités du client, du service et du service de message incohérent s'affichent dans les fenêtres de console. Vous pouvez voir le service recevoir des messages du client. Appuyez sur ENTER dans chaque fenêtre de console pour arrêter les services.

 Le service commence à s'exécuter, à traiter les commandes et à mettre fin au traitement de manière aléatoire. Si le message indique qu'il a traité la commande, vous pouvez réexécuter le client afin d'envoyer un autre message jusqu'à ce que vous constatiez que le service a réellement terminé un message. Selon les paramètres de gestion de message incohérent configurés, une tentative de traitement du message est effectuée avant qu'il ne soit déplacé vers la file d'attente finale de messages incohérents.

```console
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 0f063b71-93e0-42a1-aa3b-bca6c7a89546
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending

Processing Purchase Order: 5ef9a4fa-5a30-4175-b455-2fb1396095fa
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending

Aborting transaction, cannot process purchase order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89
```

 Démarrez le service de message incohérent pour lire le message incohérent de la file d'attente de messages incohérents. Dans cet exemple, le service de message incohérent lit le message et le traite. Vous pouvez voir que la commande fournisseur qui a été terminée et marquée comme étant incohérente est lue par le service de message incohérent.

```console
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple

1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)

2. Si le service est exécuté en premier, il vérifie que la file d'attente existe. Si la file d'attente n'existe pas, le service en crée une. Vous pouvez exécuter le service en premier pour créer la file d'attente, ou en créer une à l'aide du Gestionnaire de files d'attente MSMQ. Procédez comme suit pour créer une file d'attente dans Windows 2008 :

    1. Open Server Manager dans Visual Studio 2012.

    2. Élargissez l’onglet **Caractéristiques.**

    3. Cliquez à droite **Files d’attente de messages privés**, et sélectionnez **Nouveau**, **File d’attente privée**.

    4. Vérifiez la **case Transactionnelle.**

    5. Entrez `ServiceModelSamplesTransacted` comme le nom de la nouvelle file d’attente.

3. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).

4. Pour exécuter l’échantillon dans une configuration d’ordinateur unique ou croisée, modifiez les noms de file d’attente pour refléter le nom d’hôte réel au lieu de localhost et suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).

 Avec le transport de liaison `netMsmqBinding`, la sécurité est activée par défaut. Les propriétés `MsmqAuthenticationMode` et `MsmqProtectionLevel` déterminent toutes deux le type de sécurité du transport. Par défaut, le mode d'authentification a la valeur `Windows` et le niveau de protection a la valeur `Sign`. Pour que MSMQ fournisse la fonctionnalité d’authentification et de signature, il doit faire partie d’un domaine. Si vous exécutez cet exemple sur un ordinateur ne faisant pas partie d'un domaine, vous recevez l'erreur suivante : "Le certificat Message Queuing interne pour l'utilisateur n'existe pas."

#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Pour exécuter l'exemple sur un ordinateur joint à un groupe de travail

1. Si votre ordinateur ne fait pas partie d'un domaine, désactivez la sécurité du transport en affectant `None` au mode d'authentification et au niveau de protection, tel qu'indiqué dans l'exemple de configuration suivant :

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     Assurez-vous que le point de terminaison est associé à la liaison en définissant l'attribut bindingConfiguration du point de terminaison.

2. Assurez-vous de modifier la configuration sur le PoisonMessageServer, le serveur et le client avant d’exécuter l’échantillon.

    > [!NOTE]
    > L'affectation de `security mode` à `None` revient à affecter `MsmqAuthenticationMode` à la sécurité `MsmqProtectionLevel`, `Message` et `None`.  
  
3. Pour que Meta Data Exchange fonctionne, nous enregistrons une URL avec une liaison http. Cela demande que le service soit exécuté dans une fenêtre de commande élevée. Sinon, vous obtenez une `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`exception telle que: .  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`
