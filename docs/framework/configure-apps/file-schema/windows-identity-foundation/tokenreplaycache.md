---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 9f3a95fd0a39f199eaf13c7509aff22caa0e3b66
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251783"
---
# <a name="tokenreplaycache"></a><span data-ttu-id="45f85-101">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="45f85-101">\<tokenReplayCache></span></span>
<span data-ttu-id="45f85-102">Inscrit un cache de relecture de jetons avec un service ou une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="45f85-102">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
<span data-ttu-id="45f85-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="45f85-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="45f85-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="45f85-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="45f85-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="45f85-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="45f85-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<caches >** ](caches.md)</span><span class="sxs-lookup"><span data-stu-id="45f85-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)</span></span>\
<span data-ttu-id="45f85-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<tokenReplayCache >**</span><span class="sxs-lookup"><span data-stu-id="45f85-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayCache>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45f85-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45f85-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <tokenReplayCache type=xs:string>  
      </tokenReplayCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45f85-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="45f85-109">Attributes and Elements</span></span>  
 <span data-ttu-id="45f85-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="45f85-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45f85-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="45f85-111">Attributes</span></span>  
  
|<span data-ttu-id="45f85-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="45f85-112">Attribute</span></span>|<span data-ttu-id="45f85-113">Description</span><span class="sxs-lookup"><span data-stu-id="45f85-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="45f85-114">type</span><span class="sxs-lookup"><span data-stu-id="45f85-114">type</span></span>|<span data-ttu-id="45f85-115">Type qui dérive de la <xref:System.IdentityModel.Tokens.TokenReplayCache> classe.</span><span class="sxs-lookup"><span data-stu-id="45f85-115">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="45f85-116">Pour plus d’informations sur la façon de spécifier `type`un personnalisé, consultez [références de types personnalisés].</span><span class="sxs-lookup"><span data-stu-id="45f85-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="45f85-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="45f85-117">Child Elements</span></span>  
 <span data-ttu-id="45f85-118">Aucun</span><span class="sxs-lookup"><span data-stu-id="45f85-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="45f85-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="45f85-119">Parent Elements</span></span>  
  
|<span data-ttu-id="45f85-120">Élément</span><span class="sxs-lookup"><span data-stu-id="45f85-120">Element</span></span>|<span data-ttu-id="45f85-121">Description</span><span class="sxs-lookup"><span data-stu-id="45f85-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="45f85-122">\<caches></span><span class="sxs-lookup"><span data-stu-id="45f85-122">\<caches></span></span>](caches.md)|<span data-ttu-id="45f85-123">Inscrit les caches utilisés par un service ou une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="45f85-123">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45f85-124">Notes</span><span class="sxs-lookup"><span data-stu-id="45f85-124">Remarks</span></span>  
 <span data-ttu-id="45f85-125">Le cache de relecture de jetons est utilisé pour détecter les jetons relus.</span><span class="sxs-lookup"><span data-stu-id="45f85-125">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="45f85-126">La détection de relecture de jetons est activée par l' [ \<élément tokenReplayDetection >](tokenreplaydetection.md) , qui spécifie également le délai d’expiration maximal pour les jetons.</span><span class="sxs-lookup"><span data-stu-id="45f85-126">Token replay detection is enabled by the [\<tokenReplayDetection>](tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45f85-127">Exemples</span><span class="sxs-lookup"><span data-stu-id="45f85-127">Example</span></span>  
 <span data-ttu-id="45f85-128">Le code XML suivant montre la configuration d’un cache personnalisé pour la détection des jetons relus.</span><span class="sxs-lookup"><span data-stu-id="45f85-128">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="45f85-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45f85-129">See also</span></span>

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [<span data-ttu-id="45f85-130">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="45f85-130">\<tokenReplayDetection></span></span>](tokenreplaydetection.md)
