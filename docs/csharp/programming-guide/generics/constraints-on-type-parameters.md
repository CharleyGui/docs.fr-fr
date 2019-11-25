---
title: Contraintes sur les paramètres de type - Guide de programmation C#
ms.custom: seodec18
ms.date: 04/12/2018
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
ms.openlocfilehash: d05307735506db0f0e4abab067334e4f0466ee6a
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204641"
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a>Contraintes sur les paramètres de type (Guide de programmation C#)

Les contraintes informent le compilateur sur les fonctionnalités que doit avoir un argument de type. Sans contrainte, l’argument de type peut être n’importe quel type. Le compilateur peut seulement deviner les membres de <xref:System.Object?displayProperty=nameWithType>, qui est la classe de base par excellence de tous les types .NET. Pour plus d’informations, consultez [Pourquoi utiliser des contraintes](#why-use-constraints). Si le code client essaie d’instancier votre classe à l’aide d’un type qui n’est pas autorisé par une contrainte, il en résulte une erreur de compilation. Les contraintes sont spécifiées à l’aide du mot clé contextuel `where`. Le tableau suivant liste les sept types de contrainte :

|Contrainte|Description|
|----------------|-----------------|
|`where T : struct`|The type argument must be a non-nullable value type. For information about nullable value types, see [Nullable value types](../../language-reference/builtin-types/nullable-value-types.md). Because all value types have an accessible parameterless constructor, the `struct` constraint implies the `new()` constraint and can't be combined with the `new()` constraint. You also cannot combine the `struct` constraint with the `unmanaged` constraint.|
|`where T : class`|L’argument de type doit être un type référence. Cette contrainte s’applique également à tous les types de classe, d’interface, de délégué ou de tableau.|
|`where T : notnull`|The type argument must be a non-nullable type. The argument can be a non-nullable reference type in C# 8.0 or later, or a not nullable value type. Cette contrainte s’applique également à tous les types de classe, d’interface, de délégué ou de tableau.|
|`where T : unmanaged`|The type argument must be a non-nullable [unmanaged type](../../language-reference/builtin-types/unmanaged-types.md). The `unmanaged` constraint implies the `struct` constraint and can't be combined with either the `struct` or `new()` constraints.|
|`where T : new()`|L’argument de type doit avoir un constructeur sans paramètre public. Quand vous utilisez la contrainte `new()` avec d’autres contraintes, elle doit être spécifiée en dernier. The `new()` constraint can't be combined with the `struct` and `unmanaged` constraints.|
|`where T :` *\<nom_classe_de_base>*|L’argument de type doit être la classe de base spécifiée ou en dériver.|
|`where T :` *\<nom_interface>*|L’argument de type doit être ou implémenter l’interface spécifiée. Plusieurs contraintes d’interface peuvent être spécifiées. L’interface qui impose les contraintes peut également être générique.|
|`where T : U`|L’argument de type fourni pour T doit être l’argument fourni pour U ou en dériver.|

## <a name="why-use-constraints"></a>Pourquoi utiliser des contraintes

En limitant le paramètre de type, vous augmentez le nombre d’opérations et d’appels de méthode autorisés au niveau de celui pris en charge par le type de contrainte et tous les types dans sa hiérarchie d’héritage. When you design generic classes or methods, if you'll be performing any operation on the generic members beyond simple assignment or calling any methods not supported by <xref:System.Object?displayProperty=nameWithType>, you'll have to apply constraints to the type parameter. Par exemple, la contrainte de classe de base indique au compilateur que seuls les objets de ce type ou dérivés de ce type seront utilisés comme arguments de type. Une fois que le compilateur a cette garantie, il peut autoriser les méthodes de ce type à être appelées dans la classe générique. L’exemple de code suivant illustre la fonctionnalité que vous pouvez ajouter à la classe `GenericList<T>` (dans [Introduction aux génériques](../../../standard/generics/index.md)) en appliquant une contrainte de classe de base.

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#9)]

La contrainte permet à la classe générique d’utiliser la propriété `Employee.Name`. La contrainte spécifie que tous les éléments de type `T` sont soit un objet `Employee`, soit un objet qui hérite de `Employee`, et rien d’autre.

Plusieurs contraintes peuvent être appliquées au même paramètre de type, et les contraintes elles-mêmes peuvent être des types génériques, comme suit :

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#10)]

En appliquant la contrainte `where T : class`, évitez d’utiliser les opérateurs `==` et `!=` sur le paramètre de type, car ces opérateurs testent uniquement l’identité des références, et non l’égalité des valeurs. Ce comportement se produit même si ces opérateurs sont surchargés dans un type qui est utilisé comme argument. Le code suivant illustre ce point ; la sortie a la valeur false même si la classe <xref:System.String> surcharge l’opérateur `==`.

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#11)]

The compiler only knows that `T` is a reference type at compile time and must use the default operators that are valid for all reference types. Si vous devez tester l’égalité des valeurs, il est recommandé d’appliquer également la contrainte `where T : IEquatable<T>` ou `where T : IComparable<T>` et d’implémenter l’interface dans toute classe qui sera utilisée pour construire la classe générique.

## <a name="constraining-multiple-parameters"></a>Utilisation de contraintes dans plusieurs paramètres

Vous pouvez appliquer des contraintes à plusieurs paramètres et plusieurs contraintes à un seul paramètre, comme indiqué dans l’exemple suivant :

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#12)]

## <a name="unbounded-type-parameters"></a>Paramètres de type unbounded

 Les paramètres de type qui n’ont aucune contrainte, tels que T dans la classe publique `SampleClass<T>{}`, sont appelés paramètres de type unbounded. Les paramètres de type unbounded obéissent aux règles suivantes :

- The `!=` and `==` operators can't be used because there's no guarantee that the concrete type argument will support these operators.
- Ils peuvent être convertis vers et depuis `System.Object` ou être explicitement convertis vers tout type d’interface.
- Vous pouvez les comparer à [null](../../language-reference/keywords/null.md). Si un paramètre unbounded est comparé à `null`, la comparaison retourne toujours la valeur false si l’argument de type est un type valeur.

## <a name="type-parameters-as-constraints"></a>Paramètres de type en tant que contraintes

L’utilisation d’un paramètre de type générique comme contrainte est utile quand une fonction membre dotée de son propre paramètre de type doit contraindre ce paramètre au paramètre du type conteneur, comme le montre l’exemple suivant :

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#13)]

Dans l’exemple précédent, `T` est une contrainte de type dans le contexte de la méthode `Add` et un paramètre de type unbounded dans le contexte de la classe `List`.

Les paramètres de type peuvent également être utilisés comme contraintes dans les définitions de classes génériques. Le paramètre de type doit être déclaré entre crochets pointus, ainsi que tous les autres paramètres de type :

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#14)]

L’utilité des paramètres de type en tant que contraintes avec les classes génériques est limitée, car le compilateur ne peut rien deviner à propos du paramètre de type en dehors du fait qu’il dérive de `System.Object`. Utilisez des paramètres de type en tant que contraintes sur les classes génériques dans les scénarios dans lesquels vous souhaitez mettre en application une relation d’héritage entre deux paramètres de type.

## <a name="notnull-constraint"></a>NotNull constraint

Beginning with C# 8.0, you can use the `notnull` constraint to specify that the type argument must be a non-nullable value type or non-nullable reference type. The `notnull` constraint can only be used in a `nullable enable` context. The compiler generates a warning if you add the `notnull` constraint in a nullable oblivious context. 

Unlike other constraints, when a type argument violates the `notnull` constraint, the compiler generates a warning when that code is compiled in a `nullable enable` context. If the code is compiled in a nullable oblivious context, the compiler doesn't generate any warnings or errors.

## <a name="unmanaged-constraint"></a>Contrainte non managée

Beginning with C# 7.3, you can use the `unmanaged` constraint to specify that the type parameter must be a non-nullable [unmanaged type](../../language-reference/builtin-types/unmanaged-types.md). La contrainte `unmanaged` vous permet d’écrire des routines réutilisables à appliquer aux types qui peuvent être manipulés comme blocs de mémoire, comme illustré dans l’exemple suivant :

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#15)]

La méthode précédente doit être compilée dans un contexte `unsafe`, car elle utilise l’opérateur `sizeof` sur un type qui n’est pas connu pour être un type intégré. Sans la contrainte `unmanaged`, l’opérateur `sizeof` n’est pas disponible.

The `unmanaged` constraint implies the `struct` constraint and can't be combined with it. Because the `struct` constraint implies the `new()` constraint, the `unmanaged` constraint can't be combined with the `new()` constraint as well.

## <a name="delegate-constraints"></a>Contraintes de délégué

À partir de C# 7.3, vous pouvez aussi utiliser <xref:System.Delegate?displayProperty=nameWithType> ou <xref:System.MulticastDelegate?displayProperty=nameWithType> comme contrainte de classe de base. Le CLR a toujours autorisé cette contrainte, contrairement au langage C#. La contrainte `System.Delegate` vous permet d’écrire du code qui fonctionne avec les délégués en mode type sécurisé. The following code defines an extension method that combines two delegates provided they're the same type:

[!code-csharp[using the delegate constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#16)]

Vous pouvez utiliser la méthode ci-dessus pour combiner des délégués qui sont du même type :

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#17)]

Si vous supprimez les commentaires de la dernière ligne, il ne sera pas compilé. Both `first` and `test` are delegate types, but they're different delegate types.

## <a name="enum-constraints"></a>Contraintes d’enum

À compter de C# 7.3, vous pouvez également spécifier le type <xref:System.Enum?displayProperty=nameWithType> comme contrainte de classe de base. Le CLR a toujours autorisé cette contrainte, contrairement au langage C#. Les génériques utilisant `System.Enum` fournissent une programmation de type sécurisé aux résultats de cache issus de l’utilisation de méthodes statiques dans `System.Enum`. L’exemple suivant recherche toutes les valeurs valides d’un type enum, puis génère un dictionnaire qui mappe ces valeurs à sa représentation sous forme de chaîne.

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#18)]

Les méthodes utilisées font appel à la réflexion, ce qui a des implications en termes de performances. Vous pouvez appeler cette méthode pour générer une collection qui est mise en cache et réutilisée, plutôt que de répéter les appels qui nécessitent la réflexion.

Vous pouvez l’utiliser comme montré dans l’exemple suivant pour créer un enum et générer un dictionnaire de ses valeurs et de ses noms :

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#19)]

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#20)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Collections.Generic>
- [Guide de programmation C#](../index.md)
- [Introduction aux génériques](./index.md)
- [Classes génériques](./generic-classes.md)
- [new, contrainte](../../language-reference/keywords/new-constraint.md)
