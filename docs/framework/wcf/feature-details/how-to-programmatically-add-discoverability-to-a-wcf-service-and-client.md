---
title: 'Procédure : ajouter la détectabilité par programme à un service et un client WCF'
ms.date: 03/30/2017
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
ms.openlocfilehash: bf89c793cbd72a0a3980e6ec8e42c688dcedec26
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344979"
---
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a>Procédure : ajouter la détectabilité par programme à un service et un client WCF
Ce sujet explique comment rendre un service de la Windows Communication Foundation (WCF) détectable. Il est basé sur l’échantillon [d’auto-hôte.](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host)  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a>Pour configurer l'exemple existant de service Self-Host pour la découverte  
  
1. Ouvrez la solution Self-Host dans Visual Studio 2012. L'exemple se trouve dans le répertoire TechnologySamples\Basic\Service\Hosting\SelfHost.  
  
2. Ajoutez au projet du service une référence à `System.ServiceModel.Discovery.dll`. Vous pouvez voir un message d’erreur disant "Système. ServiceModel.Discovery.dll ou l’une de ses dépendances nécessite une version ultérieure du cadre .NET que celui spécifié dans le projet ..." Si vous voyez ce message, cliquez à droite sur le projet dans la Solution Explorer et choisissez **Propriétés**. Dans la fenêtre **Propriétés du projet,** assurez-vous que le **cadre cible** est [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].  
  
3. Ouvrez le fichier Service.cs et ajoutez l'instruction `using` suivante.  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4. Dans la méthode `Main()`, à l'intérieur de l'instruction `using`, ajoutez une instance <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> à l'hôte du service.  
  
    ```csharp  
    public static void Main()  
    {  
        // Create a ServiceHost for the CalculatorService type.  
        using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService)))  
        {  
            // Add a ServiceDiscoveryBehavior  
            serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());
  
            // ...  
        }  
    }  
    ```  
  
     L'instance <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> spécifie que le service auquel elle s'applique est détectable.  
  
5. Ajoutez un objet <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> à l'hôte du service, juste après le code qui ajoute l'instance <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     Ce code spécifie que les messages de découverte doivent être envoyés au point de terminaison de découverte UDP standard.  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a>Pour créer une application cliente utilisant la découverte pour appeler le service  
  
1. Ajoutez à la solution une nouvelle application console nommée `DiscoveryClientApp`.  
  
2. Ajoutez une référence à `System.ServiceModel.dll` et à `System.ServiceModel.Discovery.dll`.  
  
3. Copiez les fichiers GeneratedClient.cs et App.config du projet client existant dans le nouveau projet DiscoveryClientApp. Pour ce faire, cliquez à droite sur les fichiers de la **Solution Explorer**, sélectionnez **Copy**, puis sélectionnez le projet **DiscoveryClientApp,** cliquez à droite et sélectionnez **Pâte**.  
  
4. Ouvrez le fichier Program.cs.  
  
5. Ajoutez les instructions `using` suivantes.  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6. Ajoutez une méthode statique nommée `FindCalculatorServiceAddress()` à la classe `Program`.  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     Cette méthode utilise la découverte pour rechercher le service `CalculatorService`.  
  
7. À l'intérieur de la méthode `FindCalculatorServiceAddress`, créez une instance <xref:System.ServiceModel.Discovery.DiscoveryClient>, en transmettant un objet <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> au constructeur.  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     Cela indique à <xref:System.ServiceModel.Discovery.DiscoveryClient> WCF que la classe devrait utiliser le point de terminaison de découverte UDP standard pour envoyer et recevoir des messages de découverte.  
  
8. Sur la ligne suivante, appelez la méthode <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> et spécifiez une instance <xref:System.ServiceModel.Discovery.FindCriteria> qui contient le contrat de service que vous souhaitez rechercher. Le contrat à spécifier dans le cas présent est `ICalculator`.  
  
    ```csharp  
    // Find ICalculatorService endpoints
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. Après l'appel à la méthode <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, vérifiez s'il existe au moins un service correspondant et retournez l'objet <xref:System.ServiceModel.EndpointAddress> du premier service correspondant. Autrement, retournez une valeur `null`.  
  
    ```csharp  
    if (findResponse.Endpoints.Count > 0)  
    {  
        return findResponse.Endpoints[0].Address;  
    }  
    else  
    {  
        return null;  
    }  
    ```  
  
10. Ajoutez une méthode statique nommée `InvokeCalculatorService` à la classe `Program`.  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     Cette méthode utilise l'adresse du point de terminaison retournée par l'objet `FindCalculatorServiceAddress` pour appeler le service de calculatrice.  
  
11. À l'intérieur de la méthode `InvokeCalculatorService`, créez une instance de la classe `CalculatorServiceClient`. Cette classe est définie par l’échantillon [d’auto-hôte.](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host) Elle a été générée à l'aide de Svcutil.exe.  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. Sur la ligne suivante, définissez l'adresse du point de terminaison du client sur l'adresse du point de terminaison retournée par l'objet `FindCalculatorServiceAddress()`.  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. Immédiatement après le code de l'étape précédente, appelez les méthodes exposées par le service de calculatrice.  
  
    ```csharp  
    Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
  
    // Call the Add service operation.  
    double result = client.Add(value1, value2);  
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation.  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Multiply service operation.  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    result = client.Divide(value1, value2);  
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
    Console.WriteLine();  
  
    //Closing the client gracefully closes the connection and cleans up resources  
    client.Close();  
    ```  
  
14. Ajoutez un code à la méthode `Main()` dans la classe `Program` pour appeler `FindCalculatorServiceAddress`.  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. Sur la ligne suivante, appelez `InvokeCalculatorService()` et passez l'adresse du point de terminaison retournée par `FindCalculatorServiceAddress()`.  
  
    ```csharp  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a>Pour tester l'application  
  
1. Ouvrez une invite de commandes avec élévation de privilèges et exécutez Service.exe.  
  
2. Ouvrez une invite de commandes et exécutez Discoveryclientapp.exe.  
  
3. La sortie de service.exe doit ressembler à la sortie suivante.  
  
    ```output  
    Received Add(100,15.99)  
    Return: 115.99  
    Received Subtract(100,15.99)  
    Return: 84.01  
    Received Multiply(100,15.99)  
    Return: 1599  
    Received Divide(100,15.99)  
    Return: 6.25390869293308  
    ```  
  
4. La sortie de Discoveryclientapp.exe doit ressembler à la sortie suivante.  
  
    ```output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a>Exemple  
 L'intégralité du code utilisé dans cet exemple est présentée ci-dessous. Étant donné que ce code est basé sur l’échantillon [d’auto-hôte,](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host) seuls les fichiers modifiés sont répertoriés. Pour plus d’informations sur l’échantillon d’auto-hôte, voir [Instructions d’installation](https://docs.microsoft.com/dotnet/framework/wcf/samples/set-up-instructions).  
  
```csharp  
// Service.cs  
using System;  
using System.Configuration;  
using System.ServiceModel;  
using System.ServiceModel.Discovery;  
  
namespace Microsoft.ServiceModel.Samples  
{  
    // See SelfHost sample for service contract and implementation  
    // ...  
  
        // Host the service within this EXE console application.  
        public static void Main()  
        {  
            // Create a ServiceHost for the CalculatorService type.  
            using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService)))  
            {  
                // Add the ServiceDiscoveryBehavior to make the service discoverable  
                serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
                serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
  
                // Open the ServiceHost to create listeners and start listening for messages.  
                serviceHost.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
            }  
        }  
    }  
}  
```  
  
```csharp  
// Program.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.ServiceModel;  
using System.ServiceModel.Discovery;  
using Microsoft.ServiceModel.Samples;  
using System.Text;  
  
namespace DiscoveryClientApp  
{  
    class Program  
    {  
        static EndpointAddress FindCalculatorServiceAddress()  
        {  
            // Create DiscoveryClient  
            DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
            // Find ICalculatorService endpoints
            FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
  
            if (findResponse.Endpoints.Count > 0)  
            {  
                return findResponse.Endpoints[0].Address;  
            }  
            else  
            {  
                return null;  
            }  
        }  
  
        static void InvokeCalculatorService(EndpointAddress endpointAddress)  
        {  
            // Create a client  
            CalculatorClient client = new CalculatorClient();  
  
            // Connect to the discovered service endpoint  
            client.Endpoint.Address = endpointAddress;  
  
            Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
            double value1 = 100.00D;  
            double value2 = 15.99D;  
  
            // Call the Add service operation.  
            double result = client.Add(value1, value2);  
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Subtract service operation.  
            result = client.Subtract(value1, value2);  
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Multiply service operation.  
            result = client.Multiply(value1, value2);  
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Divide service operation.  
            result = client.Divide(value1, value2);  
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
            Console.WriteLine();  
  
            //Closing the client gracefully closes the connection and cleans up resources  
            client.Close();  
        }  
        static void Main(string[] args)  
        {  
            EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
  
            if (endpointAddress != null)  
            {  
                InvokeCalculatorService(endpointAddress);  
            }  
  
            Console.WriteLine("Press <ENTER> to exit.");  
            Console.ReadLine();  
  
        }  
    }  
}  
```  

## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble de la découverte WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [Modèle objet de découverte WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)
