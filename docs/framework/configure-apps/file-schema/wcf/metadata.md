---
title: <metadata>
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: 4555dc9c2e0b783de2fb57e47c9aada0d69462e7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931302"
---
# <a name="metadata"></a><span data-ttu-id="8cefc-101">\<metadata></span><span class="sxs-lookup"><span data-stu-id="8cefc-101">\<metadata></span></span>
<span data-ttu-id="8cefc-102">Indique la façon dont les métadonnées peuvent être traitées.</span><span class="sxs-lookup"><span data-stu-id="8cefc-102">Specifies how service metadata can be processed.</span></span>  
  
 <span data-ttu-id="8cefc-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8cefc-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="8cefc-104">\<client></span><span class="sxs-lookup"><span data-stu-id="8cefc-104">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cefc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8cefc-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <client>
    <metadata>
      <policyImporters>
        <policyImporter type="string" />
      </policyImporters>
      <wsdlImporters>
        <wsdlImporter type="string" />
      </wsdlImporters>
    </metadata>
  </client>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8cefc-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8cefc-106">Attributes and Elements</span></span>  
 <span data-ttu-id="8cefc-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8cefc-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8cefc-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="8cefc-108">Attributes</span></span>  
 <span data-ttu-id="8cefc-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8cefc-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8cefc-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8cefc-110">Child Elements</span></span>  
  
|<span data-ttu-id="8cefc-111">Élément</span><span class="sxs-lookup"><span data-stu-id="8cefc-111">Element</span></span>|<span data-ttu-id="8cefc-112">Description</span><span class="sxs-lookup"><span data-stu-id="8cefc-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8cefc-113">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="8cefc-113">\<policyImporters></span></span>](policyimporters.md)|<span data-ttu-id="8cefc-114">Indique tous les importateurs de stratégie contrôlant l'importation d'assertions de stratégie personnalisées concernant les liaisons.</span><span class="sxs-lookup"><span data-stu-id="8cefc-114">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="8cefc-115">Un importateur de stratégie permet de rechercher des assertions de stratégie personnalisées concernant les fonctionnalités de liaison et de joindre un élément de liaison personnalisé qui implémente les fonctionnalités requises par l’assertion.</span><span class="sxs-lookup"><span data-stu-id="8cefc-115">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[<span data-ttu-id="8cefc-116">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="8cefc-116">\<wsdlImporters></span></span>](wsdlimporters.md)|<span data-ttu-id="8cefc-117">Indique tous les importateurs WSDL qui importent des métadonnées Web Services Description Language (WSDL) 1.1 avec des pièces jointes WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="8cefc-117">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="8cefc-118">Un importateur WSDL permet d'importer des métadonnées et de convertir ces informations en différentes classes représentant les informations de contrat et de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="8cefc-118">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="8cefc-119">Il peut importer sélectivement des informations de contrat et de point de terminaison ainsi que des propriétés qui exposent toute erreur d'importation et accepte des informations de types liées au processus d'importation et de conversion.</span><span class="sxs-lookup"><span data-stu-id="8cefc-119">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="8cefc-120">Il prend également en charge les informations et les propriétés de liaison qui donnent accès aux documents de stratégie, documents WSDL, extensions WSDL et documents de schéma XML.</span><span class="sxs-lookup"><span data-stu-id="8cefc-120">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8cefc-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8cefc-121">Parent Elements</span></span>  
  
|<span data-ttu-id="8cefc-122">Élément</span><span class="sxs-lookup"><span data-stu-id="8cefc-122">Element</span></span>|<span data-ttu-id="8cefc-123">Description</span><span class="sxs-lookup"><span data-stu-id="8cefc-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8cefc-124">\<client></span><span class="sxs-lookup"><span data-stu-id="8cefc-124">\<client></span></span>](client.md)|<span data-ttu-id="8cefc-125">La section client définit la liste de points de terminaison auxquels un client peut se connecter.</span><span class="sxs-lookup"><span data-stu-id="8cefc-125">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8cefc-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8cefc-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="8cefc-127">Configuration du client WCF</span><span class="sxs-lookup"><span data-stu-id="8cefc-127">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="8cefc-128">Clients</span><span class="sxs-lookup"><span data-stu-id="8cefc-128">Clients</span></span>](../../../wcf/feature-details/clients.md)
