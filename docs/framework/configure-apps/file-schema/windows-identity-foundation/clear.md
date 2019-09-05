---
title: <clear>
ms.date: 03/30/2017
ms.assetid: 54dcd1d1-038f-4fc8-a3a4-56ba7a1ca0fd
author: BrucePerlerMS
ms.openlocfilehash: e96349c72fc4a952e3dc7efeea5f69ebaa1fd0ad
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252046"
---
# <a name="clear"></a><span data-ttu-id="438c7-101">\<clear></span><span class="sxs-lookup"><span data-stu-id="438c7-101">\<clear></span></span>
<span data-ttu-id="438c7-102">Efface tous les gestionnaires de jetons de sécurité de la collection de gestionnaires de jetons actuelle.</span><span class="sxs-lookup"><span data-stu-id="438c7-102">Clears all security token handlers from the current token handler collection.</span></span>  
  
<span data-ttu-id="438c7-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="438c7-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="438c7-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="438c7-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="438c7-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="438c7-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="438c7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="438c7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="438c7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<désactivez >**</span><span class="sxs-lookup"><span data-stu-id="438c7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="438c7-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="438c7-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <clear>  
      </clear>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="438c7-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="438c7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="438c7-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="438c7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="438c7-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="438c7-111">Attributes</span></span>  
 <span data-ttu-id="438c7-112">Aucun</span><span class="sxs-lookup"><span data-stu-id="438c7-112">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="438c7-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="438c7-113">Child Elements</span></span>  
 <span data-ttu-id="438c7-114">Aucun</span><span class="sxs-lookup"><span data-stu-id="438c7-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="438c7-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="438c7-115">Parent Elements</span></span>  
  
|<span data-ttu-id="438c7-116">Élément</span><span class="sxs-lookup"><span data-stu-id="438c7-116">Element</span></span>|<span data-ttu-id="438c7-117">Description</span><span class="sxs-lookup"><span data-stu-id="438c7-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="438c7-118">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="438c7-118">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="438c7-119">Spécifie une collection de gestionnaires de jetons de sécurité inscrits auprès du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="438c7-119">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|
