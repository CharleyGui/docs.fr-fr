---
title: 'Comment : utiliser une classe qui définit des opérateurs'
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedures [Visual Basic], calling
- examples [Visual Basic], CType
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
ms.openlocfilehash: 455c839702b90738ec5aea37c1b09d72eba42ff4
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347890"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a><span data-ttu-id="7ea73-102">Comment : utiliser une classe qui définit des opérateurs (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ea73-102">How to: Use a Class that Defines Operators (Visual Basic)</span></span>
<span data-ttu-id="7ea73-103">Si vous utilisez une classe ou une structure qui définit ses propres opérateurs, vous pouvez accéder à ces opérateurs à partir de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7ea73-103">If you are using a class or structure that defines its own operators, you can access those operators from Visual Basic.</span></span>  
  
 <span data-ttu-id="7ea73-104">La définition d’un opérateur sur une classe ou une structure est également appelée *surcharge* de l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="7ea73-104">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ea73-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="7ea73-105">Example</span></span>  
 <span data-ttu-id="7ea73-106">L’exemple suivant accède à la structure SQL <xref:System.Data.SqlTypes.SqlString>, qui définit les opérateurs de conversion ([fonction CType](../../../../visual-basic/language-reference/functions/ctype-function.md)) dans les deux directions entre une chaîne SQL et une chaîne Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7ea73-106">The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) in both directions between a SQL string and a Visual Basic string.</span></span> <span data-ttu-id="7ea73-107">Utilisez `CType(`*expression de chaîne SQL*, `String)` pour convertir une chaîne SQL en une chaîne Visual Basic et `CType(`*Visual Basic expression de chaîne*, <xref:System.Data.SqlTypes.SqlString>`)` pour la convertir dans l’autre sens.</span><span class="sxs-lookup"><span data-stu-id="7ea73-107">Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a Visual Basic string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.</span></span>  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 <span data-ttu-id="7ea73-108">La structure <xref:System.Data.SqlTypes.SqlString> définit un opérateur de conversion ([fonction CType](../../../../visual-basic/language-reference/functions/ctype-function.md)) de `String` à <xref:System.Data.SqlTypes.SqlString> et une autre <xref:System.Data.SqlTypes.SqlString> à `String`.</span><span class="sxs-lookup"><span data-stu-id="7ea73-108">The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`.</span></span> <span data-ttu-id="7ea73-109">L’instruction qui assigne `title` à `jobTitle` utilise le premier opérateur, et l’appel de fonction <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> utilise la seconde.</span><span class="sxs-lookup"><span data-stu-id="7ea73-109">The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="7ea73-110">Compiler le code</span><span class="sxs-lookup"><span data-stu-id="7ea73-110">Compile the code</span></span>  
 <span data-ttu-id="7ea73-111">Assurez-vous que la classe ou la structure que vous utilisez définit l’opérateur que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="7ea73-111">Be sure the class or structure you are using defines the operator you want to use.</span></span> <span data-ttu-id="7ea73-112">Ne partez pas du principe que la classe ou la structure a défini chaque opérateur disponible pour la surcharge.</span><span class="sxs-lookup"><span data-stu-id="7ea73-112">Do not assume that the class or structure has defined every operator available for overloading.</span></span> <span data-ttu-id="7ea73-113">Pour obtenir la liste des opérateurs disponibles, consultez [instruction Operator](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7ea73-113">For a list of available operators, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
 <span data-ttu-id="7ea73-114">Incluez l’instruction de `Imports` appropriée pour la chaîne SQL au début de votre fichier source (dans ce cas <xref:System.Data.SqlTypes>).</span><span class="sxs-lookup"><span data-stu-id="7ea73-114">Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).</span></span>  
  
 <span data-ttu-id="7ea73-115">Votre projet doit avoir des références à System. Data et System. XML.</span><span class="sxs-lookup"><span data-stu-id="7ea73-115">Your project must have references to System.Data and System.XML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ea73-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ea73-116">See also</span></span>

- [<span data-ttu-id="7ea73-117">Procédures d’opérateur</span><span class="sxs-lookup"><span data-stu-id="7ea73-117">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="7ea73-118">Guide pratique : définir un opérateur</span><span class="sxs-lookup"><span data-stu-id="7ea73-118">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="7ea73-119">Guide pratique : définir un opérateur de conversion</span><span class="sxs-lookup"><span data-stu-id="7ea73-119">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="7ea73-120">Guide pratique : appeler une procédure d’opérateur</span><span class="sxs-lookup"><span data-stu-id="7ea73-120">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="7ea73-121">Widening</span><span class="sxs-lookup"><span data-stu-id="7ea73-121">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="7ea73-122">Narrowing</span><span class="sxs-lookup"><span data-stu-id="7ea73-122">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="7ea73-123">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="7ea73-123">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="7ea73-124">Guide pratique : déclarer une structure</span><span class="sxs-lookup"><span data-stu-id="7ea73-124">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="7ea73-125">Conversions implicites et explicites</span><span class="sxs-lookup"><span data-stu-id="7ea73-125">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="7ea73-126">Conversions étendues et restrictives</span><span class="sxs-lookup"><span data-stu-id="7ea73-126">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
