---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: e1b40718638ded54e59743730159ea6e65a51a57
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398185"
---
# \<callbackTimeouts>
<span data-ttu-id="4ed36-101">Spécifie la valeur du délai d'attente lors du transfert de transactions du serveur vers un client dans un scénario de contrat de rappel duplex.</span><span class="sxs-lookup"><span data-stu-id="4ed36-101">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackTimeOuts>**  
  
## <a name="syntax"></a><span data-ttu-id="4ed36-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ed36-102">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="4ed36-103">Type</span><span class="sxs-lookup"><span data-stu-id="4ed36-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4ed36-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4ed36-104">Attributes and Elements</span></span>  
 <span data-ttu-id="4ed36-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4ed36-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4ed36-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="4ed36-106">Attributes</span></span>  
  
|<span data-ttu-id="4ed36-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="4ed36-107">Attribute</span></span>|<span data-ttu-id="4ed36-108">Description</span><span class="sxs-lookup"><span data-stu-id="4ed36-108">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="4ed36-109">Valeur <xref:System.TimeSpan> qui spécifie l’intervalle au cours duquel les transactions doivent être automatiquement effectuées ou arrêtées.</span><span class="sxs-lookup"><span data-stu-id="4ed36-109">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="4ed36-110">La valeur par défaut est « 00:00:00 ».</span><span class="sxs-lookup"><span data-stu-id="4ed36-110">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4ed36-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4ed36-111">Child Elements</span></span>  
 <span data-ttu-id="4ed36-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4ed36-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4ed36-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4ed36-113">Parent Elements</span></span>  
  
|<span data-ttu-id="4ed36-114">Élément</span><span class="sxs-lookup"><span data-stu-id="4ed36-114">Element</span></span>|<span data-ttu-id="4ed36-115">Description</span><span class="sxs-lookup"><span data-stu-id="4ed36-115">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="4ed36-116">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="4ed36-116">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4ed36-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ed36-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
