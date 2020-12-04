---
title: Contraintes sur les paramètres de type - Guide de programmation C#
description: En savoir plus sur les contraintes sur les paramètres de type. Les contraintes indiquent au compilateur les fonctionnalités que doit avoir un argument de type.
ms.date: 04/12/2018
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
ms.openlocfilehash: 8230dfed11bb4ba21e922827cc1a525ce45ba3e5
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599113"
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a>Contraintes sur les paramètres de type (Guide de programmation C#)

Les contraintes informent le compilateur sur les fonctionnalités que doit avoir un argument de type. Sans contrainte, l’argument de type peut être n’importe quel type. Le compilateur peut seulement deviner les membres de <xref:System.Object?displayProperty=nameWithType>, qui est la classe de base par excellence de tous les types .NET. Pour plus d’informations, consultez [Pourquoi utiliser des contraintes](#why-use-constraints). Si le code client utilise un type qui ne satisfait pas une contrainte, le compilateur émet une erreur. Les contraintes sont spécifiées à l’aide du mot clé contextuel `where`. Le tableau suivant répertorie les différents types de contraintes :

|Contrainte|Description|
|----------------|-----------------|
|`where T : struct`|L’argument de type doit être un [type valeur](../../language-reference/builtin-types/value-types.md)n’acceptant pas les valeurs NULL. Pour plus d’informations sur les types valeur Nullable, consultez [types valeur Nullable](../../language-reference/builtin-types/nullable-value-types.md). Étant donné que tous les types valeur ont un constructeur sans paramètre accessible, la `struct` contrainte implique la `new()` contrainte et ne peut pas être combinée avec la `new()` contrainte. Vous ne pouvez pas associer la `struct` contrainte à la `unmanaged` contrainte.|
|`where T : class`|L’argument de type doit être un type référence. Cette contrainte s’applique également à tous les types de classe, d’interface, de délégué ou de tableau. Dans un contexte Nullable en C# 8,0 ou une version ultérieure, `T` doit être un type de référence non Nullable. |
|`where T : class?`|L’argument de type doit être un type référence, Nullable ou non Nullable. Cette contrainte s’applique également à tous les types de classe, d’interface, de délégué ou de tableau.|
|`where T : notnull`|L’argument de type doit être un type non Nullable. L’argument peut être un type référence non Nullable en C# 8,0 ou version ultérieure, ou un type valeur qui n’autorise pas les valeurs NULL. |
|`where T : unmanaged`|L’argument de type doit être un type non [managé](../../language-reference/builtin-types/unmanaged-types.md)qui n’accepte pas les valeurs NULL. La `unmanaged` contrainte implique la `struct` contrainte et ne peut pas être combinée avec `struct` les `new()` contraintes ou.|
|`where T : new()`|L’argument de type doit avoir un constructeur sans paramètre public. Quand vous utilisez la contrainte `new()` avec d’autres contraintes, elle doit être spécifiée en dernier. La `new()` contrainte ne peut pas être combinée avec les `struct` `unmanaged` contraintes et.|
|`where T :` *\<base class name>*|L’argument de type doit être la classe de base spécifiée ou en dériver. Dans un contexte Nullable en C# 8,0 et versions ultérieures, `T` doit être un type de référence non Nullable dérivé de la classe de base spécifiée. |
|`where T :` *\<base class name>?*|L’argument de type doit être la classe de base spécifiée ou en dériver. Dans un contexte Nullable en C# 8,0 et versions ultérieures, `T` peut être un type Nullable ou non Nullable dérivé de la classe de base spécifiée. |
|`where T :` *\<interface name>*|L’argument de type doit être ou implémenter l’interface spécifiée. Plusieurs contraintes d’interface peuvent être spécifiées. L’interface qui impose les contraintes peut également être générique. Dans un contexte Nullable en C# 8,0 et versions ultérieures, `T` doit être un type non Nullable qui implémente l’interface spécifiée.|
|`where T :` *\<interface name>?*|L’argument de type doit être ou implémenter l’interface spécifiée. Plusieurs contraintes d’interface peuvent être spécifiées. L’interface qui impose les contraintes peut également être générique. Dans un contexte Nullable en C# 8,0, `T` peut être un type de référence Nullable, un type de référence non Nullable ou un type valeur. `T` n’est pas un type valeur Nullable.|
|`where T : U`|L’argument de type fourni pour `T` doit être ou dériver de l’argument fourni pour `U` . Dans un contexte Nullable, si `U` est un type référence qui n’accepte pas les valeurs NULL, `T` doit être un type référence non Nullable. Si `U` est un type de référence Nullable, `T` peut avoir la valeur null ou n’accepte pas les valeurs NULL. |

## <a name="why-use-constraints"></a>Pourquoi utiliser des contraintes

Les contraintes spécifient les capacités et les attentes d’un paramètre de type. La déclaration de ces contraintes signifie que vous pouvez utiliser les opérations et les appels de méthode du type de contrainte. Si votre classe ou méthode générique utilise une opération sur les membres génériques au-delà de l’assignation simple ou l’appel de toute méthode non prise en charge par <xref:System.Object?displayProperty=nameWithType> , vous devez appliquer des contraintes au paramètre de type. Par exemple, la contrainte de classe de base indique au compilateur que seuls les objets de ce type ou dérivés de ce type seront utilisés comme arguments de type. Une fois que le compilateur a cette garantie, il peut autoriser les méthodes de ce type à être appelées dans la classe générique. L’exemple de code suivant illustre la fonctionnalité que vous pouvez ajouter à la classe `GenericList<T>` (dans [Introduction aux génériques](../../../standard/generics/index.md)) en appliquant une contrainte de classe de base.

[!code-csharp[using the class and struct constraints](snippets/GenericWhereConstraints.cs#9)]

La contrainte permet à la classe générique d’utiliser la propriété `Employee.Name`. La contrainte spécifie que tous les éléments de type `T` sont soit un objet `Employee`, soit un objet qui hérite de `Employee`, et rien d’autre.

Plusieurs contraintes peuvent être appliquées au même paramètre de type, et les contraintes elles-mêmes peuvent être des types génériques, comme suit :

[!code-csharp[using the class and struct constraints](snippets/GenericWhereConstraints.cs#10)]

En appliquant la contrainte `where T : class`, évitez d’utiliser les opérateurs `==` et `!=` sur le paramètre de type, car ces opérateurs testent uniquement l’identité des références, et non l’égalité des valeurs. Ce comportement se produit même si ces opérateurs sont surchargés dans un type qui est utilisé comme argument. Le code suivant illustre ce point ; la sortie a la valeur false même si la classe <xref:System.String> surcharge l’opérateur `==`.

[!code-csharp[using the class and struct constraints](snippets/GenericWhereConstraints.cs#11)]

Le compilateur sait uniquement que `T` est un type référence au moment de la compilation et doit utiliser les opérateurs par défaut qui sont valides pour tous les types référence. Si vous devez tester l’égalité des valeurs, il est recommandé d’appliquer également la contrainte `where T : IEquatable<T>` ou `where T : IComparable<T>` et d’implémenter l’interface dans toute classe qui sera utilisée pour construire la classe générique.

## <a name="constraining-multiple-parameters"></a>Utilisation de contraintes dans plusieurs paramètres

Vous pouvez appliquer des contraintes à plusieurs paramètres et plusieurs contraintes à un seul paramètre, comme indiqué dans l’exemple suivant :

[!code-csharp[using the class and struct constraints](snippets/GenericWhereConstraints.cs#12)]

## <a name="unbounded-type-parameters"></a>Paramètres de type unbounded

 Les paramètres de type qui n’ont aucune contrainte, tels que T dans la classe publique `SampleClass<T>{}`, sont appelés paramètres de type unbounded. Les paramètres de type unbounded obéissent aux règles suivantes :

- Les `!=` `==` opérateurs et ne peuvent pas être utilisés, car il n’y a aucune garantie que l’argument de type concret prendra en charge ces opérateurs.
- Ils peuvent être convertis vers et depuis `System.Object` ou être explicitement convertis vers tout type d’interface.
- Vous pouvez les comparer à [null](../../language-reference/keywords/null.md). Si un paramètre unbounded est comparé à `null`, la comparaison retourne toujours la valeur false si l’argument de type est un type valeur.

## <a name="type-parameters-as-constraints"></a>Paramètres de type en tant que contraintes

L’utilisation d’un paramètre de type générique comme contrainte est utile quand une fonction membre dotée de son propre paramètre de type doit contraindre ce paramètre au paramètre du type conteneur, comme le montre l’exemple suivant :

[!code-csharp[using the class and struct constraints](snippets/GenericWhereConstraints.cs#13)]

Dans l’exemple précédent, `T` est une contrainte de type dans le contexte de la méthode `Add` et un paramètre de type unbounded dans le contexte de la classe `List`.

Les paramètres de type peuvent également être utilisés comme contraintes dans les définitions de classes génériques. Le paramètre de type doit être déclaré entre crochets pointus, ainsi que tous les autres paramètres de type :

[!code-csharp[using the class and struct constraints](snippets/GenericWhereConstraints.cs#14)]

L’utilité des paramètres de type en tant que contraintes avec les classes génériques est limitée, car le compilateur ne peut rien deviner à propos du paramètre de type en dehors du fait qu’il dérive de `System.Object`. Utilisez des paramètres de type en tant que contraintes sur les classes génériques dans les scénarios dans lesquels vous souhaitez mettre en application une relation d’héritage entre deux paramètres de type.

## <a name="notnull-constraint"></a>Contrainte NotNull

À compter de C# 8,0 dans un contexte Nullable, vous pouvez utiliser la `notnull` contrainte pour spécifier que l’argument de type doit être un type valeur n’acceptant pas les valeurs null ou un type référence non Nullable. La `notnull` contrainte ne peut être utilisée que dans un `nullable enable` contexte. Le compilateur génère un avertissement si vous ajoutez la `notnull` contrainte dans un contexte oublie Nullable.

Contrairement à d’autres contraintes, lorsqu’un argument de type viole la `notnull` contrainte, le compilateur génère un avertissement lorsque ce code est compilé dans un `nullable enable` contexte. Si le code est compilé dans un contexte oublie Nullable, le compilateur ne génère pas d’avertissements ni d’erreurs.

À compter de C# 8,0 dans un contexte Nullable, la `class` contrainte spécifie que l’argument de type doit être un type de référence n’acceptant pas les valeurs NULL. Dans un contexte Nullable, lorsqu’un paramètre de type est un type référence Nullable, le compilateur génère un avertissement.

## <a name="unmanaged-constraint"></a>Contrainte non managée

À compter de C# 7,3, vous pouvez utiliser la `unmanaged` contrainte pour spécifier que le paramètre de type doit être un [type non managé](../../language-reference/builtin-types/unmanaged-types.md)qui n’accepte pas les valeurs NULL. La contrainte `unmanaged` vous permet d’écrire des routines réutilisables à appliquer aux types qui peuvent être manipulés comme blocs de mémoire, comme illustré dans l’exemple suivant :

[!code-csharp[using the unmanaged constraint](snippets/GenericWhereConstraints.cs#15)]

La méthode précédente doit être compilée dans un contexte `unsafe`, car elle utilise l’opérateur `sizeof` sur un type qui n’est pas connu pour être un type intégré. Sans la contrainte `unmanaged`, l’opérateur `sizeof` n’est pas disponible.

La `unmanaged` contrainte implique la `struct` contrainte et ne peut pas être associée à celle-ci. Étant donné que la `struct` contrainte implique la `new()` contrainte, la contrainte `unmanaged` ne peut pas être combinée à la contrainte `new()` .

## <a name="delegate-constraints"></a>Contraintes de délégué

À partir de C# 7.3, vous pouvez aussi utiliser <xref:System.Delegate?displayProperty=nameWithType> ou <xref:System.MulticastDelegate?displayProperty=nameWithType> comme contrainte de classe de base. Le CLR a toujours autorisé cette contrainte, contrairement au langage C#. La contrainte `System.Delegate` vous permet d’écrire du code qui fonctionne avec les délégués en mode type sécurisé. Le code suivant définit une méthode d’extension qui combine deux délégués à condition qu’ils soient du même type :

[!code-csharp[using the delegate constraint](snippets/GenericWhereConstraints.cs#16)]

Vous pouvez utiliser la méthode ci-dessus pour combiner des délégués qui sont du même type :

[!code-csharp[using the unmanaged constraint](snippets/GenericWhereConstraints.cs#17)]

Si vous supprimez les commentaires de la dernière ligne, il ne sera pas compilé. `first`Et `test` sont des types délégués, mais il s’agit de types délégués différents.

## <a name="enum-constraints"></a>Contraintes d’enum

À compter de C# 7.3, vous pouvez également spécifier le type <xref:System.Enum?displayProperty=nameWithType> comme contrainte de classe de base. Le CLR a toujours autorisé cette contrainte, contrairement au langage C#. Les génériques utilisant `System.Enum` fournissent une programmation de type sécurisé aux résultats de cache issus de l’utilisation de méthodes statiques dans `System.Enum`. L’exemple suivant recherche toutes les valeurs valides d’un type enum, puis génère un dictionnaire qui mappe ces valeurs à sa représentation sous forme de chaîne.

[!code-csharp[using the enum constraint](snippets/GenericWhereConstraints.cs#18)]

`Enum.GetValues` et `Enum.GetName` utilisent la réflexion, ce qui a des répercussions sur les performances. Vous pouvez appeler `EnumNamedValues` pour générer une collection qui est mise en cache et réutilisée au lieu de répéter les appels qui requièrent la réflexion.

Vous pouvez l’utiliser comme montré dans l’exemple suivant pour créer un enum et générer un dictionnaire de ses valeurs et de ses noms :

[!code-csharp[enum definition](snippets/GenericWhereConstraints.cs#19)]

[!code-csharp[using the enum constrained method](snippets/GenericWhereConstraints.cs#20)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Collections.Generic>
- [Guide de programmation C#](../index.md)
- [Introduction aux génériques](./index.md)
- [Classes génériques](./generic-classes.md)
- [nouvelle contrainte](../../language-reference/keywords/new-constraint.md)
