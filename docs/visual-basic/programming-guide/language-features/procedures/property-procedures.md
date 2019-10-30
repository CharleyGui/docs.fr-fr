---
title: Procédures de propriété (Visual Basic)
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
ms.openlocfilehash: 118c9e776813f303ed921946f4cf6f1236ac02e3
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040971"
---
# <a name="property-procedures-visual-basic"></a><span data-ttu-id="a48c1-102">Procédures de propriété (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a48c1-102">Property Procedures (Visual Basic)</span></span>

<span data-ttu-id="a48c1-103">Une procédure de propriété est une série d’instructions Visual Basic qui manipulent une propriété personnalisée sur un module, une classe ou une structure.</span><span class="sxs-lookup"><span data-stu-id="a48c1-103">A property procedure is a series of Visual Basic statements that manipulate a custom property on a module, class, or structure.</span></span> <span data-ttu-id="a48c1-104">Les procédures de propriété sont également appelées *accesseurs de propriété*.</span><span class="sxs-lookup"><span data-stu-id="a48c1-104">Property procedures are also known as *property accessors*.</span></span>

<span data-ttu-id="a48c1-105">Visual Basic fournit les procédures de propriété suivantes :</span><span class="sxs-lookup"><span data-stu-id="a48c1-105">Visual Basic provides for the following property procedures:</span></span>

- <span data-ttu-id="a48c1-106">Une procédure `Get` retourne la valeur d’une propriété.</span><span class="sxs-lookup"><span data-stu-id="a48c1-106">A `Get` procedure returns the value of a property.</span></span> <span data-ttu-id="a48c1-107">Elle est appelée lorsque vous accédez à la propriété dans une expression.</span><span class="sxs-lookup"><span data-stu-id="a48c1-107">It is called when you access the property in an expression.</span></span>
- <span data-ttu-id="a48c1-108">Une procédure `Set` affecte une valeur à une propriété, y compris une référence d’objet.</span><span class="sxs-lookup"><span data-stu-id="a48c1-108">A `Set` procedure sets a property to a value, including an object reference.</span></span> <span data-ttu-id="a48c1-109">Elle est appelée lorsque vous assignez une valeur à la propriété.</span><span class="sxs-lookup"><span data-stu-id="a48c1-109">It is called when you assign a value to the property.</span></span>

<span data-ttu-id="a48c1-110">Vous définissez généralement des procédures de propriété par paires, à l’aide des instructions `Get` et `Set`, mais vous pouvez définir l’une ou l’autre procédure uniquement si la propriété est en lecture seule ([instruction d’extraction](../../../../visual-basic/language-reference/statements/get-statement.md)) ou en écriture seule ([instruction Set](../../../../visual-basic/language-reference/statements/set-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="a48c1-110">You usually define property procedures in pairs, using the `Get` and `Set` statements, but you can define either procedure alone if the property is read-only ([Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md)) or write-only ([Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md)).</span></span>

<span data-ttu-id="a48c1-111">Vous pouvez omettre les `Get` et `Set` procédure lors de l’utilisation d’une propriété implémentée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="a48c1-111">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="a48c1-112">Pour plus d’informations, consultez [Propriétés implémentées automatiquement](./auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="a48c1-112">For more information, see [Auto-Implemented Properties](./auto-implemented-properties.md).</span></span>

<span data-ttu-id="a48c1-113">Vous pouvez définir des propriétés dans des classes, des structures et des modules.</span><span class="sxs-lookup"><span data-stu-id="a48c1-113">You can define properties in classes, structures, and modules.</span></span> <span data-ttu-id="a48c1-114">Les propriétés sont `Public` par défaut, ce qui signifie que vous pouvez les appeler à partir de n’importe où dans votre application qui peut accéder au conteneur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="a48c1-114">Properties are `Public` by default, which means you can call them from anywhere in your application that can access the property's container.</span></span>

<span data-ttu-id="a48c1-115">Pour une comparaison des propriétés et des variables, consultez [différences entre les propriétés et les variables dans Visual Basic](differences-between-properties-and-variables.md).</span><span class="sxs-lookup"><span data-stu-id="a48c1-115">For a comparison of properties and variables, see [Differences Between Properties and Variables in Visual Basic](differences-between-properties-and-variables.md).</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="a48c1-116">Syntaxe de déclaration</span><span class="sxs-lookup"><span data-stu-id="a48c1-116">Declaration syntax</span></span>

<span data-ttu-id="a48c1-117">Une propriété elle-même est définie par un bloc de code placé entre l' [instruction Property](../../../../visual-basic/language-reference/statements/property-statement.md) et l’instruction `End Property`.</span><span class="sxs-lookup"><span data-stu-id="a48c1-117">A property itself is defined by a block of code enclosed within the [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="a48c1-118">À l’intérieur de ce bloc, chaque procédure de propriété apparaît sous la forme d’un bloc interne délimité par une instruction de déclaration (`Get` ou `Set`) et de la déclaration de `End` correspondante.</span><span class="sxs-lookup"><span data-stu-id="a48c1-118">Inside this block, each property procedure appears as an internal block enclosed within a declaration statement (`Get` or `Set`) and the matching `End` declaration.</span></span>

<span data-ttu-id="a48c1-119">La syntaxe de déclaration d’une propriété et de ses procédures est la suivante :</span><span class="sxs-lookup"><span data-stu-id="a48c1-119">The syntax for declaring a property and its procedures is as follows:</span></span>

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

<span data-ttu-id="a48c1-120">La `Modifiers` peut spécifier le niveau d’accès et les informations relatives à la surcharge, à la substitution, au partage et à l’occultation, ainsi que la propriété en lecture seule ou en écriture seule.</span><span class="sxs-lookup"><span data-stu-id="a48c1-120">The `Modifiers` can specify access level and information regarding overloading, overriding, sharing, and shadowing, as well as whether the property is read-only or write-only.</span></span> <span data-ttu-id="a48c1-121">La `AccessLevel` sur la procédure `Get` ou `Set` peut être n’importe quel niveau qui est plus restrictif que le niveau d’accès spécifié pour la propriété elle-même.</span><span class="sxs-lookup"><span data-stu-id="a48c1-121">The `AccessLevel` on the `Get` or `Set` procedure can be any level that is more restrictive than the access level specified for the property itself.</span></span> <span data-ttu-id="a48c1-122">Pour plus d’informations, consultez [Property, instruction](../../../../visual-basic/language-reference/statements/property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a48c1-122">For more information, see [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md).</span></span>

### <a name="data-type"></a><span data-ttu-id="a48c1-123">Type de données</span><span class="sxs-lookup"><span data-stu-id="a48c1-123">Data Type</span></span>

<span data-ttu-id="a48c1-124">Le type de données et le niveau d’accès principal d’une propriété sont définis dans l’instruction `Property`, pas dans les procédures de propriété.</span><span class="sxs-lookup"><span data-stu-id="a48c1-124">A property's data type and principal access level are defined in the `Property` statement, not in the property procedures.</span></span> <span data-ttu-id="a48c1-125">Une propriété ne peut avoir qu’un seul type de données.</span><span class="sxs-lookup"><span data-stu-id="a48c1-125">A property can have only one data type.</span></span> <span data-ttu-id="a48c1-126">Par exemple, vous ne pouvez pas définir une propriété pour stocker une valeur de `Decimal`, mais récupérer une valeur de `Double`.</span><span class="sxs-lookup"><span data-stu-id="a48c1-126">For example, you cannot define a property to store a `Decimal` value but retrieve a `Double` value.</span></span>

### <a name="access-level"></a><span data-ttu-id="a48c1-127">Niveau d’accès</span><span class="sxs-lookup"><span data-stu-id="a48c1-127">Access Level</span></span>

<span data-ttu-id="a48c1-128">Toutefois, vous pouvez définir un niveau d’accès principal pour une propriété et restreindre davantage le niveau d’accès dans l’une de ses procédures de propriété.</span><span class="sxs-lookup"><span data-stu-id="a48c1-128">However, you can define a principal access level for a property and further restrict the access level in one of its property procedures.</span></span> <span data-ttu-id="a48c1-129">Par exemple, vous pouvez définir une propriété `Public`, puis définir une procédure `Private Set`.</span><span class="sxs-lookup"><span data-stu-id="a48c1-129">For example, you can define a `Public` property and then define a `Private Set` procedure.</span></span> <span data-ttu-id="a48c1-130">La procédure `Get` reste `Public`.</span><span class="sxs-lookup"><span data-stu-id="a48c1-130">The `Get` procedure remains `Public`.</span></span> <span data-ttu-id="a48c1-131">Vous pouvez modifier le niveau d’accès dans une seule des procédures d’une propriété, et vous pouvez le rendre plus restrictif que le niveau d’accès du principal.</span><span class="sxs-lookup"><span data-stu-id="a48c1-131">You can change the access level in only one of a property's procedures, and you can only make it more restrictive than the principal access level.</span></span> <span data-ttu-id="a48c1-132">Pour plus d’informations, consultez [Comment : déclarer une propriété avec des niveaux d’accès mixtes](how-to-declare-a-property-with-mixed-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="a48c1-132">For more information, see [How to: Declare a Property with Mixed Access Levels](how-to-declare-a-property-with-mixed-access-levels.md).</span></span>

## <a name="parameter-declaration"></a><span data-ttu-id="a48c1-133">Déclaration de paramètre</span><span class="sxs-lookup"><span data-stu-id="a48c1-133">Parameter declaration</span></span>

<span data-ttu-id="a48c1-134">Vous déclarez chaque paramètre de la même façon que pour les [procédures Sub](sub-procedures.md), à ceci près que le mécanisme de passage doit être `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="a48c1-134">You declare each parameter the same way you do for [Sub Procedures](sub-procedures.md), except that the passing mechanism must be `ByVal`.</span></span>

<span data-ttu-id="a48c1-135">La syntaxe de chaque paramètre dans la liste de paramètres est la suivante :</span><span class="sxs-lookup"><span data-stu-id="a48c1-135">The syntax for each parameter in the parameter list is as follows:</span></span>

```vb
[Optional] ByVal [ParamArray] parametername As datatype
```

<span data-ttu-id="a48c1-136">Si le paramètre est facultatif, vous devez également fournir une valeur par défaut dans le cadre de sa déclaration.</span><span class="sxs-lookup"><span data-stu-id="a48c1-136">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="a48c1-137">La syntaxe permettant de spécifier une valeur par défaut est la suivante :</span><span class="sxs-lookup"><span data-stu-id="a48c1-137">The syntax for specifying a default value is as follows:</span></span>

```vb
Optional ByVal parametername As datatype = defaultvalue
```

## <a name="property-value"></a><span data-ttu-id="a48c1-138">Valeur de la propriété</span><span class="sxs-lookup"><span data-stu-id="a48c1-138">Property value</span></span>

<span data-ttu-id="a48c1-139">Dans une procédure `Get`, la valeur de retour est fournie à l’expression appelante comme valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="a48c1-139">In a `Get` procedure, the return value is supplied to the calling expression as the value of the property.</span></span>

<span data-ttu-id="a48c1-140">Dans une procédure `Set`, la nouvelle valeur de propriété est passée au paramètre de l’instruction `Set`.</span><span class="sxs-lookup"><span data-stu-id="a48c1-140">In a `Set` procedure, the new property value is passed to the parameter of the `Set` statement.</span></span> <span data-ttu-id="a48c1-141">Si vous déclarez explicitement un paramètre, vous devez le déclarer avec le même type de données que la propriété.</span><span class="sxs-lookup"><span data-stu-id="a48c1-141">If you explicitly declare a parameter, you must declare it with the same data type as the property.</span></span> <span data-ttu-id="a48c1-142">Si vous ne déclarez pas de paramètre, le compilateur utilise le paramètre implicite `Value` pour représenter la nouvelle valeur à assigner à la propriété.</span><span class="sxs-lookup"><span data-stu-id="a48c1-142">If you do not declare a parameter, the compiler uses the implicit parameter `Value` to represent the new value to be assigned to the property.</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="a48c1-143">Syntaxe d’appel</span><span class="sxs-lookup"><span data-stu-id="a48c1-143">Calling syntax</span></span>

<span data-ttu-id="a48c1-144">Vous appelez une procédure de propriété implicitement en faisant référence à la propriété.</span><span class="sxs-lookup"><span data-stu-id="a48c1-144">You invoke a property procedure implicitly by making reference to the property.</span></span> <span data-ttu-id="a48c1-145">Vous utilisez le nom de la propriété de la même façon que vous utilisez le nom d’une variable, mais vous devez fournir des valeurs pour tous les arguments qui ne sont pas facultatifs, et vous devez placer la liste d’arguments entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="a48c1-145">You use the name of the property the same way you would use the name of a variable, except that you must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="a48c1-146">Si aucun argument n’est fourni, vous pouvez éventuellement omettre les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="a48c1-146">If no arguments are supplied, you can optionally omit the parentheses.</span></span>

<span data-ttu-id="a48c1-147">La syntaxe d’un appel implicite à une procédure `Set` se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="a48c1-147">The syntax for an implicit call to a `Set` procedure is as follows:</span></span>

```vb
propertyname[(argumentlist)] = expression
```

<span data-ttu-id="a48c1-148">La syntaxe d’un appel implicite à une procédure `Get` se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="a48c1-148">The syntax for an implicit call to a `Get` procedure is as follows:</span></span>

```vb
lvalue = propertyname[(argumentlist)]
Do While (propertyname[(argumentlist)] > expression)
```

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="a48c1-149">Illustration de la déclaration et de l’appel</span><span class="sxs-lookup"><span data-stu-id="a48c1-149">Illustration of declaration and call</span></span>

<span data-ttu-id="a48c1-150">La propriété suivante stocke un nom complet sous la forme de deux noms constitutifs, le prénom et le nom.</span><span class="sxs-lookup"><span data-stu-id="a48c1-150">The following property stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="a48c1-151">Lorsque le code appelant lit `fullName`, la procédure `Get` combine les deux noms constitutifs et retourne le nom complet.</span><span class="sxs-lookup"><span data-stu-id="a48c1-151">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="a48c1-152">Lorsque le code appelant assigne un nouveau nom complet, la procédure `Set` tente de la décomposer en deux noms constitutifs.</span><span class="sxs-lookup"><span data-stu-id="a48c1-152">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="a48c1-153">S’il ne trouve pas d’espace, il le stocke comme premier nom.</span><span class="sxs-lookup"><span data-stu-id="a48c1-153">If it does not find a space, it stores it all as the first name.</span></span>

[!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]

<span data-ttu-id="a48c1-154">L’exemple suivant montre des appels classiques aux procédures de propriété de `fullName`:</span><span class="sxs-lookup"><span data-stu-id="a48c1-154">The following example shows typical calls to the property procedures of `fullName`:</span></span>

[!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]

## <a name="see-also"></a><span data-ttu-id="a48c1-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a48c1-155">See also</span></span>

- [<span data-ttu-id="a48c1-156">Procédures</span><span class="sxs-lookup"><span data-stu-id="a48c1-156">Procedures</span></span>](index.md)
- [<span data-ttu-id="a48c1-157">Procédures Function</span><span class="sxs-lookup"><span data-stu-id="a48c1-157">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="a48c1-158">Procédures d’opérateur</span><span class="sxs-lookup"><span data-stu-id="a48c1-158">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="a48c1-159">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="a48c1-159">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="a48c1-160">Différences entre les propriétés et les variables dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a48c1-160">Differences Between Properties and Variables in Visual Basic</span></span>](differences-between-properties-and-variables.md)
- [<span data-ttu-id="a48c1-161">Guide pratique : créer une propriété</span><span class="sxs-lookup"><span data-stu-id="a48c1-161">How to: Create a Property</span></span>](how-to-create-a-property.md)
- [<span data-ttu-id="a48c1-162">Guide pratique : appeler une procédure de propriété</span><span class="sxs-lookup"><span data-stu-id="a48c1-162">How to: Call a Property Procedure</span></span>](how-to-call-a-property-procedure.md)
- [<span data-ttu-id="a48c1-163">Comment : déclarer et appeler une propriété par défaut dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a48c1-163">How to: Declare and Call a Default Property in Visual Basic</span></span>](how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="a48c1-164">Guide pratique : placer une valeur dans une propriété</span><span class="sxs-lookup"><span data-stu-id="a48c1-164">How to: Put a Value in a Property</span></span>](how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="a48c1-165">Guide pratique : obtenir une valeur d’une propriété</span><span class="sxs-lookup"><span data-stu-id="a48c1-165">How to: Get a Value from a Property</span></span>](how-to-get-a-value-from-a-property.md)
