---
title: <claimTypeRequired>
ms.date: 03/30/2017
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
author: BrucePerlerMS
ms.openlocfilehash: a86265ba3963ebc8bea880befbcf80345529116d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203850"
---
# \<claimTypeRequired>

<span data-ttu-id="185ba-101">Spécifie l’ensemble des revendications requises pour les jetons de sécurité entrants.</span><span class="sxs-lookup"><span data-stu-id="185ba-101">Specifies the set of required claims for incoming security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimTypeRequired>**  
  
## <a name="syntax"></a><span data-ttu-id="185ba-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="185ba-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="185ba-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="185ba-103">Attributes and Elements</span></span>  

 <span data-ttu-id="185ba-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="185ba-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="185ba-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="185ba-105">Attributes</span></span>  

 <span data-ttu-id="185ba-106">None</span><span class="sxs-lookup"><span data-stu-id="185ba-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="185ba-107">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="185ba-107">Child Elements</span></span>  
  
|<span data-ttu-id="185ba-108">Élément</span><span class="sxs-lookup"><span data-stu-id="185ba-108">Element</span></span>|<span data-ttu-id="185ba-109">Description</span><span class="sxs-lookup"><span data-stu-id="185ba-109">Description</span></span>|  
|-------------|-----------------|  
|[\<claimType>](claimtype.md)|<span data-ttu-id="185ba-110">Spécifie une revendication unique ou facultative pour les jetons de sécurité entrants.</span><span class="sxs-lookup"><span data-stu-id="185ba-110">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="185ba-111">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="185ba-111">Parent Elements</span></span>  
  
|<span data-ttu-id="185ba-112">Élément</span><span class="sxs-lookup"><span data-stu-id="185ba-112">Element</span></span>|<span data-ttu-id="185ba-113">Description</span><span class="sxs-lookup"><span data-stu-id="185ba-113">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="185ba-114">Spécifie les paramètres d’identité au niveau du service.</span><span class="sxs-lookup"><span data-stu-id="185ba-114">Specifies service-level identity settings.</span></span>|
