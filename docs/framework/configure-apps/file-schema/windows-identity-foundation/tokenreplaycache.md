---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 5e695bb56b59da40ce9e83f9f4f77d0d22d0b40f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202420"
---
# \<tokenReplayCache>

<span data-ttu-id="5f6b1-101">Inscrit un cache de relecture de jetons avec un service ou une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="5f6b1-101">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayCache>**  
  
## <a name="syntax"></a><span data-ttu-id="5f6b1-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f6b1-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f6b1-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5f6b1-103">Attributes and Elements</span></span>  

 <span data-ttu-id="5f6b1-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5f6b1-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f6b1-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="5f6b1-105">Attributes</span></span>  
  
|<span data-ttu-id="5f6b1-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="5f6b1-106">Attribute</span></span>|<span data-ttu-id="5f6b1-107">Description</span><span class="sxs-lookup"><span data-stu-id="5f6b1-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5f6b1-108">type</span><span class="sxs-lookup"><span data-stu-id="5f6b1-108">type</span></span>|<span data-ttu-id="5f6b1-109">Type qui dérive de la <xref:System.IdentityModel.Tokens.TokenReplayCache> classe.</span><span class="sxs-lookup"><span data-stu-id="5f6b1-109">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="5f6b1-110">Pour plus d’informations sur la façon de spécifier un personnalisé `type` , consultez [références de types personnalisés].</span><span class="sxs-lookup"><span data-stu-id="5f6b1-110">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="5f6b1-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5f6b1-111">Child Elements</span></span>  

 <span data-ttu-id="5f6b1-112">None</span><span class="sxs-lookup"><span data-stu-id="5f6b1-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5f6b1-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5f6b1-113">Parent Elements</span></span>  
  
|<span data-ttu-id="5f6b1-114">Élément</span><span class="sxs-lookup"><span data-stu-id="5f6b1-114">Element</span></span>|<span data-ttu-id="5f6b1-115">Description</span><span class="sxs-lookup"><span data-stu-id="5f6b1-115">Description</span></span>|  
|-------------|-----------------|  
|[\<caches>](caches.md)|<span data-ttu-id="5f6b1-116">Inscrit les caches utilisés par un service ou une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="5f6b1-116">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f6b1-117">Notes</span><span class="sxs-lookup"><span data-stu-id="5f6b1-117">Remarks</span></span>  

 <span data-ttu-id="5f6b1-118">Le cache de relecture de jetons est utilisé pour détecter les jetons relus.</span><span class="sxs-lookup"><span data-stu-id="5f6b1-118">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="5f6b1-119">La détection de relecture de jetons est activée par l' [\<tokenReplayDetection>](tokenreplaydetection.md) élément, qui spécifie également le délai d’expiration maximal pour les jetons.</span><span class="sxs-lookup"><span data-stu-id="5f6b1-119">Token replay detection is enabled by the [\<tokenReplayDetection>](tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f6b1-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="5f6b1-120">Example</span></span>  

 <span data-ttu-id="5f6b1-121">Le code XML suivant montre la configuration d’un cache personnalisé pour la détection des jetons relus.</span><span class="sxs-lookup"><span data-stu-id="5f6b1-121">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5f6b1-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f6b1-122">See also</span></span>

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [\<tokenReplayDetection>](tokenreplaydetection.md)
