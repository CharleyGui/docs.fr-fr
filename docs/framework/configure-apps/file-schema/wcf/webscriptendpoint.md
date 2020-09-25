---
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: 5e3ca9c4a43432d7f5da6d8816b6a2b984851050
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177837"
---
# \<webScriptEndpoint>

<span data-ttu-id="7c0f7-101">Cet élément de configuration définit un point de terminaison standard avec une [\<webHttpBinding>](webhttpbinding.md) liaison fixe qui ajoute automatiquement le [\<enableWebScript>](enablewebscript.md) comportement.</span><span class="sxs-lookup"><span data-stu-id="7c0f7-101">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](enablewebscript.md) behavior.</span></span> <span data-ttu-id="7c0f7-102">Utilisez ce point de terminaison lorsque vous écrivez un service appelé à partir d'une application ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="7c0f7-102">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webScriptEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="7c0f7-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c0f7-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c0f7-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7c0f7-104">Attributes and Elements</span></span>  

 <span data-ttu-id="7c0f7-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7c0f7-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c0f7-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="7c0f7-106">Attributes</span></span>  
  
|<span data-ttu-id="7c0f7-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="7c0f7-107">Attribute</span></span>|<span data-ttu-id="7c0f7-108">Description</span><span class="sxs-lookup"><span data-stu-id="7c0f7-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7c0f7-109">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="7c0f7-109">webEndpointType</span></span>|<span data-ttu-id="7c0f7-110">Chaîne qui spécifie le type du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="7c0f7-110">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7c0f7-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7c0f7-111">Child Elements</span></span>  

 <span data-ttu-id="7c0f7-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7c0f7-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7c0f7-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7c0f7-113">Parent Elements</span></span>  
  
|<span data-ttu-id="7c0f7-114">Élément</span><span class="sxs-lookup"><span data-stu-id="7c0f7-114">Element</span></span>|<span data-ttu-id="7c0f7-115">Description</span><span class="sxs-lookup"><span data-stu-id="7c0f7-115">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="7c0f7-116">Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes.</span><span class="sxs-lookup"><span data-stu-id="7c0f7-116">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7c0f7-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c0f7-117">See also</span></span>

- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
