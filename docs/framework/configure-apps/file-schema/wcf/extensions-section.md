---
title: <extensions>section
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 35621acaf96a80ffa3ffe4a3c6605143c48995a5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855357"
---
# <a name="extensions-section"></a><span data-ttu-id="3d796-102">\<extensions>section</span><span class="sxs-lookup"><span data-stu-id="3d796-102">\<extensions> section</span></span>
<span data-ttu-id="3d796-103">Cette section de configuration contient une collection d’extensions, qui permettent à l’utilisateur de créer des liaisons, des comportements et d’autres aspects d’extensions définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3d796-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<extensions>**  
  
## <a name="syntax"></a><span data-ttu-id="3d796-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d796-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3d796-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3d796-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3d796-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3d796-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3d796-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="3d796-107">Attributes</span></span>  
 <span data-ttu-id="3d796-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3d796-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3d796-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3d796-109">Child Elements</span></span>  
  
|<span data-ttu-id="3d796-110">Élément</span><span class="sxs-lookup"><span data-stu-id="3d796-110">Element</span></span>|<span data-ttu-id="3d796-111">Description</span><span class="sxs-lookup"><span data-stu-id="3d796-111">Description</span></span>|  
|-------------|-----------------|  
|[\<behaviorExtensions>](behaviorextensions.md)|<span data-ttu-id="3d796-112">Cette section contient des éléments enfants qui spécifient des extensions de comportement permettant à l'utilisateur de personnaliser les comportements de service ou de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="3d796-112">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[\<bindingElementExtensions>](bindingelementextensions.md)|<span data-ttu-id="3d796-113">Cette section active l'utilisation d'un élément de liaison personnalisé à partir d'un ordinateur ou d'un fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="3d796-113">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[\<bindingExtensions>](bindingextensions.md)|<span data-ttu-id="3d796-114">Cette section contient des éléments enfants qui spécifient des extensions de liaison permettant à l'utilisateur de personnaliser des liaisons.</span><span class="sxs-lookup"><span data-stu-id="3d796-114">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[\<endpointExtensions>](endpointextensions.md)|<span data-ttu-id="3d796-115">Cette section contient des éléments enfants qui inscrivent des points de terminaison standard.</span><span class="sxs-lookup"><span data-stu-id="3d796-115">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3d796-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3d796-116">Parent Elements</span></span>  
  
|<span data-ttu-id="3d796-117">Élément</span><span class="sxs-lookup"><span data-stu-id="3d796-117">Element</span></span>|<span data-ttu-id="3d796-118">Description</span><span class="sxs-lookup"><span data-stu-id="3d796-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3d796-119">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3d796-119">system.ServiceModel</span></span>|<span data-ttu-id="3d796-120">Élément racine de tous les éléments de configuration WCF.</span><span class="sxs-lookup"><span data-stu-id="3d796-120">The root element of all WCF configuration elements.</span></span>|
