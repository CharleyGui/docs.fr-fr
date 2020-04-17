---
title: Programmation Async
description: Découvrez comment FMD fournit un soutien propre à l’asynchronie basé sur un modèle de programmation au niveau de la langue dérivé des concepts de programmation fonctionnelle de base.
ms.date: 12/17/2018
ms.openlocfilehash: 9b2e3057c126d84474c21fde653da5bbee32938a
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608034"
---
# <a name="async-programming-in-f"></a>Programmation Async en F\#

La programmation asynchrone est un mécanisme qui est essentiel aux applications modernes pour diverses raisons. Il y a deux cas d’utilisation primaire que la plupart des développeurs rencontreront :

- Présentation d’un processus serveur qui peut traiter un nombre important de demandes entrantes simultanées, tout en minimisant les ressources système occupées pendant le traitement des demandes, vous attendez des entrées de systèmes ou de services externes à ce processus.
- Maintenir une interface utilisateur ou un thread principal réactif tout en progressant simultanément dans les travaux d’arrière-plan

Bien que le travail de fond implique souvent l’utilisation de plusieurs threads, il est important de considérer les concepts d’asynchrone et multi-threading séparément. En fait, il s’agit de préoccupations distinctes, et l’une n’implique pas l’autre. Ce qui suit dans cet article décrit cela plus en détail.

## <a name="asynchrony-defined"></a>Asynchrony défini

Le point précédent - que l’asynchronie est indépendante de l’utilisation de plusieurs threads - vaut la peine d’expliquer un peu plus loin. Il y a trois concepts qui sont parfois liés, mais strictement indépendants les uns des autres :

- La concurrence; lorsque plusieurs calculs s’exécutent dans des périodes de temps qui se chevauchent.
- Le parallélisme; lorsque plusieurs calculs ou plusieurs parties d’un calcul unique s’exécutent exactement en même temps.
- Asynchrony; lorsqu’un ou plusieurs calculs peuvent s’exécuter séparément du flux principal du programme.

Tous les trois sont des concepts orthogonaux, mais peuvent être facilement confondus, surtout quand ils sont utilisés ensemble. Par exemple, vous devrez peut-être exécuter plusieurs calculs asynchrones en parallèle. Cela ne signifie pas que le parallélisme ou l’asynchrone s’impliquent les uns les autres.

Si vous considérez l’étymologie du mot «asynchrone», il ya deux pièces impliquées:

- "a", c’est-à-dire "non".
- "synchrone", c’est-à-dire "en même temps".

Lorsque vous mettez ces deux termes ensemble, vous verrez que "asynchrone" signifie "pas en même temps". Et voilà ! Il n’y a aucune implication de concordance ou de parallélisme dans cette définition. Cela est également vrai dans la pratique.

Concrètement, les calculs asynchrones dans le F sont programmés pour exécuter indépendamment du flux principal du programme. Cela n’implique pas la concurrence ou le parallélisme, ni cela n’implique qu’un calcul se produit toujours en arrière-plan. En fait, les calculs asynchrones peuvent même exécuter de façon synchrone, selon la nature du calcul et de l’environnement dans lequel le calcul est exécuté.

Le principal plat à emporter que vous devriez avoir est que les calculs asynchrones sont indépendants du flux principal du programme. Bien qu’il y ait peu de garanties quant au moment ou à la façon dont un calcul asynchrone s’exécute, il existe quelques approches pour les orchestrer et les planifier. Le reste de cet article explore les concepts de base pour l’asynchrone de F et comment utiliser les types, les fonctions et les expressions intégrées dans le F.

## <a name="core-concepts"></a>Principaux concepts

Dans la programmation asynchrone, la programmation asynchrone est centrée autour de trois concepts fondamentaux :

- Le `Async<'T>` type, qui représente un calcul asynchrone composable.
- Les `Async` fonctions du module, qui vous permettent de planifier des travaux asynchrones, de composer des calculs asynchrones, et de transformer des résultats asynchrones.
- `async { }` [L’expression de calcul](../../language-reference/computation-expressions.md), qui fournit une syntaxe pratique pour la construction et le contrôle des calculs asynchrones.

Vous pouvez voir ces trois concepts dans l’exemple suivant :

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    printTotalFileBytes "path-to-file.txt"
    |> Async.RunSynchronously

    Console.Read() |> ignore
    0
```

Dans l’exemple, la `printTotalFileBytes` `string -> Async<unit>`fonction est de type . Appeler la fonction n’exécute pas réellement le calcul asynchrone. Au lieu de `Async<unit>` cela, il renvoie un qui agit comme une *spécification* de l’œuvre qui est d’exécuter asynchrone. Il `Async.AwaitTask` appelle dans son corps, qui <xref:System.IO.File.ReadAllBytesAsync%2A> convertit le résultat d’un type approprié.

Une autre ligne importante `Async.RunSynchronously`est l’appel à . Il s’agit de l’une des fonctions de démarrage du module Async que vous aurez besoin d’appeler si vous voulez réellement exécuter un calcul asynchrone F.

Il s’agit d’une différence fondamentale `async` avec le style de programmation de base visuelle et C. Dans les calculs asynchrones, on peut penser que les tâches froides sont considérées comme **des tâches froides.** Ils doivent être explicitement commencés à exécuter réellement. Cela a quelques avantages, car il vous permet de combiner et séquencer un travail asynchrone beaucoup plus facilement que dans C ou Visual Basic.

## <a name="combine-asynchronous-computations"></a>Combinez des calculs asynchrones

Voici un exemple qui s’appuie sur le précédent en combinant les calculs :

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    argv
    |> Array.map printTotalFileBytes
    |> Async.Parallel
    |> Async.Ignore
    |> Async.RunSynchronously

    0
```

Comme vous pouvez `main` le voir, la fonction a un peu plus d’appels effectués. Conceptuellement, il fait ce qui suit :

1. Transformez les arguments `Async<unit>` de la ligne `Array.map`de commande en calculs avec .
2. Créez `Async<'T[]>` un qui planifie `printTotalFileBytes` et exécute les calculs en parallèle quand il s’exécute.
3. Créez `Async<unit>` un calcul parallèle qui exécutera le calcul parallèle et ignorera son résultat.
4. Exécutez explicitement le dernier `Async.RunSynchronously` calcul avec et bloquez jusqu’à ce qu’il soit terminé.

Lorsque ce programme `printTotalFileBytes` s’exécute, fonctionne en parallèle pour chaque argument de la ligne de commande. Parce que les calculs asynchrones exécutent indépendamment du flux de programme, il n’y a aucun ordre dans lequel ils impriment leurs informations et finissent d’exécuter. Les calculs seront programmés en parallèle, mais leur ordre d’exécution n’est pas garanti.

## <a name="sequence-asynchronous-computations"></a>Séquences de calculs asynchrones

Parce `Async<'T>` que c’est une spécification du travail plutôt qu’une tâche déjà en cours d’exécution, vous pouvez effectuer des transformations plus complexes facilement. Voici un exemple qui séquence un ensemble de calculs Async afin qu’ils s’exécutent l’un après l’autre.

```fsharp
let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    argv
    |> Array.map printTotalFileBytes
    |> Async.Sequential
    |> Async.Ignore
    |> Async.RunSynchronously
    |> ignore
```

Cela permettra `printTotalFileBytes` d’exécuter dans l’ordre des éléments de plutôt que de `argv` les planifier en parallèle. Étant donné que le prochain élément ne sera programmé qu’après la fin de l’exécution du dernier calcul, les calculs sont séquencés de telle sorte qu’il n’y ait pas de chevauchement dans leur exécution.

## <a name="important-async-module-functions"></a>Fonctions importantes du module Async

Lorsque vous écrivez du code async en F, vous interagissez généralement avec un cadre qui gère la planification des calculs pour vous. Cependant, ce n’est pas toujours le cas, il est donc bon d’apprendre les différentes fonctions de départ pour planifier un travail asynchrone.

Étant donné que les calculs asynchrones de F sont une _spécification_ du travail plutôt qu’une représentation du travail qui est déjà en cours d’exécution, elles doivent être explicitement commencées par une fonction de départ. Il existe de nombreuses [fonctions de départ Async](https://msdn.microsoft.com/library/ee370232.aspx) qui sont utiles dans différents contextes. La section suivante décrit certaines des fonctions de départ les plus courantes.

### <a name="asyncstartchild"></a>Async.StartChild

Commence un calcul pour enfant dans un calcul asynchrone. Cela permet d’exécuter plusieurs calculs asynchrones en même temps. Le calcul de l’enfant partage un jeton d’annulation avec le calcul parent. Si le calcul parent est annulé, le calcul de l’enfant est également annulé.

Signature :

```fsharp
computation: Async<'T> * timeout: ?int -> Async<Async<'T>>
```

Quand l’utiliser :

- Lorsque vous voulez exécuter plusieurs calculs asynchrones en même temps plutôt qu’un à la fois, mais ne pas les avoir programmés en parallèle.
- Lorsque vous souhaitez lier la durée de vie d’un calcul enfant à celui d’un calcul parent.

Ce qu’il faut surveiller :

- Démarrer plusieurs calculs avec `Async.StartChild` n’est pas la même chose que de les planifier en parallèle. Si vous souhaitez planifier les calculs en `Async.Parallel`parallèle, utilisez .
- L’annulation d’un calcul parent déclenchera l’annulation de tous les calculs d’enfants qu’elle a commencés.

### <a name="asyncstartimmediate"></a>Async.StartImmediate

Exécute un calcul asynchrone, en commençant immédiatement sur le thread du système d’exploitation actuel. Ceci est utile si vous avez besoin de mettre à jour quelque chose sur le fil d’appel pendant le calcul. Par exemple, si un calcul asynchrone doit mettre à jour une interface `Async.StartImmediate` utilisateur (comme la mise à jour d’une barre de progression), il faut alors l’utiliser.

Signature :

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

Quand l’utiliser :

- Lorsque vous avez besoin de mettre à jour quelque chose sur le fil d’appel au milieu d’un calcul asynchrone.

Ce qu’il faut surveiller :

- Code dans le calcul asynchrone s’exécutera sur n’importe quel fil on se trouve être programmé sur. Cela peut être problématique si ce thread est en quelque sorte sensible, comme un thread d’interface utilisateur. Dans de `Async.StartImmediate` tels cas, est probablement inapproprié à utiliser.

### <a name="asyncstartastask"></a>Async.StartAsTask

Exécute un calcul dans le pool de threads. Renvoie <xref:System.Threading.Tasks.Task%601> un qui sera complété sur l’état correspondant une fois que le calcul se termine (produit le résultat, jette l’exception, ou obtient annulé). Si aucun jeton d’annulation n’est fourni, alors le jeton d’annulation par défaut est utilisé.

Signature :

```fsharp
computation: Async<'T> - taskCreationOptions: ?TaskCreationOptions - cancellationToken: ?CancellationToken -> Task<'T>
```

Quand l’utiliser :

- Lorsque vous avez besoin d’appeler dans <xref:System.Threading.Tasks.Task%601> un API .NET qui s’attend à un pour représenter le résultat d’un calcul asynchrone.

Ce qu’il faut surveiller :

- Cet appel allouera `Task` un objet supplémentaire, qui peut augmenter les frais généraux s’il est utilisé souvent.

### <a name="asyncparallel"></a>Async.Parallèle

Planifie une séquence de calculs asynchrones à exécuter en parallèle. Le degré de parallélisme peut être réglé/étranglé `maxDegreesOfParallelism` en spécifiant le paramètre.

Signature :

```fsharp
computations: seq<Async<'T>> - ?maxDegreesOfParallelism: int -> Async<'T[]>
```

Quand l’utiliser :

- Si vous avez besoin d’exécuter un ensemble de calculs en même temps et ne vous fiez pas à leur ordre d’exécution.
- Si vous n’avez pas besoin de résultats de calculs programmés en parallèle jusqu’à ce qu’ils aient tous terminé.

Ce qu’il faut surveiller :

- Vous ne pouvez accéder à la gamme de valeurs résultante qu’une fois que tous les calculs ont été terminés.
- Les calculs seront exécutés mais ils finissent par être programmés. Cela signifie que vous ne pouvez pas compter sur leur ordre de leur exécution.

### <a name="asyncsequential"></a>Async.Sequential

Planifie une séquence de calculs asynchrones à exécuter dans l’ordre de leur passage. Le premier calcul sera exécuté, puis le suivant, et ainsi de suite. Aucun calcul ne sera exécuté en parallèle.

Signature :

```fsharp
computations: seq<Async<'T>> -> Async<'T[]>
```

Quand l’utiliser :

- Si vous avez besoin d’exécuter plusieurs calculs dans l’ordre.

Ce qu’il faut surveiller :

- Vous ne pouvez accéder à la gamme de valeurs résultante qu’une fois que tous les calculs ont été terminés.
- Les calculs seront exécutés dans l’ordre qu’ils sont transmis à cette fonction, ce qui peut signifier que plus de temps s’écoulera avant que les résultats soient retournés.

### <a name="asyncawaittask"></a>Async.AwaitTask

Retourne un calcul asynchrone qui attend que <xref:System.Threading.Tasks.Task%601> la donnée soit complète et retourne son résultat en tant que`Async<'T>`

Signature :

```fsharp
task: Task<'T>  -> Async<'T>
```

Quand l’utiliser :

- Lorsque vous consommez un API <xref:System.Threading.Tasks.Task%601> .NET qui renvoie un dans un calcul asynchrone F.

Ce qu’il faut surveiller :

- Des exceptions <xref:System.AggregateException> sont enveloppées dans la suite de la convention de la Bibliothèque parallèle de travail, et ceci est différent de la façon dont F 'async fait généralement surface exceptions.

### <a name="asynccatch"></a>Async.Catch

Crée un calcul asynchrone qui exécute `Async<'T>`un donné `Async<Choice<'T, exn>>`, le retour d’un . Si l’donnée `Async<'T>` se termine `Choice1Of2` avec succès, alors un est retourné avec la valeur résultante. Si une exception est lancée avant `Choice2of2` qu’elle ne se termine, alors un est retourné à l’exception soulevée. S’il est utilisé sur un calcul asynchrone qui est lui-même composé de nombreux calculs, et l’un de ces calculs jette une exception, le calcul englobant sera arrêté entièrement.

Signature :

```fsharp
computation: Async<'T> -> Async<Choice<'T, exn>>
```

Quand l’utiliser :

- Lorsque vous exécutez un travail asynchrone qui peut échouer à une exception près et vous voulez gérer cette exception dans l’appelant.

Ce qu’il faut surveiller :

- Lors de l’utilisation de calculs asynchrones combinés ou séquencés, le calcul englobant s’arrêtera complètement si l’un de ses calculs « internes » jette une exception.

### <a name="asyncignore"></a>Async.Ignorer

Crée un calcul asynchrone qui exécute le calcul donné et ignore son résultat.

Signature :

```fsharp
computation: Async<'T> -> Async<unit>
```

Quand l’utiliser :

- Lorsque vous avez un calcul asynchrone dont le résultat n’est pas nécessaire. Ceci est analogue `ignore` au code pour le code non asynchrone.

Ce qu’il faut surveiller :

- Si vous devez utiliser cela `Async.Start` parce que vous `Async<unit>`souhaitez utiliser ou une autre fonction qui nécessite , considérer si jeter le résultat est acceptable à faire. Le rejet des résultats juste pour s’adapter à une signature de type ne doit généralement pas être fait.

### <a name="asyncrunsynchronously"></a>Async.RunSynchronously

Exécute un calcul asynchrone et attend son résultat sur le fil d’appel. Cet appel bloque.

Signature :

```fsharp
computation: Async<'T> - timeout: ?int - cancellationToken: ?CancellationToken -> 'T
```

Quand l’utiliser :

- Si vous en avez besoin, ne l’utilisez qu’une seule fois dans une application - au point d’entrée pour un exécutable.
- Lorsque vous ne vous souciez pas des performances et que vous voulez exécuter un ensemble d’autres opérations asynchrones à la fois.

Ce qu’il faut surveiller :

- L’appel `Async.RunSynchronously` bloque le fil d’appel jusqu’à ce que l’exécution se termine.

### <a name="asyncstart"></a>Async.Start

Démarre un calcul asynchrone dans le pool `unit`de fil qui revient . N’attend pas son résultat. Les calculs imbriqués `Async.Start` commencés avec sont commencés complètement indépendamment du calcul parent qui les appelait. Leur vie n’est liée à aucun calcul parent. Si le calcul parent est annulé, aucun calcul pour enfants n’est annulé.

Signature :

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

Utiliser uniquement lorsque :

- Vous avez un calcul asynchrone qui ne donne pas de résultat et/ou qui nécessite un traitement d’un.
- Vous n’avez pas besoin de savoir quand un calcul asynchrone se termine.
- Vous ne vous souciez pas quel fil d’un calcul asynchrone fonctionne sur.
- Vous n’avez pas besoin d’être au courant ou de signaler les exceptions résultant de la tâche.

Ce qu’il faut surveiller :

- Les exceptions soulevées par `Async.Start` les calculs commencés ne sont pas propagées à l’appelant. La pile d’appels sera complètement dénouée.
- Tout travail efficace (comme `printfn`l’appel) commencé par `Async.Start` ne fera pas en sorte que l’effet se produise sur le fil principal de l’exécution d’un programme.

## <a name="interoperate-with-net"></a>Interopér l’interopérabilité avec .NET

Vous pouvez travailler avec une bibliothèque .NET ou une base de code Cmd qui utilise une programmation asynchrone asynchrone [de](../../../standard/async.md)style asynchrone. Parce que C et la majorité <xref:System.Threading.Tasks.Task%601> des <xref:System.Threading.Tasks.Task> bibliothèques .NET utilisent `Async<'T>`le et les types comme leurs abstractions de base plutôt que , vous devez franchir une frontière entre ces deux approches de l’asynchronie.

### <a name="how-to-work-with-net-async-and-taskt"></a>Comment travailler avec .NET async et`Task<T>`

Travailler avec des bibliothèques async .NET <xref:System.Threading.Tasks.Task%601> et des bases de code qui utilisent (c’est-à-dire, des calculs async qui ont des valeurs de retour) est simple et a intégré le soutien avec F.

Vous pouvez `Async.AwaitTask` utiliser la fonction pour attendre un calcul asynchrone .NET:

```fsharp
let getValueFromLibrary param =
    async {
        let! value = DotNetLibrary.GetValueAsync param |> Async.AwaitTask
        return value
    }
```

Vous pouvez `Async.StartAsTask` utiliser la fonction pour passer un calcul asynchrone à un appelant .NET:

```fsharp
let computationForCaller param =
    async {
        let! result = getAsyncResult param
        return result
    } |> Async.StartAsTask
```

### <a name="how-to-work-with-net-async-and-task"></a>Comment travailler avec .NET async et`Task`

Pour travailler avec des <xref:System.Threading.Tasks.Task> API qui utilisent (c’est-à-dire les calculs async .NET qui ne `Async<'T>` retournent <xref:System.Threading.Tasks.Task>pas de valeur), vous devrez peut-être ajouter une fonction supplémentaire qui convertira un :

```fsharp
module Async =
    // Async<unit> -> Task
    let startTaskFromAsyncUnit (comp: Async<unit>) =
        Async.StartAsTask comp :> Task
```

Il y `Async.AwaitTask` a déjà <xref:System.Threading.Tasks.Task> un qui accepte un comme contribution. Avec ceci et `startTaskFromAsyncUnit` la fonction précédemment définie, vous pouvez commencer et attendre <xref:System.Threading.Tasks.Task> des types à partir d’un calcul d’async de F.

## <a name="relationship-to-multi-threading"></a>Relation à multi-threading

Bien que le filetage est mentionné tout au long de cet article, il ya deux choses importantes à retenir:

1. Il n’y a pas d’affinité entre un calcul asynchrone et un thread, à moins d’avoir explicitement commencé sur le thread actuel.
1. La programmation asynchrone dans F n’est pas une abstraction pour le multi-threading.

Par exemple, un calcul peut effectivement s’exécuter sur le fil de son appelant, selon la nature de l’œuvre. Un calcul pourrait également « sauter » entre les threads, les empruntant pour une petite quantité de temps pour faire un travail utile entre les périodes d'« attente » (comme lorsqu’un appel réseau est en transit).

Bien que F fournit certaines capacités pour démarrer un calcul asynchrone sur le thread actuel (ou explicitement pas sur le thread actuel), asynchrony n’est généralement pas associée à une stratégie de threading particulier.

## <a name="see-also"></a>Voir aussi

- [Le modèle de programmation asynchrone FMD](https://www.microsoft.com/research/publication/the-f-asynchronous-programming-model)
- [Guide de voyage De Jet.com’s FMD Async](https://medium.com/jettech/f-async-guide-eb3c8a2d180a)
- [F POUR le plaisir et le profit Asynchrone Guide de programmation](https://fsharpforfunandprofit.com/posts/concurrency-async-and-parallel/)
- [Async en C et F: Gotchas asynchrones en C #](http://tomasp.net/blog/csharp-async-gotchas.aspx/)
