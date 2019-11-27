---
title: Conversions implicites et explicites
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [Visual Basic], type
- variables [Visual Basic], changing data type
- casting
- conversions [Visual Basic], data type
- type conversion [Visual Basic], implicit conversions
- CType function [Visual Basic], conversions
- casting, data types
- data type conversion [Visual Basic], explicit
- type conversion [Visual Basic], explicit conversions
- data types [Visual Basic], casting
- conversions [Visual Basic], implicit
- explicit data type conversions [Visual Basic]
- conversions [Visual Basic]
- changing data types [Visual Basic]
- conversions [Visual Basic], explicit
- data type conversion [Visual Basic], implicit
- implicit data type conversions [Visual Basic]
ms.assetid: 77de1659-af8a-492c-967e-e7ef60ccce66
ms.openlocfilehash: b7215933cec89b7023f08e8996a283b39b3a3c83
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346370"
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a><span data-ttu-id="feb87-102">Conversions implicites et explicites (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="feb87-102">Implicit and Explicit Conversions (Visual Basic)</span></span>

<span data-ttu-id="feb87-103">Une *conversion implicite* ne requiert pas de syntaxe spéciale dans le code source.</span><span class="sxs-lookup"><span data-stu-id="feb87-103">An *implicit conversion* does not require any special syntax in the source code.</span></span> <span data-ttu-id="feb87-104">Dans l’exemple suivant, Visual Basic convertit implicitement la valeur de `k` en une valeur à virgule flottante simple précision avant de l’assigner à `q`.</span><span class="sxs-lookup"><span data-stu-id="feb87-104">In the following example, Visual Basic implicitly converts the value of `k` to a single-precision floating-point value before assigning it to `q`.</span></span>

```vb
Dim k As Integer
Dim q As Double
' Integer widens to Double, so you can do this with Option Strict On.
k = 432
q = k
```

<span data-ttu-id="feb87-105">Une *conversion explicite* utilise un mot clé de conversion de type.</span><span class="sxs-lookup"><span data-stu-id="feb87-105">An *explicit conversion* uses a type conversion keyword.</span></span> <span data-ttu-id="feb87-106">Visual Basic fournit plusieurs mots clés de ce type, qui forcent une expression entre parenthèses au type de données souhaité.</span><span class="sxs-lookup"><span data-stu-id="feb87-106">Visual Basic provides several such keywords, which coerce an expression in parentheses to the desired data type.</span></span> <span data-ttu-id="feb87-107">Ces mots clés agissent comme des fonctions, mais le compilateur génère le code en ligne, de sorte que l’exécution est légèrement plus rapide qu’avec un appel de fonction.</span><span class="sxs-lookup"><span data-stu-id="feb87-107">These keywords act like functions, but the compiler generates the code inline, so execution is slightly faster than with a function call.</span></span>

<span data-ttu-id="feb87-108">Dans l’extension suivante de l’exemple précédent, le mot clé `CInt` convertit la valeur de `q` en un entier avant de l’assigner à `k`.</span><span class="sxs-lookup"><span data-stu-id="feb87-108">In the following extension of the preceding example, the `CInt` keyword converts the value of `q` back to an integer before assigning it to `k`.</span></span>

```vb
' q had been assigned the value 432 from k.
q = Math.Sqrt(q)
k = CInt(q)
' k now has the value 21 (rounded square root of 432).
```

## <a name="conversion-keywords"></a><span data-ttu-id="feb87-109">Mots clés de conversion</span><span class="sxs-lookup"><span data-stu-id="feb87-109">Conversion Keywords</span></span>

<span data-ttu-id="feb87-110">Le tableau suivant présente les mots clés de conversion disponibles.</span><span class="sxs-lookup"><span data-stu-id="feb87-110">The following table shows the available conversion keywords.</span></span>

|<span data-ttu-id="feb87-111">Mot clé de conversion de type</span><span class="sxs-lookup"><span data-stu-id="feb87-111">Type conversion keyword</span></span>|<span data-ttu-id="feb87-112">Convertit une expression en type de données</span><span class="sxs-lookup"><span data-stu-id="feb87-112">Converts an expression to data type</span></span>|<span data-ttu-id="feb87-113">Types de données autorisés de l’expression à convertir</span><span class="sxs-lookup"><span data-stu-id="feb87-113">Allowable data types of expression to be converted</span></span>|
|---|---|---|
|`CBool`|[<span data-ttu-id="feb87-114">Booléen (type de données)</span><span class="sxs-lookup"><span data-stu-id="feb87-114">Boolean Data Type</span></span>](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="feb87-115">Tout type numérique (y compris `Byte`, `SByte`et les types énumérés), `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="feb87-115">Any numeric type (including `Byte`, `SByte`, and enumerated types), `String`, `Object`</span></span>|
|`CByte`|[<span data-ttu-id="feb87-116">Byte (type de données)</span><span class="sxs-lookup"><span data-stu-id="feb87-116">Byte Data Type</span></span>](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="feb87-117">Tout type numérique (y compris `SByte` et les types énumérés), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="feb87-117">Any numeric type (including `SByte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CChar`|[<span data-ttu-id="feb87-118">Char (type de données)</span><span class="sxs-lookup"><span data-stu-id="feb87-118">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="feb87-119">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="feb87-119">`String`, `Object`</span></span>|
|`CDate`|[<span data-ttu-id="feb87-120">Date (type de données)</span><span class="sxs-lookup"><span data-stu-id="feb87-120">Date Data Type</span></span>](../../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="feb87-121">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="feb87-121">`String`, `Object`</span></span>|
|`CDbl`|[<span data-ttu-id="feb87-122">Double (type de données)</span><span class="sxs-lookup"><span data-stu-id="feb87-122">Double Data Type</span></span>](../../../../visual-basic/language-reference/data-types/double-data-type.md)|<span data-ttu-id="feb87-123">Tout type numérique (y compris `Byte`, `SByte`et les types énumérés), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="feb87-123">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CDec`|[<span data-ttu-id="feb87-124">Decimal (type de données)</span><span class="sxs-lookup"><span data-stu-id="feb87-124">Decimal Data Type</span></span>](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="feb87-125">Tout type numérique (y compris `Byte`, `SByte`et les types énumérés), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="feb87-125">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CInt`|[<span data-ttu-id="feb87-126">Integer (type de données)</span><span class="sxs-lookup"><span data-stu-id="feb87-126">Integer Data Type</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="feb87-127">Tout type numérique (y compris `Byte`, `SByte`et les types énumérés), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="feb87-127">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CLng`|[<span data-ttu-id="feb87-128">Long (type de données)</span><span class="sxs-lookup"><span data-stu-id="feb87-128">Long Data Type</span></span>](../../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="feb87-129">Tout type numérique (y compris `Byte`, `SByte`et les types énumérés), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="feb87-129">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CObj`|[<span data-ttu-id="feb87-130">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="feb87-130">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)|<span data-ttu-id="feb87-131">Tout type</span><span class="sxs-lookup"><span data-stu-id="feb87-131">Any type</span></span>|
|`CSByte`|[<span data-ttu-id="feb87-132">SByte (type de données)</span><span class="sxs-lookup"><span data-stu-id="feb87-132">SByte Data Type</span></span>](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="feb87-133">Tout type numérique (y compris `Byte` et les types énumérés), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="feb87-133">Any numeric type (including `Byte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CShort`|[<span data-ttu-id="feb87-134">Short (type de données)</span><span class="sxs-lookup"><span data-stu-id="feb87-134">Short Data Type</span></span>](../../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="feb87-135">Tout type numérique (y compris `Byte`, `SByte`et les types énumérés), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="feb87-135">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CSng`|[<span data-ttu-id="feb87-136">Single (type de données)</span><span class="sxs-lookup"><span data-stu-id="feb87-136">Single Data Type</span></span>](../../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="feb87-137">Tout type numérique (y compris `Byte`, `SByte`et les types énumérés), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="feb87-137">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CStr`|[<span data-ttu-id="feb87-138">String (type de données)</span><span class="sxs-lookup"><span data-stu-id="feb87-138">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)|<span data-ttu-id="feb87-139">Tout type numérique (y compris `Byte`, `SByte`et les types énumérés), `Boolean`, `Char`, `Char` Array, `Date`, `Object`</span><span class="sxs-lookup"><span data-stu-id="feb87-139">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `Char`, `Char` array, `Date`, `Object`</span></span>|
|`CType`|<span data-ttu-id="feb87-140">Type spécifié à la suite de la virgule (`,`)</span><span class="sxs-lookup"><span data-stu-id="feb87-140">Type specified following the comma (`,`)</span></span>|<span data-ttu-id="feb87-141">Lors de la conversion en un *type de données élémentaire* (y compris un tableau d’un type élémentaire), les mêmes types que ceux autorisés pour le mot clé de conversion correspondant</span><span class="sxs-lookup"><span data-stu-id="feb87-141">When converting to an *elementary data type* (including an array of an elementary type), the same types as allowed for the corresponding conversion keyword</span></span><br /><br /> <span data-ttu-id="feb87-142">Lors de la conversion en un *type de données composite*, les interfaces qu’il implémente et les classes dont il hérite</span><span class="sxs-lookup"><span data-stu-id="feb87-142">When converting to a *composite data type*, the interfaces it implements and the classes from which it inherits</span></span><br /><br /> <span data-ttu-id="feb87-143">Lors de la conversion vers une classe ou une structure sur laquelle vous avez surchargé `CType`, cette classe ou structure</span><span class="sxs-lookup"><span data-stu-id="feb87-143">When converting to a class or structure on which you have overloaded `CType`, that class or structure</span></span>|
|`CUInt`|[<span data-ttu-id="feb87-144">UInteger (type de données)</span><span class="sxs-lookup"><span data-stu-id="feb87-144">UInteger Data Type</span></span>](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="feb87-145">Tout type numérique (y compris `Byte`, `SByte`et les types énumérés), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="feb87-145">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CULng`|[<span data-ttu-id="feb87-146">ULong (type de données)</span><span class="sxs-lookup"><span data-stu-id="feb87-146">ULong Data Type</span></span>](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="feb87-147">Tout type numérique (y compris `Byte`, `SByte`et les types énumérés), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="feb87-147">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CUShort`|[<span data-ttu-id="feb87-148">UShort (type de données)</span><span class="sxs-lookup"><span data-stu-id="feb87-148">UShort Data Type</span></span>](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="feb87-149">Tout type numérique (y compris `Byte`, `SByte`et les types énumérés), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="feb87-149">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|

## <a name="the-ctype-function"></a><span data-ttu-id="feb87-150">Fonction CType</span><span class="sxs-lookup"><span data-stu-id="feb87-150">The CType Function</span></span>

<span data-ttu-id="feb87-151">La [fonction CType](../../../../visual-basic/language-reference/functions/ctype-function.md) opère sur deux arguments.</span><span class="sxs-lookup"><span data-stu-id="feb87-151">The [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) operates on two arguments.</span></span> <span data-ttu-id="feb87-152">Le premier est l’expression à convertir, tandis que le second est le type de données ou la classe d’objet de destination.</span><span class="sxs-lookup"><span data-stu-id="feb87-152">The first is the expression to be converted, and the second is the destination data type or object class.</span></span> <span data-ttu-id="feb87-153">Notez que le premier argument doit être une expression et non un type.</span><span class="sxs-lookup"><span data-stu-id="feb87-153">Note that the first argument must be an expression, not a type.</span></span>

<span data-ttu-id="feb87-154">`CType` est une *fonction inline*, ce qui signifie que le code compilé effectue la conversion, souvent sans générer un appel de fonction.</span><span class="sxs-lookup"><span data-stu-id="feb87-154">`CType` is an *inline function*, meaning the compiled code makes the conversion, often without generating a function call.</span></span> <span data-ttu-id="feb87-155">Cela améliore les performances.</span><span class="sxs-lookup"><span data-stu-id="feb87-155">This improves performance.</span></span>

<span data-ttu-id="feb87-156">Pour une comparaison des `CType` avec les autres mots clés de conversion de type, consultez [opérateur DirectCast](../../../../visual-basic/language-reference/operators/directcast-operator.md) et [opérateur TryCast](../../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="feb87-156">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span>

### <a name="elementary-types"></a><span data-ttu-id="feb87-157">Types élémentaires</span><span class="sxs-lookup"><span data-stu-id="feb87-157">Elementary Types</span></span>

<span data-ttu-id="feb87-158">L'exemple suivant montre l'utilisation de `CType`.</span><span class="sxs-lookup"><span data-stu-id="feb87-158">The following example demonstrates the use of `CType`.</span></span>

```vb
k = CType(q, Integer)
' The following statement coerces w to the specific object class Label.
f = CType(w, Label)
```

### <a name="composite-types"></a><span data-ttu-id="feb87-159">Types composites</span><span class="sxs-lookup"><span data-stu-id="feb87-159">Composite Types</span></span>

<span data-ttu-id="feb87-160">Vous pouvez utiliser `CType` pour convertir des valeurs en types de données composites et en types élémentaires.</span><span class="sxs-lookup"><span data-stu-id="feb87-160">You can use `CType` to convert values to composite data types as well as to elementary types.</span></span> <span data-ttu-id="feb87-161">Vous pouvez également l’utiliser pour forcer une classe d’objet vers le type de l’une de ses interfaces, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="feb87-161">You can also use it to coerce an object class to the type of one of its interfaces, as in the following example.</span></span>

```vb
' Assume class cZone implements interface iZone.
Dim h As Object
' The first argument to CType must be an expression, not a type.
Dim cZ As cZone
' The following statement coerces a cZone object to its interface iZone.
h = CType(cZ, iZone)
```

### <a name="array-types"></a><span data-ttu-id="feb87-162">Types tableau</span><span class="sxs-lookup"><span data-stu-id="feb87-162">Array Types</span></span>

<span data-ttu-id="feb87-163">`CType` pouvez également convertir des types de données tableau, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="feb87-163">`CType` can also convert array data types, as in the following example.</span></span>

```vb
Dim v() As classV
Dim obArray() As Object
' Assume some object array has been assigned to obArray.
' Check for run-time type compatibility.
If TypeOf obArray Is classV()
    ' obArray can be converted to classV.
    v = CType(obArray, classV())
End If
```

<span data-ttu-id="feb87-164">Pour plus d’informations et pour obtenir un exemple, consultez [conversions de tableau](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="feb87-164">For more information and an example, see [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md).</span></span>

### <a name="types-defining-ctype"></a><span data-ttu-id="feb87-165">Types définissant CType</span><span class="sxs-lookup"><span data-stu-id="feb87-165">Types Defining CType</span></span>

<span data-ttu-id="feb87-166">Vous pouvez définir des `CType` sur une classe ou une structure que vous avez définie.</span><span class="sxs-lookup"><span data-stu-id="feb87-166">You can define `CType` on a class or structure you have defined.</span></span> <span data-ttu-id="feb87-167">Cela vous permet de convertir des valeurs vers et à partir du type de votre classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="feb87-167">This allows you to convert values to and from the type of your class or structure.</span></span> <span data-ttu-id="feb87-168">Pour plus d’informations et pour obtenir un exemple, consultez [Comment : définir un opérateur de conversion](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="feb87-168">For more information and an example, see [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>

> [!NOTE]
> <span data-ttu-id="feb87-169">Les valeurs utilisées avec un mot clé de conversion doivent être valides pour le type de données de destination, sinon une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="feb87-169">Values used with a conversion keyword must be valid for the destination data type, or an error occurs.</span></span> <span data-ttu-id="feb87-170">Par exemple, si vous tentez de convertir un `Long` en `Integer`, la valeur de la `Long` doit être comprise dans la plage valide pour le type de données `Integer`.</span><span class="sxs-lookup"><span data-stu-id="feb87-170">For example, if you attempt to convert a `Long` to an `Integer`, the value of the `Long` must be within the valid range for the `Integer` data type.</span></span>

> [!CAUTION]
> <span data-ttu-id="feb87-171">La spécification d' `CType` pour convertir d’un type de classe en un autre échoue au moment de l’exécution si le type source ne dérive pas du type de destination.</span><span class="sxs-lookup"><span data-stu-id="feb87-171">Specifying `CType` to convert from one class type to another fails at run time if the source type does not derive from the destination type.</span></span> <span data-ttu-id="feb87-172">Un tel échec lève une exception <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="feb87-172">Such a failure throws an <xref:System.InvalidCastException> exception.</span></span>

<span data-ttu-id="feb87-173">Toutefois, si l’un des types est une structure ou une classe que vous avez définie, et si vous avez défini `CType` sur cette structure ou classe, une conversion peut être effectuée si elle répond aux spécifications de votre `CType`.</span><span class="sxs-lookup"><span data-stu-id="feb87-173">However, if one of the types is a structure or class you have defined, and if you have defined `CType` on that structure or class, a conversion can succeed if it satisfies the requirements of your `CType`.</span></span> <span data-ttu-id="feb87-174">Consultez [Comment : définir un opérateur de conversion](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="feb87-174">See [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>

<span data-ttu-id="feb87-175">L’exécution d’une conversion explicite est également appelée *Cast* d’une expression en un type de données ou une classe d’objet donné (e).</span><span class="sxs-lookup"><span data-stu-id="feb87-175">Performing an explicit conversion is also known as *casting* an expression to a given data type or object class.</span></span>

## <a name="see-also"></a><span data-ttu-id="feb87-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="feb87-176">See also</span></span>

- [<span data-ttu-id="feb87-177">Conversions de type dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="feb87-177">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="feb87-178">Conversion entre des chaînes et d’autres types</span><span class="sxs-lookup"><span data-stu-id="feb87-178">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="feb87-179">Comment : convertir un objet en un autre type dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="feb87-179">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="feb87-180">Structures</span><span class="sxs-lookup"><span data-stu-id="feb87-180">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="feb87-181">Types de données</span><span class="sxs-lookup"><span data-stu-id="feb87-181">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="feb87-182">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="feb87-182">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="feb87-183">Dépannage des types de données</span><span class="sxs-lookup"><span data-stu-id="feb87-183">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
