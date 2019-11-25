---
title: "Comment : déclarer un objet à l'aide d'un initialiseur d'objet"
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: ae04d338b61027c3917ad3a7f62ff40f0a95e53e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347134"
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a><span data-ttu-id="d937a-102">Comment : déclarer un objet à l'aide d'un initialiseur d'objet (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d937a-102">How to: Declare an Object by Using an Object Initializer (Visual Basic)</span></span>
<span data-ttu-id="d937a-103">Object initializers enable you to declare and instantiate an instance of a class in a single statement.</span><span class="sxs-lookup"><span data-stu-id="d937a-103">Object initializers enable you to declare and instantiate an instance of a class in a single statement.</span></span> <span data-ttu-id="d937a-104">In addition, you can initialize one or more members of the instance at the same time, without invoking a parameterized constructor.</span><span class="sxs-lookup"><span data-stu-id="d937a-104">In addition, you can initialize one or more members of the instance at the same time, without invoking a parameterized constructor.</span></span>  
  
 <span data-ttu-id="d937a-105">When you use an object initializer to create an instance of a named type, the parameterless constructor for the class is called, followed by initialization of designated members in the order you specify.</span><span class="sxs-lookup"><span data-stu-id="d937a-105">When you use an object initializer to create an instance of a named type, the parameterless constructor for the class is called, followed by initialization of designated members in the order you specify.</span></span>  
  
 <span data-ttu-id="d937a-106">The following procedure shows how to create an instance of a `Student` class in three different ways.</span><span class="sxs-lookup"><span data-stu-id="d937a-106">The following procedure shows how to create an instance of a `Student` class in three different ways.</span></span> <span data-ttu-id="d937a-107">The class has first name, last name, and class year properties, among others.</span><span class="sxs-lookup"><span data-stu-id="d937a-107">The class has first name, last name, and class year properties, among others.</span></span> <span data-ttu-id="d937a-108">Each of the three declarations creates a new instance of `Student`, with property `First` set to "Michael", property `Last` set to "Tucker", and all other members set to their default values.</span><span class="sxs-lookup"><span data-stu-id="d937a-108">Each of the three declarations creates a new instance of `Student`, with property `First` set to "Michael", property `Last` set to "Tucker", and all other members set to their default values.</span></span> <span data-ttu-id="d937a-109">The result of each declaration in the procedure is equivalent to the following example, which does not use an object initializer.</span><span class="sxs-lookup"><span data-stu-id="d937a-109">The result of each declaration in the procedure is equivalent to the following example, which does not use an object initializer.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#20)]  
  
 <span data-ttu-id="d937a-110">For an implementation of the `Student` class, see [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="d937a-110">For an implementation of the `Student` class, see [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span> <span data-ttu-id="d937a-111">You can copy the code from that topic to set up the class and create a list of `Student` objects to work with.</span><span class="sxs-lookup"><span data-stu-id="d937a-111">You can copy the code from that topic to set up the class and create a list of `Student` objects to work with.</span></span>  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a><span data-ttu-id="d937a-112">To create an object of a named class by using an object initializer</span><span class="sxs-lookup"><span data-stu-id="d937a-112">To create an object of a named class by using an object initializer</span></span>  
  
1. <span data-ttu-id="d937a-113">Begin the declaration as if you planned to use a constructor.</span><span class="sxs-lookup"><span data-stu-id="d937a-113">Begin the declaration as if you planned to use a constructor.</span></span>  
  
     `Dim student1 As New Student`  
  
2. <span data-ttu-id="d937a-114">Type the keyword `With`, followed by an initialization list in braces.</span><span class="sxs-lookup"><span data-stu-id="d937a-114">Type the keyword `With`, followed by an initialization list in braces.</span></span>  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3. <span data-ttu-id="d937a-115">In the initialization list, include each property that you want to initialize and assign an initial value to it.</span><span class="sxs-lookup"><span data-stu-id="d937a-115">In the initialization list, include each property that you want to initialize and assign an initial value to it.</span></span> <span data-ttu-id="d937a-116">The name of the property is preceded by a period.</span><span class="sxs-lookup"><span data-stu-id="d937a-116">The name of the property is preceded by a period.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#21)]  
  
     <span data-ttu-id="d937a-117">You can initialize one or more members of the class.</span><span class="sxs-lookup"><span data-stu-id="d937a-117">You can initialize one or more members of the class.</span></span>  
  
4. <span data-ttu-id="d937a-118">Alternatively, you can declare a new instance of the class and then assign a value to it.</span><span class="sxs-lookup"><span data-stu-id="d937a-118">Alternatively, you can declare a new instance of the class and then assign a value to it.</span></span> <span data-ttu-id="d937a-119">First, declare an instance of `Student`:</span><span class="sxs-lookup"><span data-stu-id="d937a-119">First, declare an instance of `Student`:</span></span>  
  
     `Dim student2 As Student`  
  
5. <span data-ttu-id="d937a-120">Begin the creation of an instance of `Student` in the normal way.</span><span class="sxs-lookup"><span data-stu-id="d937a-120">Begin the creation of an instance of `Student` in the normal way.</span></span>  
  
     `Dim student2 As Student = New Student`  
  
6. <span data-ttu-id="d937a-121">Type `With` and then an object initializer to initialize one or more members of the new instance.</span><span class="sxs-lookup"><span data-stu-id="d937a-121">Type `With` and then an object initializer to initialize one or more members of the new instance.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#22)]  
  
7. <span data-ttu-id="d937a-122">You can simplify the definition in the previous step by omitting `As Student`.</span><span class="sxs-lookup"><span data-stu-id="d937a-122">You can simplify the definition in the previous step by omitting `As Student`.</span></span> <span data-ttu-id="d937a-123">If you do this, the compiler determines that `student3` is an instance of `Student` by using local type inference.</span><span class="sxs-lookup"><span data-stu-id="d937a-123">If you do this, the compiler determines that `student3` is an instance of `Student` by using local type inference.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#23)]  
  
     <span data-ttu-id="d937a-124">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="d937a-124">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d937a-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d937a-125">See also</span></span>

- [<span data-ttu-id="d937a-126">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="d937a-126">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="d937a-127">Guide pratique : créer une liste d’éléments</span><span class="sxs-lookup"><span data-stu-id="d937a-127">How to: Create a List of Items</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)
- [<span data-ttu-id="d937a-128">Initialiseurs d’objets : types nommés et anonymes</span><span class="sxs-lookup"><span data-stu-id="d937a-128">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="d937a-129">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="d937a-129">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
