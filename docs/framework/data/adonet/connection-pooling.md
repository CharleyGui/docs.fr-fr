---
title: Regroupement de connexions
ms.date: 03/30/2017
ms.assetid: 955c057f-aea8-4ba8-aa6d-e3dfa18ba8d5
ms.openlocfilehash: c431011cf57fd9ef79c2f0a099ab1080116c571f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786715"
---
# <a name="connection-pooling"></a><span data-ttu-id="0ba1a-102">Regroupement de connexions</span><span class="sxs-lookup"><span data-stu-id="0ba1a-102">Connection Pooling</span></span>
<span data-ttu-id="0ba1a-103">Se connecter à une source de données peut prendre beaucoup de temps.</span><span class="sxs-lookup"><span data-stu-id="0ba1a-103">Connecting to a data source can be time consuming.</span></span> <span data-ttu-id="0ba1a-104">Pour réduire le coût de l’ouverture des connexions, ADO.NET utilise une technique d’optimisation appelée *regroupement de connexions*, qui réduit le coût de l’ouverture et de la fermeture à plusieurs reprises des connexions.</span><span class="sxs-lookup"><span data-stu-id="0ba1a-104">To minimize the cost of opening connections, ADO.NET uses an optimization technique called *connection pooling*, which minimizes the cost of repeatedly opening and closing connections.</span></span> <span data-ttu-id="0ba1a-105">Le regroupement de connexions est géré différemment pour les fournisseurs de données .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0ba1a-105">Connection pooling is handled differently for the .NET Framework data providers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0ba1a-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="0ba1a-106">In This Section</span></span>  
 [<span data-ttu-id="0ba1a-107">Regroupement de connexions SQL Server (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="0ba1a-107">SQL Server Connection Pooling (ADO.NET)</span></span>](sql-server-connection-pooling.md)  
 <span data-ttu-id="0ba1a-108">Fournit une vue d’ensemble du regroupement de connexions et décrit le fonctionnement du regroupement de connexions dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0ba1a-108">Provides an overview of connection pooling and describes how connection pooling works in SQL Server.</span></span>  
  
 [<span data-ttu-id="0ba1a-109">Regroupement de connexions OLE DB, ODBC et Oracle</span><span class="sxs-lookup"><span data-stu-id="0ba1a-109">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)  
 <span data-ttu-id="0ba1a-110">Décrit le regroupement de connexions pour les fournisseurs de données .NET Framework pour OLE DB, ODBC et Oracle.</span><span class="sxs-lookup"><span data-stu-id="0ba1a-110">Describes connection pooling for the .NET Framework Data Provider for OLE DB, the .NET Framework Data Provider for ODBC, and the .NET Framework Data Provider for Oracle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ba1a-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ba1a-111">See also</span></span>

- [<span data-ttu-id="0ba1a-112">Extraction et modification de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0ba1a-112">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="0ba1a-113">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0ba1a-113">ADO.NET Overview</span></span>](ado-net-overview.md)
