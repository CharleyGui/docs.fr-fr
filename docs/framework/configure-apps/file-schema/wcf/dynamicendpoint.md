---
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: da57ca3ba3bc0036727a749f1cab9ec3657a4fda
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855342"
---
# <a name="dynamicendpoint"></a><span data-ttu-id="999f1-101">\<dynamicEndpoint></span><span class="sxs-lookup"><span data-stu-id="999f1-101">\<dynamicEndpoint></span></span>
<span data-ttu-id="999f1-102">Cet élément de configuration définit un point de terminaison standard qui contient des informations pour permettre à une application de fonctionner en tant que programme client qui peut rechercher l'adresse du point de terminaison de manière dynamique au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="999f1-102">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="999f1-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="999f1-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="999f1-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="999f1-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="999f1-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="999f1-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="999f1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<dynamicEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="999f1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dynamicEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="999f1-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="999f1-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="999f1-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="999f1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="999f1-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="999f1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="999f1-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="999f1-110">Attributes</span></span>  
 <span data-ttu-id="999f1-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="999f1-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="999f1-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="999f1-112">Child Elements</span></span>  
  
|<span data-ttu-id="999f1-113">Élément</span><span class="sxs-lookup"><span data-stu-id="999f1-113">Element</span></span>|<span data-ttu-id="999f1-114">Description</span><span class="sxs-lookup"><span data-stu-id="999f1-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="999f1-115">\<discoveryClientSettings></span><span class="sxs-lookup"><span data-stu-id="999f1-115">\<discoveryClientSettings></span></span>](discoveryclientsettings.md)|<span data-ttu-id="999f1-116">Contient les paramètres requis par une application pour participer au processus de découverte de service en tant que client.</span><span class="sxs-lookup"><span data-stu-id="999f1-116">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="999f1-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="999f1-117">Parent Elements</span></span>  
  
|<span data-ttu-id="999f1-118">Élément</span><span class="sxs-lookup"><span data-stu-id="999f1-118">Element</span></span>|<span data-ttu-id="999f1-119">Description</span><span class="sxs-lookup"><span data-stu-id="999f1-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="999f1-120">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="999f1-120">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="999f1-121">Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes.</span><span class="sxs-lookup"><span data-stu-id="999f1-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="999f1-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="999f1-122">See also</span></span>

- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
