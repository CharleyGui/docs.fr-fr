---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: e1b40718638ded54e59743730159ea6e65a51a57
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398185"
---
# <a name="callbacktimeouts"></a><span data-ttu-id="c55e1-101">\<callbackTimeouts></span><span class="sxs-lookup"><span data-stu-id="c55e1-101">\<callbackTimeouts></span></span>
<span data-ttu-id="c55e1-102">Spécifie la valeur du délai d'attente lors du transfert de transactions du serveur vers un client dans un scénario de contrat de rappel duplex.</span><span class="sxs-lookup"><span data-stu-id="c55e1-102">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
<span data-ttu-id="c55e1-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c55e1-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c55e1-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c55e1-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c55e1-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c55e1-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="c55e1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c55e1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="c55e1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c55e1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="c55e1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<callbackTimeOuts >**</span><span class="sxs-lookup"><span data-stu-id="c55e1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackTimeOuts>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c55e1-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c55e1-109">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="c55e1-110">Type</span><span class="sxs-lookup"><span data-stu-id="c55e1-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c55e1-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c55e1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c55e1-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c55e1-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c55e1-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="c55e1-113">Attributes</span></span>  
  
|<span data-ttu-id="c55e1-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="c55e1-114">Attribute</span></span>|<span data-ttu-id="c55e1-115">Description</span><span class="sxs-lookup"><span data-stu-id="c55e1-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="c55e1-116">Valeur <xref:System.TimeSpan> qui spécifie l’intervalle au cours duquel les transactions doivent être automatiquement effectuées ou arrêtées.</span><span class="sxs-lookup"><span data-stu-id="c55e1-116">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="c55e1-117">La valeur par défaut est « 00:00:00 ».</span><span class="sxs-lookup"><span data-stu-id="c55e1-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c55e1-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c55e1-118">Child Elements</span></span>  
 <span data-ttu-id="c55e1-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c55e1-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c55e1-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c55e1-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c55e1-121">Élément</span><span class="sxs-lookup"><span data-stu-id="c55e1-121">Element</span></span>|<span data-ttu-id="c55e1-122">Description</span><span class="sxs-lookup"><span data-stu-id="c55e1-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c55e1-123">\<behavior></span><span class="sxs-lookup"><span data-stu-id="c55e1-123">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c55e1-124">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="c55e1-124">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c55e1-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c55e1-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
