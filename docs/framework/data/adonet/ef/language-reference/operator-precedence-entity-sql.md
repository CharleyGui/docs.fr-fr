---
title: Priorité des opérateurs (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
ms.openlocfilehash: f8aa0f213a24d6431d8910af849571a67fbd9f57
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175640"
---
# <a name="operator-precedence-entity-sql"></a><span data-ttu-id="3cf60-102">Priorité des opérateurs (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3cf60-102">Operator Precedence (Entity SQL)</span></span>

<span data-ttu-id="3cf60-103">Lorsqu’une [!INCLUDE[esql](../../../../../../includes/esql-md.md)] requête a plusieurs opérateurs, la priorité des opérateurs détermine l’ordre dans lequel les opérations sont exécutées.</span><span class="sxs-lookup"><span data-stu-id="3cf60-103">When an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query has multiple operators, operator precedence determines the sequence in which the operations are performed.</span></span> <span data-ttu-id="3cf60-104">Cet ordre peut affecter considérablement le résultat de la requête.</span><span class="sxs-lookup"><span data-stu-id="3cf60-104">The order of execution can significantly affect the query result.</span></span>  
  
 <span data-ttu-id="3cf60-105">L'ordre de priorité des opérateurs est indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="3cf60-105">Operators have the precedence levels shown in the following table.</span></span> <span data-ttu-id="3cf60-106">Un opérateur avec un haut niveau de priorité est évalué avant un opérateur avec un faible niveau de priorité.</span><span class="sxs-lookup"><span data-stu-id="3cf60-106">An operator with a higher level is evaluated before an operator with a lower level.</span></span>  
  
|<span data-ttu-id="3cf60-107">Level</span><span class="sxs-lookup"><span data-stu-id="3cf60-107">Level</span></span>|<span data-ttu-id="3cf60-108">Type d'opération</span><span class="sxs-lookup"><span data-stu-id="3cf60-108">Operation type</span></span>|<span data-ttu-id="3cf60-109">Opérateur</span><span class="sxs-lookup"><span data-stu-id="3cf60-109">Operator</span></span>|  
|-----------|--------------------|--------------|  
|<span data-ttu-id="3cf60-110">1</span><span class="sxs-lookup"><span data-stu-id="3cf60-110">1</span></span>|<span data-ttu-id="3cf60-111">Principal</span><span class="sxs-lookup"><span data-stu-id="3cf60-111">Primary</span></span>|`. , [] ()`|  
|<span data-ttu-id="3cf60-112">2</span><span class="sxs-lookup"><span data-stu-id="3cf60-112">2</span></span>|<span data-ttu-id="3cf60-113">Unaire</span><span class="sxs-lookup"><span data-stu-id="3cf60-113">Unary</span></span>|`! not`|  
|<span data-ttu-id="3cf60-114">3</span><span class="sxs-lookup"><span data-stu-id="3cf60-114">3</span></span>|<span data-ttu-id="3cf60-115">Multiplicatif</span><span class="sxs-lookup"><span data-stu-id="3cf60-115">Multiplicative</span></span>|`* / %`|  
|<span data-ttu-id="3cf60-116">4</span><span class="sxs-lookup"><span data-stu-id="3cf60-116">4</span></span>|<span data-ttu-id="3cf60-117">Additive</span><span class="sxs-lookup"><span data-stu-id="3cf60-117">Additive</span></span>|`+ -`|  
|<span data-ttu-id="3cf60-118">5</span><span class="sxs-lookup"><span data-stu-id="3cf60-118">5</span></span>|<span data-ttu-id="3cf60-119">Classement</span><span class="sxs-lookup"><span data-stu-id="3cf60-119">Ordering</span></span>|`< > <= >=`|  
|<span data-ttu-id="3cf60-120">6</span><span class="sxs-lookup"><span data-stu-id="3cf60-120">6</span></span>|<span data-ttu-id="3cf60-121">Égalité</span><span class="sxs-lookup"><span data-stu-id="3cf60-121">Equality</span></span>|`= != <>`|  
|<span data-ttu-id="3cf60-122">7</span><span class="sxs-lookup"><span data-stu-id="3cf60-122">7</span></span>|<span data-ttu-id="3cf60-123">AND conditionnel</span><span class="sxs-lookup"><span data-stu-id="3cf60-123">Conditional AND</span></span>|`and &&`|  
|<span data-ttu-id="3cf60-124">8</span><span class="sxs-lookup"><span data-stu-id="3cf60-124">8</span></span>|<span data-ttu-id="3cf60-125">OR conditionnel</span><span class="sxs-lookup"><span data-stu-id="3cf60-125">Conditional OR</span></span>|`or &#124;&#124;`|  
  
 <span data-ttu-id="3cf60-126">Lorsque deux opérateurs dans une expression ont le même niveau de priorité, ils sont évalués de gauche à droite, en fonction de leur position dans la requête.</span><span class="sxs-lookup"><span data-stu-id="3cf60-126">When two operators in an expression have the same operator precedence level, they are evaluated left to right, based on their position in the query.</span></span> <span data-ttu-id="3cf60-127">Par exemple, `x+y-z` est évalué comme étant `(x+y)-z`.</span><span class="sxs-lookup"><span data-stu-id="3cf60-127">For example, `x+y-z` is evaluated as `(x+y)-z`.</span></span>  
  
 <span data-ttu-id="3cf60-128">Vous pouvez utiliser des parenthèses pour modifier la priorité habituelle des opérateurs dans une requête.</span><span class="sxs-lookup"><span data-stu-id="3cf60-128">You can use parentheses to override the defined precedence of the operators in a query.</span></span> <span data-ttu-id="3cf60-129">Tout ce qui se trouve entre parenthèses est évalué en premier pour produire un seul résultat, qui est ensuite utilisé par un opérateur en dehors des parenthèses.</span><span class="sxs-lookup"><span data-stu-id="3cf60-129">Everything within parentheses is evaluated first to yield a single result before that result can be used by any operator outside the parentheses.</span></span> <span data-ttu-id="3cf60-130">Par exemple, `x+y*z` multiplie `y` par, `z` puis ajoute `x` , mais `(x+y)*z` ajoute `x` à, puis `y` multiplie le résultat par `z` .</span><span class="sxs-lookup"><span data-stu-id="3cf60-130">For example, `x+y*z` multiplies `y` by `z` and then adds `x`, but `(x+y)*z` adds `x` to `y` and then multiplies the result by `z`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cf60-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3cf60-131">See also</span></span>

- [<span data-ttu-id="3cf60-132">Vue d'ensemble d'Entity SQL</span><span class="sxs-lookup"><span data-stu-id="3cf60-132">Entity SQL Overview</span></span>](entity-sql-overview.md)
