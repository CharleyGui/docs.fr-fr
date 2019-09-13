---
title: Conversions étendues et restrictives (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- widening conversions [Visual Basic]
- narrowing conversions [Visual Basic]
- conversions [Visual Basic], type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- conversions [Visual Basic], exceptions during conversion
- type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], data type
- conversions [Visual Basic], narrowing
- type conversion [Visual Basic], narrowing
- data type conversion [Visual Basic], widening
- data type conversion [Visual Basic], narrowing
- changing data types [Visual Basic]
- type conversion [Visual Basic], widening
- data type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], widening
ms.assetid: 058c3152-6c28-4268-af44-2209e774f0bd
ms.openlocfilehash: 858b2b2e154b659470fa61b21f25ab61eabda012
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965652"
---
# <a name="widening-and-narrowing-conversions-visual-basic"></a>Conversions étendues et restrictives (Visual Basic)
Un point important à prendre en compte lors d’une conversion de type est le fait que le résultat de la conversion se situe dans la plage du type de données de destination.  
  
 Une *conversion étendue* modifie une valeur en un type de données qui peut autoriser toute valeur possible des données d’origine.  Les conversions étendues préservent la valeur source, mais peuvent modifier sa représentation. Cela se produit si vous convertissez un type intégral `Decimal`en, ou `Char` de `String`à.  
  
 Une *conversion restrictive* modifie une valeur en un type de données qui peut ne pas pouvoir contenir certaines des valeurs possibles. Par exemple, une valeur fractionnaire est arrondie lorsqu’elle est convertie en un type intégral, et un type numérique converti `Boolean` en type est réduit `True` en `False`ou.  
  
## <a name="widening-conversions"></a>conversions étendues  
 Le tableau suivant répertorie les conversions étendues standard.  
  
|Type de données|S’étend aux types de données <sup>1</sup>|  
|---|---|  
|[SByte](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[Byte](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[short](../../../../visual-basic/language-reference/data-types/short-data-type.md)|`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[UShort](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Integer](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[UInteger](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Long](../../../../visual-basic/language-reference/data-types/long-data-type.md)|`Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[ULong](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Single](../../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`, `Double`|  
|[Double](../../../../visual-basic/language-reference/data-types/double-data-type.md)|`Double`|  
|Tout type énuméré ([enum](../../../../visual-basic/language-reference/statements/enum-statement.md))|Son type intégral sous-jacent et tout type d’extension du type sous-jacent.|  
|[Char](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`Char`, `String`|  
|Tableau `Char`|`Char`ensemble`String`|  
|Tout type|[Objet](../../../../visual-basic/language-reference/data-types/object-data-type.md)|  
|Tout type dérivé|Tout type de base dont il est dérivé <sup>3</sup>.|  
|Tout type|Toute interface qu’il implémente.|  
|[Nothing](../../../../visual-basic/language-reference/nothing.md)|Tout type de données ou type d’objet.|  
  
 <sup>1</sup> par définition, chaque type de données s’étend à lui-même.  
  
 <sup>2</sup> les conversions `Integer`de `UInteger`, `Long`, `ULong`, ou `Decimal` vers `Single` ou`Double` peuvent entraîner une perte de précision, mais ne sont jamais à l’ampleur. Dans ce sens, ils n’entraînent pas de perte d’informations.  
  
 <sup>3</sup> il peut paraître surprenant qu’une conversion d’un type dérivé vers l’un de ses types de base soit étendue. La justification est que le type dérivé contient tous les membres du type de base, donc il est qualifié d’instance du type de base. Dans la direction opposée, le type de base ne contient pas de nouveaux membres définis par le type dérivé.  
  
 Les conversions étendues fonctionnent toujours au moment de l’exécution et n’entraînent jamais de perte de données. Vous pouvez toujours les effectuer implicitement, que l' [instruction Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) définit le commutateur de vérification de `On` type sur `Off`ou sur.  
  
## <a name="narrowing-conversions"></a>conversions restrictives  
 Les conversions restrictives standard sont les suivantes :  
  
- Sens inverse des conversions étendues dans le tableau précédent (sauf que chaque type s’étend à lui-même)  
  
- Conversions dans l’un ou l’autre sens entre les types [booléen](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) et tout type numérique  
  
- Conversions d’un type numérique en n’importe quel type énuméré`Enum`()  
  
- Conversions dans l’un ou l’autre sens entre une [chaîne](../../../../visual-basic/language-reference/data-types/string-data-type.md) et un type numérique, `Boolean`, ou [Date](../../../../visual-basic/language-reference/data-types/date-data-type.md)  
  
- Conversions d’un type de données ou d’un type d’objet en un type dérivé de celui-ci  
  
 Les conversions restrictives ne réussissent pas toujours au moment de l’exécution et peuvent échouer ou entraîner une perte de données. Une erreur se produit si le type de données de destination ne peut pas recevoir la valeur en cours de conversion. Par exemple, une conversion numérique peut entraîner un dépassement de capacité. Le compilateur ne vous permet pas d’effectuer des conversions restrictives de manière implicite, sauf si l' [instruction Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) définit `Off`le commutateur de vérification de type sur.  
  
> [!NOTE]
> L’erreur de conversion restrictive est supprimée pour les conversions des éléments d’une `For Each…Next` collection vers la variable de contrôle de boucle. Pour plus d’informations et d’exemples, consultez la section « conversions restrictives » dans [for each... Instruction suivante](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
### <a name="when-to-use-narrowing-conversions"></a>Quand utiliser des conversions restrictives  
 Vous utilisez une conversion restrictive lorsque vous savez que la valeur source peut être convertie vers le type de données de destination sans erreur ou perte de données. Par exemple, si vous avez un `String` dont vous savez qu’il contient « true » ou « false », vous pouvez `CBool` utiliser le mot clé pour `Boolean`le convertir en.  
  
## <a name="exceptions-during-conversion"></a>Exceptions pendant la conversion  
 Étant donné que les conversions étendues fonctionnent toujours, elles ne lèvent pas d’exceptions. Les conversions restrictives, quand elles échouent, génèrent généralement les exceptions suivantes :  
  
- <xref:System.InvalidCastException>: si aucune conversion n’est définie entre les deux types  
  
- <xref:System.OverflowException>— (types intégraux uniquement) si la valeur convertie est trop grande pour le type cible  
  
 Si une classe ou une structure définit une [fonction CType](../../../../visual-basic/language-reference/functions/ctype-function.md) comme opérateur de conversion vers ou à partir de cette classe ou structure, `CType` cela peut lever toute exception qu’elle juge appropriée. De plus, cela `CType` peut appeler des fonctions Visual Basic ou des méthodes .NET Framework, qui peuvent à leur tour lever diverses exceptions.  
  
## <a name="changes-during-reference-type-conversions"></a>Modifications lors des conversions de types de référence  
 Une conversion à partir d’un *type référence* copie uniquement le pointeur vers la valeur. La valeur elle-même n’est ni copiée, ni modifiée de quelque manière que ce soit. La seule chose qui peut changer est le type de données de la variable qui contient le pointeur. Dans l’exemple suivant, le type de données est converti de la classe dérivée en sa classe de base, mais l’objet vers lequel les deux variables pointent est inchangé.  
  
```  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## <a name="see-also"></a>Voir aussi

- [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Conversions de type dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Conversions implicites et explicites](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Conversion entre des chaînes et d’autres types](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [Guide pratique pour Convertir un objet en un autre type dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [Conversions de tableau](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [Types de données](../../../../visual-basic/language-reference/data-types/index.md)
- [Fonctions de conversion de types](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
