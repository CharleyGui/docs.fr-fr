---
title: Exemple Basic
ms.date: 03/30/2017
ms.assetid: c1910bc1-3d0a-4fa6-b12a-4ed6fe759620
ms.openlocfilehash: 2ea5af0a1c05b5632632b2619c0ee4813696d2fc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738169"
---
# <a name="basic-sample"></a>Exemple Basic

Cet exemple montre comment rendre un service détectable, et comment rechercher et appeler un service détectable. Cet exemple est composé de deux projets : service et client.

> [!NOTE]
> Cet exemple implémente la découverte dans le code.  Pour obtenir un exemple qui implémente la découverte dans la configuration, consultez [configuration](../../../../docs/framework/wcf/samples/configuration-sample.md).

## <a name="service"></a>Service

Il s'agit d'une implémentation simple du service de calculatrice. Le code de découverte associé se trouve dans `Main`, où un <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> est ajouté à l'hôte de service et où un <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> est ajouté comme indiqué dans le code suivant.

```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new
      WSHttpBinding(), String.Empty);

    // Make the service discoverable over UDP multicast
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());

    serviceHost.Open();
    // ...
}
```

## <a name="client"></a>Client

Le client utilise un <xref:System.ServiceModel.Discovery.DynamicEndpoint> pour localiser le service. Le <xref:System.ServiceModel.Discovery.DynamicEndpoint>, un point de terminaison standard, résout le point de terminaison du service lorsque le client est ouvert. Dans ce cas, le <xref:System.ServiceModel.Discovery.DynamicEndpoint> recherche le service en se basant sur son contrat. Le <xref:System.ServiceModel.Discovery.DynamicEndpoint> effectue la recherche sur un <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> par défaut. Lorsqu’il trouve un point de terminaison de service, le client se connecte à ce service sur la liaison spécifiée.

```csharp
public static void Main()
{
   DynamicEndpoint dynamicEndpoint = new DynamicEndpoint( ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());
   // ...
}
```

Le client définit une méthode nommée `InvokeCalculatorService` qui utilise la classe <xref:System.ServiceModel.Discovery.DiscoveryClient> pour rechercher des services. Le <xref:System.ServiceModel.Discovery.DynamicEndpoint> hérite de <xref:System.ServiceModel.Description.ServiceEndpoint>, de sorte qu'il peut être passé à la méthode `InvokeCalculatorService`. L'exemple utilise ensuite le <xref:System.ServiceModel.Discovery.DynamicEndpoint> pour créer une instance de `CalculatorServiceClient` et appelle les différentes opérations du service de calculatrice.

```csharp
static void InvokeCalculatorService(ServiceEndpoint serviceEndpoint)
{
   // Create a client
   CalculatorServiceClient client = new CalculatorServiceClient(serviceEndpoint);

   Console.WriteLine("Invoking CalculatorService");
   Console.WriteLine();

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
```

#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple

1. Cet exemple utilise des points de terminaison HTTP et pour exécuter cet exemple, des listes de contrôle d'accès (ACL) d'URL appropriées doivent être ajoutées. Pour plus d’informations, consultez [configuration de http et HTTPS](../feature-details/configuring-http-and-https.md). L'exécution de la commande suivante avec un privilège élevé doit ajouter les ACL appropriées. Vous pouvez substituer vos domaine et nom d’utilisateur aux arguments suivants si la commande ne fonctionne pas telle quelle. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. À l’aide de Visual Studio 2012, ouvrez Basic. sln et générez l’exemple.

3. Exécutez l'application service.exe.

4. Une fois le service démarré, exécutez client.exe.

5. Observez que le client a trouvé le service sans connaître son adresse.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Basic`
