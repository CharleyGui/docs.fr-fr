---
title: <add> de <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 69a0bbbc8774251dbdc062875bb06453f355c882
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149138"
---
# <a name="add-of-contracttypenames"></a><span data-ttu-id="46349-102">\<add> de \<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="46349-102">\<add> of \<contractTypeNames></span></span>

<span data-ttu-id="46349-103">Élément de configuration qui spécifie le nom de contrat des services recherchés et les critères généralement utilisés lors de la recherche d'un service.</span><span class="sxs-lookup"><span data-stu-id="46349-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="46349-104">Si plusieurs noms de contrat sont spécifiés, seuls les points de terminaison de service correspondant à TOUS les contrats répondent.</span><span class="sxs-lookup"><span data-stu-id="46349-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="46349-105">Notez que dans Windows Communication Foundation (WCF), un point de terminaison ne peut prendre en charge qu’un seul contrat.</span><span class="sxs-lookup"><span data-stu-id="46349-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<findCriteria>**](findcriteria.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<contractTypeNames>**](contracttypenames.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="46349-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46349-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan"
                        maxResults="Integer"
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String" namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI"/>
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46349-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="46349-107">Attributes and Elements</span></span>  

 <span data-ttu-id="46349-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="46349-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46349-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="46349-109">Attributes</span></span>  
  
|<span data-ttu-id="46349-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="46349-110">Attribute</span></span>|<span data-ttu-id="46349-111">Description</span><span class="sxs-lookup"><span data-stu-id="46349-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="46349-112">name</span><span class="sxs-lookup"><span data-stu-id="46349-112">name</span></span>|<span data-ttu-id="46349-113">Chaîne qui spécifie le nom du type de contrat.</span><span class="sxs-lookup"><span data-stu-id="46349-113">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="46349-114">espace de noms</span><span class="sxs-lookup"><span data-stu-id="46349-114">namespace</span></span>|<span data-ttu-id="46349-115">Chaîne qui spécifie l'espace de noms du type de contrat.</span><span class="sxs-lookup"><span data-stu-id="46349-115">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="46349-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="46349-116">Child Elements</span></span>  

 <span data-ttu-id="46349-117">None</span><span class="sxs-lookup"><span data-stu-id="46349-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="46349-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="46349-118">Parent Elements</span></span>  
  
|<span data-ttu-id="46349-119">Élément</span><span class="sxs-lookup"><span data-stu-id="46349-119">Element</span></span>|<span data-ttu-id="46349-120">Description</span><span class="sxs-lookup"><span data-stu-id="46349-120">Description</span></span>|  
|-------------|-----------------|  
|[\<contractTypeNames>](contracttypenames.md)|<span data-ttu-id="46349-121">Collection de noms de type de contrat.</span><span class="sxs-lookup"><span data-stu-id="46349-121">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="46349-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46349-122">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
