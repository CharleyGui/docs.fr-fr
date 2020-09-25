---
title: Expressions de comparaison
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec7637a9-01d5-4a95-8bb0-478311cd263b
ms.openlocfilehash: d92020f353393eee683e578f4306cd4a2f214152
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197844"
---
# <a name="comparison-expressions"></a><span data-ttu-id="51f20-102">Expressions de comparaison</span><span class="sxs-lookup"><span data-stu-id="51f20-102">Comparison Expressions</span></span>

<span data-ttu-id="51f20-103">Une expression de comparaison définit une valeur constante, une valeur de propriété ou un résultat de méthode par rapport à une autre valeur (égal, différent de, supérieur à ou inférieur à).</span><span class="sxs-lookup"><span data-stu-id="51f20-103">A comparison expression checks whether a constant value, property value, or method result is equal, not equal, greater than, or less than another value.</span></span> <span data-ttu-id="51f20-104">Si une comparaison particulière n’est pas valide pour LINQ to Entities, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="51f20-104">If a particular comparison is not valid for LINQ to Entities, an exception will be thrown.</span></span> <span data-ttu-id="51f20-105">Toutes les comparaisons, implicites et explicites, requièrent que tous les composants soient comparables dans la source de données.</span><span class="sxs-lookup"><span data-stu-id="51f20-105">All comparisons, both implicit and explicit, require that all components are comparable in the data source.</span></span> <span data-ttu-id="51f20-106">Des expressions de comparaison sont souvent utilisées dans des clauses `Where` pour restreindre les résultats d'une requête.</span><span class="sxs-lookup"><span data-stu-id="51f20-106">Comparison expressions are frequently used in `Where` clauses for restricting the query results.</span></span>  
  
 <span data-ttu-id="51f20-107">L'exemple suivant dans la syntaxe d'expression de requête présente une requête qui retourne des résultats dans lesquels le numéro de commande client est égal à SO43663 :</span><span class="sxs-lookup"><span data-stu-id="51f20-107">The following example in query expression syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression)]  
  
 <span data-ttu-id="51f20-108">L'exemple suivant dans la syntaxe de requête fondée sur une méthode présente une requête qui retourne des résultats dans lesquels le numéro de commande client est égal à SO43663 :</span><span class="sxs-lookup"><span data-stu-id="51f20-108">The following example in method-based query syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression_mq)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression_mq)]  
  
 <span data-ttu-id="51f20-109">L'exemple suivant dans la syntaxe d'expression de requête présente une requête qui retourne des informations de commande client dans lesquelles la date d'expédition est égale au 8 juillet 2001 :</span><span class="sxs-lookup"><span data-stu-id="51f20-109">The following example in query expression syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison)]  
  
 <span data-ttu-id="51f20-110">L'exemple suivant dans la syntaxe de requête fondée sur une méthode présente une requête qui retourne des informations de commande client dans lesquelles la date d'expédition est égale au 8 juillet 2001 :</span><span class="sxs-lookup"><span data-stu-id="51f20-110">The following example in method-based query syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison_mq)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison_mq)]  
  
 <span data-ttu-id="51f20-111">Les expressions qui génèrent une constante sont converties au niveau du serveur, et aucune tentative d'évaluation locale n'est effectuée.</span><span class="sxs-lookup"><span data-stu-id="51f20-111">Expressions that yield a constant are converted at the server, and no attempt to do local evaluation is performed.</span></span> <span data-ttu-id="51f20-112">L'exemple suivant utilise une expression dans la clause `Where` qui génère une constante.</span><span class="sxs-lookup"><span data-stu-id="51f20-112">The following example uses an expression in the `Where` clause that yields a constant.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 <span data-ttu-id="51f20-113">LINQ to Entities ne prend pas en charge l’utilisation d’une classe d’utilisateur en tant que constante.</span><span class="sxs-lookup"><span data-stu-id="51f20-113">LINQ to Entities does not support using a user class as a constant.</span></span> <span data-ttu-id="51f20-114">Toutefois, une référence de propriété sur une classe d'utilisateur est considérée comme une constante. Elle est donc convertie en expression constante d'arborescence de commandes et exécutée sur la source de données.</span><span class="sxs-lookup"><span data-stu-id="51f20-114">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myclass)]
 [!code-vb[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myclass)]  
  
 [!code-csharp[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#propertyasconstant)]
 [!code-vb[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#propertyasconstant)]  
  
 <span data-ttu-id="51f20-115">Les méthodes qui retournent une expression constante ne sont pas prises en charge.</span><span class="sxs-lookup"><span data-stu-id="51f20-115">Methods that return a constant expression are not supported.</span></span> <span data-ttu-id="51f20-116">L'exemple suivant contient une méthode dans la clause `Where` qui retourne une constante.</span><span class="sxs-lookup"><span data-stu-id="51f20-116">The following example contains a method in the `Where` clause that returns a constant.</span></span> <span data-ttu-id="51f20-117">Cet exemple lève une exception au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="51f20-117">This example will throw an exception at run time.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodasconstantfails)]
 [!code-vb[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodasconstantfails)]  
  
## <a name="see-also"></a><span data-ttu-id="51f20-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51f20-118">See also</span></span>

- [<span data-ttu-id="51f20-119">Expressions dans les requêtes LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="51f20-119">Expressions in LINQ to Entities Queries</span></span>](expressions-in-linq-to-entities-queries.md)
