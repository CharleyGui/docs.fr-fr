---
title: Exécution d’arborescences d’expressions
description: En savoir plus sur l’exécution des arborescences d’expressions en les convertissant en instructions de langage intermédiaire exécutables.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.openlocfilehash: 802a83f52f9c05a99c3f49f8f6511eff81ef3eaa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146019"
---
# <a name="executing-expression-trees"></a>Exécution d’arborescences d’expressions

[Précédent -- Types de frameworks prenant en charge les arborescences d’expressions](expression-classes.md)

Une *arborescence d’expressions* est une structure de données qui représente du code.
Il ne s’agit pas de code compilé et exécutable. Si vous souhaitez exécuter le code .NET représenté par une arborescence d’expressions, vous devez le convertir en instructions de langage intermédiaire exécutables.

## <a name="lambda-expressions-to-functions"></a>Des expressions lambda aux fonctions

Vous pouvez convertir n’importe quelle LambdaExpression ou n’importe quel type dérivé de LambdaExpression en langage intermédiaire exécutable. Les autres types d’expressions ne peuvent pas être convertis directement en code. Cette restriction a peu d’effet dans la pratique. Les expressions lambda sont les seuls types d’expressions que vous pourriez souhaiter exécuter par l’intermédiaire d’une conversion en langage intermédiaire exécutable. (Pensez à ce que cela signifierait d’exécuter directement une `ConstantExpression`. Cela signifierait-il quelque chose d’utile?) Tout arbre d’expression qui est `LambdaExpression` `LambdaExpression` un , ou un type dérivé peut être converti en IL.
Le type d’expression `Expression<TDelegate>` est le seul exemple concret dans les bibliothèques .NET Core. Il sert à représenter une expression mappée à un type délégué quelconque. Ce type étant mappé à un type délégué, .NET peut examiner l’expression et générer le langage intermédiaire pour un délégué approprié qui correspond à la signature de l’expression lambda.

Dans la plupart des cas, cela crée un mappage simple entre une expression et son délégué correspondant. Par exemple, une arborescence d’expressions représentée par `Expression<Func<int>>` serait convertie en un délégué du type `Func<int>`. Pour une expression lambda avec tout type de retour et liste d’arguments, il existe un type délégué qui est le type cible pour le code exécutable représenté par cette expression lambda.

Le type `LambdaExpression` contient des membres `Compile` et `CompileToMethod` que vous utiliseriez pour convertir une arborescence d’expressions en code exécutable. La méthode `Compile` crée un délégué. La méthode `CompileToMethod` met à jour un objet `MethodBuilder` avec le langage intermédiaire qui représente la sortie compilée de l’arborescence d’expressions. Notez que `CompileToMethod` n’est disponible que sur le framework de bureau complet, et non dans .NET Core.

Si vous le souhaitez, vous pouvez également fournir un `DebugInfoGenerator` qui recevra les informations de débogage de symbole pour l’objet délégué généré. Cela vous permet de convertir l’arborescence d’expressions en objet délégué et de disposer d’informations de débogage complètes sur le délégué généré.

Vous pouvez convertir une expression en délégué à l’aide du code suivant :

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

Notez que le type délégué est basé sur le type d’expression. Si vous souhaitez utiliser l’objet délégué d’une manière fortement typée, vous devez connaître le type de retour et la liste d’arguments. La méthode `LambdaExpression.Compile()` retourne le type `Delegate`. Vous devrez effectuer un cast vers le type délégué approprié pour que les outils de compilation puissent vérifier la liste d’arguments de type de retour.

## <a name="execution-and-lifetimes"></a>Exécution et durées de vie

Vous exécutez le code en appelant le délégué créé quand vous avez appelé `LambdaExpression.Compile()`. Vous pouvez l’observer ci-dessus, où `add.Compile()` retourne un délégué. L’appel de ce délégué en appelant `func()` exécute le code.

Ce délégué représente le code dans l’arborescence d’expressions. Vous pouvez conserver le handle de ce délégué et l’appeler ultérieurement. Vous n’avez pas besoin de compiler l’arborescence d’expressions chaque fois que vous souhaitez exécuter le code qu’elle représente. (N’oubliez pas que les arborescences d’expressions sont immuables ; compiler la même arborescence d’expressions ultérieurement crée un délégué qui exécute le même code.)

Je vous déconseille d’essayer de créer des mécanismes de mise en cache plus complexes pour améliorer les performances en évitant les appels de compilation inutiles. Comparer deux arborescences d’expressions arbitraires pour déterminer si elles représentent le même algorithme prend également beaucoup de temps. Vous vous rendrez sans doute compte que le temps de calcul économisé en évitant tout appel supplémentaire à `LambdaExpression.Compile()` sera largement contrebalancé par le temps passé à exécuter le code qui détermine si deux arborescences d’expressions génèrent le même code exécutable.

## <a name="caveats"></a>Mises en garde

Compiler une expression lambda en un délégué et appeler ce délégué sont l’une des opérations les plus simples que vous puissiez effectuer avec une arborescence d’expressions. Toutefois, même avec cette simple opération, il existe des pièges dont vous devez être conscient.

Les expressions lambda créent des fermetures sur toutes les variables locales qui sont référencées dans l’expression. Vous devez vérifier que toutes les variables qui font partie du délégué sont utilisables à l’emplacement où vous appelez `Compile` et quand vous exécutez le délégué résultant.

En règle générale, le compilateur s’assure que ce soit le cas. Toutefois, si votre expression accède à une variable qui implémente `IDisposable`, il est possible que votre code supprime l’objet alors qu’il est toujours détenu par l’arborescence d’expressions.

Par exemple, ce code fonctionne bien, car `int` n’implémente pas `IDisposable` :

```csharp
private static Func<int, int> CreateBoundFunc()
{
    var constant = 5; // constant is captured by the expression tree
    Expression<Func<int, int>> expression = (b) => constant + b;
    var rVal = expression.Compile();
    return rVal;
}
```

Le délégué a capturé une référence à la variable locale `constant`.
Cette variable est accessible à tout moment ultérieurement, quand la fonction retournée par `CreateBoundFunc` s’exécute.

Maintenant, examinez cette classe qui implémente `IDisposable` :

```csharp
public class Resource : IDisposable
{
    private bool isDisposed = false;
    public int Argument
    {
        get
        {
            if (!isDisposed)
                return 5;
            else throw new ObjectDisposedException("Resource");
        }
    }

    public void Dispose()
    {
        isDisposed = true;
    }
}
```

Si vous l’utilisez dans une expression comme illustré ci-dessous, vous obtenez une `ObjectDisposedException` quand vous exécutez le code référencé par la propriété `Resource.Argument` :

```csharp
private static Func<int, int> CreateBoundResource()
{
    using (var constant = new Resource()) // constant is captured by the expression tree
    {
        Expression<Func<int, int>> expression = (b) => constant.Argument + b;
        var rVal = expression.Compile();
        return rVal;
    }
}
```

Le délégué retourné par cette méthode a fermé l’objet `constant`, qui a été supprimé. (Il a été supprimé car il a été déclaré dans une instruction `using`.)

Désormais, quand vous exécuterez le délégué retourné par cette méthode, une `ObjectDisposedException` sera levée au moment de l’exécution.

Cela semble étrange d’avoir une erreur d’exécution qui représente une construction de compilation, mais cela fait partie des éventualités quand nous travaillons avec des arborescences d’expressions.

Comme il existe de nombreuses permutations de ce problème, il est difficile de proposer des conseils généraux pour l’éviter. Faites attention si vous accédez à des variables locales quand vous définissez des expressions et faites attention si vous accédez à l’état de l’objet actif (représenté par `this`) quand vous créez une arborescence d’expressions qui peut être retournée par une API publique.

Le code dans votre expression peut référencer des méthodes ou des propriétés dans d’autres assemblys. Ces assemblys doivent être accessibles quand l’expression est définie, quand elle est compilée et quand le délégué résultant est appelé. S’il n’est pas présent, vous recevrez une `ReferencedAssemblyNotFoundException`.

## <a name="summary"></a>Résumé

Les arborescences d’expressions qui représentent des expressions lambda peuvent être compilées pour créer un délégué exécutable. Cela fournit un mécanisme pour exécuter le code représenté par une arborescence d’expressions.

L’arborescence d’expressions représente le code qui s’exécuterait pour toute construction donnée que vous créez. Tant que l’environnement dans lequel vous compilez et exécutez le code correspond à celui dans lequel vous créez une expression, tout fonctionne comme prévu. Si ce n’est pas le cas, les erreurs sont très prévisibles et seront interceptées lors de vos premiers tests de n’importe quel code utilisant les arborescences d’expressions.

[Suivant -- Interprétation d’expressions](expression-trees-interpreting.md)
