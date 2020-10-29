---
title: Pièges potentiels avec PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, pitfalls
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
ms.openlocfilehash: 012ac4078c1e2f17d6eef88ee295b11161a0e24a
ms.sourcegitcommit: 6d09ae36acba0b0e2ba47999f8f1a725795462a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92925270"
---
# <a name="potential-pitfalls-with-plinq"></a>Pièges potentiels avec PLINQ

Dans de nombreux cas, PLINQ permet d’améliorer les performances de manière significative par rapport à des requêtes LINQ to Objects séquentielles. Toutefois, le travail de parallélisation de l’exécution de la requête présente une certaine complexité pouvant entraîner des problèmes qui, dans du code séquentiel, ne sont pas si courants ou ne surviennent pas du tout. Cette rubrique répertorie des pratiques à éviter lorsque vous écrivez des requêtes PLINQ.

## <a name="dont-assume-that-parallel-is-always-faster"></a>Ne partez pas du principe que Parallel est toujours plus rapide

Parfois, la parallélisation entraîne l’exécution plus lente d’une requête PLINQ que son LINQ to Objects équivalent. La règle empirique de base veut que les requêtes ayant peu d’éléments source et des délégués utilisateurs rapides ne sont pas susceptibles d’apporter une grande accélération. Toutefois, étant donné que de nombreux facteurs sont impliqués dans les performances, nous vous recommandons de mesurer les résultats réels avant de décider si vous utiliserez PLINW. Pour plus d’informations, consultez [Fonctionnement de l’accélération dans PLINQ](understanding-speedup-in-plinq.md).

## <a name="avoid-writing-to-shared-memory-locations"></a>Éviter d’écrire dans des emplacements de mémoire partagée

Dans du code séquentiel, il n’est pas rare de lire des variables statiques ou d’écrire dans ces dernières ou dans des champs de classe. Toutefois, l’accès simultané de plusieurs threads à de telles variables entraîne un fort risque d’engorgement. Bien que vous puissiez utiliser des verrous pour synchroniser l’accès à la variable, le coût de synchronisation peut nuire aux performances. Par conséquent, nous vous recommandons d’éviter, ou au moins de limiter autant que possible l’accès à un état partagé dans une requête PLINQ.

## <a name="avoid-over-parallelization"></a>Éviter les surparallélisations

À l’aide de la `AsParallel` méthode, vous encourez les frais généraux liés au partitionnement de la collection source et à la synchronisation des threads de travail. Les avantages de la parallélisation sont également limités par le nombre de processeurs de l’ordinateur. L’exécution de plusieurs threads liés au calcul sur un seul processeur ne permet aucune accélération. Par conséquent, vous devez veiller à ne pas surparalléliser une requête.

Les requêtes imbriquées sont le scénario le plus courant dans lequel une surparallélisation peut se produire, comme le montre l’extrait suivant.

[!code-csharp[PLINQ#20](~/samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
[!code-vb[PLINQ#20](~/samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]

Dans ce cas, il est préférable de paralléliser uniquement la source de données externe (clients), sauf si une ou plusieurs conditions suivantes s’appliquent :

- La source de données interne (cust.Orders) est connue pour être très longue.

- Vous effectuez un calcul coûteux sur chaque commande. (l’opération montrée dans l’exemple n’est pas coûteuse)

- Le système cible est connu pour avoir suffisamment de processeurs pour gérer le nombre de threads produits en parallélisant la requête sur `cust.Orders`.

Dans tous les cas, le test et la mesure sont la meilleure façon de déterminer la forme de requête optimale. Pour plus d’informations, consultez [Comment : mesurer les performances des requêtes PLINQ](how-to-measure-plinq-query-performance.md).

## <a name="avoid-calls-to-non-thread-safe-methods"></a>Éviter les appels à des méthodes non thread-safe

L’écriture dans des méthodes d’instance qui ne sont pas thread-safe à partir d’une requête PLINQ peut entraîner une corruption des données qui peut être détectée ou non dans votre programme. Cela peut également entraîner des exceptions. Dans l’exemple suivant, plusieurs threads tenteraient d’appeler simultanément la méthode `FileStream.Write`, qui n’est pas prise en charge par la classe.

```vb
Dim fs As FileStream = File.OpenWrite(…)
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))
```

```csharp
FileStream fs = File.OpenWrite(...);
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));
```

## <a name="limit-calls-to-thread-safe-methods"></a>Limiter les appels aux méthodes thread-safe

La plupart des méthodes statiques dans .NET sont thread-safe et peuvent être appelées à partir de plusieurs threads simultanément. Toutefois, même dans ces cas, la synchronisation impliquée peut entraîner un ralentissement significatif de la requête.

> [!NOTE]
> Vous pouvez le tester vous-même en insérant des appels à <xref:System.Console.WriteLine%2A> dans vos requêtes. Bien que cette méthode soit utilisée dans les exemples de documentation destinés à la démonstration, ne l’utilisez pas dans les requêtes PLINQ.

## <a name="avoid-unnecessary-ordering-operations"></a>Éviter les opérations de tri inutiles

Lorsque PLINQ exécute une requête en parallèle, il divise la séquence source en partitions qui peuvent être traitées simultanément sur plusieurs threads. Par défaut, l’ordre dans lequel les partitions sont traitées et les résultats sont remis n’est pas prévisible (à l’exception des opérateurs tels que `OrderBy`). Vous pouvez demander à PLINQ de conserver le classement de toute séquence source, mais cela a un impact négatif sur les performances. Si possible, la meilleure pratique consiste à structurer les requêtes afin qu’elles ne reposent pas sur la conservation de l’ordre. Pour plus d’informations, consultez [Order Preservation in PLINQ](order-preservation-in-plinq.md) (Conservation de l’ordre dans PLINQ).

## <a name="prefer-forall-to-foreach-when-it-is-possible"></a>Préférer ForAll à ForEach quand c’est possible

Bien que PLINQ exécute une requête sur plusieurs threads, si vous consommez les résultats dans une boucle `foreach` (`For Each` en Visual Basic), les résultats de la requête doivent être fusionnés dans un thread et consultés de façon séquentielle par l’énumérateur. Dans certains cas, c’est inévitable ; toutefois, si possible, utilisez la méthode `ForAll` pour activer chaque thread afin qu’il sorte ses propres résultats, par exemple, en écrivant dans une collection thread-safe, telle que <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.

Le même problème s’applique à <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> . En d’autres termes, `source.AsParallel().Where().ForAll(...)` doit être fortement préféré à `Parallel.ForEach(source.AsParallel().Where(), ...)` .

## <a name="be-aware-of-thread-affinity-issues"></a>Tenez compte des problèmes d’affinité de thread

Certaines technologies, par exemple, les composants STA (Single-Threaded Apartment), Windows Forms et Windows Presentation Foundation (WPF) imposent des restrictions d’affinité de thread qui requièrent l’exécution de code sur un thread spécifique. Par exemple, dans Windows Forms et WPF, un contrôle est uniquement accessible sur le thread sur lequel il a été créé. Si vous essayez d’accéder à l’état partagé d’un contrôle Windows Forms dans une requête PLINQ, une exception est levée si vous exécutez dans le débogueur. (Ce paramètre peut être désactivé.) Toutefois, si votre requête est consommée sur le thread d’interface utilisateur, vous pouvez accéder au contrôle à partir de la `foreach` boucle qui énumère les résultats de la requête, car ce code s’exécute sur un seul thread.

## <a name="dont-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>Ne partez pas du principe que les itérations de ForEach, for et ForAll s’exécutent toujours en parallèle

Il est important de garder à l’esprit que les itérations individuelles dans une <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> boucle, ou <xref:System.Linq.ParallelEnumerable.ForAll%2A> peuvent, mais n’ont pas besoin de s’exécuter en parallèle. Par conséquent, vous devez éviter d’écrire du code dont l’exactitude dépend de l’exécution parallèle d’itérations ou de l’exécution d’itérations dans un ordre particulier.

Par exemple, ce code est susceptible d’interbloquer :

```vb
Dim mre = New ManualResetEventSlim()
Enumerable.Range(0, Environment.ProcessorCount * 100).AsParallel().ForAll(Sub(j)
   If j = Environment.ProcessorCount Then
       Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)
       mre.Set()
   Else
       Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)
       mre.Wait()
   End If
End Sub) ' deadlocks
```

```csharp
ManualResetEventSlim mre = new ManualResetEventSlim();
Enumerable.Range(0, Environment.ProcessorCount * 100).AsParallel().ForAll((j) =>
{
    if (j == Environment.ProcessorCount)
    {
        Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);
        mre.Set();
    }
    else
    {
        Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);
        mre.Wait();
    }
}); //deadlocks
```

Dans cet exemple, une itération définit un événement que toutes les autres itérations attendent. Aucune des itérations en attente ne peut s’achever tant que l’itération de définition d’événement n’est pas terminée. Toutefois, il est possible que les itérations en attente bloquent tous les threads utilisés pour exécuter la boucle parallèle, avant que l’itération de définition d’événement ait eu une chance de s’exécuter. Cela provoque un interblocage : l’itération de définition d’événement ne s’exécute jamais et les itérations en attente ne s’activent pas non plus.

En particulier, une itération de boucle parallèle ne doit jamais attendre une autre itération de la boucle pour progresser. Si la boucle parallèle décide de planifier les itérations de manière séquentielle, mais dans l’ordre inverse, un interblocage se produit.

## <a name="see-also"></a>Voir aussi

- [Parallel LINQ (PLINQ)](introduction-to-plinq.md)
