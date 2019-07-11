---
title: 'Procédure : Déclarez un objet à l’aide d’un initialiseur d’objet (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: 850e20fe8b5b6bfd392c80c87950a81a1a8a5c24
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755199"
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a><span data-ttu-id="f045c-102">Procédure : Déclarez un objet à l’aide d’un initialiseur d’objet (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f045c-102">How to: Declare an Object by Using an Object Initializer (Visual Basic)</span></span>
<span data-ttu-id="f045c-103">Initialiseurs d’objets permettent de déclarer et instancier une instance d’une classe dans une instruction unique.</span><span class="sxs-lookup"><span data-stu-id="f045c-103">Object initializers enable you to declare and instantiate an instance of a class in a single statement.</span></span> <span data-ttu-id="f045c-104">En outre, vous pouvez initialiser un ou plusieurs membres de l’instance en même temps, sans appeler un constructeur paramétrable.</span><span class="sxs-lookup"><span data-stu-id="f045c-104">In addition, you can initialize one or more members of the instance at the same time, without invoking a parameterized constructor.</span></span>  
  
 <span data-ttu-id="f045c-105">Lorsque vous utilisez un initialiseur d’objet pour créer une instance d’un type nommé, le constructeur sans paramètre pour la classe est appelé, suivie de l’initialisation de membres désignés dans l’ordre que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="f045c-105">When you use an object initializer to create an instance of a named type, the parameterless constructor for the class is called, followed by initialization of designated members in the order you specify.</span></span>  
  
 <span data-ttu-id="f045c-106">La procédure suivante montre comment créer une instance d’un `Student` classe de trois façons différentes.</span><span class="sxs-lookup"><span data-stu-id="f045c-106">The following procedure shows how to create an instance of a `Student` class in three different ways.</span></span> <span data-ttu-id="f045c-107">La classe a prénom, nom de famille, propriétés et de classe année, entre autres.</span><span class="sxs-lookup"><span data-stu-id="f045c-107">The class has first name, last name, and class year properties, among others.</span></span> <span data-ttu-id="f045c-108">Chacune des trois déclarations de crée une nouvelle instance de `Student`, avec la propriété `First` défini sur « Michael, « propriété `Last` défini sur « Tucker », et tous les autres membres définissent à leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="f045c-108">Each of the three declarations creates a new instance of `Student`, with property `First` set to "Michael", property `Last` set to "Tucker", and all other members set to their default values.</span></span> <span data-ttu-id="f045c-109">Le résultat de chaque déclaration dans la procédure est équivalent à l’exemple suivant, qui n’utilise pas un initialiseur d’objet.</span><span class="sxs-lookup"><span data-stu-id="f045c-109">The result of each declaration in the procedure is equivalent to the following example, which does not use an object initializer.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#20)]  
  
 <span data-ttu-id="f045c-110">Pour une implémentation de la `Student` de classe, consultez [Comment : Créer une liste d’éléments](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="f045c-110">For an implementation of the `Student` class, see [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span> <span data-ttu-id="f045c-111">Vous pouvez copier le code de cette rubrique pour définir la classe et créer une liste de `Student` objets à utiliser.</span><span class="sxs-lookup"><span data-stu-id="f045c-111">You can copy the code from that topic to set up the class and create a list of `Student` objects to work with.</span></span>  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a><span data-ttu-id="f045c-112">Pour créer un objet d’une classe nommée à l’aide d’un initialiseur d’objet</span><span class="sxs-lookup"><span data-stu-id="f045c-112">To create an object of a named class by using an object initializer</span></span>  
  
1. <span data-ttu-id="f045c-113">Commencez la déclaration comme si vous aviez prévu d’utiliser un constructeur.</span><span class="sxs-lookup"><span data-stu-id="f045c-113">Begin the declaration as if you planned to use a constructor.</span></span>  
  
     `Dim student1 As New Student`  
  
2. <span data-ttu-id="f045c-114">Tapez le mot clé `With`, suivie d’une liste d’initialisation entre accolades.</span><span class="sxs-lookup"><span data-stu-id="f045c-114">Type the keyword `With`, followed by an initialization list in braces.</span></span>  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3. <span data-ttu-id="f045c-115">Dans la liste d’initialisation, incluez chaque propriété que vous souhaitez initialiser et lui affecter une valeur initiale.</span><span class="sxs-lookup"><span data-stu-id="f045c-115">In the initialization list, include each property that you want to initialize and assign an initial value to it.</span></span> <span data-ttu-id="f045c-116">Le nom de la propriété est précédé d’un point.</span><span class="sxs-lookup"><span data-stu-id="f045c-116">The name of the property is preceded by a period.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#21)]  
  
     <span data-ttu-id="f045c-117">Vous pouvez initialiser un ou plusieurs membres de la classe.</span><span class="sxs-lookup"><span data-stu-id="f045c-117">You can initialize one or more members of the class.</span></span>  
  
4. <span data-ttu-id="f045c-118">Vous pouvez également déclarer une nouvelle instance de la classe et puis affectez-lui une valeur.</span><span class="sxs-lookup"><span data-stu-id="f045c-118">Alternatively, you can declare a new instance of the class and then assign a value to it.</span></span> <span data-ttu-id="f045c-119">Tout d’abord, déclarez une instance de `Student`:</span><span class="sxs-lookup"><span data-stu-id="f045c-119">First, declare an instance of `Student`:</span></span>  
  
     `Dim student2 As Student`  
  
5. <span data-ttu-id="f045c-120">Commencer la création d’une instance de `Student` de façon normale.</span><span class="sxs-lookup"><span data-stu-id="f045c-120">Begin the creation of an instance of `Student` in the normal way.</span></span>  
  
     `Dim student2 As Student = New Student`  
  
6. <span data-ttu-id="f045c-121">Type `With` et un initialiseur d’objet pour initialiser un ou plusieurs membres de la nouvelle instance.</span><span class="sxs-lookup"><span data-stu-id="f045c-121">Type `With` and then an object initializer to initialize one or more members of the new instance.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#22)]  
  
7. <span data-ttu-id="f045c-122">Vous pouvez simplifier la définition dans l’étape précédente en omettant `As Student`.</span><span class="sxs-lookup"><span data-stu-id="f045c-122">You can simplify the definition in the previous step by omitting `As Student`.</span></span> <span data-ttu-id="f045c-123">Si vous procédez ainsi, le compilateur détermine que `student3` est une instance de `Student` à l’aide de l’inférence de type local.</span><span class="sxs-lookup"><span data-stu-id="f045c-123">If you do this, the compiler determines that `student3` is an instance of `Student` by using local type inference.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#23)]  
  
     <span data-ttu-id="f045c-124">Pour plus d’informations, consultez [l’inférence de Type Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="f045c-124">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f045c-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f045c-125">See also</span></span>

- [<span data-ttu-id="f045c-126">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="f045c-126">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="f045c-127">Guide pratique : Créer une liste d’éléments</span><span class="sxs-lookup"><span data-stu-id="f045c-127">How to: Create a List of Items</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)
- [<span data-ttu-id="f045c-128">Initialiseurs d’objets : Types nommés et anonymes</span><span class="sxs-lookup"><span data-stu-id="f045c-128">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="f045c-129">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="f045c-129">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
