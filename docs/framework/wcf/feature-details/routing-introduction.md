---
title: Introduction au routage
ms.date: 03/30/2017
ms.assetid: bf6ceb38-6622-433b-9ee7-f79bc93497a1
ms.openlocfilehash: 8ce98aab2ed14401fa7c2cbf43eb92a633fa96b0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746467"
---
# <a name="routing-introduction"></a><span data-ttu-id="6759f-102">Introduction au routage</span><span class="sxs-lookup"><span data-stu-id="6759f-102">Routing Introduction</span></span>

<span data-ttu-id="6759f-103">Le service de routage fournit un intermédiaire SOAP générique connectable, capable de router des messages en fonction du contenu.</span><span class="sxs-lookup"><span data-stu-id="6759f-103">The Routing Service provides a generic pluggable SOAP intermediary that is capable of routing messages based on message content.</span></span> <span data-ttu-id="6759f-104">Le service de routage vous permet de créer une logique de routage complexe et d'implémenter des scénarios, tels que l'agrégation de service, le contrôle des versions de service, le routage par priorité et en mode multidiffusion.</span><span class="sxs-lookup"><span data-stu-id="6759f-104">With the Routing Service, you can create complex routing logic that allows you to implement scenarios such as service aggregation, service versioning, priority routing, and multicast routing.</span></span> <span data-ttu-id="6759f-105">Le service de routage fournit également une gestion des erreurs qui vous permet de définir des listes de points de terminaison de sauvegarde auxquels sont envoyés les messages en cas d'échec de l'envoi au point de terminaison de destination primaire.</span><span class="sxs-lookup"><span data-stu-id="6759f-105">The Routing Service also provides error handling that allows you to set up lists of backup endpoints, to which messages are sent if a failure occurs when sending to the primary destination endpoint.</span></span>

<span data-ttu-id="6759f-106">Cette rubrique est destinée aux nouveaux utilisateurs du service de routage ; elle présente la configuration de base et l'hébergement du service de routage.</span><span class="sxs-lookup"><span data-stu-id="6759f-106">This topic is intended for those new to the Routing Service and covers basic configuration and hosting of the Routing Service.</span></span>

## <a name="configuration"></a><span data-ttu-id="6759f-107">Configuration</span><span class="sxs-lookup"><span data-stu-id="6759f-107">Configuration</span></span>

<span data-ttu-id="6759f-108">Le service de routage est implémenté en tant que service WCF qui expose un ou plusieurs points de terminaison de service ; ceux-ci reçoivent les messages provenant d'applications clientes et les acheminent vers un ou plusieurs points de terminaison de destination.</span><span class="sxs-lookup"><span data-stu-id="6759f-108">The Routing Service is implemented as a WCF service that exposes one or more service endpoints that receive messages from client applications and route the messages to one or more destination endpoints.</span></span> <span data-ttu-id="6759f-109">Le service fournit une classe <xref:System.ServiceModel.Routing.RoutingBehavior>, appliquée aux points de terminaison de service exposés par le service.</span><span class="sxs-lookup"><span data-stu-id="6759f-109">The service provides a <xref:System.ServiceModel.Routing.RoutingBehavior>, which is applied to the service endpoints exposed by the service.</span></span> <span data-ttu-id="6759f-110">Ce comportement permet de configurer différents aspects du fonctionnement du service.</span><span class="sxs-lookup"><span data-stu-id="6759f-110">This behavior is used to configure various aspects of how the service operates.</span></span> <span data-ttu-id="6759f-111">Pour faciliter la configuration lors de l’utilisation d’un fichier de configuration, les paramètres sont spécifiés sur le **RoutingBehavior**.</span><span class="sxs-lookup"><span data-stu-id="6759f-111">For ease of configuration when using a configuration file, the parameters are specified on the **RoutingBehavior**.</span></span> <span data-ttu-id="6759f-112">Dans les scénarios basés sur du code, ces paramètres sont spécifiés dans le cadre d’un objet <xref:System.ServiceModel.Routing.RoutingConfiguration>, qui peut ensuite être transmis à un **RoutingBehavior**.</span><span class="sxs-lookup"><span data-stu-id="6759f-112">In code-based scenarios, these parameters would be specified as part of a <xref:System.ServiceModel.Routing.RoutingConfiguration> object, which can then be passed to a **RoutingBehavior**.</span></span>

<span data-ttu-id="6759f-113">Au moment du démarrage, ce comportement ajoute aux points de terminaison clients la classe <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, utilisée pour exécuter le traitement SOAP des messages.</span><span class="sxs-lookup"><span data-stu-id="6759f-113">When starting, this behavior adds the <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, which is used to perform SOAP processing of messages, to the client endpoints.</span></span> <span data-ttu-id="6759f-114">Cela permet au service de routage de transmettre des messages aux points de terminaison qui nécessitent une **MessageVersion** différente de celle du point de terminaison sur lequel le message a été reçu.</span><span class="sxs-lookup"><span data-stu-id="6759f-114">This allows the Routing Service to transmit messages to endpoints that require a different **MessageVersion** than the endpoint the message was received over.</span></span> <span data-ttu-id="6759f-115">**RoutingBehavior** enregistre également une extension de service, la <xref:System.ServiceModel.Routing.RoutingExtension>, qui fournit un point d’accessibilité pour modifier la configuration du service de routage au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="6759f-115">The **RoutingBehavior** also registers a service extension, the <xref:System.ServiceModel.Routing.RoutingExtension>, which provides an accessibility point for modifying the Routing Service configuration at run time.</span></span>

<span data-ttu-id="6759f-116">La classe **RoutingConfiguration** fournit un moyen cohérent de configurer et de mettre à jour la configuration du service de routage.</span><span class="sxs-lookup"><span data-stu-id="6759f-116">The **RoutingConfiguration** class provides a consistent means of configuring and updating the configuration of the Routing Service.</span></span>  <span data-ttu-id="6759f-117">Il contient des paramètres qui jouent le rôle de paramètres pour le service de routage et qui est utilisé pour configurer le **RoutingBehavior** lorsque le service démarre, ou est passé à **RoutingExtension** pour modifier la configuration de routage au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="6759f-117">It contains parameters that act as the settings for the Routing Service and is used to configure the **RoutingBehavior** when the service starts, or is passed to the **RoutingExtension** to modify routing configuration at run time.</span></span>

<span data-ttu-id="6759f-118">La logique de routage utilisée pour router les messages en fonction du contenu est définie en regroupant plusieurs objets <xref:System.ServiceModel.Dispatcher.MessageFilter> dans des tables de filtres (objets <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601>).</span><span class="sxs-lookup"><span data-stu-id="6759f-118">The routing logic used to perform content-based routing of messages is defined by grouping multiple <xref:System.ServiceModel.Dispatcher.MessageFilter> objects together into filter tables (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> objects).</span></span> <span data-ttu-id="6759f-119">Les messages entrants sont évalués par rapport aux filtres de messages contenus dans la table de filtres, et pour chaque **MessageFilter** qui correspond au message, transmis à un point de terminaison de destination.</span><span class="sxs-lookup"><span data-stu-id="6759f-119">Incoming messages are evaluated against the message filters contained in the filter table, and for each **MessageFilter** that matches the message, forwarded to a destination endpoint.</span></span> <span data-ttu-id="6759f-120">La table de filtres à utiliser pour router les messages est spécifiée à l’aide de **RoutingBehavior** dans la configuration ou par le biais du code à l’aide de l’objet **RoutingConfiguration** .</span><span class="sxs-lookup"><span data-stu-id="6759f-120">The filter table that should be used to route messages is specified by using either the **RoutingBehavior** in configuration or through code by using the **RoutingConfiguration** object.</span></span>

### <a name="defining-endpoints"></a><span data-ttu-id="6759f-121">Définition des points de terminaison</span><span class="sxs-lookup"><span data-stu-id="6759f-121">Defining Endpoints</span></span>

<span data-ttu-id="6759f-122">La première chose à configurer n'est pas, comme vous pourriez le penser, de définir la logique de routage que vous utiliserez, mais de déterminer la forme des points de terminaison vers lesquels les messages seront routés.</span><span class="sxs-lookup"><span data-stu-id="6759f-122">While it may seem that you should start your configuration by defining the routing logic you will use, your first step should actually be to determine the shape of the endpoints you will be routing messages to.</span></span> <span data-ttu-id="6759f-123">Le service de routage utilise des contrats définissant la forme des canaux qui permettent de recevoir et envoyer des messages ; par conséquent, la forme du canal d'entrée doit correspondre à celle du canal de sortie.</span><span class="sxs-lookup"><span data-stu-id="6759f-123">The Routing Service uses contracts that define the shape of the channels used to receive and send messages, and therefore the shape of the input channel must match that of the output channel.</span></span>  <span data-ttu-id="6759f-124">Par exemple, si vous effectuez un routage vers des points de terminaison utilisant la forme de canal demande-réponse, vous devez utiliser un contrat compatible sur les points de terminaison entrants, comme l'interface <xref:System.ServiceModel.Routing.IRequestReplyRouter>.</span><span class="sxs-lookup"><span data-stu-id="6759f-124">For example, if you are routing to endpoints that use the request-reply channel shape, then you must use a compatible contract on the inbound endpoints, such as the <xref:System.ServiceModel.Routing.IRequestReplyRouter>.</span></span>

<span data-ttu-id="6759f-125">Cela signifie que si vos points de terminaison de destination utilisent des contrats avec plusieurs modèles de communication (comme une combinaison d'opérations monodirectionnelles et bidirectionnelles), vous ne pouvez pas créer de point de terminaison de service unique qui puisse recevoir et router des messages vers tous les points de terminaison de destination.</span><span class="sxs-lookup"><span data-stu-id="6759f-125">This means that if your destination endpoints use contracts with multiple communication patterns (such as mixing one-way and two-way operations,) you cannot create a single service endpoint that can receive and route messages to all of them.</span></span> <span data-ttu-id="6759f-126">Vous devez déterminer les points de terminaison qui ont des formes compatibles et définir un ou plusieurs points de terminaison de service qui permettront de recevoir les messages devant être routés vers les points de terminaison de destination.</span><span class="sxs-lookup"><span data-stu-id="6759f-126">You must determine which endpoints have compatible shapes and define one or more service endpoints that will be used to receive messages to be routed to the destination endpoints.</span></span>

> [!NOTE]
> <span data-ttu-id="6759f-127">En cas d’utilisation de contrats spécifiant plusieurs modèles de communication (comme une combinaison d’opérations monodirectionnelles et bidirectionnelles), vous pouvez utiliser un contrat duplex au service de routage tel que l’interface <xref:System.ServiceModel.Routing.IDuplexSessionRouter>.</span><span class="sxs-lookup"><span data-stu-id="6759f-127">When working with contracts that specify multiple communication patterns (such as a mix of one-way and two-way operations,) a workaround is to use a duplex contract at the Routing Service such as <xref:System.ServiceModel.Routing.IDuplexSessionRouter>.</span></span> <span data-ttu-id="6759f-128">Cependant, cela suppose que la liaison soit capable d’une communication duplex, ce qui n’est pas le cas dans tous les scénarios.</span><span class="sxs-lookup"><span data-stu-id="6759f-128">However this means that the binding must be capable of duplex communication, which may not be possible for all scenarios.</span></span> <span data-ttu-id="6759f-129">Dans les scénarios où cela n'est pas possible, il faudra peut-être développer la communication en plusieurs points de terminaison ou modifier l'application.</span><span class="sxs-lookup"><span data-stu-id="6759f-129">In scenarios where this is not possible, factoring the communication into multiple endpoints or modifying the application may be necessary.</span></span>

<span data-ttu-id="6759f-130">Pour plus d’informations sur les contrats de routage, consultez [routage des contrats](routing-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="6759f-130">For more information about routing contracts, see [Routing Contracts](routing-contracts.md).</span></span>

<span data-ttu-id="6759f-131">Une fois le point de terminaison de service défini, vous pouvez utiliser **RoutingBehavior** pour associer un **RoutingConfiguration** spécifique au point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="6759f-131">After the service endpoint is defined, you can use the **RoutingBehavior** to associate a specific **RoutingConfiguration** with the endpoint.</span></span> <span data-ttu-id="6759f-132">Lors de la configuration du service de routage à l’aide d’un fichier de configuration, **RoutingBehavior** est utilisé pour spécifier la table de filtres qui contient la logique de routage utilisée pour traiter les messages reçus sur ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="6759f-132">When configuring the Routing Service by using a configuration file, the **RoutingBehavior** is used to specify the filter table that contains the routing logic used to process messages received on this endpoint.</span></span> <span data-ttu-id="6759f-133">Si vous configurez le service de routage par programmation, vous pouvez spécifier la table de filtres à l’aide de **RoutingConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="6759f-133">If you are configuring the Routing Service programmatically you can specify the filter table by using the **RoutingConfiguration**.</span></span>

<span data-ttu-id="6759f-134">L'exemple suivant définit les points de terminaison clients et de service utilisés par le service de routage à la fois par programme et par un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="6759f-134">The following example defines the service and client endpoints that are used by the Routing Service both programmatically and by using a configuration file.</span></span>

```xml
<services>
  <!--ROUTING SERVICE -->
  <service behaviorConfiguration="routingData"
            name="System.ServiceModel.Routing.RoutingService">
    <host>
      <baseAddresses>
        <add baseAddress="http://localhost:8000/routingservice/router"/>
      </baseAddresses>
    </host>
    <!-- Define the service endpoints that are receive messages -->
    <endpoint address=""
              binding="wsHttpBinding"
              name="reqReplyEndpoint"
              contract="System.ServiceModel.Routing.IRequestReplyRouter" />
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="routingData">
      <serviceMetadata httpGetEnabled="True"/>
      <!-- Add the RoutingBehavior and specify the Routing Table to use -->
      <routing filterTableName="routingTable1" />
    </behavior>
  </serviceBehaviors>
</behaviors>
<client>
<!-- Define the client endpoint(s) to route messages to -->
  <endpoint name="CalculatorService"
            address="http://localhost:8000/servicemodelsamples/service"
            binding="wsHttpBinding" contract="*" />
</client>
```

```csharp
//set up some communication defaults
string clientAddress = "http://localhost:8000/servicemodelsamples/service";
string routerAddress = "http://localhost:8000/routingservice/router";
Binding routerBinding = new WSHttpBinding();
Binding clientBinding = new WSHttpBinding();
//add the endpoint the router uses to receive messages
serviceHost.AddServiceEndpoint(
     typeof(IRequestReplyRouter),
     routerBinding,
     routerAddress);
//create the client endpoint the router routes messages to
ContractDescription contract = ContractDescription.GetContract(
     typeof(IRequestReplyRouter));
ServiceEndpoint client = new ServiceEndpoint(
     contract,
     clientBinding,
     new EndpointAddress(clientAddress));
//create a new routing configuration object
RoutingConfiguration rc = new RoutingConfiguration();
….
rc.FilterTable.Add(new MatchAllMessageFilter(), endpointList);
//attach the behavior to the service host
serviceHost.Description.Behaviors.Add(
     new RoutingBehavior(rc));
```

<span data-ttu-id="6759f-135">Cet exemple configure le service de routage pour exposer un point de terminaison unique avec une adresse de `http://localhost:8000/routingservice/router`, qui est utilisée pour recevoir les messages à Router.</span><span class="sxs-lookup"><span data-stu-id="6759f-135">This example configures the Routing Service to expose a single endpoint with an address of `http://localhost:8000/routingservice/router`, which is used to receive messages to be routed.</span></span> <span data-ttu-id="6759f-136">Étant donné que les messages sont routés vers des points de terminaison demande-réponse, le point de terminaison de service utilise le contrat <xref:System.ServiceModel.Routing.IRequestReplyRouter>.</span><span class="sxs-lookup"><span data-stu-id="6759f-136">Because the messages are routed to request-reply endpoints, the service endpoint uses the <xref:System.ServiceModel.Routing.IRequestReplyRouter> contract.</span></span> <span data-ttu-id="6759f-137">Cette configuration définit également un point de terminaison client unique de `http://localhost:8000/servicemodelsample/service` vers lequel les messages sont routés.</span><span class="sxs-lookup"><span data-stu-id="6759f-137">This configuration also defines a single client endpoint of `http://localhost:8000/servicemodelsample/service` that messages are routed to.</span></span> <span data-ttu-id="6759f-138">La table de filtres (non affichée) nommée « routingTable1 » contient la logique de routage utilisée pour router les messages et est associée au point de terminaison de service à l’aide de **RoutingBehavior** (pour un fichier de configuration) ou de **RoutingConfiguration** (pour la configuration par programmation).</span><span class="sxs-lookup"><span data-stu-id="6759f-138">The filter table (not shown) named "routingTable1" contains the routing logic used to route messages, and is associated with the service endpoint by using the **RoutingBehavior** (for a configuration file) or **RoutingConfiguration** (for programmatic configuration).</span></span>

### <a name="routing-logic"></a><span data-ttu-id="6759f-139">Logique de routage</span><span class="sxs-lookup"><span data-stu-id="6759f-139">Routing Logic</span></span>

<span data-ttu-id="6759f-140">Pour définir la logique de routage utilisée pour router les messages, vous devez déterminer sur quelles données contenues dans les messages entrants il est possible d'agir de manière unique.</span><span class="sxs-lookup"><span data-stu-id="6759f-140">To define the routing logic used to route messages, you must determine what data contained within the incoming messages can be uniquely acted upon.</span></span> <span data-ttu-id="6759f-141">Par exemple, si tous les points de terminaison de destination de votre routage partagent la même Action SOAP, la valeur de l'Action contenue dans le message ne constitue pas un bon indicateur du point de terminaison spécifique vers lequel le message doit être routé.</span><span class="sxs-lookup"><span data-stu-id="6759f-141">For example, if all the destination endpoints you are routing to share the same SOAP Actions, the value of the Action contained within the message is not a good indicator of which specific endpoint the message should be routed to.</span></span> <span data-ttu-id="6759f-142">Si vous devez router des messages uniquement vers un point de terminaison spécifique, vous devez appliquer un filtre sur des données qui identifient de manière unique le point de terminaison de destination vers lequel le message est routé.</span><span class="sxs-lookup"><span data-stu-id="6759f-142">If you must uniquely route messages to one specific endpoint, you should filter upon data that uniquely identifies the destination endpoint that the message is routed to.</span></span>

<span data-ttu-id="6759f-143">Le service de routage fournit plusieurs implémentations de **MessageFilter** qui inspectent des valeurs spécifiques dans le message, telles que l’adresse, l’action, le nom du point de terminaison ou même une requête XPath.</span><span class="sxs-lookup"><span data-stu-id="6759f-143">The Routing Service provides several **MessageFilter** implementations that inspect specific values within the message, such as the address, action, endpoint name, or even an XPath query.</span></span> <span data-ttu-id="6759f-144">Si aucune de ces implémentations ne répond à vos besoins, vous pouvez créer une implémentation personnalisée de **MessageFilter** .</span><span class="sxs-lookup"><span data-stu-id="6759f-144">If none of these implementations meet your needs you can create a custom **MessageFilter** implementation.</span></span> <span data-ttu-id="6759f-145">Pour plus d’informations sur les filtres de messages et pour obtenir une comparaison des implémentations utilisées par le service de routage, consultez [filtres de message](message-filters.md) et [choix d’un filtre](choosing-a-filter.md).</span><span class="sxs-lookup"><span data-stu-id="6759f-145">For more information about message filters and a comparison of the implementations used by the Routing Service, see [Message Filters](message-filters.md) and [Choosing a Filter](choosing-a-filter.md).</span></span>

<span data-ttu-id="6759f-146">Plusieurs filtres de messages sont organisés en tables de filtres, qui associent chaque **MessageFilter** à un point de terminaison de destination.</span><span class="sxs-lookup"><span data-stu-id="6759f-146">Multiple message filters are organized together into filter tables, which associate each **MessageFilter** with a destination endpoint.</span></span> <span data-ttu-id="6759f-147">La table de filtres peut également être utilisée pour spécifier une liste de points de terminaison de sauvegarde auxquels, en cas d'échec de transmission, le service de routage tente d'envoyer le message.</span><span class="sxs-lookup"><span data-stu-id="6759f-147">Optionally, the filter table can also be used to specify a list of back-up endpoints that the Routing Service will attempt to send the message to in the event of a transmission failure.</span></span>

<span data-ttu-id="6759f-148">Par défaut, tous les filtres de message d'une table de filtres sont évalués simultanément ; toutefois, vous pouvez spécifier une propriété <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> qui fait évaluer les filtres de messages dans un ordre spécifique.</span><span class="sxs-lookup"><span data-stu-id="6759f-148">By default all message filters within a filter table are evaluated simultaneously; however, you can specify a <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> that causes the message filters to be evaluated in a specific order.</span></span> <span data-ttu-id="6759f-149">Les entrées de priorité plus élevée sont évaluées en premier et les filtres de message de priorité plus faible ne sont pas évalués si un résultat est trouvé à un niveau de priorité supérieur.</span><span class="sxs-lookup"><span data-stu-id="6759f-149">All entries with the highest priority are evaluated first, and message filters of lower priorities are not evaluated if a match is found at a higher priority level.</span></span> <span data-ttu-id="6759f-150">Pour plus d’informations sur les tables de filtres, consultez [filtres de messages](message-filters.md).</span><span class="sxs-lookup"><span data-stu-id="6759f-150">For more information about filter tables, see [Message Filters](message-filters.md).</span></span>

<span data-ttu-id="6759f-151">Les exemples suivants utilisent l'objet <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>, qui prend tous les messages qui ont la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="6759f-151">The following examples use the <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>, which evaluates to `true` for all messages.</span></span> <span data-ttu-id="6759f-152">Ce **MessageFilter** est ajouté à la table de filtres « routingTable1 », qui associe le **MessageFilter** au point de terminaison client nommé « CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="6759f-152">This **MessageFilter** is added to the "routingTable1" filter table, which associates the **MessageFilter** with the client endpoint named "CalculatorService".</span></span> <span data-ttu-id="6759f-153">Le **RoutingBehavior** spécifie ensuite que cette table doit être utilisée pour acheminer les messages traités par le point de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="6759f-153">The **RoutingBehavior** then specifies that this table should be used to route messages processed by the service endpoint.</span></span>

```xml
<behaviors>
  <serviceBehaviors>
    <behavior name="routingData">
      <serviceMetadata httpGetEnabled="True"/>
      <!-- Add the RoutingBehavior and specify the Routing Table to use -->
      <routing filterTableName="routingTable1" />
    </behavior>
  </serviceBehaviors>
</behaviors>
<!--ROUTING SECTION -->
<routing>
  <filters>
    <filter name="MatchAllFilter1" filterType="MatchAll" />
  </filters>
  <filterTables>
    <table name="routingTable1">
      <filters>
        <add filterName="MatchAllFilter1" endpointName="CalculatorService" />
      </filters>
    </table>
  </filterTables>
</routing>
```

```csharp
//create a new routing configuration object
RoutingConfiguration rc = new RoutingConfiguration();
//create the endpoint list that contains the endpoints to route to
//in this case we have only one
List<ServiceEndpoint> endpointList = new List<ServiceEndpoint>();
endpointList.Add(client);
//add a MatchAll filter to the Router's filter table
//map it to the endpoint list defined earlier
//when a message matches this filter, it is sent to the endpoint contained in the list
rc.FilterTable.Add(new MatchAllMessageFilter(), endpointList);
```

> [!NOTE]
> <span data-ttu-id="6759f-154">Par défaut, le service de routage évalue uniquement les en-têtes du message.</span><span class="sxs-lookup"><span data-stu-id="6759f-154">By default, the Routing Service only evaluates the headers of the message.</span></span> <span data-ttu-id="6759f-155">Pour permettre aux filtres d'accéder au corps du message, vous devez attribuer à la propriété <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="6759f-155">To allow the filters to access the message body, you must set <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> to `false`.</span></span>

<span data-ttu-id="6759f-156">**Multidiffusion**</span><span class="sxs-lookup"><span data-stu-id="6759f-156">**Multicast**</span></span>

<span data-ttu-id="6759f-157">Alors que de nombreuses configurations de service de routage utilisent une logique de filtre exclusive qui route les messages vers un seul point de terminaison spécifique, vous aurez peut-être besoin de router un message donné vers plusieurs points de terminaison de destination.</span><span class="sxs-lookup"><span data-stu-id="6759f-157">While many Routing Service configurations use exclusive filter logic that routes messages to only one specific endpoint, you may need to route a given message to multiple destination endpoints.</span></span> <span data-ttu-id="6759f-158">Pour envoyer un message en mode multidiffusion à des destinations multiples, les conditions suivantes doivent être remplies :</span><span class="sxs-lookup"><span data-stu-id="6759f-158">To multicast a message to multiple destinations, the following conditions must be true:</span></span>

- <span data-ttu-id="6759f-159">La forme de canal ne doit pas être de type demande-réponse (bien qu'elle puisse être monodirectionnelle ou duplex), parce qu'une seule réponse peut être reçue par l'application cliente en réponse à la demande.</span><span class="sxs-lookup"><span data-stu-id="6759f-159">The channel shape must not be request-reply (though may be one-way or duplex,) because only one reply can be received by the client application in response to the request.</span></span>

- <span data-ttu-id="6759f-160">Plusieurs filtres doivent retourner une valeur `true` lors de l'évaluation du message.</span><span class="sxs-lookup"><span data-stu-id="6759f-160">Multiple filters must return `true` when evaluating the message.</span></span>

<span data-ttu-id="6759f-161">Si ces conditions sont remplies, le message est routé vers tous les points de terminaison de tous les filtres qui doivent avoir la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="6759f-161">If these conditions are met, the message is routed to all endpoints of all filters that evaluate to `true`.</span></span> <span data-ttu-id="6759f-162">L’exemple suivant définit une configuration de routage qui entraîne le routage des messages vers les deux points de terminaison si l’adresse du point de terminaison dans le message est `http://localhost:8000/routingservice/router/rounding`.</span><span class="sxs-lookup"><span data-stu-id="6759f-162">The following example defines a routing configuration that results in messages being routed to both endpoints if the endpoint address in the message is `http://localhost:8000/routingservice/router/rounding`.</span></span>

```xml
<!--ROUTING SECTION -->
<routing>
  <filters>
    <filter name="MatchAllFilter1" filterType="MatchAll" />
    <filter name="RoundingFilter1" filterType="EndpointAddress"
            filterData="http://localhost:8000/routingservice/router/rounding" />
  </filters>
  <filterTables>
    <table name="routingTable1">
      <filters>
        <add filterName="MatchAllFilter1" endpointName="CalculatorService" />
        <add filterName="RoundingFilter1" endpointName="RoundingCalcService" />
      </filters>
    </table>
  </filterTables>
</routing>
```

```csharp
rc.FilterTable.Add(new MatchAllMessageFilter(), calculatorEndpointList);
rc.FilterTable.Add(new EndpointAddressMessageFilter(new EndpointAddress(
    "http://localhost:8000/routingservice/router/rounding")),
    roundingCalcEndpointList);
```

### <a name="soap-processing"></a><span data-ttu-id="6759f-163">Traitement SOAP</span><span class="sxs-lookup"><span data-stu-id="6759f-163">SOAP Processing</span></span>

<span data-ttu-id="6759f-164">Pour prendre en charge le routage de messages entre des protocoles différents, le **RoutingBehavior** ajoute par défaut le <xref:System.ServiceModel.Routing.SoapProcessingBehavior> à tous les points de terminaison clients vers lesquels les messages sont routés.</span><span class="sxs-lookup"><span data-stu-id="6759f-164">To support the routing of messages between dissimilar protocols, the **RoutingBehavior** by default adds the <xref:System.ServiceModel.Routing.SoapProcessingBehavior> to all client endpoint(s) that messages are routed to.</span></span> <span data-ttu-id="6759f-165">Ce comportement crée automatiquement un nouveau **MessageVersion** avant de router le message vers le point de terminaison, ainsi que la création d’un **MessageVersion** compatible pour tout document de réponse avant de le retourner à l’application cliente à l’origine de la demande.</span><span class="sxs-lookup"><span data-stu-id="6759f-165">This behavior automatically creates a new **MessageVersion** before routing the message to the endpoint, as well as creating a compatible **MessageVersion** for any response document before returning it to the requesting client application.</span></span>

<span data-ttu-id="6759f-166">Les étapes nécessaires pour créer un nouveau **MessageVersion** pour le message sortant sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="6759f-166">The steps taken to create a new **MessageVersion** for the outbound message are as follows:</span></span>

<span data-ttu-id="6759f-167">**Traitement des demandes**</span><span class="sxs-lookup"><span data-stu-id="6759f-167">**Request processing**</span></span>

- <span data-ttu-id="6759f-168">Obtient le **MessageVersion** de la liaison/canal sortant.</span><span class="sxs-lookup"><span data-stu-id="6759f-168">Get the **MessageVersion** of the outbound binding/channel.</span></span>

- <span data-ttu-id="6759f-169">Obtenez le lecteur de corps du message d'origine.</span><span class="sxs-lookup"><span data-stu-id="6759f-169">Get the body reader for the original message.</span></span>

- <span data-ttu-id="6759f-170">Créez un nouveau message avec la même action, le même lecteur de corps et un nouveau **MessageVersion**.</span><span class="sxs-lookup"><span data-stu-id="6759f-170">Create a new message with the same action, body reader, and a new **MessageVersion**.</span></span>

- <span data-ttu-id="6759f-171">Si <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing. None**, copiez les en-têtes vers, from, FaultTo et latesto dans le nouveau message.</span><span class="sxs-lookup"><span data-stu-id="6759f-171">If <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> != **Addressing.None**, copy the To, From, FaultTo, and RelatesTo headers to the new message.</span></span>

- <span data-ttu-id="6759f-172">Copiez toutes les propriétés du message dans le nouveau message.</span><span class="sxs-lookup"><span data-stu-id="6759f-172">Copy all message properties to the new message.</span></span>

- <span data-ttu-id="6759f-173">Stockez le message de demande d'origine à utiliser lors du traitement de la réponse.</span><span class="sxs-lookup"><span data-stu-id="6759f-173">Store the original request message to use when processing the response.</span></span>

- <span data-ttu-id="6759f-174">Retournez le nouveau message de demande.</span><span class="sxs-lookup"><span data-stu-id="6759f-174">Return the new request message.</span></span>

<span data-ttu-id="6759f-175">**Traitement des réponses**</span><span class="sxs-lookup"><span data-stu-id="6759f-175">**Response processing**</span></span>

- <span data-ttu-id="6759f-176">Obtient le **MessageVersion** du message de demande d’origine.</span><span class="sxs-lookup"><span data-stu-id="6759f-176">Get the **MessageVersion** of the original request message.</span></span>

- <span data-ttu-id="6759f-177">Obtenez le lecteur de corps du message de réponse reçu.</span><span class="sxs-lookup"><span data-stu-id="6759f-177">Get the body reader for the received response message.</span></span>

- <span data-ttu-id="6759f-178">Créez un nouveau message de réponse avec la même action, le même lecteur de corps et le **MessageVersion** du message de demande d’origine.</span><span class="sxs-lookup"><span data-stu-id="6759f-178">Create a new response message with the same action, body reader, and the **MessageVersion** of the original request message.</span></span>

- <span data-ttu-id="6759f-179">Si <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing. None**, copiez les en-têtes vers, from, FaultTo et latesto dans le nouveau message.</span><span class="sxs-lookup"><span data-stu-id="6759f-179">If <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> != **Addressing.None**, copy the To, From, FaultTo, and RelatesTo headers to the new message.</span></span>

- <span data-ttu-id="6759f-180">Copiez les propriétés du message dans le nouveau message.</span><span class="sxs-lookup"><span data-stu-id="6759f-180">Copy the message properties to the new message.</span></span>

- <span data-ttu-id="6759f-181">Retournez le nouveau message de réponse.</span><span class="sxs-lookup"><span data-stu-id="6759f-181">Return the new response message.</span></span>

<span data-ttu-id="6759f-182">Par défaut, le **SoapProcessingBehavior** est automatiquement ajouté aux points de terminaison du client par le <xref:System.ServiceModel.Routing.RoutingBehavior> au démarrage du service ; Toutefois, vous pouvez contrôler si le traitement SOAP est ajouté à tous les points de terminaison clients à l’aide de la propriété <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A>.</span><span class="sxs-lookup"><span data-stu-id="6759f-182">By default, the **SoapProcessingBehavior** is automatically added to the client endpoints by the <xref:System.ServiceModel.Routing.RoutingBehavior> when the service starts; however, you can control whether SOAP processing is added to all client endpoints by using the <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> property.</span></span> <span data-ttu-id="6759f-183">Vous pouvez également ajouter directement le comportement à un point de terminaison spécifique, au niveau duquel vous pouvez l'activer ou le désactiver, si un contrôle plus précis du traitement SOAP est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="6759f-183">You can also add the behavior directly to a specific endpoint and enable or disable this behavior at the endpoint level if a more granular control of SOAP processing is required.</span></span>

> [!NOTE]
> <span data-ttu-id="6759f-184">Si le traitement SOAP est désactivé pour un point de terminaison qui requiert une version MessageVersion différente de celle du message de demande d'origine, vous devez fournir un mécanisme personnalisé pour effectuer les modifications SOAP nécessaires avant d'envoyer le message au point de terminaison de destination.</span><span class="sxs-lookup"><span data-stu-id="6759f-184">If SOAP processing is disabled for an endpoint that requires a different MessageVersion than that of the original request message, you must provide a custom mechanism for performing any SOAP modifications that are required before sending the message to the destination endpoint.</span></span>

<span data-ttu-id="6759f-185">Dans les exemples suivants, la propriété **SoapProcessingEnabled** est utilisée pour empêcher l’ajout automatique de **SoapProcessingBehavior** à tous les points de terminaison clients.</span><span class="sxs-lookup"><span data-stu-id="6759f-185">In the following examples, the **soapProcessingEnabled** property is used to prevent the **SoapProcessingBehavior** from being automatically added to all client endpoints.</span></span>

```xml
<behaviors>
  <!--default routing service behavior definition-->
  <serviceBehaviors>
    <behavior name="routingConfiguration">
      <routing filterTableName="filterTable1" soapProcessingEnabled="false"/>
    </behavior>
  </serviceBehaviors>
</behaviors>
```

```csharp
//create the default RoutingConfiguration
RoutingConfiguration rc = new RoutingConfiguration();
rc.SoapProcessingEnabled = false;
```

### <a name="dynamic-configuration"></a><span data-ttu-id="6759f-186">Configuration dynamique</span><span class="sxs-lookup"><span data-stu-id="6759f-186">Dynamic Configuration</span></span>

<span data-ttu-id="6759f-187">Lorsque vous ajoutez des points de terminaison clients supplémentaires, ou que vous devez modifier les filtres utilisés pour router les messages, vous devez pouvoir mettre la configuration à jour dynamiquement au moment de l'exécution afin d'éviter une interruption de service aux points de terminaison qui reçoivent actuellement des messages via le service de routage.</span><span class="sxs-lookup"><span data-stu-id="6759f-187">When you add additional client endpoints, or need to modify the filters that are used to route messages, you must have a way to update the configuration dynamically at run time to prevent interrupting the service to the endpoints currently receiving messages through the Routing Service.</span></span> <span data-ttu-id="6759f-188">Modifier un fichier de configuration ou le code de l'application hôte n'est pas toujours suffisant, car l'une ou l'autre méthode requiert le recyclage de l'application, ce qui signifierait la perte potentielle de tous les messages actuellement en transit et le risque d'un temps mort en attendant le redémarrage du service.</span><span class="sxs-lookup"><span data-stu-id="6759f-188">Modifying a configuration file or the code of the host application is not always sufficient, because either method requires recycling the application, which would lead to the potential loss of any messages currently in transit and the potential for downtime while waiting on the service to restart.</span></span>

<span data-ttu-id="6759f-189">Vous pouvez uniquement modifier **RoutingConfiguration** par programme.</span><span class="sxs-lookup"><span data-stu-id="6759f-189">You can only modify the **RoutingConfiguration** programmatically.</span></span> <span data-ttu-id="6759f-190">Bien que vous puissiez initialement configurer le service à l’aide d’un fichier de configuration, vous pouvez uniquement modifier la configuration au moment de l’exécution en construisant un nouveau **RoutingConfiguration** et en le transmettant en tant que paramètre à la méthode <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> exposée par l’extension de service <xref:System.ServiceModel.Routing.RoutingExtension>.</span><span class="sxs-lookup"><span data-stu-id="6759f-190">While you can initially configure the service by using a configuration file, you can only modify the configuration at run time by constructing a new **RoutingConfiguration** and passing it as a parameter to the <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> method exposed by the <xref:System.ServiceModel.Routing.RoutingExtension> service extension.</span></span> <span data-ttu-id="6759f-191">Tous les messages actuellement en transit continuent à être routés à l’aide de la configuration précédente, tandis que les messages reçus après l’appel à **ApplyConfiguration** utilisent la nouvelle configuration.</span><span class="sxs-lookup"><span data-stu-id="6759f-191">Any messages currently in transit continue to be routed using the previous configuration, while messages received after the call to **ApplyConfiguration** use the new configuration.</span></span> <span data-ttu-id="6759f-192">L'exemple suivant montre la création d'une instance du service de routage, suivie d'une modification de la configuration.</span><span class="sxs-lookup"><span data-stu-id="6759f-192">The following example demonstrates creating an instance of the Routing Service and then subsequently modifying the configuration.</span></span>

```csharp
RoutingConfiguration routingConfig = new RoutingConfiguration();
routingConfig.RouteOnHeadersOnly = true;
routingConfig.FilterTable.Add(new MatchAllMessageFilter(), endpointList);
RoutingBehavior routing = new RoutingBehavior(routingConfig);
routerHost.Description.Behaviors.Add(routing);
routerHost.Open();
// Construct a new RoutingConfiguration
RoutingConfiguration rc2 = new RoutingConfiguration();
ServiceEndpoint clientEndpoint = new ServiceEndpoint();
ServiceEndpoint clientEndpoint2 = new ServiceEndpoint();
// Add filters to the FilterTable in the new configuration
rc2.FilterTable.add(new MatchAllMessageFilter(),
       new List<ServiceEndpoint>() { clientEndpoint });
rc2.FilterTable.add(new MatchAllMessageFilter(),
       new List<ServiceEndpoint>() { clientEndpoint2 });
rc2.RouteOnHeadersOnly = false;
// Apply the new configuration to the Routing Service hosted in
routerHost.routerHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc2);
```

> [!NOTE]
> <span data-ttu-id="6759f-193">Lorsque le service de routage est mis à jour de cette manière, seule la transmission d'une nouvelle configuration est possible.</span><span class="sxs-lookup"><span data-stu-id="6759f-193">When updating the Routing Service in this manner it is only possible to pass a new configuration.</span></span> <span data-ttu-id="6759f-194">Il est impossible de modifier uniquement une sélection d'éléments de la configuration actuelle ni d'ajouter à celle-ci de nouvelles entrées ; vous devez créer et transmettre une nouvelle configuration qui remplace l'existante.</span><span class="sxs-lookup"><span data-stu-id="6759f-194">It is not possible to modify only select elements of the current configuration or append new entries to the current configuration; you must create and pass a new configuration that replaces the existing one.</span></span>

> [!NOTE]
> <span data-ttu-id="6759f-195">Toutes les sessions ouvertes à l'aide de la configuration précédente continuent à utiliser la configuration précédente.</span><span class="sxs-lookup"><span data-stu-id="6759f-195">Any sessions opened using the previous configuration continue using the previous configuration.</span></span> <span data-ttu-id="6759f-196">La nouvelle configuration est utilisée uniquement par les nouvelles sessions.</span><span class="sxs-lookup"><span data-stu-id="6759f-196">The new configuration is only used by new sessions.</span></span>

## <a name="error-handling"></a><span data-ttu-id="6759f-197">Gestion des erreurs</span><span class="sxs-lookup"><span data-stu-id="6759f-197">Error Handling</span></span>

<span data-ttu-id="6759f-198">Si un objet <xref:System.ServiceModel.CommunicationException> est rencontré lors de la tentative d'envoi d'un message, une gestion des erreurs intervient.</span><span class="sxs-lookup"><span data-stu-id="6759f-198">If any <xref:System.ServiceModel.CommunicationException> is encountered while attempting to send a message, error handling take place.</span></span> <span data-ttu-id="6759f-199">Ces exceptions indiquent en général qu'un problème s'est produit lors de la tentative de communication avec le point de terminaison client défini ; il peut s'agir d'une exception <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException> ou <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span><span class="sxs-lookup"><span data-stu-id="6759f-199">These exceptions typically indicate that a problem was encountered while attempting to communicate with the defined client endpoint, such as an <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, or <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span></span> <span data-ttu-id="6759f-200">Le code de gestion des erreurs intercepte également et tente de réessayer l’envoi lorsqu’un <xref:System.TimeoutException> se produit, ce qui constitue une autre exception courante qui n’est pas dérivée de **CommunicationException**.</span><span class="sxs-lookup"><span data-stu-id="6759f-200">The error handling-code will also catch and attempt to retry sending when a <xref:System.TimeoutException> occurs, which is another common exception that is not derived from **CommunicationException**.</span></span>

<span data-ttu-id="6759f-201">Lorsque l'une des exceptions précédentes se produit, le service de routage bascule sur une liste de points de terminaison de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="6759f-201">When one of the preceding exceptions occurs, the Routing Service fails over to a list of backup endpoints.</span></span> <span data-ttu-id="6759f-202">Si tous les points de terminaison de sauvegarde échouent avec un échec de communication, ou si un point de terminaison retourne une exception indiquant une défaillance dans le service de destination, le service de routage retourne une erreur à l'application cliente.</span><span class="sxs-lookup"><span data-stu-id="6759f-202">If all backup endpoints fail with a communications failure, or if an endpoint returns an exception that indicates a failure within the destination service, the Routing Service returns a fault to the client application.</span></span>

> [!NOTE]
> <span data-ttu-id="6759f-203">Les fonctionnalités de gestion des erreurs capturent et gèrent des exceptions qui se produisent lors des tentatives d'envoi d'un message et de fermeture d'un canal.</span><span class="sxs-lookup"><span data-stu-id="6759f-203">The error-handling functionality captures and handles exceptions that occur when attempting to send a message and when attempting to close a channel.</span></span> <span data-ttu-id="6759f-204">Le code de gestion des erreurs n’est pas destiné à détecter ou gérer les exceptions créées par les points de terminaison d’application avec lesquels il communique. une <xref:System.ServiceModel.FaultException> levée par un service s’affiche sur le service de routage en tant que **FaultMessage** et est renvoyée au client.</span><span class="sxs-lookup"><span data-stu-id="6759f-204">The error-handling code is not intended to detect or handle exceptions created by the application endpoints it is communicating with; a <xref:System.ServiceModel.FaultException> thrown by a service appears at the Routing Service as a **FaultMessage** and is flowed back to the client.</span></span>
>
> <span data-ttu-id="6759f-205">Si une erreur se produit lorsque le service de routage tente de relayer un message, vous pouvez obtenir un <xref:System.ServiceModel.FaultException> côté client, au lieu du <xref:System.ServiceModel.EndpointNotFoundException> que vous obtiendriez normalement en l'absence du service de routage.</span><span class="sxs-lookup"><span data-stu-id="6759f-205">If an error occurs when the routing service tries to relay a message, you may  get a <xref:System.ServiceModel.FaultException> on the client side, rather than a <xref:System.ServiceModel.EndpointNotFoundException> you would normally get in the absence of the routing service.</span></span> <span data-ttu-id="6759f-206">Un service de routage peut par conséquent masquer les exceptions et ne pas fournir une transparence complète, sauf si vous analysez les exceptions imbriquées.</span><span class="sxs-lookup"><span data-stu-id="6759f-206">A routing service may thus mask exceptions and not provide full transparency unless you examine nested exceptions.</span></span>

### <a name="tracing-exceptions"></a><span data-ttu-id="6759f-207">Suivi d'exceptions</span><span class="sxs-lookup"><span data-stu-id="6759f-207">Tracing Exceptions</span></span>

<span data-ttu-id="6759f-208">Lorsque l’envoi d’un message à un point de terminaison dans une liste échoue, le service de routage effectue le suivi des données d’exception résultantes et joint les détails de l’exception sous la forme d’une propriété de message nommée **exceptions**.</span><span class="sxs-lookup"><span data-stu-id="6759f-208">When sending a message to an endpoint in a list fails, the Routing Service traces the resulting exception data and attaches the exception details as a message property named **Exceptions**.</span></span> <span data-ttu-id="6759f-209">Cela conserve les données d'exception et autorise un accès utilisateur par programme via un inspecteur de message.</span><span class="sxs-lookup"><span data-stu-id="6759f-209">This preserves the exception data and allows a user programmatic access through a message inspector.</span></span>  <span data-ttu-id="6759f-210">Les données d'exception sont stockées par message dans un dictionnaire qui mappe le nom du point de terminaison aux détails de l'exception rencontrée lors de la tentative d'envoi d'un message à ce point.</span><span class="sxs-lookup"><span data-stu-id="6759f-210">The exception data is stored per message in a dictionary that maps the endpoint name to the exception details encountered when trying to send a message to it.</span></span>

### <a name="backup-endpoints"></a><span data-ttu-id="6759f-211">Points de terminaison de sauvegarde</span><span class="sxs-lookup"><span data-stu-id="6759f-211">Backup Endpoints</span></span>

<span data-ttu-id="6759f-212">Chaque entrée de filtre dans la table de filtres peut éventuellement spécifier une liste de points de terminaison de sauvegarde, utilisés en cas de défaillance de la transmission lors de l'envoi au point de terminaison primaire.</span><span class="sxs-lookup"><span data-stu-id="6759f-212">Each filter entry within the filter table can optionally specify a list of backup endpoints, which are used in the event of a transmission failure when sending to the primary endpoint.</span></span> <span data-ttu-id="6759f-213">Si une telle défaillance se produit, le service de routage essaie de transmettre le message à la première entrée de la liste des points de terminaison de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="6759f-213">If such a failure occurs, the Routing Service attempts to transmit the message to the first entry in the backup endpoint list.</span></span> <span data-ttu-id="6759f-214">Si cette tentative d'envoi rencontre également un échec de transmission, il essaie avec le point de terminaison de sauvegarde suivant sur la liste.</span><span class="sxs-lookup"><span data-stu-id="6759f-214">If this send attempt also encounters a transmission failure, the next endpoint in the backup list is tried.</span></span> <span data-ttu-id="6759f-215">Le service de routage continue à envoyer le message à chaque point de terminaison de la liste jusqu'à ce que le message soit correctement reçu, que tous les points de terminaison aient retourné un échec de transmission, ou qu'un point de terminaison retourne un autre échec que celui de la transmission.</span><span class="sxs-lookup"><span data-stu-id="6759f-215">The Routing Service continues sending the message to each endpoint in the list until the message is successfully received, all endpoints return a transmission failure, or a non-transmission failure is returned by an endpoint.</span></span>

<span data-ttu-id="6759f-216">Les exemples suivants configurent le service de routage de manière à utiliser une liste de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="6759f-216">The following examples configure the Routing Service to use a backup list.</span></span>

```xml
<routing>
  <filters>
    <!-- Create a MatchAll filter that catches all messages -->
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
    <!-- Add an endpoint list that contains the backup destinations -->
    <backupList name="backupEndpointList">
      <add endpointName="realDestination" />
      <add endpointName="backupDestination" />
    </backupList>
  </backupLists>
</routing>
```

```csharp
//create the endpoint list that contains the service endpoints we want to route to
List<ServiceEndpoint> backupList = new List<ServiceEndpoint>();
//add the endpoints in the order that the Routing Service should contact them
//first add the endpoint that we know is down
//clearly, normally you wouldn't know that this endpoint was down by default
backupList.Add(fakeDestination);
//then add the real Destination endpoint
//the Routing Service attempts to send to this endpoint only if it
//encounters a TimeOutException or CommunicationException when sending
//to the previous endpoint in the list.
backupList.Add(realDestination);
//add the backupDestination endpoint
//the Routing Service attempts to send to this endpoint only if it
//encounters a TimeOutException or CommunicationsException when sending
//to the previous endpoints in the list
backupList.Add(backupDestination);
//create the default RoutingConfiguration option
RoutingConfiguration rc = new RoutingConfiguration();
//add a MatchAll filter to the Routing Configuration's filter table
//map it to the list of endpoints defined above
//when a message matches this filter, it is sent to the endpoints in the list in order
//if an endpoint is down or does not respond (which the first endpoint won't
//since the client does not exist), the Routing Service automatically moves the message
//to the next endpoint in the list and try again.
rc.FilterTable.Add(new MatchAllMessageFilter(), backupList);
```

### <a name="supported-error-patterns"></a><span data-ttu-id="6759f-217">Modèles d’erreurs pris en charge</span><span class="sxs-lookup"><span data-stu-id="6759f-217">Supported Error Patterns</span></span>

<span data-ttu-id="6759f-218">Le tableau suivant décrit les modèles compatibles avec l’utilisation des listes de point de terminaison de sauvegarde, avec une description des détails de gestion des erreurs pour chaque modèle spécifique.</span><span class="sxs-lookup"><span data-stu-id="6759f-218">The following table describes the patterns that are compatible with the use of backup endpoint lists, along with notes describing the details of error handling for specific patterns.</span></span>

|<span data-ttu-id="6759f-219">Motif</span><span class="sxs-lookup"><span data-stu-id="6759f-219">Pattern</span></span>|<span data-ttu-id="6759f-220">Session</span><span class="sxs-lookup"><span data-stu-id="6759f-220">Session</span></span>|<span data-ttu-id="6759f-221">Transaction</span><span class="sxs-lookup"><span data-stu-id="6759f-221">Transaction</span></span>|<span data-ttu-id="6759f-222">Contexte de réception</span><span class="sxs-lookup"><span data-stu-id="6759f-222">Receive Context</span></span>|<span data-ttu-id="6759f-223">Liste de sauvegarde prise en charge</span><span class="sxs-lookup"><span data-stu-id="6759f-223">Backup List Supported</span></span>|<span data-ttu-id="6759f-224">Remarques</span><span class="sxs-lookup"><span data-stu-id="6759f-224">Notes</span></span>|
|-------------|-------------|-----------------|---------------------|---------------------------|-----------|
|<span data-ttu-id="6759f-225">Unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="6759f-225">One-Way</span></span>||||<span data-ttu-id="6759f-226">Oui</span><span class="sxs-lookup"><span data-stu-id="6759f-226">Yes</span></span>|<span data-ttu-id="6759f-227">Tente de renvoyer le message sur un point de terminaison de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="6759f-227">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="6759f-228">Si ce message est en mode multidiffusion, seul le message sur le canal en échec est déplacé vers sa destination de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="6759f-228">If this message is being multicast, only the message on the failed channel is moved to its backup destination.</span></span>|
|<span data-ttu-id="6759f-229">Unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="6759f-229">One-Way</span></span>||<span data-ttu-id="6759f-230">✔️</span><span class="sxs-lookup"><span data-stu-id="6759f-230">✔️</span></span>||<span data-ttu-id="6759f-231">Non</span><span class="sxs-lookup"><span data-stu-id="6759f-231">No</span></span>|<span data-ttu-id="6759f-232">Une exception est levée et la transaction est restaurée.</span><span class="sxs-lookup"><span data-stu-id="6759f-232">An exception is thrown and the transaction is rolled back.</span></span>|
|<span data-ttu-id="6759f-233">Unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="6759f-233">One-Way</span></span>|||<span data-ttu-id="6759f-234">✔️</span><span class="sxs-lookup"><span data-stu-id="6759f-234">✔️</span></span>|<span data-ttu-id="6759f-235">Oui</span><span class="sxs-lookup"><span data-stu-id="6759f-235">Yes</span></span>|<span data-ttu-id="6759f-236">Tente de renvoyer le message sur un point de terminaison de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="6759f-236">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="6759f-237">Une fois le message correctement reçu, effectuez tous les contextes de réception.</span><span class="sxs-lookup"><span data-stu-id="6759f-237">After the message is successfully received, complete all receive contexts.</span></span> <span data-ttu-id="6759f-238">Si le message n'a pas été correctement reçu par un point de terminaison, n'effectuez pas le contexte de réception.</span><span class="sxs-lookup"><span data-stu-id="6759f-238">If the message is not successfully received by any endpoint, do not complete the receive context.</span></span><br /><br /> <span data-ttu-id="6759f-239">Lorsque ce message est envoyé en mode multidiffusion, le contexte de réception n'est effectué que si le message a été correctement reçu par au moins un point de terminaison (primaire ou de sauvegarde).</span><span class="sxs-lookup"><span data-stu-id="6759f-239">When this message is being multicast, the receive context is only completed if the message is successfully received by at least one endpoint (primary or backup).</span></span> <span data-ttu-id="6759f-240">Si aucun des points de terminaison situés sur les chemins d’accès de multidiffusion ne reçoit correctement le message, n’effectuez pas le contexte de réception.</span><span class="sxs-lookup"><span data-stu-id="6759f-240">If none of the endpoints in any of the multicast paths successfully receive the message, do not complete the receive context.</span></span>|
|<span data-ttu-id="6759f-241">Unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="6759f-241">One-Way</span></span>||<span data-ttu-id="6759f-242">✔️</span><span class="sxs-lookup"><span data-stu-id="6759f-242">✔️</span></span>|<span data-ttu-id="6759f-243">✔️</span><span class="sxs-lookup"><span data-stu-id="6759f-243">✔️</span></span>|<span data-ttu-id="6759f-244">Oui</span><span class="sxs-lookup"><span data-stu-id="6759f-244">Yes</span></span>|<span data-ttu-id="6759f-245">Abandonnez la transaction précédente, créez une nouvelle transaction et renvoyez tous les messages.</span><span class="sxs-lookup"><span data-stu-id="6759f-245">Abort the previous transaction, create a new transaction, and resend all messages.</span></span> <span data-ttu-id="6759f-246">Les messages qui ont rencontré une erreur sont transmis à une destination de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="6759f-246">Messages that encountered an error are transmitted to a backup destination.</span></span><br /><br /> <span data-ttu-id="6759f-247">Une fois créée une transaction dont toutes les transmissions ont réussi, effectuez les contextes de réception et validez la transaction.</span><span class="sxs-lookup"><span data-stu-id="6759f-247">After a transaction has been created in which all transmissions succeed, complete the receive contexts and commit the transaction.</span></span>|
|<span data-ttu-id="6759f-248">Unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="6759f-248">One-Way</span></span>|<span data-ttu-id="6759f-249">✔️</span><span class="sxs-lookup"><span data-stu-id="6759f-249">✔️</span></span>|||<span data-ttu-id="6759f-250">Oui</span><span class="sxs-lookup"><span data-stu-id="6759f-250">Yes</span></span>|<span data-ttu-id="6759f-251">Tente de renvoyer le message sur un point de terminaison de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="6759f-251">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="6759f-252">Dans un scénario de multidiffusion, seuls les messages qui se trouvent dans une session ayant rencontré une erreur ou dont la fin de session a échoué sont renvoyés aux destinations de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="6759f-252">In a multicast scenario only the messages in a session that encountered an error or in a session whose session close failed are resent to backup destinations.</span></span>|
|<span data-ttu-id="6759f-253">Unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="6759f-253">One-Way</span></span>|<span data-ttu-id="6759f-254">✔️</span><span class="sxs-lookup"><span data-stu-id="6759f-254">✔️</span></span>|<span data-ttu-id="6759f-255">✔️</span><span class="sxs-lookup"><span data-stu-id="6759f-255">✔️</span></span>||<span data-ttu-id="6759f-256">Non</span><span class="sxs-lookup"><span data-stu-id="6759f-256">No</span></span>|<span data-ttu-id="6759f-257">Une exception est levée et la transaction est restaurée.</span><span class="sxs-lookup"><span data-stu-id="6759f-257">An exception is thrown and the transaction is rolled back.</span></span>|
|<span data-ttu-id="6759f-258">Unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="6759f-258">One-Way</span></span>|<span data-ttu-id="6759f-259">✔️</span><span class="sxs-lookup"><span data-stu-id="6759f-259">✔️</span></span>||<span data-ttu-id="6759f-260">✔️</span><span class="sxs-lookup"><span data-stu-id="6759f-260">✔️</span></span>|<span data-ttu-id="6759f-261">Oui</span><span class="sxs-lookup"><span data-stu-id="6759f-261">Yes</span></span>|<span data-ttu-id="6759f-262">Tente de renvoyer le message sur un point de terminaison de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="6759f-262">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="6759f-263">Une fois tous les messages envoyés sans erreur, la session indique qu'il n'y a plus de messages, le service de routage ferme correctement tous les canaux de session sortante, tous les contextes de réception sont effectués et le canal de session entrante est fermé.</span><span class="sxs-lookup"><span data-stu-id="6759f-263">After all message sends complete without error, the session indicates no more messages and the Routing Service successfully closes all outbound session channel(s), all receive contexts are completed, and the inbound session channel is closed.</span></span>|
|<span data-ttu-id="6759f-264">Unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="6759f-264">One-Way</span></span>|<span data-ttu-id="6759f-265">✔️</span><span class="sxs-lookup"><span data-stu-id="6759f-265">✔️</span></span>|<span data-ttu-id="6759f-266">✔️</span><span class="sxs-lookup"><span data-stu-id="6759f-266">✔️</span></span>|<span data-ttu-id="6759f-267">✔️</span><span class="sxs-lookup"><span data-stu-id="6759f-267">✔️</span></span>|<span data-ttu-id="6759f-268">Oui</span><span class="sxs-lookup"><span data-stu-id="6759f-268">Yes</span></span>|<span data-ttu-id="6759f-269">Abandonnez la transaction actuelle et créez en une nouvelle.</span><span class="sxs-lookup"><span data-stu-id="6759f-269">Abort the current transaction and create a new one.</span></span> <span data-ttu-id="6759f-270">Renvoyez tous les messages précédents de la session.</span><span class="sxs-lookup"><span data-stu-id="6759f-270">Resend all previous messages in the session.</span></span> <span data-ttu-id="6759f-271">Une fois créée une transaction dont tous les messages ont été correctement envoyés et lorsque la session indique qu'il n'y a plus de messages, tous les canaux de session sortante sont fermés, les contextes de réception sont tous effectués avec la transaction, le canal de session entrante est fermé et la transaction est validée.</span><span class="sxs-lookup"><span data-stu-id="6759f-271">After a transaction has been created in which all messages have been successfully sent and the session indicates no more messages, all the outbound session channels are closed, receive contexts are all completed with the transaction, the inbound session channel is closed, and the transaction is committed.</span></span><br /><br /> <span data-ttu-id="6759f-272">Lorsque les sessions sont en mode multidiffusion, les messages qui n'ont eu aucune erreur sont renvoyés à la même destination qu'avant, et les messages qui ont rencontré une erreur sont envoyés aux destinations de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="6759f-272">When the sessions are being multicast the messages that had no error are resent to the same destination as before, and messages that encountered an error are sent to backup destinations.</span></span>|
|<span data-ttu-id="6759f-273">Bidirectionnel</span><span class="sxs-lookup"><span data-stu-id="6759f-273">Two-Way</span></span>||||<span data-ttu-id="6759f-274">Oui</span><span class="sxs-lookup"><span data-stu-id="6759f-274">Yes</span></span>|<span data-ttu-id="6759f-275">Envoyez à une destination de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="6759f-275">Send to a backup destination.</span></span>  <span data-ttu-id="6759f-276">Après qu'un canal a retourné un message de réponse, retournez la réponse au client d'origine.</span><span class="sxs-lookup"><span data-stu-id="6759f-276">After a channel returns a response message, return the response to the original client.</span></span>|
|<span data-ttu-id="6759f-277">Bidirectionnel</span><span class="sxs-lookup"><span data-stu-id="6759f-277">Two-Way</span></span>|<span data-ttu-id="6759f-278">✔️</span><span class="sxs-lookup"><span data-stu-id="6759f-278">✔️</span></span>|||<span data-ttu-id="6759f-279">Oui</span><span class="sxs-lookup"><span data-stu-id="6759f-279">Yes</span></span>|<span data-ttu-id="6759f-280">Envoyez tous les messages sur le canal à une destination de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="6759f-280">Send all messages on the channel to a backup destination.</span></span>  <span data-ttu-id="6759f-281">Après qu'un canal a retourné un message de réponse, retournez la réponse au client d'origine.</span><span class="sxs-lookup"><span data-stu-id="6759f-281">After a channel returns a response message, return the response to the original client.</span></span>|
|<span data-ttu-id="6759f-282">Bidirectionnel</span><span class="sxs-lookup"><span data-stu-id="6759f-282">Two-Way</span></span>||<span data-ttu-id="6759f-283">✔️</span><span class="sxs-lookup"><span data-stu-id="6759f-283">✔️</span></span>||<span data-ttu-id="6759f-284">Non</span><span class="sxs-lookup"><span data-stu-id="6759f-284">No</span></span>|<span data-ttu-id="6759f-285">Une exception est levée et la transaction est restaurée.</span><span class="sxs-lookup"><span data-stu-id="6759f-285">An exception is thrown and the transaction is rolled back.</span></span>|
|<span data-ttu-id="6759f-286">Bidirectionnel</span><span class="sxs-lookup"><span data-stu-id="6759f-286">Two-Way</span></span>|<span data-ttu-id="6759f-287">✔️</span><span class="sxs-lookup"><span data-stu-id="6759f-287">✔️</span></span>|<span data-ttu-id="6759f-288">✔️</span><span class="sxs-lookup"><span data-stu-id="6759f-288">✔️</span></span>||<span data-ttu-id="6759f-289">Non</span><span class="sxs-lookup"><span data-stu-id="6759f-289">No</span></span>|<span data-ttu-id="6759f-290">Une exception est levée et la transaction est restaurée.</span><span class="sxs-lookup"><span data-stu-id="6759f-290">An exception is thrown and the transaction is rolled back.</span></span>|
|<span data-ttu-id="6759f-291">Duplex</span><span class="sxs-lookup"><span data-stu-id="6759f-291">Duplex</span></span>||||<span data-ttu-id="6759f-292">Non</span><span class="sxs-lookup"><span data-stu-id="6759f-292">No</span></span>|<span data-ttu-id="6759f-293">La communication duplex sans session n'est pas prise en charge actuellement.</span><span class="sxs-lookup"><span data-stu-id="6759f-293">Non-session duplex communication is not currently supported.</span></span>|
|<span data-ttu-id="6759f-294">Duplex</span><span class="sxs-lookup"><span data-stu-id="6759f-294">Duplex</span></span>|<span data-ttu-id="6759f-295">✔️</span><span class="sxs-lookup"><span data-stu-id="6759f-295">✔️</span></span>|||<span data-ttu-id="6759f-296">Oui</span><span class="sxs-lookup"><span data-stu-id="6759f-296">Yes</span></span>|<span data-ttu-id="6759f-297">Envoyez à une destination de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="6759f-297">Send to a backup destination.</span></span>|

## <a name="hosting"></a><span data-ttu-id="6759f-298">Hébergement</span><span class="sxs-lookup"><span data-stu-id="6759f-298">Hosting</span></span>

<span data-ttu-id="6759f-299">Le service de routage étant implémenté en tant que service WCF, il doit être soit auto-hébergé dans une application, soit hébergé par les services IIS ou WAS.</span><span class="sxs-lookup"><span data-stu-id="6759f-299">Because the Routing Service is implemented as a WCF service, it must be either self-hosted within an application or hosted by IIS or WAS.</span></span> <span data-ttu-id="6759f-300">Il est préférable que le service de routage soit hébergé dans les services IIS ou WAS ou dans une application de service Windows afin de tirer parti des fonctionnalités de démarrage automatique et de gestion du cycle de vie, disponibles dans ces environnements d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="6759f-300">It is recommended that the Routing Service be hosted in either IIS, WAS, or a Windows Service application to take advantage of the automatic start and life-cycle management features available in these hosting environments.</span></span>

<span data-ttu-id="6759f-301">L'exemple suivant montre l'hébergement du service de routage dans une application.</span><span class="sxs-lookup"><span data-stu-id="6759f-301">The following example demonstrates hosting the Routing Service in an application.</span></span>

```csharp
using (ServiceHost serviceHost =
                new ServiceHost(typeof(RoutingService)))
```

<span data-ttu-id="6759f-302">Pour héberger le service de routage dans les services IIS ou WAS, vous devez créer un fichier de service (.svc) ou utiliser une activation du service basée sur la configuration.</span><span class="sxs-lookup"><span data-stu-id="6759f-302">To host the Routing Service within IIS or WAS, you must either create a service file (.svc) or use configuration-based activation of the service.</span></span> <span data-ttu-id="6759f-303">Lorsque vous utilisez un fichier de service, vous devez spécifier un objet <xref:System.ServiceModel.Routing.RoutingService> à l'aide du paramètre du service.</span><span class="sxs-lookup"><span data-stu-id="6759f-303">When using a service file, you must specify the <xref:System.ServiceModel.Routing.RoutingService> using the Service parameter.</span></span> <span data-ttu-id="6759f-304">L'exemple suivant contient un exemple de fichier de service qui peut être utilisé pour héberger le service de routage avec les services IIS ou WAS.</span><span class="sxs-lookup"><span data-stu-id="6759f-304">The following example contains a sample service file that can be used to host the Routing Service with IIS or WAS.</span></span>

```aspx-csharp
<%@ ServiceHost Language="C#" Debug="true" Service="System.ServiceModel.Routing.RoutingService,
     System.ServiceModel.Routing, version=4.0.0.0, Culture=neutral,
     PublicKeyToken=31bf3856ad364e35" %>
```

## <a name="routing-service-and-impersonation"></a><span data-ttu-id="6759f-305">Service de routage et emprunt d'identité</span><span class="sxs-lookup"><span data-stu-id="6759f-305">Routing Service and Impersonation</span></span>

<span data-ttu-id="6759f-306">Le service de routage WCF peut être utilisé avec l'emprunt d'identité pour l'envoi et la réception de messages.</span><span class="sxs-lookup"><span data-stu-id="6759f-306">The WCF Routing Service can be used with impersonation for both sending and receiving messages.</span></span> <span data-ttu-id="6759f-307">Toutes les contraintes d'emprunt d'identité habituelles de Windows s'appliquent.</span><span class="sxs-lookup"><span data-stu-id="6759f-307">All of the usual Windows constraints of impersonation apply.</span></span> <span data-ttu-id="6759f-308">Si vous devez configurer des autorisations de service ou de compte pour utiliser l'emprunt d'identité lors de l'écriture de votre service, vous devez effectuer ces mêmes étapes pour utiliser l'emprunt d'identité avec le service de routage.</span><span class="sxs-lookup"><span data-stu-id="6759f-308">If you would have needed to set up service or account permissions to use impersonation when writing your own service, then you’ll have to do those same steps to use impersonation with the routing service.</span></span> <span data-ttu-id="6759f-309">Pour plus d’informations, consultez [délégation et emprunt d’identité](delegation-and-impersonation-with-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="6759f-309">For more information, see [Delegation and Impersonation](delegation-and-impersonation-with-wcf.md).</span></span>

<span data-ttu-id="6759f-310">L'emprunt d'identité avec le service de routage requiert l'utilisation de l'emprunt d'identité ASP.NET en mode de compatibilité ASP.NET ou l'utilisation d'informations d'identification Windows qui ont été configurées pour permettre l'emprunt d'identité.</span><span class="sxs-lookup"><span data-stu-id="6759f-310">Impersonation with the routing service requires either the use of ASP.NET impersonation while in ASP.NET compatibility mode or the use of Windows credentials that have been configured to allow impersonation.</span></span> <span data-ttu-id="6759f-311">Pour plus d’informations sur le mode de compatibilité ASP.NET, consultez [services WCF et ASP.net](wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="6759f-311">For more information about ASP.NET compatibility mode, see [WCF Services and ASP.NET](wcf-services-and-aspnet.md).</span></span>

> [!WARNING]
> <span data-ttu-id="6759f-312">Le service de routage WCF ne prend pas en charge l'emprunt d'identité avec l'authentification de base.</span><span class="sxs-lookup"><span data-stu-id="6759f-312">The WCF Routing Service does not support impersonation with basic authentication.</span></span>

<span data-ttu-id="6759f-313">Pour utiliser l'emprunt d'identité ASP.NET avec le service de routage, activez le mode de compatibilité ASP.NET sur l'environnement d'hébergement de service.</span><span class="sxs-lookup"><span data-stu-id="6759f-313">To use ASP.NET impersonation with the routing service, enable ASP.NET compatibility mode on the service hosting environment.</span></span> <span data-ttu-id="6759f-314">Le service de routage a déjà été marqué comme autorisant le mode de compatibilité ASP.NET et l'emprunt d'identité est automatiquement activé.</span><span class="sxs-lookup"><span data-stu-id="6759f-314">The routing service has already been marked as allowing ASP.NET compatibility mode and impersonation will automatically be enabled.</span></span> <span data-ttu-id="6759f-315">L'emprunt d'identité est la seule utilisation prise en charge de l'intégration d'ASP.NET au service de routage.</span><span class="sxs-lookup"><span data-stu-id="6759f-315">Impersonation is the only supported use of ASP.NET integration with the routing service.</span></span>

<span data-ttu-id="6759f-316">Pour utiliser l'emprunt d'identité des informations d'identification Windows avec le service de routage, vous devez configurer les informations d'identification et le service.</span><span class="sxs-lookup"><span data-stu-id="6759f-316">To use Windows credential impersonation with the routing service you need to configure both the credentials and the service.</span></span> <span data-ttu-id="6759f-317">L'objet d'informations d'identification du client (<xref:System.ServiceModel.Security.WindowsClientCredential>, accessible à partir de <xref:System.ServiceModel.ChannelFactory>) définit une propriété <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> qui doit être définie pour permettre l'emprunt d'identité.</span><span class="sxs-lookup"><span data-stu-id="6759f-317">The client credentials object (<xref:System.ServiceModel.Security.WindowsClientCredential>, accessable from the <xref:System.ServiceModel.ChannelFactory>) defines an <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> property that must be set to permit impersonation.</span></span> <span data-ttu-id="6759f-318">Enfin, dans le service vous devez configurer le comportement <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> pour affecter la valeur `ImpersonateCallerForAllOperations` à `true`.</span><span class="sxs-lookup"><span data-stu-id="6759f-318">Finally, on the service you need to configure the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> behavior to set `ImpersonateCallerForAllOperations` to `true`.</span></span> <span data-ttu-id="6759f-319">Le service de routage utilise cet indicateur pour déterminer s'il faut créer les clients pour transférer des messages lorsque l'emprunt d'identité est activé.</span><span class="sxs-lookup"><span data-stu-id="6759f-319">The routing service uses this flag to decide whether to create the clients for forwarding messages with impersonation enabled.</span></span>

## <a name="see-also"></a><span data-ttu-id="6759f-320">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6759f-320">See also</span></span>

- [<span data-ttu-id="6759f-321">Filtres de message</span><span class="sxs-lookup"><span data-stu-id="6759f-321">Message Filters</span></span>](message-filters.md)
- [<span data-ttu-id="6759f-322">Contrats de routage</span><span class="sxs-lookup"><span data-stu-id="6759f-322">Routing Contracts</span></span>](routing-contracts.md)
- [<span data-ttu-id="6759f-323">Choix d’un filtre</span><span class="sxs-lookup"><span data-stu-id="6759f-323">Choosing a Filter</span></span>](choosing-a-filter.md)
