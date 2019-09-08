---
title: Données binaires et à valeurs élevées SQL Server
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: 4d941ad6b7865112b45fd8c20ad89e9236e17b9d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791672"
---
# <a name="sql-server-binary-and-large-value-data"></a><span data-ttu-id="f667c-102">Données binaires et à valeurs élevées SQL Server</span><span class="sxs-lookup"><span data-stu-id="f667c-102">SQL Server Binary and Large-Value Data</span></span>
<span data-ttu-id="f667c-103">SQL Server fournit le spécificateur `max`, qui développe la capacité de stockage des types de données `varchar`, `nvarchar` et `varbinary`.</span><span class="sxs-lookup"><span data-stu-id="f667c-103">SQL Server provides the `max` specifier, which expands the storage capacity of the `varchar`, `nvarchar`, and `varbinary` data types.</span></span> <span data-ttu-id="f667c-104">`varchar(max)`, `nvarchar(max)` et`varbinary(max)` sont collectivement appelés *types de données de valeur élevée*.</span><span class="sxs-lookup"><span data-stu-id="f667c-104">`varchar(max)`, `nvarchar(max)`, and `varbinary(max)` are collectively called *large-value data types*.</span></span> <span data-ttu-id="f667c-105">Les types de données de valeur élevée permettent de stocker jusqu'à 2^31-1 octets de données.</span><span class="sxs-lookup"><span data-stu-id="f667c-105">You can use the large-value data types to store up to 2^31-1 bytes of data.</span></span>  
  
 <span data-ttu-id="f667c-106">SQL Server 2008 introduit l'attribut FILESTREAM, qui n'est pas un type de données, mais plutôt un attribut pouvant être défini sur une colonne et permettant alors de stocker des données de valeur élevée dans le système de fichiers et non dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="f667c-106">SQL Server 2008 introduces the FILESTREAM attribute, which is not a data type, but rather an attribute that can be defined on a column, allowing large-value data to be stored on the file system instead of in the database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f667c-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="f667c-107">In This Section</span></span>  
 [<span data-ttu-id="f667c-108">Modification de données de valeurs élevées (max) dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f667c-108">Modifying Large-Value (max) Data in ADO.NET</span></span>](modifying-large-value-max-data.md)  
 <span data-ttu-id="f667c-109">Décrit comment utiliser les types de données de valeur volumineux.</span><span class="sxs-lookup"><span data-stu-id="f667c-109">Describes how to work with the large-value data types.</span></span>  
  
 [<span data-ttu-id="f667c-110">Données FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="f667c-110">FILESTREAM Data</span></span>](filestream-data.md)  
 <span data-ttu-id="f667c-111">Décrit comment utiliser les données de valeur élevée stockées dans SQL Server 2008 avec l'attribut FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="f667c-111">Describes how to work with large-value data stored in SQL Server 2008 with the FILESTREAM attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f667c-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f667c-112">See also</span></span>

- [<span data-ttu-id="f667c-113">Types de données SQL Server et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f667c-113">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)
- [<span data-ttu-id="f667c-114">Opérations sur les données SQL Server dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f667c-114">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="f667c-115">Extraction et modification de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f667c-115">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="f667c-116">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f667c-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
