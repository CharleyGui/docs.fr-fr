---
title: Procédures de propriété
ms.date: 07/20/2015
helpviewer_keywords:
- Set statement [Visual Basic], Property procedures
- Visual Basic code, procedures
- return values [Visual Basic], Property procedures
- syntax [Visual Basic], Property procedures
- procedures [Visual Basic], property
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], custom
- property procedures
- Get statement [Visual Basic], property procedures
ms.assetid: 46a98379-e1a2-45dd-a48c-b51213f5ab07
ms.openlocfilehash: a4b8ac3e27348764f537ee9502ce1fbb165bb3ef
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352562"
---
# <a name="property-procedures-visual-basic"></a><span data-ttu-id="2bb6b-102">Procédures de propriété (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2bb6b-102">Property Procedures (Visual Basic)</span></span>

<span data-ttu-id="2bb6b-103">A property procedure is a series of Visual Basic statements that manipulate a custom property on a module, class, or structure.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-103">A property procedure is a series of Visual Basic statements that manipulate a custom property on a module, class, or structure.</span></span> <span data-ttu-id="2bb6b-104">Property procedures are also known as *property accessors*.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-104">Property procedures are also known as *property accessors*.</span></span>

<span data-ttu-id="2bb6b-105">Visual Basic provides for the following property procedures:</span><span class="sxs-lookup"><span data-stu-id="2bb6b-105">Visual Basic provides for the following property procedures:</span></span>

- <span data-ttu-id="2bb6b-106">A `Get` procedure returns the value of a property.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-106">A `Get` procedure returns the value of a property.</span></span> <span data-ttu-id="2bb6b-107">It is called when you access the property in an expression.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-107">It is called when you access the property in an expression.</span></span>
- <span data-ttu-id="2bb6b-108">A `Set` procedure sets a property to a value, including an object reference.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-108">A `Set` procedure sets a property to a value, including an object reference.</span></span> <span data-ttu-id="2bb6b-109">It is called when you assign a value to the property.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-109">It is called when you assign a value to the property.</span></span>

<span data-ttu-id="2bb6b-110">You usually define property procedures in pairs, using the `Get` and `Set` statements, but you can define either procedure alone if the property is read-only ([Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md)) or write-only ([Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="2bb6b-110">You usually define property procedures in pairs, using the `Get` and `Set` statements, but you can define either procedure alone if the property is read-only ([Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md)) or write-only ([Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md)).</span></span>

<span data-ttu-id="2bb6b-111">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-111">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="2bb6b-112">Pour plus d’informations, consultez [Propriétés implémentées automatiquement](./auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="2bb6b-112">For more information, see [Auto-Implemented Properties](./auto-implemented-properties.md).</span></span>

<span data-ttu-id="2bb6b-113">You can define properties in classes, structures, and modules.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-113">You can define properties in classes, structures, and modules.</span></span> <span data-ttu-id="2bb6b-114">Properties are `Public` by default, which means you can call them from anywhere in your application that can access the property's container.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-114">Properties are `Public` by default, which means you can call them from anywhere in your application that can access the property's container.</span></span>

<span data-ttu-id="2bb6b-115">For a comparison of properties and variables, see [Differences Between Properties and Variables in Visual Basic](differences-between-properties-and-variables.md).</span><span class="sxs-lookup"><span data-stu-id="2bb6b-115">For a comparison of properties and variables, see [Differences Between Properties and Variables in Visual Basic](differences-between-properties-and-variables.md).</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="2bb6b-116">Declaration syntax</span><span class="sxs-lookup"><span data-stu-id="2bb6b-116">Declaration syntax</span></span>

<span data-ttu-id="2bb6b-117">A property itself is defined by a block of code enclosed within the [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-117">A property itself is defined by a block of code enclosed within the [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="2bb6b-118">Inside this block, each property procedure appears as an internal block enclosed within a declaration statement (`Get` or `Set`) and the matching `End` declaration.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-118">Inside this block, each property procedure appears as an internal block enclosed within a declaration statement (`Get` or `Set`) and the matching `End` declaration.</span></span>

<span data-ttu-id="2bb6b-119">The syntax for declaring a property and its procedures is as follows:</span><span class="sxs-lookup"><span data-stu-id="2bb6b-119">The syntax for declaring a property and its procedures is as follows:</span></span>

```vb
[Default] [Modifiers] Property PropertyName[(ParameterList)] [As DataType]
    [AccessLevel] Get
        ' Statements of the Get procedure.
        ' The following statement returns an expression as the property's value.
        Return Expression
    End Get
    [AccessLevel] Set[(ByVal NewValue As DataType)]
        ' Statements of the Set procedure.
        ' The following statement assigns newvalue as the property's value.
        LValue = NewValue
    End Set
End Property
' - or -
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]
```

<span data-ttu-id="2bb6b-120">The `Modifiers` can specify access level and information regarding overloading, overriding, sharing, and shadowing, as well as whether the property is read-only or write-only.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-120">The `Modifiers` can specify access level and information regarding overloading, overriding, sharing, and shadowing, as well as whether the property is read-only or write-only.</span></span> <span data-ttu-id="2bb6b-121">The `AccessLevel` on the `Get` or `Set` procedure can be any level that is more restrictive than the access level specified for the property itself.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-121">The `AccessLevel` on the `Get` or `Set` procedure can be any level that is more restrictive than the access level specified for the property itself.</span></span> <span data-ttu-id="2bb6b-122">For more information, see [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2bb6b-122">For more information, see [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md).</span></span>

### <a name="data-type"></a><span data-ttu-id="2bb6b-123">Type de données</span><span class="sxs-lookup"><span data-stu-id="2bb6b-123">Data Type</span></span>

<span data-ttu-id="2bb6b-124">A property's data type and principal access level are defined in the `Property` statement, not in the property procedures.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-124">A property's data type and principal access level are defined in the `Property` statement, not in the property procedures.</span></span> <span data-ttu-id="2bb6b-125">A property can have only one data type.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-125">A property can have only one data type.</span></span> <span data-ttu-id="2bb6b-126">For example, you cannot define a property to store a `Decimal` value but retrieve a `Double` value.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-126">For example, you cannot define a property to store a `Decimal` value but retrieve a `Double` value.</span></span>

### <a name="access-level"></a><span data-ttu-id="2bb6b-127">Access Level</span><span class="sxs-lookup"><span data-stu-id="2bb6b-127">Access Level</span></span>

<span data-ttu-id="2bb6b-128">However, you can define a principal access level for a property and further restrict the access level in one of its property procedures.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-128">However, you can define a principal access level for a property and further restrict the access level in one of its property procedures.</span></span> <span data-ttu-id="2bb6b-129">For example, you can define a `Public` property and then define a `Private Set` procedure.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-129">For example, you can define a `Public` property and then define a `Private Set` procedure.</span></span> <span data-ttu-id="2bb6b-130">The `Get` procedure remains `Public`.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-130">The `Get` procedure remains `Public`.</span></span> <span data-ttu-id="2bb6b-131">You can change the access level in only one of a property's procedures, and you can only make it more restrictive than the principal access level.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-131">You can change the access level in only one of a property's procedures, and you can only make it more restrictive than the principal access level.</span></span> <span data-ttu-id="2bb6b-132">For more information, see [How to: Declare a Property with Mixed Access Levels](how-to-declare-a-property-with-mixed-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2bb6b-132">For more information, see [How to: Declare a Property with Mixed Access Levels](how-to-declare-a-property-with-mixed-access-levels.md).</span></span>

## <a name="parameter-declaration"></a><span data-ttu-id="2bb6b-133">Parameter declaration</span><span class="sxs-lookup"><span data-stu-id="2bb6b-133">Parameter declaration</span></span>

<span data-ttu-id="2bb6b-134">You declare each parameter the same way you do for [Sub Procedures](sub-procedures.md), except that the passing mechanism must be `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-134">You declare each parameter the same way you do for [Sub Procedures](sub-procedures.md), except that the passing mechanism must be `ByVal`.</span></span>

<span data-ttu-id="2bb6b-135">The syntax for each parameter in the parameter list is as follows:</span><span class="sxs-lookup"><span data-stu-id="2bb6b-135">The syntax for each parameter in the parameter list is as follows:</span></span>

```vb
[Optional] ByVal [ParamArray] parametername As datatype
```

<span data-ttu-id="2bb6b-136">If the parameter is optional, you must also supply a default value as part of its declaration.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-136">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="2bb6b-137">The syntax for specifying a default value is as follows:</span><span class="sxs-lookup"><span data-stu-id="2bb6b-137">The syntax for specifying a default value is as follows:</span></span>

```vb
Optional ByVal parametername As datatype = defaultvalue
```

## <a name="property-value"></a><span data-ttu-id="2bb6b-138">Property value</span><span class="sxs-lookup"><span data-stu-id="2bb6b-138">Property value</span></span>

<span data-ttu-id="2bb6b-139">In a `Get` procedure, the return value is supplied to the calling expression as the value of the property.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-139">In a `Get` procedure, the return value is supplied to the calling expression as the value of the property.</span></span>

<span data-ttu-id="2bb6b-140">In a `Set` procedure, the new property value is passed to the parameter of the `Set` statement.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-140">In a `Set` procedure, the new property value is passed to the parameter of the `Set` statement.</span></span> <span data-ttu-id="2bb6b-141">If you explicitly declare a parameter, you must declare it with the same data type as the property.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-141">If you explicitly declare a parameter, you must declare it with the same data type as the property.</span></span> <span data-ttu-id="2bb6b-142">If you do not declare a parameter, the compiler uses the implicit parameter `Value` to represent the new value to be assigned to the property.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-142">If you do not declare a parameter, the compiler uses the implicit parameter `Value` to represent the new value to be assigned to the property.</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="2bb6b-143">Calling syntax</span><span class="sxs-lookup"><span data-stu-id="2bb6b-143">Calling syntax</span></span>

<span data-ttu-id="2bb6b-144">You invoke a property procedure implicitly by making reference to the property.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-144">You invoke a property procedure implicitly by making reference to the property.</span></span> <span data-ttu-id="2bb6b-145">You use the name of the property the same way you would use the name of a variable, except that you must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-145">You use the name of the property the same way you would use the name of a variable, except that you must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="2bb6b-146">If no arguments are supplied, you can optionally omit the parentheses.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-146">If no arguments are supplied, you can optionally omit the parentheses.</span></span>

<span data-ttu-id="2bb6b-147">The syntax for an implicit call to a `Set` procedure is as follows:</span><span class="sxs-lookup"><span data-stu-id="2bb6b-147">The syntax for an implicit call to a `Set` procedure is as follows:</span></span>

```vb
propertyname[(argumentlist)] = expression
```

<span data-ttu-id="2bb6b-148">The syntax for an implicit call to a `Get` procedure is as follows:</span><span class="sxs-lookup"><span data-stu-id="2bb6b-148">The syntax for an implicit call to a `Get` procedure is as follows:</span></span>

```vb
lvalue = propertyname[(argumentlist)]
Do While (propertyname[(argumentlist)] > expression)
```

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="2bb6b-149">Illustration of declaration and call</span><span class="sxs-lookup"><span data-stu-id="2bb6b-149">Illustration of declaration and call</span></span>

<span data-ttu-id="2bb6b-150">The following property stores a full name as two constituent names, the first name and the last name.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-150">The following property stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="2bb6b-151">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-151">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="2bb6b-152">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-152">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="2bb6b-153">If it does not find a space, it stores it all as the first name.</span><span class="sxs-lookup"><span data-stu-id="2bb6b-153">If it does not find a space, it stores it all as the first name.</span></span>

[!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]

<span data-ttu-id="2bb6b-154">The following example shows typical calls to the property procedures of `fullName`:</span><span class="sxs-lookup"><span data-stu-id="2bb6b-154">The following example shows typical calls to the property procedures of `fullName`:</span></span>

[!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]

## <a name="see-also"></a><span data-ttu-id="2bb6b-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2bb6b-155">See also</span></span>

- [<span data-ttu-id="2bb6b-156">Procédures</span><span class="sxs-lookup"><span data-stu-id="2bb6b-156">Procedures</span></span>](index.md)
- [<span data-ttu-id="2bb6b-157">Procédures Function</span><span class="sxs-lookup"><span data-stu-id="2bb6b-157">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="2bb6b-158">Procédures d’opérateur</span><span class="sxs-lookup"><span data-stu-id="2bb6b-158">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="2bb6b-159">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="2bb6b-159">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="2bb6b-160">Differences Between Properties and Variables in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2bb6b-160">Differences Between Properties and Variables in Visual Basic</span></span>](differences-between-properties-and-variables.md)
- [<span data-ttu-id="2bb6b-161">Guide pratique : créer une propriété</span><span class="sxs-lookup"><span data-stu-id="2bb6b-161">How to: Create a Property</span></span>](how-to-create-a-property.md)
- [<span data-ttu-id="2bb6b-162">Guide pratique : appeler une procédure de propriété</span><span class="sxs-lookup"><span data-stu-id="2bb6b-162">How to: Call a Property Procedure</span></span>](how-to-call-a-property-procedure.md)
- [<span data-ttu-id="2bb6b-163">How to: Declare and Call a Default Property in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2bb6b-163">How to: Declare and Call a Default Property in Visual Basic</span></span>](how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="2bb6b-164">Guide pratique : placer une valeur dans une propriété</span><span class="sxs-lookup"><span data-stu-id="2bb6b-164">How to: Put a Value in a Property</span></span>](how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="2bb6b-165">Guide pratique : obtenir une valeur d’une propriété</span><span class="sxs-lookup"><span data-stu-id="2bb6b-165">How to: Get a Value from a Property</span></span>](how-to-get-a-value-from-a-property.md)
