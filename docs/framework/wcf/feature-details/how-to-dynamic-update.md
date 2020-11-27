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
# <a name="how-to-dynamic-update"></a>Procédure : Mise à jour dynamique

Cette rubrique présente les étapes de base nécessaires pour créer et mettre à jour de manière dynamique la configuration de routage. Dans cet exemple, la configuration de routage initiale provient du fichier de configuration et route tous les messages vers le service de calculatrice regularCalc, mais elle est ensuite mise à jour par programme pour modifier le point de terminaison de destination du service roundingCalc.  
  
> [!NOTE]
> Dans de nombreuses implémentations, la configuration est entièrement dynamique et ne s'appuie pas sur une configuration par défaut ; mais dans certains scénarios, comme celui de cette rubrique, il est préférable de disposer d'un état de configuration par défaut lorsque le service démarre.  
  
> [!NOTE]
> Les mises à jour dynamiques se produisent uniquement en mémoire et n'entraînent aucune modification des fichiers de configuration.  
  
 Les deux services regularCalc et roundingCalc prennent en charge les mêmes opérations : addition, soustraction, multiplication et division ; toutefois, roundingCalc arrondit tous les calculs à la valeur entière la plus proche avant de les retourner. Un fichier de configuration sert à configurer le service de manière à router tous les messages vers le service regularCalc. Après le démarrage du service de routage, la méthode <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> est utilisée pour reconfigurer le service de manière à router les messages vers le service roundingCalc.  
  
### <a name="implement-initial-configuration"></a>Implémenter la configuration initiale  
  
1. Créez la configuration du service de routage de base, en spécifiant les points de terminaison de service exposés par le service. L'exemple suivant définit un point de terminaison de service unique, qui sera utilisé pour recevoir des messages. Il définit également un point de terminaison client qui permettra d'envoyer des messages au regularCalc.  
  
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
  
2. Définissez le filtre utilisé pour router les messages vers les points de terminaison de destination. Dans cet exemple, le filtre MatchAll est utilisé pour router tous les messages vers le regularCalcEndpoint défini précédemment. L'exemple suivant définit le filtre et la table de filtres.  
  
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
  
3. Pour évaluer les messages entrants en fonction des filtres contenus dans la table de filtres, vous devez associer la table de filtres aux points de terminaison de service à l'aide du comportement de routage. L’exemple suivant montre l’Association de « filterTable1 » au point de terminaison de service.  
  
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
  
## <a name="implement-dynamic-configuration"></a>Implémenter la configuration dynamique  

 La configuration dynamique du service de routage s'effectue uniquement dans le code, en créant un objet <xref:System.ServiceModel.Routing.RoutingConfiguration> et en utilisant la méthode <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> pour remplacer la configuration actuelle.  Pour cet exemple, le service de routage est auto-hébergé dans une application console. Une fois l'application démarrée, vous pouvez modifier la configuration de routage en entrant 'regular' ou 'rounding' dans la fenêtre de console, pour configurer le point de terminaison de destination vers lequel router les messages : regularCalc si vous entrez 'regular' ou roundingCalc si vous entrez 'rounding'.  
  
1. Les instructions using suivantes doivent être ajoutées afin de prendre en charge le service de routage.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ServiceModel;  
    using System.ServiceModel.Channels;  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Dispatcher;  
    using System.ServiceModel.Routing;  
    ```  
  
2. Le code suivant sert à auto-héberger le service de routage en tant qu'application console. Ce code initialise le service de routage en utilisant la configuration décrite dans l'étape précédente, contenue dans le fichier de configuration de l'application. La boucle while contient le code utilisé pour modifier la configuration de routage.  
  
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
  
3. Pour mettre à jour de manière dynamique la configuration de routage, il faut créer une nouvelle configuration de routage. Celle-ci doit contenir l'ensemble des points de terminaison, filtres et tables de filtres nécessaires pour la nouvelle configuration de routage, car elle doit remplacer complètement la configuration de routage existante. Pour utiliser la nouvelle configuration de routage, vous devez appeler la méthode <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> et transmettre la nouvelle configuration.  
  
     Ajoutez le code suivant à la boucle while définie précédemment pour permettre la reconfiguration du service en fonction de l'entrée utilisateur.  
  
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
    > Dans la mesure où la méthode qui permet de fournir un nouvel objet RoutingConfiguration est contenue dans l’extension de service RoutingExtension, les nouveaux objets RoutingConfiguration peuvent être fournis n’importe où dans le modèle d’extensibilité WCF qui détient ou peut obtenir une référence à ServiceHost ou aux ServiceExtensions (comme dans une autre ServiceExtension).
  
## <a name="example"></a> Exemple  

Voici une liste complète de l’application console utilisée dans cet exemple :
  
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
  
## <a name="example"></a> Exemple  

Voici une liste complète du fichier de configuration utilisé dans cet exemple :
  
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
  
## <a name="see-also"></a>Voir aussi

- [Services de routage](../samples/routing-services.md)
