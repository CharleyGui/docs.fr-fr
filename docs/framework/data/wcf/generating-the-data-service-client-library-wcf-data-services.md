---
title: Génération de la bibliothèque client service de données (services de données WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: a6a388f837d00d63a39212843c3fa88b28482b26
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545805"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a><span data-ttu-id="40895-102">Génération de la bibliothèque client service de données (services de données WCF)</span><span class="sxs-lookup"><span data-stu-id="40895-102">Generating the Data Service Client Library (WCF Data Services)</span></span>
<span data-ttu-id="40895-103">Un service de données qui implémente le Open Data Protocol (OData) peut retourner un document de métadonnées de service qui décrit le modèle de données exposé par le flux OData.</span><span class="sxs-lookup"><span data-stu-id="40895-103">A data service that implements the Open Data Protocol (OData) can return a service metadata document that describes the data model exposed by the OData feed.</span></span> <span data-ttu-id="40895-104">Pour plus d’informations, consultez la section document de métadonnées de service dans l’article [OData : Overview](https://www.odata.org/documentation/odata-version-2-0/overview/) .</span><span class="sxs-lookup"><span data-stu-id="40895-104">For more information, see the Service Metadata Document section in the [OData: Overview](https://www.odata.org/documentation/odata-version-2-0/overview/) article.</span></span> <span data-ttu-id="40895-105">Vous pouvez utiliser la boîte de dialogue **Ajouter une référence de service** dans Visual Studio pour ajouter une référence à un service OData.</span><span class="sxs-lookup"><span data-stu-id="40895-105">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to an OData-based service.</span></span> <span data-ttu-id="40895-106">Lorsque vous utilisez cet outil pour ajouter une référence aux métadonnées retournées par un flux OData dans un projet client, il effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="40895-106">When you use this tool to add a reference to the metadata returned by an OData feed in a client project, it performs the following actions:</span></span>  
  
- <span data-ttu-id="40895-107">Demande le document de métadonnées du service de données et interprète les métadonnées retournées.</span><span class="sxs-lookup"><span data-stu-id="40895-107">Requests the service metadata document from the data service and interprets the returned metadata.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="40895-108">Les métadonnées retournées sont stockées dans le projet client sous forme de fichier .edmx.</span><span class="sxs-lookup"><span data-stu-id="40895-108">The returned metadata is stored in the client project as an .edmx file.</span></span> <span data-ttu-id="40895-109">Ce fichier .edmx ne peut pas s’ouvrir à l’aide d’Entity Data Model Designer parce qu’il n’a pas le même format que les fichiers .edmx utilisés par Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="40895-109">This .edmx file cannot be opened by using the Entity Data Model designer because it does not have the same format an .edmx file used by the Entity Framework.</span></span> <span data-ttu-id="40895-110">Vous pouvez consulter ce fichier de métadonnées à l'aide de l'éditeur XML ou d'un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="40895-110">You can view this metadata file by using the XML editor or any text editor.</span></span> <span data-ttu-id="40895-111">Pour plus d’informations, consultez [ \[ MC-EDMX \] : Entity Data Model pour le format d’empaquetage Data Services](/openspecs/windows_protocols/mc-edmx/5dff5e25-56a1-408b-9d44-bff6634c7d16).</span><span class="sxs-lookup"><span data-stu-id="40895-111">For more information, see [\[MC-EDMX\]: Entity Data Model for Data Services Packaging Format](/openspecs/windows_protocols/mc-edmx/5dff5e25-56a1-408b-9d44-bff6634c7d16).</span></span>
  
- <span data-ttu-id="40895-112">Génère une représentation du service comme une classe de conteneur d'entités qui hérite de <xref:System.Data.Services.Client.DataServiceContext>.</span><span class="sxs-lookup"><span data-stu-id="40895-112">Generates a representation of the service as an entity container class that inherits from <xref:System.Data.Services.Client.DataServiceContext>.</span></span> <span data-ttu-id="40895-113">Cette classe de conteneur d'entités générée ressemble au conteneur d'entités que génèrent les outils Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="40895-113">This generated entity container class resembles the entity container that the Entity Data Model tools generate.</span></span> <span data-ttu-id="40895-114">Pour plus d’informations, consultez [Vue d’ensemble d’Object Services (Entity Framework)](/previous-versions/bb386871(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="40895-114">For more information, see [Object Services Overview (Entity Framework)](/previous-versions/bb386871(v=vs.100)).</span></span>  
  
- <span data-ttu-id="40895-115">Génère des classes de données pour les types de modèles de données découverts dans les métadonnées de service.</span><span class="sxs-lookup"><span data-stu-id="40895-115">Generates data classes for the data model types that it discovers in the service metadata.</span></span>  
  
- <span data-ttu-id="40895-116">Ajoute une référence à l'assembly `System.Data.Services.Client` au projet.</span><span class="sxs-lookup"><span data-stu-id="40895-116">Adds a reference to the `System.Data.Services.Client` assembly to the project.</span></span>  
  
 <span data-ttu-id="40895-117">Pour plus d’informations, consultez [Comment : ajouter une référence de service de données](how-to-add-a-data-service-reference-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="40895-117">For more information, see [How to: Add a Data Service Reference](how-to-add-a-data-service-reference-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="40895-118">Les classes de service de données client peuvent également être générées à l’aide de l’outil [DataSvcUtil.exe](wcf-data-service-client-utility-datasvcutil-exe.md) à partir de l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="40895-118">The client data service classes can also be generated by using the [DataSvcUtil.exe](wcf-data-service-client-utility-datasvcutil-exe.md) tool at the command prompt.</span></span> <span data-ttu-id="40895-119">Pour plus d’informations, consultez [Comment : générer manuellement des classes de service de données client](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="40895-119">For more information, see [How to: Manually Generate Client Data Service Classes](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span></span>  
  
## <a name="client-data-type-mapping"></a><span data-ttu-id="40895-120">Mappage de type de données client</span><span class="sxs-lookup"><span data-stu-id="40895-120">Client Data Type Mapping</span></span>  
 <span data-ttu-id="40895-121">Quand vous utilisez la boîte de dialogue **Ajouter une référence de service** dans Visual Studio ou l' `DataSvcUtil.exe` outil pour générer des classes de données clientes basées sur un flux OData, les types de données .NET Framework sont mappés aux types primitifs à partir du modèle de données comme suit :</span><span class="sxs-lookup"><span data-stu-id="40895-121">When you use the **Add Service Reference** dialog in Visual Studio or the `DataSvcUtil.exe` tool to generate client data classes that are based on an OData feed, the .NET Framework data types are mapped to the primitive types from the data model as follows:</span></span>  
  
|<span data-ttu-id="40895-122">Type de modèle de données</span><span class="sxs-lookup"><span data-stu-id="40895-122">Data model type</span></span>|<span data-ttu-id="40895-123">Type de données .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="40895-123">.NET Framework data type</span></span>|  
|---------------------|------------------------------|  
|`Edm.Binary`|<span data-ttu-id="40895-124"><xref:System.Byte> `[]`</span><span class="sxs-lookup"><span data-stu-id="40895-124"><xref:System.Byte> `[]`</span></span>|  
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
  
 <span data-ttu-id="40895-125">Pour plus d’informations, consultez la section types de données primitifs de l’article [OData : vue d’ensemble](https://www.odata.org/documentation/odata-version-2-0/overview/) .</span><span class="sxs-lookup"><span data-stu-id="40895-125">For more information, see the Primitive Data Types section in the [OData: Overview](https://www.odata.org/documentation/odata-version-2-0/overview/) article.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="40895-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40895-126">See also</span></span>

- [<span data-ttu-id="40895-127">Bibliothèque client services de données WCF</span><span class="sxs-lookup"><span data-stu-id="40895-127">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)
- [<span data-ttu-id="40895-128">Démarrage rapide</span><span class="sxs-lookup"><span data-stu-id="40895-128">Quickstart</span></span>](quickstart-wcf-data-services.md)
