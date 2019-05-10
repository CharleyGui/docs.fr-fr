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
ms.openlocfilehash: cafc742474d6f7b46fbfb73374a59a350812a2a5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64639102"
---
# <a name="operator-procedures-visual-basic"></a><span data-ttu-id="b8694-102">Procédures d'opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8694-102">Operator Procedures (Visual Basic)</span></span>
<span data-ttu-id="b8694-103">Une procédure d’opérateur est une série d’instructions Visual Basic qui définissent le comportement d’un opérateur standard (tel que `*`, `<>`, ou `And`) sur une classe ou structure que vous avez défini.</span><span class="sxs-lookup"><span data-stu-id="b8694-103">An operator procedure is a series of Visual Basic statements that define the behavior of a standard operator (such as `*`, `<>`, or `And`) on a class or structure you have defined.</span></span> <span data-ttu-id="b8694-104">Cela est également appelé *surcharge d’opérateur*.</span><span class="sxs-lookup"><span data-stu-id="b8694-104">This is also called *operator overloading*.</span></span>  
  
## <a name="when-to-define-operator-procedures"></a><span data-ttu-id="b8694-105">Quand définir des procédures d’opérateur</span><span class="sxs-lookup"><span data-stu-id="b8694-105">When to Define Operator Procedures</span></span>  
 <span data-ttu-id="b8694-106">Lorsque vous avez défini une classe ou structure, vous pouvez déclarer des variables pour être du type de cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="b8694-106">When you have defined a class or structure, you can declare variables to be of the type of that class or structure.</span></span> <span data-ttu-id="b8694-107">Parfois, cette variable doit participer à une opération dans le cadre d’une expression.</span><span class="sxs-lookup"><span data-stu-id="b8694-107">Sometimes such a variable needs to participate in an operation as part of an expression.</span></span> <span data-ttu-id="b8694-108">Pour ce faire, il doit être un opérande d’un opérateur.</span><span class="sxs-lookup"><span data-stu-id="b8694-108">To do this, it must be an operand of an operator.</span></span>  
  
 <span data-ttu-id="b8694-109">Visual Basic définit les opérateurs uniquement sur ses types de données essentielles.</span><span class="sxs-lookup"><span data-stu-id="b8694-109">Visual Basic defines operators only on its fundamental data types.</span></span> <span data-ttu-id="b8694-110">Vous pouvez définir le comportement d’un opérateur lorsqu’une ou les deux opérandes sont du type de votre classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="b8694-110">You can define the behavior of an operator when one or both of the operands are of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="b8694-111">Pour plus d’informations, consultez [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b8694-111">For more information, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
## <a name="types-of-operator-procedure"></a><span data-ttu-id="b8694-112">Types de procédure d’opérateur</span><span class="sxs-lookup"><span data-stu-id="b8694-112">Types of Operator Procedure</span></span>  
 <span data-ttu-id="b8694-113">Une procédure d’opérateur peut être un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="b8694-113">An operator procedure can be one of the following types:</span></span>  
  
- <span data-ttu-id="b8694-114">Définition d’un opérateur unaire où l’argument est du type de votre classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="b8694-114">A definition of a unary operator where the argument is of the type of your class or structure.</span></span>  
  
- <span data-ttu-id="b8694-115">Une définition d’un opérateur binaire, où au moins un des arguments est du type de votre classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="b8694-115">A definition of a binary operator where at least one of the arguments is of the type of your class or structure.</span></span>  
  
- <span data-ttu-id="b8694-116">Définition d’un opérateur de conversion où l’argument est du type de votre classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="b8694-116">A definition of a conversion operator where the argument is of the type of your class or structure.</span></span>  
  
- <span data-ttu-id="b8694-117">Définition d’un opérateur de conversion qui retourne le type de votre classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="b8694-117">A definition of a conversion operator that returns the type of your class or structure.</span></span>  
  
 <span data-ttu-id="b8694-118">Les opérateurs de conversion sont toujours unaires, et vous utilisez toujours `CType` comme l’opérateur que vous définissez.</span><span class="sxs-lookup"><span data-stu-id="b8694-118">Conversion operators are always unary, and you always use `CType` as the operator you are defining.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="b8694-119">Syntaxe de déclaration</span><span class="sxs-lookup"><span data-stu-id="b8694-119">Declaration Syntax</span></span>  
 <span data-ttu-id="b8694-120">La syntaxe de déclaration d’une procédure d’opérateur est la suivante :</span><span class="sxs-lookup"><span data-stu-id="b8694-120">The syntax for declaring an operator procedure is as follows:</span></span>  
  
 <span data-ttu-id="b8694-121">`Public Shared`   `[Widening | Narrowing]`   `Operator`  *operatorsymbol*  `(` *operand1*  `[,`  *operand2* `]) As`  *datatype*</span><span class="sxs-lookup"><span data-stu-id="b8694-121">`Public Shared`   `[Widening | Narrowing]`   `Operator`  *operatorsymbol*  `(` *operand1*  `[,`  *operand2* `]) As`  *datatype*</span></span>  
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 <span data-ttu-id="b8694-122">Vous utilisez le `Widening` ou `Narrowing` mot clé uniquement sur un opérateur de conversion de type.</span><span class="sxs-lookup"><span data-stu-id="b8694-122">You use the `Widening` or `Narrowing` keyword only on a type conversion operator.</span></span> <span data-ttu-id="b8694-123">Le symbole d’opérateur est toujours [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) pour un opérateur de conversion de type.</span><span class="sxs-lookup"><span data-stu-id="b8694-123">The operator symbol is always [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) for a type conversion operator.</span></span>  
  
 <span data-ttu-id="b8694-124">Vous déclarez deux opérandes pour définir un opérateur binaire, et un seul opérande pour définir un opérateur unaire, y compris un opérateur de conversion de type.</span><span class="sxs-lookup"><span data-stu-id="b8694-124">You declare two operands to define a binary operator, and you declare one operand to define a unary operator, including a type conversion operator.</span></span> <span data-ttu-id="b8694-125">Tous les opérandes doivent être déclarées `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="b8694-125">All operands must be declared `ByVal`.</span></span>  
  
 <span data-ttu-id="b8694-126">Vous déclarez chaque opérande de la même façon que vous déclarez des paramètres pour [procédures Sub](./sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b8694-126">You declare each operand the same way you declare parameters for [Sub Procedures](./sub-procedures.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="b8694-127">Type de données</span><span class="sxs-lookup"><span data-stu-id="b8694-127">Data Type</span></span>  
 <span data-ttu-id="b8694-128">Étant donné que vous définissez un opérateur sur une classe ou structure que vous avez défini, au moins un des opérandes doit être du type de données de cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="b8694-128">Because you are defining an operator on a class or structure you have defined, at least one of the operands must be of the data type of that class or structure.</span></span> <span data-ttu-id="b8694-129">Pour un opérateur de conversion de type, l’opérande ou le type de retour doit être du type de données de la classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="b8694-129">For a type conversion operator, either the operand or the return type must be of the data type of the class or structure.</span></span>  
  
 <span data-ttu-id="b8694-130">Pour plus d’informations, consultez [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b8694-130">For more details, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="b8694-131">Syntaxe d’appel</span><span class="sxs-lookup"><span data-stu-id="b8694-131">Calling Syntax</span></span>  
 <span data-ttu-id="b8694-132">Vous appelez une procédure d’opérateur implicitement en utilisant le symbole d’opérateur dans une expression.</span><span class="sxs-lookup"><span data-stu-id="b8694-132">You invoke an operator procedure implicitly by using the operator symbol in an expression.</span></span> <span data-ttu-id="b8694-133">Vous fournissez les opérandes de la même façon que vous le feriez pour les opérateurs prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="b8694-133">You supply the operands the same way you do for predefined operators.</span></span>  
  
 <span data-ttu-id="b8694-134">La syntaxe d’un appel implicite à une procédure d’opérateur est la suivante :</span><span class="sxs-lookup"><span data-stu-id="b8694-134">The syntax for an implicit call to an operator procedure is as follows:</span></span>  
  
 <span data-ttu-id="b8694-135">`Dim testStruct As`  *structurename*</span><span class="sxs-lookup"><span data-stu-id="b8694-135">`Dim testStruct As`  *structurename*</span></span>  
  
 <span data-ttu-id="b8694-136">`Dim testNewStruct As`  *structurename*  `= testStruct`  *operatorsymbol*  `10`</span><span class="sxs-lookup"><span data-stu-id="b8694-136">`Dim testNewStruct As`  *structurename*  `= testStruct`  *operatorsymbol*  `10`</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="b8694-137">Illustration de déclaration et d’appel</span><span class="sxs-lookup"><span data-stu-id="b8694-137">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="b8694-138">La structure suivante stocke une valeur entière signée de 128 bits en tant que les éléments constitutifs de poids fort et de poids faible.</span><span class="sxs-lookup"><span data-stu-id="b8694-138">The following structure stores a signed 128-bit integer value as the constituent high-order and low-order parts.</span></span> <span data-ttu-id="b8694-139">Il définit le `+` opérateur pour ajouter deux `veryLong` valeurs et générer résultant `veryLong` valeur.</span><span class="sxs-lookup"><span data-stu-id="b8694-139">It defines the `+` operator to add two `veryLong` values and generate a resulting `veryLong` value.</span></span>  
  
 [!code-vb[VbVbcnProcedures#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#23)]  
  
 <span data-ttu-id="b8694-140">L’exemple suivant montre un appel standard à la `+` opérateur défini sur `veryLong`.</span><span class="sxs-lookup"><span data-stu-id="b8694-140">The following example shows a typical call to the `+` operator defined on `veryLong`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#24)]  

## <a name="see-also"></a><span data-ttu-id="b8694-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8694-141">See also</span></span>

- [<span data-ttu-id="b8694-142">Procédures</span><span class="sxs-lookup"><span data-stu-id="b8694-142">Procedures</span></span>](./index.md)
- [<span data-ttu-id="b8694-143">Procédures Sub</span><span class="sxs-lookup"><span data-stu-id="b8694-143">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="b8694-144">Procédures Function</span><span class="sxs-lookup"><span data-stu-id="b8694-144">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="b8694-145">Procédures de propriété</span><span class="sxs-lookup"><span data-stu-id="b8694-145">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="b8694-146">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="b8694-146">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="b8694-147">Operator (instruction)</span><span class="sxs-lookup"><span data-stu-id="b8694-147">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="b8694-148">Guide pratique pour Définir un opérateur</span><span class="sxs-lookup"><span data-stu-id="b8694-148">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="b8694-149">Guide pratique pour Définir un opérateur de Conversion</span><span class="sxs-lookup"><span data-stu-id="b8694-149">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="b8694-150">Guide pratique pour Appeler une procédure d’opérateur</span><span class="sxs-lookup"><span data-stu-id="b8694-150">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="b8694-151">Guide pratique pour Utiliser une classe qui définit des opérateurs</span><span class="sxs-lookup"><span data-stu-id="b8694-151">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
