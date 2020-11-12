---
title: Expressions lambda-référence C#
description: En savoir plus sur les expressions lambda. Il existe des lambdas d’expression qui ont une expression comme corps, ou des lambdas d’instruction qui ont un bloc d’instruction comme corps.
ms.date: 09/25/2020
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: 51bf44af5ec3478f2b2557b047df270c0c22990d
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94556840"
---
# <a name="lambda-expressions-c-reference"></a>Expressions lambda (référence C#)

Une *expression lambda* est une expression de l’une des deux formes suivantes :

- [Expression lambda](#expression-lambdas) qui a une expression comme corps :

  ```csharp
  (input-parameters) => expression
  ```

- [Instruction lambda](#statement-lambdas) qui a un bloc d’instructions comme corps :

  ```csharp  
  (input-parameters) => { <sequence-of-statements> }
  ```

Utilisez l’[opérateur de déclaration lambda`=>`](lambda-operator.md) pour séparer la liste des paramètres de l’expression lambda de son corps. Pour créer une expression lambda, vous spécifiez des paramètres d’entrée (le cas échéant) à gauche de l’opérateur lambda et une expression ou un bloc d’instructions de l’autre côté.

Toute expression lambda peut être convertie en type [délégué](../builtin-types/reference-types.md#the-delegate-type). Le type délégué vers lequel une expression lambda peut être convertie est défini par les types de ses paramètres et de sa valeur de retour. Si une expression lambda ne retourne pas de valeur, elle peut être convertie en l’un des types délégués `Action` ; sinon, elle peut être convertie en l’un des types délégués `Func`. Par exemple, une expression lambda qui a deux paramètres et qui ne retourne aucune valeur peut être convertie en un délégué <xref:System.Action%602>. Une expression lambda qui a un paramètre et qui retourne une valeur peut être convertie en un délégué <xref:System.Func%602>. Dans l’exemple suivant, l’expression lambda `x => x * x` , qui spécifie un paramètre nommé `x` et retourne la valeur du `x` carré, est assignée à une variable d’un type délégué :

[!code-csharp-interactive[lambda is delegate](snippets/lambda-expressions/Introduction.cs#Delegate)]

Les expressions lambda d’expression peuvent également être converties en types d' [arborescences d’expression](../../programming-guide/concepts/expression-trees/index.md) , comme le montre l’exemple suivant :

[!code-csharp-interactive[lambda is expression tree](snippets/lambda-expressions/Introduction.cs#ExpressionTree)]

Vous pouvez utiliser des expressions lambda dans tout code qui requiert des instances de types délégués ou d’arborescences d’expressions, par exemple en tant qu’argument de la méthode <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> pour passer le code qui doit être exécuté en arrière-plan. Vous pouvez également utiliser des expressions lambda quand vous écrivez [LINQ en C#](../../linq/index.md), comme le montre l’exemple suivant :

[!code-csharp-interactive[lambda is argument in LINQ](snippets/lambda-expressions/Introduction.cs#Argument)]

Lorsque la méthode <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> est appelée avec une syntaxe fondée sur une méthode dans la classe <xref:System.Linq.Enumerable?displayProperty=nameWithType> (par exemple, dans LINQ to Objects et LINQ to XML), le paramètre est un type délégué <xref:System.Func%602?displayProperty=nameWithType>. Quand vous appelez la <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> méthode dans la <xref:System.Linq.Queryable?displayProperty=nameWithType> classe, par exemple dans LINQ to SQL, le type de paramètre est un type d’arborescence d’expression [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>) . Dans les deux cas, vous pouvez utiliser la même expression lambda pour spécifier la valeur de paramètre. Les deux appels `Select` semblent ainsi semblables alors qu’en fait le type des objets créés à partir des lambdas est différent.
  
## <a name="expression-lambdas"></a>Expressions lambdas

Une expression lambda comportant une expression à droite de l’opérateur `=>` est appelée *expression lambda*. Une expression lambda retourne le résultat de l'expression et prend la forme de base suivante :

```csharp
(input-parameters) => expression
```

Le corps d’une expression lambda peut se composer d’un appel de méthode. Toutefois, si vous créez des [arborescences d’expressions](../../programming-guide/concepts/expression-trees/index.md) qui sont évaluées en dehors du contexte du Common Language Runtime (CLR) .net, par exemple dans SQL Server, vous ne devez pas utiliser les appels de méthode dans les expressions lambda. Les méthodes n’auront aucune signification en dehors du contexte du Common Language Runtime (CLR) .NET.

## <a name="statement-lambdas"></a>Instructions lambda

Une instruction lambda ressemble à une expression lambda, sauf que ses instructions sont placées entre accolades :

```csharp  
(input-parameters) => { <sequence-of-statements> }
```

Le corps d'une instruction lambda peut se composer d'un nombre illimité d'instructions ; toutefois, en pratique, leur nombre est généralement de deux ou trois.

:::code language="csharp" interactive="try-dotnet-method" source="snippets/lambda-expressions/GeneralExamples.cs" id="SnippetStatementLambda":::

Vous ne pouvez pas utiliser des lambdas d’instruction pour créer des arborescences d’expressions.

## <a name="input-parameters-of-a-lambda-expression"></a>Paramètres d’entrée d’une expression lambda

Placez les paramètres d’entrée d’une expression lambda entre parenthèses. Spécifiez des paramètres d'entrée de zéro avec des parenthèses vides :  

:::code language="csharp" source="snippets/lambda-expressions/GeneralExamples.cs" id="SnippetZeroParameters":::

Si une expression lambda a un seul paramètre d’entrée, les parenthèses sont facultatives :

:::code language="csharp" source="snippets/lambda-expressions/GeneralExamples.cs" id="SnippetOneParameter":::

Deux ou plusieurs paramètres d’entrée sont séparés par des virgules :

:::code language="csharp" source="snippets/lambda-expressions/GeneralExamples.cs" id="SnippetTwoParameters":::

Parfois, le compilateur ne peut pas déduire les types de paramètres d’entrée. Vous pouvez spécifier les types explicitement comme dans l’exemple suivant :

:::code language="csharp" source="snippets/lambda-expressions/GeneralExamples.cs" id="SnippetExplicitlyTypedParameters":::

Les types de paramètres d’entrée doivent être tous explicites ou tous implicites ; sinon, une erreur de compilateur [CS0748](../../misc/cs0748.md) se produit.

À compter de C# 9,0, vous pouvez utiliser des éléments [ignorés](../../discards.md) pour spécifier au moins deux paramètres d’entrée d’une expression lambda qui ne sont pas utilisés dans l’expression :

:::code language="csharp" source="snippets/lambda-expressions/GeneralExamples.cs" id="SnippetDiscards":::

Les paramètres d’abandon lambda peuvent être utiles lorsque vous utilisez une expression lambda pour [fournir un gestionnaire d’événements](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

> [!NOTE]
> À des fins de compatibilité descendante, si un seul paramètre d’entrée est nommé `_` , alors, dans une expression lambda, `_` est traité comme le nom de ce paramètre.

## <a name="async-lambdas"></a>Lambdas asynchrones

Vous pouvez facilement créer des expressions et des instructions lambda qui incorporent le traitement asynchrone à l'aide des mots clés [async](../keywords/async.md) et [await](await.md) . Par exemple, l'exemple Windows Forms suivant contient un gestionnaire d'événements qui appelle et attend une méthode async `ExampleMethodAsync`.

```csharp
public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();
        button1.Click += button1_Click;
    }

    private async void button1_Click(object sender, EventArgs e)
    {
        await ExampleMethodAsync();
        textBox1.Text += "\r\nControl returned to Click event handler.\n";
    }

    private async Task ExampleMethodAsync()
    {
        // The following line simulates a task-returning asynchronous process.
        await Task.Delay(1000);
    }
}
```

Vous pouvez ajouter le même gestionnaire d'événements en utilisant une expression lambda asynchrone. Pour ajouter ce gestionnaire, ajoutez un modificateur `async` avant la liste des paramètres lambda, comme dans l’exemple suivant :

```csharp
public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();
        button1.Click += async (sender, e) =>
        {
            await ExampleMethodAsync();
            textBox1.Text += "\r\nControl returned to Click event handler.\n";
        };
    }

    private async Task ExampleMethodAsync()
    {
        // The following line simulates a task-returning asynchronous process.
        await Task.Delay(1000);
    }
}
```

Pour plus d’informations sur la création et l’utilisation des méthodes Async, consultez [programmation asynchrone avec Async et await](../../programming-guide/concepts/async/index.md).

## <a name="lambda-expressions-and-tuples"></a>Expressions lambda et tuples

À compter de C# 7,0, le langage C# offre une prise en charge intégrée des [tuples](../builtin-types/value-tuples.md). Vous pouvez fournir un tuple comme argument à une expression lambda, et votre expression lambda peut aussi retourner un tuple. Dans certains cas, le compilateur C# utilise l’inférence de type pour déterminer les types des composants du tuple.

Vous définissez un tuple en plaçant entre des parenthèses une liste de ses composants avec des virgules comme séparateur. L’exemple suivant utilise un tuple à trois composants pour passer une séquence de nombres à une expression lambda, qui double chaque valeur et retourne un tuple à trois composants contenant le résultat des multiplications.

[!code-csharp-interactive[lambda and tuples](snippets/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

En règle générale, les champs d’un tuple sont nommés `Item1` , `Item2` , etc. Toutefois, vous pouvez définir un tuple avec des composants nommés, comme le montre l’exemple suivant.

[!code-csharp-interactive[lambda and named tuples](snippets/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

Pour plus d’informations sur les tuples C#, consultez [types de tuples](../../language-reference/builtin-types/value-tuples.md).

## <a name="lambdas-with-the-standard-query-operators"></a>Lambdas avec les opérateurs de requête standard

LINQ to Objects, parmi d’autres implémentations, a un paramètre d’entrée dont le type fait partie de la famille <xref:System.Func%601> de délégués génériques. Ces délégués utilisent des paramètres de type pour définir le nombre et le type des paramètres d’entrée, ainsi que le type de retour du délégué. Les délégués`Func` sont très utiles pour l'encapsulation des expressions définies par l'utilisateur appliquées à chaque élément dans un jeu de données sources. Prenons par exemple le type délégué <xref:System.Func%602> :  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

Ce délégué peut être instancié comme une instance `Func<int, bool>`, où `int` est un paramètre d’entrée et `bool` la valeur de retour. La valeur de retour est toujours spécifiée dans le dernier paramètre de type. Par exemple, `Func<int, string, bool>` définit un délégué avec deux paramètres d’entrée, `int` et `string`, et un type de retour `bool`. Le délégué `Func` suivant, lorsqu’il est appelé, retourne une valeur booléenne indiquant si le paramètre d’entrée est égal à cinq :

[!code-csharp-interactive[Func example](snippets/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

Vous pouvez aussi fournir une expression lambda quand le type d’argument est <xref:System.Linq.Expressions.Expression%601>, par exemple, dans les opérateurs de requête standard définis dans le type <xref:System.Linq.Queryable>. Quand vous spécifiez un argument <xref:System.Linq.Expressions.Expression%601>, l’expression lambda est compilée en arborescence de l’expression.
  
L’exemple suivant utilise l’opérateur de requête standard <xref:System.Linq.Enumerable.Count%2A> :

[!code-csharp-interactive[Count example](snippets/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

Le compilateur peut déduire le type du paramètre d'entrée, ou vous pouvez également le spécifier explicitement. Cette expression lambda particulière compte les entiers (`n`) qui, lorsqu'ils sont divisés par deux, ont un reste de 1.

L’exemple suivant produit une séquence qui contient tous les éléments du tableau `numbers` précédant le 9, car c’est le premier nombre de la séquence qui ne remplit pas la condition :

[!code-csharp-interactive[TakeWhile example](snippets/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

L’exemple suivant spécifie plusieurs paramètres d’entrée en les plaçant entre parenthèses. La méthode retourne tous les éléments du tableau `numbers` jusqu’à ce qu’elle rencontre un nombre dont la valeur est inférieure à sa position ordinale dans le tableau :

[!code-csharp-interactive[TakeWhile example 2](snippets/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a>Inférence de type et expressions lambda

Il n’est généralement pas nécessaire, avec les expressions lambda, de spécifier un type pour les paramètres d’entrée, car le compilateur peut le déduire du corps de l’expression, des types de paramètres et d’autres facteurs, comme le décrit la spécification du langage C#. Pour la plupart des opérateurs de requête standard, la première entrée est le type des éléments dans la séquence source. Si vous interrogez un `IEnumerable<Customer>`, le type de la variable d’entrée est inféré comme étant un objet `Customer`, ce qui signifie que vous avez accès à ses méthodes et à ses propriétés :  

```csharp
customers.Where(c => c.City == "London");
```

Voici les règles générales de l’inférence de type pour les expressions lambda :

- Le lambda doit contenir le même nombre de paramètres que le type délégué.

- Chaque paramètre d'entrée dans le lambda doit être implicitement convertible en son paramètre de délégué correspondant.

- La valeur de retour du lambda (le cas échéant) doit être implicitement convertible en type de retour du délégué.
  
Notez que les expressions lambda n’ont pas de type en elles-mêmes, car le système de type commun (CTS, Common Type System) ne comporte aucun concept intrinsèque « d’expression lambda ». Toutefois, il est parfois commode de parler de manière informelle du « type » d’une expression lambda. Dans ce cas, le type fait référence au type délégué ou au type <xref:System.Linq.Expressions.Expression> dans lequel est convertie l'expression lambda.

## <a name="capture-of-outer-variables-and-variable-scope-in-lambda-expressions"></a>Capture des variables externes et de l’étendue variable dans les expressions lambda

Les expressions lambda peuvent faire référence à des *variables externes*. Il s’agit de variables dans l’étendue de la méthode qui définit l’expression lambda, ou dans l’étendue du type qui contient l’expression lambda. Les variables capturées de cette manière sont stockées pour une utilisation dans l'expression lambda, même si les variables se trouvent en dehors de la portée et sont récupérées par le garbage collector. Une variable externe doit être assignée de manière précise pour pouvoir être utilisée dans une expression lambda. L'exemple suivant illustre ces règles :

[!code-csharp[variable scope](snippets/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

Les règles suivantes s'appliquent à la portée des variables dans les expressions lambda :  

- Une variable qui est capturée ne sera pas récupérée par le garbage collector avant que le délégué qui le référence soit disponible pour le garbage collection.

- Les variables introduites dans une expression lambda ne sont pas visibles dans la méthode englobante.

- Une expression lambda ne peut pas capturer directement un paramètre [in](../keywords/in-parameter-modifier.md), [ref](../keywords/ref.md) ou [out](../keywords/out-parameter-modifier.md) dans la méthode englobante.

- Une instruction [return](../keywords/return.md) dans une expression lambda ne provoque pas le retour de la méthode englobante.

- Une expression lambda ne peut pas contenir d’instruction [goto](../keywords/goto.md), [break](../keywords/break.md) ou [continue](../keywords/continue.md) si la cible de cette instruction de saut se trouve en dehors du bloc de l’expression lambda. Il est également incorrect d’avoir une instruction de saut en dehors du bloc de l’expression lambda si la cible se trouve à l’intérieur du bloc.

À compter de C# 9,0, vous pouvez appliquer le `static` modificateur à une expression lambda pour empêcher la capture non intentionnelle de variables locales ou l’état de l’instance par le lambda :

:::code language="csharp" source="snippets/lambda-expressions/GeneralExamples.cs" id="SnippetStatic":::

Une expression lambda statique ne peut pas capturer les variables locales ou l’état de l’instance à partir des étendues englobantes, mais peut référencer des membres statiques et des définitions de constantes.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [Expressions de fonction anonyme](~/_csharplang/spec/expressions.md#anonymous-function-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

Pour plus d’informations sur les fonctionnalités ajoutées dans C# 9,0, consultez les notes de proposition de fonctionnalités suivantes :

- [Paramètres d’abandon lambda](~/_csharplang/proposals/csharp-9.0/lambda-discard-parameters.md)
- [Fonctions anonymes statiques](~/_csharplang/proposals/csharp-9.0/static-anonymous-functions.md)

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs et expressions C#](index.md)
- [LINQ (Language Integrated Query)](../../programming-guide/concepts/linq/index.md)
- [Arborescences d’expressions](../../programming-guide/concepts/expression-trees/index.md)
- [Fonctions locales et expressions lambda](../../programming-guide/classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions)
- [Exemples Visual Studio 2008 C# (voir les fichiers d’exemples de requêtes LINQ et le programme XQuery)](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
