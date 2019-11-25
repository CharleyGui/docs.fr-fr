---
title: '#If...Then...#Else, directives'
ms.date: 04/11/2018
f1_keywords:
- vb.#EndIf
- '#End If'
- '#Then'
- '#ElseIf'
- vb.#ElseIf
- vb.#Else
- vb.#If
helpviewer_keywords:
- Visual Basic code, compiling
- '#If directive [Visual Basic]'
- conditional compilation [Visual Basic], directives
- '#End if directive [Visual Basic]'
- selective compiling
- else directive (#else)
- '#Else directive [Visual Basic]'
ms.assetid: 10bba104-e3fd-451b-b672-faa472530502
ms.openlocfilehash: 40e93b718241c9819e3c0fd84595e76eb0c86472
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343811"
---
# <a name="ifthenelse-directives"></a><span data-ttu-id="e14dd-102">#If...Then...#Else, directives</span><span class="sxs-lookup"><span data-stu-id="e14dd-102">#If...Then...#Else Directives</span></span>

<span data-ttu-id="e14dd-103">Conditionally compiles selected blocks of Visual Basic code.</span><span class="sxs-lookup"><span data-stu-id="e14dd-103">Conditionally compiles selected blocks of Visual Basic code.</span></span>

## <a name="syntax"></a><span data-ttu-id="e14dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e14dd-104">Syntax</span></span>

```vb
#If expression Then
   statements
[ #ElseIf expression Then
   [ statements ]
...
#ElseIf expression Then
   [ statements ] ]
[ #Else
   [ statements ] ]
#End If
```

## <a name="parts"></a><span data-ttu-id="e14dd-105">Composants</span><span class="sxs-lookup"><span data-stu-id="e14dd-105">Parts</span></span>

`expression`  
<span data-ttu-id="e14dd-106">Required for `#If` and `#ElseIf` statements, optional elsewhere.</span><span class="sxs-lookup"><span data-stu-id="e14dd-106">Required for `#If` and `#ElseIf` statements, optional elsewhere.</span></span> <span data-ttu-id="e14dd-107">Any expression, consisting exclusively of one or more conditional compiler constants, literals, and operators, that evaluates to `True` or `False`.</span><span class="sxs-lookup"><span data-stu-id="e14dd-107">Any expression, consisting exclusively of one or more conditional compiler constants, literals, and operators, that evaluates to `True` or `False`.</span></span>

`statements`  
<span data-ttu-id="e14dd-108">Required for `#If` statement block, optional elsewhere.</span><span class="sxs-lookup"><span data-stu-id="e14dd-108">Required for `#If` statement block, optional elsewhere.</span></span> <span data-ttu-id="e14dd-109">Visual Basic program lines or compiler directives that are compiled if the associated expression evaluates to `True`.</span><span class="sxs-lookup"><span data-stu-id="e14dd-109">Visual Basic program lines or compiler directives that are compiled if the associated expression evaluates to `True`.</span></span>

`#End If`  
<span data-ttu-id="e14dd-110">Terminates the `#If` statement block.</span><span class="sxs-lookup"><span data-stu-id="e14dd-110">Terminates the `#If` statement block.</span></span>

## <a name="remarks"></a><span data-ttu-id="e14dd-111">Notes</span><span class="sxs-lookup"><span data-stu-id="e14dd-111">Remarks</span></span>

<span data-ttu-id="e14dd-112">On the surface, the behavior of the `#If...Then...#Else` directives appears the same as that of the `If...Then...Else` statements.</span><span class="sxs-lookup"><span data-stu-id="e14dd-112">On the surface, the behavior of the `#If...Then...#Else` directives appears the same as that of the `If...Then...Else` statements.</span></span> <span data-ttu-id="e14dd-113">However, the `#If...Then...#Else` directives evaluate what is compiled by the compiler, whereas the `If...Then...Else` statements evaluate conditions at run time.</span><span class="sxs-lookup"><span data-stu-id="e14dd-113">However, the `#If...Then...#Else` directives evaluate what is compiled by the compiler, whereas the `If...Then...Else` statements evaluate conditions at run time.</span></span>

<span data-ttu-id="e14dd-114">Conditional compilation is typically used to compile the same program for different platforms.</span><span class="sxs-lookup"><span data-stu-id="e14dd-114">Conditional compilation is typically used to compile the same program for different platforms.</span></span> <span data-ttu-id="e14dd-115">It is also used to prevent debugging code from appearing in an executable file.</span><span class="sxs-lookup"><span data-stu-id="e14dd-115">It is also used to prevent debugging code from appearing in an executable file.</span></span> <span data-ttu-id="e14dd-116">Code excluded during conditional compilation is completely omitted from the final executable file, so it has no effect on size or performance.</span><span class="sxs-lookup"><span data-stu-id="e14dd-116">Code excluded during conditional compilation is completely omitted from the final executable file, so it has no effect on size or performance.</span></span>

<span data-ttu-id="e14dd-117">Regardless of the outcome of any evaluation, all expressions are evaluated using `Option Compare Binary`.</span><span class="sxs-lookup"><span data-stu-id="e14dd-117">Regardless of the outcome of any evaluation, all expressions are evaluated using `Option Compare Binary`.</span></span> <span data-ttu-id="e14dd-118">The `Option Compare` statement does not affect expressions in `#If` and `#ElseIf` statements.</span><span class="sxs-lookup"><span data-stu-id="e14dd-118">The `Option Compare` statement does not affect expressions in `#If` and `#ElseIf` statements.</span></span>

> [!NOTE]
> <span data-ttu-id="e14dd-119">No single-line form of the `#If`, `#Else`, `#ElseIf`, and `#End If` directives exists.</span><span class="sxs-lookup"><span data-stu-id="e14dd-119">No single-line form of the `#If`, `#Else`, `#ElseIf`, and `#End If` directives exists.</span></span> <span data-ttu-id="e14dd-120">No other code can appear on the same line as any of the directives.</span><span class="sxs-lookup"><span data-stu-id="e14dd-120">No other code can appear on the same line as any of the directives.</span></span>

<span data-ttu-id="e14dd-121">The statements within a conditional compilation block must be complete logical statements.</span><span class="sxs-lookup"><span data-stu-id="e14dd-121">The statements within a conditional compilation block must be complete logical statements.</span></span> <span data-ttu-id="e14dd-122">For example, you cannot conditionally compile only the attributes of a function, but you can conditionally declare the function along with its attributes:</span><span class="sxs-lookup"><span data-stu-id="e14dd-122">For example, you cannot conditionally compile only the attributes of a function, but you can conditionally declare the function along with its attributes:</span></span>

```vb
#If DEBUG Then
<WebMethod()>
Public Function SomeFunction() As String
#Else
<WebMethod(CacheDuration:=86400)>
Public Function SomeFunction() As String
#End If
```

## <a name="example"></a><span data-ttu-id="e14dd-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="e14dd-123">Example</span></span>

<span data-ttu-id="e14dd-124">This example uses the `#If...Then...#Else` construct to determine whether to compile certain statements.</span><span class="sxs-lookup"><span data-stu-id="e14dd-124">This example uses the `#If...Then...#Else` construct to determine whether to compile certain statements.</span></span>

[!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="e14dd-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e14dd-125">See also</span></span>

- [<span data-ttu-id="e14dd-126">#Const (directive)</span><span class="sxs-lookup"><span data-stu-id="e14dd-126">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)
- [<span data-ttu-id="e14dd-127">If...Then...Else (instruction)</span><span class="sxs-lookup"><span data-stu-id="e14dd-127">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="e14dd-128">Compilation conditionnelle</span><span class="sxs-lookup"><span data-stu-id="e14dd-128">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>
