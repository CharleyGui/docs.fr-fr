---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 4ef5890d52c3f2af42322f023b9a2a23cb583035
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855063"
---
# <a name="policyimporter"></a><span data-ttu-id="14330-101">\<policyImporter ></span><span class="sxs-lookup"><span data-stu-id="14330-101">\<policyImporter></span></span>
<span data-ttu-id="14330-102">Indique un importateur de stratégie qui contrôle l’importation d’assertions de stratégie personnalisées concernant les liaisons.</span><span class="sxs-lookup"><span data-stu-id="14330-102">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
<span data-ttu-id="14330-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="14330-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="14330-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="14330-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="14330-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> client**](client.md)</span><span class="sxs-lookup"><span data-stu-id="14330-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="14330-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de métadonnées**](metadata.md)</span><span class="sxs-lookup"><span data-stu-id="14330-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)</span></span>\
<span data-ttu-id="14330-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<policyImporters >** ](policyimporters.md)</span><span class="sxs-lookup"><span data-stu-id="14330-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<policyImporters>**](policyimporters.md)</span></span>  
<span data-ttu-id="14330-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<policyImporter >**</span><span class="sxs-lookup"><span data-stu-id="14330-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<policyImporter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14330-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14330-109">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14330-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="14330-110">Attributes and Elements</span></span>  
 <span data-ttu-id="14330-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="14330-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14330-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="14330-112">Attributes</span></span>  
  
|<span data-ttu-id="14330-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="14330-113">Attribute</span></span>|<span data-ttu-id="14330-114">Description</span><span class="sxs-lookup"><span data-stu-id="14330-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="14330-115">Type de cet élément.</span><span class="sxs-lookup"><span data-stu-id="14330-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="14330-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="14330-116">Child Elements</span></span>  
 <span data-ttu-id="14330-117">Aucun</span><span class="sxs-lookup"><span data-stu-id="14330-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="14330-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="14330-118">Parent Elements</span></span>  
  
|<span data-ttu-id="14330-119">Élément</span><span class="sxs-lookup"><span data-stu-id="14330-119">Element</span></span>|<span data-ttu-id="14330-120">Description</span><span class="sxs-lookup"><span data-stu-id="14330-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14330-121">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="14330-121">\<policyImporters></span></span>](policyimporters.md)|<span data-ttu-id="14330-122">Indique tous les importateurs de stratégie contrôlant l'importation d'assertions de stratégie personnalisées concernant les liaisons.</span><span class="sxs-lookup"><span data-stu-id="14330-122">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14330-123">Notes</span><span class="sxs-lookup"><span data-stu-id="14330-123">Remarks</span></span>  
 <span data-ttu-id="14330-124">Un importateur de stratégie permet de rechercher des assertions de stratégie personnalisées concernant les fonctionnalités de liaison et de joindre un élément de liaison personnalisé qui implémente les fonctionnalités requises par l’assertion.</span><span class="sxs-lookup"><span data-stu-id="14330-124">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14330-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14330-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="14330-126">Configuration du client WCF</span><span class="sxs-lookup"><span data-stu-id="14330-126">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="14330-127">Clients</span><span class="sxs-lookup"><span data-stu-id="14330-127">Clients</span></span>](../../../wcf/feature-details/clients.md)
