---
title: where (contrainte de type générique) - Référence C#
ms.custom: seodec18
ms.date: 04/12/2018
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: 3982c97bc56b42237700343b2572d1bba930bbbd
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422776"
---
# <a name="where-generic-type-constraint-c-reference"></a>where (contrainte de type générique) (Référence C#)

La clause `where` dans une définition générique spécifie des contraintes sur les types qui sont utilisés comme arguments pour les paramètres de type d’un type générique, d’une méthode, d’un délégué ou d’une fonction locale. Les contraintes peuvent spécifier des interfaces ou des classes de base, ou nécessiter un type générique comme référence, valeur ou type non managé. Elles déclarent des fonctionnalités que l’argument de type doit posséder.

Vous pouvez, par exemple, déclarer une classe générique, `MyGenericClass`, de telle sorte que le paramètre de type `T` implémente l’interface <xref:System.IComparable%601> :

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> Pour plus d’informations sur la clause where dans une expression de requête, consultez [where, clause](where-clause.md).

La clause `where` peut également inclure une contrainte de classe de base. La contrainte de classe de base indique qu’un type à utiliser comme argument de type pour ce type générique a la classe spécifiée comme classe de base (ou est la classe de base) à utiliser comme argument de type pour ce type générique. Si la contrainte de classe de base est utilisée, elle doit apparaître avant toute autre contrainte sur ce paramètre de type. Certains types ne sont pas autorisés comme contrainte de classe de base : <xref:System.Object>, <xref:System.Array> et <xref:System.ValueType>. Avant C# 7.3, <xref:System.Enum>, <xref:System.Delegate> et <xref:System.MulticastDelegate> n’étaient pas non plus autorisés comme contraintes de classe de base. L’exemple suivant montre les types qui peuvent maintenant être spécifiés comme classe de base :

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

La clause `where` peut spécifier que le type est une `class` ou un `struct`. La contrainte `struct` supprime la nécessité de spécifier une contrainte de classe de base de `System.ValueType`. Le type `System.ValueType` ne doit pas être utilisé comme contrainte de classe de base. L’exemple suivant montre les contraintes `class` et `struct` :

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

La clause `where` peut aussi inclure une contrainte `unmanaged`. La contrainte `unmanaged` limite le paramètre de type aux types connus sous le nom de **types non managés**. Un **type non managé** est un type qui n’est pas un type référence et ne contient pas de champs de type référence à tous les niveaux d’imbrication. La contrainte `unmanaged` facilite l’écriture de code interop de bas niveau en C#. Cette contrainte permet des routines réutilisables sur tous les types non managés. La contrainte `unmanaged` ne peut pas être combinée avec la contrainte `class` ou `struct`. La contrainte `unmanaged` exige que le type doit être un `struct` :

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

La clause `where` peut également inclure une contrainte de constructeur, `new()`. Cette contrainte permet de créer une instance d’un paramètre de type à l’aide de l’opérateur `new`. La [contrainte new()](new-constraint.md) fait savoir au compilateur que tout argument de type fourni doit avoir un constructeur accessible sans paramètre, ou par défaut. Par exemple :

[!code-csharp[using the new constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

La contrainte `new()` apparaît en dernier dans la clause `where`. La contrainte `new()` ne peut pas être combinée avec les contraintes `struct` ou `unmanaged`. Tous les types répondant à ces contraintes doivent avoir un constructeur sans paramètre accessible, ce qui rend la contrainte `new()` redondante.

Avec plusieurs paramètres de type, utilisez une clause `where` pour chaque paramètre de type, par exemple :

[!code-csharp[using multiple where constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

Vous pouvez également joindre des contraintes aux paramètres de type des méthodes génériques, comme montré dans l’exemple suivant :

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

Notez que la syntaxe décrivant les contraintes de paramètre de type sur les délégués est la même que celle des méthodes :

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

Pour plus d’informations sur les délégués génériques, consultez [Délégués génériques](../../../csharp/programming-guide/generics/generic-delegates.md).

Pour plus d’informations sur la syntaxe et l’utilisation de contraintes, consultez [Contraintes sur les paramètres de type](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).

## <a name="c-language-specification"></a>spécification du langage C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Référence C#](../../../csharp/language-reference/index.md)
- [Guide de programmation C#](../../../csharp/programming-guide/index.md)
- [Introduction aux génériques](../../../csharp/programming-guide/generics/index.md)
- [new, contrainte](../../../csharp/language-reference/keywords/new-constraint.md)
- [Contraintes sur les paramètres de type](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
