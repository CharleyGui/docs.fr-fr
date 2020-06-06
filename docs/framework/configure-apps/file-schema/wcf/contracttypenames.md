---
title: <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: c67e5b9e82b96e27ce73512680bd4236b26ef4dd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855450"
---
# \<contractTypeNames>
<span data-ttu-id="3495b-101">Section de configuration qui spécifie une liste de noms de type de contrat, qui sont les noms de contrat des services recherchés, et les critères généralement utilisés lors de la recherche d'un service.</span><span class="sxs-lookup"><span data-stu-id="3495b-101">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="3495b-102">Si plusieurs noms de contrat sont spécifiés, seuls les points de terminaison de service correspondant à TOUS les contrats répondent.</span><span class="sxs-lookup"><span data-stu-id="3495b-102">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="3495b-103">Notez que dans Windows Communication Foundation (WCF), un point de terminaison ne peut prendre en charge qu’un seul contrat.</span><span class="sxs-lookup"><span data-stu-id="3495b-103">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<findCriteria>**](findcriteria.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<contractTypeNames>**  
  
## <a name="syntax"></a><span data-ttu-id="3495b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3495b-104">Syntax</span></span>  
  
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
              <add name="String"
                   namespace="String" />
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3495b-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3495b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3495b-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3495b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3495b-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="3495b-107">Attributes</span></span>  
 <span data-ttu-id="3495b-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3495b-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3495b-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3495b-109">Child Elements</span></span>  
  
|<span data-ttu-id="3495b-110">Élément</span><span class="sxs-lookup"><span data-stu-id="3495b-110">Element</span></span>|<span data-ttu-id="3495b-111">Description</span><span class="sxs-lookup"><span data-stu-id="3495b-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](contracttypenames.md)|<span data-ttu-id="3495b-112">Un nom de type de contrat est une propriété qui fait référence au jeu de critères utilisé en général au cours de la recherche d'un service.</span><span class="sxs-lookup"><span data-stu-id="3495b-112">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3495b-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3495b-113">Parent Elements</span></span>  
  
|<span data-ttu-id="3495b-114">Élément</span><span class="sxs-lookup"><span data-stu-id="3495b-114">Element</span></span>|<span data-ttu-id="3495b-115">Description</span><span class="sxs-lookup"><span data-stu-id="3495b-115">Description</span></span>|  
|-------------|-----------------|  
|[\<findCriteria>](findcriteria.md)|<span data-ttu-id="3495b-116">Élément de configuration qui fournit un jeu de critères utilisé par une application cliente pour rechercher un service de découverte.</span><span class="sxs-lookup"><span data-stu-id="3495b-116">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="3495b-117">Les critères peuvent être regroupés en critères de recherche (spécifiant les services recherchés) et critères d'arrêt de la recherche (durée de la recherche).</span><span class="sxs-lookup"><span data-stu-id="3495b-117">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3495b-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3495b-118">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
