---
title: Contraintes sur les paramètres de type - Guide de programmation C#
ms.custom: seodec18
ms.date: 04/12/2018
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
ms.openlocfilehash: bb545d9da73154c237f55809a3a72ff0f121ce1a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253022"
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a>Contraintes sur les paramètres de type (Guide de programmation C#)

Les contraintes informent le compilateur sur les fonctionnalités que doit avoir un argument de type. Sans contrainte, l’argument de type peut être n’importe quel type. Le compilateur peut seulement deviner les membres de <xref:System.Object?displayProperty=nameWithType>, qui est la classe de base par excellence de tous les types .NET. Pour plus d’informations, consultez [Pourquoi utiliser des contraintes](#why-use-constraints). Si le code client essaie d’instancier votre classe à l’aide d’un type qui n’est pas autorisé par une contrainte, il en résulte une erreur de compilation. Les contraintes sont spécifiées à l’aide du mot clé contextuel `where`. Le tableau suivant liste les sept types de contrainte :

|Contrainte|Description|
|----------------|-----------------|
|`where T : struct`|L’argument de type doit être un type valeur. Tout type valeur, excepté <xref:System.Nullable%601>, peut être spécifié. Pour plus d’informations sur les types Nullable en C#, consultez [Types Nullable](../nullable-types/index.md).|
|`where T : class`|L’argument de type doit être un type référence. Cette contrainte s’applique également à tous les types de classe, d’interface, de délégué ou de tableau.|
|`where T : notnull`|L’argument de type doit être un type non Nullable. L’argument peut être un type référence non Nullable dans C# 8,0 ou version ultérieure, ou un type valeur Not Nullable. Cette contrainte s’applique également à tous les types de classe, d’interface, de délégué ou de tableau.|
|`where T : unmanaged`|L’argument de type doit être un [type non managé](../../language-reference/builtin-types/unmanaged-types.md).|
|`where T : new()`|L’argument de type doit avoir un constructeur sans paramètre public. Quand vous utilisez la contrainte `new()` avec d’autres contraintes, elle doit être spécifiée en dernier.|
|`where T :` *\<nom_classe_de_base>*|L’argument de type doit être la classe de base spécifiée ou en dériver.|
|`where T :` *\<nom_interface>*|L’argument de type doit être ou implémenter l’interface spécifiée. Plusieurs contraintes d’interface peuvent être spécifiées. L’interface qui impose les contraintes peut également être générique.|
|`where T : U`|L’argument de type fourni pour T doit être l’argument fourni pour U ou en dériver.|

Certaines contraintes s’excluent mutuellement. Tous les types valeur doivent avoir un constructeur sans paramètre accessible. La `struct` contrainte implique la `new()` contrainte et la `new()` contrainte ne peut pas être combinée `struct` avec la contrainte. La contrainte `unmanaged` implique la contrainte `struct`. La `unmanaged` contrainte ne peut pas être combinée avec `struct` les `new()` contraintes ou.

## <a name="why-use-constraints"></a>Pourquoi utiliser des contraintes

En limitant le paramètre de type, vous augmentez le nombre d’opérations et d’appels de méthode autorisés au niveau de celui pris en charge par le type de contrainte et tous les types dans sa hiérarchie d’héritage. Quand vous concevez des classes ou des méthodes génériques, si vous effectuez une opération sur les membres génériques au-delà de la simple assignation ou que <xref:System.Object?displayProperty=nameWithType>vous appelez des méthodes non prises en charge par, vous devez appliquer des contraintes au paramètre de type. Par exemple, la contrainte de classe de base indique au compilateur que seuls les objets de ce type ou dérivés de ce type seront utilisés comme arguments de type. Une fois que le compilateur a cette garantie, il peut autoriser les méthodes de ce type à être appelées dans la classe générique. L’exemple de code suivant illustre la fonctionnalité que vous pouvez ajouter à la classe `GenericList<T>` (dans [Introduction aux génériques](introduction-to-generics.md)) en appliquant une contrainte de classe de base.

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#9)]

La contrainte permet à la classe générique d’utiliser la propriété `Employee.Name`. La contrainte spécifie que tous les éléments de type `T` sont soit un objet `Employee`, soit un objet qui hérite de `Employee`, et rien d’autre.

Plusieurs contraintes peuvent être appliquées au même paramètre de type, et les contraintes elles-mêmes peuvent être des types génériques, comme suit :

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#10)]

En appliquant la contrainte `where T : class`, évitez d’utiliser les opérateurs `==` et `!=` sur le paramètre de type, car ces opérateurs testent uniquement l’identité des références, et non l’égalité des valeurs. Ce comportement se produit même si ces opérateurs sont surchargés dans un type qui est utilisé comme argument. Le code suivant illustre ce point ; la sortie a la valeur false même si la classe <xref:System.String> surcharge l’opérateur `==`.

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#11)]

Le compilateur sait uniquement que `T` est un type référence au moment de la compilation et doit utiliser les opérateurs par défaut qui sont valides pour tous les types référence. Si vous devez tester l’égalité des valeurs, il est recommandé d’appliquer également la contrainte `where T : IEquatable<T>` ou `where T : IComparable<T>` et d’implémenter l’interface dans toute classe qui sera utilisée pour construire la classe générique.

## <a name="constraining-multiple-parameters"></a>Utilisation de contraintes dans plusieurs paramètres

Vous pouvez appliquer des contraintes à plusieurs paramètres et plusieurs contraintes à un seul paramètre, comme indiqué dans l’exemple suivant :

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#12)]

## <a name="unbounded-type-parameters"></a>Paramètres de type unbounded

 Les paramètres de type qui n’ont aucune contrainte, tels que T dans la classe publique `SampleClass<T>{}`, sont appelés paramètres de type unbounded. Les paramètres de type unbounded obéissent aux règles suivantes :

- Les `!=` opérateurs `==` et ne peuvent pas être utilisés, car il n’y a aucune garantie que l’argument de type concret prendra en charge ces opérateurs.
- Ils peuvent être convertis vers et depuis `System.Object` ou être explicitement convertis vers tout type d’interface.
- Vous pouvez les comparer à [null](../../language-reference/keywords/null.md). Si un paramètre unbounded est comparé à `null`, la comparaison retourne toujours la valeur false si l’argument de type est un type valeur.

## <a name="type-parameters-as-constraints"></a>Paramètres de type en tant que contraintes

L’utilisation d’un paramètre de type générique comme contrainte est utile quand une fonction membre dotée de son propre paramètre de type doit contraindre ce paramètre au paramètre du type conteneur, comme le montre l’exemple suivant :

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#13)]

Dans l’exemple précédent, `T` est une contrainte de type dans le contexte de la méthode `Add` et un paramètre de type unbounded dans le contexte de la classe `List`.

Les paramètres de type peuvent également être utilisés comme contraintes dans les définitions de classes génériques. Le paramètre de type doit être déclaré entre crochets pointus, ainsi que tous les autres paramètres de type :

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#14)]

L’utilité des paramètres de type en tant que contraintes avec les classes génériques est limitée, car le compilateur ne peut rien deviner à propos du paramètre de type en dehors du fait qu’il dérive de `System.Object`. Utilisez des paramètres de type en tant que contraintes sur les classes génériques dans les scénarios dans lesquels vous souhaitez mettre en application une relation d’héritage entre deux paramètres de type.

## <a name="notnull-constraint"></a>Contrainte NotNull

À partir C# de 8,0, vous pouvez utiliser `notnull` la contrainte pour spécifier que l’argument de type doit être un type valeur non Nullable ou un type référence non Nullable. La `notnull` contrainte ne peut être utilisée que dans `nullable enable` un contexte. Le compilateur génère un avertissement si vous ajoutez la `notnull` contrainte dans un contexte oublie Nullable. 

Contrairement à d’autres contraintes, lorsqu’un argument de type `notnull` viole la contrainte, le compilateur génère un avertissement lorsque ce code est `nullable enable` compilé dans un contexte. Si le code est compilé dans un contexte oublie Nullable, le compilateur ne génère pas d’avertissements ni d’erreurs.

## <a name="unmanaged-constraint"></a>Contrainte non managée

À partir de C# 7.3, vous pouvez utiliser la contrainte `unmanaged` pour spécifier que le paramètre de type doit être un [type non managé](../../language-reference/builtin-types/unmanaged-types.md). La contrainte `unmanaged` vous permet d’écrire des routines réutilisables à appliquer aux types qui peuvent être manipulés comme blocs de mémoire, comme illustré dans l’exemple suivant :

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#15)]

La méthode précédente doit être compilée dans un contexte `unsafe`, car elle utilise l’opérateur `sizeof` sur un type qui n’est pas connu pour être un type intégré. Sans la contrainte `unmanaged`, l’opérateur `sizeof` n’est pas disponible.

## <a name="delegate-constraints"></a>Contraintes de délégué

À partir de C# 7.3, vous pouvez aussi utiliser <xref:System.Delegate?displayProperty=nameWithType> ou <xref:System.MulticastDelegate?displayProperty=nameWithType> comme contrainte de classe de base. Le CLR a toujours autorisé cette contrainte, contrairement au langage C#. La contrainte `System.Delegate` vous permet d’écrire du code qui fonctionne avec les délégués en mode type sécurisé. Le code suivant définit une méthode d’extension qui combine deux délégués à condition qu’ils soient du même type :

[!code-csharp[using the delegate constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#16)]

Vous pouvez utiliser la méthode ci-dessus pour combiner des délégués qui sont du même type :

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#17)]

Si vous supprimez les commentaires de la dernière ligne, il ne sera pas compilé. `first` Et`test` sont des types délégués, mais il s’agit de types délégués différents.

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
