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
# <a name="how-to-error-handling"></a><span data-ttu-id="1fa67-102">Procédure : Gestion des erreurs</span><span class="sxs-lookup"><span data-stu-id="1fa67-102">How To: Error Handling</span></span>

<span data-ttu-id="1fa67-103">Cette rubrique décrit les étapes de base requises pour créer une configuration de routage utilisant la gestion des erreurs.</span><span class="sxs-lookup"><span data-stu-id="1fa67-103">This topic outlines the basic steps required to create a routing configuration that uses error handling.</span></span> <span data-ttu-id="1fa67-104">Dans cet exemple, les messages sont routés vers un point de terminaison de destination.</span><span class="sxs-lookup"><span data-stu-id="1fa67-104">In this example, messages are routed to a destination endpoint.</span></span> <span data-ttu-id="1fa67-105">Si un message ne peut pas être remis en raison d'une panne réseau ou d'une défaillance liée aux communications (<xref:System.ServiceModel.CommunicationException>), le message est renvoyé à un autre point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="1fa67-105">If a message cannot be delivered due to a network or communications-related failure (<xref:System.ServiceModel.CommunicationException>), the message is resent to an alternate endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="1fa67-106">Le point de terminaison de destination utilisé dans cet exemple contient une adresse incorrecte pour simuler une panne réseau.</span><span class="sxs-lookup"><span data-stu-id="1fa67-106">To simulate a network failure, the destination endpoint used in this example contains an incorrect address.</span></span> <span data-ttu-id="1fa67-107">Les messages routés vers ce point de terminaison échouent car aucun service n'écoute sur l'adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1fa67-107">Messages routed to this endpoint fail as no service is listening on the specified address.</span></span>

> [!NOTE]
> <span data-ttu-id="1fa67-108">Bien que l'exemple contenu dans cette rubrique ne traite pas de manière explicite des paramètres de délai d'expiration, vous devez prendre ceux-ci en considération lors de l'utilisation de la gestion des erreurs.</span><span class="sxs-lookup"><span data-stu-id="1fa67-108">While the example contained in this topic does not explicitly discuss time-out settings, you must take these into consideration when using error handling.</span></span> <span data-ttu-id="1fa67-109">Lorsque des erreurs sont rencontrées, un délai supplémentaire s'écoulera avant que le client reçoive une réponse.</span><span class="sxs-lookup"><span data-stu-id="1fa67-109">When errors are encountered, there will be an additional delay encountered before the client receives a response.</span></span> <span data-ttu-id="1fa67-110">Ce délai est dû au fait que l'erreur est reçue par le service de routage, qui essaie alors d'envoyer le message à un point de terminaison de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="1fa67-110">This is because the error is received at the Routing Service, which then attempts to send the message to a backup endpoint.</span></span> <span data-ttu-id="1fa67-111">Si les valeurs de délai d'attente associées aux points de terminaison de destination primaires et de sauvegarde sont importantes, le client risque d'attendre un long moment, le temps que le message échoue sur plusieurs points de terminaison de la liste de sauvegarde avant d'être envoyé avec succès.</span><span class="sxs-lookup"><span data-stu-id="1fa67-111">If the time-out values associated with the primary and backup destination endpoints are large, the client could experience a long delay as the message fails over multiple endpoints in the backup list before being successfully sent.</span></span>
>
> <span data-ttu-id="1fa67-112">Puisque le service de routage risque de produire un délai maximal, égal à la somme des valeurs de délai d'attente de tous les points de terminaison associés à un filtre, nous vous recommandons d'augmenter en conséquence le délai d'attente prévu sur le client.</span><span class="sxs-lookup"><span data-stu-id="1fa67-112">Since the Routing Service could encounter a maximum delay equal to the sum of the time-out value for all endpoints associated with a filter, we recommend that you increase the expected time-out at the client accordingly.</span></span>

### <a name="implement-error-handling"></a><span data-ttu-id="1fa67-113">Implémenter la gestion des erreurs</span><span class="sxs-lookup"><span data-stu-id="1fa67-113">Implement Error Handling</span></span>

1. <span data-ttu-id="1fa67-114">Créez la configuration du service de routage de base, en spécifiant le point de terminaison de service exposé par le service.</span><span class="sxs-lookup"><span data-stu-id="1fa67-114">Create the basic Routing Service configuration by specifying the service endpoint exposed by the service.</span></span> <span data-ttu-id="1fa67-115">L'exemple suivant définit un point de terminaison de service unique, utilisé pour recevoir des messages.</span><span class="sxs-lookup"><span data-stu-id="1fa67-115">The following example defines a single service endpoint, which is used to receive messages.</span></span> <span data-ttu-id="1fa67-116">Il définit également les points de terminaison clients utilisés pour envoyer des messages ; deadDestination et realDestination.</span><span class="sxs-lookup"><span data-stu-id="1fa67-116">It also defines the client endpoints that are used to send messages; deadDestination and realDestination.</span></span> <span data-ttu-id="1fa67-117">Le point de terminaison deadDestination contient une adresse qui ne référence aucun service en cours d'exécution et qui est utilisée pour simuler une panne réseau lors de l'envoi de messages à ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="1fa67-117">The deadDestination endpoint contains an address that does not reference a running service and is used to simulate a network failure when sending messages to this endpoint.</span></span>

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

2. <span data-ttu-id="1fa67-118">Définissez les filtres utilisés pour router les messages vers les points de terminaison de destination.</span><span class="sxs-lookup"><span data-stu-id="1fa67-118">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="1fa67-119">Pour cet exemple, un filtre MatchAll est utilisé pour correspondre à tous les messages reçus par le service de routage.</span><span class="sxs-lookup"><span data-stu-id="1fa67-119">For this example, a MatchAll filter is used to match all messages received by the Routing Service.</span></span>

    ```xml
    <filters>
      <!-- Create a MatchAll filter which will catch all messages -->
      <filter name="MatchAllFilter1" filterType="MatchAll" />
    </filters>
    ```

3. <span data-ttu-id="1fa67-120">Définissez la liste de points de terminaison de sauvegarde. Elle contient les points de terminaison auxquels un message est envoyé en cas de panne réseau ou d'échec de communication lors de l'envoi au point de terminaison de destination primaire.</span><span class="sxs-lookup"><span data-stu-id="1fa67-120">Define the backup endpoint list, which contains the endpoints that a message is sent to in the event of a network or communications failure when sending to the primary destination endpoint.</span></span> <span data-ttu-id="1fa67-121">L'exemple suivant définit une liste de sauvegarde contenant un point de terminaison ; toutefois, plusieurs points de terminaison peuvent être spécifiés dans une liste de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="1fa67-121">The following example defines a backup list that contains one endpoint; however, multiple endpoints can be specified in a backup list.</span></span>

     <span data-ttu-id="1fa67-122">Si la liste de sauvegarde contient plusieurs points de terminaison, lorsqu'une panne réseau ou un échec de communication se produit, le service de routage essaie d'envoyer le message au premier point de terminaison de la liste.</span><span class="sxs-lookup"><span data-stu-id="1fa67-122">If the backup list contains multiple endpoints, when a network or communications failure occurs the Routing Service attempts to send the message to the first endpoint in the list.</span></span> <span data-ttu-id="1fa67-123">Si une panne réseau ou un échec de communication se produit lors de l'envoi à ce point de terminaison, le service de routage essaie d'envoyer le message au point de terminaison suivant dans la liste.</span><span class="sxs-lookup"><span data-stu-id="1fa67-123">If a network or communications failure occurs when sending to this endpoint, the Routing Service attempts to send the message to the next endpoint contained in the list.</span></span> <span data-ttu-id="1fa67-124">Le service continue à envoyer le message à chaque point de terminaison de la liste de sauvegarde jusqu'à ce que le message soit envoyé avec succès, que tous les points de terminaison de sauvegarde retournent une erreur liée au réseau ou aux communications, ou que le message soit envoyé et que le point de terminaison retourne une erreur non liée au réseau ou aux communications.</span><span class="sxs-lookup"><span data-stu-id="1fa67-124">The service continues sending the message to each endpoint in the backup endpoint list until the message is successfully sent, all backup endpoints return a network or communications-related error, or the message is sent and the endpoint returns a non-network, non-communications-related error.</span></span>

    ```xml
    <backupLists>
      <backupList name="backupEndpointList">
          <add endpointName="realDestination" />
      </backupList>
    </backupLists>
    ```

4. <span data-ttu-id="1fa67-125">Définissez la table de filtres, qui associe le filtre au point de terminaison deadDestination, et la liste de points de terminaison de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="1fa67-125">Define the filter table, which associates the filter with the deadDestination endpoint and the backup endpoint list.</span></span>  <span data-ttu-id="1fa67-126">Le service de routage essaie d'abord d'envoyer le message au point de terminaison de destination associé au filtre.</span><span class="sxs-lookup"><span data-stu-id="1fa67-126">The Routing Service first attempts to send the message to the destination endpoint associated with the filter.</span></span> <span data-ttu-id="1fa67-127">Puisque deadDestination contient une adresse qui ne fait référence à aucun service en cours d'exécution, cela provoque une erreur réseau.</span><span class="sxs-lookup"><span data-stu-id="1fa67-127">Since the deadDestination contains an address that does not refer to a running service, this results in a network error.</span></span> <span data-ttu-id="1fa67-128">Le service de routage tente ensuite d’envoyer le message au point de terminaison spécifié dans le backupEndpointList.</span><span class="sxs-lookup"><span data-stu-id="1fa67-128">The Routing Service then attempts to send the message to the endpoint specified in the backupEndpointList.</span></span>

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

5. <span data-ttu-id="1fa67-129">Pour évaluer les messages entrants en fonction du filtre contenu dans la table de filtres, vous devez associer la table de filtres aux points de terminaison de service, à l'aide du comportement de routage.</span><span class="sxs-lookup"><span data-stu-id="1fa67-129">To evaluate incoming messages against the filter contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span>  <span data-ttu-id="1fa67-130">L’exemple suivant illustre l’Association de « filterTable1 » aux points de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="1fa67-130">The following example demonstrates associating "filterTable1" with the service endpoints.</span></span>

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

## <a name="example"></a><span data-ttu-id="1fa67-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="1fa67-131">Example</span></span>

<span data-ttu-id="1fa67-132">Voici une liste complète du fichier de configuration :</span><span class="sxs-lookup"><span data-stu-id="1fa67-132">The following is a complete listing of the configuration file:</span></span>

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
