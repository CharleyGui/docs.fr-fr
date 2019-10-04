---
title: 'Procédure : Gestion des erreurs'
ms.date: 03/30/2017
ms.assetid: de566e39-9358-44ff-8244-780f6b799966
ms.openlocfilehash: 3b8e48a74ff7671b942b5499fb3a0b5d0f389d61
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834710"
---
# <a name="how-to-error-handling"></a>Procédure : Gestion des erreurs

Cette rubrique décrit les étapes de base requises pour créer une configuration de routage utilisant la gestion des erreurs. Dans cet exemple, les messages sont routés vers un point de terminaison de destination. Si un message ne peut pas être remis en raison d'une panne réseau ou d'une défaillance liée aux communications (<xref:System.ServiceModel.CommunicationException>), le message est renvoyé à un autre point de terminaison.

> [!NOTE]
> Le point de terminaison de destination utilisé dans cet exemple contient une adresse incorrecte pour simuler une panne réseau. Les messages routés vers ce point de terminaison échouent car aucun service n'écoute sur l'adresse spécifiée.

> [!NOTE]
> Bien que l'exemple contenu dans cette rubrique ne traite pas de manière explicite des paramètres de délai d'expiration, vous devez prendre ceux-ci en considération lors de l'utilisation de la gestion des erreurs. Lorsque des erreurs sont rencontrées, un délai supplémentaire s'écoulera avant que le client reçoive une réponse. Ce délai est dû au fait que l'erreur est reçue par le service de routage, qui essaie alors d'envoyer le message à un point de terminaison de sauvegarde. Si les valeurs de délai d'attente associées aux points de terminaison de destination primaires et de sauvegarde sont importantes, le client risque d'attendre un long moment, le temps que le message échoue sur plusieurs points de terminaison de la liste de sauvegarde avant d'être envoyé avec succès.
>
> Puisque le service de routage risque de produire un délai maximal, égal à la somme des valeurs de délai d'attente de tous les points de terminaison associés à un filtre, nous vous recommandons d'augmenter en conséquence le délai d'attente prévu sur le client.

### <a name="implement-error-handling"></a>Implémenter la gestion des erreurs

1. Créez la configuration du service de routage de base, en spécifiant le point de terminaison de service exposé par le service. L'exemple suivant définit un point de terminaison de service unique, utilisé pour recevoir des messages. Il définit également les points de terminaison clients utilisés pour envoyer des messages ; deadDestination et realDestination. Le point de terminaison deadDestination contient une adresse qui ne référence aucun service en cours d'exécution et qui est utilisée pour simuler une panne réseau lors de l'envoi de messages à ce point de terminaison.

    ```xml
    <services>
      <service behaviorConfiguration="routingConfiguration"
               name="System.ServiceModel.Routing.RoutingService">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost/routingservice/" />
          </baseAddresses>
        </host>
        <!-- Create the Routing Service endpoint -->
        <endpoint address="router"
                  binding="basicHttpBinding"
                  name="RoutingServiceEndpoint"
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />
      </service>
    </services>

    <!-- Create the destination endpoints that we want to send to -->
    <client>
      <!-- Create a dummy endpoint that we know will be down -->
      <endpoint name="deadDestination"
                address="net.tcp://localhost:9090/servicemodelsamples/fakeDestination"
                binding="netTcpBinding"
                contract="*" />

      <!-- Now create the real service endpoint -->
      <endpoint name="realDestination"
                address="net.tcp://localhost:8080/servicemodelsamples/service"
                binding="netTcpBinding"
                contract="*" />
    </client>
    ```

2. Définissez les filtres utilisés pour router les messages vers les points de terminaison de destination.  Pour cet exemple, un filtre MatchAll est utilisé pour correspondre à tous les messages reçus par le service de routage.

    ```xml
    <filters>
      <!-- Create a MatchAll filter which will catch all messages -->
      <filter name="MatchAllFilter1" filterType="MatchAll" />
    </filters>
    ```

3. Définissez la liste de points de terminaison de sauvegarde. Elle contient les points de terminaison auxquels un message est envoyé en cas de panne réseau ou d'échec de communication lors de l'envoi au point de terminaison de destination primaire. L'exemple suivant définit une liste de sauvegarde contenant un point de terminaison ; toutefois, plusieurs points de terminaison peuvent être spécifiés dans une liste de sauvegarde.

     Si la liste de sauvegarde contient plusieurs points de terminaison, lorsqu'une panne réseau ou un échec de communication se produit, le service de routage essaie d'envoyer le message au premier point de terminaison de la liste. Si une panne réseau ou un échec de communication se produit lors de l'envoi à ce point de terminaison, le service de routage essaie d'envoyer le message au point de terminaison suivant dans la liste. Le service continue à envoyer le message à chaque point de terminaison de la liste de sauvegarde jusqu'à ce que le message soit envoyé avec succès, que tous les points de terminaison de sauvegarde retournent une erreur liée au réseau ou aux communications, ou que le message soit envoyé et que le point de terminaison retourne une erreur non liée au réseau ou aux communications.

    ```xml
    <backupLists>
      <backupList name="backupEndpointList">
          <add endpointName="realDestination" />
      </backupList>
    </backupLists>
    ```

4. Définissez la table de filtres, qui associe le filtre au point de terminaison deadDestination, et la liste de points de terminaison de sauvegarde.  Le service de routage essaie d'abord d'envoyer le message au point de terminaison de destination associé au filtre. Puisque deadDestination contient une adresse qui ne fait référence à aucun service en cours d'exécution, cela provoque une erreur réseau. Le service de routage tente ensuite d’envoyer le message au point de terminaison spécifié dans le backupEndpointList.

    ```xml
    <filterTables>
            <!-- Set up the Routing Service's Message Filter Table -->
            <filterTable name="filterTable1">
                <!-- Add an entity that maps the MatchAllMessageFilter to the dead destination -->
                <!-- If that endpoint is down, tell the Routing Service to try the endpoints -->
                <!-- Listed in the backupEndpointList -->
                <add filterName="MatchAllFilter1" endpointName="deadDestination" backupList="backupEndpointList"/>
            </filterTable>
          </filterTables>
    ```

5. Pour évaluer les messages entrants en fonction du filtre contenu dans la table de filtres, vous devez associer la table de filtres aux points de terminaison de service, à l'aide du comportement de routage.  L’exemple suivant illustre l’Association de « filterTable1 » aux points de terminaison de service.

    ```xml
    <behaviors>
      <serviceBehaviors>
        <!-- Set up the Routing Behavior -->
        <behavior name="routingConfiguration">
          <routing filterTableName="filterTable1" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
    ```

## <a name="example"></a>Exemple

Voici une liste complète du fichier de configuration :

```xml
<?xml version="1.0" encoding="utf-8" ?>
<!-- Copyright (c) Microsoft Corporation.  All Rights Reserved. -->
<configuration>
  <system.serviceModel>
    <services>
      <service behaviorConfiguration="routingConfiguration"
               name="System.ServiceModel.Routing.RoutingService">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost/routingservice/" />
          </baseAddresses>
        </host>
        <!-- Create the Routing Service endpoint -->
        <endpoint address="router"
                  binding="basicHttpBinding"
                  name="RoutingServiceEndpoint"
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />
      </service>
    </services>
    <behaviors>
      <serviceBehaviors>
        <!-- Set up the Routing Behavior -->
        <behavior name="routingConfiguration">
          <routing filterTableName="filterTable1" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <!-- Create the destination endpoints that we want to send to -->
    <client>
      <!-- Create a dummy endpoint that we know will be down -->
      <endpoint name="deadDestination"
                address="net.tcp://localhost:9090/servicemodelsamples/fakeDestination"
                binding="netTcpBinding"
                contract="*" />

      <!-- Now create the real service endpoint -->
      <endpoint name="realDestination"
                address="net.tcp://localhost:8080/servicemodelsamples/service"
                binding="netTcpBinding"
                contract="*" />
    </client>
    <routing>
      <filters>
        <!-- Create a MatchAll filter which will catch all messages -->
        <filter name="MatchAllFilter1" filterType="MatchAll" />
      </filters>
      <filterTables>
        <!-- Set up the Routing Service's Message Filter Table -->
        <filterTable name="filterTable1">
            <!-- Add an entry that maps the MatchAllMessageFilter to the dead destination -->
            <!-- If that endpoint is down, tell the Routing Service to try the endpoints -->
            <!-- Listed in the backupEndpointList -->
            <add filterName="MatchAllFilter1" endpointName="deadDestination" backupList="backupEndpointList"/>
        </filterTable>
      </filterTables>
      <!-- Create the backup endpoint list -->
      <backupLists>
        <backupList name="backupEndpointList">
            <add endpointName="realDestination" />
        </backupList>
      </backupLists>
      </routing>
  </system.serviceModel>
</configuration>
```
