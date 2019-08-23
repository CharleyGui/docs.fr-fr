---
title: <extensions>section
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 4c8b5fe6eef1863ee3f02cb761a3aac61406e446
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918967"
---
# <a name="extensions-section"></a><span data-ttu-id="1b35b-102">\<section > des extensions</span><span class="sxs-lookup"><span data-stu-id="1b35b-102">\<extensions> section</span></span>
<span data-ttu-id="1b35b-103">Cette section de configuration contient une collection d’extensions, qui permettent à l’utilisateur de créer des liaisons, des comportements et d’autres aspects d’extensions définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1b35b-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
<span data-ttu-id="1b35b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1b35b-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b35b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b35b-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b35b-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1b35b-106">Attributes and Elements</span></span>  
 <span data-ttu-id="1b35b-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1b35b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b35b-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="1b35b-108">Attributes</span></span>  
 <span data-ttu-id="1b35b-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="1b35b-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1b35b-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1b35b-110">Child Elements</span></span>  
  
|<span data-ttu-id="1b35b-111">Élément</span><span class="sxs-lookup"><span data-stu-id="1b35b-111">Element</span></span>|<span data-ttu-id="1b35b-112">Description</span><span class="sxs-lookup"><span data-stu-id="1b35b-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1b35b-113">\<behaviorExtensions></span><span class="sxs-lookup"><span data-stu-id="1b35b-113">\<behaviorExtensions></span></span>](behaviorextensions.md)|<span data-ttu-id="1b35b-114">Cette section contient des éléments enfants qui spécifient des extensions de comportement permettant à l'utilisateur de personnaliser les comportements de service ou de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="1b35b-114">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[<span data-ttu-id="1b35b-115">\<bindingElementExtensions></span><span class="sxs-lookup"><span data-stu-id="1b35b-115">\<bindingElementExtensions></span></span>](bindingelementextensions.md)|<span data-ttu-id="1b35b-116">Cette section active l'utilisation d'un élément de liaison personnalisé à partir d'un ordinateur ou d'un fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="1b35b-116">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[<span data-ttu-id="1b35b-117">\<bindingExtensions></span><span class="sxs-lookup"><span data-stu-id="1b35b-117">\<bindingExtensions></span></span>](bindingextensions.md)|<span data-ttu-id="1b35b-118">Cette section contient des éléments enfants qui spécifient des extensions de liaison permettant à l'utilisateur de personnaliser des liaisons.</span><span class="sxs-lookup"><span data-stu-id="1b35b-118">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[<span data-ttu-id="1b35b-119">\<endpointExtensions></span><span class="sxs-lookup"><span data-stu-id="1b35b-119">\<endpointExtensions></span></span>](endpointextensions.md)|<span data-ttu-id="1b35b-120">Cette section contient des éléments enfants qui inscrivent des points de terminaison standard.</span><span class="sxs-lookup"><span data-stu-id="1b35b-120">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1b35b-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1b35b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="1b35b-122">Élément</span><span class="sxs-lookup"><span data-stu-id="1b35b-122">Element</span></span>|<span data-ttu-id="1b35b-123">Description</span><span class="sxs-lookup"><span data-stu-id="1b35b-123">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1b35b-124">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1b35b-124">system.ServiceModel</span></span>|<span data-ttu-id="1b35b-125">Élément racine de tous les éléments de configuration WCF.</span><span class="sxs-lookup"><span data-stu-id="1b35b-125">The root element of all WCF configuration elements.</span></span>|
