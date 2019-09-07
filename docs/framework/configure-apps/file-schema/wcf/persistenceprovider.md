---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 7c4d9ae29ca1e543217d444e05a661b48e2cbb62
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400078"
---
# <a name="persistenceprovider"></a><span data-ttu-id="ed8c4-101">\<persistenceProvider></span><span class="sxs-lookup"><span data-stu-id="ed8c4-101">\<persistenceProvider></span></span>
<span data-ttu-id="ed8c4-102">Indique le type d'implémentation de fournisseur de persistance à utiliser, ainsi que le délai d'expiration à utiliser pour les opérations de persistance.</span><span class="sxs-lookup"><span data-stu-id="ed8c4-102">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
<span data-ttu-id="ed8c4-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ed8c4-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ed8c4-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ed8c4-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ed8c4-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ed8c4-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="ed8c4-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ed8c4-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="ed8c4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ed8c4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="ed8c4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<persistenceProvider >**</span><span class="sxs-lookup"><span data-stu-id="ed8c4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistenceProvider>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed8c4-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed8c4-109">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ed8c4-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ed8c4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ed8c4-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ed8c4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ed8c4-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="ed8c4-112">Attributes</span></span>  
  
|<span data-ttu-id="ed8c4-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="ed8c4-113">Attribute</span></span>|<span data-ttu-id="ed8c4-114">Description</span><span class="sxs-lookup"><span data-stu-id="ed8c4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ed8c4-115">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="ed8c4-115">persistenceOperationTimeout</span></span>|<span data-ttu-id="ed8c4-116">Valeur <xref:System.TimeSpan> indiquant le délai d'expiration utilisé pour les opérations de persistance.</span><span class="sxs-lookup"><span data-stu-id="ed8c4-116">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="ed8c4-117">La valeur par défaut est « 00:00:30 ».</span><span class="sxs-lookup"><span data-stu-id="ed8c4-117">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="ed8c4-118">type</span><span class="sxs-lookup"><span data-stu-id="ed8c4-118">type</span></span>|<span data-ttu-id="ed8c4-119">Chaîne indiquant le type à utiliser pour la fabrique de fournisseurs de persistance.</span><span class="sxs-lookup"><span data-stu-id="ed8c4-119">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ed8c4-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ed8c4-120">Child Elements</span></span>  
 <span data-ttu-id="ed8c4-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ed8c4-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ed8c4-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ed8c4-122">Parent Elements</span></span>  
  
|<span data-ttu-id="ed8c4-123">Élément</span><span class="sxs-lookup"><span data-stu-id="ed8c4-123">Element</span></span>|<span data-ttu-id="ed8c4-124">Description</span><span class="sxs-lookup"><span data-stu-id="ed8c4-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ed8c4-125">\<behavior></span><span class="sxs-lookup"><span data-stu-id="ed8c4-125">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="ed8c4-126">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="ed8c4-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed8c4-127">Notes</span><span class="sxs-lookup"><span data-stu-id="ed8c4-127">Remarks</span></span>  
 <span data-ttu-id="ed8c4-128">Cet élément spécifie le fournisseur de persistance à utiliser pour sérialiser l'état d'un service WCF.</span><span class="sxs-lookup"><span data-stu-id="ed8c4-128">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="ed8c4-129">Il doit être utilisé avec le `wsHttpContextBinding` qui transmet les informations d'état dans les en-têtes HTTP.</span><span class="sxs-lookup"><span data-stu-id="ed8c4-129">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed8c4-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed8c4-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
