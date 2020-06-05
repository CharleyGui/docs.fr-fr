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
ms.openlocfilehash: 2efc0410b9d4bb663e1ff19d5a5456d7ff2c99bd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394063"
---
# <a name="generic-procedures-in-visual-basic"></a><span data-ttu-id="c87b9-102">Procédures génériques dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c87b9-102">Generic Procedures in Visual Basic</span></span>
<span data-ttu-id="c87b9-103">Une *procédure générique*, également appelée *méthode générique*, est une procédure définie avec au moins un paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="c87b9-103">A *generic procedure*, also called a *generic method*, is a procedure defined with at least one type parameter.</span></span> <span data-ttu-id="c87b9-104">Cela permet au code appelant d’adapter les types de données à ses exigences chaque fois qu’il appelle la procédure.</span><span class="sxs-lookup"><span data-stu-id="c87b9-104">This allows the calling code to tailor the data types to its requirements each time it calls the procedure.</span></span>  
  
 <span data-ttu-id="c87b9-105">Une procédure n’est pas générique simplement en raison d’une définition à l’intérieur d’une classe générique ou d’une structure générique.</span><span class="sxs-lookup"><span data-stu-id="c87b9-105">A procedure is not generic simply by virtue of being defined inside a generic class or a generic structure.</span></span> <span data-ttu-id="c87b9-106">Pour être générique, la procédure doit accepter au moins un paramètre de type, en plus des paramètres normaux qu’il peut prendre.</span><span class="sxs-lookup"><span data-stu-id="c87b9-106">To be generic, the procedure must take at least one type parameter, in addition to any normal parameters it might take.</span></span> <span data-ttu-id="c87b9-107">Une classe ou une structure générique peut contenir des procédures non génériques, et une classe, une structure ou un module non générique peut contenir des procédures génériques.</span><span class="sxs-lookup"><span data-stu-id="c87b9-107">A generic class or structure can contain nongeneric procedures, and a nongeneric class, structure, or module can contain generic procedures.</span></span>  
  
 <span data-ttu-id="c87b9-108">Une procédure générique peut utiliser ses paramètres de type dans sa liste de paramètres normale, dans son type de retour, le cas échéant, et dans son code de procédure.</span><span class="sxs-lookup"><span data-stu-id="c87b9-108">A generic procedure can use its type parameters in its normal parameter list, in its return type if it has one, and in its procedure code.</span></span>  
  
## <a name="type-inference"></a><span data-ttu-id="c87b9-109">Inférence de type</span><span class="sxs-lookup"><span data-stu-id="c87b9-109">Type Inference</span></span>  
 <span data-ttu-id="c87b9-110">Vous pouvez appeler une procédure générique sans fournir de tout argument de type.</span><span class="sxs-lookup"><span data-stu-id="c87b9-110">You can call a generic procedure without supplying any type arguments at all.</span></span> <span data-ttu-id="c87b9-111">Si vous l’appelez de cette manière, le compilateur tente de déterminer les types de données appropriés à passer aux arguments de type de la procédure.</span><span class="sxs-lookup"><span data-stu-id="c87b9-111">If you call it this way, the compiler attempts to determine the appropriate data types to pass to the procedure's type arguments.</span></span> <span data-ttu-id="c87b9-112">C’est ce que l’on appelle l' *inférence de type*.</span><span class="sxs-lookup"><span data-stu-id="c87b9-112">This is called *type inference*.</span></span> <span data-ttu-id="c87b9-113">Le code suivant illustre un appel dans lequel le compilateur déduit qu’il doit passer le type `String` au paramètre de type `t` .</span><span class="sxs-lookup"><span data-stu-id="c87b9-113">The following code shows a call in which the compiler infers that it should pass type `String` to the type parameter `t`.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#15)]  
  
 <span data-ttu-id="c87b9-114">Si le compilateur ne peut pas déduire les arguments de type à partir du contexte de votre appel, il signale une erreur.</span><span class="sxs-lookup"><span data-stu-id="c87b9-114">If the compiler cannot infer the type arguments from the context of your call, it reports an error.</span></span> <span data-ttu-id="c87b9-115">Une erreur de ce type peut être due à une incompatibilité de rang de tableau.</span><span class="sxs-lookup"><span data-stu-id="c87b9-115">One possible cause of such an error is an array rank mismatch.</span></span> <span data-ttu-id="c87b9-116">Supposons, par exemple, que vous définissiez un paramètre normal en tant que tableau d’un paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="c87b9-116">For example, suppose you define a normal parameter as an array of a type parameter.</span></span> <span data-ttu-id="c87b9-117">Si vous appelez la procédure générique fournissant un tableau d’un rang différent (nombre de dimensions), l’incompatibilité entraîne l’échec de l’inférence de type.</span><span class="sxs-lookup"><span data-stu-id="c87b9-117">If you call the generic procedure supplying an array of a different rank (number of dimensions), the mismatch causes type inference to fail.</span></span> <span data-ttu-id="c87b9-118">Le code suivant illustre un appel dans lequel un tableau à deux dimensions est passé à une procédure qui attend un tableau unidimensionnel.</span><span class="sxs-lookup"><span data-stu-id="c87b9-118">The following code shows a call in which a two-dimensional array is passed to a procedure that expects a one-dimensional array.</span></span>  
  
```vb  
Public Sub demoSub(Of t)(ByVal arg() As t)
End Sub

Public Sub callDemoSub()
    Dim twoDimensions(,) As Integer
    demoSub(twoDimensions)
End Sub
```
  
 <span data-ttu-id="c87b9-119">Vous pouvez appeler l’inférence de type uniquement en omettant tous les arguments de type.</span><span class="sxs-lookup"><span data-stu-id="c87b9-119">You can invoke type inference only by omitting all the type arguments.</span></span> <span data-ttu-id="c87b9-120">Si vous fournissez un argument de type, vous devez tous les fournir.</span><span class="sxs-lookup"><span data-stu-id="c87b9-120">If you supply one type argument, you must supply them all.</span></span>  
  
 <span data-ttu-id="c87b9-121">L’inférence de type est prise en charge uniquement pour les procédures génériques.</span><span class="sxs-lookup"><span data-stu-id="c87b9-121">Type inference is supported only for generic procedures.</span></span> <span data-ttu-id="c87b9-122">Vous ne pouvez pas appeler l’inférence de type sur des classes, des structures, des interfaces ou des délégués génériques.</span><span class="sxs-lookup"><span data-stu-id="c87b9-122">You cannot invoke type inference on generic classes, structures, interfaces, or delegates.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c87b9-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="c87b9-123">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="c87b9-124">Description</span><span class="sxs-lookup"><span data-stu-id="c87b9-124">Description</span></span>  
 <span data-ttu-id="c87b9-125">L’exemple suivant définit une `Function` procédure générique pour rechercher un élément particulier dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="c87b9-125">The following example defines a generic `Function` procedure to find a particular element in an array.</span></span> <span data-ttu-id="c87b9-126">Il définit un paramètre de type et l’utilise pour construire les deux paramètres dans la liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="c87b9-126">It defines one type parameter and uses it to construct the two parameters in the parameter list.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c87b9-127">Code</span><span class="sxs-lookup"><span data-stu-id="c87b9-127">Code</span></span>  
 [!code-vb[VbVbalrDataTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#14)]  
  
### <a name="comments"></a><span data-ttu-id="c87b9-128">Commentaires</span><span class="sxs-lookup"><span data-stu-id="c87b9-128">Comments</span></span>  
 <span data-ttu-id="c87b9-129">L’exemple précédent nécessite la possibilité d’effectuer une comparaison `searchValue` par rapport à chaque élément de `searchArray` .</span><span class="sxs-lookup"><span data-stu-id="c87b9-129">The preceding example requires the ability to compare `searchValue` against each element of `searchArray`.</span></span> <span data-ttu-id="c87b9-130">Pour garantir cette capacité, il limite le paramètre `T` de type pour implémenter l' <xref:System.IComparable%601> interface.</span><span class="sxs-lookup"><span data-stu-id="c87b9-130">To guarantee this ability, it constrains the type parameter `T` to implement the <xref:System.IComparable%601> interface.</span></span> <span data-ttu-id="c87b9-131">Le code utilise la <xref:System.IComparable%601.CompareTo%2A> méthode au lieu de l' `=` opérateur, car il n’y a aucune garantie qu’un argument de type fourni pour `T` prend en charge l' `=` opérateur.</span><span class="sxs-lookup"><span data-stu-id="c87b9-131">The code uses the <xref:System.IComparable%601.CompareTo%2A> method instead of the `=` operator, because there is no guarantee that a type argument supplied for `T` supports the `=` operator.</span></span>  
  
 <span data-ttu-id="c87b9-132">Vous pouvez tester la `findElement` procédure à l’aide du code suivant.</span><span class="sxs-lookup"><span data-stu-id="c87b9-132">You can test the `findElement` procedure with the following code.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#13)]  
  
 <span data-ttu-id="c87b9-133">Les appels précédents à `MsgBox` affichent respectivement « 0 », « 1 » et « -1 ».</span><span class="sxs-lookup"><span data-stu-id="c87b9-133">The preceding calls to `MsgBox` display "0", "1", and "-1" respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c87b9-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c87b9-134">See also</span></span>

- [<span data-ttu-id="c87b9-135">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c87b9-135">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="c87b9-136">Procédure : Définir une classe qui fournisse des fonctionnalités identiques pour différents types de données</span><span class="sxs-lookup"><span data-stu-id="c87b9-136">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](how-to-define-a-class-that-can-provide-identical-functionality.md)
- [<span data-ttu-id="c87b9-137">Procédure : Utiliser une classe générique</span><span class="sxs-lookup"><span data-stu-id="c87b9-137">How to: Use a Generic Class</span></span>](how-to-use-a-generic-class.md)
- [<span data-ttu-id="c87b9-138">Procédures</span><span class="sxs-lookup"><span data-stu-id="c87b9-138">Procedures</span></span>](../procedures/index.md)
- [<span data-ttu-id="c87b9-139">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="c87b9-139">Procedure Parameters and Arguments</span></span>](../procedures/procedure-parameters-and-arguments.md)
- [<span data-ttu-id="c87b9-140">Type List</span><span class="sxs-lookup"><span data-stu-id="c87b9-140">Type List</span></span>](../../../language-reference/statements/type-list.md)
- [<span data-ttu-id="c87b9-141">Liste de paramètres</span><span class="sxs-lookup"><span data-stu-id="c87b9-141">Parameter List</span></span>](../../../language-reference/statements/parameter-list.md)
