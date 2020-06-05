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
ms.openlocfilehash: 2858dafd2531bd846ad89672348d103f385c4511
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393829"
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a>Conversions implicites et explicites (Visual Basic)

Une *conversion implicite* ne requiert pas de syntaxe spéciale dans le code source. Dans l’exemple suivant, Visual Basic convertit implicitement la valeur de `k` en une valeur à virgule flottante simple précision avant de l’assigner à `q` .

```vb
Dim k As Integer
Dim q As Double
' Integer widens to Double, so you can do this with Option Strict On.
k = 432
q = k
```

Une *conversion explicite* utilise un mot clé de conversion de type. Visual Basic fournit plusieurs mots clés de ce type, qui forcent une expression entre parenthèses au type de données souhaité. Ces mots clés agissent comme des fonctions, mais le compilateur génère le code en ligne, de sorte que l’exécution est légèrement plus rapide qu’avec un appel de fonction.

Dans l’extension suivante de l’exemple précédent, le `CInt` mot clé convertit la valeur de `q` en un entier avant de l’assigner à `k` .

```vb
' q had been assigned the value 432 from k.
q = Math.Sqrt(q)
k = CInt(q)
' k now has the value 21 (rounded square root of 432).
```

## <a name="conversion-keywords"></a>Mots clés de conversion

Le tableau suivant présente les mots clés de conversion disponibles.

|Mot clé de conversion de type|Convertit une expression en type de données|Types de données autorisés de l’expression à convertir|
|---|---|---|
|`CBool`|[Booléen (type de données)](../../../language-reference/data-types/boolean-data-type.md)|Tout type numérique (y compris les `Byte` `SByte` types énumérés, et), `String` ,`Object`|
|`CByte`|[Octet (type de données)](../../../language-reference/data-types/byte-data-type.md)|Tout type numérique (y compris les `SByte` types énumérés), `Boolean` , `String` ,`Object`|
|`CChar`|[Caractères (type de données)](../../../language-reference/data-types/char-data-type.md)|`String`, `Object`|
|`CDate`|[Date (type de données)](../../../language-reference/data-types/date-data-type.md)|`String`, `Object`|
|`CDbl`|[Double (type de données)](../../../language-reference/data-types/double-data-type.md)|Tout type numérique (y compris les `Byte` `SByte` types énumérés, et), `Boolean` , `String` ,`Object`|
|`CDec`|[Décimal (type de données)](../../../language-reference/data-types/decimal-data-type.md)|Tout type numérique (y compris les `Byte` `SByte` types énumérés, et), `Boolean` , `String` ,`Object`|
|`CInt`|[Entier (type de données)](../../../language-reference/data-types/integer-data-type.md)|Tout type numérique (y compris les `Byte` `SByte` types énumérés, et), `Boolean` , `String` ,`Object`|
|`CLng`|[Long (type de données)](../../../language-reference/data-types/long-data-type.md)|Tout type numérique (y compris les `Byte` `SByte` types énumérés, et), `Boolean` , `String` ,`Object`|
|`CObj`|[Object Data Type](../../../language-reference/data-types/object-data-type.md)|Tout type|
|`CSByte`|[SByte (type de données)](../../../language-reference/data-types/sbyte-data-type.md)|Tout type numérique (y compris les `Byte` types énumérés), `Boolean` , `String` ,`Object`|
|`CShort`|[Court (type de données)](../../../language-reference/data-types/short-data-type.md)|Tout type numérique (y compris les `Byte` `SByte` types énumérés, et), `Boolean` , `String` ,`Object`|
|`CSng`|[Single (type de données)](../../../language-reference/data-types/single-data-type.md)|Tout type numérique (y compris les `Byte` `SByte` types énumérés, et), `Boolean` , `String` ,`Object`|
|`CStr`|[String, type de données](../../../language-reference/data-types/string-data-type.md)|Tout type numérique (y compris les `Byte` `SByte` types énumérés,, et), `Boolean` ,, `Char` `Char` Array, `Date` ,`Object`|
|`CType`|Type spécifié à la suite de la virgule ( `,` )|Lors de la conversion en un *type de données élémentaire* (y compris un tableau d’un type élémentaire), les mêmes types que ceux autorisés pour le mot clé de conversion correspondant<br /><br /> Lors de la conversion en un *type de données composite*, les interfaces qu’il implémente et les classes dont il hérite<br /><br /> Lors de la conversion vers une classe ou une structure sur laquelle vous avez surchargé `CType` , cette classe ou structure|
|`CUInt`|[UInteger (type de données)](../../../language-reference/data-types/uinteger-data-type.md)|Tout type numérique (y compris les `Byte` `SByte` types énumérés, et), `Boolean` , `String` ,`Object`|
|`CULng`|[ULong (type de données)](../../../language-reference/data-types/ulong-data-type.md)|Tout type numérique (y compris les `Byte` `SByte` types énumérés, et), `Boolean` , `String` ,`Object`|
|`CUShort`|[UShort (type de données)](../../../language-reference/data-types/ushort-data-type.md)|Tout type numérique (y compris les `Byte` `SByte` types énumérés, et), `Boolean` , `String` ,`Object`|

## <a name="the-ctype-function"></a>Fonction CType

La [fonction CType](../../../language-reference/functions/ctype-function.md) opère sur deux arguments. Le premier est l’expression à convertir, tandis que le second est le type de données ou la classe d’objet de destination. Notez que le premier argument doit être une expression et non un type.

`CType`est une *fonction inline*, ce qui signifie que le code compilé effectue la conversion, souvent sans générer un appel de fonction. Les performances en sont alors améliorées.

Pour une comparaison de `CType` avec les autres mots clés de conversion de type, consultez [opérateur DirectCast](../../../language-reference/operators/directcast-operator.md) et [opérateur TryCast](../../../language-reference/operators/trycast-operator.md).

### <a name="elementary-types"></a>Types élémentaires

L'exemple suivant montre l'utilisation de `CType`.

```vb
k = CType(q, Integer)
' The following statement coerces w to the specific object class Label.
f = CType(w, Label)
```

### <a name="composite-types"></a>Types composites

Vous pouvez utiliser `CType` pour convertir des valeurs en types de données composites et en types élémentaires. Vous pouvez également l’utiliser pour forcer une classe d’objet vers le type de l’une de ses interfaces, comme dans l’exemple suivant.

```vb
' Assume class cZone implements interface iZone.
Dim h As Object
' The first argument to CType must be an expression, not a type.
Dim cZ As cZone
' The following statement coerces a cZone object to its interface iZone.
h = CType(cZ, iZone)
```

### <a name="array-types"></a>Types tableau

`CType`peut également convertir des types de données tableau, comme dans l’exemple suivant.

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

Pour plus d’informations et pour obtenir un exemple, consultez [conversions de tableau](array-conversions.md).

### <a name="types-defining-ctype"></a>Types définissant CType

Vous pouvez définir `CType` sur une classe ou une structure que vous avez définie. Cela vous permet de convertir des valeurs vers et à partir du type de votre classe ou structure. Pour plus d’informations et pour obtenir un exemple, consultez [Comment : définir un opérateur de conversion](../procedures/how-to-define-a-conversion-operator.md).

> [!NOTE]
> Les valeurs utilisées avec un mot clé de conversion doivent être valides pour le type de données de destination, sinon une erreur se produit. Par exemple, si vous tentez de convertir un `Long` en `Integer` , la valeur de `Long` doit être comprise dans la plage valide pour le `Integer` type de données.

> [!CAUTION]
> `CType`La spécification de la conversion d’un type de classe en un autre échoue au moment de l’exécution si le type source ne dérive pas du type de destination. Un tel échec lève une <xref:System.InvalidCastException> exception.

Toutefois, si l’un des types est une structure ou une classe que vous avez définie, et si vous avez défini `CType` sur cette structure ou cette classe, une conversion peut être effectuée si elle répond aux spécifications de votre `CType` . Consultez [Comment : définir un opérateur de conversion](../procedures/how-to-define-a-conversion-operator.md).

L’exécution d’une conversion explicite est également appelée *Cast* d’une expression en un type de données ou une classe d’objet donné (e).

## <a name="see-also"></a>Voir aussi

- [Conversions de type en Visual Basic](type-conversions.md)
- [Conversions entre des chaînes et d’autres types](conversions-between-strings-and-other-types.md)
- [Comment : convertir un objet en un autre type dans Visual Basic](how-to-convert-an-object-to-another-type.md)
- [Structures](structures.md)
- [Types de données](../../../language-reference/data-types/index.md)
- [Type Conversion Functions](../../../language-reference/functions/type-conversion-functions.md)
- [Dépannage des types de données](troubleshooting-data-types.md)
