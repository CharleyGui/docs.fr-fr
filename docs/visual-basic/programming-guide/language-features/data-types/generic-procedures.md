---
title: Procédures génériques
ms.date: 07/20/2015
helpviewer_keywords:
- generic methods [Visual Basic], type inference
- generics [Visual Basic], type inference
- procedures [Visual Basic], generic
- generic procedures
- type inference, generics
- generic methods [Visual Basic]
- type inference
- generics [Visual Basic], procedures
- generic procedures [Visual Basic], type inference
ms.assetid: 95577b28-137f-4d5c-a149-919c828600e5
ms.openlocfilehash: 16a629e07cf711778b3d8d1863958ec7a6300649
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350081"
---
# <a name="generic-procedures-in-visual-basic"></a><span data-ttu-id="54e4c-102">Procédures génériques dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="54e4c-102">Generic Procedures in Visual Basic</span></span>
<span data-ttu-id="54e4c-103">A *generic procedure*, also called a *generic method*, is a procedure defined with at least one type parameter.</span><span class="sxs-lookup"><span data-stu-id="54e4c-103">A *generic procedure*, also called a *generic method*, is a procedure defined with at least one type parameter.</span></span> <span data-ttu-id="54e4c-104">This allows the calling code to tailor the data types to its requirements each time it calls the procedure.</span><span class="sxs-lookup"><span data-stu-id="54e4c-104">This allows the calling code to tailor the data types to its requirements each time it calls the procedure.</span></span>  
  
 <span data-ttu-id="54e4c-105">A procedure is not generic simply by virtue of being defined inside a generic class or a generic structure.</span><span class="sxs-lookup"><span data-stu-id="54e4c-105">A procedure is not generic simply by virtue of being defined inside a generic class or a generic structure.</span></span> <span data-ttu-id="54e4c-106">To be generic, the procedure must take at least one type parameter, in addition to any normal parameters it might take.</span><span class="sxs-lookup"><span data-stu-id="54e4c-106">To be generic, the procedure must take at least one type parameter, in addition to any normal parameters it might take.</span></span> <span data-ttu-id="54e4c-107">A generic class or structure can contain nongeneric procedures, and a nongeneric class, structure, or module can contain generic procedures.</span><span class="sxs-lookup"><span data-stu-id="54e4c-107">A generic class or structure can contain nongeneric procedures, and a nongeneric class, structure, or module can contain generic procedures.</span></span>  
  
 <span data-ttu-id="54e4c-108">A generic procedure can use its type parameters in its normal parameter list, in its return type if it has one, and in its procedure code.</span><span class="sxs-lookup"><span data-stu-id="54e4c-108">A generic procedure can use its type parameters in its normal parameter list, in its return type if it has one, and in its procedure code.</span></span>  
  
## <a name="type-inference"></a><span data-ttu-id="54e4c-109">Inférence de type</span><span class="sxs-lookup"><span data-stu-id="54e4c-109">Type Inference</span></span>  
 <span data-ttu-id="54e4c-110">You can call a generic procedure without supplying any type arguments at all.</span><span class="sxs-lookup"><span data-stu-id="54e4c-110">You can call a generic procedure without supplying any type arguments at all.</span></span> <span data-ttu-id="54e4c-111">If you call it this way, the compiler attempts to determine the appropriate data types to pass to the procedure's type arguments.</span><span class="sxs-lookup"><span data-stu-id="54e4c-111">If you call it this way, the compiler attempts to determine the appropriate data types to pass to the procedure's type arguments.</span></span> <span data-ttu-id="54e4c-112">This is called *type inference*.</span><span class="sxs-lookup"><span data-stu-id="54e4c-112">This is called *type inference*.</span></span> <span data-ttu-id="54e4c-113">The following code shows a call in which the compiler infers that it should pass type `String` to the type parameter `t`.</span><span class="sxs-lookup"><span data-stu-id="54e4c-113">The following code shows a call in which the compiler infers that it should pass type `String` to the type parameter `t`.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#15)]  
  
 <span data-ttu-id="54e4c-114">If the compiler cannot infer the type arguments from the context of your call, it reports an error.</span><span class="sxs-lookup"><span data-stu-id="54e4c-114">If the compiler cannot infer the type arguments from the context of your call, it reports an error.</span></span> <span data-ttu-id="54e4c-115">One possible cause of such an error is an array rank mismatch.</span><span class="sxs-lookup"><span data-stu-id="54e4c-115">One possible cause of such an error is an array rank mismatch.</span></span> <span data-ttu-id="54e4c-116">For example, suppose you define a normal parameter as an array of a type parameter.</span><span class="sxs-lookup"><span data-stu-id="54e4c-116">For example, suppose you define a normal parameter as an array of a type parameter.</span></span> <span data-ttu-id="54e4c-117">If you call the generic procedure supplying an array of a different rank (number of dimensions), the mismatch causes type inference to fail.</span><span class="sxs-lookup"><span data-stu-id="54e4c-117">If you call the generic procedure supplying an array of a different rank (number of dimensions), the mismatch causes type inference to fail.</span></span> <span data-ttu-id="54e4c-118">The following code shows a call in which a two-dimensional array is passed to a procedure that expects a one-dimensional array.</span><span class="sxs-lookup"><span data-stu-id="54e4c-118">The following code shows a call in which a two-dimensional array is passed to a procedure that expects a one-dimensional array.</span></span>  
  
```vb  
Public Sub demoSub(Of t)(ByVal arg() As t)
End Sub

Public Sub callDemoSub()
    Dim twoDimensions(,) As Integer
    demoSub(twoDimensions)
End Sub
```
  
 <span data-ttu-id="54e4c-119">You can invoke type inference only by omitting all the type arguments.</span><span class="sxs-lookup"><span data-stu-id="54e4c-119">You can invoke type inference only by omitting all the type arguments.</span></span> <span data-ttu-id="54e4c-120">If you supply one type argument, you must supply them all.</span><span class="sxs-lookup"><span data-stu-id="54e4c-120">If you supply one type argument, you must supply them all.</span></span>  
  
 <span data-ttu-id="54e4c-121">Type inference is supported only for generic procedures.</span><span class="sxs-lookup"><span data-stu-id="54e4c-121">Type inference is supported only for generic procedures.</span></span> <span data-ttu-id="54e4c-122">You cannot invoke type inference on generic classes, structures, interfaces, or delegates.</span><span class="sxs-lookup"><span data-stu-id="54e4c-122">You cannot invoke type inference on generic classes, structures, interfaces, or delegates.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54e4c-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="54e4c-123">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="54e4c-124">Description</span><span class="sxs-lookup"><span data-stu-id="54e4c-124">Description</span></span>  
 <span data-ttu-id="54e4c-125">The following example defines a generic `Function` procedure to find a particular element in an array.</span><span class="sxs-lookup"><span data-stu-id="54e4c-125">The following example defines a generic `Function` procedure to find a particular element in an array.</span></span> <span data-ttu-id="54e4c-126">It defines one type parameter and uses it to construct the two parameters in the parameter list.</span><span class="sxs-lookup"><span data-stu-id="54e4c-126">It defines one type parameter and uses it to construct the two parameters in the parameter list.</span></span>  
  
### <a name="code"></a><span data-ttu-id="54e4c-127">Code</span><span class="sxs-lookup"><span data-stu-id="54e4c-127">Code</span></span>  
 [!code-vb[VbVbalrDataTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#14)]  
  
### <a name="comments"></a><span data-ttu-id="54e4c-128">Comments</span><span class="sxs-lookup"><span data-stu-id="54e4c-128">Comments</span></span>  
 <span data-ttu-id="54e4c-129">The preceding example requires the ability to compare `searchValue` against each element of `searchArray`.</span><span class="sxs-lookup"><span data-stu-id="54e4c-129">The preceding example requires the ability to compare `searchValue` against each element of `searchArray`.</span></span> <span data-ttu-id="54e4c-130">To guarantee this ability, it constrains the type parameter `T` to implement the <xref:System.IComparable%601> interface.</span><span class="sxs-lookup"><span data-stu-id="54e4c-130">To guarantee this ability, it constrains the type parameter `T` to implement the <xref:System.IComparable%601> interface.</span></span> <span data-ttu-id="54e4c-131">The code uses the <xref:System.IComparable%601.CompareTo%2A> method instead of the `=` operator, because there is no guarantee that a type argument supplied for `T` supports the `=` operator.</span><span class="sxs-lookup"><span data-stu-id="54e4c-131">The code uses the <xref:System.IComparable%601.CompareTo%2A> method instead of the `=` operator, because there is no guarantee that a type argument supplied for `T` supports the `=` operator.</span></span>  
  
 <span data-ttu-id="54e4c-132">You can test the `findElement` procedure with the following code.</span><span class="sxs-lookup"><span data-stu-id="54e4c-132">You can test the `findElement` procedure with the following code.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#13)]  
  
 <span data-ttu-id="54e4c-133">The preceding calls to `MsgBox` display "0", "1", and "-1" respectively.</span><span class="sxs-lookup"><span data-stu-id="54e4c-133">The preceding calls to `MsgBox` display "0", "1", and "-1" respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54e4c-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54e4c-134">See also</span></span>

- [<span data-ttu-id="54e4c-135">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="54e4c-135">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="54e4c-136">Guide pratique : définir une classe qui fournisse des fonctionnalités identiques pour différents types de données</span><span class="sxs-lookup"><span data-stu-id="54e4c-136">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)
- [<span data-ttu-id="54e4c-137">Guide pratique : utiliser une classe générique</span><span class="sxs-lookup"><span data-stu-id="54e4c-137">How to: Use a Generic Class</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="54e4c-138">Procédures</span><span class="sxs-lookup"><span data-stu-id="54e4c-138">Procedures</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="54e4c-139">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="54e4c-139">Procedure Parameters and Arguments</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [<span data-ttu-id="54e4c-140">Liste de types</span><span class="sxs-lookup"><span data-stu-id="54e4c-140">Type List</span></span>](../../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="54e4c-141">Liste de paramètres</span><span class="sxs-lookup"><span data-stu-id="54e4c-141">Parameter List</span></span>](../../../../visual-basic/language-reference/statements/parameter-list.md)
