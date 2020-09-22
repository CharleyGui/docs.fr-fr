---
title: ByVal
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: 8daf6600f59cea343e0d02b99632b92ce4bf3183
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875479"
---
# <a name="byval-visual-basic"></a><span data-ttu-id="722a5-102">Byval (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="722a5-102">ByVal (Visual Basic)</span></span>

<span data-ttu-id="722a5-103">Spécifie qu’un argument est passé [par valeur](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), de sorte que la procédure ou propriété appelée ne peut pas modifier la valeur d’une variable sous-jacente à l’argument dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="722a5-103">Specifies that an argument is passed [by value](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), so that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span></span> <span data-ttu-id="722a5-104">Si aucun modificateur n’est spécifié, ByVal est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="722a5-104">If no modifier is specified, ByVal is the default.</span></span>

> [!NOTE]
> <span data-ttu-id="722a5-105">Étant donné qu’il s’agit de la valeur par défaut, il n’est pas nécessaire de spécifier explicitement le `ByVal` mot clé dans les signatures de méthode.</span><span class="sxs-lookup"><span data-stu-id="722a5-105">Because it is the default, you do not have to explicitly specify the `ByVal` keyword in method signatures.</span></span> <span data-ttu-id="722a5-106">Il a tendance à produire du code bruyant et entraîne souvent un surexamen du mot clé non défini par défaut `ByRef` .</span><span class="sxs-lookup"><span data-stu-id="722a5-106">It tends to produce noisy code and often leads to the non-default `ByRef` keyword being overlooked.</span></span>

## <a name="remarks"></a><span data-ttu-id="722a5-107">Notes</span><span class="sxs-lookup"><span data-stu-id="722a5-107">Remarks</span></span>

 <span data-ttu-id="722a5-108">Le modificateur `ByVal` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="722a5-108">The `ByVal` modifier can be used in these contexts:</span></span>

 [<span data-ttu-id="722a5-109">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="722a5-109">Declare Statement</span></span>](../statements/declare-statement.md)

 [<span data-ttu-id="722a5-110">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="722a5-110">Function Statement</span></span>](../statements/function-statement.md)
  
 [<span data-ttu-id="722a5-111">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="722a5-111">Operator Statement</span></span>](../statements/operator-statement.md)
  
 [<span data-ttu-id="722a5-112">Property Statement</span><span class="sxs-lookup"><span data-stu-id="722a5-112">Property Statement</span></span>](../statements/property-statement.md)
  
 [<span data-ttu-id="722a5-113">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="722a5-113">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="example"></a><span data-ttu-id="722a5-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="722a5-114">Example</span></span>

 <span data-ttu-id="722a5-115">L’exemple suivant illustre l’utilisation du `ByVal` mécanisme de passage de paramètre avec un argument de type référence.</span><span class="sxs-lookup"><span data-stu-id="722a5-115">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span></span> <span data-ttu-id="722a5-116">Dans l’exemple, l’argument est `c1` , une instance de la classe `Class1` .</span><span class="sxs-lookup"><span data-stu-id="722a5-116">In the example, the argument is `c1`, an instance of class `Class1`.</span></span> <span data-ttu-id="722a5-117">`ByVal` empêche le code des procédures de modifier la valeur sous-jacente de l’argument de référence, `c1` , mais ne protège pas les champs et les propriétés accessibles de `c1` .</span><span class="sxs-lookup"><span data-stu-id="722a5-117">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span></span>

 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]

## <a name="see-also"></a><span data-ttu-id="722a5-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="722a5-118">See also</span></span>

- [<span data-ttu-id="722a5-119">Mots clés</span><span class="sxs-lookup"><span data-stu-id="722a5-119">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="722a5-120">Passage des arguments par valeur et par référence</span><span class="sxs-lookup"><span data-stu-id="722a5-120">Passing Arguments by Value and by Reference</span></span>](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
