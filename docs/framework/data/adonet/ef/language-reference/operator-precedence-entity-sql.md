---
title: Priorité des opérateurs (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
ms.openlocfilehash: 2d8c78f410708fd1aa843ee8f14f7243a9f686c0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249782"
---
# <a name="operator-precedence-entity-sql"></a><span data-ttu-id="405bc-102">Priorité des opérateurs (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="405bc-102">Operator Precedence (Entity SQL)</span></span>
<span data-ttu-id="405bc-103">Lorsqu’une [!INCLUDE[esql](../../../../../../includes/esql-md.md)] requête a plusieurs opérateurs, la priorité des opérateurs détermine l’ordre dans lequel les opérations sont exécutées.</span><span class="sxs-lookup"><span data-stu-id="405bc-103">When an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query has multiple operators, operator precedence determines the sequence in which the operations are performed.</span></span> <span data-ttu-id="405bc-104">Cet ordre peut affecter considérablement le résultat de la requête.</span><span class="sxs-lookup"><span data-stu-id="405bc-104">The order of execution can significantly affect the query result.</span></span>  
  
 <span data-ttu-id="405bc-105">L'ordre de priorité des opérateurs est indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="405bc-105">Operators have the precedence levels shown in the following table.</span></span> <span data-ttu-id="405bc-106">Un opérateur avec un haut niveau de priorité est évalué avant un opérateur avec un faible niveau de priorité.</span><span class="sxs-lookup"><span data-stu-id="405bc-106">An operator with a higher level is evaluated before an operator with a lower level.</span></span>  
  
|<span data-ttu-id="405bc-107">Niveau</span><span class="sxs-lookup"><span data-stu-id="405bc-107">Level</span></span>|<span data-ttu-id="405bc-108">Type d'opération</span><span class="sxs-lookup"><span data-stu-id="405bc-108">Operation type</span></span>|<span data-ttu-id="405bc-109">Opérateur</span><span class="sxs-lookup"><span data-stu-id="405bc-109">Operator</span></span>|  
|-----------|--------------------|--------------|  
|<span data-ttu-id="405bc-110">1</span><span class="sxs-lookup"><span data-stu-id="405bc-110">1</span></span>|<span data-ttu-id="405bc-111">Principale</span><span class="sxs-lookup"><span data-stu-id="405bc-111">Primary</span></span>|`. , [] ()`|  
|<span data-ttu-id="405bc-112">2</span><span class="sxs-lookup"><span data-stu-id="405bc-112">2</span></span>|<span data-ttu-id="405bc-113">Unaire</span><span class="sxs-lookup"><span data-stu-id="405bc-113">Unary</span></span>|`! not`|  
|<span data-ttu-id="405bc-114">3</span><span class="sxs-lookup"><span data-stu-id="405bc-114">3</span></span>|<span data-ttu-id="405bc-115">Multiplication</span><span class="sxs-lookup"><span data-stu-id="405bc-115">Multiplicative</span></span>|`* / %`|  
|<span data-ttu-id="405bc-116">4</span><span class="sxs-lookup"><span data-stu-id="405bc-116">4</span></span>|<span data-ttu-id="405bc-117">Addition</span><span class="sxs-lookup"><span data-stu-id="405bc-117">Additive</span></span>|`+ -`|  
|<span data-ttu-id="405bc-118">5\.</span><span class="sxs-lookup"><span data-stu-id="405bc-118">5</span></span>|<span data-ttu-id="405bc-119">Classement</span><span class="sxs-lookup"><span data-stu-id="405bc-119">Ordering</span></span>|`< > <= >=`|  
|<span data-ttu-id="405bc-120">6\.</span><span class="sxs-lookup"><span data-stu-id="405bc-120">6</span></span>|<span data-ttu-id="405bc-121">Égalité</span><span class="sxs-lookup"><span data-stu-id="405bc-121">Equality</span></span>|`= != <>`|  
|<span data-ttu-id="405bc-122">7</span><span class="sxs-lookup"><span data-stu-id="405bc-122">7</span></span>|<span data-ttu-id="405bc-123">AND conditionnel</span><span class="sxs-lookup"><span data-stu-id="405bc-123">Conditional AND</span></span>|`and &&`|  
|<span data-ttu-id="405bc-124">8</span><span class="sxs-lookup"><span data-stu-id="405bc-124">8</span></span>|<span data-ttu-id="405bc-125">OR conditionnel</span><span class="sxs-lookup"><span data-stu-id="405bc-125">Conditional OR</span></span>|`or &#124;&#124;`|  
  
 <span data-ttu-id="405bc-126">Lorsque deux opérateurs dans une expression ont le même niveau de priorité, ils sont évalués de gauche à droite, en fonction de leur position dans la requête.</span><span class="sxs-lookup"><span data-stu-id="405bc-126">When two operators in an expression have the same operator precedence level, they are evaluated left to right, based on their position in the query.</span></span> <span data-ttu-id="405bc-127">Par exemple, `x+y-z` est évalué comme étant `(x+y)-z`.</span><span class="sxs-lookup"><span data-stu-id="405bc-127">For example, `x+y-z` is evaluated as `(x+y)-z`.</span></span>  
  
 <span data-ttu-id="405bc-128">Vous pouvez utiliser des parenthèses pour modifier la priorité habituelle des opérateurs dans une requête.</span><span class="sxs-lookup"><span data-stu-id="405bc-128">You can use parentheses to override the defined precedence of the operators in a query.</span></span> <span data-ttu-id="405bc-129">Tout ce qui se trouve entre parenthèses est évalué en premier pour produire un seul résultat, qui est ensuite utilisé par un opérateur en dehors des parenthèses.</span><span class="sxs-lookup"><span data-stu-id="405bc-129">Everything within parentheses is evaluated first to yield a single result before that result can be used by any operator outside the parentheses.</span></span> <span data-ttu-id="405bc-130">Par exemple, `x+y*z` `y` multiplie par `z` , puis ajoute `x`, mais `(x+y)*z` ajoute `x` à `y` , puis multiplie le résultat par `z`.</span><span class="sxs-lookup"><span data-stu-id="405bc-130">For example, `x+y*z` multiplies `y` by `z` and then adds `x`, but `(x+y)*z` adds `x` to `y` and then multiplies the result by `z`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="405bc-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="405bc-131">See also</span></span>

- [<span data-ttu-id="405bc-132">Vue d’ensemble d’Entity SQL</span><span class="sxs-lookup"><span data-stu-id="405bc-132">Entity SQL Overview</span></span>](entity-sql-overview.md)
