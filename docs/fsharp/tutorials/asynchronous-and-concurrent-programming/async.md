---
title: Programmation asynchrone
description: Découvrez comment F# fournit une prise en charge propre pour l’asynchronie basée sur un modèle de programmation au niveau du langage dérivé des concepts de programmation fonctionnelle de base.
ms.date: 12/17/2018
ms.openlocfilehash: 7021d7936d10f9ea6fceb4aa56db3285d21624ad
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628850"
---
# <a name="async-programming-in-f"></a>Programmation asynchrone en F\#

La programmation asynchrone est un mécanisme essentiel pour les applications modernes pour diverses raisons. La plupart des développeurs rencontrent deux cas d’utilisation principaux :

- Présentation d’un processus serveur qui peut traiter un nombre important de demandes entrantes simultanées, tout en minimisant les ressources système occupées pendant que le traitement des demandes attend les entrées des systèmes ou des services externes à ce processus
- Maintien d’une interface utilisateur réactive ou d’un thread principal tout en progressant simultanément sur le travail en arrière-plan

Bien que le travail en arrière-plan implique souvent l’utilisation de plusieurs threads, il est important de prendre en compte les concepts de l’asynchronie et du multithreading séparément. En fait, il s’agit de problèmes distincts, et l’un n’implique pas l’autre. Les éléments suivants de cet article décrivent cela plus en détail.

## <a name="asynchrony-defined"></a>Asynchronie défini

Le point précédent : l’asynchronie est indépendante de l’utilisation de plusieurs threads. il est donc judicieux d’expliquer un peu plus loin. Trois concepts sont parfois liés, mais strictement indépendants les uns des autres :

- D’accès concurrentiel Lorsque plusieurs calculs s’exécutent pendant le chevauchement de périodes.
- Parallélisme Lorsque plusieurs calculs ou plusieurs parties d’un même calcul s’exécutent exactement à la même heure.
- Asynchronie Lorsqu’un ou plusieurs calculs peuvent s’exécuter indépendamment du processus principal du programme.

Les trois sont des concepts orthogonaux, mais ils peuvent être facilement conplats, en particulier lorsqu’ils sont utilisés ensemble. Par exemple, vous devrez peut-être exécuter plusieurs calculs asynchrones en parallèle. Cela ne signifie pas que le parallélisme ou l’asynchronie impliquent l’un l’autre.

Si vous considérez le mot « Asynchronous » comme Etymology, deux éléments sont nécessaires :

- « a », ce qui signifie « non ».
- « synchrone », ce qui signifie « en même temps ».

Lorsque vous regroupez ces deux termes, vous verrez que « asynchrone » signifie « pas en même temps ». Et voilà ! Il n’y a aucune implication de l’accès concurrentiel ou du parallélisme dans cette définition. Cela est également vrai dans la pratique.

En pratique, les calculs asynchrones dans F# sont planifiés pour s’exécuter indépendamment du déroulement du programme principal. Cela n’implique pas la concurrence ou le parallélisme, et n’implique pas non plus qu’un calcul se produit toujours en arrière-plan. En fait, les calculs asynchrones peuvent même s’exécuter de façon synchrone, en fonction de la nature du calcul et de l’environnement dans lequel le calcul s’exécute.

Le principal pas à pas est que les calculs asynchrones sont indépendants du processus principal du programme. Bien qu’il existe peu de garanties quant au moment ou à l’exécution d’un calcul asynchrone, il existe des approches pour l’orchestration et la planification. Le reste de cet article explore les concepts fondamentaux F# de l’asynchronie et explique comment utiliser les types, les fonctions et les F#expressions intégrés à.

## <a name="core-concepts"></a>Principaux concepts

Dans F#, la programmation asynchrone est centrée autour de trois concepts fondamentaux :

- Le type de `Async<'T>`, qui représente un calcul asynchrone composable.
- Les fonctions de module `Async`, qui vous permettent de planifier un travail asynchrone, de composer des calculs asynchrones et de transformer des résultats asynchrones.
- L' [expression de calcul](../../language-reference/computation-expressions.md)`async { }`, qui fournit une syntaxe pratique pour la génération et le contrôle des calculs asynchrones.

Vous pouvez voir ces trois concepts dans l’exemple suivant :

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

Dans l’exemple, la fonction `printTotalFileBytes` est de type `string -> Async<unit>`. L’appel de la fonction n’exécute pas réellement le calcul asynchrone. Au lieu de cela, elle retourne un `Async<unit>` qui agit comme une *spécification* du travail qui doit s’exécuter de façon asynchrone. Elle appelle `Async.AwaitTask` dans son corps, qui convertit le résultat de <xref:System.IO.File.ReadAllBytesAsync%2A> en type approprié.

Une autre ligne importante est l’appel à `Async.RunSynchronously`. Il s’agit de l’une des fonctions de démarrage de module Async que vous devrez appeler si vous souhaitez réellement exécuter F# un calcul asynchrone.

Il s’agit d’une différence fondamentale C#avec le style de base/visual de `async` programmation. Dans F#, les calculs asynchrones peuvent être considérés comme des **tâches à froid**. Ils doivent être démarrés explicitement pour s’exécuter réellement. Cela présente des avantages, car elle vous permet de combiner et de séquencer un travail asynchrone bien plus C# facilement que dans ou Visual Basic.

## <a name="combine-asynchronous-computations"></a>Combiner des calculs asynchrones

Voici un exemple qui s’appuie sur le précédent en combinant des calculs :

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

Comme vous pouvez le voir, la fonction `main` a d’autres appels effectués. D’un plan conceptuel, elle effectue les opérations suivantes :

1. Transformez les arguments de ligne de commande en `Async<unit>` calculs avec `Array.map`.
2. Créez un `Async<'T[]>` qui planifie et exécute les calculs `printTotalFileBytes` en parallèle lorsqu’il s’exécute.
3. Créer un `Async<unit>` qui exécutera le calcul parallèle et ignorer son résultat.
4. Exécuter explicitement le dernier calcul avec `Async.RunSynchronously` et bloquer jusqu’à ce qu’il soit terminé.

Quand ce programme s’exécute, `printTotalFileBytes` s’exécute en parallèle pour chaque argument de ligne de commande. Étant donné que les calculs asynchrones s’exécutent indépendamment du déroulement du programme, il n’y a aucun ordre dans lequel ils impriment leurs informations et terminent leur exécution. Les calculs sont planifiés en parallèle, mais leur ordre d’exécution n’est pas garanti.

## <a name="sequence-asynchronous-computations"></a>Séquencer des calculs asynchrones

Étant donné que `Async<'T>` est une spécification de travail plutôt qu’une tâche déjà en cours d’exécution, vous pouvez facilement effectuer des transformations plus complexes. Voici un exemple qui séquence un ensemble de calculs asynchrones de sorte qu’ils s’exécutent l’un après l’autre.

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

Cela permet de planifier l’exécution de `printTotalFileBytes` dans l’ordre des éléments de `argv` plutôt que de les planifier en parallèle. Étant donné que l’élément suivant n’est pas planifié tant que le dernier calcul n’a pas fini de s’exécuter, les calculs sont séquencés de telle sorte qu’il n’y a aucun chevauchement de leur exécution.

## <a name="important-async-module-functions"></a>Fonctions importantes du module Async

Lorsque vous écrivez du code asynchrone F# dans, vous interagissez généralement avec une infrastructure qui gère la planification des calculs pour vous. Toutefois, ce n’est pas toujours le cas. il est donc judicieux d’apprendre les différentes fonctions de démarrage pour planifier un travail asynchrone.

Étant F# donné que les calculs asynchrones sont une _spécification_ de travail plutôt qu’une représentation de travail déjà en cours d’exécution, ils doivent être démarrés explicitement à l’aide d’une fonction de démarrage. De nombreuses [fonctions de démarrage asynchrones](https://msdn.microsoft.com/library/ee370232.aspx) sont utiles dans différents contextes. La section suivante décrit quelques-unes des fonctions de démarrage les plus courantes.

### <a name="asyncstartchild"></a>Async. StartChild

Démarre un calcul enfant dans un calcul asynchrone. Cela permet l’exécution simultanée de plusieurs calculs asynchrones. Le calcul enfant partage un jeton d’annulation avec le calcul parent. Si le calcul parent est annulé, le calcul enfant est également annulé.

Signature :

```fsharp
computation: Async<'T> - timeout: ?int -> Async<Async<'T>>
```

Quand utiliser :

- Lorsque vous souhaitez exécuter plusieurs calculs asynchrones simultanément plutôt qu’un à la fois, mais que vous ne les avez pas planifiés en parallèle.
- Lorsque vous souhaitez lier la durée de vie d’un calcul enfant à celle d’un calcul parent.

Ce qu’il faut surveiller :

- Le démarrage de plusieurs calculs avec `Async.StartChild` est différent de la planification en parallèle. Si vous souhaitez planifier des calculs en parallèle, utilisez `Async.Parallel`.
- L’annulation d’un calcul parent déclenchera l’annulation de tous les calculs enfants qu’il a démarrés.

### <a name="asyncstartimmediate"></a>Async. StartImmediate

Exécute un calcul asynchrone, en commençant immédiatement sur le thread de système d’exploitation actuel. Cela est utile si vous devez mettre à jour un événement sur le thread appelant pendant le calcul. Par exemple, si un calcul asynchrone doit mettre à jour une interface utilisateur (telle que la mise à jour d’une barre de progression), `Async.StartImmediate` doit être utilisé.

Signature :

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

Quand utiliser :

- Lorsque vous devez mettre à jour un événement sur le thread appelant au milieu d’un calcul asynchrone.

Ce qu’il faut surveiller :

- Le code dans le calcul asynchrone s’exécutera sur le thread sur lequel il se produit. Cela peut être problématique si ce thread est sensible, par exemple un thread d’interface utilisateur. Dans ce cas, `Async.StartImmediate` est probablement inapproprié à utiliser.

### <a name="asyncstartastask"></a>Async. StartAsTask

Exécute un calcul dans le pool de threads. Retourne une <xref:System.Threading.Tasks.Task%601> qui sera terminée à l’état correspondant une fois le calcul terminé (produit le résultat, lève une exception ou est annulé). Si aucun jeton d’annulation n’est fourni, le jeton d’annulation par défaut est utilisé.

Signature :

```fsharp
computation: Async<'T> - taskCreationOptions: ?TaskCreationOptions - cancellationToken: ?CancellationToken -> Task<'T>
```

Quand utiliser :

- Lorsque vous devez appeler une API .NET qui attend un <xref:System.Threading.Tasks.Task%601> pour représenter le résultat d’un calcul asynchrone.

Ce qu’il faut surveiller :

- Cet appel va allouer un objet `Task` supplémentaire, ce qui peut augmenter la surcharge s’il est souvent utilisé.

### <a name="asyncparallel"></a>Async. Parallel

Planifie une séquence de calculs asynchrones à exécuter en parallèle. Le degré de parallélisme peut éventuellement être réglé/limité en spécifiant le paramètre `maxDegreesOfParallelism`.

Signature :

```fsharp
computations: seq<Async<'T>> - ?maxDegreesOfParallelism: int -> Async<'T[]>
```

Quand l’utiliser :

- Si vous devez exécuter un ensemble de calculs en même temps et que vous n’avez pas recours à leur ordre d’exécution.
- Si vous n’avez pas besoin des résultats des calculs planifiés en parallèle jusqu’à ce qu’ils soient tous terminés.

Ce qu’il faut surveiller :

- Vous ne pouvez accéder au tableau de valeurs résultant qu’une fois que tous les calculs sont terminés.
- Les calculs sont exécutés, mais ils finissent par être planifiés. Cela signifie que vous ne pouvez pas compter sur leur ordre d’exécution.

### <a name="asyncsequential"></a>Async. sequential

Planifie l’exécution d’une séquence de calculs asynchrones dans l’ordre dans lequel ils sont passés. Le premier calcul sera exécuté, puis le suivant, et ainsi de suite. Aucun calcul n’est exécuté en parallèle.

Signature :

```fsharp
computations: seq<Async<'T>> -> Async<'T[]>
```

Quand l’utiliser :

- Si vous devez exécuter plusieurs calculs dans l’ordre.

Ce qu’il faut surveiller :

- Vous ne pouvez accéder au tableau de valeurs résultant qu’une fois que tous les calculs sont terminés.
- Les calculs sont exécutés dans l’ordre dans lequel ils sont passés à cette fonction, ce qui peut signifier que plus de temps s’écoulera avant que les résultats ne soient retournés.

### <a name="asyncawaittask"></a>Async. AwaitTask

Retourne un calcul asynchrone qui attend la fin de l' <xref:System.Threading.Tasks.Task%601> donné et retourne son résultat sous la forme d’une `Async<'T>`

Signature :

```fsharp
task: Task<'T>  -> Async<'T>
```

Quand utiliser :

- Lorsque vous consommez une API .NET qui retourne un <xref:System.Threading.Tasks.Task%601> dans un F# calcul asynchrone.

Ce qu’il faut surveiller :

- Les exceptions sont encapsulées dans <xref:System.AggregateException> suivant la Convention de la bibliothèque parallèle de tâches, et cela diffère F# de la façon dont Async recouvre généralement les exceptions.

### <a name="asynccatch"></a>Async. catch

Crée un calcul asynchrone qui exécute un `Async<'T>`donné, en retournant un `Async<Choice<'T, exn>>`. Si le `Async<'T>` donné se termine correctement, un `Choice1Of2` est retourné avec la valeur résultante. Si une exception est levée avant qu’elle ne se termine, une `Choice2of2` est retournée avec l’exception levée. S’il est utilisé sur un calcul asynchrone qui est lui-même composé de plusieurs calculs, et que l’un de ces calculs lève une exception, le calcul englobant est arrêté entièrement.

Signature :

```fsharp
computation: Async<'T> -> Async<Choice<'T, exn>>
```

Quand utiliser :

- Lorsque vous effectuez un travail asynchrone qui peut échouer avec une exception et que vous souhaitez gérer cette exception dans l’appelant.

Ce qu’il faut surveiller :

- Lors de l’utilisation de calculs asynchrones combinés ou séquencés, le calcul englobant s’arrête entièrement si l’un de ses calculs « internes » lève une exception.

### <a name="asyncignore"></a>Async. ignore

Crée un calcul asynchrone qui exécute le calcul donné et ignore son résultat.

Signature :

```fsharp
computation: Async<'T> -> Async<unit>
```

Quand utiliser :

- Quand vous avez un calcul asynchrone dont le résultat n’est pas nécessaire. Cela est analogue au code `ignore` pour le code non asynchrone.

Ce qu’il faut surveiller :

- Si vous devez l’utiliser, si vous souhaitez utiliser `Async.Start` ou une autre fonction qui requiert `Async<unit>`, envisagez d’ignorer le résultat. Il n’est généralement pas nécessaire de faire en sorte que les résultats soient ignorés pour correspondre à une signature de type.

### <a name="asyncrunsynchronously"></a>Async. RunSynchronously

Exécute un calcul asynchrone et attend son résultat sur le thread appelant. Cet appel est bloquant.

Signature :

```fsharp
computation: Async<'T> - timeout: ?int - cancellationToken: ?CancellationToken -> 'T
```

Quand l’utiliser :

- Si vous en avez besoin, utilisez-le une seule fois dans une application, au point d’entrée d’un exécutable.
- Lorsque vous ne vous souciez pas des performances et que vous souhaitez exécuter un ensemble d’autres opérations asynchrones à la fois.

Ce qu’il faut surveiller :

- L’appel de `Async.RunSynchronously` bloque le thread appelant jusqu’à ce que l’exécution se termine.

### <a name="asyncstart"></a>Async. Start

Démarre un calcul asynchrone dans le pool de threads qui retourne `unit`. N’attend pas son résultat. Les calculs imbriqués lancés avec `Async.Start` sont démarrés entièrement indépendamment du calcul parent qui les a appelés. Leur durée de vie n’est pas liée à un calcul parent. Si le calcul parent est annulé, aucun calcul enfant n’est annulé.

Signature :

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

À utiliser uniquement dans les cas suivants :

- Vous avez un calcul asynchrone qui ne génère pas de résultat et/ou nécessite le traitement d’un.
- Vous n’avez pas besoin de savoir quand un calcul asynchrone se termine.
- Vous ne vous souciez pas du thread sur lequel s’exécute un calcul asynchrone.
- Vous n’avez pas besoin de connaître ou de signaler les exceptions résultant de la tâche.

Ce qu’il faut surveiller :

- Les exceptions déclenchées par les calculs démarrés avec `Async.Start` ne sont pas propagées à l’appelant. La pile des appels sera complètement déroulée.
- Tout travail en effet (tel que l’appel de `printfn`) démarré avec `Async.Start` n’entraîne pas l’effet sur le thread principal de l’exécution d’un programme.

## <a name="interoperate-with-net"></a>Interagir avec .NET

Vous utilisez peut-être une bibliothèque .NET ou C# un code base qui utilise la programmation asynchrone de style asynchrone [/await](../../../standard/async.md). Étant C# donné que et la majorité des bibliothèques .NET utilisent les types <xref:System.Threading.Tasks.Task%601> et <xref:System.Threading.Tasks.Task> comme abstractions principales plutôt que `Async<'T>`, vous devez franchir une limite entre ces deux approches pour l’asynchronie.

### <a name="how-to-work-with-net-async-and-taskt"></a>Utilisation de .NET Async et `Task<T>`

L’utilisation de bibliothèques et de codes base .NET Async qui utilisent <xref:System.Threading.Tasks.Task%601> (autrement dit, les calculs asynchrones ayant des valeurs de retour) est simple et offre une prise F#en charge intégrée de.

Vous pouvez utiliser la fonction `Async.AwaitTask` pour attendre un calcul asynchrone .NET :

```fsharp
let getValueFromLibrary param =
    async {
        let! value = DotNetLibrary.GetValueAsync param |> Async.AwaitTask
        return value
    }
```

Vous pouvez utiliser la fonction `Async.StartAsTask` pour passer un calcul asynchrone à un appelant .NET :

```fsharp
let computationForCaller param =
    async {
        let! result = getAsyncResult param
        return result
    } |> Async.StartAsTask
```

### <a name="how-to-work-with-net-async-and-task"></a>Utilisation de .NET Async et `Task`

Pour utiliser des API qui utilisent des <xref:System.Threading.Tasks.Task> (c’est-à-dire des calculs asynchrones .NET qui ne retournent pas de valeur), vous devrez peut-être ajouter une fonction supplémentaire qui convertira un `Async<'T>` en <xref:System.Threading.Tasks.Task>:

```fsharp
module Async =
    // Async<unit> -> Task
    let startTaskFromAsyncUnit (comp: Async<unit>) =
        Async.StartAsTask comp :> Task
```

Il existe déjà un `Async.AwaitTask` qui accepte un <xref:System.Threading.Tasks.Task> comme entrée. Avec cette et la fonction `startTaskFromAsyncUnit` définie précédemment, vous pouvez démarrer et attendre <xref:System.Threading.Tasks.Task> types à partir F# d’un calcul asynchrone.

## <a name="relationship-to-multi-threading"></a>Relation avec le Multi-Threading

Bien que le Threading soit mentionné tout au long de cet article, il y a deux points importants à retenir :

1. Il n’y a pas d’affinité entre un calcul asynchrone et un thread, à moins qu’il ne soit explicitement démarré sur le thread actuel.
1. La programmation asynchrone F# dans n’est pas une abstraction pour le Multi-Threading.

Par exemple, un calcul peut s’exécuter sur le thread de son appelant, en fonction de la nature du travail. Un calcul peut également « sauter » entre les threads, ce qui les emprunte pendant une courte période pour effectuer un travail utile entre les périodes d’attente (par exemple, lorsqu’un appel réseau est en transit).

Bien F# que offre des capacités pour démarrer un calcul asynchrone sur le thread actuel (ou pas explicitement sur le thread actuel), l’asynchronie n’est généralement pas associé à une stratégie de thread particulière.

## <a name="see-also"></a>Voir aussi

- [Modèle F# de programmation asynchrone](https://www.microsoft.com/research/publication/the-f-asynchronous-programming-model)
- [Guide Async de F# jet. com](https://medium.com/jettech/f-async-guide-eb3c8a2d180a)
- [F#Guide de programmation asynchrone du fun et des bénéfices](https://fsharpforfunandprofit.com/posts/concurrency-async-and-parallel/)
- [Async in C# et F#: pièges asynchrones dansC#](http://tomasp.net/blog/csharp-async-gotchas.aspx/)
