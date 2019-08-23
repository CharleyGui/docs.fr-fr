---
title: <wsdlImporter>
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 13c9400874f1e02fac3ce0c3010153ad7806288c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915189"
---
# <a name="wsdlimporter"></a><span data-ttu-id="78ee5-101">\<wsdlImporter ></span><span class="sxs-lookup"><span data-stu-id="78ee5-101">\<wsdlImporter></span></span>
<span data-ttu-id="78ee5-102">Indique tous les importateurs WSDL qui importent des métadonnées WSDL (Web Services Description Language) 1.1 avec des pièces jointes WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="78ee5-102">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
<span data-ttu-id="78ee5-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="78ee5-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="78ee5-104">\<client></span><span class="sxs-lookup"><span data-stu-id="78ee5-104">\<client></span></span>  
<span data-ttu-id="78ee5-105">\<metadata></span><span class="sxs-lookup"><span data-stu-id="78ee5-105">\<metadata></span></span>  
<span data-ttu-id="78ee5-106">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="78ee5-106">\<wsdlImporters></span></span>  
<span data-ttu-id="78ee5-107">\<wsdlImporter ></span><span class="sxs-lookup"><span data-stu-id="78ee5-107">\<wsdlImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78ee5-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78ee5-108">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78ee5-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="78ee5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="78ee5-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="78ee5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78ee5-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="78ee5-111">Attributes</span></span>  
  
|<span data-ttu-id="78ee5-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="78ee5-112">Attribute</span></span>|<span data-ttu-id="78ee5-113">Description</span><span class="sxs-lookup"><span data-stu-id="78ee5-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="78ee5-114">Type de cet élément.</span><span class="sxs-lookup"><span data-stu-id="78ee5-114">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="78ee5-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="78ee5-115">Child Elements</span></span>  
 <span data-ttu-id="78ee5-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="78ee5-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="78ee5-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="78ee5-117">Parent Elements</span></span>  
  
|<span data-ttu-id="78ee5-118">Élément</span><span class="sxs-lookup"><span data-stu-id="78ee5-118">Element</span></span>|<span data-ttu-id="78ee5-119">Description</span><span class="sxs-lookup"><span data-stu-id="78ee5-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78ee5-120">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="78ee5-120">\<wsdlImporters></span></span>](wsdlimporters.md)|<span data-ttu-id="78ee5-121">Indique tous les importateurs WSDL qui importent des métadonnées WSDL (Web Services Description Language) 1.1 avec des pièces jointes WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="78ee5-121">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78ee5-122">Notes</span><span class="sxs-lookup"><span data-stu-id="78ee5-122">Remarks</span></span>  
 <span data-ttu-id="78ee5-123">Un importateur WSDL permet d'importer des métadonnées et de convertir ces informations en différentes classes représentant les informations de contrat et de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="78ee5-123">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="78ee5-124">Il peut importer sélectivement des informations de contrat et de point de terminaison ainsi que des propriétés qui exposent toute erreur d'importation et accepte des informations de types liées au processus d'importation et de conversion.</span><span class="sxs-lookup"><span data-stu-id="78ee5-124">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="78ee5-125">Il prend également en charge les informations et les propriétés de liaison qui donnent accès aux documents de stratégie, documents WSDL, extensions WSDL et documents de schéma XML.</span><span class="sxs-lookup"><span data-stu-id="78ee5-125">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78ee5-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78ee5-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="78ee5-127">Configuration du client WCF</span><span class="sxs-lookup"><span data-stu-id="78ee5-127">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="78ee5-128">Clients</span><span class="sxs-lookup"><span data-stu-id="78ee5-128">Clients</span></span>](../../../wcf/feature-details/clients.md)
