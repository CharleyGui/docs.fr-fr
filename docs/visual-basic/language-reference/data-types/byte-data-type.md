---
title: Octet (type de données)
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 97acd1bc2ff29bac6588216b9ee4a4f187078815
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374315"
---
# <a name="byte-data-type-visual-basic"></a>Byte, type de données (Visual Basic)

Contient des entiers 8 bits (1 octet) non signés dont la valeur est comprise entre 0 et 255.

## <a name="remarks"></a>Notes

Utilisez le `Byte` type de données pour contenir des données binaires.  
  
La valeur par défaut de `Byte` est 0.

## <a name="literal-assignments"></a>Affectations littérales

Vous pouvez déclarer et initialiser une `Byte` variable en lui assignant un littéral décimal, un littéral hexadécimal, un littéral octal ou (à partir de Visual Basic 2017) un littéral binaire. Si le littéral intégral se trouve en dehors de la plage d’un `Byte` (autrement dit, s’il est inférieur à <xref:System.Byte.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.Byte.MaxValue?displayProperty=nameWithType> ), une erreur de compilation se produit.

Dans l’exemple suivant, les entiers égaux à 201 représentés comme des littéraux décimaux, hexadécimaux et binaires sont implicitement convertis d’un [entier](integer-data-type.md) en `byte` valeurs.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> Vous utilisez le préfixe `&h` ou `&H` pour désigner un littéral hexadécimal, le préfixe `&b` ou `&B` pour désigner un littéral binaire, et le préfixe `&o` ou `&O` pour désigner un littéral octal. Les littéraux décimaux n’ont pas de préfixe.

À compter de Visual Basic 2017, vous pouvez également utiliser le caractère de soulignement, `_` , comme séparateur de chiffres pour améliorer la lisibilité, comme le montre l’exemple suivant.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

À compter de Visual Basic 15,5, vous pouvez également utiliser le trait de soulignement ( `_` ) comme séparateur de début entre le préfixe et les chiffres hexadécimaux, binaires ou octaux. Par exemple :

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a>Conseils de programmation

- **Nombres négatifs.** Étant donné que `Byte` est un type non signé, il ne peut pas représenter un nombre négatif. Si vous utilisez l’opérateur moins unaire ( `-` ) sur une expression qui prend la valeur type `Byte` , Visual Basic convertit d’abord l’expression en `Short` premier.
  
- **Conversions de format.** Lorsque Visual Basic lit ou écrit des fichiers, ou lorsqu’il appelle des dll, des méthodes et des propriétés, il peut effectuer automatiquement une conversion entre des formats de données. Les données binaires stockées dans des `Byte` variables et des tableaux sont conservées au cours de ces conversions de format. Vous ne devez pas utiliser une `String` variable pour les données binaires, car son contenu peut être endommagé lors de la conversion entre des formats ANSI et Unicode.

- **Étendue.** Le `Byte` type de données s’étend à `Short` , `UShort` , `Integer` , `UInteger` , `Long` , `ULong` , `Decimal` , `Single` ou `Double` . Cela signifie que vous pouvez `Byte` effectuer une conversion vers l’un de ces types sans rencontrer d' <xref:System.OverflowException?displayProperty=nameWithType> erreur.
  
- **Caractères de type.** `Byte`n’a aucun caractère de type de littéral ou caractère de type d’identificateur.

- **Type .NET Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.Byte?displayProperty=nameWithType>.

## <a name="example"></a>Exemple

 Dans l’exemple suivant, `b` est une `Byte` variable. Les instructions démontrent la plage de la variable et l’application des opérateurs de décalage de bits.

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a>Voir aussi

- <xref:System.Byte?displayProperty=nameWithType>
- [Types de données](index.md)
- [Type Conversion Functions](../functions/type-conversion-functions.md)
- [Liste des conversions](../keywords/conversion-summary.md)
- [Utilisation efficace des types de données](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
