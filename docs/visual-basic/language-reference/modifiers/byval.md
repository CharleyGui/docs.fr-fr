---
title: Byval (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: abfe1489cb7e0d06b03c308e0704ce6f69ee55da
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433801"
---
# <a name="byval-visual-basic"></a><span data-ttu-id="6e465-102">Byval (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e465-102">ByVal (Visual Basic)</span></span>
<span data-ttu-id="6e465-103">Spécifie qu’un argument est passé [par valeur](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), de sorte que la procédure ou propriété appelée ne peut pas modifier la valeur d’une variable sous-jacente à l’argument dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="6e465-103">Specifies that an argument is passed [by value](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), so that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span></span> <span data-ttu-id="6e465-104">Si aucun modificateur n’est spécifié, ByVal est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="6e465-104">If no modifier is specified, ByVal is the default.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="6e465-105">Notes</span><span class="sxs-lookup"><span data-stu-id="6e465-105">Remarks</span></span>  
 <span data-ttu-id="6e465-106">Le modificateur `ByVal` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="6e465-106">The `ByVal` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="6e465-107">Declare (instruction)</span><span class="sxs-lookup"><span data-stu-id="6e465-107">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="6e465-108">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="6e465-108">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="6e465-109">Operator (instruction)</span><span class="sxs-lookup"><span data-stu-id="6e465-109">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="6e465-110">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="6e465-110">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="6e465-111">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="6e465-111">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="example"></a><span data-ttu-id="6e465-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="6e465-112">Example</span></span>  
 <span data-ttu-id="6e465-113">L’exemple suivant illustre l’utilisation du mécanisme `ByVal` de passage de paramètre avec un argument de type référence.</span><span class="sxs-lookup"><span data-stu-id="6e465-113">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span></span> <span data-ttu-id="6e465-114">Dans l’exemple, l’argument est `c1`, une instance de la `Class1`classe.</span><span class="sxs-lookup"><span data-stu-id="6e465-114">In the example, the argument is `c1`, an instance of class `Class1`.</span></span> <span data-ttu-id="6e465-115">`ByVal`empêche le code des procédures de modifier la valeur sous-jacente de l’argument de `c1`référence,, mais ne protège pas les champs et les `c1`propriétés accessibles de.</span><span class="sxs-lookup"><span data-stu-id="6e465-115">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="6e465-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e465-116">See also</span></span>

- [<span data-ttu-id="6e465-117">Mots clés</span><span class="sxs-lookup"><span data-stu-id="6e465-117">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="6e465-118">Passage d’un argument par valeur et par référence</span><span class="sxs-lookup"><span data-stu-id="6e465-118">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
