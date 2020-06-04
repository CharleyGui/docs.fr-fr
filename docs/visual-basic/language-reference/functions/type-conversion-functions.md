---
title: Type Conversion Functions
ms.date: 10/24/2018
f1_keywords:
- vb.CUShort
- vb.csng
- vb.CDate
- CByte
- CSng
- vb.CDec
- CBool
- CStr
- vb.CULng
- CDec
- CVErr
- CDbl
- CShort
- vb.CObj
- vb.CVErr
- CULng
- vb.cdbl
- vb.cbool
- CObj
- CDate
- CLng
- vb.cstr
- vb.cbyte
- vb.clng
- vb.CChar
- CUShort
- vb.CUInt
- vb.cint
- vb.CShort
- CInt
- CUInt
- CChar
helpviewer_keywords:
- CDate function
- CByte function
- Integer data type [Visual Basic], converting
- string conversion [Visual Basic], conversion functions
- fractions
- data types [Visual Basic], converting
- text, converting
- CDec function
- Char data type [Visual Basic], converting
- type conversion [Visual Basic], functions for
- Single data type [Visual Basic], converting
- numbers [Visual Basic], rounding
- rounding numbers [Visual Basic], type conversion
- CUShort function
- Long data type [Visual Basic], converting
- return values [Visual Basic], data types
- single-precision numbers [Visual Basic], converting
- data type conversion [Visual Basic], functions for
- CStr function
- times [Visual Basic], converting
- CSng function
- conversions [Visual Basic], type conversion functions
- CBool function
- CDbl function
- CUInt function
- Currency data type [Visual Basic], conversion functions
- numbers [Visual Basic], converting
- Double data type [Visual Basic], converting
- CLng function
- CSByte function
- double-precision numbers
- Decimal data type [Visual Basic], converting
- Boolean data type [Visual Basic], converting
- integers [Visual Basic], type conversion functions
- dates [Visual Basic], converting
- CULng function
- CInt function
- Date data type [Visual Basic], converting
- Byte data type [Visual Basic], converting
- String data type [Visual Basic], converting
- CChar function
- banker's rounding
- Short data type [Visual Basic], converting
- rounding numbers [Visual Basic], banker's rounding
- type conversion [Visual Basic], Visual Basic vs. .NET Framework
ms.assetid: d9d8d165-f967-44ff-a6cd-598e4740a99e
ms.openlocfilehash: 5c0cfae01da02222d0827e81ec1ed35ce353ead1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415373"
---
# <a name="type-conversion-functions-visual-basic"></a>Fonctions de conversion de types de données (Visual Basic)

Ces fonctions sont compilées Inline, ce qui signifie que le code de conversion fait partie du code qui évalue l’expression. Il arrive parfois qu’il n’y ait pas d’appel à une procédure pour effectuer la conversion, ce qui améliore les performances. Chaque fonction convertit une expression en un type de données spécifique.

## <a name="syntax"></a>Syntaxe

```vb
CBool(expression)
CByte(expression)
CChar(expression)
CDate(expression)
CDbl(expression)
CDec(expression)
CInt(expression)
CLng(expression)
CObj(expression)
CSByte(expression)
CShort(expression)
CSng(expression)
CStr(expression)
CUInt(expression)
CULng(expression)
CUShort(expression)
```

## <a name="part"></a>Élément

`expression`  
Obligatoire. Toute expression du type de données source.

## <a name="return-value-data-type"></a>Type de données de la valeur de retour

Le nom de la fonction détermine le type de données de la valeur qu’il retourne, comme indiqué dans le tableau suivant.

|Nom de la fonction|Type de données de retour|Plage pour l' `expression` argument|
|-------------------|----------------------|-------------------------------------|
|`CBool`|[Booléen (type de données)](../data-types/boolean-data-type.md)|Toute `Char` expression valide ou `String` numérique.|
|`CByte`|[Octet (type de données)](../data-types/byte-data-type.md)|<xref:System.Byte.MinValue?displayProperty=nameWithType>(0) à <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (non signé); les parties fractionnaires sont arrondies.<sup> 1</sup><br/><br/>À partir de Visual Basic 15,8, Visual Basic optimise les performances de la conversion de virgule flottante en octet avec la `CByte` fonction. pour plus d’informations, consultez la section [Notes](#remarks) . Pour obtenir un exemple, consultez la section [exemple CInt](#cint-example) .|
|`CChar`|[Caractères (type de données)](../data-types/char-data-type.md)|Toute `Char` expression ou valide `String` ; seul le premier caractère d’un `String` est converti ; la valeur peut être comprise entre 0 et 65535 (non signé).|
|`CDate`|[Date (type de données)](../data-types/date-data-type.md)|Toute représentation valide d’une date et d’une heure.|
|`CDbl`|[Double (type de données)](../data-types/double-data-type.md)|-1.79769313486231570 e + 308 à-4.94065645841246544 E-324 pour les valeurs négatives ; 4.94065645841246544 e-324 à 1.79769313486231570 E + 308 pour les valeurs positives.|
|`CDec`|[Décimal (type de données)](../data-types/decimal-data-type.md)|+/-79 228 335 pour les nombres à échelle zéro, autrement dit, les nombres sans décimales. Pour les nombres avec 28 décimales, la plage est +/-7,9228162514264337593543950335. Le plus petit nombre non nul possible est 0,0000000000000000000000000001 (+/-1E-28).|
|`CInt`|[Entier (type de données)](../data-types/integer-data-type.md)|<xref:System.Int32.MinValue?displayProperty=nameWithType>(-2 147 483 648) à <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2 147 483 647); les parties fractionnaires sont arrondies.<sup> 1</sup> <br/><br/>À partir de Visual Basic 15,8, Visual Basic optimise les performances de la conversion à virgule flottante en valeur entière avec la `CInt` fonction. consultez la section [Notes](#remarks) pour plus d’informations. Pour obtenir un exemple, consultez la section [exemple CInt](#cint-example) . |
|`CLng`|[Long (type de données)](../data-types/long-data-type.md)|<xref:System.Int64.MinValue?displayProperty=nameWithType>(-9223372036854775808) à <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9 223 372 036 854 775 807); les parties fractionnaires sont arrondies.<sup> 1</sup><br/><br/>À compter de Visual Basic 15,8, Visual Basic optimise les performances de la conversion d’un entier à virgule flottante en 64 bits avec la `CLng` fonction. pour plus d’informations, consultez la section [Notes](#remarks) . Pour obtenir un exemple, consultez la section [exemple CInt](#cint-example) .|
|`CObj`|[Object Data Type](../data-types/object-data-type.md)|Toute expression valide.|
|`CSByte`|[SByte (type de données)](../data-types/sbyte-data-type.md)|<xref:System.SByte.MinValue?displayProperty=nameWithType>(-128) à <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); les parties fractionnaires sont arrondies.<sup> 1</sup><br/><br/>À compter de Visual Basic 15,8, Visual Basic optimise les performances de la conversion de virgule flottante en octet signé avec la `CSByte` fonction. pour plus d’informations, consultez la section [Notes](#remarks) . Pour obtenir un exemple, consultez la section [exemple CInt](#cint-example) .|
|`CShort`|[Court (type de données)](../data-types/short-data-type.md)|<xref:System.Int16.MinValue?displayProperty=nameWithType>(-32 768) à <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32 767); les parties fractionnaires sont arrondies.<sup> 1</sup><br/><br/>À compter de Visual Basic 15,8, Visual Basic optimise les performances de la conversion d’un entier à virgule flottante en 16 bits avec la `CShort` fonction. pour plus d’informations, consultez la section [Notes](#remarks) . Pour obtenir un exemple, consultez la section [exemple CInt](#cint-example) .|
|`CSng`|[Single (type de données)](../data-types/single-data-type.md)|-3.402823 e + 38 à-1.401298 E-45 pour les valeurs négatives ; 1.401298 e-45 à 3.402823 E + 38 pour les valeurs positives.|
|`CStr`|[String, type de données](../data-types/string-data-type.md)|Retourne pour `CStr` dépendre de l' `expression` argument. Consultez [valeurs de retour pour la fonction CStr](return-values-for-the-cstr-function.md).|
|`CUInt`|[UInteger (type de données)](../data-types/uinteger-data-type.md)|<xref:System.UInt32.MinValue?displayProperty=nameWithType>(0) à <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4 294 967 295) (non signé); les parties fractionnaires sont arrondies.<sup> 1</sup><br/><br/>À compter de Visual Basic 15,8, Visual Basic optimise les performances de la conversion d’un entier à virgule flottante en non signée avec la `CUInt` fonction. consultez la section [Notes](#remarks) pour plus d’informations. Pour obtenir un exemple, consultez la section [exemple CInt](#cint-example) .|
|`CULng`|[ULong (type de données)](../data-types/ulong-data-type.md)|<xref:System.UInt64.MinValue?displayProperty=nameWithType>(0) à <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18446744073709551615) (non signé); les parties fractionnaires sont arrondies.<sup> 1</sup><br/><br/>À compter de Visual Basic 15,8, Visual Basic optimise les performances de la conversion à virgule flottante en valeur entière non signée avec la `CULng` fonction. consultez la section [Notes](#remarks) pour plus d’informations. Pour obtenir un exemple, consultez la section [exemple CInt](#cint-example) .|
|`CUShort`|[UShort (type de données)](../data-types/ushort-data-type.md)|<xref:System.UInt16.MinValue?displayProperty=nameWithType>(0) à <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65 535) (non signé); les parties fractionnaires sont arrondies.<sup> 1</sup><br/><br/>À compter de Visual Basic 15,8, Visual Basic optimise les performances de la conversion d’un entier à virgule flottante en 16 bits non signé avec la `CUShort` fonction. pour plus d’informations, consultez la section [Notes](#remarks) . Pour obtenir un exemple, consultez la section [exemple CInt](#cint-example) .|

<sup>1</sup> les parties fractionnaires peuvent être soumises à un type spécial d’arrondi appelé « *arrondi bancaire*». Pour plus d’informations, consultez « Remarques ».

## <a name="remarks"></a>Notes

En règle générale, vous devez utiliser les fonctions de conversion de type Visual Basic de préférence aux méthodes .NET Framework telles que `ToString()` , soit sur la classe, soit <xref:System.Convert> sur une structure ou une classe de type individuelle. Les fonctions Visual Basic sont conçues pour une interaction optimale avec Visual Basic Code, et elles rendent également votre code source plus concis et plus facile à lire. En outre, les méthodes de conversion .NET Framework ne produisent pas toujours les mêmes résultats que les fonctions Visual Basic, par exemple lors de la conversion `Boolean` en `Integer` . Pour plus d’informations, consultez [Dépannage des types de données](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).

À compter de Visual Basic 15,8, les performances de la conversion de virgule flottante en nombres entiers sont optimisées quand vous transmettez la <xref:System.Single> <xref:System.Double> valeur ou retournée par les méthodes suivantes à l’une des fonctions de conversion d’entiers ( `CByte` , `CShort` , `CInt` , `CLng` , `CSByte` , `CUShort` , `CUInt` , `CULng` ) :

- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Single)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Single)?displayProperty=nameWithType>
- <xref:System.Math.Ceiling(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Floor(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Round(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Truncate(System.Double)?displayProperty=nameWithType>

Cette optimisation permet au code qui effectue un grand nombre de conversions entières de s’exécuter jusqu’à deux fois plus vite. L’exemple suivant illustre ces conversions à virgule flottante, à virgule flottante optimisées :

```vb
Dim s As Single = 173.7619
Dim d As Double = s

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174
```

## <a name="behavior"></a>Comportement

- **Contrainte.** En général, vous pouvez utiliser les fonctions de conversion de type de données pour forcer le résultat d’une opération sur un type de données particulier plutôt que sur le type de données par défaut. Par exemple, utilisez `CDec` pour forcer l’arithmétique décimale dans les cas où une simple précision, une double précision ou une opération arithmétique sur les entiers aura normalement lieu.

- **Échec des conversions.** Si le `expression` passé à la fonction est en dehors de la plage du type de données vers lequel il doit être converti, un <xref:System.OverflowException> se produit.

- **Parties fractionnaires.** Quand vous convertissez une valeur non intégrale en type intégral, les fonctions de conversion d’entier ( `CByte` , `CInt` , `CLng` , `CSByte` , `CShort` , `CUInt` , `CULng` et `CUShort` ) suppriment la partie fractionnaire et arrondissent la valeur à l’entier le plus proche.

     Si la partie fractionnaire est exactement 0,5, les fonctions de conversion d’entiers l’arrondissent à l’entier pair le plus proche. Par exemple, 0,5 est arrondi à 0, et 1,5 et 2,5 à 2. C’est ce que l’on appelle parfois *l’arrondi de Banker*, et son objectif est de compenser un biais qui peut s’accumuler lors de l’ajout de nombreux nombres de ce type.

     `CInt`et `CLng` diffèrent des <xref:Microsoft.VisualBasic.Conversion.Int%2A> <xref:Microsoft.VisualBasic.Conversion.Fix%2A> fonctions et, qui tronquent, plutôt que Round, la partie fractionnaire d’un nombre. De plus, `Fix` et `Int` retournent toujours une valeur du même type de données que celui que vous transmettez.

- **Conversions de date/heure.** Utilisez la <xref:Microsoft.VisualBasic.Information.IsDate%2A> fonction pour déterminer si une valeur peut être convertie en date et heure. `CDate`reconnaît des littéraux de date et d’heure, mais pas des valeurs numériques. Pour convertir une valeur Visual Basic 6,0 en `Date` `Date` valeur dans Visual Basic 2005 ou versions ultérieures, vous pouvez utiliser la <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> méthode.

- **Valeurs de date/heure neutres.** Le [type de données date](../data-types/date-data-type.md) contient toujours des informations de date et d’heure. À des fins de conversion de type, Visual Basic considère que 1/1/0001 (1er janvier de l’année 1) comme étant une *valeur neutre* pour la date, et 00:00:00 (minuit) comme valeur neutre pour le moment. Si vous convertissez une `Date` valeur en chaîne, `CStr` n’inclut pas de valeurs neutres dans la chaîne résultante. Par exemple, si vous convertissez `#January 1, 0001 9:30:00#` en chaîne, le résultat est « 9:30:00 AM »; les informations de date sont supprimées. Toutefois, les informations de date sont toujours présentes dans la `Date` valeur d’origine et peuvent être récupérées avec des fonctions telles que <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> Function.

- **Sensibilité de la culture.** Les fonctions de conversion de type impliquant des chaînes effectuent des conversions basées sur les paramètres de culture actuels de l’application. Par exemple, `CDate` reconnaît les formats de date en fonction des paramètres régionaux de votre système. Vous devez fournir le jour, le mois et l’année dans le bon ordre pour vos paramètres régionaux, ou la date peut ne pas être interprétée correctement. Un format de date longue n’est pas reconnu s’il contient une chaîne de jour de la semaine, par exemple « mercredi ».

     Si vous devez convertir vers ou à partir d’une représentation sous forme de chaîne d’une valeur dans un format autre que celui spécifié par vos paramètres régionaux, vous ne pouvez pas utiliser les fonctions de conversion de type Visual Basic. Pour ce faire, utilisez les `ToString(IFormatProvider)` `Parse(String, IFormatProvider)` méthodes et du type de cette valeur. Par exemple, utilisez <xref:System.Double.Parse%2A?displayProperty=nameWithType> lors de la conversion d’une chaîne en `Double` et utilisez lors de la conversion d' <xref:System.Double.ToString%2A?displayProperty=nameWithType> une valeur de type `Double` en chaîne.

## <a name="ctype-function"></a>CType Function

La [fonction CType](ctype-function.md) accepte un deuxième argument, `typename` , et est forcée `expression` à `typename` , où `typename` peut être n’importe quel type de données, structure, classe ou interface pour laquelle il existe une conversion valide.

Pour une comparaison de `CType` avec les autres mots clés de conversion de type, consultez [opérateur DirectCast](../operators/directcast-operator.md) et [opérateur TryCast](../operators/trycast-operator.md).

## <a name="cbool-example"></a>CBool, exemple

L’exemple suivant utilise la `CBool` fonction pour convertir des expressions en `Boolean` valeurs. Si une expression est évaluée à une valeur différente de zéro, `CBool` retourne `True` ; sinon, elle retourne `False` .

[!code-vb[VbVbalrFunctions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#1)]

## <a name="cbyte-example"></a>CByte, exemple

L’exemple suivant utilise la `CByte` fonction pour convertir une expression en `Byte` .

[!code-vb[VbVbalrFunctions#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#2)]

## <a name="cchar-example"></a>Exemple CChar

L’exemple suivant utilise la `CChar` fonction pour convertir le premier caractère d’une `String` expression en un `Char` type.

[!code-vb[VbVbalrFunctions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#3)]

L’argument d’entrée de `CChar` doit être de type de données `Char` ou `String` . Vous ne pouvez pas utiliser `CChar` pour convertir un nombre en caractère, car `CChar` ne peut pas accepter un type de données numérique. L’exemple suivant obtient un nombre qui représente un point de code (code de caractère) et le convertit en caractère correspondant. Elle utilise la <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> fonction pour obtenir la chaîne de chiffres, `CInt` pour convertir la chaîne en type `Integer` et `ChrW` pour convertir le nombre en type `Char` .

[!code-vb[VbVbalrFunctions#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#4)]

## <a name="cdate-example"></a>Exemple CDate

L’exemple suivant utilise la `CDate` fonction pour convertir des chaînes en `Date` valeurs. En général, les dates et heures de codage en dur en tant que chaînes (comme indiqué dans cet exemple) ne sont pas recommandées. Utilisez des littéraux de date et d’heure, tels que #Feb 12, 1969 # et #4:45:23 PM #, à la place.

[!code-vb[VbVbalrFunctions#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#5)]

## <a name="cdbl-example"></a>Exemple de CDbl

[!code-vb[VbVbalrFunctions#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#6)]

## <a name="cdec-example"></a>Exemple CDec

L’exemple suivant utilise la `CDec` fonction pour convertir une valeur numérique en `Decimal` .

[!code-vb[VbVbalrFunctions#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#7)]

## <a name="cint-example"></a>Exemple CInt

L’exemple suivant utilise la `CInt` fonction pour convertir une valeur en `Integer` .

[!code-vb[VbVbalrFunctions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#8)]

## <a name="clng-example"></a>Exemple CLng

L’exemple suivant utilise la `CLng` fonction pour convertir des valeurs en `Long` .

[!code-vb[VbVbalrFunctions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#9)]

## <a name="cobj-example"></a>Exemple CObj

L’exemple suivant utilise la `CObj` fonction pour convertir une valeur numérique en `Object` . La `Object` variable elle-même contient uniquement un pointeur de 4 octets, qui pointe vers la valeur qui lui `Double` est assignée.

[!code-vb[VbVbalrFunctions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#10)]

## <a name="csbyte-example"></a>Exemple CSByte

L’exemple suivant utilise la `CSByte` fonction pour convertir une valeur numérique en `SByte` .

[!code-vb[VbVbalrFunctions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#11)]

## <a name="cshort-example"></a>CShort, exemple

L’exemple suivant utilise la `CShort` fonction pour convertir une valeur numérique en `Short` .

[!code-vb[VbVbalrFunctions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#12)]

## <a name="csng-example"></a>CSng, exemple

L’exemple suivant utilise la `CSng` fonction pour convertir des valeurs en `Single` .

[!code-vb[VbVbalrFunctions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#13)]

## <a name="cstr-example"></a>Exemple CStr

L’exemple suivant utilise la `CStr` fonction pour convertir une valeur numérique en `String` .

[!code-vb[VbVbalrFunctions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#14)]

L’exemple suivant utilise la `CStr` fonction pour convertir des `Date` valeurs en `String` valeurs.

[!code-vb[VbVbalrFunctions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#15)]

`CStr`restitue toujours une `Date` valeur au format abrégé standard pour les paramètres régionaux actuels, par exemple, « 6/15/2003 4:35:47 PM ». Toutefois, `CStr` supprime les *valeurs neutres* de 1/1/0001 pour la date et 00:00:00 pour l’heure.

Pour plus d’informations sur les valeurs retournées par `CStr` , consultez [valeurs de retour pour la fonction CStr](return-values-for-the-cstr-function.md).

## <a name="cuint-example"></a>Exemple CUInt

L’exemple suivant utilise la `CUInt` fonction pour convertir une valeur numérique en `UInteger` .

[!code-vb[VbVbalrFunctions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#16)]

## <a name="culng-example"></a>Exemple CULng

L’exemple suivant utilise la `CULng` fonction pour convertir une valeur numérique en `ULong` .

[!code-vb[VbVbalrFunctions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#17)]

## <a name="cushort-example"></a>Exemple CUShort

L’exemple suivant utilise la `CUShort` fonction pour convertir une valeur numérique en `UShort` .

[!code-vb[VbVbalrFunctions#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#18)]

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- <xref:Microsoft.VisualBasic.Strings.Format%2A>
- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:Microsoft.VisualBasic.Conversion.Oct%2A>
- <xref:Microsoft.VisualBasic.Conversion.Str%2A>
- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [Fonctions de conversion](conversion-functions.md)
- [Conversions de type en Visual Basic](../../programming-guide/language-features/data-types/type-conversions.md)
