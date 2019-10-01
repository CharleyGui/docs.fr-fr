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
ms.openlocfilehash: c5357dca24b03ddd03779866019baf14175be992
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698543"
---
# <a name="ifthenelse-directives"></a><span data-ttu-id="d680a-102">#If...Then...#Else, directives</span><span class="sxs-lookup"><span data-stu-id="d680a-102">#If...Then...#Else Directives</span></span>
<span data-ttu-id="d680a-103">Compile conditionnellement les blocs sélectionnés de Visual Basic code.</span><span class="sxs-lookup"><span data-stu-id="d680a-103">Conditionally compiles selected blocks of Visual Basic code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d680a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d680a-104">Syntax</span></span>  
  
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
  
## <a name="parts"></a><span data-ttu-id="d680a-105">Composants</span><span class="sxs-lookup"><span data-stu-id="d680a-105">Parts</span></span>  
 `expression`  
 <span data-ttu-id="d680a-106">Obligatoire pour les instructions `#If` et `#ElseIf`, facultatives ailleurs.</span><span class="sxs-lookup"><span data-stu-id="d680a-106">Required for `#If` and `#ElseIf` statements, optional elsewhere.</span></span> <span data-ttu-id="d680a-107">Toute expression, composée exclusivement d’une ou de plusieurs constantes de compilateur conditionnelles, de littéraux et d’opérateurs, qui prend la valeur `True` ou `False`.</span><span class="sxs-lookup"><span data-stu-id="d680a-107">Any expression, consisting exclusively of one or more conditional compiler constants, literals, and operators, that evaluates to `True` or `False`.</span></span>  
  
 `statements`  
 <span data-ttu-id="d680a-108">Requis pour le bloc d’instructions `#If`, facultatif ailleurs.</span><span class="sxs-lookup"><span data-stu-id="d680a-108">Required for `#If` statement block, optional elsewhere.</span></span> <span data-ttu-id="d680a-109">Visual Basic des lignes de programme ou des directives de compilateur compilées si l’expression associée prend la valeur `True`.</span><span class="sxs-lookup"><span data-stu-id="d680a-109">Visual Basic program lines or compiler directives that are compiled if the associated expression evaluates to `True`.</span></span>  
  
 `#End If`  
 <span data-ttu-id="d680a-110">Termine le bloc d’instructions `#If`.</span><span class="sxs-lookup"><span data-stu-id="d680a-110">Terminates the `#If` statement block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d680a-111">Notes</span><span class="sxs-lookup"><span data-stu-id="d680a-111">Remarks</span></span>  
 <span data-ttu-id="d680a-112">Sur la surface, le comportement des directives `#If...Then...#Else` apparaît comme celui des instructions `If...Then...Else`.</span><span class="sxs-lookup"><span data-stu-id="d680a-112">On the surface, the behavior of the `#If...Then...#Else` directives appears the same as that of the `If...Then...Else` statements.</span></span> <span data-ttu-id="d680a-113">Toutefois, les directives `#If...Then...#Else` évaluent ce qui est compilé par le compilateur, tandis que les instructions `If...Then...Else` évaluent les conditions au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="d680a-113">However, the `#If...Then...#Else` directives evaluate what is compiled by the compiler, whereas the `If...Then...Else` statements evaluate conditions at run time.</span></span>  
  
 <span data-ttu-id="d680a-114">La compilation conditionnelle est généralement utilisée pour compiler le même programme pour différentes plateformes.</span><span class="sxs-lookup"><span data-stu-id="d680a-114">Conditional compilation is typically used to compile the same program for different platforms.</span></span> <span data-ttu-id="d680a-115">Il est également utilisé pour empêcher le débogage du code d’apparaître dans un fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="d680a-115">It is also used to prevent debugging code from appearing in an executable file.</span></span> <span data-ttu-id="d680a-116">Le code exclu pendant la compilation conditionnelle est complètement omis du fichier exécutable final. il n’a donc aucun effet sur la taille ou les performances.</span><span class="sxs-lookup"><span data-stu-id="d680a-116">Code excluded during conditional compilation is completely omitted from the final executable file, so it has no effect on size or performance.</span></span>  
  
 <span data-ttu-id="d680a-117">Quel que soit le résultat de l’évaluation, toutes les expressions sont évaluées à l’aide de `Option Compare Binary`.</span><span class="sxs-lookup"><span data-stu-id="d680a-117">Regardless of the outcome of any evaluation, all expressions are evaluated using `Option Compare Binary`.</span></span> <span data-ttu-id="d680a-118">L’instruction `Option Compare` n’affecte pas les expressions dans les instructions `#If` et `#ElseIf`.</span><span class="sxs-lookup"><span data-stu-id="d680a-118">The `Option Compare` statement does not affect expressions in `#If` and `#ElseIf` statements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d680a-119">Il n’existe aucune forme à ligne unique des directives `#If`, `#Else`, `#ElseIf` et `#End If`.</span><span class="sxs-lookup"><span data-stu-id="d680a-119">No single-line form of the `#If`, `#Else`, `#ElseIf`, and `#End If` directives exists.</span></span> <span data-ttu-id="d680a-120">Aucun autre code ne peut apparaître sur la même ligne que les directives.</span><span class="sxs-lookup"><span data-stu-id="d680a-120">No other code can appear on the same line as any of the directives.</span></span> 

<span data-ttu-id="d680a-121">Les instructions contenues dans un bloc de compilation conditionnelle doivent être des instructions logiques complètes.</span><span class="sxs-lookup"><span data-stu-id="d680a-121">The statements within a conditional compilation block must be complete logical statements.</span></span> <span data-ttu-id="d680a-122">Par exemple, vous ne pouvez pas compiler de façon conditionnelle uniquement les attributs d’une fonction, mais vous pouvez déclarer la fonction de manière conditionnelle avec ses attributs :</span><span class="sxs-lookup"><span data-stu-id="d680a-122">For example, you cannot conditionally compile only the attributes of a function, but you can conditionally declare the function along with its attributes:</span></span>

```vb
   #If DEBUG Then
   <WebMethod()>
   Public Function SomeFunction() As String
   #Else
   <WebMethod(CacheDuration:=86400)>
   Public Function SomeFunction() As String
   #End If
```

## <a name="example"></a><span data-ttu-id="d680a-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="d680a-123">Example</span></span>
 <span data-ttu-id="d680a-124">Cet exemple utilise la construction `#If...Then...#Else` pour déterminer s’il faut compiler certaines instructions.</span><span class="sxs-lookup"><span data-stu-id="d680a-124">This example uses the `#If...Then...#Else` construct to determine whether to compile certain statements.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d680a-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d680a-125">See also</span></span>

- [<span data-ttu-id="d680a-126">#Const (directive)</span><span class="sxs-lookup"><span data-stu-id="d680a-126">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)
- [<span data-ttu-id="d680a-127">If...Then...Else (instruction)</span><span class="sxs-lookup"><span data-stu-id="d680a-127">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="d680a-128">Compilation conditionnelle</span><span class="sxs-lookup"><span data-stu-id="d680a-128">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>
