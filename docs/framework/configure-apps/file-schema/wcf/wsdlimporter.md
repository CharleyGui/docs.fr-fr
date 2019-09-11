---
title: <wsdlImporter>
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 317921a66fa3b8d1f0026d676ea674b67732b3df
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854760"
---
# <a name="wsdlimporter"></a><span data-ttu-id="bb24d-101">\<wsdlImporter ></span><span class="sxs-lookup"><span data-stu-id="bb24d-101">\<wsdlImporter></span></span>
<span data-ttu-id="bb24d-102">Indique tous les importateurs WSDL qui importent des métadonnées WSDL (Web Services Description Language) 1.1 avec des pièces jointes WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="bb24d-102">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
<span data-ttu-id="bb24d-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bb24d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bb24d-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="bb24d-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bb24d-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> client**](client.md)</span><span class="sxs-lookup"><span data-stu-id="bb24d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="bb24d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de métadonnées**](metadata.md)</span><span class="sxs-lookup"><span data-stu-id="bb24d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)</span></span>\
<span data-ttu-id="bb24d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsdlImporters >** ](wsdlimporters.md)</span><span class="sxs-lookup"><span data-stu-id="bb24d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsdlImporters>**](wsdlimporters.md)</span></span>  
<span data-ttu-id="bb24d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<wsdlImporter >**</span><span class="sxs-lookup"><span data-stu-id="bb24d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsdlImporter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb24d-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb24d-109">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bb24d-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="bb24d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bb24d-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="bb24d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bb24d-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="bb24d-112">Attributes</span></span>  
  
|<span data-ttu-id="bb24d-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="bb24d-113">Attribute</span></span>|<span data-ttu-id="bb24d-114">Description</span><span class="sxs-lookup"><span data-stu-id="bb24d-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="bb24d-115">Type de cet élément.</span><span class="sxs-lookup"><span data-stu-id="bb24d-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bb24d-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bb24d-116">Child Elements</span></span>  
 <span data-ttu-id="bb24d-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="bb24d-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bb24d-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bb24d-118">Parent Elements</span></span>  
  
|<span data-ttu-id="bb24d-119">Élément</span><span class="sxs-lookup"><span data-stu-id="bb24d-119">Element</span></span>|<span data-ttu-id="bb24d-120">Description</span><span class="sxs-lookup"><span data-stu-id="bb24d-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bb24d-121">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="bb24d-121">\<wsdlImporters></span></span>](wsdlimporters.md)|<span data-ttu-id="bb24d-122">Indique tous les importateurs WSDL qui importent des métadonnées WSDL (Web Services Description Language) 1.1 avec des pièces jointes WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="bb24d-122">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb24d-123">Notes</span><span class="sxs-lookup"><span data-stu-id="bb24d-123">Remarks</span></span>  
 <span data-ttu-id="bb24d-124">Un importateur WSDL permet d'importer des métadonnées et de convertir ces informations en différentes classes représentant les informations de contrat et de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="bb24d-124">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="bb24d-125">Il peut importer sélectivement des informations de contrat et de point de terminaison ainsi que des propriétés qui exposent toute erreur d'importation et accepte des informations de types liées au processus d'importation et de conversion.</span><span class="sxs-lookup"><span data-stu-id="bb24d-125">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="bb24d-126">Il prend également en charge les informations et les propriétés de liaison qui donnent accès aux documents de stratégie, documents WSDL, extensions WSDL et documents de schéma XML.</span><span class="sxs-lookup"><span data-stu-id="bb24d-126">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb24d-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb24d-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="bb24d-128">Configuration du client WCF</span><span class="sxs-lookup"><span data-stu-id="bb24d-128">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="bb24d-129">Clients</span><span class="sxs-lookup"><span data-stu-id="bb24d-129">Clients</span></span>](../../../wcf/feature-details/clients.md)
