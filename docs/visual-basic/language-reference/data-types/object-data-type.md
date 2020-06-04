---
title: Object Data Type
ms.date: 07/20/2015
f1_keywords:
- vb.Object
- vb.Variant
helpviewer_keywords:
- object variables [Visual Basic], Object type
- data types [Visual Basic], assigning
- Object data type
- Object data type [Visual Basic], reference
ms.assetid: 61ea4a7c-3b3d-48d4-adc4-eacfa91779b2
ms.openlocfilehash: 14770e74a0169dba3a45a04845dd32323e6201e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415581"
---
# <a name="object-data-type"></a>Object Data Type

Contient des adresses qui font référence à des objets. Vous pouvez assigner n’importe quel type référence (chaîne, tableau, classe ou interface) à une `Object` variable. Une `Object` variable peut également faire référence à des données de n’importe quel type de valeur (numérique,,,, `Boolean` `Char` `Date` structure ou énumération).

## <a name="remarks"></a>Notes

Le `Object` type de données peut pointer vers des données de n’importe quel type de données, y compris toute instance d’objet que votre application reconnaît. Utilisez `Object` lorsque vous ne savez pas au moment de la compilation le type de données auquel la variable peut pointer.

La valeur par défaut de `Object` est `Nothing` (une référence null).

## <a name="data-types"></a>Types de données

Vous pouvez assigner une variable, une constante ou une expression de n’importe quel type de données à une `Object` variable. Pour déterminer le type de données `Object` auquel une variable fait actuellement référence, vous pouvez utiliser la <xref:System.Type.GetTypeCode%2A> méthode de la <xref:System.Type?displayProperty=nameWithType> classe. L'exemple suivant illustre ce comportement.

```vb
Dim myObject As Object
' Suppose myObject has now had something assigned to it.
Dim datTyp As Integer
datTyp = Type.GetTypeCode(myObject.GetType())
```

Le `Object` type de données est un type référence. Toutefois, Visual Basic traite une `Object` variable comme un type valeur lorsqu’elle fait référence à des données d’un type valeur.

## <a name="storage"></a>Stockage

Quel que soit le type de données auquel il fait référence, une `Object` variable ne contient pas la valeur de données elle-même, mais plutôt un pointeur vers la valeur. Elle utilise toujours quatre octets dans la mémoire de l’ordinateur, mais cela n’inclut pas le stockage pour les données représentant la valeur de la variable. En raison du code qui utilise le pointeur pour localiser les données, les `Object` variables contenant des types valeur sont légèrement plus lentes pour l’accès que les variables explicitement typées.

## <a name="programming-tips"></a>Conseils de programmation

- **Considérations sur l'interopérabilité.** Si vous utilisez des composants non écrits pour le .NET Framework, par exemple des objets Automation ou COM, gardez à l’esprit que les types pointeur dans d’autres environnements ne sont pas compatibles avec le `Object` type Visual Basic.

- **Niveau de performance.** Une variable que vous déclarez avec le `Object` type est suffisamment flexible pour contenir une référence à n’importe quel objet. Toutefois, lorsque vous appelez une méthode ou une propriété sur une telle variable, vous subissez toujours une *liaison tardive* (au moment de l’exécution). Pour forcer une *liaison précoce* (au moment de la compilation) et de meilleures performances, déclarez la variable avec un nom de classe spécifique ou effectuez un cast de celle-ci vers le type de données spécifique.

  Quand vous déclarez une variable objet, essayez d’utiliser un type de classe spécifique, par exemple <xref:System.OperatingSystem> , au lieu du `Object` type généralisé. Vous devez également utiliser la classe la plus spécifique disponible, par exemple <xref:System.Windows.Forms.TextBox> au lieu de <xref:System.Windows.Forms.Control> , afin de pouvoir accéder à ses propriétés et méthodes. Vous pouvez généralement utiliser la liste **classes** dans l' **Explorateur d’objets** pour rechercher les noms de classes disponibles.

- **Étendue.** Tous les types de données et tous les types de référence sont étendus au `Object` type de données. Cela signifie que vous pouvez convertir n’importe quel type en `Object` sans rencontrer une <xref:System.OverflowException?displayProperty=nameWithType> erreur.

  Toutefois, si vous effectuez une conversion entre des types valeur et `Object` , Visual Basic effectue des opérations appelées *boxing* et *unboxing*, ce qui ralentit l’exécution.

- **Caractères de type.** `Object`n’a aucun caractère de type de littéral ou caractère de type d’identificateur.

- **Type .NET Framework.** Le type correspondant dans le .NET Framework est la <xref:System.Object?displayProperty=nameWithType> classe.

## <a name="example"></a>Exemple

L’exemple suivant illustre une `Object` variable pointant vers une instance d’objet.

```vb
Dim objDb As Object
Dim myCollection As New Collection()
' Suppose myCollection has now been populated.
objDb = myCollection.Item(1)
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Object>
- [Types de données](index.md)
- [Type Conversion Functions](../functions/type-conversion-functions.md)
- [Liste des conversions](../keywords/conversion-summary.md)
- [Utilisation efficace des types de données](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Comment : déterminer si deux objets sont liés](../../programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Guide pratique : déterminer si deux objets sont identiques](../../programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
