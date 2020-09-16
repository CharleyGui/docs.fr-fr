---
title: Choix d'un filtre
ms.date: 03/30/2017
ms.assetid: 67ab5af9-b9d9-4300-b3b1-41abb5a1fd10
ms.openlocfilehash: 2f96e7001a41682ef595d003e87daa06d0244f3b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559387"
---
# <a name="choosing-a-filter"></a><span data-ttu-id="82d94-102">Choix d'un filtre</span><span class="sxs-lookup"><span data-stu-id="82d94-102">Choosing a Filter</span></span>
<span data-ttu-id="82d94-103">Lors de la configuration du service de routage, il est important de sélectionner des filtres de message corrects et de les configurer pour vous permettre d'établir des correspondances exactes avec les messages que vous recevez.</span><span class="sxs-lookup"><span data-stu-id="82d94-103">When configuring the Routing Service, it is important to select correct message filters and configure them to allow you to make exact matches against the messages you receive.</span></span> <span data-ttu-id="82d94-104">Si les filtres que vous sélectionnez établissent des correspondances trop générales ou ne sont pas configurés correctement, les messages sont routés de manière incorrecte.</span><span class="sxs-lookup"><span data-stu-id="82d94-104">If the filters you select are overly broad in their matches or are incorrectly configured, messages are routed incorrectly.</span></span> <span data-ttu-id="82d94-105">Si les filtres sont trop restrictifs, vous risquez de ne pas disposer d'itinéraires valides disponibles pour certains de vos messages.</span><span class="sxs-lookup"><span data-stu-id="82d94-105">If the filters are too restrictive, you may not have any valid routes available for some of your messages.</span></span>

## <a name="filter-types"></a><span data-ttu-id="82d94-106">Types de filtres.</span><span class="sxs-lookup"><span data-stu-id="82d94-106">Filter Types</span></span>

<span data-ttu-id="82d94-107">Lors de la sélection des filtres utilisés par le service de routage, il est important de connaître le fonctionnement de chaque filtre, ainsi que les informations disponibles dans le cadre des messages entrants.</span><span class="sxs-lookup"><span data-stu-id="82d94-107">When selecting the filters that are used by the Routing Service, it is important that you understand how each filter works as well as what information is available as part of the incoming messages.</span></span> <span data-ttu-id="82d94-108">Par exemple, si tous les messages sont reçus sur le même point de terminaison, les filtres Adresse et EndpointName sont inutiles, parce que tous les messages correspondent à ces filtres.</span><span class="sxs-lookup"><span data-stu-id="82d94-108">For instance, if all messages are received over the same endpoint, the Address and EndpointName filters are not useful because all messages match these filters.</span></span>

### <a name="action"></a><span data-ttu-id="82d94-109">Action</span><span class="sxs-lookup"><span data-stu-id="82d94-109">Action</span></span>

<span data-ttu-id="82d94-110">Le filtre Action inspecte la propriété <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A>.</span><span class="sxs-lookup"><span data-stu-id="82d94-110">The Action filter inspects the <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> property.</span></span> <span data-ttu-id="82d94-111">Si le contenu de l'en-tête Action du message correspond à la valeur des données de filtre spécifiée dans la configuration du filtre, alors ce filtre retourne `true`.</span><span class="sxs-lookup"><span data-stu-id="82d94-111">If the contents of the Action header in the message match the filter data value specified in the filter configuration, then this filter returns `true`.</span></span> <span data-ttu-id="82d94-112">L’exemple suivant définit un `FilterElement` qui utilise le filtre d’action pour faire correspondre les messages avec un en-tête d’action qui contient une valeur de `http://namespace/contract/operation/` .</span><span class="sxs-lookup"><span data-stu-id="82d94-112">The following example defines a `FilterElement` that uses the Action filter to match messages with an action header that contains a value of `http://namespace/contract/operation/`.</span></span>

```xml
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/" />
```

```csharp
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });
```

<span data-ttu-id="82d94-113">Ce filtre doit être utilisé lors du routage des messages qui contiennent un en-tête Action unique.</span><span class="sxs-lookup"><span data-stu-id="82d94-113">This filter should be used when routing messages that contain a unique Action header.</span></span>

### <a name="endpointaddress"></a><span data-ttu-id="82d94-114">EndpointAddress</span><span class="sxs-lookup"><span data-stu-id="82d94-114">EndpointAddress</span></span>

<span data-ttu-id="82d94-115">Le filtre EndpointAddress inspecte l'EndpointAddress sur lequel le message a été reçu.</span><span class="sxs-lookup"><span data-stu-id="82d94-115">The EndpointAddress filter inspects the EndpointAddress that the message was received on.</span></span> <span data-ttu-id="82d94-116">Si l'adresse à laquelle le message arrive correspond exactement à l'adresse de filtre spécifiée dans la configuration de filtre, ce filtre retourne `true`.</span><span class="sxs-lookup"><span data-stu-id="82d94-116">If the address that the message arrives at exactly matches the filter address specified in the filter configuration, then this filter returns `true`.</span></span> <span data-ttu-id="82d94-117">L’exemple suivant définit un `FilterElement` qui utilise le filtre d’adresse pour faire correspondre tous les messages adressés à « http:// \<hostname> /vdir/s.svc/b ».</span><span class="sxs-lookup"><span data-stu-id="82d94-117">The following example defines a `FilterElement` that uses the Address filter to match any messages addressed to "http://\<hostname>/vdir/s.svc/b".</span></span>

```xml
<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b" />
```

```csharp
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);
```

> [!NOTE]
> <span data-ttu-id="82d94-118">Il est important de noter que la partie nom d'hôte d'une adresse peut différer selon que le client utilise le nom de domaine complet, le nom NetBIOS, l'adresse IP ou un autre nom.</span><span class="sxs-lookup"><span data-stu-id="82d94-118">It is important to note that the host name portion of an address can differ based on whether the client uses the fully qualified domain name, NetBIOS name, IP address, or other name.</span></span> <span data-ttu-id="82d94-119">Étant donné que des valeurs différentes peuvent faire référence au même hôte, le comportement par défaut de cette comparaison consiste à ne pas utiliser la partie nom d'hôte de l'adresse pour effectuer des correspondances.</span><span class="sxs-lookup"><span data-stu-id="82d94-119">Because differing values can refer to the same host, the default behavior for this comparison is to not use the host name portion of the address when performing matches.</span></span>
>
> <span data-ttu-id="82d94-120">Ce comportement peut être modifié pour permettre à la comparaison d'évaluer le nom d'hôte lors de la configuration du service de routage par programme.</span><span class="sxs-lookup"><span data-stu-id="82d94-120">This behavior can be modified to allow the comparison to evaluate the host name when configuring the Routing Service programmatically.</span></span>

<span data-ttu-id="82d94-121">Ce filtre doit être utilisé lorsque les messages entrants sont adressés à une adresse unique.</span><span class="sxs-lookup"><span data-stu-id="82d94-121">This filter should be used when the incoming messages are addressed to a unique address.</span></span>

### <a name="endpointaddressprefix"></a><span data-ttu-id="82d94-122">EndpointAddressPrefix</span><span class="sxs-lookup"><span data-stu-id="82d94-122">EndpointAddressPrefix</span></span>

<span data-ttu-id="82d94-123">Le filtre EndpointAddressPrefix est semblable au filtre EndpointAddress.</span><span class="sxs-lookup"><span data-stu-id="82d94-123">The EndpointAddressPrefix filter is similar to the EndpointAddress filter.</span></span> <span data-ttu-id="82d94-124">Le filtre EndpointAddressPrefix inspecte l'EndpointAddress sur lequel le message a été reçu.</span><span class="sxs-lookup"><span data-stu-id="82d94-124">The EndpointAddressPrefix filter inspects the EndpointAddress that the message was received on.</span></span> <span data-ttu-id="82d94-125">Toutefois, le filtre EndpointAddressPrefix agit comme un caractère générique en correspondant aux adresses qui commencent par la valeur spécifié dans la configuration de filtre.</span><span class="sxs-lookup"><span data-stu-id="82d94-125">However the EndpointAddressPrefix filter acts as a wildcard by matching addresses that begin with the value specified in the filter configuration.</span></span> <span data-ttu-id="82d94-126">L’exemple suivant définit un `FilterElement` qui utilise le filtre EndpointAddressPrefix pour faire correspondre tous les messages adressés à `http://<hostname>/vdir*` .</span><span class="sxs-lookup"><span data-stu-id="82d94-126">The following example defines a `FilterElement` that uses the EndpointAddressPrefix filter to match any messages addressed to `http://<hostname>/vdir*`.</span></span>

```xml
<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/vdir" />
```

```csharp
PrefixEndpointAddressMessageFilter prefix1 = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);
```

> [!NOTE]
> <span data-ttu-id="82d94-127">Il est important de noter que la partie nom d'hôte d'une adresse peut différer selon que le client utilise le nom de domaine complet, le nom NetBIOS, l'adresse IP ou un autre nom.</span><span class="sxs-lookup"><span data-stu-id="82d94-127">It is important to note that the host name portion of an address can differ based on whether the client uses the fully qualified domain name, NetBIOS name, IP address, or other name.</span></span> <span data-ttu-id="82d94-128">Étant donné que des valeurs différentes peuvent faire référence au même hôte, le comportement par défaut de cette comparaison consiste à ne pas utiliser la partie nom d'hôte de l'adresse pour effectuer des correspondances.</span><span class="sxs-lookup"><span data-stu-id="82d94-128">Because differing values can refer to the same host, the default behavior for this comparison is to not use the host name portion of the address when performing matches.</span></span>

<span data-ttu-id="82d94-129">Ce filtre doit être utilisé lors du routage des messages entrants qui partagent un préfixe d'adresse commun.</span><span class="sxs-lookup"><span data-stu-id="82d94-129">This filter should be used when routing incoming messages that share a common address prefix.</span></span>

### <a name="and"></a><span data-ttu-id="82d94-130">AND</span><span class="sxs-lookup"><span data-stu-id="82d94-130">AND</span></span>

<span data-ttu-id="82d94-131">Le filtre AND ne filtre pas directement sur une valeur dans un message, mais vous permet de combiner deux autres filtres pour créer une condition `AND` où les deux filtres doivent correspondre au message pour que le filtre AND retourne la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="82d94-131">The AND filter does not directly filter on a value within a message, but allows you to combine two other filters to create an `AND` condition where both filters must match the message before the AND filter evaluates to `true`.</span></span> <span data-ttu-id="82d94-132">Cela vous permet de créer des filtres complexes qui établissent une correspondance uniquement si tous les sous-filtres correspondent.</span><span class="sxs-lookup"><span data-stu-id="82d94-132">This allows you to create complex filters that only match if all the sub-filters match.</span></span> <span data-ttu-id="82d94-133">L'exemple suivant définit un filtre d'adresse et un filtre d'action, puis définit un filtre AND qui évalue un message en fonction de ces deux filtres d'action et d'adresse.</span><span class="sxs-lookup"><span data-stu-id="82d94-133">The following example defines an address filter and an action filter, and then defines an AND filter that evaluates a message against both the address and action filters.</span></span> <span data-ttu-id="82d94-134">Si les filtres d'adresse et d'action correspondent tous les deux, alors le filtre AND retourne `true`.</span><span class="sxs-lookup"><span data-stu-id="82d94-134">If both the address and the action filters match, then the AND filter returns `true`.</span></span>

```xml
<filter name="address1" filterType="AddressPrefix" filterData="http://host/vdir"/>
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/"/>
<filter name="and1" filterType="And" filter1="address1" filter2="action1" />
```

```csharp
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });
StrictAndMessageFilter and1=new StrictAndMessageFilter(address1, action1);
```

<span data-ttu-id="82d94-135">Ce filtre doit être utilisé lorsque vous devez combiner la logique de plusieurs filtres pour déterminer quand une correspondance doit être établie.</span><span class="sxs-lookup"><span data-stu-id="82d94-135">This filter should be used when you must combine the logic from multiple filters to determine when a match should be made.</span></span> <span data-ttu-id="82d94-136">Par exemple, si vous avez plusieurs destinations qui doivent recevoir uniquement certaines combinaisons d'actions et de messages à des adresses particulières, vous pouvez utiliser un filtre AND pour combiner les filtres Action et Adresse nécessaires.</span><span class="sxs-lookup"><span data-stu-id="82d94-136">For example, if you have multiple destinations that must receive only certain combinations of actions and messages to particular addresses, you can use an AND filter to combine the necessary Action and Address filters.</span></span>

### <a name="custom"></a><span data-ttu-id="82d94-137">Custom</span><span class="sxs-lookup"><span data-stu-id="82d94-137">Custom</span></span>

<span data-ttu-id="82d94-138">Lorsque vous sélectionnez le type de filtre personnalisé, vous devez fournir une valeur customType qui contient le type de l’assembly qui contient l’implémentation **MessageFilter** à utiliser pour ce filtre.</span><span class="sxs-lookup"><span data-stu-id="82d94-138">When selecting the Custom filter type, you must provide a customType value that contains the type of the assembly that contains the **MessageFilter** implementation to be used for this filter.</span></span> <span data-ttu-id="82d94-139">En outre, le filterData doit contenir les valeurs requises par le filtre personnalisé pour son évaluation des messages.</span><span class="sxs-lookup"><span data-stu-id="82d94-139">Additionally, filterData must contain any values that the custom filter may require in its evaluation of messages.</span></span> <span data-ttu-id="82d94-140">L'exemple suivant définit un `FilterElement` qui utilise l'implémentation de MessageFilter `CustomAssembly.MyCustomMsgFilter`.</span><span class="sxs-lookup"><span data-stu-id="82d94-140">The following example defines a `FilterElement` that uses the `CustomAssembly.MyCustomMsgFilter` MessageFilter implementation.</span></span>

```xml
<filter name="custom1" filterType="Custom" customType="CustomAssembly.MyCustomMsgFilter, CustomAssembly" filterData="Custom Data" />
```

```csharp
MyCustomMsgFilter custom1=new MyCustomMsgFilter("Custom Data");
```

<span data-ttu-id="82d94-141">Si vous devez exécuter une logique de correspondance personnalisée sur un message qui n’est pas couvert par les filtres fournis avec [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] , vous devez créer un filtre personnalisé qui est une implémentation de la classe **MessageFilter** .</span><span class="sxs-lookup"><span data-stu-id="82d94-141">If you need to perform custom matching logic against a message that is not covered by the filters provided with [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], you must create a custom filter that is an implementation of the **MessageFilter** class.</span></span> <span data-ttu-id="82d94-142">Par exemple, vous pouvez créer un filtre personnalisé qui compare un champ dans le message entrant à une liste de valeurs connues données au filtre en tant que configuration, ou qui hache un élément de message particulier, puis examine cette valeur pour déterminer si le filtre doit retourner `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="82d94-142">For example, you might create a custom filter that compares a field in the incoming message against a list of known values given to the filter as configuration, or that hashes a particular message element and then examines that value to determine whether the filter should return `true` or `false`.</span></span>

### <a name="endpointname"></a><span data-ttu-id="82d94-143">EndpointName</span><span class="sxs-lookup"><span data-stu-id="82d94-143">EndpointName</span></span>

<span data-ttu-id="82d94-144">Le filtre EndpointName inspecte le nom du point de terminaison qui a reçu le message.</span><span class="sxs-lookup"><span data-stu-id="82d94-144">The EndpointName filter inspects the name of the endpoint that received the message.</span></span> <span data-ttu-id="82d94-145">L’exemple suivant définit un `FilterElement` qui utilise le filtre EndpointName pour acheminer les messages reçus sur « SvcEndpoint ».</span><span class="sxs-lookup"><span data-stu-id="82d94-145">The following example defines a `FilterElement` that uses the EndpointName filter to route messages received on the "SvcEndpoint".</span></span>

```xml
<filter name="name1" filterType="Endpoint" filterData="SvcEndpoint" />
```

```csharp
EndpointNameMessageFilter name1 = new EndpointNameMessageFilter("SvcEndpoint");
```

<span data-ttu-id="82d94-146">Ce filtre est utile lorsque le service de routage expose plusieurs points de terminaison de service nommés.</span><span class="sxs-lookup"><span data-stu-id="82d94-146">This filter is useful when the Routing Service exposes more than one named service endpoint.</span></span> <span data-ttu-id="82d94-147">Par exemple, vous pouvez exposer deux points de terminaison que le service de routage utilise pour recevoir des messages ; l'un est utilisé par les clients prioritaires qui nécessitent un traitement en temps réel de leurs messages, tandis que l'autre reçoit des messages pour lesquels le délai importe peu.</span><span class="sxs-lookup"><span data-stu-id="82d94-147">For example, you might expose two endpoints that the Routing Service uses to receive messages; one is used by priority customers who require real-time processing of their messages, while the other endpoint receives messages that are not time sensitive.</span></span>

<span data-ttu-id="82d94-148">Une correspondance de l'adresse complète est souvent utilisée pour déterminer sur quel point de terminaison un message a été reçu. Cependant, utiliser le nom défini du point de terminaison est un raccourci commode souvent moins sujet aux erreurs, notamment dans le cas d'une configuration de service de routage à l'aide d'un fichier de configuration (où les noms des points de terminaison sont un attribut obligatoire).</span><span class="sxs-lookup"><span data-stu-id="82d94-148">While you can often use full address matching to determine which endpoint a message was received on, using the defined endpoint name instead is a convenient shortcut that is often less error prone, especially when configuring a Routing Service using a configuration file (where endpoint names are a required attribute).</span></span>

### <a name="matchall"></a><span data-ttu-id="82d94-149">MatchAll</span><span class="sxs-lookup"><span data-stu-id="82d94-149">MatchAll</span></span>

<span data-ttu-id="82d94-150">Le filtre MatchAll correspond à n'importe quel message reçu.</span><span class="sxs-lookup"><span data-stu-id="82d94-150">The MatchAll filter matches any received message.</span></span> <span data-ttu-id="82d94-151">Il est utile si vous devez toujours router l'ensemble des messages reçus vers un point de terminaison spécifique, tel qu'un service de journalisation qui stocke une copie de tous les messages reçus.</span><span class="sxs-lookup"><span data-stu-id="82d94-151">It is useful if you must always route all received messages to a specific endpoint, such as a logging service that stores a copy of all received messages.</span></span> <span data-ttu-id="82d94-152">L'exemple suivant définit un `FilterElement` qui utilise le filtre MatchAll.</span><span class="sxs-lookup"><span data-stu-id="82d94-152">The following example defines a `FilterElement` that uses the MatchAll filter.</span></span>

```xml
<filter name="matchAll1" filterType="MatchAll" />
```

```csharp
MatchAllMessageFilter matchAll1 = new MatchAllMessageFilter();
```

### <a name="xpath"></a><span data-ttu-id="82d94-153">XPath</span><span class="sxs-lookup"><span data-stu-id="82d94-153">XPath</span></span>

<span data-ttu-id="82d94-154">Le filtre XPath vous permet de spécifier une requête XPath utilisée pour inspecter un élément spécifique dans le message.</span><span class="sxs-lookup"><span data-stu-id="82d94-154">The XPath filter allows you to specify an XPath query that is used to inspect a specific element within the message.</span></span> <span data-ttu-id="82d94-155">Le filtrage XPath est une option de filtrage puissante qui vous permet d’inspecter directement toute entrée XML adressable dans le message ; toutefois il requiert une connaissance spécifique de la structure des messages que vous recevez.</span><span class="sxs-lookup"><span data-stu-id="82d94-155">XPath filtering is a powerful filtering option that allows you to directly inspect any XML addressable entry within the message; however it requires that you have specific knowledge of the structure of the messages that you are receiving.</span></span> <span data-ttu-id="82d94-156">L’exemple suivant définit un `FilterElement` qui utilise le filtre XPath pour inspecter le message d’un élément nommé « element » dans l’espace de noms référencé par le préfixe d’espace de noms « ns ».</span><span class="sxs-lookup"><span data-stu-id="82d94-156">The following example defines a `FilterElement` that uses the XPath filter to inspect the message for an element named "element" within the namespace referenced by the "ns" namespace prefix.</span></span>

```xml
<filter name="xpath1" filterType="XPath" filterData="//ns:element" />
```

```csharp
XPathMessageFilter xpath1=new XPathMessageFilter("//ns:element");
```

<span data-ttu-id="82d94-157">Ce filtre est utile si vous savez que les messages que vous recevez contiennent une valeur spécifique.</span><span class="sxs-lookup"><span data-stu-id="82d94-157">This filter is useful if you know that the messages you are receiving contain a specific value.</span></span> <span data-ttu-id="82d94-158">Par exemple, vous hébergez deux versions du même service et savez que les messages adressés à la version la plus récente du service contiennent une valeur unique dans un en-tête personnalisé. Vous pouvez créer un filtre qui utilise XPath pour accéder à cet en-tête. Le filtre compare la valeur présente dans l'en-tête à une autre indiquée dans la configuration du filtre, afin de déterminer si le filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="82d94-158">For example, if you are hosting two versions of the same service and you know that messages addressed to the newer version of the service contain a unique value in a custom header, you can create a filter that uses XPath to navigate to this header and compares the value present in the header to another given in the filter configuration to determine if the filter matches.</span></span>

<span data-ttu-id="82d94-159">Étant donné que les requêtes XPath contiennent souvent des espaces de noms uniques, qui sont souvent des valeurs de chaîne longues ou complexes, le filtre XPath vous permet d’utiliser la table d’espace de noms pour définir des préfixes uniques pour vos espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="82d94-159">Because XPath queries often contain unique namespaces, which are often lengthy or complex string values, the XPath filter allows you to use the namespace table to define unique prefixes for your namespaces.</span></span> <span data-ttu-id="82d94-160">Pour plus d’informations sur la table d’espace de noms, consultez [filtres de messages](message-filters.md).</span><span class="sxs-lookup"><span data-stu-id="82d94-160">For more information about the namespace table, see [Message Filters](message-filters.md).</span></span>

<span data-ttu-id="82d94-161">Pour plus d’informations sur la conception de requêtes XPath, consultez [syntaxe XPath](/previous-versions/dotnet/netframework-4.0/ms256471(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="82d94-161">For more information about designing XPath queries, see [XPath Syntax](/previous-versions/dotnet/netframework-4.0/ms256471(v=vs.100)).</span></span>

## <a name="see-also"></a><span data-ttu-id="82d94-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82d94-162">See also</span></span>

- [<span data-ttu-id="82d94-163">Filtres de message</span><span class="sxs-lookup"><span data-stu-id="82d94-163">Message Filters</span></span>](message-filters.md)
- [<span data-ttu-id="82d94-164">Procédure : utiliser des filtres</span><span class="sxs-lookup"><span data-stu-id="82d94-164">How To: Use Filters</span></span>](how-to-use-filters.md)
