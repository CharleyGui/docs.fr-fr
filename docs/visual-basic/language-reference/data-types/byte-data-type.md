---
title: Byte, type de données
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 347d7e7d0f09e089886bc81bd0be659deaca9b46
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344079"
---
# <a name="byte-data-type-visual-basic"></a>Byte, type de données (Visual Basic)

Contient des entiers 8 bits (1 octet) non signés dont la valeur est comprise entre 0 et 255.

## <a name="remarks"></a>Notes

Utilisez le type de données `Byte` pour contenir des données binaires.  
  
La valeur par défaut de `Byte` est 0.

## <a name="literal-assignments"></a>Affectations littérales

Vous pouvez déclarer et initialiser une variable `Byte` en lui assignant un littéral décimal, un littéral hexadécimal, un littéral octal ou (à partir de Visual Basic 2017) un littéral binaire. Si le littéral intégral se trouve en dehors de la plage d’un `Byte` (autrement dit, s’il est inférieur à <xref:System.Byte.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.Byte.MaxValue?displayProperty=nameWithType>), une erreur de compilation se produit.

Dans l’exemple suivant, les entiers égaux à 201 représentés comme des littéraux décimaux, hexadécimaux et binaires sont convertis implicitement d’un [entier](integer-data-type.md) en valeurs `byte`.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> Vous utilisez le préfixe `&h` ou `&H` pour désigner un littéral hexadécimal, le préfixe `&b` ou `&B` pour désigner un littéral binaire, et le préfixe `&o` ou `&O` pour désigner un littéral octal. Les littéraux décimaux n’ont pas de préfixe.

À compter de Visual Basic 2017, vous pouvez également utiliser le trait de soulignement, `_`, comme séparateur de chiffres pour améliorer la lisibilité, comme le montre l’exemple suivant.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

À compter de Visual Basic 15,5, vous pouvez également utiliser le caractère de soulignement (`_`) comme séparateur de début entre le préfixe et les chiffres hexadécimaux, binaires ou octaux. Exemple :

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a>Conseils de programmation

- **Nombres négatifs.** Étant donné que `Byte` est un type non signé, il ne peut pas représenter un nombre négatif. Si vous utilisez l’opérateur moins unaire (`-`) sur une expression qui prend la valeur du type `Byte`, Visual Basic convertit d’abord l’expression en `Short`.
  
- **Conversions de format.** Lorsque Visual Basic lit ou écrit des fichiers, ou lorsqu’il appelle des dll, des méthodes et des propriétés, il peut effectuer automatiquement une conversion entre des formats de données. Les données binaires stockées dans `Byte` les variables et les tableaux sont conservées au cours de ces conversions de format. Vous ne devez pas utiliser une variable `String` pour les données binaires, car son contenu peut être endommagé lors de la conversion entre des formats ANSI et Unicode.

- **Étendue.** Le type de données `Byte` s’étend à `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`ou `Double`. Cela signifie que vous pouvez convertir `Byte` en l’un de ces types sans rencontrer d’erreur de <xref:System.OverflowException?displayProperty=nameWithType>.
  
- **Caractères de type.** `Byte` n’a aucun caractère de type de littéral ou caractère de type d’identificateur.

- **Type de Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.Byte?displayProperty=nameWithType>.

## <a name="example"></a>Exemple

 Dans l’exemple suivant, `b` est une variable `Byte`. Les instructions démontrent la plage de la variable et l’application des opérateurs de décalage de bits.

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a>Voir aussi

- <xref:System.Byte?displayProperty=nameWithType>
- [Types de données](../../../visual-basic/language-reference/data-types/index.md)
- [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
