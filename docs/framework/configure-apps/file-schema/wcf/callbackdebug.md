---
title: <callbackDebug>
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 92a8fa83b5cf5f429278ac8edc8439b627839aad
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400567"
---
# <a name="callbackdebug"></a><span data-ttu-id="e3cf3-101">\<callbackDebug></span><span class="sxs-lookup"><span data-stu-id="e3cf3-101">\<callbackDebug></span></span>
<span data-ttu-id="e3cf3-102">Spécifie le débogage de service pour un objet de rappel Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e3cf3-102">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
<span data-ttu-id="e3cf3-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e3cf3-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e3cf3-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e3cf3-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e3cf3-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e3cf3-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="e3cf3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e3cf3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="e3cf3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e3cf3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="e3cf3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<callbackDebug >**</span><span class="sxs-lookup"><span data-stu-id="e3cf3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackDebug>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3cf3-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3cf3-109">Syntax</span></span>  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a><span data-ttu-id="e3cf3-110">Type</span><span class="sxs-lookup"><span data-stu-id="e3cf3-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3cf3-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e3cf3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e3cf3-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e3cf3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3cf3-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="e3cf3-113">Attributes</span></span>  
  
|<span data-ttu-id="e3cf3-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="e3cf3-114">Attribute</span></span>|<span data-ttu-id="e3cf3-115">Description</span><span class="sxs-lookup"><span data-stu-id="e3cf3-115">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="e3cf3-116">Valeur qui spécifie si les objets de rappel client retournent au service des informations sur les exceptions managées dans les erreurs SOAP.</span><span class="sxs-lookup"><span data-stu-id="e3cf3-116">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="e3cf3-117">Si vous définissez cet attribut par programme à `true`, vous pouvez activer le retour du flux d'informations sur les exceptions managées dans un objet de rappel client, à des fins de débogage.</span><span class="sxs-lookup"><span data-stu-id="e3cf3-117">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="e3cf3-118">**Attention :**  Le retour des informations sur les exceptions managées aux clients peut entraîner un problème de sécurité.</span><span class="sxs-lookup"><span data-stu-id="e3cf3-118">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="e3cf3-119">En effet, les détails de l'exception exposent des informations relatives à l'implémentation d'un service interne qui peuvent être utilisées par des clients non autorisés.</span><span class="sxs-lookup"><span data-stu-id="e3cf3-119">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e3cf3-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e3cf3-120">Child Elements</span></span>  
 <span data-ttu-id="e3cf3-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e3cf3-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e3cf3-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e3cf3-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e3cf3-123">Élément</span><span class="sxs-lookup"><span data-stu-id="e3cf3-123">Element</span></span>|<span data-ttu-id="e3cf3-124">Description</span><span class="sxs-lookup"><span data-stu-id="e3cf3-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e3cf3-125">\<behavior></span><span class="sxs-lookup"><span data-stu-id="e3cf3-125">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="e3cf3-126">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="e3cf3-126">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e3cf3-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3cf3-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
