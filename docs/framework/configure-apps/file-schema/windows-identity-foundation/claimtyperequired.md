---
title: <claimTypeRequired>
ms.date: 03/30/2017
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
author: BrucePerlerMS
ms.openlocfilehash: 1c40c5e4b4a24a3c1bbd6e096f12b7b044331c88
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252052"
---
# <a name="claimtyperequired"></a><span data-ttu-id="0ea4e-101">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="0ea4e-101">\<claimTypeRequired></span></span>
<span data-ttu-id="0ea4e-102">Spécifie l’ensemble des revendications requises pour les jetons de sécurité entrants.</span><span class="sxs-lookup"><span data-stu-id="0ea4e-102">Specifies the set of required claims for incoming security tokens.</span></span>  
  
<span data-ttu-id="0ea4e-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0ea4e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0ea4e-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="0ea4e-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="0ea4e-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="0ea4e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="0ea4e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<claimTypeRequired >**</span><span class="sxs-lookup"><span data-stu-id="0ea4e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimTypeRequired>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ea4e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ea4e-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ea4e-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0ea4e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0ea4e-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0ea4e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ea4e-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="0ea4e-110">Attributes</span></span>  
 <span data-ttu-id="0ea4e-111">Aucun</span><span class="sxs-lookup"><span data-stu-id="0ea4e-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0ea4e-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0ea4e-112">Child Elements</span></span>  
  
|<span data-ttu-id="0ea4e-113">Élément</span><span class="sxs-lookup"><span data-stu-id="0ea4e-113">Element</span></span>|<span data-ttu-id="0ea4e-114">Description</span><span class="sxs-lookup"><span data-stu-id="0ea4e-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0ea4e-115">\<claimType></span><span class="sxs-lookup"><span data-stu-id="0ea4e-115">\<claimType></span></span>](claimtype.md)|<span data-ttu-id="0ea4e-116">Spécifie une revendication unique ou facultative pour les jetons de sécurité entrants.</span><span class="sxs-lookup"><span data-stu-id="0ea4e-116">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0ea4e-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0ea4e-117">Parent Elements</span></span>  
  
|<span data-ttu-id="0ea4e-118">Élément</span><span class="sxs-lookup"><span data-stu-id="0ea4e-118">Element</span></span>|<span data-ttu-id="0ea4e-119">Description</span><span class="sxs-lookup"><span data-stu-id="0ea4e-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0ea4e-120">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="0ea4e-120">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="0ea4e-121">Spécifie les paramètres d’identité au niveau du service.</span><span class="sxs-lookup"><span data-stu-id="0ea4e-121">Specifies service-level identity settings.</span></span>|
