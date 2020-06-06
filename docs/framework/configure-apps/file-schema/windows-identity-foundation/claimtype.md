---
title: <claimType>
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: a46e9129bd27319abb4d7519444568af622170fc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252069"
---
# \<claimType>
<span data-ttu-id="88111-101">Spécifie une revendication unique ou facultative pour les jetons de sécurité entrants.</span><span class="sxs-lookup"><span data-stu-id="88111-101">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequired>**](claimtyperequired.md)\  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimType>**  
  
## <a name="syntax"></a><span data-ttu-id="88111-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88111-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="88111-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="88111-103">Attributes and Elements</span></span>  
 <span data-ttu-id="88111-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="88111-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="88111-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="88111-105">Attributes</span></span>  
  
|<span data-ttu-id="88111-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="88111-106">Attribute</span></span>|<span data-ttu-id="88111-107">Description</span><span class="sxs-lookup"><span data-stu-id="88111-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="88111-108">type</span><span class="sxs-lookup"><span data-stu-id="88111-108">type</span></span>|<span data-ttu-id="88111-109">Type de revendication.</span><span class="sxs-lookup"><span data-stu-id="88111-109">The claim type.</span></span> <span data-ttu-id="88111-110">Généralement un URI.</span><span class="sxs-lookup"><span data-stu-id="88111-110">Typically a URI.</span></span> <span data-ttu-id="88111-111">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="88111-111">Required.</span></span>|  
|<span data-ttu-id="88111-112">facultatif</span><span class="sxs-lookup"><span data-stu-id="88111-112">optional</span></span>|<span data-ttu-id="88111-113">Valeur booléenne qui spécifie si le type de revendication est facultatif.</span><span class="sxs-lookup"><span data-stu-id="88111-113">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="88111-114">facultatif.</span><span class="sxs-lookup"><span data-stu-id="88111-114">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="88111-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="88111-115">Child Elements</span></span>  
 <span data-ttu-id="88111-116">Aucune</span><span class="sxs-lookup"><span data-stu-id="88111-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="88111-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="88111-117">Parent Elements</span></span>  
  
|<span data-ttu-id="88111-118">Élément</span><span class="sxs-lookup"><span data-stu-id="88111-118">Element</span></span>|<span data-ttu-id="88111-119">Description</span><span class="sxs-lookup"><span data-stu-id="88111-119">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequired>](claimtyperequired.md)|<span data-ttu-id="88111-120">Spécifie l’ensemble des revendications requises pour les jetons de sécurité entrants.</span><span class="sxs-lookup"><span data-stu-id="88111-120">Specifies the set of required claims for incoming security tokens.</span></span>|
