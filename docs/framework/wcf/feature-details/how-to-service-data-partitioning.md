---
title: 'Procédure : Partitionnement des données du service'
ms.date: 03/30/2017
ms.assetid: 1ccff72e-d76b-4e36-93a2-e51f7b32dc83
ms.openlocfilehash: 7bb5eb6bda8bb2be3dfaaa88eb4b5ad787f47aa7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268922"
---
# <a name="how-to-service-data-partitioning"></a><span data-ttu-id="8565f-102">Procédure : Partitionnement des données du service</span><span class="sxs-lookup"><span data-stu-id="8565f-102">How To: Service Data Partitioning</span></span>

<span data-ttu-id="8565f-103">Cette rubrique présente les étapes de base requises pour partitionner des messages entre plusieurs instances du même service de destination.</span><span class="sxs-lookup"><span data-stu-id="8565f-103">This topic outlines the basic steps required to partition messages across multiple instances of the same destination service.</span></span> <span data-ttu-id="8565f-104">Le partitionnement des données du service est en général utilisé pour faire évoluer un service vers une meilleure qualité ou pour gérer les demandes de différents clients de manière spécifique.</span><span class="sxs-lookup"><span data-stu-id="8565f-104">Service data partitioning is typically used when you need to scale a service in order to provide better quality of service, or when you need to handle requests from different customers in a specific way.</span></span> <span data-ttu-id="8565f-105">Par exemple, les messages de clients de valeur élevée ou « Gold » peuvent avoir besoin d’être traités avec une priorité plus élevée que les messages d’un client standard.</span><span class="sxs-lookup"><span data-stu-id="8565f-105">For example, messages from high value or "Gold" customers may need to be processed at a higher priority than messages from a standard customer.</span></span>  
  
 <span data-ttu-id="8565f-106">Dans cet exemple, les messages sont routés vers l'une des deux instances du service regularCalc.</span><span class="sxs-lookup"><span data-stu-id="8565f-106">In this example, messages are routed to one of two instances of the regularCalc service.</span></span> <span data-ttu-id="8565f-107">Les deux instances du service sont identiques ; toutefois, le service représenté par le point de terminaison calculator1 traite les messages provenant de clients importants et le point de terminaison calculator2 traite les messages des autres clients.</span><span class="sxs-lookup"><span data-stu-id="8565f-107">Both instances of the service are identical; however the service represented by the calculator1 endpoint processes messages received from high value customers, the calculator 2 endpoint processes messages from other customers</span></span>  
  
 <span data-ttu-id="8565f-108">Le message envoyé par le client ne possède aucune donnée unique qui permette d'identifier l'instance du service vers laquelle le message doit être routé.</span><span class="sxs-lookup"><span data-stu-id="8565f-108">The message sent from the client does not have any unique data that can be used to identify which service instance the message should be routed to.</span></span> <span data-ttu-id="8565f-109">Pour permettre à chaque client de router des données vers un service de destination spécifique, nous allons implémenter deux points de terminaison de service qui serviront à recevoir les messages.</span><span class="sxs-lookup"><span data-stu-id="8565f-109">To allow each client to route data to a specific destination service we will implement two service endpoints that will be used to receive messages.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8565f-110">Bien que cet exemple utilise des points de terminaison spécifiques pour partitionner des données, le même résultat pourrait être obtenu en utilisant des informations contenues dans le message lui-même, comme un en-tête ou des données dans le corps.</span><span class="sxs-lookup"><span data-stu-id="8565f-110">While this example uses specific endpoints to partition data, this could also be accomplished using information contained within the message itself such as header or body data.</span></span>  
  
### <a name="implement-service-data-partitioning"></a><span data-ttu-id="8565f-111">Implémenter le partitionnement des données du service</span><span class="sxs-lookup"><span data-stu-id="8565f-111">Implement Service Data Partitioning</span></span>  
  
1. <span data-ttu-id="8565f-112">Créez la configuration de base du service de routage en spécifiant les points de terminaison de service exposés par le service.</span><span class="sxs-lookup"><span data-stu-id="8565f-112">Create the basic Routing Service configuration by specifying the service endpoints exposed by the service.</span></span> <span data-ttu-id="8565f-113">L'exemple suivant définit deux points de terminaison qui serviront à recevoir des messages.</span><span class="sxs-lookup"><span data-stu-id="8565f-113">The following example defines two endpoints, which will be used to receive messages.</span></span> <span data-ttu-id="8565f-114">Il définit également les points de terminaison clients, utilisés pour envoyer des messages aux instances du service regularCalc.</span><span class="sxs-lookup"><span data-stu-id="8565f-114">It also defines the client endpoints, which are used to send messages to the regularCalc service instances.</span></span>  
  
    ```xml  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoints for the Routing Service-->  
        <!--create the endpoints for the calculator service-->  
        <endpoint address="calculator1"  
                  binding="wsHttpBinding"  
                  name="calculator1Endpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <endpoint address="calculator2"  
                  binding="wsHttpBinding"  
                  name="calculator2Endpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
       </service>  
    </services>  
    <client>  
    <!--set up the destination endpoints-->  
        <endpoint name="CalcEndpoint1"  
                  address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                  binding="netTcpBinding"  
                  contract="*" />  
  
        <endpoint name="CalcEndpoint2"  
                  address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                  binding="netTcpBinding"  
                  contract="*" />  
     </client>  
    ```  
  
2. <span data-ttu-id="8565f-115">Définissez les filtres utilisés pour router les messages vers les points de terminaison de destination.</span><span class="sxs-lookup"><span data-stu-id="8565f-115">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="8565f-116">Dans cet exemple, le filtre EndpointName permet de déterminer quel point de terminaison de service a reçu le message.</span><span class="sxs-lookup"><span data-stu-id="8565f-116">For this example, the EndpointName filter is used to determine which service endpoint received the message.</span></span> <span data-ttu-id="8565f-117">L'exemple suivant définit la section et les filtres de routage nécessaires.</span><span class="sxs-lookup"><span data-stu-id="8565f-117">The following example defines the necessary routing section and filters.</span></span>  
  
    ```xml  
    <filters>  
      <!--define the different message filters-->  
      <!--define endpoint name filters looking for messages that show up on the virtual endpoints-->  
      <filter name="HighPriority" filterType="EndpointName"  
              filterData="calculator1Endpoint"/>  
      <filter name="NormalPriority" filterType="EndpointName"  
              filterData="calculator2Endpoint"/>  
    </filters>  
    ```  
  
3. <span data-ttu-id="8565f-118">Définissez la table de filtres, qui associe chaque filtre à un point de terminaison client.</span><span class="sxs-lookup"><span data-stu-id="8565f-118">Define the filter table, which associates each filter with a client endpoint.</span></span> <span data-ttu-id="8565f-119">Dans cet exemple, le message sera routé en fonction du point de terminaison spécifique qui l'a reçu.</span><span class="sxs-lookup"><span data-stu-id="8565f-119">In this example, the message will be routed based on the specific endpoint it was received over.</span></span> <span data-ttu-id="8565f-120">Puisque le message ne peut correspondre qu'à un seul des deux filtres possibles, il n'est pas nécessaire d'utiliser une priorité de filtre pour contrôler l'ordre dans lequel les filtres sont évalués.</span><span class="sxs-lookup"><span data-stu-id="8565f-120">Since the message can only match one of the two possible filters, there is no need for using filter priority to control to the order in which filters are evaluated.</span></span>  
  
     <span data-ttu-id="8565f-121">Les éléments suivants définissent la table de filtres et ajoutent les filtres définis précédemment.</span><span class="sxs-lookup"><span data-stu-id="8565f-121">The following defines the filter table and adds the filters defined earlier.</span></span>  
  
    ```xml  
    <filterTables>  
       <filterTable name="filterTable1">  
         <!--add the filters to the message filter table-->  
         <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
         <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
       </filterTable>  
    </filterTables>  
    ```  
  
4. <span data-ttu-id="8565f-122">Pour évaluer les messages entrants en fonction des filtres contenus dans la table, vous devez associer la table de filtres aux points de terminaison de service à l'aide du comportement de routage.</span><span class="sxs-lookup"><span data-stu-id="8565f-122">To evaluate incoming messages against the filters contained in the table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="8565f-123">L’exemple suivant illustre l’Association de « filterTable1 » aux points de terminaison de service :</span><span class="sxs-lookup"><span data-stu-id="8565f-123">The following example demonstrates associating "filterTable1" with the service endpoints:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="8565f-124"> Exemple</span><span class="sxs-lookup"><span data-stu-id="8565f-124">Example</span></span>  

 <span data-ttu-id="8565f-125">L'intégralité du fichier de configuration est présentée ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="8565f-125">The following is a complete listing of the configuration file.</span></span>  
  
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
        <!--Set up the inbound endpoints for the Routing Service-->  
        <!--create the endpoints for the calculator service-->  
        <endpoint address="calculator1"  
                  binding="wsHttpBinding"  
                  name="calculator1Endpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <endpoint address="calculator2"  
                  binding="wsHttpBinding"  
                  name="calculator2Endpoint"  
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
<!--set up the destination endpoints-->  
      <endpoint name="CalcEndpoint1"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <endpoint name="CalcEndpoint2"  
                address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
  
      <filters>  
        <!--define the different message filters-->  
        <!--define endpoint name filters looking for messages that show up on the virtual endpoints-->  
        <filter name="HighPriority" filterType="EndpointName"  
                filterData="calculator1Endpoint"/>  
        <filter name="NormalPriority" filterType="EndpointName"  
                filterData="calculator2Endpoint"/>  
      </filters>  
  
      <filterTables>  
        <filterTable name="filterTable1">  
          <!--add the filters to the message filter table-->  
          <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
          <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
        </filterTable>  
      </filterTables>  
  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8565f-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8565f-126">See also</span></span>

- [<span data-ttu-id="8565f-127">Services de routage</span><span class="sxs-lookup"><span data-stu-id="8565f-127">Routing Services</span></span>](../samples/routing-services.md)
