---
title: Facultatif
ms.date: 07/20/2015
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
ms.openlocfilehash: c46d06dba61158d7362d736731161be306af3f10
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392143"
---
# <a name="optional-visual-basic"></a><span data-ttu-id="12b55-102">Optional (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12b55-102">Optional (Visual Basic)</span></span>

<span data-ttu-id="12b55-103">Spécifie qu’un argument de procédure peut être omis lorsque la procédure est appelée.</span><span class="sxs-lookup"><span data-stu-id="12b55-103">Specifies that a procedure argument can be omitted when the procedure is called.</span></span>

## <a name="remarks"></a><span data-ttu-id="12b55-104">Notes</span><span class="sxs-lookup"><span data-stu-id="12b55-104">Remarks</span></span>

<span data-ttu-id="12b55-105">Pour chaque paramètre facultatif, vous devez spécifier une expression constante comme valeur par défaut de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="12b55-105">For each optional parameter, you must specify a constant expression as the default value of that parameter.</span></span> <span data-ttu-id="12b55-106">Si l’expression prend la valeur [Nothing](../nothing.md), la valeur par défaut du type de données value est utilisée comme valeur par défaut du paramètre.</span><span class="sxs-lookup"><span data-stu-id="12b55-106">If the expression evaluates to [Nothing](../nothing.md), the default value of the value data type is used as the default value of the parameter.</span></span>

<span data-ttu-id="12b55-107">Si la liste de paramètres contient un paramètre facultatif, chaque paramètre qui le suit doit également être facultatif.</span><span class="sxs-lookup"><span data-stu-id="12b55-107">If the parameter list contains an optional parameter, every parameter that follows it must also be optional.</span></span>

<span data-ttu-id="12b55-108">Le modificateur `Optional` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="12b55-108">The `Optional` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="12b55-109">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="12b55-109">Declare Statement</span></span>](../statements/declare-statement.md)

- [<span data-ttu-id="12b55-110">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="12b55-110">Function Statement</span></span>](../statements/function-statement.md)

- [<span data-ttu-id="12b55-111">Property Statement</span><span class="sxs-lookup"><span data-stu-id="12b55-111">Property Statement</span></span>](../statements/property-statement.md)

- [<span data-ttu-id="12b55-112">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="12b55-112">Sub Statement</span></span>](../statements/sub-statement.md)

> [!NOTE]
> <span data-ttu-id="12b55-113">Lors de l’appel d’une procédure avec ou sans paramètres facultatifs, vous pouvez passer des arguments par position ou par nom.</span><span class="sxs-lookup"><span data-stu-id="12b55-113">When calling a procedure with or without optional parameters, you can pass arguments by position or by name.</span></span> <span data-ttu-id="12b55-114">Pour plus d’informations, consultez [passage des arguments par position et par nom](../../programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="12b55-114">For more information, see [Passing Arguments by Position and by Name](../../programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span></span>

> [!NOTE]
> <span data-ttu-id="12b55-115">Vous pouvez également définir une procédure avec des paramètres facultatifs à l’aide de la surcharge.</span><span class="sxs-lookup"><span data-stu-id="12b55-115">You can also define a procedure with optional parameters by using overloading.</span></span> <span data-ttu-id="12b55-116">Si vous avez un paramètre facultatif, vous pouvez définir deux versions surchargées de la procédure, une qui accepte le paramètre et une autre qui ne l’est pas.</span><span class="sxs-lookup"><span data-stu-id="12b55-116">If you have one optional parameter, you can define two overloaded versions of the procedure, one that accepts the parameter and one that doesn’t.</span></span> <span data-ttu-id="12b55-117">Pour plus d'informations, consultez [Procedure Overloading](../../programming-guide/language-features/procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="12b55-117">For more information, see [Procedure Overloading](../../programming-guide/language-features/procedures/procedure-overloading.md).</span></span>

## <a name="example"></a><span data-ttu-id="12b55-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="12b55-118">Example</span></span>

<span data-ttu-id="12b55-119">L’exemple suivant définit une procédure qui a un paramètre facultatif.</span><span class="sxs-lookup"><span data-stu-id="12b55-119">The following example defines a procedure that has an optional parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="12b55-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="12b55-120">Example</span></span>

<span data-ttu-id="12b55-121">L’exemple suivant montre comment appeler une procédure avec des arguments passés par position et avec des arguments passés par nom.</span><span class="sxs-lookup"><span data-stu-id="12b55-121">The following example demonstrates how to call a procedure with arguments passed by position and with arguments passed by name.</span></span> <span data-ttu-id="12b55-122">La procédure a deux paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="12b55-122">The procedure has two optional parameters.</span></span>

[!code-vb[VbVbalrKeywords#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class8.vb#21)]

## <a name="see-also"></a><span data-ttu-id="12b55-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12b55-123">See also</span></span>

- [<span data-ttu-id="12b55-124">Liste de paramètres</span><span class="sxs-lookup"><span data-stu-id="12b55-124">Parameter List</span></span>](../statements/parameter-list.md)
- [<span data-ttu-id="12b55-125">Paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="12b55-125">Optional Parameters</span></span>](../../programming-guide/language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="12b55-126">Mots clés</span><span class="sxs-lookup"><span data-stu-id="12b55-126">Keywords</span></span>](../keywords/index.md)
