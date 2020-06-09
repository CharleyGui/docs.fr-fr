---
title: 'Procédure : partitionnement des données du service'
ms.date: 03/30/2017
ms.assetid: 1ccff72e-d76b-4e36-93a2-e51f7b32dc83
ms.openlocfilehash: 3b2f86ee6a4dea25fb5c972d4cecb1b9ed411b29
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601190"
---
# <a name="how-to-service-data-partitioning"></a>Procédure : partitionnement des données du service
Cette rubrique présente les étapes de base requises pour partitionner des messages entre plusieurs instances du même service de destination. Le partitionnement des données du service est en général utilisé pour faire évoluer un service vers une meilleure qualité ou pour gérer les demandes de différents clients de manière spécifique. Par exemple, les messages de clients de valeur élevée ou « Gold » peuvent avoir besoin d’être traités avec une priorité plus élevée que les messages d’un client standard.  
  
 Dans cet exemple, les messages sont routés vers l'une des deux instances du service regularCalc. Les deux instances du service sont identiques ; toutefois, le service représenté par le point de terminaison calculator1 traite les messages provenant de clients importants et le point de terminaison calculator2 traite les messages des autres clients.  
  
 Le message envoyé par le client ne possède aucune donnée unique qui permette d'identifier l'instance du service vers laquelle le message doit être routé. Pour permettre à chaque client de router des données vers un service de destination spécifique, nous allons implémenter deux points de terminaison de service qui serviront à recevoir les messages.  
  
> [!NOTE]
> Bien que cet exemple utilise des points de terminaison spécifiques pour partitionner des données, le même résultat pourrait être obtenu en utilisant des informations contenues dans le message lui-même, comme un en-tête ou des données dans le corps.  
  
### <a name="implement-service-data-partitioning"></a>Implémenter le partitionnement des données du service  
  
1. Créez la configuration de base du service de routage en spécifiant les points de terminaison de service exposés par le service. L'exemple suivant définit deux points de terminaison qui serviront à recevoir des messages. Il définit également les points de terminaison clients, utilisés pour envoyer des messages aux instances du service regularCalc.  
  
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
  
2. Définissez les filtres utilisés pour router les messages vers les points de terminaison de destination.  Dans cet exemple, le filtre EndpointName permet de déterminer quel point de terminaison de service a reçu le message. L'exemple suivant définit la section et les filtres de routage nécessaires.  
  
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
  
3. Définissez la table de filtres, qui associe chaque filtre à un point de terminaison client. Dans cet exemple, le message sera routé en fonction du point de terminaison spécifique qui l'a reçu. Puisque le message ne peut correspondre qu'à un seul des deux filtres possibles, il n'est pas nécessaire d'utiliser une priorité de filtre pour contrôler l'ordre dans lequel les filtres sont évalués.  
  
     Les éléments suivants définissent la table de filtres et ajoutent les filtres définis précédemment.  
  
    ```xml  
    <filterTables>  
       <filterTable name="filterTable1">  
         <!--add the filters to the message filter table-->  
         <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
         <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
       </filterTable>  
    </filterTables>  
    ```  
  
4. Pour évaluer les messages entrants en fonction des filtres contenus dans la table, vous devez associer la table de filtres aux points de terminaison de service à l'aide du comportement de routage. L’exemple suivant illustre l’Association de « filterTable1 » aux points de terminaison de service :  
  
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
  
## <a name="example"></a>Exemple  
 L'intégralité du fichier de configuration est présentée ci-dessous.  
  
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
  
## <a name="see-also"></a>Voir aussi

- [Services de routage](../samples/routing-services.md)
