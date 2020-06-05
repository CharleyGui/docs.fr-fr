---
title: Procédures Property
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
ms.openlocfilehash: cb5b0e12512e476b7c96bbfb19f8e4f470f6b498
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363731"
---
# <a name="property-procedures-visual-basic"></a><span data-ttu-id="e1663-102">Procédures de propriété (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1663-102">Property Procedures (Visual Basic)</span></span>

<span data-ttu-id="e1663-103">Une procédure de propriété est une série d’instructions Visual Basic qui manipulent une propriété personnalisée sur un module, une classe ou une structure.</span><span class="sxs-lookup"><span data-stu-id="e1663-103">A property procedure is a series of Visual Basic statements that manipulate a custom property on a module, class, or structure.</span></span> <span data-ttu-id="e1663-104">Les procédures de propriété sont également appelées *accesseurs de propriété*.</span><span class="sxs-lookup"><span data-stu-id="e1663-104">Property procedures are also known as *property accessors*.</span></span>

<span data-ttu-id="e1663-105">Visual Basic fournit les procédures de propriété suivantes :</span><span class="sxs-lookup"><span data-stu-id="e1663-105">Visual Basic provides for the following property procedures:</span></span>

- <span data-ttu-id="e1663-106">Une `Get` procédure retourne la valeur d’une propriété.</span><span class="sxs-lookup"><span data-stu-id="e1663-106">A `Get` procedure returns the value of a property.</span></span> <span data-ttu-id="e1663-107">Elle est appelée lorsque vous accédez à la propriété dans une expression.</span><span class="sxs-lookup"><span data-stu-id="e1663-107">It is called when you access the property in an expression.</span></span>
- <span data-ttu-id="e1663-108">Une `Set` procédure affecte une valeur à une propriété, y compris une référence d’objet.</span><span class="sxs-lookup"><span data-stu-id="e1663-108">A `Set` procedure sets a property to a value, including an object reference.</span></span> <span data-ttu-id="e1663-109">Elle est appelée lorsque vous assignez une valeur à la propriété.</span><span class="sxs-lookup"><span data-stu-id="e1663-109">It is called when you assign a value to the property.</span></span>

<span data-ttu-id="e1663-110">Vous définissez généralement des procédures de propriété par paires, à l’aide des `Get` `Set` instructions et, mais vous pouvez définir l’une ou l’autre procédure uniquement si la propriété est en lecture seule ([instruction d’extraction](../../../language-reference/statements/get-statement.md)) ou en écriture seule ([instruction Set](../../../language-reference/statements/set-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="e1663-110">You usually define property procedures in pairs, using the `Get` and `Set` statements, but you can define either procedure alone if the property is read-only ([Get Statement](../../../language-reference/statements/get-statement.md)) or write-only ([Set Statement](../../../language-reference/statements/set-statement.md)).</span></span>

<span data-ttu-id="e1663-111">Vous pouvez omettre la `Get` `Set` procédure and lors de l’utilisation d’une propriété implémentée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="e1663-111">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="e1663-112">Pour plus d’informations, consultez [Propriétés implémentées automatiquement](./auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="e1663-112">For more information, see [Auto-Implemented Properties](./auto-implemented-properties.md).</span></span>

<span data-ttu-id="e1663-113">Vous pouvez définir des propriétés dans des classes, des structures et des modules.</span><span class="sxs-lookup"><span data-stu-id="e1663-113">You can define properties in classes, structures, and modules.</span></span> <span data-ttu-id="e1663-114">Les propriétés sont `Public` par défaut, ce qui signifie que vous pouvez les appeler à partir de n’importe où dans votre application qui peut accéder au conteneur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="e1663-114">Properties are `Public` by default, which means you can call them from anywhere in your application that can access the property's container.</span></span>

<span data-ttu-id="e1663-115">Pour une comparaison des propriétés et des variables, consultez [différences entre les propriétés et les variables dans Visual Basic](differences-between-properties-and-variables.md).</span><span class="sxs-lookup"><span data-stu-id="e1663-115">For a comparison of properties and variables, see [Differences Between Properties and Variables in Visual Basic](differences-between-properties-and-variables.md).</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="e1663-116">Syntaxe de déclaration</span><span class="sxs-lookup"><span data-stu-id="e1663-116">Declaration syntax</span></span>

<span data-ttu-id="e1663-117">Une propriété elle-même est définie par un bloc de code délimité par l' [instruction Property](../../../language-reference/statements/property-statement.md) et l' `End Property` instruction.</span><span class="sxs-lookup"><span data-stu-id="e1663-117">A property itself is defined by a block of code enclosed within the [Property Statement](../../../language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="e1663-118">À l’intérieur de ce bloc, chaque procédure de propriété apparaît sous la forme d’un bloc interne délimité par une instruction de déclaration ( `Get` ou `Set` ) et par la `End` déclaration correspondante.</span><span class="sxs-lookup"><span data-stu-id="e1663-118">Inside this block, each property procedure appears as an internal block enclosed within a declaration statement (`Get` or `Set`) and the matching `End` declaration.</span></span>

<span data-ttu-id="e1663-119">La syntaxe de déclaration d’une propriété et de ses procédures est la suivante :</span><span class="sxs-lookup"><span data-stu-id="e1663-119">The syntax for declaring a property and its procedures is as follows:</span></span>

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

<span data-ttu-id="e1663-120">`Modifiers`Peut spécifier le niveau d’accès et les informations relatives à la surcharge, à la substitution, au partage et à l’occultation, ainsi que la propriété est en lecture seule ou en écriture seule.</span><span class="sxs-lookup"><span data-stu-id="e1663-120">The `Modifiers` can specify access level and information regarding overloading, overriding, sharing, and shadowing, as well as whether the property is read-only or write-only.</span></span> <span data-ttu-id="e1663-121">Le `AccessLevel` sur la `Get` `Set` procédure ou peut être tout niveau qui est plus restrictif que le niveau d’accès spécifié pour la propriété elle-même.</span><span class="sxs-lookup"><span data-stu-id="e1663-121">The `AccessLevel` on the `Get` or `Set` procedure can be any level that is more restrictive than the access level specified for the property itself.</span></span> <span data-ttu-id="e1663-122">Pour plus d’informations, consultez [Property, instruction](../../../language-reference/statements/property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e1663-122">For more information, see [Property Statement](../../../language-reference/statements/property-statement.md).</span></span>

### <a name="data-type"></a><span data-ttu-id="e1663-123">Type de données</span><span class="sxs-lookup"><span data-stu-id="e1663-123">Data Type</span></span>

<span data-ttu-id="e1663-124">Le type de données et le niveau d’accès principal d’une propriété sont définis dans l' `Property` instruction, et non dans les procédures de propriété.</span><span class="sxs-lookup"><span data-stu-id="e1663-124">A property's data type and principal access level are defined in the `Property` statement, not in the property procedures.</span></span> <span data-ttu-id="e1663-125">Une propriété ne peut avoir qu’un seul type de données.</span><span class="sxs-lookup"><span data-stu-id="e1663-125">A property can have only one data type.</span></span> <span data-ttu-id="e1663-126">Par exemple, vous ne pouvez pas définir une propriété pour stocker une `Decimal` valeur, mais récupérer une `Double` valeur.</span><span class="sxs-lookup"><span data-stu-id="e1663-126">For example, you cannot define a property to store a `Decimal` value but retrieve a `Double` value.</span></span>

### <a name="access-level"></a><span data-ttu-id="e1663-127">Niveau d’accès</span><span class="sxs-lookup"><span data-stu-id="e1663-127">Access Level</span></span>

<span data-ttu-id="e1663-128">Toutefois, vous pouvez définir un niveau d’accès principal pour une propriété et restreindre davantage le niveau d’accès dans l’une de ses procédures de propriété.</span><span class="sxs-lookup"><span data-stu-id="e1663-128">However, you can define a principal access level for a property and further restrict the access level in one of its property procedures.</span></span> <span data-ttu-id="e1663-129">Par exemple, vous pouvez définir une `Public` propriété, puis définir une `Private Set` procédure.</span><span class="sxs-lookup"><span data-stu-id="e1663-129">For example, you can define a `Public` property and then define a `Private Set` procedure.</span></span> <span data-ttu-id="e1663-130">La `Get` procédure reste `Public` .</span><span class="sxs-lookup"><span data-stu-id="e1663-130">The `Get` procedure remains `Public`.</span></span> <span data-ttu-id="e1663-131">Vous pouvez modifier le niveau d’accès dans une seule des procédures d’une propriété, et vous pouvez le rendre plus restrictif que le niveau d’accès du principal.</span><span class="sxs-lookup"><span data-stu-id="e1663-131">You can change the access level in only one of a property's procedures, and you can only make it more restrictive than the principal access level.</span></span> <span data-ttu-id="e1663-132">Pour plus d’informations, consultez [Comment : déclarer une propriété avec des niveaux d’accès mixtes](how-to-declare-a-property-with-mixed-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="e1663-132">For more information, see [How to: Declare a Property with Mixed Access Levels](how-to-declare-a-property-with-mixed-access-levels.md).</span></span>

## <a name="parameter-declaration"></a><span data-ttu-id="e1663-133">Déclaration de paramètre</span><span class="sxs-lookup"><span data-stu-id="e1663-133">Parameter declaration</span></span>

<span data-ttu-id="e1663-134">Vous déclarez chaque paramètre de la même façon que pour les [procédures Sub](sub-procedures.md), sauf que le mécanisme de passage doit être `ByVal` .</span><span class="sxs-lookup"><span data-stu-id="e1663-134">You declare each parameter the same way you do for [Sub Procedures](sub-procedures.md), except that the passing mechanism must be `ByVal`.</span></span>

<span data-ttu-id="e1663-135">La syntaxe de chaque paramètre dans la liste de paramètres est la suivante :</span><span class="sxs-lookup"><span data-stu-id="e1663-135">The syntax for each parameter in the parameter list is as follows:</span></span>

```vb
[Optional] ByVal [ParamArray] parametername As datatype
```

<span data-ttu-id="e1663-136">Si le paramètre est facultatif, vous devez également fournir une valeur par défaut dans le cadre de sa déclaration.</span><span class="sxs-lookup"><span data-stu-id="e1663-136">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="e1663-137">La syntaxe permettant de spécifier une valeur par défaut est la suivante :</span><span class="sxs-lookup"><span data-stu-id="e1663-137">The syntax for specifying a default value is as follows:</span></span>

```vb
Optional ByVal parametername As datatype = defaultvalue
```

## <a name="property-value"></a><span data-ttu-id="e1663-138">Valeur de la propriété</span><span class="sxs-lookup"><span data-stu-id="e1663-138">Property value</span></span>

<span data-ttu-id="e1663-139">Dans une `Get` procédure, la valeur de retour est fournie à l’expression appelante comme valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="e1663-139">In a `Get` procedure, the return value is supplied to the calling expression as the value of the property.</span></span>

<span data-ttu-id="e1663-140">Dans une `Set` procédure, la nouvelle valeur de propriété est passée au paramètre de l' `Set` instruction.</span><span class="sxs-lookup"><span data-stu-id="e1663-140">In a `Set` procedure, the new property value is passed to the parameter of the `Set` statement.</span></span> <span data-ttu-id="e1663-141">Si vous déclarez explicitement un paramètre, vous devez le déclarer avec le même type de données que la propriété.</span><span class="sxs-lookup"><span data-stu-id="e1663-141">If you explicitly declare a parameter, you must declare it with the same data type as the property.</span></span> <span data-ttu-id="e1663-142">Si vous ne déclarez pas de paramètre, le compilateur utilise le paramètre implicite `Value` pour représenter la nouvelle valeur à assigner à la propriété.</span><span class="sxs-lookup"><span data-stu-id="e1663-142">If you do not declare a parameter, the compiler uses the implicit parameter `Value` to represent the new value to be assigned to the property.</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="e1663-143">Syntaxe d’appel</span><span class="sxs-lookup"><span data-stu-id="e1663-143">Calling syntax</span></span>

<span data-ttu-id="e1663-144">Vous appelez une procédure de propriété implicitement en faisant référence à la propriété.</span><span class="sxs-lookup"><span data-stu-id="e1663-144">You invoke a property procedure implicitly by making reference to the property.</span></span> <span data-ttu-id="e1663-145">Vous utilisez le nom de la propriété de la même façon que vous utilisez le nom d’une variable, mais vous devez fournir des valeurs pour tous les arguments qui ne sont pas facultatifs, et vous devez placer la liste d’arguments entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="e1663-145">You use the name of the property the same way you would use the name of a variable, except that you must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="e1663-146">Si aucun argument n’est fourni, vous pouvez éventuellement omettre les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="e1663-146">If no arguments are supplied, you can optionally omit the parentheses.</span></span>

<span data-ttu-id="e1663-147">La syntaxe d’un appel implicite à une `Set` procédure est la suivante :</span><span class="sxs-lookup"><span data-stu-id="e1663-147">The syntax for an implicit call to a `Set` procedure is as follows:</span></span>

```vb
propertyname[(argumentlist)] = expression
```

<span data-ttu-id="e1663-148">La syntaxe d’un appel implicite à une `Get` procédure est la suivante :</span><span class="sxs-lookup"><span data-stu-id="e1663-148">The syntax for an implicit call to a `Get` procedure is as follows:</span></span>

```vb
lvalue = propertyname[(argumentlist)]
Do While (propertyname[(argumentlist)] > expression)
```

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="e1663-149">Illustration de la déclaration et de l’appel</span><span class="sxs-lookup"><span data-stu-id="e1663-149">Illustration of declaration and call</span></span>

<span data-ttu-id="e1663-150">La propriété suivante stocke un nom complet sous la forme de deux noms constitutifs, le prénom et le nom.</span><span class="sxs-lookup"><span data-stu-id="e1663-150">The following property stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="e1663-151">Lorsque le code appelant lit `fullName` , la `Get` procédure combine les deux noms constitutifs et retourne le nom complet.</span><span class="sxs-lookup"><span data-stu-id="e1663-151">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="e1663-152">Lorsque le code appelant assigne un nouveau nom complet, la `Set` procédure tente de la décomposer en deux noms constitutifs.</span><span class="sxs-lookup"><span data-stu-id="e1663-152">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="e1663-153">S’il ne trouve pas d’espace, il le stocke comme premier nom.</span><span class="sxs-lookup"><span data-stu-id="e1663-153">If it does not find a space, it stores it all as the first name.</span></span>

[!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]

<span data-ttu-id="e1663-154">L’exemple suivant montre des appels classiques aux procédures de propriété de `fullName` :</span><span class="sxs-lookup"><span data-stu-id="e1663-154">The following example shows typical calls to the property procedures of `fullName`:</span></span>

[!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]

## <a name="see-also"></a><span data-ttu-id="e1663-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1663-155">See also</span></span>

- [<span data-ttu-id="e1663-156">Procédures</span><span class="sxs-lookup"><span data-stu-id="e1663-156">Procedures</span></span>](index.md)
- [<span data-ttu-id="e1663-157">Function, procédures</span><span class="sxs-lookup"><span data-stu-id="e1663-157">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="e1663-158">Procédures d'opérateur</span><span class="sxs-lookup"><span data-stu-id="e1663-158">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="e1663-159">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="e1663-159">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="e1663-160">Différences entre les propriétés et les variables en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e1663-160">Differences Between Properties and Variables in Visual Basic</span></span>](differences-between-properties-and-variables.md)
- [<span data-ttu-id="e1663-161">Comment : créer une propriété</span><span class="sxs-lookup"><span data-stu-id="e1663-161">How to: Create a Property</span></span>](how-to-create-a-property.md)
- [<span data-ttu-id="e1663-162">Comment : appeler une procédure de propriété</span><span class="sxs-lookup"><span data-stu-id="e1663-162">How to: Call a Property Procedure</span></span>](how-to-call-a-property-procedure.md)
- [<span data-ttu-id="e1663-163">Comment : déclarer et appeler une propriété par défaut en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e1663-163">How to: Declare and Call a Default Property in Visual Basic</span></span>](how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="e1663-164">Comment : placer une valeur dans une propriété</span><span class="sxs-lookup"><span data-stu-id="e1663-164">How to: Put a Value in a Property</span></span>](how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="e1663-165">Comment : obtenir une valeur d'une propriété</span><span class="sxs-lookup"><span data-stu-id="e1663-165">How to: Get a Value from a Property</span></span>](how-to-get-a-value-from-a-property.md)
