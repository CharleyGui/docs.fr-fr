---
title: Regroupement de connexions
description: En savoir plus sur le regroupement de connexions, une technique d’optimisation utilisée par ADO.NET pour réduire le coût de l’ouverture des connexions aux sources de données.
ms.date: 03/30/2017
ms.assetid: 955c057f-aea8-4ba8-aa6d-e3dfa18ba8d5
ms.openlocfilehash: b8f89dfda7edbde14dbb5945f10f2284ac43c3d8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287088"
---
# <a name="connection-pooling"></a><span data-ttu-id="5d369-103">Regroupement de connexions</span><span class="sxs-lookup"><span data-stu-id="5d369-103">Connection Pooling</span></span>
<span data-ttu-id="5d369-104">Se connecter à une source de données peut prendre beaucoup de temps.</span><span class="sxs-lookup"><span data-stu-id="5d369-104">Connecting to a data source can be time consuming.</span></span> <span data-ttu-id="5d369-105">Pour réduire le coût de l’ouverture des connexions, ADO.NET utilise une technique d’optimisation appelée *regroupement de connexions*, qui réduit le coût de l’ouverture et de la fermeture à plusieurs reprises des connexions.</span><span class="sxs-lookup"><span data-stu-id="5d369-105">To minimize the cost of opening connections, ADO.NET uses an optimization technique called *connection pooling*, which minimizes the cost of repeatedly opening and closing connections.</span></span> <span data-ttu-id="5d369-106">Le regroupement de connexions est géré différemment pour les fournisseurs de données .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5d369-106">Connection pooling is handled differently for the .NET Framework data providers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5d369-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5d369-107">In This Section</span></span>  
 [<span data-ttu-id="5d369-108">Regroupement de connexions SQL Server (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="5d369-108">SQL Server Connection Pooling (ADO.NET)</span></span>](sql-server-connection-pooling.md)  
 <span data-ttu-id="5d369-109">Fournit une vue d’ensemble du regroupement de connexions et décrit le fonctionnement du regroupement de connexions dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5d369-109">Provides an overview of connection pooling and describes how connection pooling works in SQL Server.</span></span>  
  
 [<span data-ttu-id="5d369-110">Regroupement de connexions OLE DB, ODBC et Oracle</span><span class="sxs-lookup"><span data-stu-id="5d369-110">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)  
 <span data-ttu-id="5d369-111">Décrit le regroupement de connexions pour les fournisseurs de données .NET Framework pour OLE DB, ODBC et Oracle.</span><span class="sxs-lookup"><span data-stu-id="5d369-111">Describes connection pooling for the .NET Framework Data Provider for OLE DB, the .NET Framework Data Provider for ODBC, and the .NET Framework Data Provider for Oracle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d369-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d369-112">See also</span></span>

- [<span data-ttu-id="5d369-113">Extraction et modification de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5d369-113">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="5d369-114">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5d369-114">ADO.NET Overview</span></span>](ado-net-overview.md)
