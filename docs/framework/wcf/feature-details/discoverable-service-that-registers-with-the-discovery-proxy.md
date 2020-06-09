---
title: "Procédure : implémenter un service détectable qui s'enregistre avec le proxy de découverte."
ms.date: 03/30/2017
ms.assetid: eb275bc1-535b-44c8-b9f3-0b75e9aa473b
ms.openlocfilehash: bf878dff59a9a258567ff99098b0b3f8761194e2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599228"
---
# <a name="how-to-implement-a-discoverable-service-that-registers-with-the-discovery-proxy"></a><span data-ttu-id="36783-102">Procédure : implémenter un service détectable qui s'enregistre avec le proxy de découverte.</span><span class="sxs-lookup"><span data-stu-id="36783-102">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>
<span data-ttu-id="36783-103">Cette rubrique est la deuxième d'une série de quatre rubriques qui expliquent comment implémenter un proxy de découverte.</span><span class="sxs-lookup"><span data-stu-id="36783-103">This topic is the second of four topics that discusses how to implement a discovery proxy.</span></span> <span data-ttu-id="36783-104">Dans la rubrique précédente, [Comment : implémenter un proxy de découverte](how-to-implement-a-discovery-proxy.md), vous avez implémenté un proxy de découverte.</span><span class="sxs-lookup"><span data-stu-id="36783-104">In the previous topic, [How to: Implement a Discovery Proxy](how-to-implement-a-discovery-proxy.md), you implemented a discovery proxy.</span></span> <span data-ttu-id="36783-105">Dans cette rubrique, vous allez créer un service WCF qui envoie des messages `Hello` d’annonce (et `Bye` ) au proxy de découverte, ce qui lui permet de s’inscrire et d’annuler son inscription auprès du proxy de découverte.</span><span class="sxs-lookup"><span data-stu-id="36783-105">In this topic, you create a WCF service that sends announcement messages (`Hello` and `Bye`) to the discovery proxy, causing it to register and unregister itself with the discovery proxy.</span></span>

### <a name="to-define-the-service-contract"></a><span data-ttu-id="36783-106">Pour définir le contrat de service</span><span class="sxs-lookup"><span data-stu-id="36783-106">To define the service contract</span></span>

1. <span data-ttu-id="36783-107">Ajoutez à la solution `DiscoveryProxyExample` un nouveau projet d'application console nommé `Service`.</span><span class="sxs-lookup"><span data-stu-id="36783-107">Add a new console application project to the `DiscoveryProxyExample` solution called `Service`.</span></span>

2. <span data-ttu-id="36783-108">Ajoutez des références aux assemblys suivants :</span><span class="sxs-lookup"><span data-stu-id="36783-108">Add references to the following assemblies:</span></span>

    1. <span data-ttu-id="36783-109">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="36783-109">System.ServiceModel</span></span>

    2. <span data-ttu-id="36783-110">System.ServiceModel.Discovery</span><span class="sxs-lookup"><span data-stu-id="36783-110">System.ServiceModel.Discovery</span></span>

3. <span data-ttu-id="36783-111">Ajoutez une nouvelle classe au projet nommé `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="36783-111">Add a new class to the project called `CalculatorService`.</span></span>

4. <span data-ttu-id="36783-112">Ajoutez les instructions using suivantes.</span><span class="sxs-lookup"><span data-stu-id="36783-112">Add the following using statements.</span></span>

    ```csharp
    using System;
    using System.ServiceModel;
    ```

5. <span data-ttu-id="36783-113">Dans CalculatorService.cs, définissez le contrat de service.</span><span class="sxs-lookup"><span data-stu-id="36783-113">Within CalculatorService.cs, define the service contract.</span></span>

    ```csharp
    // Define a service contract.
    [ServiceContract(Namespace = "http://Microsoft.Samples.Discovery")]
    public interface ICalculatorService
    {
        [OperationContract]
        double Add(double n1, double n2);
        [OperationContract]
        double Subtract(double n1, double n2);
        [OperationContract]
        double Multiply(double n1, double n2);
        [OperationContract]
        double Divide(double n1, double n2);
    }
    ```

6. <span data-ttu-id="36783-114">Également dans CalculatorService.cs, implémentez le contrat de service.</span><span class="sxs-lookup"><span data-stu-id="36783-114">Also within CalculatorService.cs, implement the service contract.</span></span>

    ```csharp
    // Service class which implements the service contract.
    public class CalculatorService : ICalculatorService
    {
        public double Add(double n1, double n2)
        {
            double result = n1 + n2;
            Console.WriteLine("Received Add({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Subtract(double n1, double n2)
        {
            double result = n1 - n2;
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Multiply(double n1, double n2)
        {
            double result = n1 * n2;
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Divide(double n1, double n2)
        {
            double result = n1 / n2;
            Console.WriteLine("Received Divide({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
    }
    ```

### <a name="to-host-the-service"></a><span data-ttu-id="36783-115">Pour héberger le service</span><span class="sxs-lookup"><span data-stu-id="36783-115">To host the service</span></span>

1. <span data-ttu-id="36783-116">Ouvrez le fichier Program.cs qui a été généré lorsque vous avez créé le projet.</span><span class="sxs-lookup"><span data-stu-id="36783-116">Open the Program.cs file that was generated when you created the project.</span></span>

2. <span data-ttu-id="36783-117">Ajoutez les instructions using suivantes.</span><span class="sxs-lookup"><span data-stu-id="36783-117">Add the following using statements.</span></span>

    ```csharp
    using System;
    using System.ServiceModel;
    using System.ServiceModel.Description;
    using System.ServiceModel.Discovery;
    ```

3. <span data-ttu-id="36783-118">Ajoutez le code suivant dans la méthode `Main()` :</span><span class="sxs-lookup"><span data-stu-id="36783-118">Within the `Main()` method, add the following code:</span></span>

    ```csharp
    // Define the base address of the service
    Uri baseAddress = new Uri("net.tcp://localhost:9002/CalculatorService/" + Guid.NewGuid().ToString());
    // Define the endpoint address where announcement messages will be sent
    Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

    // Create the service host
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);
    try
    {
        // Add a service endpoint
        ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService),
            new NetTcpBinding(), string.Empty);

        // Create an announcement endpoint, which points to the Announcement Endpoint hosted by the proxy service.
        AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(),
            new EndpointAddress(announcementEndpointAddress));

        // Create a ServiceDiscoveryBehavior and add the announcement endpoint
        ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
        serviceDiscoveryBehavior.AnnouncementEndpoints.Add(announcementEndpoint);

        // Add the ServiceDiscoveryBehavior to the service host to make the service discoverable
        serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);

        // Start listening for messages
        serviceHost.Open();

        Console.WriteLine("Calculator Service started at {0}", baseAddress);
        Console.WriteLine();
        Console.WriteLine("Press <ENTER> to terminate the service.");
        Console.WriteLine();
        Console.ReadLine();

        serviceHost.Close();
    }
    catch (CommunicationException e)
    {
        Console.WriteLine(e.Message);
    }
    catch (TimeoutException e)
    {
        Console.WriteLine(e.Message);
    }

    if (serviceHost.State != CommunicationState.Closed)
    {
        Console.WriteLine("Aborting the service...");
        serviceHost.Abort();
    }
    ```

<span data-ttu-id="36783-119">Vous avez terminé l'implémentation d'un service détectable.</span><span class="sxs-lookup"><span data-stu-id="36783-119">You have completed implementing a discoverable service.</span></span> <span data-ttu-id="36783-120">Continuez sur [Comment : implémenter une application cliente qui utilise le proxy de découverte pour rechercher un service](client-app-discovery-proxy-to-find-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="36783-120">Continue on to [How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service](client-app-discovery-proxy-to-find-a-service.md).</span></span>

## <a name="example"></a><span data-ttu-id="36783-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="36783-121">Example</span></span>
 <span data-ttu-id="36783-122">Les éléments suivants représentent l'intégralité du code utilisé dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="36783-122">This is the full listing of the code used in this topic.</span></span>

```csharp
// CalculatorService.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.ServiceModel;

namespace Microsoft.Samples.Discovery
{
    // Define a service contract.
    [ServiceContract(Namespace = "http://Microsoft.Samples.Discovery")]
    public interface ICalculatorService
    {
        [OperationContract]
        double Add(double n1, double n2);
        [OperationContract]
        double Subtract(double n1, double n2);
        [OperationContract]
        double Multiply(double n1, double n2);
        [OperationContract]
        double Divide(double n1, double n2);
    }

    // Service class which implements the service contract.
    public class CalculatorService : ICalculatorService
    {
        public double Add(double n1, double n2)
        {
            double result = n1 + n2;
            Console.WriteLine("Received Add({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
  
        public double Subtract(double n1, double n2)
        {
            double result = n1 - n2;
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Multiply(double n1, double n2)
        {
            double result = n1 * n2;
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Divide(double n1, double n2)
        {
            double result = n1 / n2;
            Console.WriteLine("Received Divide({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
    }
}
```

```csharp
// Program.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.ServiceModel;
using System.ServiceModel.Description;
using System.ServiceModel.Discovery;

namespace Microsoft.Samples.Discovery
{
    class Program
    {
        public static void Main()
        {
            Uri baseAddress = new Uri("net.tcp://localhost:9002/CalculatorService/" + Guid.NewGuid().ToString());
            Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

            ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);
            try
            {
                ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService),
                    new NetTcpBinding(), string.Empty);

                // Create an announcement endpoint, which points to the Announcement Endpoint hosted by the proxy service.
                AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(),
                    new EndpointAddress(announcementEndpointAddress));

                ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
                serviceDiscoveryBehavior.AnnouncementEndpoints.Add(announcementEndpoint);

                // Make the service discoverable
                serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);

                serviceHost.Open();

                Console.WriteLine("Calculator Service started at {0}", baseAddress);
                Console.WriteLine();
                Console.WriteLine("Press <ENTER> to terminate the service.");
                Console.WriteLine();
                Console.ReadLine();

                serviceHost.Close();
            }
            catch (CommunicationException e)
            {
                Console.WriteLine(e.Message);
            }
            catch (TimeoutException e)
            {
                Console.WriteLine(e.Message);
            }

            if (serviceHost.State != CommunicationState.Closed)
            {
                Console.WriteLine("Aborting the service...");
                serviceHost.Abort();
            }
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="36783-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36783-123">See also</span></span>

- [<span data-ttu-id="36783-124">Discovery WCF</span><span class="sxs-lookup"><span data-stu-id="36783-124">WCF Discovery</span></span>](wcf-discovery.md)
- [<span data-ttu-id="36783-125">Procédure : implémenter un proxy de découverte</span><span class="sxs-lookup"><span data-stu-id="36783-125">How to: Implement a Discovery Proxy</span></span>](how-to-implement-a-discovery-proxy.md)
- [<span data-ttu-id="36783-126">Procédure : implémenter une application cliente qui utilise le proxy de découverte pour rechercher un service</span><span class="sxs-lookup"><span data-stu-id="36783-126">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](client-app-discovery-proxy-to-find-a-service.md)
