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
ms.openlocfilehash: a685be7cc3b346b271413e2c29faae5a839313f4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340242"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a><span data-ttu-id="e8e9f-102">Comment : appeler une procédure d'opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8e9f-102">How to: Call an Operator Procedure (Visual Basic)</span></span>
<span data-ttu-id="e8e9f-103">Vous appelez une procédure d’opérateur en utilisant le symbole d’opérateur dans une expression.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-103">You call an operator procedure by using the operator symbol in an expression.</span></span> <span data-ttu-id="e8e9f-104">Dans le cas d’un opérateur de conversion, vous appelez la [fonction CType](../../../../visual-basic/language-reference/functions/ctype-function.md) pour convertir une valeur d’un type de données en un autre.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-104">In the case of a conversion operator, you call the [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to convert a value from one data type to another.</span></span>  
  
 <span data-ttu-id="e8e9f-105">Vous n’appelez pas explicitement des procédures d’opérateur.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-105">You do not call operator procedures explicitly.</span></span> <span data-ttu-id="e8e9f-106">Vous utilisez simplement l’opérateur, ou la fonction `CType`, dans une instruction d’assignation ou une expression, de la même façon que vous utilisez habituellement un opérateur.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-106">You just use the operator, or the `CType` function, in an assignment statement or an expression, the same way you ordinarily use an operator.</span></span> <span data-ttu-id="e8e9f-107">Visual Basic effectue l’appel à la procédure d’opérateur.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-107">Visual Basic makes the call to the operator procedure.</span></span>  
  
 <span data-ttu-id="e8e9f-108">La définition d’un opérateur sur une classe ou une structure est également appelée *surcharge* de l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-108">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
### <a name="to-call-an-operator-procedure"></a><span data-ttu-id="e8e9f-109">Pour appeler une procédure d’opérateur</span><span class="sxs-lookup"><span data-stu-id="e8e9f-109">To call an operator procedure</span></span>  
  
1. <span data-ttu-id="e8e9f-110">Utilisez le symbole d’opérateur dans une expression de manière ordinaire.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-110">Use the operator symbol in an expression in the ordinary way.</span></span>  
  
2. <span data-ttu-id="e8e9f-111">Assurez-vous que les types de données des opérandes sont appropriés pour l’opérateur et dans le bon ordre.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-111">Be sure the data types of the operands are appropriate for the operator, and in the correct order.</span></span>  
  
3. <span data-ttu-id="e8e9f-112">L’opérateur contribue à la valeur de l’expression comme prévu.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-112">The operator contributes to the value of the expression as expected.</span></span>  
  
### <a name="to-call-a-conversion-operator-procedure"></a><span data-ttu-id="e8e9f-113">Pour appeler une procédure d’opérateur de conversion</span><span class="sxs-lookup"><span data-stu-id="e8e9f-113">To call a conversion operator procedure</span></span>  
  
1. <span data-ttu-id="e8e9f-114">Utilisez `CType` à l’intérieur d’une expression.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-114">Use `CType` inside an expression.</span></span>  
  
2. <span data-ttu-id="e8e9f-115">Assurez-vous que les types de données des opérandes sont appropriés pour la conversion et dans le bon ordre.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-115">Be sure the data types of the operands are appropriate for the conversion, and in the correct order.</span></span>  
  
3. <span data-ttu-id="e8e9f-116">`CType` appelle la procédure d’opérateur de conversion et retourne la valeur convertie.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-116">`CType` calls the conversion operator procedure and returns the converted value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8e9f-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="e8e9f-117">Example</span></span>  
 <span data-ttu-id="e8e9f-118">L’exemple suivant crée deux structures <xref:System.TimeSpan>, les ajoute et stocke le résultat dans une troisième <xref:System.TimeSpan> structure.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-118">The following example creates two <xref:System.TimeSpan> structures, adds them together, and stores the result in a third <xref:System.TimeSpan> structure.</span></span> <span data-ttu-id="e8e9f-119">La structure <xref:System.TimeSpan> définit des procédures d’opérateur pour surcharger plusieurs opérateurs standard.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-119">The <xref:System.TimeSpan> structure defines operator procedures to overload several standard operators.</span></span>  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 <span data-ttu-id="e8e9f-120">Étant donné que <xref:System.TimeSpan> surcharge l’opérateur `+` standard, l’exemple précédent appelle une procédure d’opérateur lorsqu’il calcule la valeur de `combinedSpan`.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-120">Because <xref:System.TimeSpan> overloads the standard `+` operator, the previous example calls an operator procedure when it calculates the value of `combinedSpan`.</span></span>  
  
 <span data-ttu-id="e8e9f-121">Pour obtenir un exemple d’appel d’une procédure d’opérateur de conversation, consultez [Comment : utiliser une classe qui définit des opérateurs](./how-to-use-a-class-that-defines-operators.md).</span><span class="sxs-lookup"><span data-stu-id="e8e9f-121">For an example of calling a conversation operator procedure, see [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e8e9f-122">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="e8e9f-122">Compiling the Code</span></span>  
 <span data-ttu-id="e8e9f-123">Assurez-vous que la classe ou la structure que vous utilisez définit l’opérateur que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="e8e9f-123">Be sure the class or structure you are using defines the operator you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8e9f-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8e9f-124">See also</span></span>

- [<span data-ttu-id="e8e9f-125">Procédures d’opérateur</span><span class="sxs-lookup"><span data-stu-id="e8e9f-125">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="e8e9f-126">Guide pratique : définir un opérateur</span><span class="sxs-lookup"><span data-stu-id="e8e9f-126">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="e8e9f-127">Guide pratique : définir un opérateur de conversion</span><span class="sxs-lookup"><span data-stu-id="e8e9f-127">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="e8e9f-128">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="e8e9f-128">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="e8e9f-129">Widening</span><span class="sxs-lookup"><span data-stu-id="e8e9f-129">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="e8e9f-130">Narrowing</span><span class="sxs-lookup"><span data-stu-id="e8e9f-130">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="e8e9f-131">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="e8e9f-131">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="e8e9f-132">Guide pratique : déclarer une structure</span><span class="sxs-lookup"><span data-stu-id="e8e9f-132">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="e8e9f-133">Conversions implicites et explicites</span><span class="sxs-lookup"><span data-stu-id="e8e9f-133">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="e8e9f-134">Conversions étendues et restrictives</span><span class="sxs-lookup"><span data-stu-id="e8e9f-134">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
