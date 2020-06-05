---
title: CType Function
ms.date: 07/20/2015
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
ms.openlocfilehash: 88d609146648fe1b0c3124b99a65e85293fc0707
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406428"
---
# <a name="ctype-function-visual-basic"></a><span data-ttu-id="733b5-102">Fonction CType (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="733b5-102">CType Function (Visual Basic)</span></span>

<span data-ttu-id="733b5-103">Retourne le résultat de la conversion explicite d’une expression en un type de données, un objet, une structure, une classe ou une interface spécifiés.</span><span class="sxs-lookup"><span data-stu-id="733b5-103">Returns the result of explicitly converting an expression to a specified data type, object, structure, class, or interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="733b5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="733b5-104">Syntax</span></span>

```vb
CType(expression, typename)
```

## <a name="parts"></a><span data-ttu-id="733b5-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="733b5-105">Parts</span></span>

<span data-ttu-id="733b5-106">`expression`Toute expression valide.</span><span class="sxs-lookup"><span data-stu-id="733b5-106">`expression` Any valid expression.</span></span> <span data-ttu-id="733b5-107">Si la valeur de `expression` est en dehors de la plage autorisée par `typename` , Visual Basic lève une exception.</span><span class="sxs-lookup"><span data-stu-id="733b5-107">If the value of `expression` is outside the range allowed by `typename`, Visual Basic throws an exception.</span></span>

<span data-ttu-id="733b5-108">`typename`Toute expression légale dans une `As` clause d’une `Dim` instruction, autrement dit, le nom d’un type de données, d’un objet, d’une structure, d’une classe ou d’une interface.</span><span class="sxs-lookup"><span data-stu-id="733b5-108">`typename` Any expression that is legal within an `As` clause in a `Dim` statement, that is, the name of any data type, object, structure, class, or interface.</span></span>

## <a name="remarks"></a><span data-ttu-id="733b5-109">Notes</span><span class="sxs-lookup"><span data-stu-id="733b5-109">Remarks</span></span>

> [!TIP]
> <span data-ttu-id="733b5-110">Vous pouvez également utiliser les fonctions suivantes pour effectuer une conversion de type :</span><span class="sxs-lookup"><span data-stu-id="733b5-110">You can also use the following functions to perform a type conversion:</span></span>
>
> - <span data-ttu-id="733b5-111">Les fonctions de conversion de type, telles que `CByte` , `CDbl` , et `CInt` qui effectuent une conversion vers un type de données spécifique.</span><span class="sxs-lookup"><span data-stu-id="733b5-111">Type conversion functions such as `CByte`, `CDbl`, and `CInt` that perform a conversion to a specific data type.</span></span> <span data-ttu-id="733b5-112">Pour plus d'informations, consultez [Fonctions de conversion de types de données](type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="733b5-112">For more information, see [Type Conversion Functions](type-conversion-functions.md).</span></span>
> - <span data-ttu-id="733b5-113">Opérateur [DirectCast](../operators/directcast-operator.md) ou [opérateur TryCast](../operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="733b5-113">[DirectCast Operator](../operators/directcast-operator.md) or [TryCast Operator](../operators/trycast-operator.md).</span></span> <span data-ttu-id="733b5-114">Ces opérateurs requièrent qu’un type hérite de ou implémente l’autre type.</span><span class="sxs-lookup"><span data-stu-id="733b5-114">These operators require that one type inherit from or implement the other type.</span></span> <span data-ttu-id="733b5-115">Elles peuvent offrir des performances légèrement supérieures à celles de `CType` la conversion vers et depuis le `Object` type de données.</span><span class="sxs-lookup"><span data-stu-id="733b5-115">They can provide somewhat better performance than `CType` when converting to and from the `Object` data type.</span></span>

<span data-ttu-id="733b5-116">`CType`est compilé en ligne, ce qui signifie que le code de conversion fait partie du code qui évalue l’expression.</span><span class="sxs-lookup"><span data-stu-id="733b5-116">`CType` is compiled inline, which means that the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="733b5-117">Dans certains cas, le code s’exécute plus rapidement, car aucune procédure n’est appelée pour effectuer la conversion.</span><span class="sxs-lookup"><span data-stu-id="733b5-117">In some cases, the code runs faster because no procedures are called to perform the conversion.</span></span>

<span data-ttu-id="733b5-118">Si aucune conversion n’est définie à partir de `expression` à `typename` (par exemple, de `Integer` à `Date` ), Visual Basic affiche un message d’erreur au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="733b5-118">If no conversion is defined from `expression` to `typename` (for example, from `Integer` to `Date`), Visual Basic displays a compile-time error message.</span></span>

<span data-ttu-id="733b5-119">Si une conversion échoue au moment de l’exécution, l’exception appropriée est levée.</span><span class="sxs-lookup"><span data-stu-id="733b5-119">If a conversion fails at run time, the appropriate exception is thrown.</span></span> <span data-ttu-id="733b5-120">Si une conversion restrictive échoue, un <xref:System.OverflowException> est le résultat le plus courant.</span><span class="sxs-lookup"><span data-stu-id="733b5-120">If a narrowing conversion fails, an <xref:System.OverflowException> is the most common result.</span></span> <span data-ttu-id="733b5-121">Si la conversion n’est pas définie, une <xref:System.InvalidCastException> exception est levée.</span><span class="sxs-lookup"><span data-stu-id="733b5-121">If the conversion is undefined, an <xref:System.InvalidCastException> in thrown.</span></span> <span data-ttu-id="733b5-122">Par exemple, cela peut se produire si `expression` est de type `Object` et que son type au moment de l’exécution n’est pas converti en `typename` .</span><span class="sxs-lookup"><span data-stu-id="733b5-122">For example, this can happen  if `expression` is of type `Object` and its run-time type has no conversion to `typename`.</span></span>

<span data-ttu-id="733b5-123">Si le type de données de `expression` ou `typename` est une classe ou une structure que vous avez définie, vous pouvez définir `CType` sur cette classe ou structure comme opérateur de conversion.</span><span class="sxs-lookup"><span data-stu-id="733b5-123">If the data type of `expression` or `typename` is a class or structure you've defined, you can define `CType` on that class or structure as a conversion operator.</span></span> <span data-ttu-id="733b5-124">Cela fait `CType` agir en tant qu' *opérateur surchargé*.</span><span class="sxs-lookup"><span data-stu-id="733b5-124">This makes `CType` act as an *overloaded operator*.</span></span> <span data-ttu-id="733b5-125">Si vous procédez ainsi, vous pouvez contrôler le comportement des conversions vers et à partir de votre classe ou structure, y compris les exceptions qui peuvent être levées.</span><span class="sxs-lookup"><span data-stu-id="733b5-125">If you do this, you can control the behavior of conversions to and from your class or structure, including the exceptions that can be thrown.</span></span>

## <a name="overloading"></a><span data-ttu-id="733b5-126">Surcharge</span><span class="sxs-lookup"><span data-stu-id="733b5-126">Overloading</span></span>

<span data-ttu-id="733b5-127">L' `CType` opérateur peut également être surchargé sur une classe ou une structure définie à l’extérieur de votre code.</span><span class="sxs-lookup"><span data-stu-id="733b5-127">The `CType` operator can also be overloaded on a class or structure defined outside your code.</span></span> <span data-ttu-id="733b5-128">Si votre code convertit vers ou à partir de ce type de classe ou de structure, assurez-vous de bien comprendre le comportement de son `CType` opérateur.</span><span class="sxs-lookup"><span data-stu-id="733b5-128">If your code converts to or from such a class or structure, be sure you understand the behavior of its `CType` operator.</span></span> <span data-ttu-id="733b5-129">Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="733b5-129">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="converting-dynamic-objects"></a><span data-ttu-id="733b5-130">Conversion d’objets dynamiques</span><span class="sxs-lookup"><span data-stu-id="733b5-130">Converting Dynamic Objects</span></span>

<span data-ttu-id="733b5-131">Les conversions de type des objets dynamiques sont effectuées par les conversions dynamiques définies par l’utilisateur qui utilisent les <xref:System.Dynamic.DynamicObject.TryConvert%2A> <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> méthodes ou.</span><span class="sxs-lookup"><span data-stu-id="733b5-131">Type conversions of dynamic objects are performed by user-defined dynamic conversions that use the <xref:System.Dynamic.DynamicObject.TryConvert%2A> or <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> methods.</span></span> <span data-ttu-id="733b5-132">Si vous utilisez des objets dynamiques, utilisez la <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> méthode pour convertir l’objet dynamique.</span><span class="sxs-lookup"><span data-stu-id="733b5-132">If you're working with dynamic objects, use the <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> method to convert the dynamic object.</span></span>

## <a name="example"></a><span data-ttu-id="733b5-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="733b5-133">Example</span></span>

<span data-ttu-id="733b5-134">L’exemple suivant utilise la `CType` fonction pour convertir une expression en `Single` type de données.</span><span class="sxs-lookup"><span data-stu-id="733b5-134">The following example uses the `CType` function to convert an expression to the `Single` data type.</span></span>

[!code-vb[VbVbalrFunctions#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#24)]

<span data-ttu-id="733b5-135">Pour obtenir des exemples supplémentaires, consultez [conversions implicites et explicites](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="733b5-135">For additional examples, see [Implicit and Explicit Conversions](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="733b5-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="733b5-136">See also</span></span>

- <xref:System.OverflowException>
- <xref:System.InvalidCastException>
- [<span data-ttu-id="733b5-137">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="733b5-137">Type Conversion Functions</span></span>](type-conversion-functions.md)
- [<span data-ttu-id="733b5-138">Fonctions de conversion</span><span class="sxs-lookup"><span data-stu-id="733b5-138">Conversion Functions</span></span>](conversion-functions.md)
- [<span data-ttu-id="733b5-139">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="733b5-139">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="733b5-140">Guide pratique : définir un opérateur de conversion</span><span class="sxs-lookup"><span data-stu-id="733b5-140">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="733b5-141">Conversion de type dans le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="733b5-141">Type Conversion in the .NET Framework</span></span>](../../../standard/base-types/type-conversion.md)
