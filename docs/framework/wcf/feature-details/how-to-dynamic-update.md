---
title: 'Procédure : Mise à jour dynamique'
ms.date: 03/30/2017
ms.assetid: 9b8f6e0d-edab-4a7e-86e3-8c66bebc64bb
ms.openlocfilehash: a12d480163bb579f34d006ae1837ed4392bf47ee
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265542"
---
# <a name="how-to-dynamic-update"></a><span data-ttu-id="243a4-102">Procédure : Mise à jour dynamique</span><span class="sxs-lookup"><span data-stu-id="243a4-102">How To: Dynamic Update</span></span>

<span data-ttu-id="243a4-103">Cette rubrique présente les étapes de base nécessaires pour créer et mettre à jour de manière dynamique la configuration de routage.</span><span class="sxs-lookup"><span data-stu-id="243a4-103">This topic outlines the basic steps required to create and dynamically update the routing configuration.</span></span> <span data-ttu-id="243a4-104">Dans cet exemple, la configuration de routage initiale provient du fichier de configuration et route tous les messages vers le service de calculatrice regularCalc, mais elle est ensuite mise à jour par programme pour modifier le point de terminaison de destination du service roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="243a4-104">In this example, the initial routing configuration is obtained from the configuration file and routes all messages to the regularCalc calculator service; however, it is subsequently updated programmatically in order to change the destination endpoint the roundingCalc service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="243a4-105">Dans de nombreuses implémentations, la configuration est entièrement dynamique et ne s'appuie pas sur une configuration par défaut ; mais dans certains scénarios, comme celui de cette rubrique, il est préférable de disposer d'un état de configuration par défaut lorsque le service démarre.</span><span class="sxs-lookup"><span data-stu-id="243a4-105">In many implementations, configuration will be fully dynamic and will not rely on a default configuration; however, there are some scenarios, such as the one in this topic, where it is desirable to have a default configuration state when the service starts.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="243a4-106">Les mises à jour dynamiques se produisent uniquement en mémoire et n'entraînent aucune modification des fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="243a4-106">Dynamic updates occur only in memory, and do not result in the modification of configuration files.</span></span>  
  
 <span data-ttu-id="243a4-107">Les deux services regularCalc et roundingCalc prennent en charge les mêmes opérations : addition, soustraction, multiplication et division ; toutefois, roundingCalc arrondit tous les calculs à la valeur entière la plus proche avant de les retourner.</span><span class="sxs-lookup"><span data-stu-id="243a4-107">Both regularCalc and roundingCalc support the same operations of add, subtract, multiply and divide; however, roundingCalc rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="243a4-108">Un fichier de configuration sert à configurer le service de manière à router tous les messages vers le service regularCalc.</span><span class="sxs-lookup"><span data-stu-id="243a4-108">A configuration file is used to configure the service to route all messages to the regularCalc service.</span></span> <span data-ttu-id="243a4-109">Après le démarrage du service de routage, la méthode <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> est utilisée pour reconfigurer le service de manière à router les messages vers le service roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="243a4-109">After the Routing Service has been started, <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> is used to reconfigure the service to route messages to the roundingCalc service.</span></span>  
  
### <a name="implement-initial-configuration"></a><span data-ttu-id="243a4-110">Implémenter la configuration initiale</span><span class="sxs-lookup"><span data-stu-id="243a4-110">Implement Initial Configuration</span></span>  
  
1. <span data-ttu-id="243a4-111">Créez la configuration du service de routage de base, en spécifiant les points de terminaison de service exposés par le service.</span><span class="sxs-lookup"><span data-stu-id="243a4-111">Create the basic Routing Service Configuration by specifying the service endpoints exposed by the service.</span></span> <span data-ttu-id="243a4-112">L'exemple suivant définit un point de terminaison de service unique, qui sera utilisé pour recevoir des messages.</span><span class="sxs-lookup"><span data-stu-id="243a4-112">The following example defines a single service endpoint, which will be used to receive messages.</span></span> <span data-ttu-id="243a4-113">Il définit également un point de terminaison client qui permettra d'envoyer des messages au regularCalc.</span><span class="sxs-lookup"><span data-stu-id="243a4-113">It also defines a client endpoint that will be used to send messages to the regularCalc.</span></span>  
  
    ```xml  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoint for the Routing Service-->  
        <endpoint address="calculator"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
      </service>  
    </services>  
    <client>  
    <!--set up the destination endpoint-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    ```  
  
2. <span data-ttu-id="243a4-114">Définissez le filtre utilisé pour router les messages vers les points de terminaison de destination.</span><span class="sxs-lookup"><span data-stu-id="243a4-114">Define the filter used to route messages to the destination endpoints.</span></span> <span data-ttu-id="243a4-115">Dans cet exemple, le filtre MatchAll est utilisé pour router tous les messages vers le regularCalcEndpoint défini précédemment.</span><span class="sxs-lookup"><span data-stu-id="243a4-115">For this example, the MatchAll filter is used to route all messages to the regularCalcEndpoint defined previously.</span></span> <span data-ttu-id="243a4-116">L'exemple suivant définit le filtre et la table de filtres.</span><span class="sxs-lookup"><span data-stu-id="243a4-116">The following example defines the filter and filter table.</span></span>  
  
    ```xml  
    <filters>  
      <!--define the message filter-->  
      <filter name="MatchAllFilter" filterType="MatchAll"/>  
    </filters>  
    <filterTables>  
      <filterTable name="filterTable1">  
          <!--add the filter to the message filter table-->  
          <add filterName="MatchAllFilter" endpointName="regularCalcEndpoint"/>  
      </filterTable>  
    </filterTables>  
    ```  
  
3. <span data-ttu-id="243a4-117">Pour évaluer les messages entrants en fonction des filtres contenus dans la table de filtres, vous devez associer la table de filtres aux points de terminaison de service à l'aide du comportement de routage.</span><span class="sxs-lookup"><span data-stu-id="243a4-117">To evaluate incoming messages against the filters contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="243a4-118">L’exemple suivant montre l’Association de « filterTable1 » au point de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="243a4-118">The following example demonstrates associating "filterTable1" with the service endpoint.</span></span>  
  
    ```xml  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="implement-dynamic-configuration"></a><span data-ttu-id="243a4-119">Implémenter la configuration dynamique</span><span class="sxs-lookup"><span data-stu-id="243a4-119">Implement Dynamic Configuration</span></span>  

 <span data-ttu-id="243a4-120">La configuration dynamique du service de routage s'effectue uniquement dans le code, en créant un objet <xref:System.ServiceModel.Routing.RoutingConfiguration> et en utilisant la méthode <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> pour remplacer la configuration actuelle.</span><span class="sxs-lookup"><span data-stu-id="243a4-120">Dynamic configuration of the Routing Service can only be performed in code by creating a new <xref:System.ServiceModel.Routing.RoutingConfiguration> and using <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> to replace the current configuration.</span></span>  <span data-ttu-id="243a4-121">Pour cet exemple, le service de routage est auto-hébergé dans une application console.</span><span class="sxs-lookup"><span data-stu-id="243a4-121">For this example, the Routing Service is self-hosted within a console application.</span></span> <span data-ttu-id="243a4-122">Une fois l'application démarrée, vous pouvez modifier la configuration de routage en entrant 'regular' ou 'rounding' dans la fenêtre de console, pour configurer le point de terminaison de destination vers lequel router les messages : regularCalc si vous entrez 'regular' ou roundingCalc si vous entrez 'rounding'.</span><span class="sxs-lookup"><span data-stu-id="243a4-122">After the application has started, you can modify the routing configuration by entering ‘regular’ or ‘rounding’ at the console window to configure the destination endpoint that messages are routed to; regularCalc when ‘regular’ is entered, otherwise roundingCalc when ‘rounding’ is entered.</span></span>  
  
1. <span data-ttu-id="243a4-123">Les instructions using suivantes doivent être ajoutées afin de prendre en charge le service de routage.</span><span class="sxs-lookup"><span data-stu-id="243a4-123">The following using statements must be added in order to support the Routing Service.</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ServiceModel;  
    using System.ServiceModel.Channels;  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Dispatcher;  
    using System.ServiceModel.Routing;  
    ```  
  
2. <span data-ttu-id="243a4-124">Le code suivant sert à auto-héberger le service de routage en tant qu'application console.</span><span class="sxs-lookup"><span data-stu-id="243a4-124">The following code is used to self-host the Routing Service as a console application.</span></span> <span data-ttu-id="243a4-125">Ce code initialise le service de routage en utilisant la configuration décrite dans l'étape précédente, contenue dans le fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="243a4-125">This initializes the Routing Service using the configuration described in the previous step, which is contained within the application configuration file.</span></span> <span data-ttu-id="243a4-126">La boucle while contient le code utilisé pour modifier la configuration de routage.</span><span class="sxs-lookup"><span data-stu-id="243a4-126">The while loop contains the code used to change the routing configuration.</span></span>  
  
    ```csharp  
    // Host the service within this EXE console application.  
    public static void Main()  
    {  
        // Create a ServiceHost for the CalculatorService type.  
        using (ServiceHost serviceHost =  
            new ServiceHost(typeof(RoutingService)))  
        {  
            // Open the ServiceHost to create listeners
            // and start listening for messages.  
            Console.WriteLine("The Routing Service configured, opening....");  
            serviceHost.Open();  
            Console.WriteLine("The Routing Service is now running.");  
             Console.WriteLine("Type 'quit' to terminate router.");  
             Console.WriteLine("<ENTER> to change routing configuration.");  
             while (Console.ReadLine() != "quit")  
             {  
            ....  
            }  
        }  
    }  
    ```  
  
3. <span data-ttu-id="243a4-127">Pour mettre à jour de manière dynamique la configuration de routage, il faut créer une nouvelle configuration de routage.</span><span class="sxs-lookup"><span data-stu-id="243a4-127">To dynamically update the routing configuration, a new routing configuration must be created.</span></span> <span data-ttu-id="243a4-128">Celle-ci doit contenir l'ensemble des points de terminaison, filtres et tables de filtres nécessaires pour la nouvelle configuration de routage, car elle doit remplacer complètement la configuration de routage existante.</span><span class="sxs-lookup"><span data-stu-id="243a4-128">This must contain all endpoints, filters and filter tables that are required for the new routing configuration, as it will completely replace the existing routing configuration.</span></span> <span data-ttu-id="243a4-129">Pour utiliser la nouvelle configuration de routage, vous devez appeler la méthode <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> et transmettre la nouvelle configuration.</span><span class="sxs-lookup"><span data-stu-id="243a4-129">In order to use the new routing configuration, you must invoke <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> and pass the new configuration.</span></span>  
  
     <span data-ttu-id="243a4-130">Ajoutez le code suivant à la boucle while définie précédemment pour permettre la reconfiguration du service en fonction de l'entrée utilisateur.</span><span class="sxs-lookup"><span data-stu-id="243a4-130">Add the following code to the while loop defined previously to allow the service to be reconfigured based on user input.</span></span>  
  
    ```csharp  
    Console.WriteLine("Enter 'regular' or 'rounding' to set the destination endpoint:");  
    string destEndpoint = Console.ReadLine();  
    // Create a new RoutingConfiguration  
    RoutingConfiguration rc = new RoutingConfiguration();  
    // Determine the endpoint to configure for  
    switch (destEndpoint)  
    {  
        case "regular":  
            // Define the destination endpoint  
            ServiceEndpoint regularCalc = new ServiceEndpoint(  
               ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
               new NetTcpBinding(),  
               new EndpointAddress("net.tcp://localhost:9090/servicemodelsamples/service/"));  
            // Create a MatchAll filter and add to the filter table  
            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { regularCalc });  
            // Use ApplyConfiguration to update the Routing Service  
            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
            Console.WriteLine("Applied new routing configuration.");  
            break;  
        case "rounding":  
            // Define the destination endpoint  
            ServiceEndpoint roundingCalc = new ServiceEndpoint(  
               ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
               new NetTcpBinding(),  
               new EndpointAddress("net.tcp://localhost:8080/servicemodelsamples/service/"));  
            // Create a MatchAll filter and add to the filter table  
            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { roundingCalc });  
            // Use ApplyConfiguration to update the Routing Service  
            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
            Console.WriteLine("Applied new routing configuration.");  
            break;  
        default:  
            Console.WriteLine("Incorrect value entered, no change.");  
            break;  
    }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="243a4-131">Dans la mesure où la méthode qui permet de fournir un nouvel objet RoutingConfiguration est contenue dans l’extension de service RoutingExtension, les nouveaux objets RoutingConfiguration peuvent être fournis n’importe où dans le modèle d’extensibilité WCF qui détient ou peut obtenir une référence à ServiceHost ou aux ServiceExtensions (comme dans une autre ServiceExtension).</span><span class="sxs-lookup"><span data-stu-id="243a4-131">Since the method for providing a new RoutingConfiguration is contained in the RoutingExtension service extension, new RoutingConfiguration objects can be provided anywhere in the WCF extensibility model that has or can obtain a reference to the ServiceHost or ServiceExtensions (such as in another ServiceExtension).</span></span>
  
## <a name="example"></a><span data-ttu-id="243a4-132"> Exemple</span><span class="sxs-lookup"><span data-stu-id="243a4-132">Example</span></span>  

<span data-ttu-id="243a4-133">Voici une liste complète de l’application console utilisée dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="243a4-133">The following is a complete listing of the console application used in this example:</span></span>
  
```csharp
//-----------------------------------------------------------------  
//  Copyright (c) Microsoft Corporation.  All Rights Reserved.  
//-----------------------------------------------------------------  
  
using System;  
using System.Collections.Generic;  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
using System.ServiceModel.Description;  
using System.ServiceModel.Dispatcher;  
using System.ServiceModel.Routing;  
  
namespace Microsoft.Samples.AdvancedFilters  
{  
    public class Router  
    {  
        // Host the service within this EXE console application.  
        public static void Main()  
        {
            // Create a ServiceHost for the CalculatorService type.  
            using (ServiceHost serviceHost =  
                new ServiceHost(typeof(RoutingService)))  
            {  
                // Open the ServiceHost to create listeners
                // and start listening for messages.  
                Console.WriteLine("The Routing Service configured, opening....");  
                serviceHost.Open();  
                Console.WriteLine("The Routing Service is now running.");  
                Console.WriteLine("Type 'quit' to terminate router.");  
                Console.WriteLine("<ENTER> to change routing configuration.");  
                while (Console.ReadLine() != "quit")  
                {  
                    Console.WriteLine("Enter 'regular' or 'rounding' to set the destination endpoint:");  
                    string destEndpoint = Console.ReadLine();  
                    // Create a new RoutingConfiguration  
                    RoutingConfiguration rc = new RoutingConfiguration();  
                    // Determine the endpoint to configure for  
                    switch (destEndpoint)  
                    {  
                        case "regular":  
                            // Define the destination endpoint  
                            ServiceEndpoint regularCalc = new ServiceEndpoint(  
                            ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
                            new NetTcpBinding(),  
                            new EndpointAddress("net.tcp://localhost:9090/servicemodelsamples/service/"));  
                            // Create a MatchAll filter and add to the filter table  
                            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { regularCalc });  
                            // Use ApplyConfiguration to update the Routing Service  
                            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
                            Console.WriteLine("Applied new routing configuration.");  
                            break;  
                        case "rounding":  
                            // Define the destination endpoint  
                            ServiceEndpoint roundingCalc = new ServiceEndpoint(  
                                ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
                                new NetTcpBinding(),  
                                new EndpointAddress("net.tcp://localhost:8080/servicemodelsamples/service/"));  
                            // Create a MatchAll filter and add to the filter table  
                            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { roundingCalc });  
                            // Use ApplyConfiguration to update the Routing Service  
                            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
                            Console.WriteLine("Applied new routing configuration.");  
                            break;  
                        default:  
                            Console.WriteLine("Incorrect value entered, no change.");  
                            break;  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="243a4-134"> Exemple</span><span class="sxs-lookup"><span data-stu-id="243a4-134">Example</span></span>  

<span data-ttu-id="243a4-135">Voici une liste complète du fichier de configuration utilisé dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="243a4-135">The following is a complete listing of the configuration file used in this example:</span></span>
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright (c) Microsoft Corporation. All rights reserved -->  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoint for the Routing Service-->  
        <endpoint address="calculator"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
      </service>  
    </services>  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
    <client>  
<!--set up the destination endpoint-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
  
      <filters>  
        <!--define the message filter-->  
        <filter name="MatchAllFilter" filterType="MatchAll"/>  
      </filters>  
      <filterTables>  
        <filterTable name="filterTable1">  
            <!--add the filter to the message filter table-->  
            <add filterName="MatchAllFilter" endpointName="regularCalcEndpoint"/>  
        </filterTable>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="243a4-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="243a4-136">See also</span></span>

- [<span data-ttu-id="243a4-137">Services de routage</span><span class="sxs-lookup"><span data-stu-id="243a4-137">Routing Services</span></span>](../samples/routing-services.md)
