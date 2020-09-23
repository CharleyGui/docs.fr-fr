---
title: "Comment : appeler une procédure d'opérateur"
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedure calls [Visual Basic], operator overloading
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- overloaded operators [Visual Basic], calling
- operator overloading
ms.assetid: 0dce42cc-f0b0-4c14-9f62-018b21f33497
ms.openlocfilehash: 0e88ff7b36535a709671a1f9b838f2b4488d1d37
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075185"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a><span data-ttu-id="ccf85-102">Comment : appeler une procédure d'opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ccf85-102">How to: Call an Operator Procedure (Visual Basic)</span></span>

<span data-ttu-id="ccf85-103">Vous appelez une procédure d’opérateur en utilisant le symbole d’opérateur dans une expression.</span><span class="sxs-lookup"><span data-stu-id="ccf85-103">You call an operator procedure by using the operator symbol in an expression.</span></span> <span data-ttu-id="ccf85-104">Dans le cas d’un opérateur de conversion, vous appelez la [fonction CType](../../../language-reference/functions/ctype-function.md) pour convertir une valeur d’un type de données en un autre.</span><span class="sxs-lookup"><span data-stu-id="ccf85-104">In the case of a conversion operator, you call the [CType Function](../../../language-reference/functions/ctype-function.md) to convert a value from one data type to another.</span></span>  
  
 <span data-ttu-id="ccf85-105">Vous n’appelez pas explicitement des procédures d’opérateur.</span><span class="sxs-lookup"><span data-stu-id="ccf85-105">You do not call operator procedures explicitly.</span></span> <span data-ttu-id="ccf85-106">Vous utilisez simplement l’opérateur, ou la `CType` fonction, dans une instruction d’assignation ou une expression, de la même façon que vous utilisez habituellement un opérateur.</span><span class="sxs-lookup"><span data-stu-id="ccf85-106">You just use the operator, or the `CType` function, in an assignment statement or an expression, the same way you ordinarily use an operator.</span></span> <span data-ttu-id="ccf85-107">Visual Basic effectue l’appel à la procédure d’opérateur.</span><span class="sxs-lookup"><span data-stu-id="ccf85-107">Visual Basic makes the call to the operator procedure.</span></span>  
  
 <span data-ttu-id="ccf85-108">La définition d’un opérateur sur une classe ou une structure est également appelée *surcharge* de l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="ccf85-108">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
### <a name="to-call-an-operator-procedure"></a><span data-ttu-id="ccf85-109">Pour appeler une procédure d’opérateur</span><span class="sxs-lookup"><span data-stu-id="ccf85-109">To call an operator procedure</span></span>  
  
1. <span data-ttu-id="ccf85-110">Utilisez le symbole d’opérateur dans une expression de manière ordinaire.</span><span class="sxs-lookup"><span data-stu-id="ccf85-110">Use the operator symbol in an expression in the ordinary way.</span></span>  
  
2. <span data-ttu-id="ccf85-111">Assurez-vous que les types de données des opérandes sont appropriés pour l’opérateur et dans le bon ordre.</span><span class="sxs-lookup"><span data-stu-id="ccf85-111">Be sure the data types of the operands are appropriate for the operator, and in the correct order.</span></span>  
  
3. <span data-ttu-id="ccf85-112">L’opérateur contribue à la valeur de l’expression comme prévu.</span><span class="sxs-lookup"><span data-stu-id="ccf85-112">The operator contributes to the value of the expression as expected.</span></span>  
  
### <a name="to-call-a-conversion-operator-procedure"></a><span data-ttu-id="ccf85-113">Pour appeler une procédure d’opérateur de conversion</span><span class="sxs-lookup"><span data-stu-id="ccf85-113">To call a conversion operator procedure</span></span>  
  
1. <span data-ttu-id="ccf85-114">Utilisez `CType` dans une expression.</span><span class="sxs-lookup"><span data-stu-id="ccf85-114">Use `CType` inside an expression.</span></span>  
  
2. <span data-ttu-id="ccf85-115">Assurez-vous que les types de données des opérandes sont appropriés pour la conversion et dans le bon ordre.</span><span class="sxs-lookup"><span data-stu-id="ccf85-115">Be sure the data types of the operands are appropriate for the conversion, and in the correct order.</span></span>  
  
3. <span data-ttu-id="ccf85-116">`CType` appelle la procédure d’opérateur de conversion et retourne la valeur convertie.</span><span class="sxs-lookup"><span data-stu-id="ccf85-116">`CType` calls the conversion operator procedure and returns the converted value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ccf85-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="ccf85-117">Example</span></span>  

 <span data-ttu-id="ccf85-118">L’exemple suivant crée deux <xref:System.TimeSpan> structures, les ajoute et stocke le résultat dans une troisième <xref:System.TimeSpan> structure.</span><span class="sxs-lookup"><span data-stu-id="ccf85-118">The following example creates two <xref:System.TimeSpan> structures, adds them together, and stores the result in a third <xref:System.TimeSpan> structure.</span></span> <span data-ttu-id="ccf85-119">La <xref:System.TimeSpan> structure définit des procédures d’opérateur pour surcharger plusieurs opérateurs standard.</span><span class="sxs-lookup"><span data-stu-id="ccf85-119">The <xref:System.TimeSpan> structure defines operator procedures to overload several standard operators.</span></span>  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 <span data-ttu-id="ccf85-120">Comme <xref:System.TimeSpan> surcharge de l’opérateur standard `+` , l’exemple précédent appelle une procédure d’opérateur lorsqu’il calcule la valeur de `combinedSpan` .</span><span class="sxs-lookup"><span data-stu-id="ccf85-120">Because <xref:System.TimeSpan> overloads the standard `+` operator, the previous example calls an operator procedure when it calculates the value of `combinedSpan`.</span></span>  
  
 <span data-ttu-id="ccf85-121">Pour obtenir un exemple d’appel d’une procédure d’opérateur de conversation, consultez [Comment : utiliser une classe qui définit des opérateurs](./how-to-use-a-class-that-defines-operators.md).</span><span class="sxs-lookup"><span data-stu-id="ccf85-121">For an example of calling a conversation operator procedure, see [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md).</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="ccf85-122">Compiler le code</span><span class="sxs-lookup"><span data-stu-id="ccf85-122">Compile the code</span></span>  

 <span data-ttu-id="ccf85-123">Assurez-vous que la classe ou la structure que vous utilisez définit l’opérateur que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="ccf85-123">Be sure the class or structure you are using defines the operator you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccf85-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ccf85-124">See also</span></span>

- [<span data-ttu-id="ccf85-125">Procédures d'opérateur</span><span class="sxs-lookup"><span data-stu-id="ccf85-125">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="ccf85-126">Comment : définir un opérateur</span><span class="sxs-lookup"><span data-stu-id="ccf85-126">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="ccf85-127">Guide pratique : définir un opérateur de conversion</span><span class="sxs-lookup"><span data-stu-id="ccf85-127">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="ccf85-128">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="ccf85-128">Operator Statement</span></span>](../../../language-reference/statements/operator-statement.md)
- [<span data-ttu-id="ccf85-129">Widening</span><span class="sxs-lookup"><span data-stu-id="ccf85-129">Widening</span></span>](../../../language-reference/modifiers/widening.md)
- [<span data-ttu-id="ccf85-130">Narrowing</span><span class="sxs-lookup"><span data-stu-id="ccf85-130">Narrowing</span></span>](../../../language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="ccf85-131">Structure, instruction</span><span class="sxs-lookup"><span data-stu-id="ccf85-131">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="ccf85-132">Procédure : Déclarer une structure</span><span class="sxs-lookup"><span data-stu-id="ccf85-132">How to: Declare a Structure</span></span>](../data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="ccf85-133">Conversions implicites et explicites</span><span class="sxs-lookup"><span data-stu-id="ccf85-133">Implicit and Explicit Conversions</span></span>](../data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="ccf85-134">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="ccf85-134">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
