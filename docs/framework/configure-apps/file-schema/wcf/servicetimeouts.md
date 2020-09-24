---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: 92d3de42daf6f7baf288e3e74242381a60e76618
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153597"
---
# \<serviceTimeouts>

<span data-ttu-id="7d6fe-101">Spécifie le délai d'attente pour un service.</span><span class="sxs-lookup"><span data-stu-id="7d6fe-101">Specifies the timeout for a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTimeouts>**  
  
## <a name="syntax"></a><span data-ttu-id="7d6fe-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d6fe-102">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="7d6fe-103">Type</span><span class="sxs-lookup"><span data-stu-id="7d6fe-103">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d6fe-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7d6fe-104">Attributes and Elements</span></span>  

 <span data-ttu-id="7d6fe-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7d6fe-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d6fe-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="7d6fe-106">Attributes</span></span>  
  
|<span data-ttu-id="7d6fe-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="7d6fe-107">Attribute</span></span>|<span data-ttu-id="7d6fe-108">Description</span><span class="sxs-lookup"><span data-stu-id="7d6fe-108">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="7d6fe-109">Valeur <xref:System.TimeSpan> qui spécifie l’intervalle de temps pour le transfert d’une transaction du client au serveur.</span><span class="sxs-lookup"><span data-stu-id="7d6fe-109">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="7d6fe-110">La valeur par défaut est « 00:00:00 ».</span><span class="sxs-lookup"><span data-stu-id="7d6fe-110">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7d6fe-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7d6fe-111">Child Elements</span></span>  

 <span data-ttu-id="7d6fe-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7d6fe-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7d6fe-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7d6fe-113">Parent Elements</span></span>  
  
|<span data-ttu-id="7d6fe-114">Élément</span><span class="sxs-lookup"><span data-stu-id="7d6fe-114">Element</span></span>|<span data-ttu-id="7d6fe-115">Description</span><span class="sxs-lookup"><span data-stu-id="7d6fe-115">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="7d6fe-116">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="7d6fe-116">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7d6fe-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d6fe-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
