---
title: Octet (type de données)
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 347d7e7d0f09e089886bc81bd0be659deaca9b46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400742"
---
# <a name="byte-data-type-visual-basic"></a>Type de données byte (Visual Basic)

Détient des intégrés 8 bits non signés (1-byte) dont la valeur varie de 0 à 255.

## <a name="remarks"></a>Notes 

Utilisez `Byte` le type de données pour contenir des données binaires.  
  
La valeur par défaut de `Byte` est 0.

## <a name="literal-assignments"></a>Affectations littérales

Vous pouvez déclarer et `Byte` initialiser une variable en lui assignant un littéal décimal, un littéal hexadecimal, un littéral octal, ou (à partir de Visual Basic 2017) un littéral binaire. Si le littéral intégral est `Byte` en dehors de la portée <xref:System.Byte.MinValue?displayProperty=nameWithType> d’un (c’est-à-dire, si elle est inférieure ou supérieure <xref:System.Byte.MaxValue?displayProperty=nameWithType>à), une erreur de compilation se produit.

Dans l’exemple suivant, les intégristes égaux à 201 qui sont représentés comme décimales, hexadecimal, `byte` et les littérals binaires sont implicitement convertis d’Integer à des valeurs. [Integer](integer-data-type.md)

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> Vous utilisez le `&h` `&H` préfixe ou pour désigner un littératal hexadecimal, le `&b` préfixe ou `&B` pour désigner un littératique binaire, et le préfixe `&o` ou `&O` pour désigner un littéral octal. Les littéraux décimaux n’ont pas de préfixe.

En commençant par Visual Basic 2017, vous `_`pouvez également utiliser le personnage de soulignement, , comme séparateur à chiffres pour améliorer la lisibilité, comme le montre l’exemple suivant.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

En commençant par Visual Basic 15.5, vous`_`pouvez également utiliser le caractère de soulignement ( ) comme séparateur de premier plan entre le préfixe et les chiffres hexadecimal, binaire ou octal. Par exemple :

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a>Conseils de programmation

- **Nombres négatifs.** Parce `Byte` qu’il s’agit d’un type non signé, il ne peut pas représenter un nombre négatif. Si vous utilisez l’opérateur unary moins (`-`) `Byte`sur une expression qui `Short` évalue au type, Visual Basic convertit l’expression en premier.
  
- **Conversions de format.** Lorsque Visual Basic lit ou écrit des fichiers, ou lorsqu’il appelle les DLL, les méthodes et les propriétés, il peut automatiquement convertir entre les formats de données. Les données `Byte` binaires stockées dans les variables et les tableaux sont conservées lors de ces conversions de format. Vous ne devez `String` pas utiliser une variable pour les données binaires, car son contenu peut être corrompu lors de la conversion entre les formats ANSI et Unicode.

- **Élargissement.** Le `Byte` type de `Short`données `UShort` `Integer`s’élargit `ULong` `Decimal`à `Single`, `Double`, , `UInteger` `Long`, , , , , ou . Cela signifie que `Byte` vous pouvez convertir à <xref:System.OverflowException?displayProperty=nameWithType> l’un de ces types sans rencontrer une erreur.
  
- **Personnages de type.** `Byte`n’a pas de caractère de type littéral ou de caractère de type identifiant.

- **Type .NET Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.Byte?displayProperty=nameWithType>.

## <a name="example"></a> Exemple

 Dans l’exemple `b` suivant, est une `Byte` variable. Les énoncés démontrent la portée de la variable et l’application des opérateurs de décalage.

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a>Voir aussi

- <xref:System.Byte?displayProperty=nameWithType>
- [Types de données](../../../visual-basic/language-reference/data-types/index.md)
- [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
