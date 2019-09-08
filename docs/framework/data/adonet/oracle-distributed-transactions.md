---
title: Transactions distribuées Oracle
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: 6f910f1dbbe448352c0edd5d1b80df659ac453d4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795150"
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="7ceb3-102">Transactions distribuées Oracle</span><span class="sxs-lookup"><span data-stu-id="7ceb3-102">Oracle Distributed Transactions</span></span>
<span data-ttu-id="7ceb3-103">L'objet <xref:System.Data.OracleClient.OracleConnection> s'inscrit automatiquement dans une transaction distribuée existante s'il détermine qu'une transaction est active.</span><span class="sxs-lookup"><span data-stu-id="7ceb3-103">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="7ceb3-104">L’inscription automatique dans une transaction se produit lorsque la connexion est ouverte et extraite du pool de connexions.</span><span class="sxs-lookup"><span data-stu-id="7ceb3-104">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="7ceb3-105">Vous pouvez désactiver l'inscription automatique dans des transactions existantes en spécifiant</span><span class="sxs-lookup"><span data-stu-id="7ceb3-105">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```  
Enlist=false  
```  
  
 <span data-ttu-id="7ceb3-106">comme paramètre de chaîne de connexion pour un <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="7ceb3-106">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ceb3-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ceb3-107">See also</span></span>

- [<span data-ttu-id="7ceb3-108">Oracle et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7ceb3-108">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="7ceb3-109">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7ceb3-109">ADO.NET Overview</span></span>](ado-net-overview.md)
