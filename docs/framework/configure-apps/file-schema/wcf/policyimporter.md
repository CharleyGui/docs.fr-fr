---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 72778ce0070d853f8b081a4889ead9524bafd0e8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181347"
---
# \<policyImporter>

<span data-ttu-id="6a980-101">Indique un importateur de stratégie qui contrôle l’importation d’assertions de stratégie personnalisées concernant les liaisons.</span><span class="sxs-lookup"><span data-stu-id="6a980-101">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<policyImporters>**](policyimporters.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<policyImporter>**  
  
## <a name="syntax"></a><span data-ttu-id="6a980-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a980-102">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6a980-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6a980-103">Attributes and Elements</span></span>  

 <span data-ttu-id="6a980-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6a980-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a980-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="6a980-105">Attributes</span></span>  
  
|<span data-ttu-id="6a980-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="6a980-106">Attribute</span></span>|<span data-ttu-id="6a980-107">Description</span><span class="sxs-lookup"><span data-stu-id="6a980-107">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="6a980-108">Type de cet élément.</span><span class="sxs-lookup"><span data-stu-id="6a980-108">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6a980-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6a980-109">Child Elements</span></span>  

 <span data-ttu-id="6a980-110">None</span><span class="sxs-lookup"><span data-stu-id="6a980-110">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6a980-111">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6a980-111">Parent Elements</span></span>  
  
|<span data-ttu-id="6a980-112">Élément</span><span class="sxs-lookup"><span data-stu-id="6a980-112">Element</span></span>|<span data-ttu-id="6a980-113">Description</span><span class="sxs-lookup"><span data-stu-id="6a980-113">Description</span></span>|  
|-------------|-----------------|  
|[\<policyImporters>](policyimporters.md)|<span data-ttu-id="6a980-114">Indique tous les importateurs de stratégie contrôlant l'importation d'assertions de stratégie personnalisées concernant les liaisons.</span><span class="sxs-lookup"><span data-stu-id="6a980-114">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a980-115">Notes</span><span class="sxs-lookup"><span data-stu-id="6a980-115">Remarks</span></span>  

 <span data-ttu-id="6a980-116">Un importateur de stratégie permet de rechercher des assertions de stratégie personnalisées concernant les fonctionnalités de liaison et de joindre un élément de liaison personnalisé qui implémente les fonctionnalités requises par l’assertion.</span><span class="sxs-lookup"><span data-stu-id="6a980-116">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a980-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a980-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="6a980-118">Configuration du client WCF</span><span class="sxs-lookup"><span data-stu-id="6a980-118">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="6a980-119">Clients</span><span class="sxs-lookup"><span data-stu-id="6a980-119">Clients</span></span>](../../../wcf/feature-details/clients.md)
