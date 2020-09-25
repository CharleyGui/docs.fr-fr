---
title: Fonctions définies par l'utilisateur (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
ms.openlocfilehash: 9e5ad1f6edb0e719733edd2518c5d62a7fc6bdf7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180970"
---
# <a name="user-defined-functions-entity-sql"></a><span data-ttu-id="4b05d-102">Fonctions définies par l'utilisateur (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4b05d-102">User-Defined Functions (Entity SQL)</span></span>

<span data-ttu-id="4b05d-103">Entity SQL prend en charge l'appel de fonctions définies par l'utilisateur dans une requête.</span><span class="sxs-lookup"><span data-stu-id="4b05d-103">Entity SQL supports calling user-defined functions in a query.</span></span> <span data-ttu-id="4b05d-104">Vous pouvez définir ces fonctions inline avec la requête (consultez [Comment : appeler une fonction définie par l’utilisateur](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))) ou dans le cadre du modèle conceptuel (consultez Guide pratique [pour définir des fonctions personnalisées dans le modèle conceptuel](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))).</span><span class="sxs-lookup"><span data-stu-id="4b05d-104">You can define these functions inline with the query (see [How to: Call a User-Defined Function](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))) or as part of the conceptual model (see [How to: Define Custom Functions in the Conceptual Model](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))).</span></span> <span data-ttu-id="4b05d-105">Les fonctions de modèle conceptuel sont définies en tant que Entity SQL commande dans l’élément [DefiningExpression](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#definingexpression-element-csdl) d’un élément de [fonction](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#function-element-csdl) dans le modèle conceptuel.</span><span class="sxs-lookup"><span data-stu-id="4b05d-105">Conceptual model functions are defined as an Entity SQL command in the [DefiningExpression](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#definingexpression-element-csdl) element of a [Function](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#function-element-csdl) element in the conceptual model.</span></span>  
  
 <span data-ttu-id="4b05d-106">Entity SQL permet de définir des fonctions dans la commande de requête elle-même.</span><span class="sxs-lookup"><span data-stu-id="4b05d-106">Entity SQL enables you to define functions in the query command itself.</span></span> <span data-ttu-id="4b05d-107">L’opérateur de [fonction](function-entity-sql.md) définit des fonctions inline.</span><span class="sxs-lookup"><span data-stu-id="4b05d-107">The [FUNCTION](function-entity-sql.md) operator defines inline functions.</span></span> <span data-ttu-id="4b05d-108">Vous pouvez définir plusieurs fonctions dans une même commande et ces fonctions peuvent avoir le même nom de fonction, tant que les signatures des fonctions sont uniques.</span><span class="sxs-lookup"><span data-stu-id="4b05d-108">You can define multiple functions in a single command, and these functions can have the same function name, as long as the function signatures are unique.</span></span> <span data-ttu-id="4b05d-109">Pour plus d'informations, consultez [Function Overload Resolution](function-overload-resolution-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="4b05d-109">For more information, see [Function Overload Resolution](function-overload-resolution-entity-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b05d-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b05d-110">See also</span></span>

- [<span data-ttu-id="4b05d-111">Fonctions</span><span class="sxs-lookup"><span data-stu-id="4b05d-111">Functions</span></span>](functions-entity-sql.md)
