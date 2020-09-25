---
title: Expressions de requête (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
ms.openlocfilehash: ca6b79b4b3d3326a74780345decf58367596adb0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175601"
---
# <a name="query-expressions-entity-sql"></a><span data-ttu-id="76fac-102">Expressions de requête (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="76fac-102">Query Expressions (Entity SQL)</span></span>

<span data-ttu-id="76fac-103">Une expression de requête combine un grand nombre d'opérateurs de requête différents dans une syntaxe unique.</span><span class="sxs-lookup"><span data-stu-id="76fac-103">A query expression combines many different query operators into a single syntax.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="76fac-104">fournit différents genres d’expressions, notamment les [littéraux](literals-entity-sql.md), les [paramètres](parameters-entity-sql.md), les [variables](variables-entity-sql.md), les opérateurs, les [fonctions](functions-entity-sql.md), les opérateurs de jeu, etc.</span><span class="sxs-lookup"><span data-stu-id="76fac-104">provides various kinds of expressions, including the following: [literals](literals-entity-sql.md), [parameters](parameters-entity-sql.md), [variables](variables-entity-sql.md), operators, [functions](functions-entity-sql.md), set operators, and so on.</span></span> <span data-ttu-id="76fac-105">Pour plus d’informations, consultez [Entity SQL référence](entity-sql-reference.md).</span><span class="sxs-lookup"><span data-stu-id="76fac-105">For more information, see [Entity SQL Reference](entity-sql-reference.md).</span></span>  
  
## <a name="clauses"></a><span data-ttu-id="76fac-106">Clauses</span><span class="sxs-lookup"><span data-stu-id="76fac-106">Clauses</span></span>  

 <span data-ttu-id="76fac-107">Une expression de requête est constituée d’une série de clauses qui appliquent des opérations successives à une collection d’objets.</span><span class="sxs-lookup"><span data-stu-id="76fac-107">A query expression is composed of a series of clauses that apply successive operations to a collection of objects.</span></span> <span data-ttu-id="76fac-108">Elles sont basées sur les mêmes clauses dans une instruction SQL SELECT standard : [Select](select-entity-sql.md), [from](from-entity-sql.md), [Where](where-entity-sql.md), [Group by](group-by-entity-sql.md), [having](having-entity-sql.md)et [order by](order-by-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="76fac-108">They are based on the same clauses found in standard a SQL select statement: [SELECT](select-entity-sql.md), [FROM](from-entity-sql.md), [WHERE](where-entity-sql.md), [GROUP BY](group-by-entity-sql.md), [HAVING](having-entity-sql.md), and [ORDER BY](order-by-entity-sql.md).</span></span>  
  
## <a name="scope"></a><span data-ttu-id="76fac-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="76fac-109">Scope</span></span>  

 <span data-ttu-id="76fac-110">Les noms définis dans la clause FROM sont introduits dans l'étendue FROM dans l'ordre de leur apparition, de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="76fac-110">Names defined in the FROM clause are introduced into the FROM scope in order of appearance, left to right.</span></span> <span data-ttu-id="76fac-111">Dans la liste JOIN, les expressions peuvent faire référence aux noms définis précédemment dans la liste.</span><span class="sxs-lookup"><span data-stu-id="76fac-111">In the JOIN list, expressions can refer to names defined earlier in the list.</span></span> <span data-ttu-id="76fac-112">Les propriétés publiques des éléments identifiés dans la clause FROM ne sont pas ajoutées à l'étendue FROM : elles doivent toujours être référencées par le biais du nom qualifié par un alias.</span><span class="sxs-lookup"><span data-stu-id="76fac-112">Public properties of elements identified in the FROM clause are not added to the FROM scope: They must be always referenced through the alias-qualified name.</span></span> <span data-ttu-id="76fac-113">Normalement, toutes les parties de l'expression select sont considérées comme faisant partie de l'étendue FROM.</span><span class="sxs-lookup"><span data-stu-id="76fac-113">Normally, all parts of the select expression are considered within the FROM scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76fac-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="76fac-114">See also</span></span>

- [<span data-ttu-id="76fac-115">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="76fac-115">Entity SQL Reference</span></span>](entity-sql-reference.md)
