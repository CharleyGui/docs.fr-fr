---
title: Génération de la bibliothèque client service de données (services de données WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: f73ea93fe76f31c81935dbfb29183c247e41d8cd
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975286"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a><span data-ttu-id="92cf4-102">Génération de la bibliothèque client service de données (services de données WCF)</span><span class="sxs-lookup"><span data-stu-id="92cf4-102">Generating the Data Service Client Library (WCF Data Services)</span></span>
<span data-ttu-id="92cf4-103">Un service de données qui implémente le Open Data Protocol (OData) peut retourner un document de métadonnées de service qui décrit le modèle de données exposé par le flux OData.</span><span class="sxs-lookup"><span data-stu-id="92cf4-103">A data service that implements the Open Data Protocol (OData) can return a service metadata document that describes the data model exposed by the OData feed.</span></span> <span data-ttu-id="92cf4-104">Pour plus d’informations, consultez [OData : document de métadonnées du service](https://go.microsoft.com/fwlink/?LinkId=186070).</span><span class="sxs-lookup"><span data-stu-id="92cf4-104">For more information, see [OData: Service Metadata Document](https://go.microsoft.com/fwlink/?LinkId=186070).</span></span> <span data-ttu-id="92cf4-105">Vous pouvez utiliser la boîte de dialogue **Ajouter une référence de service** dans Visual Studio pour ajouter une référence à un service OData.</span><span class="sxs-lookup"><span data-stu-id="92cf4-105">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to an OData-based service.</span></span> <span data-ttu-id="92cf4-106">Lorsque vous utilisez cet outil pour ajouter une référence aux métadonnées retournées par un flux OData dans un projet client, il effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="92cf4-106">When you use this tool to add a reference to the metadata returned by an OData feed in a client project, it performs the following actions:</span></span>  
  
- <span data-ttu-id="92cf4-107">Demande le document de métadonnées du service de données et interprète les métadonnées retournées.</span><span class="sxs-lookup"><span data-stu-id="92cf4-107">Requests the service metadata document from the data service and interprets the returned metadata.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="92cf4-108">Les métadonnées retournées sont stockées dans le projet client sous forme de fichier .edmx.</span><span class="sxs-lookup"><span data-stu-id="92cf4-108">The returned metadata is stored in the client project as an .edmx file.</span></span> <span data-ttu-id="92cf4-109">Ce fichier .edmx ne peut pas s’ouvrir à l’aide d’Entity Data Model Designer parce qu’il n’a pas le même format que les fichiers .edmx utilisés par Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="92cf4-109">This .edmx file cannot be opened by using the Entity Data Model designer because it does not have the same format an .edmx file used by the Entity Framework.</span></span> <span data-ttu-id="92cf4-110">Vous pouvez consulter ce fichier de métadonnées à l'aide de l'éditeur XML ou d'un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="92cf4-110">You can view this metadata file by using the XML editor or any text editor.</span></span> <span data-ttu-id="92cf4-111">Pour plus d’informations, consultez la spécification [\[MC-EDMX\]: Entity Data Model pour le format d’Empaquetage Data Services](https://go.microsoft.com/fwlink/?LinkID=178833)</span><span class="sxs-lookup"><span data-stu-id="92cf4-111">For more information, see the [\[MC-EDMX\]: Entity Data Model for Data Services Packaging Format](https://go.microsoft.com/fwlink/?LinkID=178833) specification</span></span>  
  
- <span data-ttu-id="92cf4-112">Génère une représentation du service comme une classe de conteneur d'entités qui hérite de <xref:System.Data.Services.Client.DataServiceContext>.</span><span class="sxs-lookup"><span data-stu-id="92cf4-112">Generates a representation of the service as an entity container class that inherits from <xref:System.Data.Services.Client.DataServiceContext>.</span></span> <span data-ttu-id="92cf4-113">Cette classe de conteneur d'entités générée ressemble au conteneur d'entités que génèrent les outils Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="92cf4-113">This generated entity container class resembles the entity container that the Entity Data Model tools generate.</span></span> <span data-ttu-id="92cf4-114">Pour plus d’informations, consultez [Vue d’ensemble d’Object Services (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="92cf4-114">For more information, see [Object Services Overview (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)).</span></span>  
  
- <span data-ttu-id="92cf4-115">Génère des classes de données pour les types de modèles de données découverts dans les métadonnées de service.</span><span class="sxs-lookup"><span data-stu-id="92cf4-115">Generates data classes for the data model types that it discovers in the service metadata.</span></span>  
  
- <span data-ttu-id="92cf4-116">Ajoute une référence à l'assembly `System.Data.Services.Client` au projet.</span><span class="sxs-lookup"><span data-stu-id="92cf4-116">Adds a reference to the `System.Data.Services.Client` assembly to the project.</span></span>  
  
 <span data-ttu-id="92cf4-117">Pour plus d’informations, consultez [Comment : ajouter une référence de service de données](how-to-add-a-data-service-reference-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="92cf4-117">For more information, see [How to: Add a Data Service Reference](how-to-add-a-data-service-reference-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="92cf4-118">Les classes de service de données client peuvent également être générées à l’aide de l’outil [outil DataSvcUtil. exe](wcf-data-service-client-utility-datasvcutil-exe.md) à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="92cf4-118">The client data service classes can also be generated by using the [DataSvcUtil.exe](wcf-data-service-client-utility-datasvcutil-exe.md) tool at the command prompt.</span></span> <span data-ttu-id="92cf4-119">Pour plus d’informations, consultez [Comment : générer manuellement des classes de service de données client](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="92cf4-119">For more information, see [How to: Manually Generate Client Data Service Classes](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span></span>  
  
## <a name="client-data-type-mapping"></a><span data-ttu-id="92cf4-120">Mappage de type de données client</span><span class="sxs-lookup"><span data-stu-id="92cf4-120">Client Data Type Mapping</span></span>  
 <span data-ttu-id="92cf4-121">Quand vous utilisez la boîte de dialogue **Ajouter une référence de service** dans Visual Studio ou l’outil `DataSvcUtil.exe` pour générer des classes de données clientes basées sur un flux OData, les types de données .NET Framework sont mappés aux types primitifs à partir du modèle de données comme suit :</span><span class="sxs-lookup"><span data-stu-id="92cf4-121">When you use the **Add Service Reference** dialog in Visual Studio or the `DataSvcUtil.exe` tool to generate client data classes that are based on an OData feed, the .NET Framework data types are mapped to the primitive types from the data model as follows:</span></span>  
  
|<span data-ttu-id="92cf4-122">Type de modèle de données</span><span class="sxs-lookup"><span data-stu-id="92cf4-122">Data model type</span></span>|<span data-ttu-id="92cf4-123">Types de données .NET Framework</span><span class="sxs-lookup"><span data-stu-id="92cf4-123">.NET Framework data type</span></span>|  
|---------------------|------------------------------|  
|`Edm.Binary`|<span data-ttu-id="92cf4-124"><xref:System.Byte> `[]`</span><span class="sxs-lookup"><span data-stu-id="92cf4-124"><xref:System.Byte> `[]`</span></span>|  
|`Edm.Boolean`|<xref:System.Boolean>|  
|`Edm.Byte`|<xref:System.Byte>|  
|`Edm.DateTime`|<xref:System.DateTime>|  
|`Edm.Decimal`|<xref:System.Decimal>|  
|`Edm.Double`|<xref:System.Double>|  
|`Edm.Guid`|<xref:System.Guid>|  
|`Edm.Int16`|<xref:System.Int16>|  
|`Edm.Int32`|<xref:System.Int32>|  
|`Edm.Int64`|<xref:System.Int64>|  
|`Edm.SByte`|<xref:System.SByte>|  
|`Edm.Single`|<xref:System.Single>|  
|`Edm.String`|<xref:System.String>|  
  
 <span data-ttu-id="92cf4-125">Pour plus d’informations, consultez [OData : types de données primitifs](https://go.microsoft.com/fwlink/?LinkId=186072).</span><span class="sxs-lookup"><span data-stu-id="92cf4-125">For more information, see [OData: Primitive Data Types](https://go.microsoft.com/fwlink/?LinkId=186072).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92cf4-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92cf4-126">See also</span></span>

- [<span data-ttu-id="92cf4-127">Bibliothèque cliente WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="92cf4-127">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)
- [<span data-ttu-id="92cf4-128">Démarrage rapide</span><span class="sxs-lookup"><span data-stu-id="92cf4-128">Quickstart</span></span>](quickstart-wcf-data-services.md)
