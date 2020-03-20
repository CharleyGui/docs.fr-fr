---
title: 'Procédure : utiliser des filtres'
ms.date: 03/30/2017
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
ms.openlocfilehash: f99c2af623dacac3ebe46422815a7f42e2a4df2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184814"
---
# <a name="how-to-use-filters"></a><span data-ttu-id="4a54c-102">Procédure : utiliser des filtres</span><span class="sxs-lookup"><span data-stu-id="4a54c-102">How To: Use Filters</span></span>
<span data-ttu-id="4a54c-103">Cette rubrique décrit les étapes de base requises pour créer une configuration de routage qui utilise plusieurs filtres.</span><span class="sxs-lookup"><span data-stu-id="4a54c-103">This topic outlines the basic steps required to create a routing configuration that uses multiple filters.</span></span> <span data-ttu-id="4a54c-104">Dans cet exemple, les messages sont routés vers deux implémentations d'un service de calculatrice, regularCalc et roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="4a54c-104">In this example, messages are routed to two implementations of a calculator service, regularCalc and roundingCalc.</span></span> <span data-ttu-id="4a54c-105">Les deux implémentations prennent en charge les mêmes opérations ; toutefois, l'un des services arrondit tous les calculs à la valeur entière la plus proche avant de les retourner.</span><span class="sxs-lookup"><span data-stu-id="4a54c-105">Both implementations support the same operations; however one service rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="4a54c-106">Une application cliente doit être en mesure d'indiquer s'il faut utiliser la version arrondie de ce service ; si aucune préférence de service n'est exprimée, le message est équilibré entre les deux services.</span><span class="sxs-lookup"><span data-stu-id="4a54c-106">A client application must be able to indicate whether to  use the rounding version of the service; if no service preference is expressed then the message is load balanced between the two services.</span></span> <span data-ttu-id="4a54c-107">Les opérations exposées par les deux services sont :</span><span class="sxs-lookup"><span data-stu-id="4a54c-107">The operations exposed by both services are:</span></span>  
  
- <span data-ttu-id="4a54c-108">Ajouter</span><span class="sxs-lookup"><span data-stu-id="4a54c-108">Add</span></span>  
  
- <span data-ttu-id="4a54c-109">Soustraire</span><span class="sxs-lookup"><span data-stu-id="4a54c-109">Subtract</span></span>  
  
- <span data-ttu-id="4a54c-110">Multiplier</span><span class="sxs-lookup"><span data-stu-id="4a54c-110">Multiply</span></span>  
  
- <span data-ttu-id="4a54c-111">Diviser</span><span class="sxs-lookup"><span data-stu-id="4a54c-111">Divide</span></span>  
  
 <span data-ttu-id="4a54c-112">Étant donné que les deux services implémentent les mêmes opérations, vous ne pouvez pas utiliser le filtre Action, car l'action spécifiée dans le message ne sera pas unique.</span><span class="sxs-lookup"><span data-stu-id="4a54c-112">Because both services implement the same operations, you cannot use the Action filter, because the action specified in the message will not be unique.</span></span> <span data-ttu-id="4a54c-113">Vous devez plutôt effectuer un travail supplémentaire pour vérifier que les messages sont routés vers les points de terminaison appropriés.</span><span class="sxs-lookup"><span data-stu-id="4a54c-113">Instead you must do additional work to ensure that the messages are routed to the appropriate endpoints.</span></span>  
  
### <a name="determine-unique-data"></a><span data-ttu-id="4a54c-114">Déterminer des données uniques</span><span class="sxs-lookup"><span data-stu-id="4a54c-114">Determine Unique Data</span></span>  
  
1. <span data-ttu-id="4a54c-115">Comme les deux implémentations de service gèrent les mêmes opérations et sont pour l'essentiel identiques en dehors des données qu'elles retournent, les données de base contenues dans les messages envoyés à partir d'applications clientes ne sont pas assez uniques pour vous permettre de déterminer comment router la demande.</span><span class="sxs-lookup"><span data-stu-id="4a54c-115">Because both service implementations handle the same operations, and are essentially identical other than the data that they return, the base data contained in messages sent from client applications is not unique enough to allow you to determine how to route the request.</span></span> <span data-ttu-id="4a54c-116">Mais si l'application cliente ajoute une valeur d'en-tête unique au message, vous pouvez utiliser cette valeur pour déterminer comment le message doit être routé.</span><span class="sxs-lookup"><span data-stu-id="4a54c-116">But if the client application adds a unique header value to the message, then you can use this value to determine how the message should be routed.</span></span>  
  
     <span data-ttu-id="4a54c-117">Pour cet exemple, si l'application cliente a besoin que le message soit traité par la calculatrice d'arrondi, elle ajoute un en-tête personnalisé à l'aide du code suivant :</span><span class="sxs-lookup"><span data-stu-id="4a54c-117">For this example, if the client application needs the message to be processed by the rounding calculator, it adds a custom header by using the following code:</span></span>  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     <span data-ttu-id="4a54c-118">Vous pouvez maintenant utiliser le filtre XPath pour vérifier la présence de cet en-tête dans les messages et router ceux qui le contiennent vers le service roundCalc.</span><span class="sxs-lookup"><span data-stu-id="4a54c-118">You can now use the XPath filter to inspect messages for this header, and route messages containing the header to the roundCalc service.</span></span>  
  
2. <span data-ttu-id="4a54c-119">En outre, le service de routage expose deux points de terminaison de service virtuels qui peuvent être utilisés avec les filtres EndpointName, EndpointAddress ou PrefixEndpointAddress, pour router de manière unique les messages entrants vers une implémentation de calculatrice spécifique, en fonction du point de terminaison auquel l'application cliente soumet la demande.</span><span class="sxs-lookup"><span data-stu-id="4a54c-119">Additionally the Routing Service exposes two virtual service endpoints that can be used with the EndpointName, EndpointAddress, or PrefixEndpointAddress filters to uniquely route incoming messages to a specific calculator implementation based on the endpoint to which the client application submits the request.</span></span>  
  
### <a name="define-endpoints"></a><span data-ttu-id="4a54c-120">Définir des points de terminaison</span><span class="sxs-lookup"><span data-stu-id="4a54c-120">Define Endpoints</span></span>  
  
1. <span data-ttu-id="4a54c-121">Lorsque vous définissez les points de terminaison utilisés par le service de routage, vous devez d'abord déterminer la forme du canal utilisé par vos clients et vos services.</span><span class="sxs-lookup"><span data-stu-id="4a54c-121">When defining the endpoints used by the Routing Service, you should first determine the shape of the channel used by your clients and services.</span></span> <span data-ttu-id="4a54c-122">Dans ce scénario, les deux services de destination utilisent un modèle demande-réponse, donc la forme <xref:System.ServiceModel.Routing.IRequestReplyRouter> est utilisée.</span><span class="sxs-lookup"><span data-stu-id="4a54c-122">In this scenario both the destination services use a request-reply pattern, so the <xref:System.ServiceModel.Routing.IRequestReplyRouter> is used.</span></span> <span data-ttu-id="4a54c-123">L'exemple suivant définit les points de terminaison de service exposés par le service de routage.</span><span class="sxs-lookup"><span data-stu-id="4a54c-123">The following example defines the service endpoints exposed by the Routing Service.</span></span>  
  
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
            <!--first create the general router endpoint-->  
            <endpoint address="general"  
                      binding="wsHttpBinding"  
                      name="routerEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--create a virtual endpoint for the regular calculator service-->  
            <endpoint address="regular/calculator"  
                      binding="wsHttpBinding"  
                      name="calculatorEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--now create a virtual endpoint for the rounding calculator-->  
            <endpoint address="rounding/calculator"  
                      binding="wsHttpBinding"  
                      name="roundingEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
          </service>  
    </services>  
    ```  
  
     <span data-ttu-id="4a54c-124">Avec cette configuration, le service de routage expose trois points de terminaison distincts.</span><span class="sxs-lookup"><span data-stu-id="4a54c-124">With this configuration, the Routing Service exposes three separate endpoints.</span></span> <span data-ttu-id="4a54c-125">En fonction des choix d'exécution, l'application cliente envoie des messages à l'une de ces adresses.</span><span class="sxs-lookup"><span data-stu-id="4a54c-125">Depending on run-time choices, the client application sends messages to one of these addresses.</span></span> <span data-ttu-id="4a54c-126">Les messages arrivant à l’un des critères de service « virtuels » (« arrondissement/calculatrice » ou « régulier/calculatrice ») sont transmis à la mise en œuvre correspondante de la calculatrice.</span><span class="sxs-lookup"><span data-stu-id="4a54c-126">Messages arriving at one of the "virtual" service endpoints ("rounding/calculator" or "regular/calculator") are forwarded to the corresponding calculator implementation.</span></span> <span data-ttu-id="4a54c-127">Si l'application cliente n'envoie pas la demande à un point de terminaison particulier, le message est adressé au point de terminaison général.</span><span class="sxs-lookup"><span data-stu-id="4a54c-127">If the client application doesn’t send the request to a particular endpoint, the message is addressed to the general endpoint.</span></span> <span data-ttu-id="4a54c-128">Indépendamment du point de terminaison retenu, l'application cliente peut choisir également d'inclure l'en-tête personnalisé pour indiquer que le message doit être envoyé à l'implémentation de la calculatrice d'arrondi.</span><span class="sxs-lookup"><span data-stu-id="4a54c-128">Regardless of the endpoint chosen, the client application may also choose to include the custom header to indicate that the message should be forwarded to the rounding calculator implementation.</span></span>  
  
2. <span data-ttu-id="4a54c-129">L'exemple suivant définit les points de terminaison clients (destination) vers lesquels le service de routage route des messages.</span><span class="sxs-lookup"><span data-stu-id="4a54c-129">The following example defines the client (destination) endpoints that the Routing Service routes messages to.</span></span>  
  
    ```xml  
    <client>  
          <endpoint name="regularCalcEndpoint"  
                    address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
  
          <endpoint name="roundingCalcEndpoint"  
                    address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
    </client>  
    ```  
  
     <span data-ttu-id="4a54c-130">Ces points de terminaison sont utilisés dans la table de filtres pour indiquer le point de terminaison de destination auquel le message est envoyé lorsqu'il correspond à un filtre spécifique.</span><span class="sxs-lookup"><span data-stu-id="4a54c-130">These endpoints are used in the filter table to indicate the destination endpoint the message is sent to when it matches a specific filter.</span></span>  
  
### <a name="define-filters"></a><span data-ttu-id="4a54c-131">Définir les filtres</span><span class="sxs-lookup"><span data-stu-id="4a54c-131">Define Filters</span></span>  
  
1. <span data-ttu-id="4a54c-132">Pour acheminer les messages en fonction de l’en-tête personnalisé "RoundingCalculator" que l’application client ajoute au message, définissez un filtre qui utilise une requête XPath pour vérifier la présence de cet en-tête.</span><span class="sxs-lookup"><span data-stu-id="4a54c-132">To route messages based on the "RoundingCalculator" custom header that the client application adds to the message, define a filter that uses an XPath query to check for the presence of this header.</span></span> <span data-ttu-id="4a54c-133">Parce que cet en-tête est défini en utilisant un espace de nom personnalisé, ajoutez également une entrée namespace qui définit un préfixe personnalisé namespace de "custom" qui est utilisé dans la requête XPath.</span><span class="sxs-lookup"><span data-stu-id="4a54c-133">Because this header is defined by using a custom namespace, also add a namespace entry that defines a custom namespace prefix of "custom" that is used in the XPath query.</span></span> <span data-ttu-id="4a54c-134">L'exemple suivant définit la section de routage nécessaire, la table d'espace de noms et le filtre XPath.</span><span class="sxs-lookup"><span data-stu-id="4a54c-134">The following example defines the necessary routing section, namespace table, and XPath filter.</span></span>  
  
    ```xml  
    <routing>  
          <!-- use the namespace table element to define a prefix for our custom namespace-->  
          <namespaceTable>  
            <add prefix="custom" namespace="http://my.custom.namespace/"/>  
          </namespaceTable>  
          <filters>  
            <!--define the different message filters-->  
            <!--define an xpath message filter to look for the custom header coming from the client-->  
            <filter name="XPathFilter" filterType="XPath"
                    filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
          </filters>  
    </routing>  
    ```  
  
     <span data-ttu-id="4a54c-135">Ce **MessageFilter** recherche un en-tête RoundingCalculator dans le message qui contient une valeur de "arrondi".</span><span class="sxs-lookup"><span data-stu-id="4a54c-135">This **MessageFilter** looks for a RoundingCalculator header in the message that contains a value of "rounding".</span></span> <span data-ttu-id="4a54c-136">Cet en-tête est défini par le client pour indiquer que le message doit être routé vers le service roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="4a54c-136">This header is set by the client to indicate that the message should be routed to the roundingCalc service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4a54c-137">Le préfixe s12 namespace est défini par défaut dans `http://www.w3.org/2003/05/soap-envelope`le tableau namespace, et représente l’espace nom .</span><span class="sxs-lookup"><span data-stu-id="4a54c-137">The s12 namespace prefix is defined by default in the namespace table, and represents the namespace `http://www.w3.org/2003/05/soap-envelope`.</span></span>
  
2. <span data-ttu-id="4a54c-138">Vous devez également définir des filtres qui recherchent des messages reçus sur les deux points de terminaison virtuels.</span><span class="sxs-lookup"><span data-stu-id="4a54c-138">You must also define filters that look for messages received on the two virtual endpoints.</span></span> <span data-ttu-id="4a54c-139">Le premier critère d’évaluation virtuel est le point de terminaison « régulier/calculateur ».</span><span class="sxs-lookup"><span data-stu-id="4a54c-139">The first virtual endpoint is the "regular/calculator" endpoint.</span></span> <span data-ttu-id="4a54c-140">Le client peut envoyer des demandes à ce point de terminaison pour indiquer que le message doit être routé vers le service regularCalc.</span><span class="sxs-lookup"><span data-stu-id="4a54c-140">The client can send requests to this endpoint to indicate that the message should be routed to the regularCalc service.</span></span> <span data-ttu-id="4a54c-141">La configuration suivante définit un filtre qui utilise l'objet <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> pour déterminer si le message est arrivé par un point de terminaison dont le nom est spécifié dans FilterData.</span><span class="sxs-lookup"><span data-stu-id="4a54c-141">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> to determine if the message arrived through an endpoint with the name specified in filterData.</span></span>  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     <span data-ttu-id="4a54c-142">Si un message est reçu par le point de terminaison `true`de service nommé « calculatorEndpoint », ce filtre évalue à .</span><span class="sxs-lookup"><span data-stu-id="4a54c-142">If a message is received by the service endpoint named "calculatorEndpoint", this filter evaluates to `true`.</span></span>  
  
3. <span data-ttu-id="4a54c-143">Ensuite, définissez un filtre qui recherche les messages envoyés à l'adresse du roundingEndpoint.</span><span class="sxs-lookup"><span data-stu-id="4a54c-143">Next, define a filter that looks for messages sent to the address of the roundingEndpoint.</span></span> <span data-ttu-id="4a54c-144">Le client peut envoyer des demandes à ce point de terminaison pour indiquer que le message doit être routé vers le service roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="4a54c-144">The client can send requests to this endpoint to indicate that the message should be routed to the roundingCalc service.</span></span> <span data-ttu-id="4a54c-145">La configuration suivante définit un <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> filtre qui utilise le pour déterminer si le message est arrivé au point de terminaison "arrondi/calculatrice".</span><span class="sxs-lookup"><span data-stu-id="4a54c-145">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> to determine if the message arrived at the "rounding/calculator" endpoint.</span></span>  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     <span data-ttu-id="4a54c-146">Si un message est reçu à `http://localhost/routingservice/router/rounding/` une adresse qui commence par alors ce filtre évalue à **vrai**.</span><span class="sxs-lookup"><span data-stu-id="4a54c-146">If a message is received at an address that begins with `http://localhost/routingservice/router/rounding/` then this filter evaluates to **true**.</span></span> <span data-ttu-id="4a54c-147">Étant donné que l’adresse `http://localhost/routingservice/router` de base utilisée par cette configuration est et que l’adresse spécifiée pour `http://localhost/routingservice/router/rounding/calculator`le point d’arrondissement est « arrondi/calculatrice », l’adresse complète utilisée pour communiquer avec ce point de terminaison est, qui correspond à ce filtre.</span><span class="sxs-lookup"><span data-stu-id="4a54c-147">Because the base address used by this configuration is `http://localhost/routingservice/router` and the address specified for the roundingEndpoint is "rounding/calculator", the full address used to communicate with this endpoint is `http://localhost/routingservice/router/rounding/calculator`, which matches this filter.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4a54c-148">Le filtre PrefixEndpointAddress n'évalue pas le nom d'hôte lorsqu'il effectue une correspondance, parce qu'il peut être fait référence à un hôte unique à l'aide de divers noms d'hôte qui tous peuvent constituer des moyens valides de faire référence à l'hôte à partir de l'application cliente.</span><span class="sxs-lookup"><span data-stu-id="4a54c-148">The PrefixEndpointAddress filter does not evaluate the host name when performing a match, because a single host can be referred to by using a variety of host names that may all be valid ways of referring to the host from the client application.</span></span> <span data-ttu-id="4a54c-149">Par exemple, tous les éléments suivants peuvent faire référence au même hôte :</span><span class="sxs-lookup"><span data-stu-id="4a54c-149">For example, all of the following may refer to the same host:</span></span>  
    >
    > - <span data-ttu-id="4a54c-150">localhost</span><span class="sxs-lookup"><span data-stu-id="4a54c-150">localhost</span></span>  
    > - <span data-ttu-id="4a54c-151">127.0.0.1</span><span class="sxs-lookup"><span data-stu-id="4a54c-151">127.0.0.1</span></span>  
    > - `www.contoso.com`  
    > - <span data-ttu-id="4a54c-152">ContosoWeb01</span><span class="sxs-lookup"><span data-stu-id="4a54c-152">ContosoWeb01</span></span>  
  
4. <span data-ttu-id="4a54c-153">Le filtre définitif doit prendre en charge le routage des messages qui arrivent au point de terminaison général sans en-tête personnalisé.</span><span class="sxs-lookup"><span data-stu-id="4a54c-153">The final filter must support the routing of messages that arrive at the general endpoint without the custom header.</span></span> <span data-ttu-id="4a54c-154">Pour ce scénario, les messages doivent alterner entre les services roundingCalc et regularCalc.</span><span class="sxs-lookup"><span data-stu-id="4a54c-154">For this scenario, the messages should alternate between the regularCalc and roundingCalc services.</span></span> <span data-ttu-id="4a54c-155">Pour prendre en charge le routage « round robin » de ces messages, utilisez un filtre personnalisé qui permet à une instance de filtre de correspondre à chaque message traité.</span><span class="sxs-lookup"><span data-stu-id="4a54c-155">To support the "round robin" routing of these messages,  use a custom filter that allows one filter instance to match for each message processed.</span></span>  <span data-ttu-id="4a54c-156">Les éléments suivants définissent deux instances d'un RoundRobinMessageFilter, qui sont regroupées pour indiquer qu'elles doivent alterner entre elles.</span><span class="sxs-lookup"><span data-stu-id="4a54c-156">The following defines two instances of a RoundRobinMessageFilter, which are grouped together to indicate that they should alternate between each other.</span></span>  
  
    ```xml  
    <!-- Set up the custom message filters.  In this example,   
         we'll use the example round robin message filter,   
         which alternates between the references-->  
    <filter name="RoundRobinFilter1" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    <filter name="RoundRobinFilter2" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    ```  
  
     <span data-ttu-id="4a54c-157">Au moment de l’exécution, ce type de filtre alterne entre toutes les instances de filtre définies de ce type qui sont configurées comme un même groupe dans une collection.</span><span class="sxs-lookup"><span data-stu-id="4a54c-157">During run time, this filter type alternates between all defined filter instances of this type that are configured as the same group into one collection.</span></span> <span data-ttu-id="4a54c-158">Cela provoque des messages traités par `true` ce `RoundRobinFilter1` `RoundRobinFilter2`filtre personnalisé à alterner entre le retour pour et .</span><span class="sxs-lookup"><span data-stu-id="4a54c-158">This causes messages processed by this custom filter to alternate between returning `true` for `RoundRobinFilter1` and `RoundRobinFilter2`.</span></span>  
  
### <a name="define-filter-tables"></a><span data-ttu-id="4a54c-159">Définir des tables de filtres</span><span class="sxs-lookup"><span data-stu-id="4a54c-159">Define Filter Tables</span></span>  
  
1. <span data-ttu-id="4a54c-160">Pour associer les filtres à des points de terminaison clients spécifiques, vous devez les placer dans une table de filtres.</span><span class="sxs-lookup"><span data-stu-id="4a54c-160">To associate the filters with specific client endpoints, you must place them within a filter table.</span></span> <span data-ttu-id="4a54c-161">Cet exemple de scénario utilise également des paramètres de priorité du filtre, qui sont facultatifs et vous permettent d'indiquer l'ordre dans lequel les filtres sont traités.</span><span class="sxs-lookup"><span data-stu-id="4a54c-161">This example scenario also uses filter priority settings, which is an optional setting that allows you to indicate the order in which filters are processed.</span></span> <span data-ttu-id="4a54c-162">Si aucune priorité de filtre n'est spécifiée, tous les filtres sont évalués simultanément.</span><span class="sxs-lookup"><span data-stu-id="4a54c-162">If no filter priority is specified, all filters are evaluated simultaneously.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4a54c-163">Si la spécification d'une priorité de filtre vous permet de contrôler l'ordre dans lequel les filtres sont traités, elle peut aussi nuire aux performances du service de routage.</span><span class="sxs-lookup"><span data-stu-id="4a54c-163">While specifying a filter priority allows you to control the order in which filters are processed, it can adversely affect the performance of the Routing Service.</span></span> <span data-ttu-id="4a54c-164">Si possible, construisez la logique de filtre de manière à ne pas être obligé de recourir aux priorités de filtre.</span><span class="sxs-lookup"><span data-stu-id="4a54c-164">When possible, construct filter logic so that the use of filter priorities is not required.</span></span>  
  
     <span data-ttu-id="4a54c-165">Ce qui suit définit la table de filtre et ajoute le "XPathFilter" défini plus tôt à la table avec une priorité de 2.</span><span class="sxs-lookup"><span data-stu-id="4a54c-165">The following defines the filter table and adds the "XPathFilter" defined earlier to the table with a priority of 2.</span></span> <span data-ttu-id="4a54c-166">Cette entrée précise également que `XPathFilter` si le message correspond au message, le message sera acheminé vers le `roundingCalcEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="4a54c-166">This entry also specifies that if the `XPathFilter` matches the message, the message will be routed to the `roundingCalcEndpoint`.</span></span>  
  
    ```xml  
    <routing>  
    ...      <filters>  
    ...      </filters>  
          <filterTables>  
            <table name="filterTable1">  
              <entries>  
                <!--add the filters to the message filter table-->  
                <!--first look for the custom header, and if we find it,  
                    send the message to the rounding calc endpoint-->  
                <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
              </entries>  
            </table>  
          <filterTables>  
    </routing>  
    ```  
  
     <span data-ttu-id="4a54c-167">Lors de la spécification d'une priorité de filtre, les filtres de priorité plus élevée sont évalués en premier.</span><span class="sxs-lookup"><span data-stu-id="4a54c-167">When specifying a filter priority, the highest priority filters are evaluated first.</span></span> <span data-ttu-id="4a54c-168">Si un ou plusieurs filtres d'un niveau de priorité spécifique correspondent, aucun filtre de niveau de priorité plus faible ne sera évalué.</span><span class="sxs-lookup"><span data-stu-id="4a54c-168">If one or more filters at a specific priority level match, no filters at lower priority levels will be evaluated.</span></span> <span data-ttu-id="4a54c-169">Pour ce scénario, 2 est la priorité spécifiée la plus élevée et c'est la seule entrée de filtre à ce niveau.</span><span class="sxs-lookup"><span data-stu-id="4a54c-169">For this scenario, 2 is the highest priority specified and this is the only filter entry at this level.</span></span>  
  
2. <span data-ttu-id="4a54c-170">Les entrées de filtre ont été définies pour vérifier si un message est reçu sur un point de terminaison spécifique, en contrôlant le nom du point de terminaison ou le préfixe d'adresse.</span><span class="sxs-lookup"><span data-stu-id="4a54c-170">Filter entries were defined to check to see if a message is received on a specific endpoint by inspecting the endpoint name or the address prefix.</span></span> <span data-ttu-id="4a54c-171">Les entrées suivantes ajoutent ces deux entrées de filtre à la table de filtres et les associent aux points de terminaison de destination vers lesquels le message sera routé.</span><span class="sxs-lookup"><span data-stu-id="4a54c-171">The following entries add both of these filter entries to the filter table and associate them with the destination endpoints that the message will be routed to.</span></span> <span data-ttu-id="4a54c-172">Une priorité de valeur 1 est attribuée à ces filtres pour indiquer qu'ils ne doivent s'exécuter que si le filtre XPath précédent ne correspondait pas au message.</span><span class="sxs-lookup"><span data-stu-id="4a54c-172">These filters are set to a priority of 1 to indicate that they should only run if the previous XPath filter did not match the message.</span></span>  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     <span data-ttu-id="4a54c-173">Puisque ces filtres ont une priorité de filtre de 1, ils ne seront évalués que si le filtre de niveau de priorité 2 ne correspond pas au message.</span><span class="sxs-lookup"><span data-stu-id="4a54c-173">Because these filters have a filter priority of 1, they will only be evaluated if the filter at priority level 2 does not match the message.</span></span> <span data-ttu-id="4a54c-174">Comme les deux filtres ont le même niveau de priorité, ils seront évalués simultanément.</span><span class="sxs-lookup"><span data-stu-id="4a54c-174">Also, because both filters have the same priority level they will be evaluated simultaneously.</span></span> <span data-ttu-id="4a54c-175">Puisque les deux filtres s'excluent mutuellement, un seul d'entre eux peut correspondre à un message.</span><span class="sxs-lookup"><span data-stu-id="4a54c-175">Because both filters are mutually exclusive, it is possible for only one or the other to match a message.</span></span>  
  
3. <span data-ttu-id="4a54c-176">Si un message ne correspond à aucun des filtres précédents, cela signifie que le message a été reçu via le point de terminaison de service générique et ne contenait aucune information d'en-tête indiquant où le router.</span><span class="sxs-lookup"><span data-stu-id="4a54c-176">If a message does not match any of the previous filters, then the message was received through the generic service endpoint and contained no header information that indicates where to route it.</span></span> <span data-ttu-id="4a54c-177">Ces messages doivent être contrôlés par le filtre personnalisé, qui équilibre leur charge entre les deux services de calculatrice.</span><span class="sxs-lookup"><span data-stu-id="4a54c-177">These messages are to be handled by the custom filter, which load balances them between the two calculator services.</span></span> <span data-ttu-id="4a54c-178">L'exemple suivant montre comment ajouter les entrées de filtre à la table de filtres ; chaque filtre est associé à l'un des deux points de terminaison de destination.</span><span class="sxs-lookup"><span data-stu-id="4a54c-178">The following example demonstrates how to add the filter entries to the filter table; each filter is associated with one of the two destination endpoints.</span></span>  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     <span data-ttu-id="4a54c-179">Ces entrées spécifient une priorité de niveau 0, elles ne seront donc évaluées que si aucun filtre de priorité plus élevée ne correspond au message.</span><span class="sxs-lookup"><span data-stu-id="4a54c-179">Because these entries specify a priority of 0, they will only be evaluated if no filter of a higher priority matches the message.</span></span> <span data-ttu-id="4a54c-180">De même, puisque les deux ont la même priorité, elles sont évaluées simultanément.</span><span class="sxs-lookup"><span data-stu-id="4a54c-180">Also, since both are of the same priority, they are evaluated simultaneously.</span></span>  
  
     <span data-ttu-id="4a54c-181">Comme indiqué précédemment, le filtre personnalisé utilisé par ces définitions de filtre évalue seulement l'une d'entre elles comme `true` pour chaque message reçu.</span><span class="sxs-lookup"><span data-stu-id="4a54c-181">As mentioned previously, the custom filter used by these filter definitions only evaluates one or the other as `true` for each message received.</span></span> <span data-ttu-id="4a54c-182">Comme deux filtres seulement sont définis à l'aide de ce filtre, avec le même paramètre de groupe spécifié, le résultat est que le service de routage effectue les envois en alternance au regularCalcEndpoint et au RoundingCalcEndpoint.</span><span class="sxs-lookup"><span data-stu-id="4a54c-182">Because only two filters are defined using this filter, with the same specified group setting, the effect is that the Routing Service alternates between sending to the regularCalcEndpoint and the RoundingCalcEndpoint.</span></span>  
  
4. <span data-ttu-id="4a54c-183">Pour évaluer les messages en fonction des filtres, la table de filtres doit être d'abord associée aux points de terminaison de service qui seront utilisés pour recevoir des messages.</span><span class="sxs-lookup"><span data-stu-id="4a54c-183">To evaluate messages against the filters, the filter table must first be associated with the service endpoints that will be used to receive messages.</span></span>  <span data-ttu-id="4a54c-184">L'exemple suivant montre comment associer la table de routage aux points de terminaison de service à l'aide du comportement de routage :</span><span class="sxs-lookup"><span data-stu-id="4a54c-184">The following example demonstrates how to associate the routing table with the service endpoints by using the routing behavior:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="4a54c-185"> Exemple</span><span class="sxs-lookup"><span data-stu-id="4a54c-185">Example</span></span>  
 <span data-ttu-id="4a54c-186">L'intégralité du fichier de configuration est présentée ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="4a54c-186">The following is a complete listing of the configuration file.</span></span>  
  
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
        <!--first create the general router endpoint-->  
        <endpoint address="general"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--create a virtual endpoint for the regular calculator service-->  
        <endpoint address="regular/calculator"  
                  binding="wsHttpBinding"  
                  name="calculatorEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--now create a virtual endpoint for the rounding calculator-->  
        <endpoint address="rounding/calculator"  
                  binding="wsHttpBinding"  
                  name="roundingEndpoint"  
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
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <endpoint name="roundingCalcEndpoint"  
                address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
      <namespaceTable>  
        <add prefix="custom" namespace="http://my.custom.namespace/"/>  
      </namespaceTable>  
      <filters>  
        <!--define the different message filters-->  
        <!--define an xpath message filter to look for the custom header coming from the client-->  
        <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
  
        <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
        <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
  
        <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
        <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress" filterData="http://localhost/routingservice/router/rounding/"/>  
  
        <!--Set up the custom message filters.  In this example, we'll use the example round robin message filter, which alternates between the references-->  
        <filter name="RoundRobinFilter1" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
        <filter name="RoundRobinFilter2" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
      </filters>  
      <filterTables>  
        <table name="filterTable1">  
          <entries>  
            <!--add the filters to the message filter table-->  
            <!--first look for the custom header, and if we find it, send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
  
            <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
            <!--we determine this through the endpoint name, or through the address prefix-->  
            <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
            <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
  
            <!--if none of the other filters have matched, this message showed up on the default router endpoint, with no custom header-->  
            <!--round robin these requests between the two services-->  
            <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
            <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
          </entries>  
        </table>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4a54c-187">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a54c-187">See also</span></span>

- [<span data-ttu-id="4a54c-188">Services de routage</span><span class="sxs-lookup"><span data-stu-id="4a54c-188">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
