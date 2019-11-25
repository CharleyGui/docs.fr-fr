---
title: Facultative
ms.date: 07/20/2015
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
ms.openlocfilehash: a16dae35bf4bc84d95501624c4f023f390a8dda8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351435"
---
# <a name="optional-visual-basic"></a><span data-ttu-id="11853-102">Optional (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11853-102">Optional (Visual Basic)</span></span>

<span data-ttu-id="11853-103">Specifies that a procedure argument can be omitted when the procedure is called.</span><span class="sxs-lookup"><span data-stu-id="11853-103">Specifies that a procedure argument can be omitted when the procedure is called.</span></span>

## <a name="remarks"></a><span data-ttu-id="11853-104">Notes</span><span class="sxs-lookup"><span data-stu-id="11853-104">Remarks</span></span>

<span data-ttu-id="11853-105">For each optional parameter, you must specify a constant expression as the default value of that parameter.</span><span class="sxs-lookup"><span data-stu-id="11853-105">For each optional parameter, you must specify a constant expression as the default value of that parameter.</span></span> <span data-ttu-id="11853-106">If the expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the default value of the value data type is used as the default value of the parameter.</span><span class="sxs-lookup"><span data-stu-id="11853-106">If the expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the default value of the value data type is used as the default value of the parameter.</span></span>

<span data-ttu-id="11853-107">If the parameter list contains an optional parameter, every parameter that follows it must also be optional.</span><span class="sxs-lookup"><span data-stu-id="11853-107">If the parameter list contains an optional parameter, every parameter that follows it must also be optional.</span></span>

<span data-ttu-id="11853-108">Le modificateur `Optional` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="11853-108">The `Optional` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="11853-109">Declare (instruction)</span><span class="sxs-lookup"><span data-stu-id="11853-109">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)

- [<span data-ttu-id="11853-110">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="11853-110">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- [<span data-ttu-id="11853-111">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="11853-111">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- [<span data-ttu-id="11853-112">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="11853-112">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

> [!NOTE]
> <span data-ttu-id="11853-113">When calling a procedure with or without optional parameters, you can pass arguments by position or by name.</span><span class="sxs-lookup"><span data-stu-id="11853-113">When calling a procedure with or without optional parameters, you can pass arguments by position or by name.</span></span> <span data-ttu-id="11853-114">For more information, see [Passing Arguments by Position and by Name](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="11853-114">For more information, see [Passing Arguments by Position and by Name](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span></span>

> [!NOTE]
> <span data-ttu-id="11853-115">You can also define a procedure with optional parameters by using overloading.</span><span class="sxs-lookup"><span data-stu-id="11853-115">You can also define a procedure with optional parameters by using overloading.</span></span> <span data-ttu-id="11853-116">If you have one optional parameter, you can define two overloaded versions of the procedure, one that accepts the parameter and one that doesn’t.</span><span class="sxs-lookup"><span data-stu-id="11853-116">If you have one optional parameter, you can define two overloaded versions of the procedure, one that accepts the parameter and one that doesn’t.</span></span> <span data-ttu-id="11853-117">Pour plus d'informations, consultez [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="11853-117">For more information, see [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>

## <a name="example"></a><span data-ttu-id="11853-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="11853-118">Example</span></span>

<span data-ttu-id="11853-119">The following example defines a procedure that has an optional parameter.</span><span class="sxs-lookup"><span data-stu-id="11853-119">The following example defines a procedure that has an optional parameter.</span></span>

```vb
Public Function FindMatches(ByRef values As List(Of String),
                            ByVal searchString As String,
                            Optional ByVal matchCase As Boolean = False) As List(Of String)

    Dim results As IEnumerable(Of String)

    If matchCase Then
        results = From v In values
                  Where v.Contains(searchString)
    Else
        results = From v In values
                  Where UCase(v).Contains(UCase(searchString))
    End If

    Return results.ToList()
End Function
```

## <a name="example"></a><span data-ttu-id="11853-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="11853-120">Example</span></span>

<span data-ttu-id="11853-121">The following example demonstrates how to call a procedure with arguments passed by position and with arguments passed by name.</span><span class="sxs-lookup"><span data-stu-id="11853-121">The following example demonstrates how to call a procedure with arguments passed by position and with arguments passed by name.</span></span> <span data-ttu-id="11853-122">The procedure has two optional parameters.</span><span class="sxs-lookup"><span data-stu-id="11853-122">The procedure has two optional parameters.</span></span>

[!code-vb[VbVbalrKeywords#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class8.vb#21)]

## <a name="see-also"></a><span data-ttu-id="11853-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11853-123">See also</span></span>

- [<span data-ttu-id="11853-124">Liste de paramètres</span><span class="sxs-lookup"><span data-stu-id="11853-124">Parameter List</span></span>](../../../visual-basic/language-reference/statements/parameter-list.md)
- [<span data-ttu-id="11853-125">Paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="11853-125">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="11853-126">Mots clés</span><span class="sxs-lookup"><span data-stu-id="11853-126">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
