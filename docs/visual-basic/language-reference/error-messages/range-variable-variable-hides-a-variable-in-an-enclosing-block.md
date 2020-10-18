---
title: La variable de portée '<variable>' masque une variable dans un bloc englobant, une variable de portée précédemment définie ou une variable déclarée implicitement dans une expression de requête
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: 90fed3dd27f18fe87c326cc36dfb774822fc4b21
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162347"
---
# <a name="bc36633-range-variable-variable-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a><span data-ttu-id="b9505-102">BC36633 : la variable \<variable> de portée masque une variable dans un bloc englobant, une variable de portée précédemment définie ou une variable déclarée implicitement dans une expression de requête</span><span class="sxs-lookup"><span data-stu-id="b9505-102">BC36633: Range variable \<variable> hides a variable in an enclosing block, a previously defined range variable, or an implicitly declared variable in a query expression</span></span>

<span data-ttu-id="b9505-103">Un nom de variable de portée spécifié dans une `Select` `From` clause,, `Aggregate` ou `Let` est un doublon du nom d’une variable de portée déjà spécifiée dans la requête, ou du nom d’une variable déclarée implicitement par la requête, par exemple un nom de champ ou le nom d’une fonction d’agrégation.</span><span class="sxs-lookup"><span data-stu-id="b9505-103">A range variable name specified in a `Select`, `From`, `Aggregate`, or `Let` clause duplicates the name of a range variable already specified previously in the query, or the name of a variable that is implicitly declared by the query, such as a field name or the name of an aggregate function.</span></span>

 <span data-ttu-id="b9505-104">**ID d’erreur :** BC36633</span><span class="sxs-lookup"><span data-stu-id="b9505-104">**Error ID:** BC36633</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="b9505-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="b9505-105">To correct this error</span></span>

- <span data-ttu-id="b9505-106">Vérifiez que toutes les variables de plage dans une étendue de requête particulière ont des noms uniques.</span><span class="sxs-lookup"><span data-stu-id="b9505-106">Ensure that all range variables in a particular query scope have unique names.</span></span> <span data-ttu-id="b9505-107">Vous pouvez placer une requête entre parenthèses pour vous assurer que les requêtes imbriquées ont une étendue unique.</span><span class="sxs-lookup"><span data-stu-id="b9505-107">You can enclose a query in parentheses to ensure that nested queries have a unique scope.</span></span>

## <a name="see-also"></a><span data-ttu-id="b9505-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9505-108">See also</span></span>

- [<span data-ttu-id="b9505-109">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b9505-109">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="b9505-110">From, clause</span><span class="sxs-lookup"><span data-stu-id="b9505-110">From Clause</span></span>](../queries/from-clause.md)
- [<span data-ttu-id="b9505-111">Clause let</span><span class="sxs-lookup"><span data-stu-id="b9505-111">Let Clause</span></span>](../queries/let-clause.md)
- [<span data-ttu-id="b9505-112">Aggregate Clause</span><span class="sxs-lookup"><span data-stu-id="b9505-112">Aggregate Clause</span></span>](../queries/aggregate-clause.md)
- [<span data-ttu-id="b9505-113">Clause SELECT</span><span class="sxs-lookup"><span data-stu-id="b9505-113">Select Clause</span></span>](../queries/select-clause.md)
