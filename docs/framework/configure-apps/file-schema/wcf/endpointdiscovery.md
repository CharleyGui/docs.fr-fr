---
title: <endpointDiscovery>
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 98b1655f42b7b43604ed4ab9d66870ec204a9590
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398017"
---
# <a name="endpointdiscovery"></a><span data-ttu-id="16ea8-101">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="16ea8-101">\<endpointDiscovery></span></span>
<span data-ttu-id="16ea8-102">Spécifie les différents paramètres de découverte d’un point de terminaison, tels que la fonctionnalité de découverte, les portées et toutes les extensions personnalisées de ses métadonnées.</span><span class="sxs-lookup"><span data-stu-id="16ea8-102">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
<span data-ttu-id="16ea8-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="16ea8-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="16ea8-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="16ea8-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="16ea8-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="16ea8-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="16ea8-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="16ea8-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="16ea8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="16ea8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="16ea8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<endpointDiscovery >**</span><span class="sxs-lookup"><span data-stu-id="16ea8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointDiscovery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16ea8-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16ea8-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16ea8-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="16ea8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="16ea8-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="16ea8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16ea8-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="16ea8-112">Attributes</span></span>  
  
|<span data-ttu-id="16ea8-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="16ea8-113">Attribute</span></span>|<span data-ttu-id="16ea8-114">Description</span><span class="sxs-lookup"><span data-stu-id="16ea8-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="16ea8-115">enabled</span><span class="sxs-lookup"><span data-stu-id="16ea8-115">enabled</span></span>|<span data-ttu-id="16ea8-116">Valeur booléenne qui spécifie si la détectabilité est activée sur ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="16ea8-116">A Boolean value that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="16ea8-117">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="16ea8-117">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16ea8-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="16ea8-118">Child Elements</span></span>  
  
|<span data-ttu-id="16ea8-119">Élément</span><span class="sxs-lookup"><span data-stu-id="16ea8-119">Element</span></span>|<span data-ttu-id="16ea8-120">Description</span><span class="sxs-lookup"><span data-stu-id="16ea8-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="16ea8-121">\<scopes></span><span class="sxs-lookup"><span data-stu-id="16ea8-121">\<scopes></span></span>](scopes.md)|<span data-ttu-id="16ea8-122">Collection d'URI de portée pour le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="16ea8-122">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="16ea8-123">Plusieurs URI de portée peuvent être associés au même point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="16ea8-123">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="16ea8-124">[\<extensions>](extensions.md) [of \<endpointDiscovery>]</span><span class="sxs-lookup"><span data-stu-id="16ea8-124">[\<extensions>](extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="16ea8-125">Collection d'éléments XML qui vous permet de spécifier des métadonnées personnalisées à publier pour un point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="16ea8-125">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|<span data-ttu-id="16ea8-126">\<types></span><span class="sxs-lookup"><span data-stu-id="16ea8-126">\<types></span></span>|<span data-ttu-id="16ea8-127">Collection d'interfaces à rechercher.</span><span class="sxs-lookup"><span data-stu-id="16ea8-127">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="16ea8-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="16ea8-128">Parent Elements</span></span>  
  
|<span data-ttu-id="16ea8-129">Élément</span><span class="sxs-lookup"><span data-stu-id="16ea8-129">Element</span></span>|<span data-ttu-id="16ea8-130">Description</span><span class="sxs-lookup"><span data-stu-id="16ea8-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="16ea8-131">\<behavior></span><span class="sxs-lookup"><span data-stu-id="16ea8-131">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="16ea8-132">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="16ea8-132">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="16ea8-133">Notes</span><span class="sxs-lookup"><span data-stu-id="16ea8-133">Remarks</span></span>  
 <span data-ttu-id="16ea8-134">Lorsqu'il est ajouté à la configuration de comportement du point de terminaison et si le jeu d'attributs `enabled` a la valeur `true`, cet élément de configuration devient détectable.</span><span class="sxs-lookup"><span data-stu-id="16ea8-134">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="16ea8-135">En outre, vous pouvez utiliser les [ \<étendues >](scopes.md)élément enfant pour spécifier des URI de portée personnalisée qui peuvent être utilisés pour filtrer les points de terminaison de service pendant la requête, ainsi que les [ \<extensions >](extensions.md) élément enfant pour spécifier personnalisé les métadonnées qui doivent être publiées avec les métadonnées détectables standard (EPR, ContractTypeName, BindingName, Scope et ListenURI).</span><span class="sxs-lookup"><span data-stu-id="16ea8-135">In addition, you can use the [\<scopes>](scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="16ea8-136">Cet élément de configuration dépend de l' [ \<élément serviceDiscovery >](servicediscovery.md) qui fournit le contrôle du niveau de service de la détectabilité.</span><span class="sxs-lookup"><span data-stu-id="16ea8-136">This configuration element is dependent on the [\<serviceDiscovery>](servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="16ea8-137">Cela signifie que les paramètres de cet élément sont ignorés si [ \<serviceDiscovery >](servicediscovery.md) n’est pas présent dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="16ea8-137">This means that this element’s settings are ignored if [\<serviceDiscovery>](servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16ea8-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="16ea8-138">Example</span></span>  
 <span data-ttu-id="16ea8-139">L'exemple de configuration suivant spécifie des portées de filtrage et des métadonnées d'extension à publier pour un point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="16ea8-139">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="16ea8-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16ea8-140">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
