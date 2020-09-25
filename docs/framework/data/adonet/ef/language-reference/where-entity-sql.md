---
title: WHERE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 1907b8786622d3c8019c75916f997c830cc07cfb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180957"
---
# <a name="where-entity-sql"></a><span data-ttu-id="6d1da-102">WHERE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6d1da-102">WHERE (Entity SQL)</span></span>

<span data-ttu-id="6d1da-103">La clause WHERE est appliquée directement après la clause [from](from-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="6d1da-103">The WHERE clause is applied directly after the [FROM](from-entity-sql.md) clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d1da-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d1da-104">Syntax</span></span>  
  
```sql  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="6d1da-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="6d1da-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="6d1da-106">Type booléen.</span><span class="sxs-lookup"><span data-stu-id="6d1da-106">A Boolean type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d1da-107">Notes</span><span class="sxs-lookup"><span data-stu-id="6d1da-107">Remarks</span></span>  

 <span data-ttu-id="6d1da-108">La clause WHERE a la même sémantique que celle décrite dans Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="6d1da-108">The WHERE clause has the same semantics as described for Transact-SQL.</span></span> <span data-ttu-id="6d1da-109">Elle restreint le nombre d’objets générés par l’expression de requête en limitant les éléments des collections sources à ceux qui répondent à la condition.</span><span class="sxs-lookup"><span data-stu-id="6d1da-109">It restricts the objects produced by the query expression by limiting the elements of the source collections to those that pass the condition.</span></span>  
  
```sql  
select c from cs as c where e  
```  
  
 <span data-ttu-id="6d1da-110">L'expression `e` doit être de type booléen.</span><span class="sxs-lookup"><span data-stu-id="6d1da-110">The expression `e` must have the type Boolean.</span></span>  
  
 <span data-ttu-id="6d1da-111">La clause WHERE est appliquée directement après la clause FROM et avant tout regroupement, classement ou projection éventuel.</span><span class="sxs-lookup"><span data-stu-id="6d1da-111">The WHERE clause is applied directly after the FROM clause and before any grouping, ordering, or projection takes place.</span></span> <span data-ttu-id="6d1da-112">Tous les noms d'éléments définis dans la clause FROM sont visibles pour l'expression de la clause WHERE.</span><span class="sxs-lookup"><span data-stu-id="6d1da-112">All element names defined in the FROM clause are visible to the expression of the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d1da-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d1da-113">See also</span></span>

- [<span data-ttu-id="6d1da-114">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="6d1da-114">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="6d1da-115">Expressions de requête</span><span class="sxs-lookup"><span data-stu-id="6d1da-115">Query Expressions</span></span>](query-expressions-entity-sql.md)
