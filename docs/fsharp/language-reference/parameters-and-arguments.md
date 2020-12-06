---
title: Paramètres et arguments
description: 'En savoir plus sur la prise en charge du langage F # pour définir des paramètres et passer des arguments à des fonctions, des méthodes et des propriétés.'
ms.date: 08/15/2020
ms.openlocfilehash: 3c391ca37a1cf3bd150316943e5b06efa532b317
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740287"
---
# <a name="parameters-and-arguments"></a>Paramètres et arguments

Cette rubrique décrit la prise en charge linguistique pour définir des paramètres et passer des arguments à des fonctions, des méthodes et des propriétés. Elle contient des informations sur la façon de passer par référence, ainsi que sur la façon de définir et d’utiliser des méthodes qui peuvent prendre un nombre variable d’arguments.

## <a name="parameters-and-arguments"></a>Paramètres et arguments

Le terme *paramètre* est utilisé pour décrire les noms des valeurs qui sont supposées être fournies. Le terme *argument* est utilisé pour les valeurs fournies pour chaque paramètre.

Les paramètres peuvent être spécifiés sous forme de tuple ou de formulaire curryfiée, ou dans une combinaison des deux. Vous pouvez passer des arguments à l’aide d’un nom de paramètre explicite. Les paramètres des méthodes peuvent être spécifiés comme facultatifs et donner une valeur par défaut.

## <a name="parameter-patterns"></a>Modèles de paramètres

Les paramètres fournis aux fonctions et aux méthodes sont, en général, des modèles séparés par des espaces. Cela signifie que, en principe, l’un des modèles décrits dans [expressions de correspondance](match-expressions.md) peut être utilisé dans une liste de paramètres pour une fonction ou un membre.

Les méthodes utilisent généralement la forme de tuple de passage des arguments. Cela permet d’obtenir un résultat plus clair du point de vue d’autres langages .NET, car la forme de tuple correspond à la façon dont les arguments sont passés dans les méthodes .NET.

La forme curryfiée est le plus souvent utilisée avec les fonctions créées à l’aide de `let` liaisons.

Le pseudo-code suivant montre des exemples de tuple et d’arguments curryfiés.

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

Les formulaires combinés sont possibles lorsque certains arguments se trouvent dans des tuples et d’autres non.

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

D’autres modèles peuvent également être utilisés dans les listes de paramètres, mais si le modèle de paramètre ne correspond pas à toutes les entrées possibles, il peut y avoir une correspondance incomplète au moment de l’exécution. L’exception `MatchFailureException` est générée lorsque la valeur d’un argument ne correspond pas aux critères spécifiés dans la liste de paramètres. Le compilateur émet un avertissement lorsqu’un modèle de paramètre autorise des correspondances incomplètes. Au moins un autre modèle est souvent utile pour les listes de paramètres et c’est le modèle de caractère générique. Vous utilisez le modèle de caractère générique dans une liste de paramètres lorsque vous souhaitez simplement ignorer tous les arguments fournis. Le code suivant illustre l’utilisation du modèle de caractère générique dans une liste d’arguments.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

Le modèle de caractère générique peut être utile lorsque vous n’avez pas besoin des arguments passés, comme dans le point d’entrée principal d’un programme, lorsque vous n’êtes pas intéressé par les arguments de ligne de commande qui sont normalement fournis en tant que tableau de chaînes, comme dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

Les autres modèles qui sont parfois utilisés dans les arguments sont le `as` modèle et les modèles d’identificateur associés aux unions discriminées et aux modèles actifs. Vous pouvez utiliser le modèle d’union discriminée à cas unique comme suit.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

La sortie est la suivante.

```console
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

Les modèles actifs peuvent être utiles comme paramètres, par exemple lors de la transformation d’un argument dans un format souhaité, comme dans l’exemple suivant :

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

Vous pouvez utiliser le `as` modèle pour stocker une valeur correspondante comme valeur locale, comme indiqué dans la ligne de code suivante.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

Un autre modèle qui est utilisé occasionnellement est une fonction qui laisse le dernier argument sans nom en fournissant, en tant que corps de la fonction, une expression lambda qui effectue immédiatement une correspondance de modèle sur l’argument implicite. La ligne de code suivante en est un exemple.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

Ce code définit une fonction qui prend une liste générique et retourne `true` si la liste est vide, et dans le `false` cas contraire. L’utilisation de ces techniques peut rendre le code plus difficile à lire.

Parfois, les modèles qui impliquent des correspondances incomplètes sont utiles, par exemple, si vous savez que les listes de votre programme ne comportent que trois éléments, vous pouvez utiliser un modèle comme celui qui suit dans une liste de paramètres.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

L’utilisation de modèles qui ont des correspondances incomplètes est réservée au prototypage rapide et à d’autres utilisations temporaires. Le compilateur émettra un avertissement pour ce type de code. Ces modèles ne peuvent pas couvrir le cas général de toutes les entrées possibles et ne conviennent donc pas aux API de composant.

## <a name="named-arguments"></a>Arguments nommés

Les arguments des méthodes peuvent être spécifiés par position dans une liste d’arguments séparée par des virgules, ou ils peuvent être passés explicitement à une méthode en fournissant le nom, suivi d’un signe égal et de la valeur à passer. S’ils sont spécifiés en fournissant le nom, ils peuvent apparaître dans un ordre différent de celui utilisé dans la déclaration.

Les arguments nommés peuvent rendre le code plus lisible et plus adaptable à certains types de modifications dans l’API, tels que la réorganisation des paramètres de méthode.

Les arguments nommés sont autorisés uniquement pour les méthodes, pas pour les `let` fonctions liées aux fonctions, les valeurs de fonctions ou les expressions lambda.

L’exemple de code suivant illustre l’utilisation d’arguments nommés.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

Dans un appel à un constructeur de classe, vous pouvez définir les valeurs des propriétés de la classe à l’aide d’une syntaxe similaire à celle des arguments nommés. L’exemple suivant illustre cette syntaxe.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

Pour plus d’informations, consultez [constructeurs (F #)](members/constructors.md).

## <a name="optional-parameters"></a>Paramètres facultatifs

Vous pouvez spécifier un paramètre facultatif pour une méthode à l’aide d’un point d’interrogation devant le nom du paramètre. Les paramètres facultatifs sont interprétés comme le type d’option F #, ce qui vous permet de les interroger de manière régulière que les types d’options sont interrogés, en utilisant une `match` expression avec `Some` et `None` . Les paramètres facultatifs sont autorisés uniquement sur les membres, et non sur les fonctions créées à l’aide de `let` liaisons.

Vous pouvez passer des valeurs facultatives existantes à la méthode par nom de paramètre, tel que `?arg=None` ou `?arg=Some(3)` `?arg=arg` . Cela peut être utile lors de la génération d’une méthode qui transmet des arguments facultatifs à une autre méthode.

Vous pouvez également utiliser une fonction `defaultArg` , qui définit une valeur par défaut d’un argument facultatif. La `defaultArg` fonction prend le paramètre facultatif comme premier argument et la valeur par défaut comme second.

L’exemple suivant illustre l’utilisation de paramètres facultatifs.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

La sortie est la suivante.

```console
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
```

Dans le cadre de C# et de Visual Basic Interop, vous pouvez utiliser les attributs `[<Optional; DefaultParameterValue<(...)>]` en F # pour que les appelants voient un argument comme facultatif. Cela équivaut à définir l’argument comme facultatif dans C#, comme dans `MyMethod(int i = 3)` .

```fsharp
open System
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue("Hello world")>] message) =
        printfn $"{message}"
```

Vous pouvez également spécifier un nouvel objet en tant que valeur de paramètre par défaut. Par exemple, le `Foo` membre peut avoir un facultatif `CancellationToken` comme entrée à la place :

```fsharp
open System.Threading
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue(CancellationToken())>] ct: CancellationToken) =
        printfn $"{ct}"
```

La valeur donnée comme argument de `DefaultParameterValue` doit correspondre au type du paramètre. Par exemple, ce qui suit n’est pas autorisé :

```fsharp
type C =
    static member Wrong([<Optional; DefaultParameterValue("string")>] i:int) = ()
```

Dans ce cas, le compilateur génère un avertissement et ignore les deux attributs. Notez que la valeur par défaut `null` doit être annotée de type, dans le cas contraire, le compilateur déduit le type incorrect, c.-à-d. `[<Optional; DefaultParameterValue(null:obj)>] o:obj` .

## <a name="passing-by-reference"></a>Passer par référence

La transmission d’une valeur F # par référence implique [types ByRef](byrefs.md), qui sont des types pointeur managés. Les instructions pour le type à utiliser sont les suivantes :

- Utilisez `inref<'T>` si vous devez uniquement lire le pointeur.
- Utilisez `outref<'T>` si vous devez uniquement écrire dans le pointeur.
- Utilisez `byref<'T>` si vous avez besoin de lire et d’écrire dans le pointeur.

```fsharp
let example1 (x: inref<int>) = printfn $"It's %d{x}"

let example2 (x: outref<int>) = x <- x + 1

let example3 (x: byref<int>) =
    printfn $"It's %d{x}"
    x <- x + 1

let test () =
    // No need to make it mutable, since it's read-only
    let x = 1
    example1 &x

    // Needs to be mutable, since we write to it
    let mutable y = 2
    example2 &y
    example3 &y // Now 'y' is 3
```

Étant donné que le paramètre est un pointeur et que la valeur est mutable, toute modification apportée à la valeur est conservée après l’exécution de la fonction.

Vous pouvez utiliser un tuple comme valeur de retour pour stocker des `out` paramètres dans les méthodes de la bibliothèque .net. Vous pouvez également traiter le `out` paramètre en tant que `byref` paramètre. L’exemple de code suivant illustre les deux méthodes.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a>Tableaux de paramètres

Il est parfois nécessaire de définir une fonction qui accepte un nombre arbitraire de paramètres de type hétérogène. Il n’est pas pratique de créer toutes les méthodes surchargées possibles pour tenir compte de tous les types qui pourraient être utilisés. Les implémentations .NET prennent en charge ces méthodes par le biais de la fonctionnalité de tableau de paramètres. Une méthode qui accepte un tableau de paramètres dans sa signature peut être fournie avec un nombre arbitraire de paramètres. Les paramètres sont placés dans un tableau. Le type des éléments du tableau détermine les types de paramètres qui peuvent être passés à la fonction. Si vous définissez le tableau de paramètres avec `System.Object` comme type d’élément, le code client peut passer des valeurs de n’importe quel type.

En F #, les tableaux de paramètres ne peuvent être définis que dans des méthodes. Elles ne peuvent pas être utilisées dans des fonctions autonomes ou des fonctions définies dans des modules.

Vous définissez un tableau de paramètres à l’aide de l' `ParamArray` attribut. L' `ParamArray` attribut ne peut être appliqué qu’au dernier paramètre.

Le code suivant illustre l’appel d’une méthode .NET qui accepte un tableau de paramètres et la définition d’un type en F # qui a une méthode qui prend un tableau de paramètres.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

Lorsqu’il est exécuté dans un projet, la sortie du code précédent se présente comme suit :

```console
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a>Voir aussi

- [Members](./members/index.md) (Membres)
