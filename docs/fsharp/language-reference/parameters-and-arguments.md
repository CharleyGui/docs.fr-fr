---
title: Paramètres et arguments
description: Renseignez-vous sur le support linguistique de FMD pour définir les paramètres et transmettre des arguments aux fonctions, aux méthodes et aux propriétés.
ms.date: 12/04/2019
ms.openlocfilehash: b234ef939128e7cf09d35f9580d4d5010d7dc639
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400196"
---
# <a name="parameters-and-arguments"></a>Paramètres et arguments

Ce sujet décrit le support linguistique pour définir les paramètres et passer des arguments aux fonctions, aux méthodes et aux propriétés. Il comprend des informations sur la façon de passer par référence, et comment définir et utiliser des méthodes qui peuvent prendre un nombre variable d’arguments.

## <a name="parameters-and-arguments"></a>Paramètres et arguments

Le *paramètre* de terme est utilisé pour décrire les noms des valeurs qui devraient être fournies. Le terme *argument* est utilisé pour les valeurs prévues pour chaque paramètre.

Les paramètres peuvent être spécifiés sous forme de tuple ou de curry, ou dans une combinaison des deux. Vous pouvez passer des arguments en utilisant un nom de paramètre explicite. Les paramètres des méthodes peuvent être spécifiés comme facultatifs et une valeur par défaut.

## <a name="parameter-patterns"></a>Modèles de paramètres

Les paramètres fournis aux fonctions et aux méthodes sont, en général, des modèles séparés par des espaces. Cela signifie que, en principe, l’un des modèles décrits dans [Les expressions de correspondance](match-expressions.md) peut être utilisé dans une liste de paramètres pour une fonction ou un membre.

Les méthodes utilisent généralement la forme de tuple des arguments de passage. Cela permet d’obtenir un résultat plus clair du point de vue d’autres langues .NET parce que la forme de tuple correspond à la façon dont les arguments sont adoptés dans des méthodes .NET.

La forme au curry est le plus `let` souvent utilisée avec les fonctions créées à l’aide de fixations.

Le pseudocode suivant montre des exemples de tuple et d’arguments au curry.

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

Des formes combinées sont possibles lorsque certains arguments sont en tuples et d’autres ne le sont pas.

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

D’autres modèles peuvent également être utilisés dans les listes de paramètres, mais si le modèle de paramètre ne correspond pas à toutes les entrées possibles, il pourrait y avoir une correspondance incomplète au moment de l’exécution. L’exception `MatchFailureException` est générée lorsque la valeur d’un argument ne correspond pas aux modèles spécifiés dans la liste des paramètres. Le compilateur émet un avertissement lorsqu’un modèle de paramètre permet des correspondances incomplètes. Au moins un autre modèle est généralement utile pour les listes de paramètres, et c’est le modèle wildcard. Vous utilisez le modèle wildcard dans une liste de paramètres lorsque vous voulez simplement ignorer tous les arguments qui sont fournis. Le code suivant illustre l’utilisation du modèle wildcard dans une liste d’arguments.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

Le modèle wildcard peut être utile chaque fois que vous n’avez pas besoin des arguments passés, comme dans le point d’entrée principal d’un programme, lorsque vous n’êtes pas intéressé par les arguments de ligne de commande qui sont normalement fournis comme un tableau de chaîne, comme dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

D’autres modèles qui sont `as` parfois utilisés dans les arguments sont le modèle, et les modèles d’identification associés à des syndicats discriminés et des modèles actifs. Vous pouvez utiliser le modèle syndical à cas unique et discriminé comme suit.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

La sortie est la suivante.

```console
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

Les modèles actifs peuvent être utiles comme paramètres, par exemple, lors de la transformation d’un argument en un format souhaité, comme dans l’exemple suivant :

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

Vous pouvez `as` utiliser le modèle pour stocker une valeur appariée comme valeur locale, comme le montre la ligne de code suivante.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

Un autre modèle qui est utilisé de temps en temps est une fonction qui laisse le dernier argument sans nom en fournissant, comme le corps de la fonction, une expression lambda qui effectue immédiatement une correspondance de modèle sur l’argument implicite. Un exemple de ceci est la ligne suivante de code.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

Ce code définit une fonction qui prend `true` une liste générique `false` et renvoie si la liste est vide, et autrement. L’utilisation de telles techniques peut rendre le code plus difficile à lire.

De temps en temps, les modèles qui impliquent des correspondances incomplètes sont utiles, par exemple, si vous savez que les listes de votre programme n’ont que trois éléments, vous pouvez utiliser un modèle comme ce qui suit dans une liste de paramètres.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

L’utilisation de modèles qui ont des correspondances incomplètes est mieux réservée au prototypage rapide et à d’autres utilisations temporaires. Le compilateur émettra un avertissement pour un tel code. Ces modèles ne peuvent pas couvrir le cas général de toutes les entrées possibles et ne conviennent donc pas aux API composant.

## <a name="named-arguments"></a>Arguments nommés

Les arguments en faveur de méthodes peuvent être spécifiés par position dans une liste d’arguments séparées par virgule, ou ils peuvent être transmis à une méthode explicitement en fournissant le nom, suivi d’un signe égal et de la valeur à transmettre. S’ils sont spécifiés en fournissant le nom, ils peuvent apparaître dans un ordre différent de celui utilisé dans la déclaration.

Les arguments nommés peuvent rendre le code plus lisible et plus adaptable à certains types de modifications de l’API, comme une réorganisation des paramètres de la méthode.

Les arguments nommés ne sont `let`autorisés que pour les méthodes, pas pour les fonctions liées, les valeurs de fonction, ou les expressions lambda.

L’exemple de code suivant montre l’utilisation d’arguments nommés.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

Dans un appel à un constructeur de classe, vous pouvez définir les valeurs des propriétés de la classe en utilisant une syntaxe similaire à celle des arguments nommés. L’exemple suivant montre cette syntaxe.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

Pour plus d’informations, voir [Constructors (F)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).

## <a name="optional-parameters"></a>Paramètres facultatifs

Vous pouvez spécifier un paramètre facultatif pour une méthode en utilisant un point d’interrogation devant le nom du paramètre. Les paramètres facultatifs sont interprétés comme le type d’option F, de sorte que `match` vous `Some` pouvez `None`les interroger de la manière régulière que les types d’options sont interrogés, en utilisant une expression avec et . Les paramètres facultatifs ne sont autorisés que `let` sur les membres, et non sur les fonctions créées par l’utilisation de fixations.

Vous pouvez transmettre les valeurs facultatives `?arg=None` existantes à la méthode par nom de paramètre, comme ou `?arg=Some(3)` `?arg=arg`. Cela peut être utile lors de la construction d’une méthode qui passe arguments optionnels à une autre méthode.

Vous pouvez également `defaultArg`utiliser une fonction , qui définit une valeur par défaut d’un argument facultatif. La `defaultArg` fonction prend le paramètre facultatif comme premier argument et la valeur par défaut comme le second.

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

Aux fins de l’interop de base visuelle `[<Optional; DefaultParameterValue<(...)>]` et de C, vous pouvez utiliser les attributs dans le F, de sorte que les appelants verront un argument comme facultatif. Cela équivaut à définir l’argument comme `MyMethod(int i = 3)`facultatif dans C ' comme dans .

```fsharp
open System
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue("Hello world")>] message) =
        printfn "%s" message
```

Vous pouvez également spécifier un nouvel objet comme valeur de paramètre par défaut. Par exemple, `Foo` le membre `CancellationToken` pourrait avoir une option comme entrée à la place :

```fsharp
open System.Threading
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue(CancellationToken())>] ct: CancellationToken) =
        printfn "%A" ct
```

La valeur donnée `DefaultParameterValue` comme argument doit correspondre au type de paramètre. Par exemple, ce qui suit n’est pas autorisé :

```fsharp
type C =
    static member Wrong([<Optional; DefaultParameterValue("string")>] i:int) = ()
```

Dans ce cas, le compilateur génère un avertissement et ignorera les deux attributs tout à fait. Notez que `null` la valeur par défaut doit être annotée de type, comme sinon le `[<Optional; DefaultParameterValue(null:obj)>] o:obj`compilateur déduit le mauvais type, c’est-à-dire .

## <a name="passing-by-reference"></a>Passer par référence

Passer une valeur F par référence implique [byrefs](byrefs.md), qui sont gérés types de pointeurs. Les conseils pour le type à utiliser sont les suivants :

- Utilisez `inref<'T>` si vous avez seulement besoin de lire le pointeur.
- Utilisez `outref<'T>` si vous avez seulement besoin d’écrire sur le pointeur.
- Utilisez `byref<'T>` si vous avez besoin à la fois lire et écrire sur le pointeur.

```fsharp
let example1 (x: inref<int>) = printfn "It's %d" x

let example2 (x: outref<int>) = x <- x + 1

let example3 (x: byref<int>) =
    printfn "It'd %d" x
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

Étant donné que le paramètre est un pointeur et que la valeur est mutable, toute modification de la valeur est conservée après l’exécution de la fonction.

Vous pouvez utiliser un tuple comme `out` valeur de retour pour stocker tous les paramètres dans les méthodes de bibliothèque .NET. Alternativement, vous pouvez `out` traiter `byref` le paramètre comme un paramètre. L’exemple de code suivant illustre les deux façons.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a>Tableaux de paramètres

Il est parfois nécessaire de définir une fonction qui prend un nombre arbitraire de paramètres de type hétérogène. Il ne serait pas pratique de créer toutes les méthodes surchargées possibles pour tenir compte de tous les types qui pourraient être utilisés. Les implémentations .NET fournissent un soutien à ces méthodes grâce à la fonction de tableau de paramètres. Une méthode qui prend un tableau de paramètres dans sa signature peut être fournie avec un nombre arbitraire de paramètres. Les paramètres sont mis dans un tableau. Le type d’éléments de tableau détermine les types de paramètres qui peuvent être transmis à la fonction. Si vous définissez `System.Object` le tableau de paramètres comme type d’élément, le code client peut passer des valeurs de n’importe quel type.

Dans les tableaux de paramètres, les paramètres ne peuvent être définis que dans les méthodes. Ils ne peuvent pas être utilisés dans des fonctions ou des fonctions autonomes qui sont définies dans des modules.

Vous définissez un tableau `ParamArray` de paramètres en utilisant l’attribut. L’attribut `ParamArray` ne peut être appliqué qu’au dernier paramètre.

Le code suivant illustre à la fois l’appel d’une méthode .NET qui prend un tableau de paramètres et la définition d’un type dans F 'qui a une méthode qui prend un tableau de paramètres.

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

Lorsqu’il est exécuté dans un projet, la sortie du code précédent est la suivante :

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

- [Membres](./members/index.md)
