---
title: '#If... Then... #Else directives (Visual Basic)'
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
ms.openlocfilehash: 697521276e2d5a8d0a4aaae38789a21b7aa87fcb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940758"
---
# <a name="ifthenelse-directives"></a><span data-ttu-id="399b8-102">#If...Then...#Else, directives</span><span class="sxs-lookup"><span data-stu-id="399b8-102">#If...Then...#Else Directives</span></span>
<span data-ttu-id="399b8-103">Compile conditionnellement les blocs sélectionnés de Visual Basic code.</span><span class="sxs-lookup"><span data-stu-id="399b8-103">Conditionally compiles selected blocks of Visual Basic code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="399b8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="399b8-104">Syntax</span></span>  
  
```  
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
  
## <a name="parts"></a><span data-ttu-id="399b8-105">Composants</span><span class="sxs-lookup"><span data-stu-id="399b8-105">Parts</span></span>  
 `expression`  
 <span data-ttu-id="399b8-106">Requis pour `#If` les `#ElseIf` instructions et, facultatif ailleurs.</span><span class="sxs-lookup"><span data-stu-id="399b8-106">Required for `#If` and `#ElseIf` statements, optional elsewhere.</span></span> <span data-ttu-id="399b8-107">Toute expression, composée exclusivement d’une ou de plusieurs constantes de compilateur conditionnelles, de littéraux et d' `True` opérateurs, qui prend la valeur ou. `False`</span><span class="sxs-lookup"><span data-stu-id="399b8-107">Any expression, consisting exclusively of one or more conditional compiler constants, literals, and operators, that evaluates to `True` or `False`.</span></span>  
  
 `statements`  
 <span data-ttu-id="399b8-108">Requis pour `#If` le bloc d’instructions, facultatif ailleurs.</span><span class="sxs-lookup"><span data-stu-id="399b8-108">Required for `#If` statement block, optional elsewhere.</span></span> <span data-ttu-id="399b8-109">Visual Basic des lignes de programme ou des directives de compilateur compilées si l’expression associée `True`prend la valeur.</span><span class="sxs-lookup"><span data-stu-id="399b8-109">Visual Basic program lines or compiler directives that are compiled if the associated expression evaluates to `True`.</span></span>  
  
 `#End If`  
 <span data-ttu-id="399b8-110">Termine le `#If` bloc d’instructions.</span><span class="sxs-lookup"><span data-stu-id="399b8-110">Terminates the `#If` statement block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="399b8-111">Notes</span><span class="sxs-lookup"><span data-stu-id="399b8-111">Remarks</span></span>  
 <span data-ttu-id="399b8-112">Sur la surface, le comportement des `#If...Then...#Else` directives est le même que celui `If...Then...Else` des instructions.</span><span class="sxs-lookup"><span data-stu-id="399b8-112">On the surface, the behavior of the `#If...Then...#Else` directives appears the same as that of the `If...Then...Else` statements.</span></span> <span data-ttu-id="399b8-113">Toutefois, les `#If...Then...#Else` directives évaluent ce qui est compilé par le compilateur, `If...Then...Else` tandis que les instructions évaluent les conditions au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="399b8-113">However, the `#If...Then...#Else` directives evaluate what is compiled by the compiler, whereas the `If...Then...Else` statements evaluate conditions at run time.</span></span>  
  
 <span data-ttu-id="399b8-114">La compilation conditionnelle est généralement utilisée pour compiler le même programme pour différentes plateformes.</span><span class="sxs-lookup"><span data-stu-id="399b8-114">Conditional compilation is typically used to compile the same program for different platforms.</span></span> <span data-ttu-id="399b8-115">Il est également utilisé pour empêcher le débogage du code d’apparaître dans un fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="399b8-115">It is also used to prevent debugging code from appearing in an executable file.</span></span> <span data-ttu-id="399b8-116">Le code exclu pendant la compilation conditionnelle est complètement omis du fichier exécutable final. il n’a donc aucun effet sur la taille ou les performances.</span><span class="sxs-lookup"><span data-stu-id="399b8-116">Code excluded during conditional compilation is completely omitted from the final executable file, so it has no effect on size or performance.</span></span>  
  
 <span data-ttu-id="399b8-117">Quel que soit le résultat de l’évaluation, toutes les expressions sont `Option Compare Binary`évaluées à l’aide de.</span><span class="sxs-lookup"><span data-stu-id="399b8-117">Regardless of the outcome of any evaluation, all expressions are evaluated using `Option Compare Binary`.</span></span> <span data-ttu-id="399b8-118">L' `Option Compare` instruction n’affecte pas les expressions `#If` dans `#ElseIf` les instructions et.</span><span class="sxs-lookup"><span data-stu-id="399b8-118">The `Option Compare` statement does not affect expressions in `#If` and `#ElseIf` statements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="399b8-119">Il n’existe pas de formulaire à `#If`ligne `#Else`unique `#ElseIf`des directives `#End If` ,, et.</span><span class="sxs-lookup"><span data-stu-id="399b8-119">No single-line form of the `#If`, `#Else`, `#ElseIf`, and `#End If` directives exists.</span></span> <span data-ttu-id="399b8-120">Aucun autre code ne peut apparaître sur la même ligne que les directives.</span><span class="sxs-lookup"><span data-stu-id="399b8-120">No other code can appear on the same line as any of the directives.</span></span> 

<span data-ttu-id="399b8-121">Les instructions contenues dans un bloc de compilation conditionnelle doivent être des instructions logiques complètes.</span><span class="sxs-lookup"><span data-stu-id="399b8-121">The statements within a conditional compilation block must be complete logical statements.</span></span> <span data-ttu-id="399b8-122">Par exemple, vous ne pouvez pas compiler de façon conditionnelle uniquement les attributs d’une fonction, mais vous pouvez déclarer la fonction de manière conditionnelle avec ses attributs:</span><span class="sxs-lookup"><span data-stu-id="399b8-122">For example, you cannot conditionally compile only the attributes of a function, but you can conditionally declare the function along with its attributes:</span></span>

```vb
   #If DEBUG Then
   <WebMethod()>
   Public Function SomeFunction() As String
   #Else
   <WebMethod(CacheDuration:=86400)>
   Public Function SomeFunction() As String
   #End If
```

## <a name="example"></a><span data-ttu-id="399b8-123">Exemples</span><span class="sxs-lookup"><span data-stu-id="399b8-123">Example</span></span>
 <span data-ttu-id="399b8-124">Cet exemple utilise la `#If...Then...#Else` construction pour déterminer s’il faut compiler certaines instructions.</span><span class="sxs-lookup"><span data-stu-id="399b8-124">This example uses the `#If...Then...#Else` construct to determine whether to compile certain statements.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="399b8-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="399b8-125">See also</span></span>

- [<span data-ttu-id="399b8-126">#Const (directive)</span><span class="sxs-lookup"><span data-stu-id="399b8-126">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)
- [<span data-ttu-id="399b8-127">If...Then...Else (instruction)</span><span class="sxs-lookup"><span data-stu-id="399b8-127">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="399b8-128">Compilation conditionnelle</span><span class="sxs-lookup"><span data-stu-id="399b8-128">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>
