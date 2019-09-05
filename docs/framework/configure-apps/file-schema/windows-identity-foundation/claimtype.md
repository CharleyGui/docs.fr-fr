---
title: <claimType>
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: a46e9129bd27319abb4d7519444568af622170fc
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252069"
---
# <a name="claimtype"></a><span data-ttu-id="70dd6-101">\<claimType></span><span class="sxs-lookup"><span data-stu-id="70dd6-101">\<claimType></span></span>
<span data-ttu-id="70dd6-102">Spécifie une revendication unique ou facultative pour les jetons de sécurité entrants.</span><span class="sxs-lookup"><span data-stu-id="70dd6-102">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
<span data-ttu-id="70dd6-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="70dd6-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="70dd6-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="70dd6-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="70dd6-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="70dd6-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="70dd6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<claimTypeRequired >** ](claimtyperequired.md)</span><span class="sxs-lookup"><span data-stu-id="70dd6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequired>**](claimtyperequired.md)</span></span>\  
<span data-ttu-id="70dd6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> claimType**</span><span class="sxs-lookup"><span data-stu-id="70dd6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70dd6-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70dd6-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70dd6-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="70dd6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="70dd6-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="70dd6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70dd6-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="70dd6-111">Attributes</span></span>  
  
|<span data-ttu-id="70dd6-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="70dd6-112">Attribute</span></span>|<span data-ttu-id="70dd6-113">Description</span><span class="sxs-lookup"><span data-stu-id="70dd6-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="70dd6-114">type</span><span class="sxs-lookup"><span data-stu-id="70dd6-114">type</span></span>|<span data-ttu-id="70dd6-115">Type de revendication.</span><span class="sxs-lookup"><span data-stu-id="70dd6-115">The claim type.</span></span> <span data-ttu-id="70dd6-116">Généralement un URI.</span><span class="sxs-lookup"><span data-stu-id="70dd6-116">Typically a URI.</span></span> <span data-ttu-id="70dd6-117">Requis.</span><span class="sxs-lookup"><span data-stu-id="70dd6-117">Required.</span></span>|  
|<span data-ttu-id="70dd6-118">facultatif</span><span class="sxs-lookup"><span data-stu-id="70dd6-118">optional</span></span>|<span data-ttu-id="70dd6-119">Valeur booléenne qui spécifie si le type de revendication est facultatif.</span><span class="sxs-lookup"><span data-stu-id="70dd6-119">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="70dd6-120">facultatif.</span><span class="sxs-lookup"><span data-stu-id="70dd6-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="70dd6-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="70dd6-121">Child Elements</span></span>  
 <span data-ttu-id="70dd6-122">Aucun</span><span class="sxs-lookup"><span data-stu-id="70dd6-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="70dd6-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="70dd6-123">Parent Elements</span></span>  
  
|<span data-ttu-id="70dd6-124">Élément</span><span class="sxs-lookup"><span data-stu-id="70dd6-124">Element</span></span>|<span data-ttu-id="70dd6-125">Description</span><span class="sxs-lookup"><span data-stu-id="70dd6-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70dd6-126">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="70dd6-126">\<claimTypeRequired></span></span>](claimtyperequired.md)|<span data-ttu-id="70dd6-127">Spécifie l’ensemble des revendications requises pour les jetons de sécurité entrants.</span><span class="sxs-lookup"><span data-stu-id="70dd6-127">Specifies the set of required claims for incoming security tokens.</span></span>|
