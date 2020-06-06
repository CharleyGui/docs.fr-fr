---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 9f3a95fd0a39f199eaf13c7509aff22caa0e3b66
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251783"
---
# \<tokenReplayCache>
<span data-ttu-id="90163-101">Inscrit un cache de relecture de jetons avec un service ou une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="90163-101">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayCache>**  
  
## <a name="syntax"></a><span data-ttu-id="90163-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90163-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90163-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="90163-103">Attributes and Elements</span></span>  
 <span data-ttu-id="90163-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="90163-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90163-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="90163-105">Attributes</span></span>  
  
|<span data-ttu-id="90163-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="90163-106">Attribute</span></span>|<span data-ttu-id="90163-107">Description</span><span class="sxs-lookup"><span data-stu-id="90163-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="90163-108">type</span><span class="sxs-lookup"><span data-stu-id="90163-108">type</span></span>|<span data-ttu-id="90163-109">Type qui dérive de la <xref:System.IdentityModel.Tokens.TokenReplayCache> classe.</span><span class="sxs-lookup"><span data-stu-id="90163-109">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="90163-110">Pour plus d’informations sur la façon de spécifier un personnalisé `type` , consultez [références de types personnalisés].</span><span class="sxs-lookup"><span data-stu-id="90163-110">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="90163-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="90163-111">Child Elements</span></span>  
 <span data-ttu-id="90163-112">Aucune</span><span class="sxs-lookup"><span data-stu-id="90163-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="90163-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="90163-113">Parent Elements</span></span>  
  
|<span data-ttu-id="90163-114">Élément</span><span class="sxs-lookup"><span data-stu-id="90163-114">Element</span></span>|<span data-ttu-id="90163-115">Description</span><span class="sxs-lookup"><span data-stu-id="90163-115">Description</span></span>|  
|-------------|-----------------|  
|[\<caches>](caches.md)|<span data-ttu-id="90163-116">Inscrit les caches utilisés par un service ou une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="90163-116">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90163-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="90163-117">Remarks</span></span>  
 <span data-ttu-id="90163-118">Le cache de relecture de jetons est utilisé pour détecter les jetons relus.</span><span class="sxs-lookup"><span data-stu-id="90163-118">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="90163-119">La détection de relecture de jetons est activée par l' [\<tokenReplayDetection>](tokenreplaydetection.md) élément, qui spécifie également le délai d’expiration maximal pour les jetons.</span><span class="sxs-lookup"><span data-stu-id="90163-119">Token replay detection is enabled by the [\<tokenReplayDetection>](tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90163-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="90163-120">Example</span></span>  
 <span data-ttu-id="90163-121">Le code XML suivant montre la configuration d’un cache personnalisé pour la détection des jetons relus.</span><span class="sxs-lookup"><span data-stu-id="90163-121">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="90163-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90163-122">See also</span></span>

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [\<tokenReplayDetection>](tokenreplaydetection.md)
