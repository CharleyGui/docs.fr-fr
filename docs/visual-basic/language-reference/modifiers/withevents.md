---
title: WithEvents
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 2309c675b50a2025d73841a47fe8e30e7cecd522
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350742"
---
# <a name="withevents-visual-basic"></a><span data-ttu-id="802f8-102">WithEvents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="802f8-102">WithEvents (Visual Basic)</span></span>
<span data-ttu-id="802f8-103">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span><span class="sxs-lookup"><span data-stu-id="802f8-103">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span></span>

## <a name="remarks"></a><span data-ttu-id="802f8-104">Notes</span><span class="sxs-lookup"><span data-stu-id="802f8-104">Remarks</span></span>

<span data-ttu-id="802f8-105">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span><span class="sxs-lookup"><span data-stu-id="802f8-105">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span></span>

<span data-ttu-id="802f8-106">You can use `WithEvents` only at class or module level.</span><span class="sxs-lookup"><span data-stu-id="802f8-106">You can use `WithEvents` only at class or module level.</span></span> <span data-ttu-id="802f8-107">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span><span class="sxs-lookup"><span data-stu-id="802f8-107">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span></span>

<span data-ttu-id="802f8-108">You cannot use `WithEvents` on a structure member.</span><span class="sxs-lookup"><span data-stu-id="802f8-108">You cannot use `WithEvents` on a structure member.</span></span>

<span data-ttu-id="802f8-109">You can declare only individual variables—not arrays—with `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="802f8-109">You can declare only individual variables—not arrays—with `WithEvents`.</span></span>

## <a name="rules"></a><span data-ttu-id="802f8-110">Règles</span><span class="sxs-lookup"><span data-stu-id="802f8-110">Rules</span></span>

<span data-ttu-id="802f8-111">**Element Types.**</span><span class="sxs-lookup"><span data-stu-id="802f8-111">**Element Types.**</span></span> <span data-ttu-id="802f8-112">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span><span class="sxs-lookup"><span data-stu-id="802f8-112">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span></span> <span data-ttu-id="802f8-113">However, you cannot declare them as `Object`.</span><span class="sxs-lookup"><span data-stu-id="802f8-113">However, you cannot declare them as `Object`.</span></span> <span data-ttu-id="802f8-114">You must declare them as the specific class that can raise the events.</span><span class="sxs-lookup"><span data-stu-id="802f8-114">You must declare them as the specific class that can raise the events.</span></span>

<span data-ttu-id="802f8-115">The `WithEvents` modifier can be used in this context: [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="802f8-115">The `WithEvents` modifier can be used in this context: [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)</span></span>

## <a name="example"></a><span data-ttu-id="802f8-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="802f8-116">Example</span></span>

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a><span data-ttu-id="802f8-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="802f8-117">See also</span></span>

- [<span data-ttu-id="802f8-118">Handles</span><span class="sxs-lookup"><span data-stu-id="802f8-118">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="802f8-119">Mots clés</span><span class="sxs-lookup"><span data-stu-id="802f8-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="802f8-120">Événements</span><span class="sxs-lookup"><span data-stu-id="802f8-120">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
