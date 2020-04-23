---
title: Nouveautés de C# 7.0 | Guide C#
description: Découvrez les nouvelles fonctionnalités disponibles dans la version 7.0 du langage C#.
ms.date: 02/20/2019
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: 1291de95b88b3de16fb94fb376fb4153dd4a5862
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102669"
---
# <a name="whats-new-in-c-70"></a>Nouveautés de C# 7.0

C# 7.0 ajoute un certain nombre de nouvelles fonctionnalités au langage C# :

- [`out`Variables](#out-variables)
  - Vous pouvez déclarer des valeurs `out` inline comme arguments de la méthode dans laquelle elles sont utilisées.
- [Tuples](#tuples)
  - Vous pouvez créer des types légers et sans nom qui contiennent plusieurs champs publics. Les compilateurs et les outils de l’IDE comprennent la sémantique de ces types.
- [Éléments ignorés](#discards)
  - Les éléments ignorés sont les variables temporaires en écriture seule utilisées dans les attributions quand vous ne vous souciez pas de la valeur assignée. Ils s’avèrent utiles lors de la déconstruction de tuples et de types définis par l’utilisateur, ainsi que lors de l’appel de méthodes avec des paramètres `out`.
- [Critères spéciaux](#pattern-matching)
  - Vous pouvez créer une logique de branchement basée sur des types arbitraires et les valeurs des membres de ces types.
- [`ref`habitants et les retours](#ref-locals-and-returns)
  - Les valeurs de retour et les variables locales de méthode peuvent être des références à un autre stockage.
- [Fonctions locales](#local-functions)
  - Vous pouvez imbriquer des fonctions dans d’autres fonctions afin de limiter leur portée et leur visibilité.
- [Autres membres expression-bodied](#more-expression-bodied-members)
  - La liste des membres pouvant être créés à l’aide d’expressions s’est allongée.
- [`throw`Expressions](#throw-expressions)
  - Vous pouvez lever des exceptions dans les constructions de code qui n’étaient pas autorisées auparavant, car `throw` était une instruction.
- [Types de retour async généralisés](#generalized-async-return-types)
  - Les méthodes déclarées avec le modificateur `async` peuvent retourner d’autres types en plus de `Task` et de `Task<T>`.
- [Améliorations de la syntaxe littérale numérique](#numeric-literal-syntax-improvements)
  - De nouveaux jetons améliorent la lisibilité des constantes numériques.

Le reste de cet article présente une vue d’ensemble de chaque fonctionnalité. Vous découvrirez la logique de chacune d’elles. Vous allez apprendre leur syntaxe. Vous pouvez explorer ces fonctionnalités dans votre environnement à l’aide de l’outil global `dotnet try` :

1. Installez l’outil global [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup).
1. Clonez le référentiel [dotnet/try-samples](https://github.com/dotnet/try-samples).
1. Définissez le répertoire actuel sur le sous-répertoire *csharp7* pour le référentiel *try-samples*.
1. Exécutez `dotnet try`.

## <a name="out-variables"></a>Variables `out`

La syntaxe existante qui prend en charge les paramètres `out` a été améliorée dans cette version. Vous pouvez désormais déclarer des variables `out` dans la liste d’arguments d’un appel de méthode, au lieu d’écrire une instruction de déclaration distincte :

[!code-csharp[OutVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVariableDeclarations "Out variable declarations")]

Par souci de clarté, vous voulez peut-être spécifier le type de la variable `out`, comme indiqué ci-dessus. Toutefois, le langage prend en charge l’utilisation d’une variable locale implicitement typée :

[!code-csharp[OutVarVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVarVariableDeclarations "Implicitly typed Out variable")]

- Le code est plus facile à lire.
  - Vous déclarez la variable out à l’endroit où vous l’utilisez, et non pas sur une autre ligne au-dessus.
- Il n’est pas nécessaire d’assigner une valeur initiale.
  - En déclarant la variable `out` à l’endroit où elle est utilisée dans un appel de méthode, vous ne pouvez pas l’utiliser accidentellement avant qu’elle soit assignée.

## <a name="tuples"></a>Tuples

C# fournit une syntaxe complète pour les classes et les structs, utilisée pour expliquer l’intention de votre conception. Cependant, cette syntaxe complète nécessite parfois un travail supplémentaire avec peu d’avantages. Vous pouvez souvent écrire des méthodes qui nécessitent une structure simple contenant plusieurs éléments de données. Pour prendre en charge ces scénarios, des *tuples* ont été ajoutées à C#. Les tuples sont des structures de données légères contenant plusieurs champs pour représenter les membres de données.
Les champs ne sont pas validés et vous ne pouvez pas définir vos propres méthodes.

> [!NOTE]
> Les tuples étaient disponibles avant C# 7.0, mais ils n’étaient pas efficaces et n’avaient aucune prise en charge du langage.
> Cela signifiait que les éléments tuples pouvaient uniquement être référencés comme `Item1`, `Item2`, et ainsi de suite. C# 7.0 introduit la prise en charge du langage pour les tuples, ce qui permet d’utiliser des noms sémantiques pour les champs d’un tuple avec de nouveaux types tuple plus efficaces.

Vous pouvez créer un tuple en assignant une valeur à chaque membre et éventuellement, en fournissant des noms sémantiques à chacun des membres du tuple :

[!code-csharp[NamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#NamedTuple "Named tuple")]

Le tuple `namedLetters` contient des champs appelés `Alpha` et `Beta`. Ces noms n’existent qu’au moment de la compilation et ne sont pas conservés par exemple lors de l’inspection du tuple à l’aide de la réflexion lors de l’exécution.

Dans une assignation de tuple, vous pouvez également spécifier les noms des champs dans la partie droite :

[!code-csharp[ImplicitNamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#ImplicitNamedTuple "Implicitly named tuple")]

Dans certains cas, vous pouvez souhaiter décompresser les membres d’un tuple qui ont été retournés à partir d’une méthode.  Pour ce faire, déclarez des variables distinctes pour chacune des valeurs dans le tuple. Cette décompression est appelée *déconstruction* du tuple :

[!code-csharp[CallingWithDeconstructor](~/samples/snippets/csharp/new-in-7/program.cs#CallingWithDeconstructor "Deconstructing a tuple")]

Vous pouvez également fournir une déconstruction similaire pour tout type dans le .NET. Vous écrivez une méthode `Deconstruct` en tant que membre de la classe. Cette méthode `Deconstruct` fournit un ensemble d’arguments `out` pour chacune des propriétés que vous voulez extraire. Prenons la classe `Point` suivante qui fournit une méthode de déconstructeur qui extrait les coordonnées `X` et `Y` :

[!code-csharp[PointWithDeconstruction](~/samples/snippets/csharp/new-in-7/point.cs#PointWithDeconstruction "Point with deconstruction method")]

Vous pouvez extraire les champs individuels en affectant un `Point` à un tuple :

[!code-csharp[DeconstructPoint](~/samples/snippets/csharp/new-in-7/program.cs#DeconstructPoint "Deconstruct a point")]

Vous pouvez approfondir vos connaissances sur les tuples avec [cet article](../tuples.md).

## <a name="discards"></a>Éléments ignorés

Souvent, lors de la déconstruction d’un tuple ou de l’appel d’une méthode avec des paramètres `out`, vous devez définir une variable dont la valeur ne vous importe pas et que vous ne prévoyez pas d’utiliser. C# ajoute la prise en charge des *éléments ignorés* pour gérer ce scénario. Un élément ignoré est une variable en écriture seule dont le nom est `_` (caractère de soulignement) ; vous pouvez assigner toutes les valeurs que vous souhaitez ignorer à la variable unique. Un élément ignoré est semblable à une variable non assignée ; en dehors de l’instruction d’assignation, l’élément ignoré ne peut pas être utilisé dans le code.

Les éléments ignorés sont pris en charge dans les scénarios suivants :

- Lors de la déconstruction de tuples ou de types définis par l’utilisateur.
- Lors d’appels à des méthodes avec des paramètres [out](../language-reference/keywords/out-parameter-modifier.md).
- Dans une opération de critères spéciaux avec les instructions [is](../language-reference/keywords/is.md) et [switch](../language-reference/keywords/switch.md).
- Comme un identificateur autonome quand vous voulez explicitement identifier la valeur d’une assignation comme un élément ignoré.

L’exemple suivant définit une méthode `QueryCityDataForYears` qui retourne un tuple à 6 composants qui contient des données pour une ville au cours de deux années différentes. L’appel de méthode dans l’exemple s’intéresse uniquement à deux valeurs de population retournées par la méthode et traite par conséquent les valeurs restantes dans le tuple comme des éléments ignorés lors de la déconstruction du tuple.

[!code-csharp[Tuple-discard](~/samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Pour plus d’informations, consultez [Éléments ignorés](../discards.md).

## <a name="pattern-matching"></a>Critères spéciaux

Les *critères spéciaux* constituent une fonctionnalité qui vous permet d’implémenter la distribution de méthodes sur des propriétés autres que le type d’un objet. Vous êtes probablement déjà familiarisé avec la distribution de méthodes en fonction du type d’un objet. Dans la programmation orientée objet, les méthodes virtuelles et override fournissent une syntaxe du langage permettant d’implémenter la distribution de méthodes basées sur le type d’un objet. Les classes de base et dérivées offrent des implémentations différentes.
Les expressions de critères spéciaux étendent ce concept de manière à vous permettre d’implémenter facilement des modèles de distribution similaires pour les types et les éléments de données qui ne sont pas liés au moyen d’une hiérarchie d’héritage.

Les critères spéciaux prennent en charge les expressions `is` et les expressions `switch`. L’une ou l’autre permettent d’inspecter un objet et ses propriétés afin de déterminer s’il correspond au modèle recherché. Vous utilisez le mot clé `when` pour spécifier des règles supplémentaires pour le modèle.

L’expression `is` du modèle étend [ `is` l’opérateur](../language-reference/keywords/is.md#pattern-matching-with-is) familier pour interroger un objet sur son type et attribuer le résultat dans une instruction. Le code suivant vérifie si une variable est un `int`, et si tel est le cas, il l’ajoute à la somme actuelle :

```csharp
if (input is int count)
    sum += count;
```

Le petit exemple précédent illustre les améliorations apportées à l’expression `is`. Vous pouvez tester par rapport à des types valeur, ainsi que des types référence, et vous pouvez assigner le résultat de réussite à une nouvelle variable du type correct.

L’expression de correspondance switch a une syntaxe familière, basée sur l’instruction `switch` qui fait déjà partie du langage C#. L’instruction switch mise à jour a plusieurs nouvelles constructions :

- Le type directeur d’une expression `switch` n’est plus limité aux types intégraux, aux types `Enum`, `string` ou à un type nullable correspondant à l’un de ces types. Vous pouvez utiliser n’importe quel type.
- Vous pouvez tester le type de l’expression `switch` dans chaque étiquette `case`. Comme avec l’expression `is`, vous pouvez assigner une nouvelle variable à ce type.
- Vous pouvez ajouter une clause `when` pour tester encore les conditions sur cette variable.
- L’ordre des étiquettes `case` est à présent important. La première branche à faire correspondre est exécutée ; les autres sont ignorées.

Le code suivant illustre ces nouvelles fonctionnalités :

```csharp
public static int SumPositiveNumbers(IEnumerable<object> sequence)
{
    int sum = 0;
    foreach (var i in sequence)
    {
        switch (i)
        {
            case 0:
                break;
            case IEnumerable<int> childSequence:
            {
                foreach(var item in childSequence)
                    sum += (item > 0) ? item : 0;
                break;
            }
            case int n when n > 0:
                sum += n;
                break;
            case null:
                throw new NullReferenceException("Null found in sequence");
            default:
                throw new InvalidOperationException("Unrecognized type");
        }
    }
    return sum;
}
```

- `case 0:` est le modèle de constante classique.
- `case IEnumerable<int> childSequence:` est un modèle de type.
- `case int n when n > 0:` est un modèle de type avec une autre condition `when`.
- `case null:` est le modèle null.
- `default:` est le cas par défaut classique.

Pour plus d’informations sur les critères spéciaux, consultez [Critères spéciaux en C#](../pattern-matching.md).

## <a name="ref-locals-and-returns"></a>Variables locales et retours ref

Cette fonctionnalité active les algorithmes qui utilisent et retournent des références à des variables définies ailleurs. C’est le cas, par exemple, lors de la recherche d’un emplacement unique comportant certaines caractéristiques dans une matrice de grande taille. La méthode suivante retourne une **référence** à ce stockage dans la matrice :

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

Vous pouvez déclarer la valeur de retour en tant que `ref` et modifier cette valeur dans la matrice, comme indiqué dans le code suivant :

[!code-csharp[AssignRefReturn](~/samples/snippets/csharp/new-in-7/Program.cs#AssignRefReturn "Assign ref return")]

Le langage C# a plusieurs règles qui vous protègent contre une mauvaise utilisation des variables locales et des retours `ref` :

- Vous devez ajouter le mot clé `ref` à la signature de méthode et à toutes les instructions `return` dans une méthode.
  - Cela permet de clarifier le retour par référence tout au long de la méthode.
- Un `ref return` peut être assigné à une variable de la valeur ou à une variable `ref`.
  - L’appelant contrôle si la valeur de retour est copiée ou non. L’omission du modificateur `ref` lors de l’assignation de la valeur de retour indique que l’appelant souhaite une copie de la valeur, pas une référence au stockage.
- Vous ne pouvez pas affecter une valeur de retour de méthode standard à une variable locale `ref`.
  - Cela rejette les instructions telles que `ref int i = sequence.Count();`.
- Vous ne pouvez pas retourner un `ref` à une variable dont la durée de vie ne s’étend pas au-delà de l’exécution de la méthode.
  - Cela signifie que vous ne pouvez pas retourner une référence à une variable locale ni une variable avec une étendue similaire.
- Les variables locales et les retours `ref` ne peuvent pas être utilisés avec les méthodes Async.
  - Le compilateur ne peut pas savoir si la variable référencée a été définie à sa valeur finale quand la méthode Async est retournée.

L’ajout de variables locales ref et de retours ref permet d’utiliser des algorithmes qui sont plus efficaces en évitant la copie de valeurs, ou d’effectuer plusieurs fois des opérations de déréférencement.

L’ajout de `ref` à la valeur de retour est une [modification compatible avec la source](version-update-considerations.md#source-compatible-changes). Le code existant est compilé, mais la valeur de retour référencée est copiée lorsqu’elle est assignée. Les appelants doivent mettre à jour le stockage pour la valeur de retour sur une variable locale `ref` afin de stocker la valeur de retour en tant que référence.

Pour plus d'informations, voir l’article [ref, mot clé](../language-reference/keywords/ref.md).

## <a name="local-functions"></a>Fonctions locales

De nombreuses conceptions pour les classes incluent des méthodes qui sont appelées à partir d’un seul emplacement. Ces méthodes privées supplémentaires maintiennent chaque méthode réduite et focalisée. Les *fonctions locales* vous permettent de déclarer des méthodes dans le contexte d’une autre méthode. Il est ainsi plus facile pour les lecteurs de la classe de voir que la méthode locale est appelée uniquement à partir du contexte dans lequel elle a été déclarée.

Il existe deux cas d’utilisation courants pour les fonctions locales : les méthodes iterator publiques et les méthodes async publiques. Ces deux types de méthodes génèrent du code qui signale les erreurs plus tard que ce qu’attendent les programmeurs. Dans les méthodes iterator, toute exception est observée uniquement lors de l’appel de code qui énumère la séquence retournée. Dans les méthodes async, toute exception est observée uniquement quand le `Task` retourné est attendu. L’exemple suivant illustre la séparation entre la validation de paramètres et l’implémentation de l’itérateur à l’aide d’une fonction locale :

[!code-csharp[22_IteratorMethodLocal](~/samples/snippets/csharp/new-in-7/Iterator.cs#IteratorMethodLocal "Iterator method with local function")]

Il est possible d’utiliser la même technique avec les méthodes `async` pour garantir que les exceptions résultant de la validation d’argument sont levées avant le début de la tâche asynchrone :

[!code-csharp[TaskExample](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

> [!NOTE]
> Certaines des conceptions qui sont soutenues par des fonctions locales peuvent également être accomplies en utilisant *des expressions lambda*. Pour plus d’informations, voir [fonctions locales vs expressions lambda](../programming-guide/classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions).

## <a name="more-expression-bodied-members"></a>Autres membres expression-bodied

C# 6 a introduit les [membres expression-bodied](csharp-6.md#expression-bodied-function-members) pour les fonctions membres, ainsi que des propriétés en lecture seule. C# 7.0 développe les membres autorisés pouvant être implémentés comme expressions. Dans C# 7.0, vous pouvez implémenter des *constructeurs*, des *finaliseurs* ainsi que des accesseurs `get` et `set` sur des *propriétés* et des *indexeurs*. Le code suivant présente des exemples de chaque élément :

[!code-csharp[ExpressionBodiedMembers](~/samples/snippets/csharp/new-in-7/expressionmembers.cs#ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> Cet exemple n’a pas besoin de finaliseur, mais il est présenté pour illustrer la syntaxe. Vous ne devez implémenter un finaliseur dans votre classe que si cela est nécessaire pour libérer des ressources non managées. Vous devez également envisager d’utiliser la classe <xref:System.Runtime.InteropServices.SafeHandle> au lieu de gérer directement les ressources non managées.

Ces nouveaux emplacements pour les membres expression-bodied représentent une étape importante pour le langage C# : ces fonctionnalités ont été implémentées par des membres de la communauté travaillant sur le projet open source [Roslyn](https://github.com/dotnet/Roslyn).

La modification d’une méthode en un membre expression-bodied est une [modification compatible binaire](version-update-considerations.md#binary-compatible-changes).

## <a name="throw-expressions"></a>Expressions throw

En C#, `throw` a toujours été une instruction. Étant donné que `throw` est une instruction, et non pas une expression, certaines constructions C# ne pouvaient pas l’utiliser. Il s’agit notamment des expressions conditionnelles, des expressions de fusion null, ainsi que de certaines expressions lambda. L’ajout de membres expression-bodied ajoute des emplacements supplémentaires où les expressions `throw` seraient utiles. Pour que vous puissiez écrire l’une de ces constructions, C 7.0 introduit [*des expressions de lancer*](../language-reference/keywords/throw.md#the-throw-expression).

Cet ajout facilite l’écriture de code davantage basé sur des expressions. Vous n’avez pas besoin d’instructions supplémentaires pour la vérification des erreurs.

## <a name="generalized-async-return-types"></a>Types de retour async généralisés

Le retour d’un objet `Task` à partir de méthodes async peut introduire des goulots d’étranglement au niveau des performances dans certains chemins. `Task` est un type référence. Si vous l’utilisez, vous allouez donc un objet. Dans les cas où une méthode déclarée avec le modificateur `async` retourne un résultat mis en cache, ou si elle s’exécute de manière synchrone, le coût en termes de temps induit par les allocations supplémentaires peut s’avérer significatif dans les sections de code critiques pour les performances. Cela peut devenir coûteux si ces allocations se produisent dans des boucles serrées.

La nouvelle fonctionnalité du langage signifie que les types de retour des méthodes async ne se limitent pas à `Task`, `Task<T>` et `void`. Le type retourné doit toujours correspondre au modèle async, ce qui signifie qu’une méthode `GetAwaiter` doit être accessible. Comme exemple concret, `ValueTask` le type a été ajouté à .NET pour faire usage de cette nouvelle fonctionnalité linguistique:

[!code-csharp[UsingValueTask](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#UsingValueTask "Using ValueTask")]

> [!NOTE]
> Vous devez ajouter le [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) paquet NuGet <xref:System.Threading.Tasks.ValueTask%601> afin d’utiliser le type.

Cette amélioration s’avère particulièrement utile pour les auteurs de bibliothèques afin d’éviter d’allouer un `Task` dans le code critique pour les performances.

## <a name="numeric-literal-syntax-improvements"></a>Améliorations de la syntaxe littérale numérique

La mauvaise interprétation de constantes numériques peut rendre plus difficile la compréhension du code quand il est lu pour la première fois. Les masques de bits ou d’autres valeurs symboliques sont source de méprise. C# 7.0 comprend deux nouvelles fonctionnalités permettant d’écrire des nombres de la manière la plus lisible pour l’utilisation prévue : les *littéraux binaires* et les *séparateurs de chiffres*.

Dans les cas où vous créez des masques de bits chaque fois qu’une représentation binaire d’un nombre rend le code plus lisible, écrivez ce nombre au format binaire :

[!code-csharp[ThousandSeparators](~/samples/snippets/csharp/new-in-7/Program.cs#ThousandSeparators "Thousands separators")]

Le `0b` au début de la constante indique que le nombre est écrit sous la forme d’un nombre binaire. Les nombres binaires peuvent être longs. Il est donc souvent plus facile de voir les modèles de bits en introduisant le `_` comme séparateur de chiffres, comme indiqué ci-dessus dans la constante binaire. Le séparateur de chiffres peut apparaître n’importe où dans la constante. Pour les nombres de base 10, il arrive fréquemment qu’il soit utilisé comme séparateur des milliers :

[!code-csharp[LargeIntegers](~/samples/snippets/csharp/new-in-7/Program.cs#LargeIntegers "Large integer")]

Il est possible d’utiliser le séparateur de chiffres également avec les types `decimal`, `float` et `double` :

[!code-csharp[OtherConstants](~/samples/snippets/csharp/new-in-7/Program.cs#OtherConstants "non-integral constants")]

Globalement, vous pouvez déclarer des constantes numériques avec beaucoup plus de lisibilité.
