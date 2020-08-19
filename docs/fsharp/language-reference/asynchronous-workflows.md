---
title: Workflows asynchrones
description: 'En savoir plus sur la prise en charge dans le langage de programmation F # pour effectuer des calculs de manière asynchrone, qui s’exécutent sans bloquer l’exécution d’autres travaux.'
ms.date: 08/15/2020
ms.openlocfilehash: ac727fc630f13db01da964131ab39dc242a12cd1
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557709"
---
# <a name="asynchronous-workflows"></a>Flux de travail asynchrones

Cet article décrit la prise en charge dans F # pour effectuer des calculs de manière asynchrone, autrement dit, sans bloquer l’exécution d’autres travaux. Par exemple, les calculs asynchrones peuvent être utilisés pour écrire des applications qui ont des interfaces utilisateur qui restent réactives aux utilisateurs au fur et à mesure que l’application exécute d’autres tâches.

## <a name="syntax"></a>Syntaxe

```fsharp
async { expression }
```

## <a name="remarks"></a>Notes

Dans la syntaxe précédente, le calcul représenté par `expression` est configuré pour s’exécuter de façon asynchrone, autrement dit, sans bloquer le thread de calcul actuel lorsque des opérations de veille asynchrones, des e/s et d’autres opérations asynchrones sont effectuées. Les calculs asynchrones sont souvent démarrés sur un thread d’arrière-plan pendant que l’exécution se poursuit sur le thread actuel. Le type de l’expression est `Async<'T>` , où `'T` est le type retourné par l’expression lorsque le `return` mot clé est utilisé. Le code d’une telle expression est appelé *bloc asynchrone*ou *bloc Async*.

Il existe plusieurs façons de programmer de façon asynchrone, et la [`Async`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html) classe fournit des méthodes qui prennent en charge plusieurs scénarios. L’approche générale consiste à créer `Async` des objets qui représentent le calcul ou les calculs que vous souhaitez exécuter de façon asynchrone, puis à démarrer ces calculs à l’aide de l’une des fonctions de déclenchement. Les diverses fonctions de déclenchement offrent différentes façons d’exécuter des calculs asynchrones, et celle que vous utilisez varie selon que vous souhaitez utiliser le thread actuel, un thread d’arrière-plan ou un objet de tâche .NET Framework, et s’il existe des fonctions de continuation qui doivent s’exécuter lorsque le calcul se termine. Par exemple, pour démarrer un calcul asynchrone sur le thread actuel, vous pouvez utiliser [`Async.StartImmediate`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#StartImmediate) . Quand vous démarrez un calcul asynchrone à partir du thread d’interface utilisateur, vous ne bloquez pas la boucle d’événements principale qui traite les actions de l’utilisateur, telles que les séquences de touches et l’activité de la souris, afin que votre application reste réactive.

## <a name="asynchronous-binding-by-using-let"></a>Liaison asynchrone à l’aide de Let !

Dans un flux de travail asynchrone, certaines expressions et opérations sont synchrones, tandis que d’autres sont des calculs plus longs conçus pour retourner un résultat de manière asynchrone. Lorsque vous appelez une méthode de façon asynchrone, au lieu d’une `let` liaison ordinaire, vous utilisez `let!` . L’effet de `let!` est de permettre à l’exécution de continuer sur d’autres calculs ou threads à mesure que le calcul est effectué. Une fois le côté droit de la `let!` liaison retourné, le reste du flux de travail asynchrone reprend l’exécution.

Le code suivant illustre la différence entre `let` et `let!` . La ligne de code qui utilise `let` crée simplement un calcul asynchrone sous la forme d’un objet que vous pouvez exécuter ultérieurement à l’aide de, par exemple `Async.StartImmediate` ou [`Async.RunSynchronously`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#RunSynchronously) . La ligne de code qui utilise `let!` démarre le calcul, puis le thread est suspendu jusqu’à ce que le résultat soit disponible, auquel cas l’exécution continue.

```fsharp
// let just stores the result as an asynchronous operation.
let (result1 : Async<byte[]>) = stream.AsyncRead(bufferSize)
// let! completes the asynchronous operation and returns the data.
let! (result2 : byte[])  = stream.AsyncRead(bufferSize)
```

En plus de `let!` , vous pouvez utiliser `use!` pour effectuer des liaisons asynchrones. La différence entre `let!` et `use!` est identique à la différence entre `let` et `use` . Pour `use!` , l’objet est supprimé à la fermeture de l’étendue actuelle. Notez que dans la version actuelle du langage F #, `use!` ne permet pas à une valeur d’être initialisée à la valeur null, bien que le fasse `use` .

## <a name="asynchronous-primitives"></a>Primitives asynchrones

Une méthode qui effectue une seule tâche asynchrone et retourne le résultat est appelée une *primitive asynchrone*, et celles-ci sont conçues spécifiquement pour une utilisation avec `let!` . Plusieurs primitives asynchrones sont définies dans la bibliothèque principale F #. Deux de ces méthodes pour les applications Web sont définies dans le module [`FSharp.Control.WebExtensions`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-webextensions.html) : [`WebRequest.AsyncGetResponse`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-webextensions.html#AsyncGetResponse) et [`WebClient.AsyncDownloadString`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-webextensions.html#AsyncDownloadString) . Les deux primitives téléchargent des données à partir d’une page Web, en fonction d’une URL. `AsyncGetResponse` produit un `System.Net.WebResponse` objet et `AsyncDownloadString` produit une chaîne qui représente le code HTML d’une page Web.

Plusieurs primitives pour les opérations d’e/s asynchrones sont incluses dans le [`FSharp.Control.CommonExtensions`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-commonextensions.html) module. Ces méthodes d’extension de la `System.IO.Stream` classe sont [`Stream.AsyncRead`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-commonextensions.html#AsyncRead) et [`Stream.AsyncWrite`](hhttps://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-commonextensions.html#AsyncWrite) .

Vous pouvez également écrire vos propres primitives asynchrones en définissant une fonction dont le corps complet est placé dans un bloc Async.

Pour utiliser des méthodes asynchrones dans les .NET Framework conçues pour d’autres modèles asynchrones avec le modèle de programmation asynchrone F #, vous créez une fonction qui retourne un objet F # `Async` . La bibliothèque F # possède des fonctions qui facilitent cette tâche.

Vous trouverez ici un exemple d’utilisation de workflows asynchrones. Il existe de nombreux autres éléments dans la documentation pour les méthodes de la [classe Async](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html).

Cet exemple montre comment utiliser des flux de travail asynchrones pour effectuer des calculs en parallèle.

Dans l’exemple de code suivant, une fonction `fetchAsync` obtient le texte HTML retourné à partir d’une requête Web. La `fetchAsync` fonction contient un bloc de code asynchrone. Lorsqu’une liaison est établie avec le résultat d’une primitive asynchrone, dans ce cas [`AsyncDownloadString`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-webextensions.html#AsyncDownloadString) , `let!` est utilisé à la place de `let` .

Vous utilisez la fonction [`Async.RunSynchronously`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#RunSynchronously) pour exécuter une opération asynchrone et attendre son résultat. Par exemple, vous pouvez exécuter plusieurs opérations asynchrones en parallèle en utilisant la [`Async.Parallel`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#Parallel) fonction avec la `Async.RunSynchronously` fonction. La `Async.Parallel` fonction prend une liste des `Async` objets, définit le code pour chaque objet de `Async` tâche afin qu’il s’exécute en parallèle et retourne un `Async` objet qui représente le calcul parallèle. Tout comme pour une opération unique, vous appelez `Async.RunSynchronously` pour démarrer l’exécution.

La `runAll` fonction lance trois workflows asynchrones en parallèle et attend la fin de leur exécution.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet8003.fs)]

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage F #](index.md)
- [Expressions de calcul](computation-expressions.md)
- [Control. Async, classe](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.async-class-%5bfsharp%5d)
