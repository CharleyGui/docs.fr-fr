---
title: Types de tuple-référence C#
description: 'En savoir plus sur les tuples C# : structures de données légères que vous pouvez utiliser pour regrouper des éléments de données faiblement liés'
ms.date: 07/09/2020
helpviewer_keywords:
- value tuples [C#]
ms.openlocfilehash: d996c7afecba1b58bfd8337fa444fd71790dd482
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471770"
---
# <a name="tuple-types-c-reference"></a>Types de tuples (référence C#)

Disponible en C# 7,0 et versions ultérieures, la fonctionnalité de *tuples* fournit une syntaxe concise pour regrouper plusieurs éléments de données dans une structure de données légère. L’exemple suivant montre comment vous pouvez déclarer une variable de tuple, l’initialiser et accéder à ses membres de données :

[!code-csharp-interactive[tuple intro](snippets/shared/ValueTuples.cs#Introduction)]

Comme le montre l’exemple précédent, pour définir un type de tuple, vous spécifiez les types de tous ses membres de données et, éventuellement, les [noms de champs](#tuple-field-names). Vous ne pouvez pas définir de méthodes dans un type de tuple, mais vous pouvez utiliser les méthodes fournies par .NET, comme le montre l’exemple suivant :

[!code-csharp-interactive[tuple methods](snippets/shared/ValueTuples.cs#MethodOnTuples)]

À compter de C# 7,3, les types de tuple prennent en charge les [opérateurs d’égalité](../operators/equality-operators.md) `==` et `!=` . Pour plus d’informations, consultez la section [égalité des tuples](#tuple-equality) .

Les types de tuples sont des [types valeur](value-types.md); les éléments de tuple sont des champs publics. Cela rend les types valeur *mutable* de tuples.

> [!NOTE]
> La fonctionnalité des tuples requiert le <xref:System.ValueTuple?displayProperty=nameWithType> type et les types génériques associés (par exemple, <xref:System.ValueTuple%602?displayProperty=nameWithType> ), qui sont disponibles dans .net Core et .NET Framework 4,7 et versions ultérieures. Pour utiliser des tuples dans un projet qui cible .NET Framework 4.6.2 ou version antérieure, ajoutez le package NuGet [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) au projet.

Vous pouvez définir des tuples avec un grand nombre d’éléments arbitraires :

[!code-csharp-interactive[large tuple](snippets/shared/ValueTuples.cs#LargeTuple)]

## <a name="use-cases-of-tuples"></a>Cas d’usage de tuples

L’un des cas d’utilisation les plus courants de tuples est le type de retour de la méthode. Autrement dit, au lieu de définir des [ `out` paramètres de méthode](../keywords/out-parameter-modifier.md), vous pouvez regrouper les résultats de méthode dans un type de retour de tuple, comme le montre l’exemple suivant :

[!code-csharp-interactive[multiple method outputs](snippets/shared/ValueTuples.cs#MultipleReturns)]

Comme le montre l’exemple précédent, vous pouvez utiliser l’instance de tuple retournée directement ou la [décomposer](#tuple-assignment-and-deconstruction) dans des variables distinctes.

Vous pouvez également utiliser des types de tuples au lieu de [types anonymes](../../programming-guide/classes-and-structs/anonymous-types.md). par exemple, dans les requêtes LINQ. Pour plus d’informations, consultez [choix entre les types de tuples et anonymes](../../../standard/base-types/choosing-between-anonymous-and-tuple.md).

En général, vous utilisez des tuples pour regrouper des éléments de données faiblement liés. Cela est généralement utile dans les méthodes utilitaires privées et internes. Dans le cas d’une API publique, envisagez de définir une [classe](../keywords/class.md) ou un type de [structure](struct.md) .

## <a name="tuple-field-names"></a>Noms de champs de Tuple

Vous pouvez spécifier explicitement les noms des champs de tuple dans une expression d’initialisation de tuple ou dans la définition d’un type de tuple, comme le montre l’exemple suivant :

[!code-csharp-interactive[explicit field names](snippets/shared/ValueTuples.cs#ExplicitFieldNames)]

À compter de C# 7,1, si vous ne spécifiez pas de nom de champ, il peut être déduit à partir du nom de la variable correspondante dans une expression d’initialisation de tuple, comme le montre l’exemple suivant :

[!code-csharp-interactive[inferred field names](snippets/shared/ValueTuples.cs#InferFieldNames)]

C’est ce que l’on appelle des initialiseurs de projection de Tuple. Le nom d’une variable n’est pas projeté sur un nom de champ de tuple dans les cas suivants :

- Le nom du candidat est un nom de membre d’un type de tuple, par exemple,, `Item3` `ToString` ou `Rest` .
- Le nom du candidat est un doublon d’un autre nom de champ de tuple, explicite ou implicite.

Dans ce cas, vous spécifiez explicitement le nom d’un champ ou vous accédez à un champ par son nom par défaut.

Les noms par défaut des champs de tuple sont `Item1` , `Item2` , `Item3` et ainsi de suite. Vous pouvez toujours utiliser le nom par défaut d’un champ, même lorsqu’un nom de champ est spécifié de manière explicite ou déduite, comme le montre l’exemple suivant :

[!code-csharp-interactive[default field names](snippets/shared/ValueTuples.cs#DefaultFieldNames)]

Les [comparaisons d’égalité](#tuple-equality) des tuples et [des tuples](#tuple-assignment-and-deconstruction) ne prennent pas en compte les noms de champs.

Au moment de la compilation, le compilateur remplace les noms de champs non par défaut par les noms par défaut correspondants. Par conséquent, les noms de champs explicitement spécifiés ou inférés ne sont pas disponibles au moment de l’exécution.

## <a name="tuple-assignment-and-deconstruction"></a>Assignation et déconstruction de Tuple

C# prend en charge l’assignation entre les types tuple qui satisfont les deux conditions suivantes :

- les deux types de tuples ont le même nombre d’éléments
- pour chaque position de tuple, le type de l’élément de tuple de droite est le même que ou implicitement convertible en type de l’élément de tuple de gauche correspondant

Les valeurs d’éléments tuples sont assignées à la suite de l’ordre des éléments de Tuple. Les noms des champs de tuple sont ignorés et non assignés, comme le montre l’exemple suivant :

[!code-csharp-interactive[tuple assignment](snippets/shared/ValueTuples.cs#Assignment)]

Vous pouvez également utiliser l’opérateur `=` d’assignation pour *déconstruire* une instance de tuple dans des variables distinctes. Pour ce faire, vous pouvez procéder de l’une des façons suivantes :

- Déclarez explicitement le type de chaque variable à l’intérieur des parenthèses :

  [!code-csharp-interactive[specify types of variables](snippets/shared/ValueTuples.cs#DeconstructExplicit)]

- Utilisez le `var` mot clé en dehors des parenthèses pour déclarer les variables implicitement typées et laisser le compilateur déduire leurs types :

  [!code-csharp-interactive[implicitly typed variables](snippets/shared/ValueTuples.cs#DeconstructVar)]

- Utiliser des variables existantes :

  [!code-csharp-interactive[existing variables](snippets/shared/ValueTuples.cs#DeconstructExisting)]

Pour plus d’informations sur la déconstruction de tuples et d’autres types, consultez déconstruction de [tuples et d’autres types](../../deconstruct.md).

## <a name="tuple-equality"></a>Égalité des tuples

À compter de C# 7.3, les types tuple prennent en charge les opérateurs `==` et `!=`. Ces opérateurs comparent les membres de l’opérande de gauche avec les membres correspondants de l’opérande de droite suivant l’ordre des éléments de Tuple.

[!code-csharp-interactive[tuple equality](snippets/shared/ValueTuples.cs#TupleEquality)]

Comme le montre l’exemple précédent, `==` les `!=` opérations et ne prennent pas en compte les noms de champs de Tuple.

Deux tuples sont comparables lorsque les deux conditions suivantes sont satisfaites :

- Les deux tuples ont le même nombre d’éléments. Par exemple, `t1 != t2` ne compile pas si `t1` et `t2` ont un nombre d’éléments différent.
- Pour chaque position de tuple, les éléments correspondants des opérandes de tuple de gauche et de droite sont comparables aux `==` opérateurs et `!=` . Par exemple, `(1, (2, 3)) == ((1, 2), 3)` ne se compile `1` pas, car n’est pas comparable à `(1, 2)` .

Les `==` `!=` opérateurs et comparent les tuples en mode court-circuit. Autrement dit, une opération s’arrête dès qu’elle rencontre une paire d’éléments non égaux ou atteint les terminaisons des tuples. Toutefois, avant toute comparaison, *tous les* éléments tuples sont évalués, comme le montre l’exemple suivant :

[!code-csharp-interactive[tuple element evaluation](snippets/shared/ValueTuples.cs#TupleEvaluationForEquality)]

## <a name="tuples-as-out-parameters"></a>Tuples en tant que paramètres de sortie

En règle générale, vous refactorisez une méthode qui a des [ `out` paramètres](../keywords/out-parameter-modifier.md) dans une méthode qui retourne un tuple. Toutefois, il existe des cas dans lesquels un `out` paramètre peut être de type Tuple. L’exemple suivant montre comment utiliser des tuples en tant que `out` Paramètres :

[!code-csharp-interactive[tuple as out parameter](snippets/shared/ValueTuples.cs#TupleAsOutParameter)]

## <a name="tuples-vs-systemtuple"></a>Tuples et `System.Tuple`

Les tuples C#, qui sont sauvegardés par les <xref:System.ValueTuple?displayProperty=nameWithType> types, sont différents des tuples représentés par les <xref:System.Tuple?displayProperty=nameWithType> types. Les principales différences sont les suivantes :

- `ValueTuple` les types sont des [types valeur](value-types.md). `Tuple` les types sont des [types référence](../keywords/reference-types.md).
- `ValueTuple` les types sont mutables. `Tuple` les types sont immuables.
- Les membres de données de `ValueTuple` types sont des champs. Les membres de données de `Tuple` types sont des propriétés.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les notes de la proposition de fonctionnalités suivantes :

- [Déduire les noms de tuples (également appelés initialiseurs de projection de Tuple)](~/_csharplang/proposals/csharp-7.1/infer-tuple-names.md)
- [Prise en charge pour `==` et `!=` sur les types de Tuple](~/_csharplang/proposals/csharp-7.3/tuple-equality.md)

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Types de valeur](value-types.md)
- [Choix entre les types de tuples et anonymes](../../../standard/base-types/choosing-between-anonymous-and-tuple.md)
- <xref:System.ValueTuple?displayProperty=nameWithType>
