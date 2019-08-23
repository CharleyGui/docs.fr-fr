---
title: <claimType>
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: 4253aec961b812b6893ee201861d2ab38048032a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942878"
---
# <a name="claimtype"></a><span data-ttu-id="52ce3-101">\<claimType></span><span class="sxs-lookup"><span data-stu-id="52ce3-101">\<claimType></span></span>
<span data-ttu-id="52ce3-102">Spécifie une revendication unique ou facultative pour les jetons de sécurité entrants.</span><span class="sxs-lookup"><span data-stu-id="52ce3-102">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="52ce3-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="52ce3-103">\<system.identityModel></span></span>  
<span data-ttu-id="52ce3-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="52ce3-104">\<identityConfiguration></span></span>  
<span data-ttu-id="52ce3-105">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="52ce3-105">\<claimTypeRequired></span></span>  
<span data-ttu-id="52ce3-106">\<claimType></span><span class="sxs-lookup"><span data-stu-id="52ce3-106">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52ce3-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52ce3-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
      <claimType type=URI optional=xs:boolean >  
      </claimType>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="52ce3-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="52ce3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="52ce3-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="52ce3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="52ce3-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="52ce3-110">Attributes</span></span>  
  
|<span data-ttu-id="52ce3-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="52ce3-111">Attribute</span></span>|<span data-ttu-id="52ce3-112">Description</span><span class="sxs-lookup"><span data-stu-id="52ce3-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="52ce3-113">type</span><span class="sxs-lookup"><span data-stu-id="52ce3-113">type</span></span>|<span data-ttu-id="52ce3-114">Type de revendication.</span><span class="sxs-lookup"><span data-stu-id="52ce3-114">The claim type.</span></span> <span data-ttu-id="52ce3-115">Généralement un URI.</span><span class="sxs-lookup"><span data-stu-id="52ce3-115">Typically a URI.</span></span> <span data-ttu-id="52ce3-116">Requis.</span><span class="sxs-lookup"><span data-stu-id="52ce3-116">Required.</span></span>|  
|<span data-ttu-id="52ce3-117">facultatif</span><span class="sxs-lookup"><span data-stu-id="52ce3-117">optional</span></span>|<span data-ttu-id="52ce3-118">Valeur booléenne qui spécifie si le type de revendication est facultatif.</span><span class="sxs-lookup"><span data-stu-id="52ce3-118">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="52ce3-119">facultatif.</span><span class="sxs-lookup"><span data-stu-id="52ce3-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="52ce3-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="52ce3-120">Child Elements</span></span>  
 <span data-ttu-id="52ce3-121">Aucun</span><span class="sxs-lookup"><span data-stu-id="52ce3-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="52ce3-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="52ce3-122">Parent Elements</span></span>  
  
|<span data-ttu-id="52ce3-123">Élément</span><span class="sxs-lookup"><span data-stu-id="52ce3-123">Element</span></span>|<span data-ttu-id="52ce3-124">Description</span><span class="sxs-lookup"><span data-stu-id="52ce3-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="52ce3-125">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="52ce3-125">\<claimTypeRequired></span></span>](claimtyperequired.md)|<span data-ttu-id="52ce3-126">Spécifie l’ensemble des revendications requises pour les jetons de sécurité entrants.</span><span class="sxs-lookup"><span data-stu-id="52ce3-126">Specifies the set of required claims for incoming security tokens.</span></span>|
