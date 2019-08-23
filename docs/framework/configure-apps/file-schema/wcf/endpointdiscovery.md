---
title: <endpointDiscovery>
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 5cb64c54067ba695f67d86c0026db77ebbe7d5ee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919049"
---
# <a name="endpointdiscovery"></a><span data-ttu-id="f9a29-101">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="f9a29-101">\<endpointDiscovery></span></span>
<span data-ttu-id="f9a29-102">Spécifie les différents paramètres de découverte d’un point de terminaison, tels que la fonctionnalité de découverte, les portées et toutes les extensions personnalisées de ses métadonnées.</span><span class="sxs-lookup"><span data-stu-id="f9a29-102">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
<span data-ttu-id="f9a29-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f9a29-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="f9a29-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="f9a29-104">\<behaviors></span></span>  
<span data-ttu-id="f9a29-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="f9a29-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="f9a29-106">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="f9a29-106">\<behavior></span></span>  
<span data-ttu-id="f9a29-107">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="f9a29-107">\<endpointDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9a29-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9a29-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enabled="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
        <extensions />
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9a29-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f9a29-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f9a29-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f9a29-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9a29-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="f9a29-111">Attributes</span></span>  
  
|<span data-ttu-id="f9a29-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="f9a29-112">Attribute</span></span>|<span data-ttu-id="f9a29-113">Description</span><span class="sxs-lookup"><span data-stu-id="f9a29-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f9a29-114">enabled</span><span class="sxs-lookup"><span data-stu-id="f9a29-114">enabled</span></span>|<span data-ttu-id="f9a29-115">Valeur booléenne qui spécifie si la détectabilité est activée sur ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="f9a29-115">A Boolean value that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="f9a29-116">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="f9a29-116">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f9a29-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f9a29-117">Child Elements</span></span>  
  
|<span data-ttu-id="f9a29-118">Élément</span><span class="sxs-lookup"><span data-stu-id="f9a29-118">Element</span></span>|<span data-ttu-id="f9a29-119">Description</span><span class="sxs-lookup"><span data-stu-id="f9a29-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f9a29-120">\<scopes></span><span class="sxs-lookup"><span data-stu-id="f9a29-120">\<scopes></span></span>](scopes.md)|<span data-ttu-id="f9a29-121">Collection d'URI de portée pour le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="f9a29-121">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="f9a29-122">Plusieurs URI de portée peuvent être associés au même point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="f9a29-122">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="f9a29-123">[\<extensions>](extensions.md) [of \<endpointDiscovery>]</span><span class="sxs-lookup"><span data-stu-id="f9a29-123">[\<extensions>](extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="f9a29-124">Collection d'éléments XML qui vous permet de spécifier des métadonnées personnalisées à publier pour un point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="f9a29-124">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|<span data-ttu-id="f9a29-125">\<types></span><span class="sxs-lookup"><span data-stu-id="f9a29-125">\<types></span></span>|<span data-ttu-id="f9a29-126">Collection d'interfaces à rechercher.</span><span class="sxs-lookup"><span data-stu-id="f9a29-126">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f9a29-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f9a29-127">Parent Elements</span></span>  
  
|<span data-ttu-id="f9a29-128">Élément</span><span class="sxs-lookup"><span data-stu-id="f9a29-128">Element</span></span>|<span data-ttu-id="f9a29-129">Description</span><span class="sxs-lookup"><span data-stu-id="f9a29-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f9a29-130">\<behavior></span><span class="sxs-lookup"><span data-stu-id="f9a29-130">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="f9a29-131">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="f9a29-131">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="f9a29-132">Notes</span><span class="sxs-lookup"><span data-stu-id="f9a29-132">Remarks</span></span>  
 <span data-ttu-id="f9a29-133">Lorsqu'il est ajouté à la configuration de comportement du point de terminaison et si le jeu d'attributs `enabled` a la valeur `true`, cet élément de configuration devient détectable.</span><span class="sxs-lookup"><span data-stu-id="f9a29-133">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="f9a29-134">En outre, vous pouvez utiliser les [ \<étendues >](scopes.md)élément enfant pour spécifier des URI de portée personnalisée qui peuvent être utilisés pour filtrer les points de terminaison de service pendant la requête, ainsi que les [ \<extensions >](extensions.md) élément enfant pour spécifier personnalisé les métadonnées qui doivent être publiées avec les métadonnées détectables standard (EPR, ContractTypeName, BindingName, Scope et ListenURI).</span><span class="sxs-lookup"><span data-stu-id="f9a29-134">In addition, you can use the [\<scopes>](scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="f9a29-135">Cet élément de configuration dépend de l' [ \<élément serviceDiscovery >](servicediscovery.md) qui fournit le contrôle du niveau de service de la détectabilité.</span><span class="sxs-lookup"><span data-stu-id="f9a29-135">This configuration element is dependent on the [\<serviceDiscovery>](servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="f9a29-136">Cela signifie que les paramètres de cet élément sont ignorés si [ \<serviceDiscovery >](servicediscovery.md) n’est pas présent dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="f9a29-136">This means that this element’s settings are ignored if [\<serviceDiscovery>](servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9a29-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="f9a29-137">Example</span></span>  
 <span data-ttu-id="f9a29-138">L'exemple de configuration suivant spécifie des portées de filtrage et des métadonnées d'extension à publier pour un point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="f9a29-138">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService"
              behaviorConfiguration="calculatorEndpointBehavior" />
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDiscovery />
    </behavior>
  </serviceBehaviors>
  <endpointBehaviors>
    <behavior name="calculatorEndpointBehavior">
      <endpointDiscovery enabled="true">
        <scopes>
          <add scope="http://contoso/test1" />
          <add scope="http://contoso/test2" />
        </scopes>
        <extensions>
          <e:Publisher xmlns:e="http://example.org">
            <e:Name>The Example Organization</e:Name>
            <e:Address>One Example Way, ExampleTown, EX 12345</e:Address>
            <e:Contact>support@example.org</e:Contact>
          </e:Publisher>
          <AnotherCustomMetadata>Custom Metadata</AnotherCustomMetadata>
        </extensions>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="f9a29-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9a29-139">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
