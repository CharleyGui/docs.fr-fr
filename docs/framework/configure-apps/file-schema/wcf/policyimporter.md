---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 273bd0d5e68a661c639b82264b440b83d8127427
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933792"
---
# <a name="policyimporter"></a><span data-ttu-id="028f1-101">\<policyImporter ></span><span class="sxs-lookup"><span data-stu-id="028f1-101">\<policyImporter></span></span>
<span data-ttu-id="028f1-102">Indique un importateur de stratégie qui contrôle l’importation d’assertions de stratégie personnalisées concernant les liaisons.</span><span class="sxs-lookup"><span data-stu-id="028f1-102">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="028f1-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="028f1-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="028f1-104">\<client></span><span class="sxs-lookup"><span data-stu-id="028f1-104">\<client></span></span>  
<span data-ttu-id="028f1-105">\<metadata></span><span class="sxs-lookup"><span data-stu-id="028f1-105">\<metadata></span></span>  
<span data-ttu-id="028f1-106">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="028f1-106">\<policyImporters></span></span>  
<span data-ttu-id="028f1-107">\<policyImporter ></span><span class="sxs-lookup"><span data-stu-id="028f1-107">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="028f1-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="028f1-108">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="028f1-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="028f1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="028f1-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="028f1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="028f1-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="028f1-111">Attributes</span></span>  
  
|<span data-ttu-id="028f1-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="028f1-112">Attribute</span></span>|<span data-ttu-id="028f1-113">Description</span><span class="sxs-lookup"><span data-stu-id="028f1-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="028f1-114">Type de cet élément.</span><span class="sxs-lookup"><span data-stu-id="028f1-114">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="028f1-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="028f1-115">Child Elements</span></span>  
 <span data-ttu-id="028f1-116">Aucun</span><span class="sxs-lookup"><span data-stu-id="028f1-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="028f1-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="028f1-117">Parent Elements</span></span>  
  
|<span data-ttu-id="028f1-118">Élément</span><span class="sxs-lookup"><span data-stu-id="028f1-118">Element</span></span>|<span data-ttu-id="028f1-119">Description</span><span class="sxs-lookup"><span data-stu-id="028f1-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="028f1-120">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="028f1-120">\<policyImporters></span></span>](policyimporters.md)|<span data-ttu-id="028f1-121">Indique tous les importateurs de stratégie contrôlant l'importation d'assertions de stratégie personnalisées concernant les liaisons.</span><span class="sxs-lookup"><span data-stu-id="028f1-121">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="028f1-122">Notes</span><span class="sxs-lookup"><span data-stu-id="028f1-122">Remarks</span></span>  
 <span data-ttu-id="028f1-123">Un importateur de stratégie permet de rechercher des assertions de stratégie personnalisées concernant les fonctionnalités de liaison et de joindre un élément de liaison personnalisé qui implémente les fonctionnalités requises par l’assertion.</span><span class="sxs-lookup"><span data-stu-id="028f1-123">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="028f1-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="028f1-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="028f1-125">Configuration du client WCF</span><span class="sxs-lookup"><span data-stu-id="028f1-125">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="028f1-126">Clients</span><span class="sxs-lookup"><span data-stu-id="028f1-126">Clients</span></span>](../../../wcf/feature-details/clients.md)
