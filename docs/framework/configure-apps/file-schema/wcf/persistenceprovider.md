---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 7c4d9ae29ca1e543217d444e05a661b48e2cbb62
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400078"
---
# \<persistenceProvider>
<span data-ttu-id="c5cea-101">Indique le type d'implémentation de fournisseur de persistance à utiliser, ainsi que le délai d'expiration à utiliser pour les opérations de persistance.</span><span class="sxs-lookup"><span data-stu-id="c5cea-101">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistenceProvider>**  
  
## <a name="syntax"></a><span data-ttu-id="c5cea-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5cea-102">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5cea-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c5cea-103">Attributes and Elements</span></span>  
 <span data-ttu-id="c5cea-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c5cea-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5cea-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="c5cea-105">Attributes</span></span>  
  
|<span data-ttu-id="c5cea-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="c5cea-106">Attribute</span></span>|<span data-ttu-id="c5cea-107">Description</span><span class="sxs-lookup"><span data-stu-id="c5cea-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c5cea-108">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="c5cea-108">persistenceOperationTimeout</span></span>|<span data-ttu-id="c5cea-109">Valeur <xref:System.TimeSpan> indiquant le délai d'expiration utilisé pour les opérations de persistance.</span><span class="sxs-lookup"><span data-stu-id="c5cea-109">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="c5cea-110">La valeur par défaut est « 00:00:30 ».</span><span class="sxs-lookup"><span data-stu-id="c5cea-110">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="c5cea-111">type</span><span class="sxs-lookup"><span data-stu-id="c5cea-111">type</span></span>|<span data-ttu-id="c5cea-112">Chaîne indiquant le type à utiliser pour la fabrique de fournisseurs de persistance.</span><span class="sxs-lookup"><span data-stu-id="c5cea-112">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5cea-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c5cea-113">Child Elements</span></span>  
 <span data-ttu-id="c5cea-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c5cea-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c5cea-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c5cea-115">Parent Elements</span></span>  
  
|<span data-ttu-id="c5cea-116">Élément</span><span class="sxs-lookup"><span data-stu-id="c5cea-116">Element</span></span>|<span data-ttu-id="c5cea-117">Description</span><span class="sxs-lookup"><span data-stu-id="c5cea-117">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c5cea-118">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="c5cea-118">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5cea-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="c5cea-119">Remarks</span></span>  
 <span data-ttu-id="c5cea-120">Cet élément spécifie le fournisseur de persistance à utiliser pour sérialiser l'état d'un service WCF.</span><span class="sxs-lookup"><span data-stu-id="c5cea-120">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="c5cea-121">Il doit être utilisé avec le `wsHttpContextBinding` qui transmet les informations d'état dans les en-têtes HTTP.</span><span class="sxs-lookup"><span data-stu-id="c5cea-121">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5cea-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5cea-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
