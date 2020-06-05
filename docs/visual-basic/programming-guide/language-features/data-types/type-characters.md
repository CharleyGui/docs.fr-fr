---
title: Caractères de type
ms.date: 01/31/2018
helpviewer_keywords:
- '&H prefix for hexadecimal values'
- hexadecimal literals [Visual Basic]
- F literal type character [Visual Basic]
- '& identifier type character'
- type characters [Visual Basic]
- octal literals [Visual Basic]
- literals [Visual Basic], hexadecimal
- '&O prefix for octal values'
- literals [Visual Basic], default types
- defaults, literal types
- C literal type character [Visual Basic]
- type characters [Visual Basic], literal
- $ identifier type character
- L literal type character [Visual Basic]
- UI literal type characters [Visual Basic]
- default literal types [Visual Basic]
- D literal type character [Visual Basic]
- literals [Visual Basic], octal
- S literal type character [Visual Basic]
- '! identifier type character'
- US literal type characters [Visual Basic]
- '% identifier type character'
- data types [Visual Basic], type characters
- characters [Visual Basic], identifier type
- type characters [Visual Basic], identifier
- '# identifier type character'
- identifier type characters [Visual Basic]
- literal type characters [Visual Basic]
- I literal type character [Visual Basic]
- R literal type character [Visual Basic]
- '@ identifier type character'
- UL literal type characters [Visual Basic]
- literal types [Visual Basic], default
ms.assetid: 6353cb9b-6ee4-4af6-a5a8-88ce39f90cc5
ms.openlocfilehash: a48260694c1dfcbbb8f804f220fe89b1663c7319
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393076"
---
# <a name="type-characters-visual-basic"></a>Caractères de type (Visual Basic)

En plus de spécifier un type de données dans une instruction de déclaration, vous pouvez forcer le type de données de certains éléments de programmation avec un *caractère de type*. Le caractère de type doit suivre immédiatement l’élément, sans aucun caractère intermédiaire de quelque sorte que ce soit.

Le caractère de type ne fait pas partie du nom de l’élément. Un élément défini avec un caractère de type peut être référencé sans le caractère de type.

## <a name="identifier-type-characters"></a>Caractères de type d’identificateur

Visual Basic fournit un ensemble de *caractères de type d’identificateur* que vous pouvez utiliser dans une déclaration pour spécifier le type de données d’une variable ou d’une constante. Le tableau suivant présente les caractères de type d’identificateur disponibles avec des exemples d’utilisation.
  
|Caractère de type d’identificateur|Type de données|Exemple|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 Il n’existe aucun caractère de type d’identificateur pour les `Boolean` `Byte` types de données,, `Char` , `Date` ,,,,, `Object` `SByte` `Short` `UInteger` `ULong` ou `UShort` , ou pour tous les types de données composites tels que les tableaux ou les structures.

Dans certains cas, vous pouvez ajouter le `$` caractère à une fonction Visual Basic, par exemple `Left$` au lieu de `Left` , pour obtenir une valeur retournée de type `String` .

Dans tous les cas, le caractère de type d’identificateur doit suivre immédiatement le nom de l’identificateur.

## <a name="literal-type-characters"></a>Caractères de type littéral

Un *littéral* est une représentation textuelle d’une valeur particulière d’un type de données.  

### <a name="default-literal-types"></a>Types de littéraux par défaut

La forme d’un littéral tel qu’il apparaît dans votre code détermine normalement son type de données. Le tableau suivant présente ces types par défaut.  
  
|Forme textuelle du littéral|Type de données par défaut|Exemple|  
|-----------------------------|-----------------------|-------------|  
|Numérique, aucune partie fractionnaire|`Integer`|`2147483647`|  
|Numérique, aucune partie fractionnaire, trop grande pour`Integer`|`Long`|`2147483648`|  
|Numérique, partie fractionnaire|`Double`|`1.2`|  
|délimité par des guillemets doubles ;|`String`|`"A"`|  
|Entre les signes dièse|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a>Types de littéraux forcés

Visual Basic fournit un ensemble de *caractères de type de littéral*, que vous pouvez utiliser pour forcer un littéral à supposer un type de données autre que celui que son formulaire indique. Pour ce faire, ajoutez le caractère à la fin du littéral. Le tableau suivant présente les caractères de type de littéral disponibles avec des exemples d’utilisation.
  
|Caractère de type littéral|Type de données|Exemple|  
|----------------------------|---------------|-------------|  
|`S`|`Short`|`I = 347S`|
|`I`|`Integer`|`J = 347I`|
|`L`|`Long`|`K = 347L`|
|`D`|`Decimal`|`X = 347D`|
|`F`|`Single`|`Y = 347F`|
|`R`|`Double`|`Z = 347R`|
|`US`|`UShort`|`L = 347US`|
|`UI`|`UInteger`|`M = 347UI`|
|`UL`|`ULong`|`N = 347UL`|
|`C`|`Char`|`Q = "."C`|

Il n’existe aucun caractère de type de littéral pour les `Boolean` `Byte` types de données,, `Date` , `Object` , `SByte` ou `String` , ou pour tous les types de données composites tels que les tableaux ou les structures.

Les littéraux peuvent également utiliser les caractères de type d’identificateur ( `%` , `&` ,, `@` `!` , `#` , `$` ), comme les variables, les constantes et les expressions. Toutefois, les caractères de type de littéral ( `S` , `I` , `L` , `D` , `F` , `R` , `C` ) ne peuvent être utilisés qu’avec des littéraux.

Dans tous les cas, le caractère de type de littéral doit suivre immédiatement la valeur littérale.

## <a name="hexadecimal-binary-and-octal-literals"></a>Littéraux hexadécimaux, binaires et octaux

Le compilateur interprète normalement un littéral d’entier comme étant dans le système de nombre décimal (base 10). Vous pouvez également définir un littéral d’entier comme nombre hexadécimal (base 16) avec le `&H` préfixe, en tant que nombre binaire (base 2) avec le `&B` préfixe, et en tant que nombre octal (base 8) avec le `&O` préfixe. Les chiffres qui suivent le préfixe doivent être appropriés pour le système de nombres. Le tableau suivant illustre cela.  
  
|Base numérique|Préfixe|Valeurs de chiffres valides|Exemple|
|-----------------|------------|------------------------|-------------|
|Hexadécimale (base 16)|`&H`|0-9 et A-F|`&HFFFF`|
|Binaire (base 2)|`&B`|0-1|`&B01111100`|
|Octale (base 8)|`&O`|0-7|`&O77`|

À partir de Visual Basic 2017, vous pouvez utiliser le caractère de soulignement ( `_` ) comme séparateur de groupes pour améliorer la lisibilité d’un littéral intégral. L’exemple suivant utilise le `_` caractère pour regrouper un littéral binaire en groupes 8 bits :

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

Vous pouvez suivre un littéral préfixé avec un caractère de type littéral. L'exemple suivant illustre cela.

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

Dans l’exemple précédent, `counter` a la valeur décimale-32768 et `flags` a la valeur décimale + 32768.

À compter de Visual Basic 15,5, vous pouvez également utiliser le trait de soulignement ( `_` ) comme séparateur de début entre le préfixe et les chiffres hexadécimaux, binaires ou octaux. Par exemple :

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../../includes/vb-separator-langversion.md)]

## <a name="see-also"></a>Voir aussi

- [Types de données](index.md)
- [Types de données élémentaires](elementary-data-types.md)
- [Types valeur et types référence](value-types-and-reference-types.md)
- [Conversions de type en Visual Basic](type-conversions.md)
- [Dépannage des types de données](troubleshooting-data-types.md)
- [Déclaration de variable](../variables/variable-declaration.md)
- [Types de données](../../../language-reference/data-types/index.md)
