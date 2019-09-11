---
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: b4bc33cf8ff4e703973efe7df49e9f1d2189302e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854817"
---
# <a name="webscriptendpoint"></a><span data-ttu-id="84c49-101">\<webScriptEndpoint></span><span class="sxs-lookup"><span data-stu-id="84c49-101">\<webScriptEndpoint></span></span>
<span data-ttu-id="84c49-102">Cet élément de configuration définit un point de terminaison standard avec une liaison [ \<WebHttpBinding >](webhttpbinding.md) fixe qui ajoute automatiquement le comportement de [ \<> enableWebScript](enablewebscript.md) .</span><span class="sxs-lookup"><span data-stu-id="84c49-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](enablewebscript.md) behavior.</span></span> <span data-ttu-id="84c49-103">Utilisez ce point de terminaison lorsque vous écrivez un service appelé à partir d'une application ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="84c49-103">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="84c49-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="84c49-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="84c49-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="84c49-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="84c49-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="84c49-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="84c49-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<webScriptEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="84c49-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webScriptEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84c49-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84c49-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84c49-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="84c49-109">Attributes and Elements</span></span>  
 <span data-ttu-id="84c49-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="84c49-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84c49-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="84c49-111">Attributes</span></span>  
  
|<span data-ttu-id="84c49-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="84c49-112">Attribute</span></span>|<span data-ttu-id="84c49-113">Description</span><span class="sxs-lookup"><span data-stu-id="84c49-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="84c49-114">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="84c49-114">webEndpointType</span></span>|<span data-ttu-id="84c49-115">Chaîne qui spécifie le type du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="84c49-115">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="84c49-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="84c49-116">Child Elements</span></span>  
 <span data-ttu-id="84c49-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="84c49-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="84c49-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="84c49-118">Parent Elements</span></span>  
  
|<span data-ttu-id="84c49-119">Élément</span><span class="sxs-lookup"><span data-stu-id="84c49-119">Element</span></span>|<span data-ttu-id="84c49-120">Description</span><span class="sxs-lookup"><span data-stu-id="84c49-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84c49-121">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="84c49-121">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="84c49-122">Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes.</span><span class="sxs-lookup"><span data-stu-id="84c49-122">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="84c49-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84c49-123">See also</span></span>

- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
