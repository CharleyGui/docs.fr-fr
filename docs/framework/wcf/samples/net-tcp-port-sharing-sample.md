---
title: Net.TCP Port Sharing, exemple
ms.date: 03/30/2017
ms.assetid: 03da5959-0574-4e91-8a53-05854b6c55dc
ms.openlocfilehash: 62642daffb7e41fb4e023bdd18c221c9dcfd9f2f
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65876380"
---
# <a name="nettcp-port-sharing-sample"></a>Net.TCP Port Sharing, exemple
Le protocole TCP/IP utilise un numéro à 16 bits, appelé un port, pour différencier des connexions vers des applications réseau multiples qui s'exécutent sur le même ordinateur. Si une application écoute un port, tout le trafic TCP de ce port va à cette application. Les autres applications ne peuvent pas écouter en même temps ce port.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples de Windows Workflow Foundation (WF) pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples. Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\PortSharing`  
  
 De nombreux protocoles utilisent un numéro de port standard ou par défaut. Par exemple, le protocole HTTP utilise en général le port TCP 80. Internet Information Services (IIS) a un écouteur qui partage un port entre plusieurs applications HTTP. IIS écoute directement le port et envoie les messages à l'application appropriée en fonction des informations du flux de messages. Cela permet à plusieurs applications HTTP d'utiliser le même numéro de port sans devoir rivaliser pour réserver le port pour recevoir des messages.  
  
 Partage de ports NetTcp est une fonctionnalité de Windows Communication Foundation (WCF) qui permet même de plusieurs applications de réseau de partager un port unique. Le service de partage de ports NetTcp accepte les connexions utilisant le protocole net.tcp et transfère les messages en fonction de leur adresse de destination.  
  
 Le service de partage de ports NetTcp n'est pas activé par défaut. Avant d'exécuter cet exemple, vous devez activer le service manuellement. Pour plus d'informations, voir [Procédure : Activer le Service de partage de ports Net.TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md). Si le service est désactivé, une exception est levée lorsque l'application serveur est démarrée.  
  
```  
Unhandled Exception: System.ServiceModel.CommunicationException: The TransportManager failed to listen on the supplied URI using the NetTcpPortSharing service: failed to start the service because it is disabled. An administrator can enable it by running 'sc.exe config NetTcpPortSharing start= demand'.. ---> System.InvalidOperationException: Cannot start service NetTcpPortSharing on computer '.'. ---> System.ComponentModel.Win32Exception: The service cannot be started, either because it is disabled or because it has no enabled devices associated with it  
```  
  
 Le partage de ports est activé sur le serveur en définissant la propriété <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> de la liaison <xref:System.ServiceModel.NetTcpBinding> ou de l'élément de liaison <xref:System.ServiceModel.Channels.TcpTransportBindingElement>. Le client n'a pas besoin de savoir comment le partage de ports a été configuré pour l'utiliser sur le serveur.  
  
## <a name="enabling-port-sharing"></a>Activation du partage de ports  
 Le code suivant illustre l'activation du partage de ports sur le serveur. Il démarre une instance du service `ICalculator` sur un port fixe avec un chemin d’accès URI aléatoire. Bien que deux services puissent partager le même port, leurs adresses de point de terminaison globales doivent demeurer uniques afin que le service de partage de ports NetTcp puisse router les messages vers l'application qui convient.  

```csharp
// Configure a binding with TCP port sharing enabled  
NetTcpBinding binding = new NetTcpBinding();  
binding.PortSharingEnabled = true;  
  
// Start a service on a fixed TCP port  
ServiceHost host = new ServiceHost(typeof(CalculatorService));  
ushort salt = (ushort)new Random().Next();  
string address = $"net.tcp://localhost:9000/calculator/{salt}";
host.AddServiceEndpoint(typeof(ICalculator), binding, address);  
host.Open();  
```

 Avec le partage de ports activé, vous pouvez exécuter plusieurs fois le service sans conflit de numéro de port. Si vous modifiez le code pour désactiver le partage de ports, le fait de démarrer deux copies des résultats du service fait échouer la seconde avec une <xref:System.ServiceModel.AddressAlreadyInUseException>.  
  
```  
Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000.  Make sure that you are not trying to use this endpoint multiple times in your application and that there are no other applications listening on this endpoint. ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted  
```  
  
## <a name="running-the-sample"></a>Exécution de l'exemple  
 Vous pouvez utiliser le client test pour vérifier que les messages sont correctement routés aux services qui partagent le port.  

```csharp
class client  
{  
   static void Main(string[] args)  
   {  
      Console.Write("Enter the service number to test: ");  
      ushort salt = ushort.Parse(Console.ReadLine());  
      string address = $"net.tcp://localhost:9000/calculator/{salt}";
      ChannelFactory<ICalculator> factory = new ChannelFactory<ICalculator>(new NetTcpBinding());  
      ICalculator proxy = factory.CreateChannel(new EndpointAddress(address));  
  
      // Call the Add service operation.  
      double value1 = 100.00D;  
      double value2 = 15.99D;  
      double result = proxy.Add(value1, value2);  
      Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Subtract service operation.  
      value1 = 145.00D;  
      value2 = 76.54D;  
      result = proxy.Subtract(value1, value2);  
      Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Multiply service operation.  
      value1 = 9.00D;  
      value2 = 81.25D;  
      result = proxy.Multiply(value1, value2);  
      Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Divide service operation.  
      value1 = 22.00D;  
      value2 = 7.00D;  
      result = proxy.Divide(value1, value2);  
      Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
      Console.WriteLine();  
      Console.WriteLine("Press <ENTER> to terminate client.");  
      Console.ReadLine();  
  
      factory.Close();  
   }  
}  
```

 Chaque instance du service imprime son nombre et adresse uniques. Par exemple, vous pouvez voir le texte suivant lorsque vous exécutez service.exe.  
  
```  
Service #4381 listening on net.tcp://localhost:9000/calculator/4381.  
Press <ENTER> to terminate service.  
```  
  
 Entrez le numéro de service que vous voyez lorsque vous exécutez client.exe.  
  
```  
Enter the service number to test: 4381  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 Cet exemple peut être exécuté dans une configuration à plusieurs ordinateurs en modifiant l'adresse générée que le client utilise. Dans Client.cs, modifiez la chaîne de mise en forme de l'adresse du point de terminaison pour la faire correspondre à la nouvelle adresse de votre service. Remplacez toute référence au « localhost » par l'adresse IP de l'ordinateur serveur. Vous devez recompiler l'exemple après avoir apporté cette modification.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Installer ASP.NET 4.0 à l’aide de la commande suivante.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Vérifiez que vous avez effectué la [procédure d’installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Activez le service de partage de ports NetTcp comme décrit précédemment dans la section d'introduction.  
  
4. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5. Pour exécuter l’exemple dans une configuration unique ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md). Les détails d'exécution spécifiques de cet exemple sont inclus dans la section Exécution de l'exemple ci-dessus.  
