---
title: Procédures d'opérateur (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
ms.openlocfilehash: d62c3480db56b5cbf22c1f3f6ff59ab220a48b09
ms.sourcegitcommit: 5e05f983e63d5bbd8c0b246d02c6e4f23d2fc1db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2019
ms.locfileid: "67152037"
---
# <a name="operator-procedures-visual-basic"></a><span data-ttu-id="1d261-102">Procédures d'opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d261-102">Operator Procedures (Visual Basic)</span></span>
<span data-ttu-id="1d261-103">Une procédure d’opérateur est une série d’instructions Visual Basic qui définissent le comportement d’un opérateur standard (tel que `*`, `<>`, ou `And`) sur une classe ou structure que vous avez défini.</span><span class="sxs-lookup"><span data-stu-id="1d261-103">An operator procedure is a series of Visual Basic statements that define the behavior of a standard operator (such as `*`, `<>`, or `And`) on a class or structure you have defined.</span></span> <span data-ttu-id="1d261-104">Cela est également appelé *surcharge d’opérateur*.</span><span class="sxs-lookup"><span data-stu-id="1d261-104">This is also called *operator overloading*.</span></span>  
  
## <a name="when-to-define-operator-procedures"></a><span data-ttu-id="1d261-105">Quand définir des procédures d’opérateur</span><span class="sxs-lookup"><span data-stu-id="1d261-105">When to Define Operator Procedures</span></span>  
 <span data-ttu-id="1d261-106">Lorsque vous avez défini une classe ou structure, vous pouvez déclarer des variables pour être du type de cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="1d261-106">When you have defined a class or structure, you can declare variables to be of the type of that class or structure.</span></span> <span data-ttu-id="1d261-107">Parfois, cette variable doit participer à une opération dans le cadre d’une expression.</span><span class="sxs-lookup"><span data-stu-id="1d261-107">Sometimes such a variable needs to participate in an operation as part of an expression.</span></span> <span data-ttu-id="1d261-108">Pour ce faire, il doit être un opérande d’un opérateur.</span><span class="sxs-lookup"><span data-stu-id="1d261-108">To do this, it must be an operand of an operator.</span></span>  
  
 <span data-ttu-id="1d261-109">Visual Basic définit les opérateurs uniquement sur ses types de données essentielles.</span><span class="sxs-lookup"><span data-stu-id="1d261-109">Visual Basic defines operators only on its fundamental data types.</span></span> <span data-ttu-id="1d261-110">Vous pouvez définir le comportement d’un opérateur lorsqu’une ou les deux opérandes sont du type de votre classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="1d261-110">You can define the behavior of an operator when one or both of the operands are of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="1d261-111">Pour plus d’informations, consultez [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1d261-111">For more information, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
## <a name="types-of-operator-procedure"></a><span data-ttu-id="1d261-112">Types de procédure d’opérateur</span><span class="sxs-lookup"><span data-stu-id="1d261-112">Types of Operator Procedure</span></span>  
 <span data-ttu-id="1d261-113">Une procédure d’opérateur peut être un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="1d261-113">An operator procedure can be one of the following types:</span></span>  
  
- <span data-ttu-id="1d261-114">Définition d’un opérateur unaire où l’argument est du type de votre classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="1d261-114">A definition of a unary operator where the argument is of the type of your class or structure.</span></span>  
  
- <span data-ttu-id="1d261-115">Une définition d’un opérateur binaire, où au moins un des arguments est du type de votre classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="1d261-115">A definition of a binary operator where at least one of the arguments is of the type of your class or structure.</span></span>  
  
- <span data-ttu-id="1d261-116">Définition d’un opérateur de conversion où l’argument est du type de votre classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="1d261-116">A definition of a conversion operator where the argument is of the type of your class or structure.</span></span>  
  
- <span data-ttu-id="1d261-117">Définition d’un opérateur de conversion qui retourne le type de votre classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="1d261-117">A definition of a conversion operator that returns the type of your class or structure.</span></span>  
  
 <span data-ttu-id="1d261-118">Les opérateurs de conversion sont toujours unaires, et vous utilisez toujours `CType` comme l’opérateur que vous définissez.</span><span class="sxs-lookup"><span data-stu-id="1d261-118">Conversion operators are always unary, and you always use `CType` as the operator you are defining.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="1d261-119">Syntaxe de déclaration</span><span class="sxs-lookup"><span data-stu-id="1d261-119">Declaration Syntax</span></span>  
 <span data-ttu-id="1d261-120">La syntaxe de déclaration d’une procédure d’opérateur est la suivante :</span><span class="sxs-lookup"><span data-stu-id="1d261-120">The syntax for declaring an operator procedure is as follows:</span></span>  
 
 ```vb 
 Public Shared [Widening | Narrowing] Operator operatorsymbol ( operand1 [,  operand2 ]) As datatype  
  
 ' Statements of the operator procedure.
  
 End Operator
 ```
 
 <span data-ttu-id="1d261-121">Vous utilisez le `Widening` ou `Narrowing` mot clé uniquement sur un opérateur de conversion de type.</span><span class="sxs-lookup"><span data-stu-id="1d261-121">You use the `Widening` or `Narrowing` keyword only on a type conversion operator.</span></span> <span data-ttu-id="1d261-122">Le symbole d’opérateur est toujours [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) pour un opérateur de conversion de type.</span><span class="sxs-lookup"><span data-stu-id="1d261-122">The operator symbol is always [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) for a type conversion operator.</span></span>  
  
 <span data-ttu-id="1d261-123">Vous déclarez deux opérandes pour définir un opérateur binaire, et un seul opérande pour définir un opérateur unaire, y compris un opérateur de conversion de type.</span><span class="sxs-lookup"><span data-stu-id="1d261-123">You declare two operands to define a binary operator, and you declare one operand to define a unary operator, including a type conversion operator.</span></span> <span data-ttu-id="1d261-124">Tous les opérandes doivent être déclarées `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="1d261-124">All operands must be declared `ByVal`.</span></span>  
  
 <span data-ttu-id="1d261-125">Vous déclarez chaque opérande de la même façon que vous déclarez des paramètres pour [procédures Sub](./sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="1d261-125">You declare each operand the same way you declare parameters for [Sub Procedures](./sub-procedures.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="1d261-126">Type de données</span><span class="sxs-lookup"><span data-stu-id="1d261-126">Data Type</span></span>  
 <span data-ttu-id="1d261-127">Étant donné que vous définissez un opérateur sur une classe ou structure que vous avez défini, au moins un des opérandes doit être du type de données de cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="1d261-127">Because you are defining an operator on a class or structure you have defined, at least one of the operands must be of the data type of that class or structure.</span></span> <span data-ttu-id="1d261-128">Pour un opérateur de conversion de type, l’opérande ou le type de retour doit être du type de données de la classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="1d261-128">For a type conversion operator, either the operand or the return type must be of the data type of the class or structure.</span></span>  
  
 <span data-ttu-id="1d261-129">Pour plus d’informations, consultez [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1d261-129">For more details, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="1d261-130">Syntaxe d’appel</span><span class="sxs-lookup"><span data-stu-id="1d261-130">Calling Syntax</span></span>  
 <span data-ttu-id="1d261-131">Vous appelez une procédure d’opérateur implicitement en utilisant le symbole d’opérateur dans une expression.</span><span class="sxs-lookup"><span data-stu-id="1d261-131">You invoke an operator procedure implicitly by using the operator symbol in an expression.</span></span> <span data-ttu-id="1d261-132">Vous fournissez les opérandes de la même façon que vous le feriez pour les opérateurs prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="1d261-132">You supply the operands the same way you do for predefined operators.</span></span>  
  
 <span data-ttu-id="1d261-133">La syntaxe d’un appel implicite à une procédure d’opérateur est la suivante :</span><span class="sxs-lookup"><span data-stu-id="1d261-133">The syntax for an implicit call to an operator procedure is as follows:</span></span>  
  
 <span data-ttu-id="1d261-134">`Dim testStruct As`  *structurename*</span><span class="sxs-lookup"><span data-stu-id="1d261-134">`Dim testStruct As`  *structurename*</span></span>  
  
 <span data-ttu-id="1d261-135">`Dim testNewStruct As`  *structurename*  `= testStruct`  *operatorsymbol*  `10`</span><span class="sxs-lookup"><span data-stu-id="1d261-135">`Dim testNewStruct As`  *structurename*  `= testStruct`  *operatorsymbol*  `10`</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="1d261-136">Illustration de déclaration et d’appel</span><span class="sxs-lookup"><span data-stu-id="1d261-136">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="1d261-137">La structure suivante stocke une valeur entière signée de 128 bits en tant que les éléments constitutifs de poids fort et de poids faible.</span><span class="sxs-lookup"><span data-stu-id="1d261-137">The following structure stores a signed 128-bit integer value as the constituent high-order and low-order parts.</span></span> <span data-ttu-id="1d261-138">Il définit le `+` opérateur pour ajouter deux `veryLong` valeurs et générer résultant `veryLong` valeur.</span><span class="sxs-lookup"><span data-stu-id="1d261-138">It defines the `+` operator to add two `veryLong` values and generate a resulting `veryLong` value.</span></span>  
  
 [!code-vb[VbVbcnProcedures#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#23)]  
  
 <span data-ttu-id="1d261-139">L’exemple suivant montre un appel standard à la `+` opérateur défini sur `veryLong`.</span><span class="sxs-lookup"><span data-stu-id="1d261-139">The following example shows a typical call to the `+` operator defined on `veryLong`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#24)]  

## <a name="see-also"></a><span data-ttu-id="1d261-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d261-140">See also</span></span>

- [<span data-ttu-id="1d261-141">Procédures</span><span class="sxs-lookup"><span data-stu-id="1d261-141">Procedures</span></span>](./index.md)
- [<span data-ttu-id="1d261-142">Procédures Sub</span><span class="sxs-lookup"><span data-stu-id="1d261-142">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="1d261-143">Procédures Function</span><span class="sxs-lookup"><span data-stu-id="1d261-143">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="1d261-144">Procédures de propriété</span><span class="sxs-lookup"><span data-stu-id="1d261-144">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="1d261-145">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="1d261-145">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="1d261-146">Operator (instruction)</span><span class="sxs-lookup"><span data-stu-id="1d261-146">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="1d261-147">Guide pratique pour Définir un opérateur</span><span class="sxs-lookup"><span data-stu-id="1d261-147">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="1d261-148">Guide pratique pour Définir un opérateur de Conversion</span><span class="sxs-lookup"><span data-stu-id="1d261-148">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="1d261-149">Guide pratique pour Appeler une procédure d’opérateur</span><span class="sxs-lookup"><span data-stu-id="1d261-149">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="1d261-150">Guide pratique pour Utiliser une classe qui définit des opérateurs</span><span class="sxs-lookup"><span data-stu-id="1d261-150">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
