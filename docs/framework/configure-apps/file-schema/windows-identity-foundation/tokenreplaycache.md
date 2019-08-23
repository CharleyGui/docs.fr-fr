---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 5747a4cfa93118dd41292904b168bbef02fec415
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944076"
---
# <a name="tokenreplaycache"></a><span data-ttu-id="c96b8-101">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="c96b8-101">\<tokenReplayCache></span></span>
<span data-ttu-id="c96b8-102">Inscrit un cache de relecture de jetons avec un service ou une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="c96b8-102">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="c96b8-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="c96b8-103">\<system.identityModel></span></span>  
<span data-ttu-id="c96b8-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="c96b8-104">\<identityConfiguration></span></span>  
<span data-ttu-id="c96b8-105">\<caches></span><span class="sxs-lookup"><span data-stu-id="c96b8-105">\<caches></span></span>  
<span data-ttu-id="c96b8-106">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="c96b8-106">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c96b8-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c96b8-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c96b8-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c96b8-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c96b8-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c96b8-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c96b8-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="c96b8-110">Attributes</span></span>  
  
|<span data-ttu-id="c96b8-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="c96b8-111">Attribute</span></span>|<span data-ttu-id="c96b8-112">Description</span><span class="sxs-lookup"><span data-stu-id="c96b8-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c96b8-113">type</span><span class="sxs-lookup"><span data-stu-id="c96b8-113">type</span></span>|<span data-ttu-id="c96b8-114">Type qui dérive de la <xref:System.IdentityModel.Tokens.TokenReplayCache> classe.</span><span class="sxs-lookup"><span data-stu-id="c96b8-114">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="c96b8-115">Pour plus d’informations sur la façon de spécifier `type`un personnalisé, consultez [références de types personnalisés].</span><span class="sxs-lookup"><span data-stu-id="c96b8-115">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="c96b8-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c96b8-116">Child Elements</span></span>  
 <span data-ttu-id="c96b8-117">Aucun</span><span class="sxs-lookup"><span data-stu-id="c96b8-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c96b8-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c96b8-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c96b8-119">Élément</span><span class="sxs-lookup"><span data-stu-id="c96b8-119">Element</span></span>|<span data-ttu-id="c96b8-120">Description</span><span class="sxs-lookup"><span data-stu-id="c96b8-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c96b8-121">\<caches></span><span class="sxs-lookup"><span data-stu-id="c96b8-121">\<caches></span></span>](caches.md)|<span data-ttu-id="c96b8-122">Inscrit les caches utilisés par un service ou une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="c96b8-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c96b8-123">Notes</span><span class="sxs-lookup"><span data-stu-id="c96b8-123">Remarks</span></span>  
 <span data-ttu-id="c96b8-124">Le cache de relecture de jetons est utilisé pour détecter les jetons relus.</span><span class="sxs-lookup"><span data-stu-id="c96b8-124">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="c96b8-125">La détection de relecture de jetons est activée par l' [ \<élément tokenReplayDetection >](tokenreplaydetection.md) , qui spécifie également le délai d’expiration maximal pour les jetons.</span><span class="sxs-lookup"><span data-stu-id="c96b8-125">Token replay detection is enabled by the [\<tokenReplayDetection>](tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c96b8-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="c96b8-126">Example</span></span>  
 <span data-ttu-id="c96b8-127">Le code XML suivant montre la configuration d’un cache personnalisé pour la détection des jetons relus.</span><span class="sxs-lookup"><span data-stu-id="c96b8-127">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c96b8-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c96b8-128">See also</span></span>

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [<span data-ttu-id="c96b8-129">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="c96b8-129">\<tokenReplayDetection></span></span>](tokenreplaydetection.md)
