---
title: <extensions> section
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: f3eb5d446291dfa6b7c8e0f1ee2b6a5cf53c2162
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185780"
---
# <a name="extensions-section"></a><span data-ttu-id="e27cc-102">\<extensions> section</span><span class="sxs-lookup"><span data-stu-id="e27cc-102">\<extensions> section</span></span>

<span data-ttu-id="e27cc-103">Cette section de configuration contient une collection d’extensions, qui permettent à l’utilisateur de créer des liaisons, des comportements et d’autres aspects d’extensions définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e27cc-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<extensions>**  
  
## <a name="syntax"></a><span data-ttu-id="e27cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e27cc-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e27cc-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e27cc-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e27cc-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e27cc-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e27cc-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="e27cc-107">Attributes</span></span>  

 <span data-ttu-id="e27cc-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e27cc-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e27cc-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e27cc-109">Child Elements</span></span>  
  
|<span data-ttu-id="e27cc-110">Élément</span><span class="sxs-lookup"><span data-stu-id="e27cc-110">Element</span></span>|<span data-ttu-id="e27cc-111">Description</span><span class="sxs-lookup"><span data-stu-id="e27cc-111">Description</span></span>|  
|-------------|-----------------|  
|[\<behaviorExtensions>](behaviorextensions.md)|<span data-ttu-id="e27cc-112">Cette section contient des éléments enfants qui spécifient des extensions de comportement permettant à l'utilisateur de personnaliser les comportements de service ou de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="e27cc-112">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[\<bindingElementExtensions>](bindingelementextensions.md)|<span data-ttu-id="e27cc-113">Cette section active l'utilisation d'un élément de liaison personnalisé à partir d'un ordinateur ou d'un fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="e27cc-113">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[\<bindingExtensions>](bindingextensions.md)|<span data-ttu-id="e27cc-114">Cette section contient des éléments enfants qui spécifient des extensions de liaison permettant à l'utilisateur de personnaliser des liaisons.</span><span class="sxs-lookup"><span data-stu-id="e27cc-114">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[\<endpointExtensions>](endpointextensions.md)|<span data-ttu-id="e27cc-115">Cette section contient des éléments enfants qui inscrivent des points de terminaison standard.</span><span class="sxs-lookup"><span data-stu-id="e27cc-115">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e27cc-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e27cc-116">Parent Elements</span></span>  
  
|<span data-ttu-id="e27cc-117">Élément</span><span class="sxs-lookup"><span data-stu-id="e27cc-117">Element</span></span>|<span data-ttu-id="e27cc-118">Description</span><span class="sxs-lookup"><span data-stu-id="e27cc-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e27cc-119">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e27cc-119">system.ServiceModel</span></span>|<span data-ttu-id="e27cc-120">Élément racine de tous les éléments de configuration WCF.</span><span class="sxs-lookup"><span data-stu-id="e27cc-120">The root element of all WCF configuration elements.</span></span>|
