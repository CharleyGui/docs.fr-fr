---
title: Type de données défini par l’utilisateur (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- UserDefined
- UDT
- vb.UDT
- User-Defined
- vb.UserDefined
- vb.User-Defined
helpviewer_keywords:
- user-defined data types [Visual Basic], Visual Basic
- user-defined types
- structures [Visual Basic], as user-defined data types
- user-defined types [Visual Basic], Visual Basic
- user-defined types [Visual Basic], structure declaration
- user-defined types [Visual Basic], structures in Visual Basic
- user-defined data types [Visual Basic], structure declaration
- data types [Visual Basic], assigning
- Structure statement [Visual Basic]
- data types [Visual Basic], user-defined
- user-defined data types [Visual Basic], structures in Visual Basic
- user-defined data types
- types [Visual Basic], user-defined
ms.assetid: be913dca-a364-4a51-96a1-549a1b390b0a
ms.openlocfilehash: 76073037dcaac0e87bc8a352f3b438332d11d881
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630131"
---
# <a name="user-defined-data-type"></a>Type de données défini par l'utilisateur

Contient des données dans un format que vous définissez. L' `Structure` instruction définit le format.

Les versions précédentes de Visual Basic prennent en charge le type défini par l’utilisateur (UDT). La version actuelle développe l’UDT en une *structure*. Une structure est une concaténation d’un ou plusieurs *membres* de différents types de données. Visual Basic traite une structure comme une unité unique, même si vous pouvez également accéder à ses membres individuellement.

## <a name="remarks"></a>Notes

Définissez et utilisez un type de données structure lorsque vous devez combiner plusieurs types de données en une seule unité, ou lorsque aucun des types de données élémentaires ne répond à vos besoins.

La valeur par défaut d’un type de données structure se compose de la combinaison des valeurs par défaut de chacun de ses membres.

## <a name="declaration-format"></a>Format de déclaration

Une déclaration de structure commence par l' [instruction structure](../../../visual-basic/language-reference/statements/structure-statement.md) et se termine par l' `End Structure` instruction. L' `Structure` instruction fournit le nom de la structure, qui est également l’identificateur du type de données défini par la structure. D’autres parties du code peuvent utiliser cet identificateur pour déclarer des variables, des paramètres et des valeurs de retour de fonction comme étant du type de données de cette structure.

Les déclarations entre les `Structure` instructions `End Structure` et définissent les membres de la structure.

## <a name="member-access-levels"></a>Niveaux d’accès aux membres

Vous devez déclarer chaque membre à l’aide d’une [instruction Dim](../../../visual-basic/language-reference/statements/dim-statement.md) ou d’une instruction qui spécifie le niveau d’accès, par exemple [public](../../../visual-basic/language-reference/modifiers/public.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md)ou [Private](../../../visual-basic/language-reference/modifiers/private.md). Si vous utilisez une `Dim` instruction, le niveau d’accès par défaut est public.

## <a name="programming-tips"></a>Conseils de programmation

- **Consommation de mémoire.** Comme avec tous les types de données composites, vous ne pouvez pas calculer en toute sécurité la consommation de mémoire totale d’une structure en additionnant les allocations de stockage nominal de ses membres. En outre, vous ne pouvez pas supposer sans risque que l’ordre de stockage en mémoire est le même que celui de votre ordre de déclaration. Si vous devez contrôler la disposition de stockage d’une structure, vous pouvez appliquer l' <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribut à l' `Structure` instruction.

- **Considérations relatives à l’interopérabilité.** Si vous utilisez des composants non écrits pour le .NET Framework, par exemple des objets Automation ou COM, n’oubliez pas que les types définis par l’utilisateur dans d’autres environnements ne sont pas compatibles avec les types de structure Visual Basic.

- **Étendue.** Il n’existe aucune conversion automatique vers ou à partir de n’importe quel type de données de structure. Vous pouvez définir des opérateurs de conversion sur votre structure à l’aide de l' [instruction Operator](../../../visual-basic/language-reference/statements/operator-statement.md), et vous pouvez déclarer `Widening` chaque `Narrowing`opérateur de conversion comme étant ou.

- **Caractères de type.** Les types de données de structure n’ont aucun caractère de type de littéral ou caractère de type d’identificateur.

- **Type de Framework.** Il n’y a aucun type correspondant dans la .NET Framework. Toutes les structures héritent de la <xref:System.ValueType?displayProperty=nameWithType>classe .NET Framework, mais aucune structure individuelle <xref:System.ValueType?displayProperty=nameWithType>ne correspond à.

## <a name="example"></a>Exemple

Le paradigme suivant montre le plan de la déclaration d’une structure.

```
[Public | Protected | Friend | Protected Friend | Private] Structure structname
    {Dim | Public | Friend | Private} member1 As datatype1
    ' ...
    {Dim | Public | Friend | Private} memberN As datatypeN
End Structure
```

## <a name="see-also"></a>Voir aussi

- <xref:System.ValueType>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [Types de données](../../../visual-basic/language-reference/data-types/index.md)
- [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Structure (instruction)](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Widening](../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
