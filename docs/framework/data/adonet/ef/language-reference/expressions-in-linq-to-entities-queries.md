---
title: Expressions dans les requêtes LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: 5262d2bca07525aba6db5303e730c8b358641d52
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250973"
---
# <a name="expressions-in-linq-to-entities-queries"></a><span data-ttu-id="badca-102">Expressions dans les requêtes LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="badca-102">Expressions in LINQ to Entities Queries</span></span>
<span data-ttu-id="badca-103">Une expression est un fragment de code qui peut correspondre à une valeur, un objet, une méthode ou un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="badca-103">An expression is a fragment of code that can be evaluated to a single value, object, method, or namespace.</span></span> <span data-ttu-id="badca-104">Elle peut contenir une valeur littérale, un appel de méthode, un opérateur et ses opérandes ou un nom simple.</span><span class="sxs-lookup"><span data-stu-id="badca-104">Expressions can contain a literal value, a method call, an operator and its operands, or a simple name.</span></span> <span data-ttu-id="badca-105">Un nom simple peut être le nom d'une variable, d'un membre de type, d'un paramètre de méthode, d'un espace de noms ou d'un type.</span><span class="sxs-lookup"><span data-stu-id="badca-105">Simple names can be the name of a variable, type member, method parameter, namespace or type.</span></span> <span data-ttu-id="badca-106">Les expressions peuvent utiliser des opérateurs qui à leur tour utilisent d'autres expressions comme des paramètres, ou des appels de méthode dont les paramètres sont à leur tour d'autres appels de méthode.</span><span class="sxs-lookup"><span data-stu-id="badca-106">Expressions can use operators that in turn use other expressions as parameters, or method calls whose parameters are in turn other method calls.</span></span> <span data-ttu-id="badca-107">Par conséquent, les expressions peuvent être simples ou très complexes.</span><span class="sxs-lookup"><span data-stu-id="badca-107">Therefore, expressions can range from simple to very complex.</span></span>  
  
 <span data-ttu-id="badca-108">Dans LINQ to Entities requêtes, les expressions peuvent contenir tout ce qui est autorisé par <xref:System.Linq.Expressions> les types dans l’espace de noms, y compris les expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="badca-108">In LINQ to Entities queries, expressions can contain anything allowed by the types within the <xref:System.Linq.Expressions> namespace, including lambda expressions.</span></span> <span data-ttu-id="badca-109">Les expressions qui peuvent être utilisées dans les requêtes LINQ to Entities sont un sur-ensemble des expressions qui peuvent être utilisées pour [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]interroger le.</span><span class="sxs-lookup"><span data-stu-id="badca-109">The expressions that can be used in LINQ to Entities queries are a superset of the expressions that can be used to query the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="badca-110">Les expressions qui font partie des requêtes sur [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] le sont limitées aux opérations prises `ObjectQuery<T>` en charge par et la source de données sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="badca-110">Expressions that are part of queries against the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are limited to operations supported by `ObjectQuery<T>` and the underlying data source.</span></span>  
  
 <span data-ttu-id="badca-111">Dans l'exemple suivant, la comparaison dans la clause `Where` est une expression :</span><span class="sxs-lookup"><span data-stu-id="badca-111">In the following example, the comparison in the `Where` clause is an expression:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
> <span data-ttu-id="badca-112">Les constructions de langage spécifiques, telles C# `unchecked`que, n’ont aucune signification dans LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="badca-112">Specific language constructs, such as C# `unchecked`, have no meaning in LINQ to Entities.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="badca-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="badca-113">In This Section</span></span>  
 [<span data-ttu-id="badca-114">Expressions de constantes</span><span class="sxs-lookup"><span data-stu-id="badca-114">Constant Expressions</span></span>](constant-expressions.md)  
  
 [<span data-ttu-id="badca-115">Expressions de comparaison</span><span class="sxs-lookup"><span data-stu-id="badca-115">Comparison Expressions</span></span>](comparison-expressions.md)  
  
 [<span data-ttu-id="badca-116">Comparaisons Null</span><span class="sxs-lookup"><span data-stu-id="badca-116">Null Comparisons</span></span>](null-comparisons.md)  
  
 [<span data-ttu-id="badca-117">Expressions d’initialisation</span><span class="sxs-lookup"><span data-stu-id="badca-117">Initialization Expressions</span></span>](initialization-expressions.md)  
  
 [<span data-ttu-id="badca-118">Relations, propriétés de navigation et clés étrangères</span><span class="sxs-lookup"><span data-stu-id="badca-118">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)  
  
## <a name="see-also"></a><span data-ttu-id="badca-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="badca-119">See also</span></span>

- [<span data-ttu-id="badca-120">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="badca-120">ADO.NET Entity Framework</span></span>](../index.md)
