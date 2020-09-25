---
title: <endpointDiscovery>
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 621c742e3bb06ce91fa5a6b8951351295f73df9e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185806"
---
# \<endpointDiscovery>

<span data-ttu-id="4ac44-101">Spécifie les différents paramètres de découverte d’un point de terminaison, tels que la fonctionnalité de découverte, les portées et toutes les extensions personnalisées de ses métadonnées.</span><span class="sxs-lookup"><span data-stu-id="4ac44-101">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointDiscovery>**  
  
## <a name="syntax"></a><span data-ttu-id="4ac44-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ac44-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4ac44-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4ac44-103">Attributes and Elements</span></span>  

 <span data-ttu-id="4ac44-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4ac44-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4ac44-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="4ac44-105">Attributes</span></span>  
  
|<span data-ttu-id="4ac44-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="4ac44-106">Attribute</span></span>|<span data-ttu-id="4ac44-107">Description</span><span class="sxs-lookup"><span data-stu-id="4ac44-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4ac44-108">enabled</span><span class="sxs-lookup"><span data-stu-id="4ac44-108">enabled</span></span>|<span data-ttu-id="4ac44-109">Valeur booléenne qui spécifie si la détectabilité est activée sur ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="4ac44-109">A Boolean value that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="4ac44-110">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="4ac44-110">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4ac44-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4ac44-111">Child Elements</span></span>  
  
|<span data-ttu-id="4ac44-112">Élément</span><span class="sxs-lookup"><span data-stu-id="4ac44-112">Element</span></span>|<span data-ttu-id="4ac44-113">Description</span><span class="sxs-lookup"><span data-stu-id="4ac44-113">Description</span></span>|  
|-------------|-----------------|  
|[\<scopes>](scopes.md)|<span data-ttu-id="4ac44-114">Collection d'URI de portée pour le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="4ac44-114">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="4ac44-115">Plusieurs URI de portée peuvent être associés au même point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="4ac44-115">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="4ac44-116">[\<extensions>](extensions.md) [of \<endpointDiscovery> ]</span><span class="sxs-lookup"><span data-stu-id="4ac44-116">[\<extensions>](extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="4ac44-117">Collection d'éléments XML qui vous permet de spécifier des métadonnées personnalisées à publier pour un point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="4ac44-117">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|\<types>|<span data-ttu-id="4ac44-118">Collection d'interfaces à rechercher.</span><span class="sxs-lookup"><span data-stu-id="4ac44-118">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4ac44-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4ac44-119">Parent Elements</span></span>  
  
|<span data-ttu-id="4ac44-120">Élément</span><span class="sxs-lookup"><span data-stu-id="4ac44-120">Element</span></span>|<span data-ttu-id="4ac44-121">Description</span><span class="sxs-lookup"><span data-stu-id="4ac44-121">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="4ac44-122">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="4ac44-122">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="4ac44-123">Notes</span><span class="sxs-lookup"><span data-stu-id="4ac44-123">Remarks</span></span>  

 <span data-ttu-id="4ac44-124">Lorsqu'il est ajouté à la configuration de comportement du point de terminaison et si le jeu d'attributs `enabled` a la valeur `true`, cet élément de configuration devient détectable.</span><span class="sxs-lookup"><span data-stu-id="4ac44-124">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="4ac44-125">En outre, vous pouvez utiliser l' [\<scopes>](scopes.md) élément enfant pour spécifier des URI de portée personnalisée qui peuvent être utilisés pour filtrer des points de terminaison de service pendant la requête, ainsi que l' [\<extensions>](extensions.md) élément enfant pour spécifier des métadonnées personnalisées qui doivent être publiées avec les métadonnées détectables standard (EPR, ContractTypeName, BindingName, Scope et ListenUri).</span><span class="sxs-lookup"><span data-stu-id="4ac44-125">In addition, you can use the [\<scopes>](scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="4ac44-126">Cet élément de configuration dépend de l' [\<serviceDiscovery>](servicediscovery.md) élément qui fournit le contrôle du niveau de service de la détectabilité.</span><span class="sxs-lookup"><span data-stu-id="4ac44-126">This configuration element is dependent on the [\<serviceDiscovery>](servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="4ac44-127">Cela signifie que les paramètres de cet élément sont ignorés si [\<serviceDiscovery>](servicediscovery.md) n’est pas présent dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="4ac44-127">This means that this element’s settings are ignored if [\<serviceDiscovery>](servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ac44-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="4ac44-128">Example</span></span>  

 <span data-ttu-id="4ac44-129">L'exemple de configuration suivant spécifie des portées de filtrage et des métadonnées d'extension à publier pour un point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="4ac44-129">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4ac44-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ac44-130">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
