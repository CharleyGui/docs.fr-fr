---
title: Nothing (mot clé)
ms.date: 07/20/2015
f1_keywords:
- Nothing
- vb.Nothing
helpviewer_keywords:
- Nothing keyword [Visual Basic]
- Nothing keyword [Visual Basic], syntax
ms.assetid: 06176e2d-bbf7-4a37-afaa-a86ad21ee99f
ms.openlocfilehash: 3bd4681341a33cc8db4ecbc2b284be243db56549
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344166"
---
# <a name="nothing-keyword-visual-basic"></a>Mot clé Nothing (Visual Basic)

Représente la valeur par défaut de n’importe quel type de données. Pour les types de référence, la valeur par défaut est la référence `null`. Pour les types valeur, la valeur par défaut varie selon que le type valeur est Nullable ou non.

> [!NOTE]
> Pour les types valeur n’acceptant pas les valeurs NULL, `Nothing` dans C#Visual Basic diffère de `null` dans. Dans Visual Basic, si vous définissez une variable d’un type valeur qui n’autorise pas les valeurs NULL sur `Nothing`, la variable est définie sur la valeur par défaut pour son type déclaré. Dans C#, si vous assignez une variable d’un type valeur n’acceptant pas les valeurs null à `null`, une erreur de compilation se produit.

## <a name="remarks"></a>Notes

`Nothing` représente la valeur par défaut d’un type de données. La valeur par défaut varie selon que la variable est d’un type valeur ou d’un type référence.

Une variable d’un *type valeur* contient directement sa valeur. Les types valeur incluent tous les types de données numériques, les `Boolean`, les `Char`, les `Date`, toutes les structures et toutes les énumérations. Une variable d’un *type référence* stocke une référence à une instance de l’objet en mémoire. Les types référence incluent des classes, des tableaux, des délégués et des chaînes. Pour plus d'informations, consultez [Value Types and Reference Types](../programming-guide/language-features/data-types/value-types-and-reference-types.md).

Si une variable est d’un type valeur, le comportement de `Nothing` varie selon que la variable est d’un type de données Nullable ou non. Pour représenter un type valeur Nullable, ajoutez un modificateur `?` au nom de type. L’affectation de `Nothing` à une variable Nullable définit la valeur sur `null`. Pour plus d’informations et d’exemples, consultez [types valeur Nullable](../programming-guide/language-features/data-types/nullable-value-types.md).

Si une variable est d’un type de valeur qui n’accepte pas la valeur null, l’assignation de `Nothing` à celle-ci lui affecte la valeur par défaut pour son type déclaré. Si ce type contient des membres de variables, ils sont tous définis sur leurs valeurs par défaut. L’exemple suivant illustre cela pour les types scalaires.

[!code-vb[VbVbalrKeywords#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class2.vb#7)]

Si une variable est d’un type référence, l’affectation de `Nothing` à la variable la définit sur une `null` référence du type de la variable. Une variable qui est définie sur une référence `null` n’est pas associée à un objet. Cela est illustré par l'exemple suivant :

[!code-vb[VbVbalrKeywords#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class3.vb#8)]

Lorsque vous vérifiez si une variable de référence (ou un type de valeur Nullable) est `null`, n’utilisez pas `= Nothing` ou `<> Nothing`. Utilisez toujours `Is Nothing` ou `IsNot Nothing`.

Pour les chaînes dans Visual Basic, la chaîne vide est égale à `Nothing`. Par conséquent, `"" = Nothing` a la valeur true.

L’exemple suivant illustre des comparaisons qui utilisent les opérateurs `Is` et `IsNot` :

[!code-vb[VbVbalrKeywords#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class4.vb#9)]

Si vous déclarez une variable sans utiliser de clause `As` et que vous la définissez sur `Nothing`, la variable a un type de `Object`. `Dim something = Nothing`en est un exemple. Dans ce cas, une erreur de compilation se produit lorsque `Option Strict` est activé et que `Option Infer` est désactivé.

Quand vous assignez des `Nothing` à une variable objet, elle ne fait plus référence à une instance d’objet. Si la variable avait précédemment fait l’appel d’une instance, sa définition sur `Nothing` ne met pas fin à l’instance elle-même. L’instance est arrêtée, et la mémoire et les ressources système qui lui sont associées sont libérées, uniquement après que le garbage collector (GC) a détecté qu’il n’y a aucune référence active restante.

`Nothing` diffère de l’objet <xref:System.DBNull>, qui représente une variante non initialisée ou une colonne de base de données inexistante.

## <a name="see-also"></a>Voir aussi

- [Dim (instruction)](./statements/dim-statement.md)
- [Durée de vie d’un objet : création et destruction des objets](../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Durée de vie dans Visual Basic](../programming-guide/language-features/declared-elements/lifetime.md)
- [Is (opérateur)](./operators/is-operator.md)
- [IsNot (opérateur)](./operators/isnot-operator.md)
- [Types valeur Nullable](../programming-guide/language-features/data-types/nullable-value-types.md)
