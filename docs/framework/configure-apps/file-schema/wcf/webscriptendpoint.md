---
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: cc69029d9830fd12df5a4070f11847fadf4c60bb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940403"
---
# <a name="webscriptendpoint"></a><span data-ttu-id="18434-101">\<webScriptEndpoint></span><span class="sxs-lookup"><span data-stu-id="18434-101">\<webScriptEndpoint></span></span>
<span data-ttu-id="18434-102">Cet élément de configuration définit un point de terminaison standard avec une liaison [ \<WebHttpBinding >](webhttpbinding.md) fixe qui ajoute automatiquement le comportement de [ \<> enableWebScript](enablewebscript.md) .</span><span class="sxs-lookup"><span data-stu-id="18434-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](enablewebscript.md) behavior.</span></span> <span data-ttu-id="18434-103">Utilisez ce point de terminaison lorsque vous écrivez un service appelé à partir d'une application ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="18434-103">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="18434-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="18434-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="18434-105">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="18434-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18434-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18434-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18434-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="18434-107">Attributes and Elements</span></span>  
 <span data-ttu-id="18434-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="18434-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18434-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="18434-109">Attributes</span></span>  
  
|<span data-ttu-id="18434-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="18434-110">Attribute</span></span>|<span data-ttu-id="18434-111">Description</span><span class="sxs-lookup"><span data-stu-id="18434-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="18434-112">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="18434-112">webEndpointType</span></span>|<span data-ttu-id="18434-113">Chaîne qui spécifie le type du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="18434-113">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="18434-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="18434-114">Child Elements</span></span>  
 <span data-ttu-id="18434-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="18434-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="18434-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="18434-116">Parent Elements</span></span>  
  
|<span data-ttu-id="18434-117">Élément</span><span class="sxs-lookup"><span data-stu-id="18434-117">Element</span></span>|<span data-ttu-id="18434-118">Description</span><span class="sxs-lookup"><span data-stu-id="18434-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18434-119">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="18434-119">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="18434-120">Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes.</span><span class="sxs-lookup"><span data-stu-id="18434-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="18434-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18434-121">See also</span></span>

- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
