---
title: <wsdlImporter>
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 317921a66fa3b8d1f0026d676ea674b67732b3df
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854760"
---
# \<wsdlImporter>
<span data-ttu-id="e01d0-101">Indique tous les importateurs WSDL qui importent des métadonnées WSDL (Web Services Description Language) 1.1 avec des pièces jointes WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="e01d0-101">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsdlImporters>**](wsdlimporters.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsdlImporter>**  
  
## <a name="syntax"></a><span data-ttu-id="e01d0-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e01d0-102">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e01d0-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e01d0-103">Attributes and Elements</span></span>  
 <span data-ttu-id="e01d0-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e01d0-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e01d0-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="e01d0-105">Attributes</span></span>  
  
|<span data-ttu-id="e01d0-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="e01d0-106">Attribute</span></span>|<span data-ttu-id="e01d0-107">Description</span><span class="sxs-lookup"><span data-stu-id="e01d0-107">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="e01d0-108">Type de cet élément.</span><span class="sxs-lookup"><span data-stu-id="e01d0-108">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e01d0-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e01d0-109">Child Elements</span></span>  
 <span data-ttu-id="e01d0-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e01d0-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e01d0-111">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e01d0-111">Parent Elements</span></span>  
  
|<span data-ttu-id="e01d0-112">Élément</span><span class="sxs-lookup"><span data-stu-id="e01d0-112">Element</span></span>|<span data-ttu-id="e01d0-113">Description</span><span class="sxs-lookup"><span data-stu-id="e01d0-113">Description</span></span>|  
|-------------|-----------------|  
|[\<wsdlImporters>](wsdlimporters.md)|<span data-ttu-id="e01d0-114">Indique tous les importateurs WSDL qui importent des métadonnées WSDL (Web Services Description Language) 1.1 avec des pièces jointes WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="e01d0-114">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e01d0-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="e01d0-115">Remarks</span></span>  
 <span data-ttu-id="e01d0-116">Un importateur WSDL permet d'importer des métadonnées et de convertir ces informations en différentes classes représentant les informations de contrat et de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="e01d0-116">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="e01d0-117">Il peut importer sélectivement des informations de contrat et de point de terminaison ainsi que des propriétés qui exposent toute erreur d'importation et accepte des informations de types liées au processus d'importation et de conversion.</span><span class="sxs-lookup"><span data-stu-id="e01d0-117">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="e01d0-118">Il prend également en charge les informations et les propriétés de liaison qui donnent accès aux documents de stratégie, documents WSDL, extensions WSDL et documents de schéma XML.</span><span class="sxs-lookup"><span data-stu-id="e01d0-118">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e01d0-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e01d0-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="e01d0-120">Configuration client WCF</span><span class="sxs-lookup"><span data-stu-id="e01d0-120">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="e01d0-121">Clients</span><span class="sxs-lookup"><span data-stu-id="e01d0-121">Clients</span></span>](../../../wcf/feature-details/clients.md)
