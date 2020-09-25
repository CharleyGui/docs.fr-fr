---
title: Fonctions d'agrégation (Entity SQL)
ms.date: 03/30/2017
ms.assetid: acfd3149-f519-4c6e-8fe1-b21d243a0e58
ms.openlocfilehash: 308670f04b9a04b1fff77ece08deb39c8c4081d1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198078"
---
# <a name="aggregate-functions-entity-sql"></a><span data-ttu-id="9cf23-102">Fonctions d'agrégation (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9cf23-102">Aggregate Functions (Entity SQL)</span></span>

<span data-ttu-id="9cf23-103">Un agrégat est une construction de langage qui condense une collection en un scalaire dans le cadre d'une opération de groupe.</span><span class="sxs-lookup"><span data-stu-id="9cf23-103">An aggregate is a language construct that condenses a collection into a scalar as a part of a group operation.</span></span> <span data-ttu-id="9cf23-104">Les agrégats [!INCLUDE[esql](../../../../../../includes/esql-md.md)] se présentent sous deux formes :</span><span class="sxs-lookup"><span data-stu-id="9cf23-104">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] aggregates come in two forms:</span></span>  
  
- [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="9cf23-105">fonctions de collection qui peuvent être utilisées n’importe où dans une expression.</span><span class="sxs-lookup"><span data-stu-id="9cf23-105">collection functions that may be used anywhere in an expression.</span></span> <span data-ttu-id="9cf23-106">Cela inclut l'utilisation de fonctions d'agrégation dans les projections et les prédicats qui agissent sur les collections.</span><span class="sxs-lookup"><span data-stu-id="9cf23-106">This includes using aggregate functions in projections and predicates that act on collections.</span></span> <span data-ttu-id="9cf23-107">Dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)], la spécification des agrégats s’effectue de préférence par fonctions de collection.</span><span class="sxs-lookup"><span data-stu-id="9cf23-107">Collection functions are the preferred mode of specifying aggregates in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
- <span data-ttu-id="9cf23-108">Les agrégats de groupe dans les expressions de requête dotées d'une clause GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="9cf23-108">Group aggregates in query expressions that have a GROUP BY clause.</span></span> <span data-ttu-id="9cf23-109">Comme dans Transact-SQL, les agrégats de groupe acceptent DISTINCT et ALL comme modificateurs de l’entrée d’agrégation.</span><span class="sxs-lookup"><span data-stu-id="9cf23-109">As in Transact-SQL, group aggregates accept DISTINCT and ALL as modifiers to the aggregate input.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="9cf23-110">tente d’abord d’interpréter une expression comme une fonction de collection et si l’expression est dans le contexte d’une expression SELECT, elle l’interprète comme un agrégat de groupe.</span><span class="sxs-lookup"><span data-stu-id="9cf23-110">first tries to interpret an expression as a collection function and if the expression is in the context of a SELECT expression it interprets it as a group aggregate.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="9cf23-111">définit un opérateur d’agrégation spécial appelé [GROUPPARTITION](grouppartition-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="9cf23-111">defines a special aggregate operator called [GROUPPARTITION](grouppartition-entity-sql.md).</span></span> <span data-ttu-id="9cf23-112">Cet opérateur vous permet d'obtenir une référence au jeu de données d'entrée groupé.</span><span class="sxs-lookup"><span data-stu-id="9cf23-112">This operator enables you to get a reference to the grouped input set.</span></span> <span data-ttu-id="9cf23-113">Cela permet d’exécuter des requêtes de regroupement améliorées, où les résultats de la clause GROUP BY peuvent être utilisés à des emplacements autres qu’un agrégat de groupe ou des fonctions de collection.</span><span class="sxs-lookup"><span data-stu-id="9cf23-113">This allows more advanced grouping queries, where the results of the GROUP BY clause can be used in places other than group aggregate or collection functions.</span></span>  
  
## <a name="collection-functions"></a><span data-ttu-id="9cf23-114">Fonctions de collection</span><span class="sxs-lookup"><span data-stu-id="9cf23-114">Collection Functions</span></span>  

 <span data-ttu-id="9cf23-115">Les fonctions de collection fonctionnent sur des collections et retournent une valeur scalaire.</span><span class="sxs-lookup"><span data-stu-id="9cf23-115">Collection functions operate on collections and return a scalar value.</span></span> <span data-ttu-id="9cf23-116">Par exemple, si `orders` est une collection de toutes les commandes `orders`, vous pouvez calculer la première date d’expédition grâce à l’expression suivante :</span><span class="sxs-lookup"><span data-stu-id="9cf23-116">For example, if `orders` is a collection of all `orders`, you can calculate the earliest ship date with the following expression:</span></span>  
  
 `min(select value o.ShipDate from LOB.Orders as o)`  
  
## <a name="group-aggregates"></a><span data-ttu-id="9cf23-117">Agrégats de groupe</span><span class="sxs-lookup"><span data-stu-id="9cf23-117">Group Aggregates</span></span>  

 <span data-ttu-id="9cf23-118">Les agrégats de groupe sont calculés sur un résultat de groupe, tel que défini par la clause GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="9cf23-118">Group aggregates are calculated over a group result as defined by the GROUP BY clause.</span></span> <span data-ttu-id="9cf23-119">La clause GROUP BY partitionne les données en groupes.</span><span class="sxs-lookup"><span data-stu-id="9cf23-119">The GROUP BY clause partitions data  into groups.</span></span> <span data-ttu-id="9cf23-120">Pour chaque groupe du résultat, la fonction d'agrégation est appliquée et un agrégat distinct est calculé en utilisant les éléments de chaque groupe comme entrées du calcul d'agrégation.</span><span class="sxs-lookup"><span data-stu-id="9cf23-120">For each group in the result, the aggregate function is applied and a separate aggregate is calculated by using the elements in each group as inputs to the aggregate calculation.</span></span> <span data-ttu-id="9cf23-121">Lorsqu'une clause GROUP BY est utilisée dans une expression SELECT, seuls des noms d'expressions de regroupement, des agrégats ou des expressions constantes peuvent figurer dans la clause de projection, HAVING ou ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="9cf23-121">When a GROUP BY clause is used in a SELECT expression, only grouping expression names, aggregates, or constant expressions may be present in the projection, HAVING, or ORDER BY clause.</span></span>  
  
 <span data-ttu-id="9cf23-122">L'exemple suivant calcule la quantité moyenne commandée pour chaque produit.</span><span class="sxs-lookup"><span data-stu-id="9cf23-122">The following example calculates the average quantity ordered for each product.</span></span>  
  
 `select p, avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `group by ol.Product as p`  
  
 <span data-ttu-id="9cf23-123">Un agrégat de groupe peut ne pas avoir de clause GROUP BY explicite dans l'expression SELECT.</span><span class="sxs-lookup"><span data-stu-id="9cf23-123">It is possible to have a group aggregate without an explicit GROUP BY clause in the SELECT expression.</span></span> <span data-ttu-id="9cf23-124">Tous les éléments seront traités comme un groupe unique, équivalent à la spécification d'un regroupement basé sur une constante.</span><span class="sxs-lookup"><span data-stu-id="9cf23-124">All elements will be treated as a single group, equivalent to the case of specifying a grouping based on a constant.</span></span>  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol group by 1`  
  
 <span data-ttu-id="9cf23-125">Les expressions utilisées dans la clause GROUP BY sont évaluées à l’aide de la même résolution de noms de portée qui serait visible pour l’expression de la clause WHERE.</span><span class="sxs-lookup"><span data-stu-id="9cf23-125">Expressions used in the GROUP BY clause are evaluated by using the same name-resolution scope that would be visible to the WHERE clause expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cf23-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9cf23-126">See also</span></span>

- [<span data-ttu-id="9cf23-127">Fonctions</span><span class="sxs-lookup"><span data-stu-id="9cf23-127">Functions</span></span>](functions-entity-sql.md)
