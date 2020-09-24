---
title: Expressions dans les requêtes LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: f65759d37661271588d56965eadcccbe997623f4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166649"
---
# <a name="expressions-in-linq-to-entities-queries"></a><span data-ttu-id="00938-102">Expressions dans les requêtes LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="00938-102">Expressions in LINQ to Entities Queries</span></span>

<span data-ttu-id="00938-103">Une expression est un fragment de code qui peut correspondre à une valeur, un objet, une méthode ou un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="00938-103">An expression is a fragment of code that can be evaluated to a single value, object, method, or namespace.</span></span> <span data-ttu-id="00938-104">Elle peut contenir une valeur littérale, un appel de méthode, un opérateur et ses opérandes ou un nom simple.</span><span class="sxs-lookup"><span data-stu-id="00938-104">Expressions can contain a literal value, a method call, an operator and its operands, or a simple name.</span></span> <span data-ttu-id="00938-105">Un nom simple peut être le nom d'une variable, d'un membre de type, d'un paramètre de méthode, d'un espace de noms ou d'un type.</span><span class="sxs-lookup"><span data-stu-id="00938-105">Simple names can be the name of a variable, type member, method parameter, namespace or type.</span></span> <span data-ttu-id="00938-106">Les expressions peuvent utiliser des opérateurs qui à leur tour utilisent d'autres expressions comme des paramètres, ou des appels de méthode dont les paramètres sont à leur tour d'autres appels de méthode.</span><span class="sxs-lookup"><span data-stu-id="00938-106">Expressions can use operators that in turn use other expressions as parameters, or method calls whose parameters are in turn other method calls.</span></span> <span data-ttu-id="00938-107">Par conséquent, les expressions peuvent être simples ou très complexes.</span><span class="sxs-lookup"><span data-stu-id="00938-107">Therefore, expressions can range from simple to very complex.</span></span>  
  
 <span data-ttu-id="00938-108">Dans LINQ to Entities requêtes, les expressions peuvent contenir tout ce qui est autorisé par les types dans l' <xref:System.Linq.Expressions> espace de noms, y compris les expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="00938-108">In LINQ to Entities queries, expressions can contain anything allowed by the types within the <xref:System.Linq.Expressions> namespace, including lambda expressions.</span></span> <span data-ttu-id="00938-109">Les expressions qui peuvent être utilisées dans les requêtes LINQ to Entities sont un sur-ensemble des expressions qui peuvent être utilisées pour interroger le Entity Framework. les expressions qui font partie des requêtes sur les Entity Framework sont limitées aux opérations prises en charge par `ObjectQuery<T>` et la source de données sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="00938-109">The expressions that can be used in LINQ to Entities queries are a superset of the expressions that can be used to query the Entity Framework.Expressions that are part of queries against the Entity Framework are limited to operations supported by `ObjectQuery<T>` and the underlying data source.</span></span>  
  
 <span data-ttu-id="00938-110">Dans l'exemple suivant, la comparaison dans la clause `Where` est une expression :</span><span class="sxs-lookup"><span data-stu-id="00938-110">In the following example, the comparison in the `Where` clause is an expression:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
> <span data-ttu-id="00938-111">Les constructions de langage spécifiques, telles que C# `unchecked` , n’ont aucune signification dans LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="00938-111">Specific language constructs, such as C# `unchecked`, have no meaning in LINQ to Entities.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="00938-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="00938-112">In This Section</span></span>  

 [<span data-ttu-id="00938-113">Expressions constantes</span><span class="sxs-lookup"><span data-stu-id="00938-113">Constant Expressions</span></span>](constant-expressions.md)  
  
 [<span data-ttu-id="00938-114">Expressions de comparaison</span><span class="sxs-lookup"><span data-stu-id="00938-114">Comparison Expressions</span></span>](comparison-expressions.md)  
  
 [<span data-ttu-id="00938-115">Comparaisons null</span><span class="sxs-lookup"><span data-stu-id="00938-115">Null Comparisons</span></span>](null-comparisons.md)  
  
 [<span data-ttu-id="00938-116">Expressions d’initialisation</span><span class="sxs-lookup"><span data-stu-id="00938-116">Initialization Expressions</span></span>](initialization-expressions.md)  
  
 [<span data-ttu-id="00938-117">Relations, propriétés de navigation et clés étrangères</span><span class="sxs-lookup"><span data-stu-id="00938-117">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)  
  
## <a name="see-also"></a><span data-ttu-id="00938-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00938-118">See also</span></span>

- [<span data-ttu-id="00938-119">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="00938-119">ADO.NET Entity Framework</span></span>](../index.md)
