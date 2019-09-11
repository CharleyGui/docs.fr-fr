---
title: <extensions>section
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 35621acaf96a80ffa3ffe4a3c6605143c48995a5
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855357"
---
# <a name="extensions-section"></a><span data-ttu-id="d4396-102">\<section > des extensions</span><span class="sxs-lookup"><span data-stu-id="d4396-102">\<extensions> section</span></span>
<span data-ttu-id="d4396-103">Cette section de configuration contient une collection d’extensions, qui permettent à l’utilisateur de créer des liaisons, des comportements et d’autres aspects d’extensions définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d4396-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
<span data-ttu-id="d4396-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d4396-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d4396-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d4396-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d4396-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<extensions >**</span><span class="sxs-lookup"><span data-stu-id="d4396-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<extensions>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4396-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4396-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <extensions>
    <bindingExtensions>
    </bindingExtensions>
    <behaviorExtensions>
    </behaviorExtensions>
    <bindingElementExtensions>
    </bindingElementExtensions>
    <endpointExtensions>
    </endpointExtensions>
  </extensions>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4396-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d4396-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d4396-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d4396-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4396-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="d4396-110">Attributes</span></span>  
 <span data-ttu-id="d4396-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d4396-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d4396-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d4396-112">Child Elements</span></span>  
  
|<span data-ttu-id="d4396-113">Élément</span><span class="sxs-lookup"><span data-stu-id="d4396-113">Element</span></span>|<span data-ttu-id="d4396-114">Description</span><span class="sxs-lookup"><span data-stu-id="d4396-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4396-115">\<behaviorExtensions></span><span class="sxs-lookup"><span data-stu-id="d4396-115">\<behaviorExtensions></span></span>](behaviorextensions.md)|<span data-ttu-id="d4396-116">Cette section contient des éléments enfants qui spécifient des extensions de comportement permettant à l'utilisateur de personnaliser les comportements de service ou de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="d4396-116">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[<span data-ttu-id="d4396-117">\<bindingElementExtensions></span><span class="sxs-lookup"><span data-stu-id="d4396-117">\<bindingElementExtensions></span></span>](bindingelementextensions.md)|<span data-ttu-id="d4396-118">Cette section active l'utilisation d'un élément de liaison personnalisé à partir d'un ordinateur ou d'un fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="d4396-118">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[<span data-ttu-id="d4396-119">\<bindingExtensions></span><span class="sxs-lookup"><span data-stu-id="d4396-119">\<bindingExtensions></span></span>](bindingextensions.md)|<span data-ttu-id="d4396-120">Cette section contient des éléments enfants qui spécifient des extensions de liaison permettant à l'utilisateur de personnaliser des liaisons.</span><span class="sxs-lookup"><span data-stu-id="d4396-120">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[<span data-ttu-id="d4396-121">\<endpointExtensions></span><span class="sxs-lookup"><span data-stu-id="d4396-121">\<endpointExtensions></span></span>](endpointextensions.md)|<span data-ttu-id="d4396-122">Cette section contient des éléments enfants qui inscrivent des points de terminaison standard.</span><span class="sxs-lookup"><span data-stu-id="d4396-122">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d4396-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d4396-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d4396-124">Élément</span><span class="sxs-lookup"><span data-stu-id="d4396-124">Element</span></span>|<span data-ttu-id="d4396-125">Description</span><span class="sxs-lookup"><span data-stu-id="d4396-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d4396-126">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d4396-126">system.ServiceModel</span></span>|<span data-ttu-id="d4396-127">Élément racine de tous les éléments de configuration WCF.</span><span class="sxs-lookup"><span data-stu-id="d4396-127">The root element of all WCF configuration elements.</span></span>|
