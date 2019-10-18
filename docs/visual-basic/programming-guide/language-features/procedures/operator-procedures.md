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
ms.openlocfilehash: 46afbbe411a1adf27960e3c7d9d3ca98046ecec5
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524527"
---
# <a name="operator-procedures-visual-basic"></a><span data-ttu-id="b491c-102">Procédures d'opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b491c-102">Operator Procedures (Visual Basic)</span></span>

<span data-ttu-id="b491c-103">Une procédure d’opérateur est une série d’instructions Visual Basic qui définissent le comportement d’un opérateur standard (comme `*`, `<>` ou `And`) sur une classe ou une structure que vous avez définie.</span><span class="sxs-lookup"><span data-stu-id="b491c-103">An operator procedure is a series of Visual Basic statements that define the behavior of a standard operator (such as `*`, `<>`, or `And`) on a class or structure you have defined.</span></span> <span data-ttu-id="b491c-104">C’est ce que l’on appelle également la *surcharge d’opérateur*.</span><span class="sxs-lookup"><span data-stu-id="b491c-104">This is also called *operator overloading*.</span></span>

## <a name="when-to-define-operator-procedures"></a><span data-ttu-id="b491c-105">Quand définir des procédures d’opérateur</span><span class="sxs-lookup"><span data-stu-id="b491c-105">When to Define Operator Procedures</span></span>

<span data-ttu-id="b491c-106">Lorsque vous avez défini une classe ou une structure, vous pouvez déclarer des variables comme étant du type de cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="b491c-106">When you have defined a class or structure, you can declare variables to be of the type of that class or structure.</span></span> <span data-ttu-id="b491c-107">Parfois, une telle variable doit participer à une opération dans le cadre d’une expression.</span><span class="sxs-lookup"><span data-stu-id="b491c-107">Sometimes such a variable needs to participate in an operation as part of an expression.</span></span> <span data-ttu-id="b491c-108">Pour ce faire, il doit s’agir d’un opérande d’un opérateur.</span><span class="sxs-lookup"><span data-stu-id="b491c-108">To do this, it must be an operand of an operator.</span></span>

<span data-ttu-id="b491c-109">Visual Basic définit des opérateurs uniquement sur ses types de données fondamentaux.</span><span class="sxs-lookup"><span data-stu-id="b491c-109">Visual Basic defines operators only on its fundamental data types.</span></span> <span data-ttu-id="b491c-110">Vous pouvez définir le comportement d’un opérateur quand l’un des opérandes ou les deux sont du type de votre classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="b491c-110">You can define the behavior of an operator when one or both of the operands are of the type of your class or structure.</span></span>

<span data-ttu-id="b491c-111">Pour plus d’informations, consultez [Operator, instruction](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b491c-111">For more information, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>

## <a name="types-of-operator-procedure"></a><span data-ttu-id="b491c-112">Types de procédure d’opérateur</span><span class="sxs-lookup"><span data-stu-id="b491c-112">Types of Operator Procedure</span></span>

<span data-ttu-id="b491c-113">Une procédure d’opérateur peut être de l’un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="b491c-113">An operator procedure can be one of the following types:</span></span>

- <span data-ttu-id="b491c-114">Définition d’un opérateur unaire dans lequel l’argument est du type de votre classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="b491c-114">A definition of a unary operator where the argument is of the type of your class or structure.</span></span>

- <span data-ttu-id="b491c-115">Définition d’un opérateur binaire où au moins l’un des arguments est du type de votre classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="b491c-115">A definition of a binary operator where at least one of the arguments is of the type of your class or structure.</span></span>

- <span data-ttu-id="b491c-116">Définition d’un opérateur de conversion où l’argument est du type de votre classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="b491c-116">A definition of a conversion operator where the argument is of the type of your class or structure.</span></span>

- <span data-ttu-id="b491c-117">Définition d’un opérateur de conversion qui retourne le type de votre classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="b491c-117">A definition of a conversion operator that returns the type of your class or structure.</span></span>

 <span data-ttu-id="b491c-118">Les opérateurs de conversion sont toujours unaires, et vous utilisez toujours `CType` comme opérateur que vous définissez.</span><span class="sxs-lookup"><span data-stu-id="b491c-118">Conversion operators are always unary, and you always use `CType` as the operator you are defining.</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="b491c-119">Syntaxe de déclaration</span><span class="sxs-lookup"><span data-stu-id="b491c-119">Declaration Syntax</span></span>

<span data-ttu-id="b491c-120">La syntaxe de la déclaration d’une procédure d’opérateur est la suivante :</span><span class="sxs-lookup"><span data-stu-id="b491c-120">The syntax for declaring an operator procedure is as follows:</span></span>

```vb
Public Shared [Widening | Narrowing] Operator operatorsymbol ( operand1 [,  operand2 ]) As datatype

' Statements of the operator procedure.

End Operator
```

<span data-ttu-id="b491c-121">Vous utilisez le mot clé `Widening` ou `Narrowing` uniquement sur un opérateur de conversion de type.</span><span class="sxs-lookup"><span data-stu-id="b491c-121">You use the `Widening` or `Narrowing` keyword only on a type conversion operator.</span></span> <span data-ttu-id="b491c-122">Le symbole d’opérateur est toujours la [fonction CType](../../../../visual-basic/language-reference/functions/ctype-function.md) pour un opérateur de conversion de type.</span><span class="sxs-lookup"><span data-stu-id="b491c-122">The operator symbol is always [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) for a type conversion operator.</span></span>

<span data-ttu-id="b491c-123">Vous pouvez déclarer deux opérandes pour définir un opérateur binaire et déclarer un opérande pour définir un opérateur unaire, y compris un opérateur de conversion de type.</span><span class="sxs-lookup"><span data-stu-id="b491c-123">You declare two operands to define a binary operator, and you declare one operand to define a unary operator, including a type conversion operator.</span></span> <span data-ttu-id="b491c-124">Tous les opérandes doivent être déclarés `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="b491c-124">All operands must be declared `ByVal`.</span></span>

<span data-ttu-id="b491c-125">Vous déclarez chaque opérande de la même façon que vous déclarez des paramètres pour les [procédures Sub](./sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b491c-125">You declare each operand the same way you declare parameters for [Sub Procedures](./sub-procedures.md).</span></span>

### <a name="data-type"></a><span data-ttu-id="b491c-126">Type de données</span><span class="sxs-lookup"><span data-stu-id="b491c-126">Data Type</span></span>

<span data-ttu-id="b491c-127">Étant donné que vous définissez un opérateur sur une classe ou une structure que vous avez définie, au moins l’un des opérandes doit être du type de données de cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="b491c-127">Because you are defining an operator on a class or structure you have defined, at least one of the operands must be of the data type of that class or structure.</span></span> <span data-ttu-id="b491c-128">Pour un opérateur de conversion de type, l’opérande ou le type de retour doit être du type de données de la classe ou de la structure.</span><span class="sxs-lookup"><span data-stu-id="b491c-128">For a type conversion operator, either the operand or the return type must be of the data type of the class or structure.</span></span>

<span data-ttu-id="b491c-129">Pour plus d’informations, consultez [Operator, instruction](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b491c-129">For more details, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="b491c-130">Syntaxe d’appel</span><span class="sxs-lookup"><span data-stu-id="b491c-130">Calling Syntax</span></span>

<span data-ttu-id="b491c-131">Vous appelez une procédure d’opérateur implicitement en utilisant le symbole d’opérateur dans une expression.</span><span class="sxs-lookup"><span data-stu-id="b491c-131">You invoke an operator procedure implicitly by using the operator symbol in an expression.</span></span> <span data-ttu-id="b491c-132">Vous fournissez les opérandes de la même façon que pour les opérateurs prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="b491c-132">You supply the operands the same way you do for predefined operators.</span></span>

<span data-ttu-id="b491c-133">La syntaxe d’un appel implicite à une procédure d’opérateur est la suivante :</span><span class="sxs-lookup"><span data-stu-id="b491c-133">The syntax for an implicit call to an operator procedure is as follows:</span></span>

<span data-ttu-id="b491c-134">`Dim testStruct As`  *structurename*</span><span class="sxs-lookup"><span data-stu-id="b491c-134">`Dim testStruct As`  *structurename*</span></span>

<span data-ttu-id="b491c-135">`Dim testNewStruct As`*structurename* `= testStruct`*operatorsymbol* `10`</span><span class="sxs-lookup"><span data-stu-id="b491c-135">`Dim testNewStruct As`  *structurename*  `= testStruct`  *operatorsymbol*  `10`</span></span>

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="b491c-136">Illustration de la déclaration et de l’appel</span><span class="sxs-lookup"><span data-stu-id="b491c-136">Illustration of Declaration and Call</span></span>

<span data-ttu-id="b491c-137">La structure suivante stocke une valeur d’entier 128 bits signée comme parties de poids fort et de poids faible constituantes.</span><span class="sxs-lookup"><span data-stu-id="b491c-137">The following structure stores a signed 128-bit integer value as the constituent high-order and low-order parts.</span></span> <span data-ttu-id="b491c-138">Il définit l’opérateur `+` pour ajouter deux valeurs `veryLong` et générer une valeur de `veryLong` résultante.</span><span class="sxs-lookup"><span data-stu-id="b491c-138">It defines the `+` operator to add two `veryLong` values and generate a resulting `veryLong` value.</span></span>

[!code-vb[VbVbcnProcedures#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#23)]

<span data-ttu-id="b491c-139">L’exemple suivant montre un appel typique à l’opérateur `+` défini sur `veryLong`.</span><span class="sxs-lookup"><span data-stu-id="b491c-139">The following example shows a typical call to the `+` operator defined on `veryLong`.</span></span>

[!code-vb[VbVbcnProcedures#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#24)]

## <a name="see-also"></a><span data-ttu-id="b491c-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b491c-140">See also</span></span>

- [<span data-ttu-id="b491c-141">Procédures</span><span class="sxs-lookup"><span data-stu-id="b491c-141">Procedures</span></span>](./index.md)
- [<span data-ttu-id="b491c-142">Procédures Sub</span><span class="sxs-lookup"><span data-stu-id="b491c-142">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="b491c-143">Procédures Function</span><span class="sxs-lookup"><span data-stu-id="b491c-143">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="b491c-144">Procédures de propriété</span><span class="sxs-lookup"><span data-stu-id="b491c-144">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="b491c-145">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="b491c-145">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="b491c-146">Operator (instruction)</span><span class="sxs-lookup"><span data-stu-id="b491c-146">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="b491c-147">Guide pratique : définir un opérateur</span><span class="sxs-lookup"><span data-stu-id="b491c-147">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="b491c-148">Guide pratique : définir un opérateur de conversion</span><span class="sxs-lookup"><span data-stu-id="b491c-148">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="b491c-149">Guide pratique : appeler une procédure d’opérateur</span><span class="sxs-lookup"><span data-stu-id="b491c-149">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="b491c-150">Guide pratique : utiliser une classe qui définit des opérateurs</span><span class="sxs-lookup"><span data-stu-id="b491c-150">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
