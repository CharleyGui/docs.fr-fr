---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 4ef5890d52c3f2af42322f023b9a2a23cb583035
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855063"
---
# \<policyImporter>
<span data-ttu-id="2f9f6-101">Indique un importateur de stratégie qui contrôle l’importation d’assertions de stratégie personnalisées concernant les liaisons.</span><span class="sxs-lookup"><span data-stu-id="2f9f6-101">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<policyImporters>**](policyimporters.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<policyImporter>**  
  
## <a name="syntax"></a><span data-ttu-id="2f9f6-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f9f6-102">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2f9f6-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2f9f6-103">Attributes and Elements</span></span>  
 <span data-ttu-id="2f9f6-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2f9f6-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2f9f6-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="2f9f6-105">Attributes</span></span>  
  
|<span data-ttu-id="2f9f6-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="2f9f6-106">Attribute</span></span>|<span data-ttu-id="2f9f6-107">Description</span><span class="sxs-lookup"><span data-stu-id="2f9f6-107">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="2f9f6-108">Type de cet élément.</span><span class="sxs-lookup"><span data-stu-id="2f9f6-108">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2f9f6-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2f9f6-109">Child Elements</span></span>  
 <span data-ttu-id="2f9f6-110">Aucune</span><span class="sxs-lookup"><span data-stu-id="2f9f6-110">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2f9f6-111">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2f9f6-111">Parent Elements</span></span>  
  
|<span data-ttu-id="2f9f6-112">Élément</span><span class="sxs-lookup"><span data-stu-id="2f9f6-112">Element</span></span>|<span data-ttu-id="2f9f6-113">Description</span><span class="sxs-lookup"><span data-stu-id="2f9f6-113">Description</span></span>|  
|-------------|-----------------|  
|[\<policyImporters>](policyimporters.md)|<span data-ttu-id="2f9f6-114">Indique tous les importateurs de stratégie contrôlant l'importation d'assertions de stratégie personnalisées concernant les liaisons.</span><span class="sxs-lookup"><span data-stu-id="2f9f6-114">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f9f6-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="2f9f6-115">Remarks</span></span>  
 <span data-ttu-id="2f9f6-116">Un importateur de stratégie permet de rechercher des assertions de stratégie personnalisées concernant les fonctionnalités de liaison et de joindre un élément de liaison personnalisé qui implémente les fonctionnalités requises par l’assertion.</span><span class="sxs-lookup"><span data-stu-id="2f9f6-116">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f9f6-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f9f6-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="2f9f6-118">Configuration client WCF</span><span class="sxs-lookup"><span data-stu-id="2f9f6-118">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="2f9f6-119">Clients</span><span class="sxs-lookup"><span data-stu-id="2f9f6-119">Clients</span></span>](../../../wcf/feature-details/clients.md)
