---
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: da57ca3ba3bc0036727a749f1cab9ec3657a4fda
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855342"
---
# \<dynamicEndpoint>
<span data-ttu-id="765b7-101">Cet élément de configuration définit un point de terminaison standard qui contient des informations pour permettre à une application de fonctionner en tant que programme client qui peut rechercher l'adresse du point de terminaison de manière dynamique au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="765b7-101">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dynamicEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="765b7-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="765b7-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="765b7-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="765b7-103">Attributes and Elements</span></span>  
 <span data-ttu-id="765b7-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="765b7-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="765b7-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="765b7-105">Attributes</span></span>  
 <span data-ttu-id="765b7-106">Aucun.</span><span class="sxs-lookup"><span data-stu-id="765b7-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="765b7-107">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="765b7-107">Child Elements</span></span>  
  
|<span data-ttu-id="765b7-108">Élément</span><span class="sxs-lookup"><span data-stu-id="765b7-108">Element</span></span>|<span data-ttu-id="765b7-109">Description</span><span class="sxs-lookup"><span data-stu-id="765b7-109">Description</span></span>|  
|-------------|-----------------|  
|[\<discoveryClientSettings>](discoveryclientsettings.md)|<span data-ttu-id="765b7-110">Contient les paramètres requis par une application pour participer au processus de découverte de service en tant que client.</span><span class="sxs-lookup"><span data-stu-id="765b7-110">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="765b7-111">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="765b7-111">Parent Elements</span></span>  
  
|<span data-ttu-id="765b7-112">Élément</span><span class="sxs-lookup"><span data-stu-id="765b7-112">Element</span></span>|<span data-ttu-id="765b7-113">Description</span><span class="sxs-lookup"><span data-stu-id="765b7-113">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="765b7-114">Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes.</span><span class="sxs-lookup"><span data-stu-id="765b7-114">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="765b7-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="765b7-115">See also</span></span>

- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
