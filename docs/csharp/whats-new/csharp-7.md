---
title: Nouveautés de C# 7.0 | Guide C#
description: Découvrez les nouvelles fonctionnalités disponibles dans la version 7.0 du langage C#.
ms.date: 10/02/2020
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: 774bf9860d929d725f3a2bda4a52bc75ae3921fe
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91755822"
---
# <a name="whats-new-in-c-70-through-c-73"></a>Nouveautés de C# 7,0 par C# 7,3

C# 7,0 à C# 7,3 a apporté un certain nombre de fonctionnalités et des améliorations incrémentielles à votre expérience de développement avec C#. Cet article fournit une vue d’ensemble des nouvelles fonctionnalités de langage et des options du compilateur. Les descriptions décrivent le comportement de C# 7,3, qui est la version la plus récente prise en charge pour les applications .NET Framework.

L’élément de configuration de sélection de la [version de langage](../language-reference/configure-language-version.md) a été ajouté avec C# 7,1, ce qui vous permet de spécifier la version du langage du compilateur dans votre fichier projet.

C# 7.0-7.3 ajoute ces fonctionnalités et thèmes au langage C# :

- [Tuples et éléments ignorés](#tuples-and-discards)
  - Vous pouvez créer des types légers et sans nom qui contiennent plusieurs champs publics. Les compilateurs et les outils de l’IDE comprennent la sémantique de ces types.
  - Les éléments ignorés sont les variables temporaires en écriture seule utilisées dans les attributions quand vous ne vous souciez pas de la valeur assignée. Ils s’avèrent utiles lors de la déconstruction de tuples et de types définis par l’utilisateur, ainsi que lors de l’appel de méthodes avec des paramètres `out`.
- [Critères spéciaux](#pattern-matching)
  - Vous pouvez créer une logique de branchement basée sur des types arbitraires et les valeurs des membres de ces types.
- [`async``Main`méthode](#async-main)
  - Le point d’entrée pour une application peut avoir le modificateur `async`.
- [Fonctions locales](#local-functions)
  - Vous pouvez imbriquer des fonctions dans d’autres fonctions afin de limiter leur portée et leur visibilité.
- [Autres membres expression-bodied](#more-expression-bodied-members)
  - La liste des membres pouvant être créés à l’aide d’expressions s’est allongée.
- [`throw` Manifestations](#throw-expressions)
  - Vous pouvez lever des exceptions dans les constructions de code qui n’étaient pas autorisées auparavant, car `throw` était une instruction.
- [`default` expressions littérales](#default-literal-expressions)
  - Vous pouvez utiliser des expressions littérales default dans les expressions de valeur par défaut quand le type cible peut être inféré.
- [Améliorations de la syntaxe littérale numérique](#numeric-literal-syntax-improvements)
  - De nouveaux jetons améliorent la lisibilité des constantes numériques.
- [`out` variables](#out-variables)
  - Vous pouvez déclarer des valeurs `out` inline comme arguments de la méthode dans laquelle elles sont utilisées.
- [Arguments nommés non placés en position de fin](#non-trailing-named-arguments)
  - Les arguments nommés peuvent être suivis par des arguments de position.
- [`private protected` modificateur d’accès](#private-protected-access-modifier)
  - Le modificateur d’accès `private protected` active l’accès pour les classes dérivées dans le même assembly.
- [Résolution de surcharge améliorée](#improved-overload-resolution)
  - Nouvelles règles pour résoudre l’ambiguïté de résolution de surcharge.
- [Techniques d’écriture de code safe et efficace](#safe-efficient-code-enhancements)
  - Une combinaison des améliorations de la syntaxe qui permettent d’utiliser les types valeur avec la sémantique de référence.

Enfin, le compilateur a de nouvelles options :

- `-refout` et `-refonly` qui contrôlent la génération de l' [assembly de référence](#reference-assembly-generation).
- `-publicsign` pour activer la signature d’assemblys Open Source Software (OSS).
- `-pathmap` pour fournir un mappage des répertoires sources.

Le reste de cet article présente une vue d’ensemble de chaque fonctionnalité. Pour chaque fonctionnalité, vous apprendrez le raisonnement sous-jacent et la syntaxe. Vous pouvez explorer ces fonctionnalités dans votre environnement à l’aide de l’outil global `dotnet try` :

1. Installez l’outil global [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup).
1. Clonez le référentiel [dotnet/try-samples](https://github.com/dotnet/try-samples).
1. Définissez le répertoire actuel sur le sous-répertoire *csharp7* pour le référentiel *try-samples*.
1. Exécutez `dotnet try`.

## <a name="tuples-and-discards"></a>Tuples et éléments ignorés

C# fournit une syntaxe complète pour les classes et les structs, utilisée pour expliquer l’intention de votre conception. Cependant, cette syntaxe complète nécessite parfois un travail supplémentaire avec peu d’avantages. Vous pouvez souvent écrire des méthodes qui nécessitent une structure simple contenant plusieurs éléments de données. Pour prendre en charge ces scénarios, des *tuples* ont été ajoutées à C#. Les tuples sont des structures de données légères contenant plusieurs champs pour représenter les membres de données. Les champs ne sont pas validés et vous ne pouvez pas définir vos propres méthodes. Les types de tuple C# prennent en charge `==` et `!=` . Pour plus d’informations, consultez

> [!NOTE]
> Les tuples étaient disponibles avant C# 7.0, mais ils n’étaient pas efficaces et n’avaient aucune prise en charge du langage. Cela signifiait que les éléments tuples pouvaient uniquement être référencés comme `Item1`, `Item2`, et ainsi de suite. C# 7.0 introduit la prise en charge du langage pour les tuples, ce qui permet d’utiliser des noms sémantiques pour les champs d’un tuple avec de nouveaux types tuple plus efficaces.

Vous pouvez créer un tuple en assignant une valeur à chaque membre et éventuellement, en fournissant des noms sémantiques à chacun des membres du tuple :

[!code-csharp[NamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#NamedTuple "Named tuple")]

Le tuple `namedLetters` contient des champs appelés `Alpha` et `Beta`. Ces noms existent uniquement au moment de la compilation et ne sont pas conservés, par exemple lors de l’inspection du tuple à l’aide de la réflexion au moment de l’exécution.

Dans une assignation de tuple, vous pouvez également spécifier les noms des champs dans la partie droite :

[!code-csharp[ImplicitNamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#ImplicitNamedTuple "Implicitly named tuple")]

Dans certains cas, vous pouvez souhaiter décompresser les membres d’un tuple qui ont été retournés à partir d’une méthode.  Pour ce faire, déclarez des variables distinctes pour chacune des valeurs dans le tuple. Cette décompression est appelée *déconstruction* du tuple :

[!code-csharp[CallingWithDeconstructor](~/samples/snippets/csharp/new-in-7/program.cs#CallingWithDeconstructor "Deconstructing a tuple")]

Vous pouvez également fournir une déconstruction similaire pour tout type dans le .NET. Vous écrivez une méthode `Deconstruct` en tant que membre de la classe. Cette méthode `Deconstruct` fournit un ensemble d’arguments `out` pour chacune des propriétés que vous voulez extraire. Prenons la classe `Point` suivante qui fournit une méthode de déconstructeur qui extrait les coordonnées `X` et `Y` :

[!code-csharp[PointWithDeconstruction](~/samples/snippets/csharp/new-in-7/point.cs#PointWithDeconstruction "Point with deconstruction method")]

Vous pouvez extraire les champs individuels en affectant un `Point` à un tuple :

[!code-csharp[DeconstructPoint](~/samples/snippets/csharp/new-in-7/program.cs#DeconstructPoint "Deconstruct a point")]

Bien souvent, lorsque vous initialisez un tuple, les variables utilisées pour le côté droit de l’assignation sont les mêmes que les noms que vous souhaitez pour les éléments de tuple : les noms des éléments de tuple peuvent être déduits à partir des variables utilisées pour initialiser le tuple :

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

Pour plus d’informations sur cette fonctionnalité, consultez l’article [types de tuples](../language-reference/builtin-types/value-tuples.md) .

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

Les *critères spéciaux* sont un ensemble de fonctionnalités qui permettent de nouvelles façons d’exprimer le contrôle du workflow dans votre code. Vous pouvez tester des variables pour leur type, leurs valeurs ou les valeurs de leurs propriétés. Ces techniques créent un flot de code plus lisible.

Les critères spéciaux prennent en charge les expressions `is` et les expressions `switch`. L’une ou l’autre permettent d’inspecter un objet et ses propriétés afin de déterminer s’il correspond au modèle recherché. Vous utilisez le mot clé `when` pour spécifier des règles supplémentaires pour le modèle.

L' `is` expression de modèle étend l' [ `is` opérateur](../language-reference/keywords/is.md#pattern-matching-with-is) familier pour interroger un objet sur son type et assigner le résultat dans une instruction. Le code suivant vérifie si une variable est un `int`, et si tel est le cas, il l’ajoute à la somme actuelle :

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

À compter de C# 7.1, l’expression de modèle de `is` et du modèle de type `switch` peut avoir le type d’un paramètre de type générique, ce qui peut se révéler particulièrement utile pour vérifier des types potentiellement `struct` ou `class` tout en évitant le boxing.

Pour plus d’informations sur les critères spéciaux, consultez [Critères spéciaux en C#](../pattern-matching.md).

## <a name="async-main"></a>Async main

Une méthode *async main* vous permet d’utiliser `await` dans votre méthode `Main`. Auparavant, vous deviez écrire :

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

Vous pouvez désormais écrire :

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

Si votre programme ne retourne pas de code de sortie, vous pouvez déclarer une méthode `Main` qui retourne une <xref:System.Threading.Tasks.Task> :

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

Pour plus d’informations, voir l’article [async main](../programming-guide/main-and-command-args/index.md) du guide de programmation.

## <a name="local-functions"></a>Fonctions locales

De nombreuses conceptions pour les classes incluent des méthodes qui sont appelées à partir d’un seul emplacement. Ces méthodes privées supplémentaires maintiennent chaque méthode réduite et focalisée. Les *fonctions locales* vous permettent d’utiliser des méthodes dans le contexte d’une autre méthode. Il est ainsi plus facile pour les lecteurs de la classe de voir que la méthode locale est appelée uniquement à partir du contexte dans lequel elle a été déclarée.

Il existe deux cas d’utilisation courants pour les fonctions locales : les méthodes iterator publiques et les méthodes async publiques. Ces deux types de méthodes génèrent du code qui signale les erreurs plus tard que ce qu’attendent les programmeurs. Dans les méthodes iterator, toute exception est observée uniquement lors de l’appel de code qui énumère la séquence retournée. Dans les méthodes async, toute exception est observée uniquement quand le `Task` retourné est attendu. L’exemple suivant illustre la séparation entre la validation de paramètres et l’implémentation de l’itérateur à l’aide d’une fonction locale :

[!code-csharp[22_IteratorMethodLocal](~/samples/snippets/csharp/new-in-7/Iterator.cs#IteratorMethodLocal "Iterator method with local function")]

Il est possible d’utiliser la même technique avec les méthodes `async` pour garantir que les exceptions résultant de la validation d’argument sont levées avant le début de la tâche asynchrone :

[!code-csharp[TaskExample](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

Cette syntaxe est maintenant prise en charge :

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

L’attribut `SomeThingAboutFieldAttribute` est appliqué au champ de stockage généré par le compilateur pour `SomeProperty`. Pour plus d’informations, consultez les [attributs](../programming-guide/concepts/attributes/index.md) dans le guide de programmation C#.

> [!NOTE]
> Certaines des conceptions prises en charge par les fonctions locales peuvent également être accomplies à l’aide d' *expressions lambda*. Pour plus d’informations, consultez [fonctions locales et expressions lambda](../programming-guide/classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions).

## <a name="more-expression-bodied-members"></a>Autres membres expression-bodied

C# 6 a introduit les [membres expression-bodied](csharp-6.md#expression-bodied-function-members) pour les fonctions membres, ainsi que des propriétés en lecture seule. C# 7.0 développe les membres autorisés pouvant être implémentés comme expressions. Dans C# 7.0, vous pouvez implémenter des *constructeurs*, des *finaliseurs* ainsi que des accesseurs `get` et `set` sur des *propriétés* et des *indexeurs*. Le code suivant présente des exemples de chaque élément :

[!code-csharp[ExpressionBodiedMembers](~/samples/snippets/csharp/new-in-7/expressionmembers.cs#ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> Cet exemple n’a pas besoin de finaliseur, mais il est présenté pour illustrer la syntaxe. Vous ne devez implémenter un finaliseur dans votre classe que si cela est nécessaire pour libérer des ressources non managées. Vous devez également envisager d’utiliser la classe <xref:System.Runtime.InteropServices.SafeHandle> au lieu de gérer directement les ressources non managées.

Ces nouveaux emplacements pour les membres expression-bodied représentent une étape importante pour le langage C# : ces fonctionnalités ont été implémentées par des membres de la communauté travaillant sur le projet open source [Roslyn](https://github.com/dotnet/Roslyn).

La modification d’une méthode en un membre expression-bodied est une [modification compatible binaire](version-update-considerations.md#binary-compatible-changes).

## <a name="throw-expressions"></a>Expressions throw

En C#, `throw` a toujours été une instruction. Étant donné que `throw` est une instruction, et non pas une expression, certaines constructions C# ne pouvaient pas l’utiliser. Il s’agit notamment des expressions conditionnelles, des expressions de fusion null, ainsi que de certaines expressions lambda. L’ajout de membres expression-bodied ajoute des emplacements supplémentaires où les expressions `throw` seraient utiles. Afin que vous puissiez écrire l’une de ces constructions, C# 7,0 introduit des [*expressions Throw*](../language-reference/keywords/throw.md#the-throw-expression).

Cet ajout facilite l’écriture de code davantage basé sur des expressions. Vous n’avez pas besoin d’instructions supplémentaires pour la vérification des erreurs.

## <a name="default-literal-expressions"></a>Expressions littérales par défaut

Les expressions littérales par défaut sont une amélioration des expressions de valeur par défaut. Ces expressions initialisent une variable à la valeur par défaut. Vous deviez écrire auparavant :

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

Vous pouvez désormais omettre le type du côté droit de l’initialisation :

```csharp
Func<string, bool> whereClause = default;
```

Pour plus d’informations, voir la section [littéral par défaut](../language-reference/operators/default.md#default-literal) de l’article [opérateur par défaut](../language-reference/operators/default.md).

## <a name="numeric-literal-syntax-improvements"></a>Améliorations de la syntaxe littérale numérique

La mauvaise interprétation de constantes numériques peut rendre plus difficile la compréhension du code quand il est lu pour la première fois. Les masques de bits ou d’autres valeurs symboliques sont source de méprise. C# 7.0 comprend deux nouvelles fonctionnalités permettant d’écrire des nombres de la manière la plus lisible pour l’utilisation prévue : les *littéraux binaires* et les *séparateurs de chiffres*.

Dans les cas où vous créez des masques de bits chaque fois qu’une représentation binaire d’un nombre rend le code plus lisible, écrivez ce nombre au format binaire :

[!code-csharp[ThousandSeparators](~/samples/snippets/csharp/new-in-7/Program.cs#ThousandSeparators "Thousands separators")]

Le `0b` au début de la constante indique que le nombre est écrit sous la forme d’un nombre binaire. Les nombres binaires peuvent être longs. il est donc souvent plus facile de voir les modèles binaires en introduisant le `_` sous forme de séparateur numérique, comme indiqué dans la constante binaire de l’exemple précédent. Le séparateur de chiffres peut apparaître n’importe où dans la constante. Pour les nombres de base 10, il est courant de l’utiliser comme séparateur des milliers. Les littéraux numériques hexadécimaux et binaires peuvent commencer par un `_` :

[!code-csharp[LargeIntegers](~/samples/snippets/csharp/new-in-7/Program.cs#LargeIntegers "Large integer")]

Il est possible d’utiliser le séparateur de chiffres également avec les types `decimal`, `float` et `double` :

[!code-csharp[OtherConstants](~/samples/snippets/csharp/new-in-7/Program.cs#OtherConstants "non-integral constants")]

Globalement, vous pouvez déclarer des constantes numériques avec beaucoup plus de lisibilité.

## <a name="out-variables"></a>Variables `out`

La syntaxe existante qui prend en charge les `out` paramètres a été améliorée en C# 7. Vous pouvez désormais déclarer des variables `out` dans la liste d’arguments d’un appel de méthode, au lieu d’écrire une instruction de déclaration distincte :

[!code-csharp[OutVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVariableDeclarations "Out variable declarations")]

Vous pouvez spécifier le type de la `out` variable pour plus de clarté, comme indiqué dans l’exemple précédent. Toutefois, le langage prend en charge l’utilisation d’une variable locale implicitement typée :

[!code-csharp[OutVarVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVarVariableDeclarations "Implicitly typed Out variable")]

- Le code est plus facile à lire.
  - Vous déclarez la variable out là où vous l’utilisez, et non sur une ligne de code précédente.
- Il n’est pas nécessaire d’assigner une valeur initiale.
  - En déclarant la variable `out` à l’endroit où elle est utilisée dans un appel de méthode, vous ne pouvez pas l’utiliser accidentellement avant qu’elle soit assignée.

La syntaxe ajoutée dans C# 7.0 pour autoriser les déclarations variables `out` a été étendue pour inclure des initialiseurs de champ, des initialiseurs de propriété, des initialiseurs de constructeur et des clauses de requête. Il permet d’écrire un code tel que l’exemple suivant :

```csharp
public class B
{
   public B(int i, out int j)
   {
      j = i;
   }
}

public class D : B
{
   public D(int i) : base(i, out var j)
   {
      Console.WriteLine($"The value of 'j' is {j}");
   }
}
```

## <a name="non-trailing-named-arguments"></a>Arguments nommés non placés en position de fin

Les appels de méthode peuvent désormais utiliser des arguments nommés qui précèdent les arguments de position quand ces arguments nommés se trouvent dans les positions appropriées. Pour plus d’informations, consultez [arguments nommés et facultatifs](../programming-guide/classes-and-structs/named-and-optional-arguments.md).

## <a name="private-protected-access-modifier"></a>*private protected* (modificateur d’accès)

Enfin, un nouveau modificateur d’accès composé, `private protected`, indique qu’un membre est accessible à la classe globale ou aux classes dérivées déclarées dans le même assembly. Alors que `protected internal` autorise l’accès par des classes dérivées ou qui se trouvent dans le même assembly, `private protected` limite l’accès aux types dérivés déclarés dans le même assembly.

Pour plus d’informations, consultez [modificateurs d’accès](../language-reference/keywords/access-modifiers.md) dans la référence du langage.

## <a name="improved-overload-candidates"></a>Candidats de surcharge améliorés

Dans chaque version, les règles de résolution de surcharge ont été mises à jour pour résoudre les situations où des appels de méthode ambigus sont face à un choix « évident ». Cette version ajoute trois nouvelles règles pour aider le compilateur à opter pour le choix évident :

1. Lorsqu’un groupe de méthodes contient à la fois une instance et des membres statiques, le compilateur ignore les membres de l’instance si la méthode a été appelée sans récepteur d’instance ou contexte. Le compilateur ignore les membres statiques si la méthode a été appelée avec un récepteur d’instance. Lorsqu’il n’existe aucun récepteur, le compilateur inclut uniquement les membres statiques dans un contexte statique, sinon, à la fois les membres statiques et les membres de l’instance. Lorsque le récepteur représente de façon ambiguë une instance ou un type, le compilateur inclut les deux éléments. Un contexte statique, où un récepteur d’instance `this` implicite ne peut pas être utilisé, inclut le corps des membres où aucun `this` n’est défini, par exemple des membres statiques, ainsi que chaque endroit où `this` ne peut pas être utilisé, par exemple les initialiseurs de champ et les initialiseurs de constructeur.
1. Lorsqu’un groupe de méthodes contient certaines méthodes génériques dont les arguments de type ne répondent pas à leurs contraintes, ces membres sont supprimés de l’ensemble de candidats.
1. Pour une conversion de groupe de méthodes, les méthodes candidates dont le type de retour ne correspond pas à celui du délégué sont supprimées de l’ensemble.

Vous ne remarquerez que cette modification car vous trouverez moins d’erreurs de compilateur pour les surcharges de méthode ambiguës si vous savez quelle méthode est la meilleure.

## <a name="enabling-more-efficient-safe-code"></a>Code sécurisé plus performant

Vous devez être en mesure d’écrire en toute sécurité un code C# ainsi performant qu’un code non sécurisé. Le code sécurisé évite les classes d’erreurs, par exemple les dépassements de mémoire tampon, les pointeurs perdus et d’autres erreurs d’accès à la mémoire. Ces nouvelles fonctionnalités étendent les fonctionnalités de code sécurisé vérifiables. Efforcez-vous d’utiliser plus de constructions sécurisées pour écrire votre code. Ces fonctionnalités facilitent cette écriture.

Les nouvelles fonctionnalités suivantes prennent en charge le thème de meilleures performances pour le code sécurisé :

- Vous pouvez accéder à des champs fixes sans épinglage.
- Vous pouvez réaffecter des variables locales `ref`.
- Vous pouvez utiliser des initialiseurs sur les tableaux `stackalloc`.
- Vous pouvez utiliser des instructions `fixed` avec tout type prenant en charge un modèle.
- Vous pouvez utiliser des contraintes génériques supplémentaires.
- Le modificateur `in` sur les paramètres pour spécifier qu’un argument est passé par référence, mais pas modifié par la méthode appelée. L’ajout du modificateur `in` à un argument est une [modification compatible avec la source](version-update-considerations.md#source-compatible-changes).
- Le modificateur `ref readonly` sur les retours de méthode pour indiquer qu’une méthode retourne sa valeur par référence, mais n’autorise pas les écritures sur cet objet. L’ajout du modificateur `ref readonly` est une [modification compatible avec la source](version-update-considerations.md#source-compatible-changes), si une valeur est assignée au retour. Le fait d’ajouter le modificateur `readonly` à une instruction de retour `ref` existante représente une [modification incompatible](version-update-considerations.md#incompatible-changes). Cela nécessite que les appelants mettent à jour de la déclaration de variables locales `ref` pour inclure le modificateur `readonly`.
- La déclaration `readonly struct` pour indiquer qu’un struct est immuable et doit être passé comme un paramètre `in` aux méthodes de ses membres. L’ajout du modificateur `readonly` à une déclaration struct existante est une [modification compatible binaire](version-update-considerations.md#binary-compatible-changes).
- La déclaration `ref struct` pour indiquer qu’un type struct accède directement à la mémoire managée et doit toujours être alloué par la pile. L’ajout du modificateur `ref` à une déclaration `struct` existante est une [modification incompatible](version-update-considerations.md#incompatible-changes). Un `ref struct` ne peut pas être membre d’une classe ou utilisé dans d’autres emplacements où il pourrait être alloué sur le tas.

Pour plus d’informations sur toutes ces modifications, voir [Écrire du code safe et efficace](../write-safe-efficient-code.md).

### <a name="ref-locals-and-returns"></a>Variables locales et retours ref

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

Désormais, les variables locales `ref` peuvent être réassignées pour faire référence à d’autres instances, après avoir été initialisées. Le code suivant effectue maintenant une compilation :

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

Pour plus d’informations, consultez l’article sur les [ `ref` retours et les `ref` variables locales](../programming-guide/classes-and-structs/ref-returns.md), ainsi que l’article sur [`foreach`](../language-reference/keywords/foreach-in.md) .

Pour plus d'informations, voir l’article [ref, mot clé](../language-reference/keywords/ref.md).

### <a name="conditional-ref-expressions"></a>Expressions `ref` conditionnelles

Enfin, l’expression conditionnelle peut produire comme résultat une référence plutôt qu’une valeur. Prenons par exemple la ligne suivante, qui récupère une référence au premier élément dans un des deux tableaux :

```csharp
ref var r = ref (arr != null ? ref arr[0] : ref otherArr[0]);
```

La variable `r` est une référence à la première valeur de `arr` ou `otherArr`.

Pour plus d’informations, voir [Opérateur conditionnel (?:)](../language-reference/operators/conditional-operator.md) dans la référence sur le langage.

### <a name="in-parameter-modifier"></a>`in` modificateur de paramètre

Le `in` mot clé complète les mots clés REF et out existants pour passer des arguments par référence. Le mot clé `in` spécifie que l’argument doit être passé par référence, mais la méthode appelée ne modifie pas la valeur.

Vous pouvez déclarer des surcharges qui passent par valeur ou par référence ReadOnly, comme indiqué dans le code suivant :

```csharp
static void M(S arg);
static void M(in S arg);
```

La valeur par valeur (tout d’abord dans l’exemple précédent) est meilleure que la version de référence par ReadOnly. Pour appeler la version avec l’argument de référence en lecture seule, vous devez inclure le modificateur `in` lors de l’appel de la méthode.

Pour plus d’informations, consultez l’article sur le [ `in` modificateur de paramètre](../language-reference/keywords/in-parameter-modifier.md).

### <a name="more-types-support-the-fixed-statement"></a>D’autres types prennent en charge l’instruction `fixed`

L’instruction `fixed` prenait en charge un ensemble limité de types. À partir de C# 7.3, tout type contenant une méthode `GetPinnableReference()` qui retourne `ref T` ou `ref readonly T` peut être `fixed`. L’ajout de cette fonctionnalité signifie que `fixed` peut être utilisé avec <xref:System.Span%601?displayProperty=nameWithType> et des types connexes.

Pour plus d’informations, consultez l’article sur les [ `fixed` instructions](../language-reference/keywords/fixed-statement.md) dans la référence du langage.

### <a name="indexing-fixed-fields-does-not-require-pinning"></a>L’indexation des champs `fixed` ne nécessite aucun épinglage

Prenons le struct suivant :

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

Dans les versions antérieures de C#, vous deviez épingler une variable pour accéder à un des entiers faisant partie de `myFixedField`. À présent, le code suivant se compile sans épingler la variable `p` à l’intérieur d’une instruction `fixed` distincte :

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        int p = s.myFixedField[5];
    }
}
```

La variable `p` accède à un élément dans `myFixedField`. Vous n’avez pas besoin de déclarer une variable `int*` distincte. Vous avez toujours besoin d’un `unsafe` contexte. Dans les versions antérieures de C#, vous devez déclarer un second pointeur fixe :

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        fixed (int* ptr = s.myFixedField)
        {
            int p = ptr[5];
        }
    }
}
```

Pour plus d’informations, consultez l’article sur l' [ `fixed` instruction](../language-reference/keywords/fixed-statement.md).

### <a name="stackalloc-arrays-support-initializers"></a>Les tableaux `stackalloc` prennent en charge les initialiseurs

Vous avez été en mesure de spécifier les valeurs des éléments dans un tableau lors de son initialisation :

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

Maintenant, la même syntaxe peut être appliquée aux tableaux déclarés avec `stackalloc` :

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

Pour plus d’informations, consultez l’article relatif à l' [ `stackalloc` opérateur](../language-reference/operators/stackalloc.md) .

### <a name="enhanced-generic-constraints"></a>Contraintes génériques améliorées

Vous pouvez maintenant spécifier le type <xref:System.Enum?displayProperty=nameWithType> ou <xref:System.Delegate?displayProperty=nameWithType> en tant que contraintes de classe de base pour un paramètre de type.

Vous pouvez également utiliser la nouvelle `unmanaged` contrainte pour spécifier qu’un paramètre de type doit être un [type non managé](../language-reference/builtin-types/unmanaged-types.md)qui n’accepte pas les valeurs NULL.

Pour plus d’informations, consultez les articles sur les contraintes et contraintes [ `where` génériques](../language-reference/keywords/where-generic-type-constraint.md) [sur les paramètres de type](../programming-guide/generics/constraints-on-type-parameters.md).

L’ajout de ces contraintes aux types existants est une [modification incompatible](version-update-considerations.md#incompatible-changes). Les types génériques fermés peuvent ne plus respecter ces nouvelles contraintes.

### <a name="generalized-async-return-types"></a>Types de retour async généralisés

Le retour d’un objet `Task` à partir de méthodes async peut introduire des goulots d’étranglement au niveau des performances dans certains chemins. `Task` est un type référence. Si vous l’utilisez, vous allouez donc un objet. Dans les cas où une méthode déclarée avec le modificateur `async` retourne un résultat mis en cache, ou si elle s’exécute de manière synchrone, le coût en termes de temps induit par les allocations supplémentaires peut s’avérer significatif dans les sections de code critiques pour les performances. Cela peut devenir coûteux si ces allocations se produisent dans des boucles serrées.

La nouvelle fonctionnalité du langage signifie que les types de retour des méthodes async ne se limitent pas à `Task`, `Task<T>` et `void`. Le type retourné doit toujours correspondre au modèle async, ce qui signifie qu’une méthode `GetAwaiter` doit être accessible. En guise d’exemple concret, le `ValueTask` type a été ajouté à .net pour utiliser cette nouvelle fonctionnalité de langage :

[!code-csharp[UsingValueTask](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#UsingValueTask "Using ValueTask")]

> [!NOTE]
> Vous devez ajouter le package NuGet [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) > pour pouvoir utiliser le <xref:System.Threading.Tasks.ValueTask%601> type.

Cette amélioration s’avère particulièrement utile pour les auteurs de bibliothèques afin d’éviter d’allouer un `Task` dans le code critique pour les performances.

## <a name="new-compiler-options"></a>Nouvelles options du compilateur

De nouvelles options du compilateur prennent en charge la nouvelle build et les scénarios DevOps pour les programmes C#.

### <a name="reference-assembly-generation"></a>Génération d’assemblys de références

Il existe deux nouvelles options de compilateur qui génèrent des *assemblys de référence uniquement*: [-REFOUT](../language-reference/compiler-options/refout-compiler-option.md) et [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).
Les articles en lien décrivent plus en détail ces options et les assemblys de références.

### <a name="public-or-open-source-signing"></a>Signature publique ou Open Source

L’option du compilateur `-publicsign` indique au compilateur de signer l’assembly à l’aide d’une clé publique. L’assembly est marqué comme étant signé, mais la signature provient de la clé publique. Cette option vous permet de générer des assemblys signés à partir de projets open source à l’aide d’une clé publique.

Pour plus d’informations, consultez l’article [Option du compilateur -publicsign](../language-reference/compiler-options/publicsign-compiler-option.md).

### <a name="pathmap"></a>pathmap

L’option du compilateur `-pathmap` indique au compilateur de remplacer les chemins sources de l’environnement de build par des chemins sources mappés. L’option `-pathmap` contrôle le chemin source écrit par le compilateur vers les fichiers PDB ou pour <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.

Pour plus d’informations, consultez l’article [Option du compilateur -pathmap](../language-reference/compiler-options/pathmap-compiler-option.md).
