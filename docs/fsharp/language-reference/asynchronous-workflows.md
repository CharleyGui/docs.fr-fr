---
title: Workflows asynchrones
description: 'En savoir plus sur la prise en charge dans le langage de programmation F # pour effectuer des calculs de manière asynchrone, qui s’exécutent sans bloquer l’exécution d’autres travaux.'
ms.date: 05/16/2016
ms.openlocfilehash: 3bc24639b329401a8f944488e974f0739d4680df
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855463"
---
# <a name="asynchronous-workflows"></a>Flux de travail asynchrones

Cet article décrit la prise en charge dans F # pour effectuer des calculs de manière asynchrone, autrement dit, sans bloquer l’exécution d’autres travaux. Par exemple, les calculs asynchrones peuvent être utilisés pour écrire des applications qui ont des interfaces utilisateur qui restent réactives aux utilisateurs au fur et à mesure que l’application exécute d’autres tâches.

> [!NOTE]
> La référence de l’API docs.microsoft.com pour F # n’est pas terminée. Si vous rencontrez des liens rompus, consultez plutôt [la documentation de la bibliothèque principale F #](https://fsharp.github.io/fsharp-core-docs/) .

## <a name="syntax"></a>Syntaxe

```fsharp
async { expression }
```

## <a name="remarks"></a>Notes

Dans la syntaxe précédente, le calcul représenté par `expression` est configuré pour s’exécuter de façon asynchrone, autrement dit, sans bloquer le thread de calcul actuel lorsque des opérations de veille asynchrones, des e/s et d’autres opérations asynchrones sont effectuées. Les calculs asynchrones sont souvent démarrés sur un thread d’arrière-plan pendant que l’exécution se poursuit sur le thread actuel. Le type de l’expression est `Async<'T>` , où `'T` est le type retourné par l’expression lorsque le `return` mot clé est utilisé. Le code d’une telle expression est appelé *bloc asynchrone*ou *bloc Async*.

Il existe plusieurs façons de programmer de façon asynchrone, et la [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7) classe fournit des méthodes qui prennent en charge plusieurs scénarios. L’approche générale consiste à créer `Async` des objets qui représentent le calcul ou les calculs que vous souhaitez exécuter de façon asynchrone, puis à démarrer ces calculs à l’aide de l’une des fonctions de déclenchement. Les diverses fonctions de déclenchement offrent différentes façons d’exécuter des calculs asynchrones, et celle que vous utilisez varie selon que vous souhaitez utiliser le thread actuel, un thread d’arrière-plan ou un objet de tâche .NET Framework, et s’il existe des fonctions de continuation qui doivent s’exécuter lorsque le calcul se termine. Par exemple, pour démarrer un calcul asynchrone sur le thread actuel, vous pouvez utiliser [`Async.StartImmediate`](https://msdn.microsoft.com/library/2f71d1cc-187f-48cf-ac66-e7fda41c46e3) . Quand vous démarrez un calcul asynchrone à partir du thread d’interface utilisateur, vous ne bloquez pas la boucle d’événements principale qui traite les actions de l’utilisateur, telles que les séquences de touches et l’activité de la souris, afin que votre application reste réactive.

## <a name="asynchronous-binding-by-using-let"></a>Liaison asynchrone à l’aide de Let !

Dans un flux de travail asynchrone, certaines expressions et opérations sont synchrones, tandis que d’autres sont des calculs plus longs conçus pour retourner un résultat de manière asynchrone. Lorsque vous appelez une méthode de façon asynchrone, au lieu d’une `let` liaison ordinaire, vous utilisez `let!` . L’effet de `let!` est de permettre à l’exécution de continuer sur d’autres calculs ou threads à mesure que le calcul est effectué. Une fois le côté droit de la `let!` liaison retourné, le reste du flux de travail asynchrone reprend l’exécution.

Le code suivant illustre la différence entre `let` et `let!` . La ligne de code qui utilise `let` crée simplement un calcul asynchrone sous la forme d’un objet que vous pouvez exécuter ultérieurement à l’aide de, par exemple `Async.StartImmediate` ou [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) . La ligne de code qui utilise `let!` démarre le calcul, puis le thread est suspendu jusqu’à ce que le résultat soit disponible, auquel cas l’exécution continue.

```fsharp
// let just stores the result as an asynchronous operation.
let (result1 : Async<byte[]>) = stream.AsyncRead(bufferSize)
// let! completes the asynchronous operation and returns the data.
let! (result2 : byte[])  = stream.AsyncRead(bufferSize)
```

En plus de `let!` , vous pouvez utiliser `use!` pour effectuer des liaisons asynchrones. La différence entre `let!` et `use!` est identique à la différence entre `let` et `use` . Pour `use!` , l’objet est supprimé à la fermeture de l’étendue actuelle. Notez que dans la version actuelle du langage F #, `use!` ne permet pas à une valeur d’être initialisée à la valeur null, bien que le fasse `use` .

## <a name="asynchronous-primitives"></a>Primitives asynchrones

Une méthode qui effectue une seule tâche asynchrone et retourne le résultat est appelée une *primitive asynchrone*, et celles-ci sont conçues spécifiquement pour une utilisation avec `let!` . Plusieurs primitives asynchrones sont définies dans la bibliothèque principale F #. Deux de ces méthodes pour les applications Web sont définies dans le module [`Microsoft.FSharp.Control.WebExtensions`](https://msdn.microsoft.com/library/95ef17bc-ee3f-44ba-8a11-c90fcf4cf003) : [`WebRequest.AsyncGetResponse`](https://msdn.microsoft.com/library/09a60c31-e6e2-4b5c-ad23-92a86e50060c) et [`WebClient.AsyncDownloadString`](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a) . Les deux primitives téléchargent des données à partir d’une page Web, en fonction d’une URL. `AsyncGetResponse`produit un `System.Net.WebResponse` objet et `AsyncDownloadString` produit une chaîne qui représente le code HTML d’une page Web.

Plusieurs primitives pour les opérations d’e/s asynchrones sont incluses dans le [`Microsoft.FSharp.Control.CommonExtensions`](https://msdn.microsoft.com/library/2edb67cb-6814-4a30-849f-b6dbdd042396) module. Ces méthodes d’extension de la `System.IO.Stream` classe sont [`Stream.AsyncRead`](https://msdn.microsoft.com/library/85698aaa-bdda-47e6-abed-3730f59fda5e) et [`Stream.AsyncWrite`](https://msdn.microsoft.com/library/1b0a2751-e42a-47e1-bd27-020224adc618) .

Vous pouvez également écrire vos propres primitives asynchrones en définissant une fonction dont le corps complet est placé dans un bloc Async.

Pour utiliser des méthodes asynchrones dans les .NET Framework conçues pour d’autres modèles asynchrones avec le modèle de programmation asynchrone F #, vous créez une fonction qui retourne un objet F # `Async` . La bibliothèque F # possède des fonctions qui facilitent cette tâche.

Vous trouverez ici un exemple d’utilisation de workflows asynchrones. Il existe de nombreux autres éléments dans la documentation pour les méthodes de la [classe Async](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).

Cet exemple montre comment utiliser des flux de travail asynchrones pour effectuer des calculs en parallèle.

Dans l’exemple de code suivant, une fonction `fetchAsync` obtient le texte HTML retourné à partir d’une requête Web. La `fetchAsync` fonction contient un bloc de code asynchrone. Quand une liaison est établie avec le résultat d’une primitive asynchrone, dans ce cas [`AsyncDownloadString`](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a) , Let ! est utilisé à la place de Let.

Vous utilisez la fonction [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) pour exécuter une opération asynchrone et attendre son résultat. Par exemple, vous pouvez exécuter plusieurs opérations asynchrones en parallèle en utilisant la [`Async.Parallel`](https://msdn.microsoft.com/library/aa9b0355-2d55-4858-b943-cbe428de9dc4) fonction avec la `Async.RunSynchronously` fonction. La `Async.Parallel` fonction prend une liste des `Async` objets, définit le code pour chaque objet de `Async` tâche afin qu’il s’exécute en parallèle et retourne un `Async` objet qui représente le calcul parallèle. Tout comme pour une opération unique, vous appelez `Async.RunSynchronously` pour démarrer l’exécution.

La `runAll` fonction lance trois workflows asynchrones en parallèle et attend la fin de leur exécution.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet8003.fs)]

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage F #](index.md)
- [Expressions de calcul](computation-expressions.md)
- [Control. Async, classe](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.async-class-%5bfsharp%5d)
