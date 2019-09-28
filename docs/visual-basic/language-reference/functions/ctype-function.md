---
title: Fonction CType (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
ms.openlocfilehash: 4a0391b0a5d76f36803b433369d4832c02b05e09
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592097"
---
# <a name="ctype-function-visual-basic"></a><span data-ttu-id="b6513-102">Fonction CType (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6513-102">CType Function (Visual Basic)</span></span>

<span data-ttu-id="b6513-103">Retourne le résultat de la conversion explicite d’une expression en un type de données, un objet, une structure, une classe ou une interface spécifiés.</span><span class="sxs-lookup"><span data-stu-id="b6513-103">Returns the result of explicitly converting an expression to a specified data type, object, structure, class, or interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="b6513-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6513-104">Syntax</span></span>

```vb
CType(expression, typename)
```

## <a name="parts"></a><span data-ttu-id="b6513-105">Composants</span><span class="sxs-lookup"><span data-stu-id="b6513-105">Parts</span></span>

<span data-ttu-id="b6513-106">`expression` toute expression valide.</span><span class="sxs-lookup"><span data-stu-id="b6513-106">`expression` Any valid expression.</span></span> <span data-ttu-id="b6513-107">Si la valeur de `expression` est en dehors de la plage autorisée par `typename`, Visual Basic lève une exception.</span><span class="sxs-lookup"><span data-stu-id="b6513-107">If the value of `expression` is outside the range allowed by `typename`, Visual Basic throws an exception.</span></span>

<span data-ttu-id="b6513-108">`typename` toute expression légale dans une clause `As` dans une instruction `Dim`, autrement dit, le nom d’un type de données, d’un objet, d’une structure, d’une classe ou d’une interface.</span><span class="sxs-lookup"><span data-stu-id="b6513-108">`typename` Any expression that is legal within an `As` clause in a `Dim` statement, that is, the name of any data type, object, structure, class, or interface.</span></span>

## <a name="remarks"></a><span data-ttu-id="b6513-109">Notes</span><span class="sxs-lookup"><span data-stu-id="b6513-109">Remarks</span></span>

> [!TIP]
> <span data-ttu-id="b6513-110">Vous pouvez également utiliser les fonctions suivantes pour effectuer une conversion de type :</span><span class="sxs-lookup"><span data-stu-id="b6513-110">You can also use the following functions to perform a type conversion:</span></span>
>
> - <span data-ttu-id="b6513-111">Les fonctions de conversion de type, telles que `CByte`, `CDbl` et `CInt` qui effectuent une conversion vers un type de données spécifique.</span><span class="sxs-lookup"><span data-stu-id="b6513-111">Type conversion functions such as `CByte`, `CDbl`, and `CInt` that perform a conversion to a specific data type.</span></span> <span data-ttu-id="b6513-112">Pour plus d’informations, consultez [fonctions de conversion de type](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="b6513-112">For more information, see [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>
> - <span data-ttu-id="b6513-113">Opérateur [DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) ou [opérateur TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="b6513-113">[DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span> <span data-ttu-id="b6513-114">Ces opérateurs requièrent qu’un type hérite de ou implémente l’autre type.</span><span class="sxs-lookup"><span data-stu-id="b6513-114">These operators require that one type inherit from or implement the other type.</span></span> <span data-ttu-id="b6513-115">Ils peuvent fournir des performances légèrement meilleures que `CType` lors de la conversion vers et à partir du type de données `Object`.</span><span class="sxs-lookup"><span data-stu-id="b6513-115">They can provide somewhat better performance than `CType` when converting to and from the `Object` data type.</span></span>

<span data-ttu-id="b6513-116">`CType` est compilé en ligne, ce qui signifie que le code de conversion fait partie du code qui évalue l’expression.</span><span class="sxs-lookup"><span data-stu-id="b6513-116">`CType` is compiled inline, which means that the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="b6513-117">Dans certains cas, le code s’exécute plus rapidement, car aucune procédure n’est appelée pour effectuer la conversion.</span><span class="sxs-lookup"><span data-stu-id="b6513-117">In some cases, the code runs faster because no procedures are called to perform the conversion.</span></span>

<span data-ttu-id="b6513-118">Si aucune conversion n’est définie de `expression` à `typename` (par exemple, de `Integer` à `Date`), Visual Basic affiche un message d’erreur au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="b6513-118">If no conversion is defined from `expression` to `typename` (for example, from `Integer` to `Date`), Visual Basic displays a compile-time error message.</span></span>

<span data-ttu-id="b6513-119">Si une conversion échoue au moment de l’exécution, l’exception appropriée est levée.</span><span class="sxs-lookup"><span data-stu-id="b6513-119">If a conversion fails at run time, the appropriate exception is thrown.</span></span> <span data-ttu-id="b6513-120">En cas d’échec d’une conversion restrictive, un <xref:System.OverflowException> est le résultat le plus courant.</span><span class="sxs-lookup"><span data-stu-id="b6513-120">If a narrowing conversion fails, an <xref:System.OverflowException> is the most common result.</span></span> <span data-ttu-id="b6513-121">Si la conversion n’est pas définie, un <xref:System.InvalidCastException> dans est levé.</span><span class="sxs-lookup"><span data-stu-id="b6513-121">If the conversion is undefined, an <xref:System.InvalidCastException> in thrown.</span></span> <span data-ttu-id="b6513-122">Par exemple, cela peut se produire si `expression` est de type `Object` et que son type au moment de l’exécution n’est pas converti en `typename`.</span><span class="sxs-lookup"><span data-stu-id="b6513-122">For example, this can happen  if `expression` is of type `Object` and its run-time type has no conversion to `typename`.</span></span>

<span data-ttu-id="b6513-123">Si le type de données de `expression` ou `typename` est une classe ou une structure que vous avez définie, vous pouvez définir `CType` sur cette classe ou structure comme opérateur de conversion.</span><span class="sxs-lookup"><span data-stu-id="b6513-123">If the data type of `expression` or `typename` is a class or structure you've defined, you can define `CType` on that class or structure as a conversion operator.</span></span> <span data-ttu-id="b6513-124">Cela rend `CType` agir comme *opérateur surchargé*.</span><span class="sxs-lookup"><span data-stu-id="b6513-124">This makes `CType` act as an *overloaded operator*.</span></span> <span data-ttu-id="b6513-125">Si vous procédez ainsi, vous pouvez contrôler le comportement des conversions vers et à partir de votre classe ou structure, y compris les exceptions qui peuvent être levées.</span><span class="sxs-lookup"><span data-stu-id="b6513-125">If you do this, you can control the behavior of conversions to and from your class or structure, including the exceptions that can be thrown.</span></span>

## <a name="overloading"></a><span data-ttu-id="b6513-126">Surcharge</span><span class="sxs-lookup"><span data-stu-id="b6513-126">Overloading</span></span>

<span data-ttu-id="b6513-127">L’opérateur `CType` peut également être surchargé sur une classe ou une structure définie à l’extérieur de votre code.</span><span class="sxs-lookup"><span data-stu-id="b6513-127">The `CType` operator can also be overloaded on a class or structure defined outside your code.</span></span> <span data-ttu-id="b6513-128">Si votre code convertit vers ou à partir de ce type de classe ou de structure, assurez-vous de bien comprendre le comportement de son opérateur `CType`.</span><span class="sxs-lookup"><span data-stu-id="b6513-128">If your code converts to or from such a class or structure, be sure you understand the behavior of its `CType` operator.</span></span> <span data-ttu-id="b6513-129">Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b6513-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="converting-dynamic-objects"></a><span data-ttu-id="b6513-130">Conversion d’objets dynamiques</span><span class="sxs-lookup"><span data-stu-id="b6513-130">Converting Dynamic Objects</span></span>

<span data-ttu-id="b6513-131">Les conversions de type des objets dynamiques sont effectuées par les conversions dynamiques définies par l’utilisateur qui utilisent les méthodes <xref:System.Dynamic.DynamicObject.TryConvert%2A> ou <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A>.</span><span class="sxs-lookup"><span data-stu-id="b6513-131">Type conversions of dynamic objects are performed by user-defined dynamic conversions that use the <xref:System.Dynamic.DynamicObject.TryConvert%2A> or <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> methods.</span></span> <span data-ttu-id="b6513-132">Si vous utilisez des objets dynamiques, utilisez la méthode <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> pour convertir l’objet dynamique.</span><span class="sxs-lookup"><span data-stu-id="b6513-132">If you're working with dynamic objects, use the <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> method to convert the dynamic object.</span></span>

## <a name="example"></a><span data-ttu-id="b6513-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="b6513-133">Example</span></span>

<span data-ttu-id="b6513-134">L’exemple suivant utilise la fonction `CType` pour convertir une expression en type de données `Single`.</span><span class="sxs-lookup"><span data-stu-id="b6513-134">The following example uses the `CType` function to convert an expression to the `Single` data type.</span></span>

[!code-vb[VbVbalrFunctions#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#24)]

<span data-ttu-id="b6513-135">Pour obtenir des exemples supplémentaires, consultez [conversions implicites et explicites](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="b6513-135">For additional examples, see [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b6513-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6513-136">See also</span></span>

- <xref:System.OverflowException>
- <xref:System.InvalidCastException>
- [<span data-ttu-id="b6513-137">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="b6513-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="b6513-138">Fonctions de conversion</span><span class="sxs-lookup"><span data-stu-id="b6513-138">Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [<span data-ttu-id="b6513-139">Operator (instruction)</span><span class="sxs-lookup"><span data-stu-id="b6513-139">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- <span data-ttu-id="b6513-140">[Guide pratique pour Définir un opérateur de conversion @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="b6513-140">[How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)</span></span>
- [<span data-ttu-id="b6513-141">Conversion de type dans le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b6513-141">Type Conversion in the .NET Framework</span></span>](../../../standard/base-types/type-conversion.md)
