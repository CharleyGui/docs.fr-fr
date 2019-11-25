---
title: Méthodes partielles
ms.date: 07/20/2015
f1_keywords:
- vb.PartialMethod
- PartialMethod
helpviewer_keywords:
- custom logic into code [Visual Basic]
- partial methods [Visual Basic]
- partial [Visual Basic], methods [Visual Basic]
- methods [Visual Basic], partial methods
- inserting custom logic into code
ms.assetid: 74b3368b-b348-44a0-a326-7d7dc646f4e9
ms.openlocfilehash: 7abf0565a985f1fb44fcf2bb91b9220d57a10f20
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352637"
---
# <a name="partial-methods-visual-basic"></a><span data-ttu-id="a2117-102">Méthodes partielles (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2117-102">Partial Methods (Visual Basic)</span></span>
<span data-ttu-id="a2117-103">Partial methods enable developers to insert custom logic into code.</span><span class="sxs-lookup"><span data-stu-id="a2117-103">Partial methods enable developers to insert custom logic into code.</span></span> <span data-ttu-id="a2117-104">Typically, the code is part of a designer-generated class.</span><span class="sxs-lookup"><span data-stu-id="a2117-104">Typically, the code is part of a designer-generated class.</span></span> <span data-ttu-id="a2117-105">Partial methods are defined in a partial class that is created by a code generator, and they are commonly used to provide notification that something has been changed.</span><span class="sxs-lookup"><span data-stu-id="a2117-105">Partial methods are defined in a partial class that is created by a code generator, and they are commonly used to provide notification that something has been changed.</span></span> <span data-ttu-id="a2117-106">They enable the developer to specify custom behavior in response to the change.</span><span class="sxs-lookup"><span data-stu-id="a2117-106">They enable the developer to specify custom behavior in response to the change.</span></span>  
  
 <span data-ttu-id="a2117-107">The designer of the code generator defines only the method signature and one or more calls to the method.</span><span class="sxs-lookup"><span data-stu-id="a2117-107">The designer of the code generator defines only the method signature and one or more calls to the method.</span></span> <span data-ttu-id="a2117-108">Developers can then provide implementations for the method if they want to customize the behavior of the generated code.</span><span class="sxs-lookup"><span data-stu-id="a2117-108">Developers can then provide implementations for the method if they want to customize the behavior of the generated code.</span></span> <span data-ttu-id="a2117-109">When no implementation is provided, calls to the method are removed by the compiler, resulting in no additional performance overhead.</span><span class="sxs-lookup"><span data-stu-id="a2117-109">When no implementation is provided, calls to the method are removed by the compiler, resulting in no additional performance overhead.</span></span>  
  
## <a name="declaration"></a><span data-ttu-id="a2117-110">Déclaration</span><span class="sxs-lookup"><span data-stu-id="a2117-110">Declaration</span></span>  
 <span data-ttu-id="a2117-111">The generated code marks the definition of a partial method by placing the keyword `Partial` at the start of the signature line.</span><span class="sxs-lookup"><span data-stu-id="a2117-111">The generated code marks the definition of a partial method by placing the keyword `Partial` at the start of the signature line.</span></span>  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 <span data-ttu-id="a2117-112">The definition must meet the following conditions:</span><span class="sxs-lookup"><span data-stu-id="a2117-112">The definition must meet the following conditions:</span></span>  
  
- <span data-ttu-id="a2117-113">The method must be a `Sub`, not a `Function`.</span><span class="sxs-lookup"><span data-stu-id="a2117-113">The method must be a `Sub`, not a `Function`.</span></span>  
  
- <span data-ttu-id="a2117-114">The body of the method must be left empty.</span><span class="sxs-lookup"><span data-stu-id="a2117-114">The body of the method must be left empty.</span></span>  
  
- <span data-ttu-id="a2117-115">The access modifier must be `Private`.</span><span class="sxs-lookup"><span data-stu-id="a2117-115">The access modifier must be `Private`.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="a2117-116">Implémentation</span><span class="sxs-lookup"><span data-stu-id="a2117-116">Implementation</span></span>  
 <span data-ttu-id="a2117-117">The implementation consists primarily of filling in the body of the partial method.</span><span class="sxs-lookup"><span data-stu-id="a2117-117">The implementation consists primarily of filling in the body of the partial method.</span></span> <span data-ttu-id="a2117-118">The implementation is typically in a separate partial class from the definition, and is written by a developer who wants to extend the generated code.</span><span class="sxs-lookup"><span data-stu-id="a2117-118">The implementation is typically in a separate partial class from the definition, and is written by a developer who wants to extend the generated code.</span></span>  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 <span data-ttu-id="a2117-119">The previous example duplicates the signature in the declaration exactly, but variations are possible.</span><span class="sxs-lookup"><span data-stu-id="a2117-119">The previous example duplicates the signature in the declaration exactly, but variations are possible.</span></span> <span data-ttu-id="a2117-120">In particular, other modifiers can be added, such as `Overloads` or `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="a2117-120">In particular, other modifiers can be added, such as `Overloads` or `Overrides`.</span></span> <span data-ttu-id="a2117-121">Only one `Overrides` modifier is permitted.</span><span class="sxs-lookup"><span data-stu-id="a2117-121">Only one `Overrides` modifier is permitted.</span></span> <span data-ttu-id="a2117-122">For more information about method modifiers, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a2117-122">For more information about method modifiers, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="use"></a><span data-ttu-id="a2117-123">Utilisez</span><span class="sxs-lookup"><span data-stu-id="a2117-123">Use</span></span>  
 <span data-ttu-id="a2117-124">You call a partial method as you would call any other `Sub` procedure.</span><span class="sxs-lookup"><span data-stu-id="a2117-124">You call a partial method as you would call any other `Sub` procedure.</span></span> <span data-ttu-id="a2117-125">If the method has been implemented, the arguments are evaluated and the body of the method is executed.</span><span class="sxs-lookup"><span data-stu-id="a2117-125">If the method has been implemented, the arguments are evaluated and the body of the method is executed.</span></span> <span data-ttu-id="a2117-126">However, remember that implementing a partial method is optional.</span><span class="sxs-lookup"><span data-stu-id="a2117-126">However, remember that implementing a partial method is optional.</span></span> <span data-ttu-id="a2117-127">If the method is not implemented, a call to it has no effect, and expressions passed as arguments to the method are not evaluated.</span><span class="sxs-lookup"><span data-stu-id="a2117-127">If the method is not implemented, a call to it has no effect, and expressions passed as arguments to the method are not evaluated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2117-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="a2117-128">Example</span></span>  
 <span data-ttu-id="a2117-129">In a file named Product.Designer.vb, define a `Product` class that has a `Quantity` property.</span><span class="sxs-lookup"><span data-stu-id="a2117-129">In a file named Product.Designer.vb, define a `Product` class that has a `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#4)]  
  
 <span data-ttu-id="a2117-130">In a file named Product.vb, provide an implementation for `QuantityChanged`.</span><span class="sxs-lookup"><span data-stu-id="a2117-130">In a file named Product.vb, provide an implementation for `QuantityChanged`.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#5)]  
  
 <span data-ttu-id="a2117-131">Finally, in the Main method of a project, declare a `Product` instance and provide an initial value for its `Quantity` property.</span><span class="sxs-lookup"><span data-stu-id="a2117-131">Finally, in the Main method of a project, declare a `Product` instance and provide an initial value for its `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#6)]  
  
 <span data-ttu-id="a2117-132">A message box should appear that displays this message:</span><span class="sxs-lookup"><span data-stu-id="a2117-132">A message box should appear that displays this message:</span></span>  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a><span data-ttu-id="a2117-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2117-133">See also</span></span>

- [<span data-ttu-id="a2117-134">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="a2117-134">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="a2117-135">Procédures Sub</span><span class="sxs-lookup"><span data-stu-id="a2117-135">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="a2117-136">Paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="a2117-136">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="a2117-137">Partial</span><span class="sxs-lookup"><span data-stu-id="a2117-137">Partial</span></span>](../../../../visual-basic/language-reference/modifiers/partial.md)
- [<span data-ttu-id="a2117-138">Génération de code dans LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="a2117-138">Code Generation in LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="a2117-139">Ajout d’une logique métier à l’aide de méthodes partielles</span><span class="sxs-lookup"><span data-stu-id="a2117-139">Adding Business Logic By Using Partial Methods</span></span>](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
