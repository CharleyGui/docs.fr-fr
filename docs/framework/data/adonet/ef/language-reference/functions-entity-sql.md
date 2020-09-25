---
title: Fonctions (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 52b3d776-5acc-4f69-b614-5a43ce56ef9f
ms.openlocfilehash: bef959ae6a835b5d1d696162528a8f904c59e8e5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201068"
---
# <a name="functions-entity-sql"></a><span data-ttu-id="0d414-102">Fonctions (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0d414-102">Functions (Entity SQL)</span></span>

<span data-ttu-id="0d414-103">Entity SQL prend en charge les fonctions définies par l'utilisateur, les fonctions canoniques et les fonctions spécifiques au fournisseur.</span><span class="sxs-lookup"><span data-stu-id="0d414-103">Entity SQL supports user-defined functions, canonical functions, and provider-specific functions.</span></span> <span data-ttu-id="0d414-104">Les fonctions définies par l'utilisateur sont spécifiées dans le modèle conceptuel ou inline dans la requête.</span><span class="sxs-lookup"><span data-stu-id="0d414-104">User-defined functions are specified in the conceptual model or inline in the query.</span></span> <span data-ttu-id="0d414-105">Pour plus d’informations, consultez [fonctions définies par l’utilisateur](user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="0d414-105">For more information, see [User-Defined Functions](user-defined-functions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="0d414-106">Les fonctions canoniques sont prédéfinies dans Entity Framework et doivent être prises en charge par les fournisseurs de données.</span><span class="sxs-lookup"><span data-stu-id="0d414-106">Canonical functions are predefined in the Entity Framework and should be supported by data providers.</span></span> <span data-ttu-id="0d414-107">Les commandes Entity SQL échouent si un utilisateur appelle une fonction qui n'est pas prise en charge par un fournisseur.</span><span class="sxs-lookup"><span data-stu-id="0d414-107">Entity SQL commands will fail if a user calls a function that is not supported by a provider.</span></span> <span data-ttu-id="0d414-108">Par conséquent, les fonctions canoniques sont généralement recommandées par rapport aux fonctions spécifiques au magasin, qui se trouvent dans un espace de noms spécifique au fournisseur.</span><span class="sxs-lookup"><span data-stu-id="0d414-108">Therefore, canonical functions are generally recommended over store-specific functions, which are in a provider-specific namespace.</span></span> <span data-ttu-id="0d414-109">Pour plus d’informations, consultez [fonctions canoniques](canonical-functions.md).</span><span class="sxs-lookup"><span data-stu-id="0d414-109">For more information, see [Canonical Functions](canonical-functions.md).</span></span>  
  
 <span data-ttu-id="0d414-110">Le fournisseur managé Client Microsoft SQL fournit un jeu de fonctions spécifiques au fournisseur.</span><span class="sxs-lookup"><span data-stu-id="0d414-110">The Microsoft SQL Client Managed Provider provides a set of provider-specific functions.</span></span> <span data-ttu-id="0d414-111">Pour plus d’informations, consultez [SqlClient pour les fonctions de Entity Framework](../sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="0d414-111">For more information, see [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0d414-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="0d414-112">In This Section</span></span>  

 [<span data-ttu-id="0d414-113">Fonctions définies par l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="0d414-113">User-Defined Functions</span></span>](user-defined-functions-entity-sql.md)  
  
 [<span data-ttu-id="0d414-114">Résolution de surcharge des fonctions</span><span class="sxs-lookup"><span data-stu-id="0d414-114">Function Overload Resolution</span></span>](function-overload-resolution-entity-sql.md)  
  
 [<span data-ttu-id="0d414-115">Fonctions d’agrégation</span><span class="sxs-lookup"><span data-stu-id="0d414-115">Aggregate Functions</span></span>](../aggregate-functions-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="0d414-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d414-116">See also</span></span>

- [<span data-ttu-id="0d414-117">Vue d'ensemble d'Entity SQL</span><span class="sxs-lookup"><span data-stu-id="0d414-117">Entity SQL Overview</span></span>](entity-sql-overview.md)
