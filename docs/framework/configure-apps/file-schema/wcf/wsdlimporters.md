---
title: <wsdlImporters>
ms.date: 03/30/2017
ms.assetid: 270c7f93-eab7-47b6-8b94-ac3f5b7f17e4
ms.openlocfilehash: da9ab00c86e7f2657bfc28724d328ccbbc6957b1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915164"
---
# <a name="wsdlimporters"></a><span data-ttu-id="b922b-101">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="b922b-101">\<wsdlImporters></span></span>
<span data-ttu-id="b922b-102">Cet élément de configuration indique tous les importateurs WSDL qui importent des métadonnées Web Services Description Language (WSDL) 1.1 avec des pièces jointes WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="b922b-102">This configuration element specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="b922b-103">Chaque élément enfant est un <`wsdlImporter`> qui spécifie la façon d’importer des métadonnées et de convertir ces informations en différentes classes représentant les informations de contrat et de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="b922b-103">Each child element is a <`wsdlImporter`> that specifies the way to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="b922b-104">Il peut importer sélectivement des informations de contrat et de point de terminaison ainsi que des propriétés qui exposent toute erreur d'importation et accepte des informations de types liées au processus d'importation et de conversion.</span><span class="sxs-lookup"><span data-stu-id="b922b-104">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="b922b-105">Il prend également en charge les informations et les propriétés de liaison qui donnent accès aux documents de stratégie, documents WSDL, extensions WSDL et documents de schéma XML.</span><span class="sxs-lookup"><span data-stu-id="b922b-105">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b922b-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b922b-106">See also</span></span>

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="b922b-107">Configuration du client WCF</span><span class="sxs-lookup"><span data-stu-id="b922b-107">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="b922b-108">Clients</span><span class="sxs-lookup"><span data-stu-id="b922b-108">Clients</span></span>](../../../wcf/feature-details/clients.md)
