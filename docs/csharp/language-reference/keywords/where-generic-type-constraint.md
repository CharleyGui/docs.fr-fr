---
title: where (contrainte de type générique) - Référence C#
ms.date: 04/15/2020
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: 5a56b8058735d3ca786520a82424c79d1975bfc4
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463010"
---
# <a name="where-generic-type-constraint-c-reference"></a>where (contrainte de type générique) (Référence C#)

La clause `where` dans une définition générique spécifie des contraintes sur les types qui sont utilisés comme arguments pour les paramètres de type d’un type générique, d’une méthode, d’un délégué ou d’une fonction locale. Les contraintes peuvent spécifier les interfaces, les classes de base ou exiger qu’un type générique soit un type de référence, de valeur ou non. Ils déclarent des capacités que l’argument de type doit avoir.

Vous pouvez, par exemple, déclarer une classe générique, `MyGenericClass`, de telle sorte que le paramètre de type `T` implémente l’interface <xref:System.IComparable%601> :

[!code-csharp[using an interface constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> Pour plus d’informations sur la clause where dans une expression de requête, consultez [where, clause](where-clause.md).

La clause `where` peut également inclure une contrainte de classe de base. La contrainte de classe de base indique qu’un type à utiliser comme argument de type pour ce type générique a la classe spécifiée comme classe de base, ou est cette classe de base. Si la contrainte de classe de base est utilisée, elle doit apparaître avant toute autre contrainte sur ce paramètre de type. Certains types ne sont pas autorisés comme contrainte de classe de base : <xref:System.Object>, <xref:System.Array> et <xref:System.ValueType>. Avant C <xref:System.Enum>7.3, <xref:System.Delegate>, <xref:System.MulticastDelegate> , et ont également été refusés comme contraintes de classe de base. L’exemple suivant montre les types qui peuvent maintenant être spécifiés comme classe de base :

[!code-csharp[using an interface constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

Dans un contexte indissauble dans le C 8.0 et plus tard, l’annulation du type de classe de base est appliquée. Si la classe de base n’est pas annulable (par exemple), `Base`l’argument de type doit être non annulable. Si la classe de base `Base?`est annulée (par exemple), l’argument de type peut être soit un type de référence nul ou non annulable. Le compilateur émet un avertissement si l’argument type est un type de référence nul lorsque la classe de base n’est pas annulable.

La clause `where` peut spécifier que le type est une `class` ou un `struct`. La contrainte `struct` supprime la nécessité de spécifier une contrainte de classe de base de `System.ValueType`. Le type `System.ValueType` ne doit pas être utilisé comme contrainte de classe de base. L’exemple suivant montre les contraintes `class` et `struct` :

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

Dans un contexte in annulable dans le C `class` 8.0 et plus tard, la contrainte exige qu’un type soit un type de référence non annulable. Pour permettre les types de `class?` référence in annulables, utilisez la contrainte, qui permet à la fois les types de référence nuls et non annulables.

La `where` clause peut `notnull` inclure la contrainte. La `notnull` contrainte limite le paramètre de type à des types non annulables. Ce type peut être un [type de valeur](../builtin-types/value-types.md) ou un type de référence non annulable. La `notnull` contrainte est disponible à partir de C 8.0 pour le code compilé dans un [ `nullable enable` contexte](../../nullable-references.md#nullable-contexts). Contrairement à d’autres contraintes, `notnull` si un argument type viole la contrainte, le compilateur génère un avertissement au lieu d’une erreur. Les avertissements ne `nullable enable` sont générés que dans un contexte.

> [!IMPORTANT]
> Les déclarations génériques qui incluent la `notnull` contrainte peuvent être utilisées dans un contexte inouigne, mais le compilateur n’applique pas la contrainte.

[!code-csharp[using the nonnull constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#NotNull)]

La clause `where` peut aussi inclure une contrainte `unmanaged`. La contrainte `unmanaged` limite le paramètre de type aux types connus sous le nom de [types non managés](../builtin-types/unmanaged-types.md). La contrainte `unmanaged` facilite l’écriture de code interop de bas niveau en C#. Cette contrainte permet des routines réutilisables sur tous les types non managés. La contrainte `unmanaged` ne peut pas être combinée avec la contrainte `class` ou `struct`. La contrainte `unmanaged` exige que le type doit être un `struct` :

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

La clause `where` peut également inclure une contrainte de constructeur, `new()`. Cette contrainte permet de créer une instance d’un paramètre de type à l’aide de l’opérateur `new`. La [nouvelle () contrainte](new-constraint.md) permet au compilateur de savoir que tout argument de type fourni doit avoir un constructeur sans paramètres accessible. Par exemple :

[!code-csharp[using the new constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

La contrainte `new()` apparaît en dernier dans la clause `where`. La contrainte `new()` ne peut pas être combinée avec les contraintes `struct` ou `unmanaged`. Tous les types répondant à ces contraintes doivent avoir un constructeur sans paramètre accessible, ce qui rend la contrainte `new()` redondante.

Avec plusieurs paramètres de type, utilisez une clause `where` pour chaque paramètre de type, par exemple :

[!code-csharp[using multiple where constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

Vous pouvez également joindre des contraintes aux paramètres de type des méthodes génériques, comme montré dans l’exemple suivant :

[!code-csharp[where constraints with generic methods](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

Notez que la syntaxe décrivant les contraintes de paramètre de type sur les délégués est la même que celle des méthodes :

[!code-csharp[where constraints with generic methods](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

Pour plus d’informations sur les délégués génériques, consultez [Délégués génériques](../../programming-guide/generics/generic-delegates.md).

Pour plus d’informations sur la syntaxe et l’utilisation de contraintes, consultez [Contraintes sur les paramètres de type](../../programming-guide/generics/constraints-on-type-parameters.md).

## <a name="c-language-specification"></a>spécification du langage C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Référence C](../index.md)
- [Guide de programmation CMD](../../programming-guide/index.md)
- [Introduction aux génériques](../../programming-guide/generics/index.md)
- [nouvelle contrainte](./new-constraint.md)
- [Contraintes sur les paramètres de type](../../programming-guide/generics/constraints-on-type-parameters.md)
