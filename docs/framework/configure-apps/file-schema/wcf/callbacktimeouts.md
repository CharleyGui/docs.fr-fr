---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: 98523489aacebf910bcf5d81c479819183887dff
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198884"
---
# \<callbackTimeouts>

<span data-ttu-id="89367-101">Spécifie la valeur du délai d'attente lors du transfert de transactions du serveur vers un client dans un scénario de contrat de rappel duplex.</span><span class="sxs-lookup"><span data-stu-id="89367-101">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackTimeOuts>**  
  
## <a name="syntax"></a><span data-ttu-id="89367-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89367-102">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="89367-103">Type</span><span class="sxs-lookup"><span data-stu-id="89367-103">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89367-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="89367-104">Attributes and Elements</span></span>  

 <span data-ttu-id="89367-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="89367-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89367-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="89367-106">Attributes</span></span>  
  
|<span data-ttu-id="89367-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="89367-107">Attribute</span></span>|<span data-ttu-id="89367-108">Description</span><span class="sxs-lookup"><span data-stu-id="89367-108">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="89367-109">Valeur <xref:System.TimeSpan> qui spécifie l’intervalle au cours duquel les transactions doivent être automatiquement effectuées ou arrêtées.</span><span class="sxs-lookup"><span data-stu-id="89367-109">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="89367-110">La valeur par défaut est « 00:00:00 ».</span><span class="sxs-lookup"><span data-stu-id="89367-110">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89367-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="89367-111">Child Elements</span></span>  

 <span data-ttu-id="89367-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="89367-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="89367-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="89367-113">Parent Elements</span></span>  
  
|<span data-ttu-id="89367-114">Élément</span><span class="sxs-lookup"><span data-stu-id="89367-114">Element</span></span>|<span data-ttu-id="89367-115">Description</span><span class="sxs-lookup"><span data-stu-id="89367-115">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="89367-116">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="89367-116">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="89367-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89367-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
