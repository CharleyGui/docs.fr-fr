---
title: <wsdlImporters>
ms.date: 03/30/2017
ms.assetid: 270c7f93-eab7-47b6-8b94-ac3f5b7f17e4
ms.openlocfilehash: da9ab00c86e7f2657bfc28724d328ccbbc6957b1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "69915164"
---
# \<wsdlImporters>
<span data-ttu-id="3f5be-101">Cet élément de configuration indique tous les importateurs WSDL qui importent des métadonnées Web Services Description Language (WSDL) 1.1 avec des pièces jointes WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="3f5be-101">This configuration element specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="3f5be-102">Chaque élément enfant est un <`wsdlImporter`> qui spécifie la façon d’importer des métadonnées et de convertir ces informations en différentes classes représentant les informations de contrat et de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="3f5be-102">Each child element is a <`wsdlImporter`> that specifies the way to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="3f5be-103">Il peut importer sélectivement des informations de contrat et de point de terminaison ainsi que des propriétés qui exposent toute erreur d'importation et accepte des informations de types liées au processus d'importation et de conversion.</span><span class="sxs-lookup"><span data-stu-id="3f5be-103">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="3f5be-104">Il prend également en charge les informations et les propriétés de liaison qui donnent accès aux documents de stratégie, documents WSDL, extensions WSDL et documents de schéma XML.</span><span class="sxs-lookup"><span data-stu-id="3f5be-104">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f5be-105">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f5be-105">See also</span></span>

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="3f5be-106">Configuration client WCF</span><span class="sxs-lookup"><span data-stu-id="3f5be-106">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="3f5be-107">Clients</span><span class="sxs-lookup"><span data-stu-id="3f5be-107">Clients</span></span>](../../../wcf/feature-details/clients.md)
