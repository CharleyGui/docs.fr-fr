---
title: <metadata>
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: 028e4d3fbe7bce06caa7497c8f95f3b293a4b068
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855229"
---
# <a name="metadata"></a><span data-ttu-id="3fb57-101">\<metadata></span><span class="sxs-lookup"><span data-stu-id="3fb57-101">\<metadata></span></span>
<span data-ttu-id="3fb57-102">Indique la façon dont les métadonnées peuvent être traitées.</span><span class="sxs-lookup"><span data-stu-id="3fb57-102">Specifies how service metadata can be processed.</span></span>  
  
<span data-ttu-id="3fb57-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3fb57-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3fb57-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="3fb57-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="3fb57-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> client**](client.md)</span><span class="sxs-lookup"><span data-stu-id="3fb57-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="3fb57-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de métadonnées**</span><span class="sxs-lookup"><span data-stu-id="3fb57-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<metadata>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fb57-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3fb57-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3fb57-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3fb57-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3fb57-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3fb57-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3fb57-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="3fb57-110">Attributes</span></span>  
 <span data-ttu-id="3fb57-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3fb57-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3fb57-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3fb57-112">Child Elements</span></span>  
  
|<span data-ttu-id="3fb57-113">Élément</span><span class="sxs-lookup"><span data-stu-id="3fb57-113">Element</span></span>|<span data-ttu-id="3fb57-114">Description</span><span class="sxs-lookup"><span data-stu-id="3fb57-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3fb57-115">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="3fb57-115">\<policyImporters></span></span>](policyimporters.md)|<span data-ttu-id="3fb57-116">Indique tous les importateurs de stratégie contrôlant l'importation d'assertions de stratégie personnalisées concernant les liaisons.</span><span class="sxs-lookup"><span data-stu-id="3fb57-116">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="3fb57-117">Un importateur de stratégie permet de rechercher des assertions de stratégie personnalisées concernant les fonctionnalités de liaison et de joindre un élément de liaison personnalisé qui implémente les fonctionnalités requises par l’assertion.</span><span class="sxs-lookup"><span data-stu-id="3fb57-117">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[<span data-ttu-id="3fb57-118">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="3fb57-118">\<wsdlImporters></span></span>](wsdlimporters.md)|<span data-ttu-id="3fb57-119">Indique tous les importateurs WSDL qui importent des métadonnées Web Services Description Language (WSDL) 1.1 avec des pièces jointes WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="3fb57-119">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="3fb57-120">Un importateur WSDL permet d'importer des métadonnées et de convertir ces informations en différentes classes représentant les informations de contrat et de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="3fb57-120">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="3fb57-121">Il peut importer sélectivement des informations de contrat et de point de terminaison ainsi que des propriétés qui exposent toute erreur d'importation et accepte des informations de types liées au processus d'importation et de conversion.</span><span class="sxs-lookup"><span data-stu-id="3fb57-121">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="3fb57-122">Il prend également en charge les informations et les propriétés de liaison qui donnent accès aux documents de stratégie, documents WSDL, extensions WSDL et documents de schéma XML.</span><span class="sxs-lookup"><span data-stu-id="3fb57-122">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3fb57-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3fb57-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3fb57-124">Élément</span><span class="sxs-lookup"><span data-stu-id="3fb57-124">Element</span></span>|<span data-ttu-id="3fb57-125">Description</span><span class="sxs-lookup"><span data-stu-id="3fb57-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3fb57-126">\<client></span><span class="sxs-lookup"><span data-stu-id="3fb57-126">\<client></span></span>](client.md)|<span data-ttu-id="3fb57-127">La section client définit la liste de points de terminaison auxquels un client peut se connecter.</span><span class="sxs-lookup"><span data-stu-id="3fb57-127">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3fb57-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3fb57-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="3fb57-129">Configuration du client WCF</span><span class="sxs-lookup"><span data-stu-id="3fb57-129">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="3fb57-130">Clients</span><span class="sxs-lookup"><span data-stu-id="3fb57-130">Clients</span></span>](../../../wcf/feature-details/clients.md)
