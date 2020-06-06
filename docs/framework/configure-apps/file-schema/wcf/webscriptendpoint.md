---
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: b4bc33cf8ff4e703973efe7df49e9f1d2189302e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854817"
---
# \<webScriptEndpoint>
<span data-ttu-id="ff329-101">Cet élément de configuration définit un point de terminaison standard avec une [\<webHttpBinding>](webhttpbinding.md) liaison fixe qui ajoute automatiquement le [\<enableWebScript>](enablewebscript.md) comportement.</span><span class="sxs-lookup"><span data-stu-id="ff329-101">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](enablewebscript.md) behavior.</span></span> <span data-ttu-id="ff329-102">Utilisez ce point de terminaison lorsque vous écrivez un service appelé à partir d'une application ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="ff329-102">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webScriptEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="ff329-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff329-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff329-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ff329-104">Attributes and Elements</span></span>  
 <span data-ttu-id="ff329-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ff329-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff329-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="ff329-106">Attributes</span></span>  
  
|<span data-ttu-id="ff329-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="ff329-107">Attribute</span></span>|<span data-ttu-id="ff329-108">Description</span><span class="sxs-lookup"><span data-stu-id="ff329-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ff329-109">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="ff329-109">webEndpointType</span></span>|<span data-ttu-id="ff329-110">Chaîne qui spécifie le type du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="ff329-110">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff329-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ff329-111">Child Elements</span></span>  
 <span data-ttu-id="ff329-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ff329-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ff329-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ff329-113">Parent Elements</span></span>  
  
|<span data-ttu-id="ff329-114">Élément</span><span class="sxs-lookup"><span data-stu-id="ff329-114">Element</span></span>|<span data-ttu-id="ff329-115">Description</span><span class="sxs-lookup"><span data-stu-id="ff329-115">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="ff329-116">Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes.</span><span class="sxs-lookup"><span data-stu-id="ff329-116">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ff329-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff329-117">See also</span></span>

- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
