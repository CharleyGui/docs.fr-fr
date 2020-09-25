---
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: 6f9cb127deb5651ed27a0ef5802512fb5b6c7b54
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190096"
---
# \<dynamicEndpoint>

<span data-ttu-id="836ba-101">Cet élément de configuration définit un point de terminaison standard qui contient des informations pour permettre à une application de fonctionner en tant que programme client qui peut rechercher l'adresse du point de terminaison de manière dynamique au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="836ba-101">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dynamicEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="836ba-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="836ba-102">Syntax</span></span>  
  
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
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="836ba-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="836ba-103">Attributes and Elements</span></span>  

 <span data-ttu-id="836ba-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="836ba-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="836ba-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="836ba-105">Attributes</span></span>  

 <span data-ttu-id="836ba-106">Aucun.</span><span class="sxs-lookup"><span data-stu-id="836ba-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="836ba-107">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="836ba-107">Child Elements</span></span>  
  
|<span data-ttu-id="836ba-108">Élément</span><span class="sxs-lookup"><span data-stu-id="836ba-108">Element</span></span>|<span data-ttu-id="836ba-109">Description</span><span class="sxs-lookup"><span data-stu-id="836ba-109">Description</span></span>|  
|-------------|-----------------|  
|[\<discoveryClientSettings>](discoveryclientsettings.md)|<span data-ttu-id="836ba-110">Contient les paramètres requis par une application pour participer au processus de découverte de service en tant que client.</span><span class="sxs-lookup"><span data-stu-id="836ba-110">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="836ba-111">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="836ba-111">Parent Elements</span></span>  
  
|<span data-ttu-id="836ba-112">Élément</span><span class="sxs-lookup"><span data-stu-id="836ba-112">Element</span></span>|<span data-ttu-id="836ba-113">Description</span><span class="sxs-lookup"><span data-stu-id="836ba-113">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="836ba-114">Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes.</span><span class="sxs-lookup"><span data-stu-id="836ba-114">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="836ba-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="836ba-115">See also</span></span>

- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
