---
title: <metadata>
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: 028e4d3fbe7bce06caa7497c8f95f3b293a4b068
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855229"
---
# \<metadata>
<span data-ttu-id="0c831-101">Indique la façon dont les métadonnées peuvent être traitées.</span><span class="sxs-lookup"><span data-stu-id="0c831-101">Specifies how service metadata can be processed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<metadata>**  
  
## <a name="syntax"></a><span data-ttu-id="0c831-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c831-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c831-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0c831-103">Attributes and Elements</span></span>  
 <span data-ttu-id="0c831-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0c831-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c831-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="0c831-105">Attributes</span></span>  
 <span data-ttu-id="0c831-106">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0c831-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0c831-107">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0c831-107">Child Elements</span></span>  
  
|<span data-ttu-id="0c831-108">Élément</span><span class="sxs-lookup"><span data-stu-id="0c831-108">Element</span></span>|<span data-ttu-id="0c831-109">Description</span><span class="sxs-lookup"><span data-stu-id="0c831-109">Description</span></span>|  
|-------------|-----------------|  
|[\<policyImporters>](policyimporters.md)|<span data-ttu-id="0c831-110">Indique tous les importateurs de stratégie contrôlant l'importation d'assertions de stratégie personnalisées concernant les liaisons.</span><span class="sxs-lookup"><span data-stu-id="0c831-110">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="0c831-111">Un importateur de stratégie permet de rechercher des assertions de stratégie personnalisées concernant les fonctionnalités de liaison et de joindre un élément de liaison personnalisé qui implémente les fonctionnalités requises par l’assertion.</span><span class="sxs-lookup"><span data-stu-id="0c831-111">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[\<wsdlImporters>](wsdlimporters.md)|<span data-ttu-id="0c831-112">Indique tous les importateurs WSDL qui importent des métadonnées Web Services Description Language (WSDL) 1.1 avec des pièces jointes WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="0c831-112">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="0c831-113">Un importateur WSDL permet d'importer des métadonnées et de convertir ces informations en différentes classes représentant les informations de contrat et de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="0c831-113">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="0c831-114">Il peut importer sélectivement des informations de contrat et de point de terminaison ainsi que des propriétés qui exposent toute erreur d'importation et accepte des informations de types liées au processus d'importation et de conversion.</span><span class="sxs-lookup"><span data-stu-id="0c831-114">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="0c831-115">Il prend également en charge les informations et les propriétés de liaison qui donnent accès aux documents de stratégie, documents WSDL, extensions WSDL et documents de schéma XML.</span><span class="sxs-lookup"><span data-stu-id="0c831-115">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0c831-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0c831-116">Parent Elements</span></span>  
  
|<span data-ttu-id="0c831-117">Élément</span><span class="sxs-lookup"><span data-stu-id="0c831-117">Element</span></span>|<span data-ttu-id="0c831-118">Description</span><span class="sxs-lookup"><span data-stu-id="0c831-118">Description</span></span>|  
|-------------|-----------------|  
|[\<client>](client.md)|<span data-ttu-id="0c831-119">La section client définit la liste de points de terminaison auxquels un client peut se connecter.</span><span class="sxs-lookup"><span data-stu-id="0c831-119">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0c831-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c831-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="0c831-121">Configuration client WCF</span><span class="sxs-lookup"><span data-stu-id="0c831-121">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="0c831-122">Clients</span><span class="sxs-lookup"><span data-stu-id="0c831-122">Clients</span></span>](../../../wcf/feature-details/clients.md)
