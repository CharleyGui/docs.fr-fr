---
title: 'Procédure : ajouter la détectabilité par programme à un service et un client WCF'
ms.date: 03/30/2017
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
ms.openlocfilehash: dd96bc168413eef99260a5251e74971aa1309ff4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184886"
---
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a><span data-ttu-id="7544c-102">Procédure : ajouter la détectabilité par programme à un service et un client WCF</span><span class="sxs-lookup"><span data-stu-id="7544c-102">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>
<span data-ttu-id="7544c-103">Ce sujet explique comment rendre un service de la Windows Communication Foundation (WCF) détectable.</span><span class="sxs-lookup"><span data-stu-id="7544c-103">This topic explains how to make a Windows Communication Foundation (WCF) service discoverable.</span></span> <span data-ttu-id="7544c-104">Il est basé sur l’échantillon [d’auto-hôte.](https://go.microsoft.com/fwlink/?LinkId=145523)</span><span class="sxs-lookup"><span data-stu-id="7544c-104">It is based on the [Self-Host](https://go.microsoft.com/fwlink/?LinkId=145523) sample.</span></span>  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a><span data-ttu-id="7544c-105">Pour configurer l'exemple existant de service Self-Host pour la découverte</span><span class="sxs-lookup"><span data-stu-id="7544c-105">To configure the existing Self-Host service sample for Discovery</span></span>  
  
1. <span data-ttu-id="7544c-106">Ouvrez la solution Self-Host dans Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="7544c-106">Open the Self-Host solution in Visual Studio 2012.</span></span> <span data-ttu-id="7544c-107">L'exemple se trouve dans le répertoire TechnologySamples\Basic\Service\Hosting\SelfHost.</span><span class="sxs-lookup"><span data-stu-id="7544c-107">The sample is located in the TechnologySamples\Basic\Service\Hosting\SelfHost directory.</span></span>  
  
2. <span data-ttu-id="7544c-108">Ajoutez au projet du service une référence à `System.ServiceModel.Discovery.dll`.</span><span class="sxs-lookup"><span data-stu-id="7544c-108">Add a reference to `System.ServiceModel.Discovery.dll` to the service project.</span></span> <span data-ttu-id="7544c-109">Vous pouvez voir un message d’erreur disant "Système.</span><span class="sxs-lookup"><span data-stu-id="7544c-109">You may see an error message saying "System.</span></span> <span data-ttu-id="7544c-110">ServiceModel.Discovery.dll ou l’une de ses dépendances nécessite une version ultérieure du cadre .NET que celui spécifié dans le projet ..." Si vous voyez ce message, cliquez à droite sur le projet dans la Solution Explorer et choisissez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="7544c-110">ServiceModel.Discovery.dll or one of its dependencies requires a later version of the .NET Framework than the one specified in the project …" If you see this message, right-click the project in the Solution Explorer and choose **Properties**.</span></span> <span data-ttu-id="7544c-111">Dans la fenêtre **Propriétés du projet,** assurez-vous que le **cadre cible** est [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7544c-111">In the **Project Properties** window, make sure that the **Target Framework** is [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
3. <span data-ttu-id="7544c-112">Ouvrez le fichier Service.cs et ajoutez l'instruction `using` suivante.</span><span class="sxs-lookup"><span data-stu-id="7544c-112">Open the Service.cs file and add the following `using` statement.</span></span>  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4. <span data-ttu-id="7544c-113">Dans la méthode `Main()`, à l'intérieur de l'instruction `using`, ajoutez une instance <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> à l'hôte du service.</span><span class="sxs-lookup"><span data-stu-id="7544c-113">In the `Main()` method, inside the `using` statement, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance to the service host.</span></span>  
  
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
  
     <span data-ttu-id="7544c-114">L'instance <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> spécifie que le service auquel elle s'applique est détectable.</span><span class="sxs-lookup"><span data-stu-id="7544c-114">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> specifies that the service it is applied to is discoverable.</span></span>  
  
5. <span data-ttu-id="7544c-115">Ajoutez un objet <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> à l'hôte du service, juste après le code qui ajoute l'instance <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span><span class="sxs-lookup"><span data-stu-id="7544c-115">Add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the service host right after the code that adds the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span>  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     <span data-ttu-id="7544c-116">Ce code spécifie que les messages de découverte doivent être envoyés au point de terminaison de découverte UDP standard.</span><span class="sxs-lookup"><span data-stu-id="7544c-116">This code specifies that discovery messages should be sent to the standard UDP discovery endpoint.</span></span>  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a><span data-ttu-id="7544c-117">Pour créer une application cliente utilisant la découverte pour appeler le service</span><span class="sxs-lookup"><span data-stu-id="7544c-117">To create a client application that uses discovery to call the service</span></span>  
  
1. <span data-ttu-id="7544c-118">Ajoutez à la solution une nouvelle application console nommée `DiscoveryClientApp`.</span><span class="sxs-lookup"><span data-stu-id="7544c-118">Add a new console application to the solution called `DiscoveryClientApp`.</span></span>  
  
2. <span data-ttu-id="7544c-119">Ajoutez une référence à `System.ServiceModel.dll` et à `System.ServiceModel.Discovery.dll`.</span><span class="sxs-lookup"><span data-stu-id="7544c-119">Add a reference to `System.ServiceModel.dll` and `System.ServiceModel.Discovery.dll`</span></span>  
  
3. <span data-ttu-id="7544c-120">Copiez les fichiers GeneratedClient.cs et App.config du projet client existant dans le nouveau projet DiscoveryClientApp.</span><span class="sxs-lookup"><span data-stu-id="7544c-120">Copy the GeneratedClient.cs and App.config files from the existing client project to the new DiscoveryClientApp project.</span></span> <span data-ttu-id="7544c-121">Pour ce faire, cliquez à droite sur les fichiers de la **Solution Explorer**, sélectionnez **Copy**, puis sélectionnez le projet **DiscoveryClientApp,** cliquez à droite et sélectionnez **Pâte**.</span><span class="sxs-lookup"><span data-stu-id="7544c-121">To do this, right-click the files in the **Solution Explorer**, select **Copy**, and then select the **DiscoveryClientApp** project, right-click and select **Paste**.</span></span>  
  
4. <span data-ttu-id="7544c-122">Ouvrez le fichier Program.cs.</span><span class="sxs-lookup"><span data-stu-id="7544c-122">Open Program.cs.</span></span>  
  
5. <span data-ttu-id="7544c-123">Ajoutez les instructions `using` suivantes.</span><span class="sxs-lookup"><span data-stu-id="7544c-123">Add the following `using` statements.</span></span>  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6. <span data-ttu-id="7544c-124">Ajoutez une méthode statique nommée `FindCalculatorServiceAddress()` à la classe `Program`.</span><span class="sxs-lookup"><span data-stu-id="7544c-124">Add a static method called `FindCalculatorServiceAddress()` to the `Program` class.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     <span data-ttu-id="7544c-125">Cette méthode utilise la découverte pour rechercher le service `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="7544c-125">This method uses discovery to search for the `CalculatorService` service.</span></span>  
  
7. <span data-ttu-id="7544c-126">À l'intérieur de la méthode `FindCalculatorServiceAddress`, créez une instance <xref:System.ServiceModel.Discovery.DiscoveryClient>, en transmettant un objet <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> au constructeur.</span><span class="sxs-lookup"><span data-stu-id="7544c-126">Inside the `FindCalculatorServiceAddress` method, create a new <xref:System.ServiceModel.Discovery.DiscoveryClient> instance, passing in a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the constructor.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     <span data-ttu-id="7544c-127">Cela indique à <xref:System.ServiceModel.Discovery.DiscoveryClient> WCF que la classe devrait utiliser le point de terminaison de découverte UDP standard pour envoyer et recevoir des messages de découverte.</span><span class="sxs-lookup"><span data-stu-id="7544c-127">This tells WCF that the <xref:System.ServiceModel.Discovery.DiscoveryClient> class should use the standard UDP discovery endpoint to send and receive discovery messages.</span></span>  
  
8. <span data-ttu-id="7544c-128">Sur la ligne suivante, appelez la méthode <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> et spécifiez une instance <xref:System.ServiceModel.Discovery.FindCriteria> qui contient le contrat de service que vous souhaitez rechercher.</span><span class="sxs-lookup"><span data-stu-id="7544c-128">On the next line, call the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method and specify a <xref:System.ServiceModel.Discovery.FindCriteria> instance that contains the service contract you want to search for.</span></span> <span data-ttu-id="7544c-129">Le contrat à spécifier dans le cas présent est `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="7544c-129">In this case, specify `ICalculator`.</span></span>  
  
    ```csharp  
    // Find ICalculatorService endpoints
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. <span data-ttu-id="7544c-130">Après l'appel à la méthode <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, vérifiez s'il existe au moins un service correspondant et retournez l'objet <xref:System.ServiceModel.EndpointAddress> du premier service correspondant.</span><span class="sxs-lookup"><span data-stu-id="7544c-130">After the call to <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, check to see if there is at least one matching service and return the <xref:System.ServiceModel.EndpointAddress> of the first matching service.</span></span> <span data-ttu-id="7544c-131">Autrement, retournez une valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="7544c-131">Otherwise return `null`.</span></span>  
  
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
  
10. <span data-ttu-id="7544c-132">Ajoutez une méthode statique nommée `InvokeCalculatorService` à la classe `Program`.</span><span class="sxs-lookup"><span data-stu-id="7544c-132">Add a static method named `InvokeCalculatorService` to the `Program` class.</span></span>  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     <span data-ttu-id="7544c-133">Cette méthode utilise l'adresse du point de terminaison retournée par l'objet `FindCalculatorServiceAddress` pour appeler le service de calculatrice.</span><span class="sxs-lookup"><span data-stu-id="7544c-133">This method uses the endpoint address returned from `FindCalculatorServiceAddress` to call the calculator service.</span></span>  
  
11. <span data-ttu-id="7544c-134">À l'intérieur de la méthode `InvokeCalculatorService`, créez une instance de la classe `CalculatorServiceClient`.</span><span class="sxs-lookup"><span data-stu-id="7544c-134">Inside the `InvokeCalculatorService` method, create an instance of the `CalculatorServiceClient` class.</span></span> <span data-ttu-id="7544c-135">Cette classe est définie par l’échantillon [d’auto-hôte.](https://go.microsoft.com/fwlink/?LinkId=145523)</span><span class="sxs-lookup"><span data-stu-id="7544c-135">This class is defined by the [Self-Host](https://go.microsoft.com/fwlink/?LinkId=145523) sample.</span></span> <span data-ttu-id="7544c-136">Elle a été générée à l'aide de Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="7544c-136">It was generated using Svcutil.exe.</span></span>  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. <span data-ttu-id="7544c-137">Sur la ligne suivante, définissez l'adresse du point de terminaison du client sur l'adresse du point de terminaison retournée par l'objet `FindCalculatorServiceAddress()`.</span><span class="sxs-lookup"><span data-stu-id="7544c-137">On the next line, set the endpoint address of the client to the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. <span data-ttu-id="7544c-138">Immédiatement après le code de l'étape précédente, appelez les méthodes exposées par le service de calculatrice.</span><span class="sxs-lookup"><span data-stu-id="7544c-138">Immediately after the code for the previous step, call the methods exposed by the calculator service.</span></span>  
  
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
  
14. <span data-ttu-id="7544c-139">Ajoutez un code à la méthode `Main()` dans la classe `Program` pour appeler `FindCalculatorServiceAddress`.</span><span class="sxs-lookup"><span data-stu-id="7544c-139">Add code to the `Main()` method in the `Program` class to call `FindCalculatorServiceAddress`.</span></span>  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. <span data-ttu-id="7544c-140">Sur la ligne suivante, appelez `InvokeCalculatorService()` et passez l'adresse du point de terminaison retournée par `FindCalculatorServiceAddress()`.</span><span class="sxs-lookup"><span data-stu-id="7544c-140">On the next line, call the `InvokeCalculatorService()` and pass in the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a><span data-ttu-id="7544c-141">Pour tester l'application</span><span class="sxs-lookup"><span data-stu-id="7544c-141">To test the application</span></span>  
  
1. <span data-ttu-id="7544c-142">Ouvrez une invite de commandes avec élévation de privilèges et exécutez Service.exe.</span><span class="sxs-lookup"><span data-stu-id="7544c-142">Open an elevated command prompt and run Service.exe.</span></span>  
  
2. <span data-ttu-id="7544c-143">Ouvrez une invite de commandes et exécutez Discoveryclientapp.exe.</span><span class="sxs-lookup"><span data-stu-id="7544c-143">Open a command prompt and run Discoveryclientapp.exe.</span></span>  
  
3. <span data-ttu-id="7544c-144">La sortie de service.exe doit ressembler à la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="7544c-144">The output from service.exe should look like the following output.</span></span>  
  
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
  
4. <span data-ttu-id="7544c-145">La sortie de Discoveryclientapp.exe doit ressembler à la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="7544c-145">The output from Discoveryclientapp.exe should look like the following output.</span></span>  
  
    ```output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a><span data-ttu-id="7544c-146"> Exemple</span><span class="sxs-lookup"><span data-stu-id="7544c-146">Example</span></span>  
 <span data-ttu-id="7544c-147">L'intégralité du code utilisé dans cet exemple est présentée ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="7544c-147">The following is a listing of the code for this sample.</span></span> <span data-ttu-id="7544c-148">Étant donné que ce code est basé sur l’échantillon [d’auto-hôte,](https://go.microsoft.com/fwlink/?LinkId=145523) seuls les fichiers modifiés sont répertoriés.</span><span class="sxs-lookup"><span data-stu-id="7544c-148">Because this code is based on the [Self-Host](https://go.microsoft.com/fwlink/?LinkId=145523) sample, only those files that are changed are listed.</span></span> <span data-ttu-id="7544c-149">Pour plus d’informations sur l’échantillon d’auto-hôte, voir [Instructions d’installation](https://go.microsoft.com/fwlink/?LinkId=145522).</span><span class="sxs-lookup"><span data-stu-id="7544c-149">For more information about the Self-Host sample, see [Setup Instructions](https://go.microsoft.com/fwlink/?LinkId=145522).</span></span>  
  
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

## <a name="see-also"></a><span data-ttu-id="7544c-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7544c-150">See also</span></span>

- [<span data-ttu-id="7544c-151">Vue d'ensemble de la découverte WCF</span><span class="sxs-lookup"><span data-stu-id="7544c-151">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [<span data-ttu-id="7544c-152">Modèle objet de découverte WCF</span><span class="sxs-lookup"><span data-stu-id="7544c-152">WCF Discovery Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)
