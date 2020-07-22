---
title: Comment utiliser et déboguer la non-chargeabilité d’assembly dans .NET Core
description: Découvrez comment utiliser un AssemblyLoadContext pouvant être collecté pour charger et décharger des assemblys managés, et comment résoudre les problèmes de déchargement.
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: 9d1f604816dcbd7a84a3692b3cfd24481532789a
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865344"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a>Comment utiliser et déboguer la non-chargeabilité d’assembly dans .NET Core

À compter de .NET Core 3.0, il est possible de charger un ensemble d’assemblys et de le décharger plus tard. Dans le .NET Framework, les domaines d’application personnalisés étaient utilisés à cet effet, mais .NET Core ne prend en charge qu’un seul domaine d’application par défaut.

.NET Core 3.0 et versions ultérieures utilisent <xref:System.Runtime.Loader.AssemblyLoadContext> pour prendre en charge le déchargement. Vous pouvez charger un ensemble d’assemblys dans un `AssemblyLoadContext` pouvant être collecté, exécuter des méthodes dans ceux-ci ou simplement les inspecter par réflexion, puis finalement décharger `AssemblyLoadContext`. Cela décharge les assemblys chargés dans le `AssemblyLoadContext` .

Il existe une différence notable entre le déchargement qui utilise `AssemblyLoadContext` et celui qui utilise des domaines d’application. Avec les domaines d’application, le déchargement est forcé. Au moment du déchargement, tous les threads qui s’exécutent dans l’AppDomain cible sont abandonnés, les objets COM managés créés dans l’AppDomain cible sont détruits, et ainsi de suite. Avec `AssemblyLoadContext`, le déchargement est « coopératif ». L’appel de la méthode <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> lance simplement le déchargement. Le déchargement se termine quand :

- Aucun thread n’a de méthodes provenant des assemblys chargés dans `AssemblyLoadContext` sur leurs piles d’appels.
- Aucun des types des assemblys chargés dans le, les `AssemblyLoadContext` instances de ces types et les assemblys eux-mêmes sont référencés par :
  - Des références en dehors d’`AssemblyLoadContext`, à l’exception de références faibles (<xref:System.WeakReference> ou <xref:System.WeakReference%601>).
  - Handles de garbage collector (GC) forts ([GCHandleType. normal](xref:System.Runtime.InteropServices.GCHandleType.Normal) ou [GCHandleType. épinglé](xref:System.Runtime.InteropServices.GCHandleType.Pinned)) à partir de l’intérieur et de l’extérieur de `AssemblyLoadContext` .

## <a name="use-collectible-assemblyloadcontext"></a>Utiliser l’AssemblyLoadContext pouvant être collecté

Cette section contient un tutoriel pas à pas qui présente un moyen simple de charger une application .NET Core dans un `AssemblyLoadContext` pouvant être collecté, d’exécuter son point d’entrée, puis de procéder au déchargement. Vous trouverez un exemple complet à l’adresse [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading) .

### <a name="create-a-collectible-assemblyloadcontext"></a>Créer un AssemblyLoadContext pouvant être collecté

Vous devez dériver votre classe de <xref:System.Runtime.Loader.AssemblyLoadContext> et substituer sa <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> méthode. Cette méthode résout les références à tous les assemblys qui sont des dépendances d’assemblys chargés dans cet `AssemblyLoadContext`.

Le code suivant est un exemple d’un `AssemblyLoadContext` de base personnalisé :

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

Comme vous pouvez le voir, la méthode `Load` retourne `null`. Cela signifie que tous les assemblys de dépendances sont chargés dans le contexte par défaut, et que le nouveau contexte contient uniquement les assemblys explicitement chargés dans celui-ci.

Si vous souhaitez également charger une partie ou la totalité des dépendances dans `AssemblyLoadContext`, vous pouvez utiliser `AssemblyDependencyResolver` dans la méthode `Load`. `AssemblyDependencyResolver`Résout les noms d’assembly en chemins d’accès absolus au fichier d’assembly. Le programme de résolution utilise la *.deps.jssur* les fichiers d’assembly et de fichier dans le répertoire de l’assembly principal chargé dans le contexte.

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a>Utiliser un AssemblyLoadContext personnalisé pouvant être collecté

Cette section part du principe que vous utilisez la version de base de `TestAssemblyLoadContext`.

Pour créer une instance d’un `AssemblyLoadContext` personnalisé et y charger un assembly, effectuez les étapes suivantes :

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

Pour chacun des assemblys référencés par l’assembly chargé, la méthode `TestAssemblyLoadContext.Load` est appelée afin que `TestAssemblyLoadContext` puisse déterminer où obtenir l’assembly. Dans notre cas, elle retourne `null` pour indiquer qu’il doit être chargé dans le contexte par défaut à partir d’emplacements que le runtime utilise pour charger les assemblys par défaut.

Maintenant qu’un assembly a été chargé, vous pouvez exécuter une méthode à partir de celui-ci. Exécutez la méthode `Main` :

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

Quand la méthode `Main` retourne une valeur, vous pouvez lancer le déchargement en appelant la méthode `Unload` sur l’`AssemblyLoadContext` personnalisé ou en éliminant la référence à `AssemblyLoadContext` :

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

Cela suffit pour décharger l’assembly de test. Nous allons à présent placer tout cela dans une méthode distincte non inlineable de telle sorte que `TestAssemblyLoadContext`, `Assembly` et `MethodInfo` (`Assembly.EntryPoint`) ne puissent pas être maintenus actifs par des références d’emplacement de pile (variables locales en temps réel ou juste-à-temps). En effet, le déchargement n’a pas lieu si `TestAssemblyLoadContext` reste actif.

Retournez également une référence faible à `AssemblyLoadContext` afin que vous puissiez l’utiliser par la suite pour détecter la fin du déchargement.

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

Vous pouvez maintenant exécuter cette fonction pour charger, exécuter et décharger l’assembly.

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

Toutefois, le déchargement ne se termine pas immédiatement. Comme mentionné précédemment, il s’appuie sur le garbage collector pour collecter tous les objets de l’assembly de test. Dans de nombreux cas, il n’est pas nécessaire d’attendre la fin du déchargement. Toutefois, dans certains cas, il est utile de savoir que le déchargement est terminé. Par exemple, vous souhaitez peut-être supprimer le fichier d’assembly qui a été chargé dans l’`AssemblyLoadContext` personnalisé du disque. Dans ce cas, vous pouvez utiliser l’extrait de code suivant. Il déclenche garbage collection et attend les finaliseurs en attente dans une boucle jusqu’à ce que la référence faible à la personnalisée `AssemblyLoadContext` soit définie sur `null` , ce qui indique que l’objet cible a été collecté. Dans la plupart des cas, un seul passage à la boucle est requis. Toutefois, dans les cas plus complexes où les objets créés par le code qui s’exécute dans `AssemblyLoadContext` ont des finaliseurs, des passages supplémentaires peuvent être nécessaires.

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a>Événement de déchargement

Dans certains cas, le code chargé dans un `AssemblyLoadContext` personnalisé doit effectuer des tâches de nettoyage au moment du lancement du déchargement. Par exemple, il peut être nécessaire d’arrêter des threads ou de nettoyer des handles de GC forts. L’événement `Unloading` peut être utilisé dans de tels cas. Un gestionnaire qui effectue le nettoyage nécessaire peut être raccroché à cet événement.

### <a name="troubleshoot-unloadability-issues"></a>Résoudre les problèmes de déchargement

En raison de la nature coopérative du déchargement, il est facile d’oublier les références qui peuvent conserver le contenu d’un collecté `AssemblyLoadContext` actif et empêcher le déchargement. Voici un résumé des entités (certaines d’entre elles non évidentes) qui peuvent contenir les références :

- Les références régulières détenues de l’extérieur de la collection `AssemblyLoadContext` sont stockées dans un emplacement de pile ou un registre de processeur (variables locales, créées explicitement par le code utilisateur ou implicitement par le compilateur juste-à-temps (JIT)), une variable statique ou un handle de GC fort (épinglage) et pointant vers :
  - Un assembly chargé dans l’`AssemblyLoadContext` pouvant être collecté.
  - Un type d’un tel assembly.
  - Une instance d’un type à partir d’un tel assembly.
- Threads exécutant du code à partir d’un assembly chargé dans l’`AssemblyLoadContext` pouvant être collecté.
- Instances de types personnalisés et non pouvant être collectés `AssemblyLoadContext` créés à l’intérieur de l’objets pouvant être collectés `AssemblyLoadContext` .
- <xref:System.Threading.RegisteredWaitHandle>Les instances en attente avec des rappels sont définies sur les méthodes dans le personnalisé `AssemblyLoadContext` .

> [!TIP]
> Les références d’objets stockées dans des emplacements de pile ou des registres de processeur et qui peuvent empêcher le déchargement d’un `AssemblyLoadContext` peuvent se produire dans les situations suivantes :
>
> - Lorsque les résultats de l’appel de fonction sont passés directement à une autre fonction, même s’il n’y a aucune variable locale créée par l’utilisateur.
> - Quand le compilateur JIT conserve une référence à un objet qui était disponible à un moment donné dans une méthode.

## <a name="debug-unloading-issues"></a>Déboguer les problèmes de déchargement

Le débogage des problèmes de déchargement peut être fastidieux. Vous pouvez vous retrouver dans des situations où le déchargement échoue sans que vous sachiez ce qui maintient un `AssemblyLoadContext` actif. Le meilleur moyen de résoudre ce genre de problème est d’utiliser WinDbg (LLDB sur UNIX) avec le plug-in SOS. Vous devez déterminer ce qui fait qu’un `LoaderAllocator` appartenant à l’`AssemblyLoadContext` donné reste actif. Le plug-in SOS vous permet d’examiner les objets du tas GC, leurs hiérarchies et leurs racines.

Pour charger le plug-in dans le débogueur, entrez la commande suivante dans la ligne de commande du débogueur :

Dans WinDbg (apparemment, WinDbg le fait automatiquement quand il s’arrête dans une application .NET Core) :

```console
.loadby sos coreclr
```

Dans LLDB :

```console
plugin load /path/to/libsosplugin.so
```

Déboguez un exemple de programme qui rencontre des problèmes de déchargement. Le code source est inclus ci-dessous. Quand vous l’exécutez sous WinDbg, le programme s’arrête dans le débogueur juste après la tentative de vérification de la réussite du déchargement. Vous pouvez ensuite commencer à rechercher les coupables.

> [!TIP]
> Si vous déboguez à l’aide de LLDB sur UNIX, les commandes SOS dans les exemples suivants n’ont pas le `!` devant.

```console
!dumpheap -type LoaderAllocator
```

Cette commande vide tous les objets dont le nom de type contient `LoaderAllocator` et qui se trouvent dans le tas GC. Voici un exemple :

```console
         Address               MT     Size
000002b78000ce40 00007ffadc93a288       48
000002b78000ceb0 00007ffadc93a218       24

Statistics:
              MT    Count    TotalSize Class Name
00007ffadc93a218        1           24 System.Reflection.LoaderAllocatorScout
00007ffadc93a288        1           48 System.Reflection.LoaderAllocator
Total 2 objects
```

Dans la partie « Statistics: » ci-dessous, examinez l’élément `MT` (`MethodTable`) appartenant à `System.Reflection.LoaderAllocator`, qui est l’objet qui nous intéresse. Ensuite, dans la liste au début, recherchez l’entrée correspondant à celle `MT` -ci et obtenez l’adresse de l’objet lui-même. Dans notre cas, il s’agit de « 000002b78000ce40 ».

Maintenant que nous savons l’adresse de l' `LoaderAllocator` objet, nous pouvons utiliser une autre commande pour rechercher ses racines GC :

```console
!gcroot -all 0x000002b78000ce40
```

Cette commande vide la chaîne des références d’objet qui mènent à l’instance `LoaderAllocator`. La liste commence par la racine, qui est l’entité qui conserve notre `LoaderAllocator` état actif et constitue donc le cœur du problème. La racine peut être un emplacement de pile, un registre de processeur, un handle de GC ou une variable statique.

Voici un exemple de sortie de la commande `gcroot` :

```console
Thread 4ac:
    000000cf9499dd20 00007ffa7d0236bc example.Program.Main(System.String[]) [E:\unloadability\example\Program.cs @ 70]
        rbp-20: 000000cf9499dd90
            ->  000002b78000d328 System.Reflection.RuntimeMethodInfo
            ->  000002b78000d1f8 System.RuntimeType+RuntimeTypeCache
            ->  000002b78000d1d0 System.RuntimeType
            ->  000002b78000ce40 System.Reflection.LoaderAllocator

HandleTable:
    000002b7f8a81198 (strong handle)
    -> 000002b78000d948 test.Test
    -> 000002b78000ce40 System.Reflection.LoaderAllocator

    000002b7f8a815f8 (pinned handle)
    -> 000002b790001038 System.Object[]
    -> 000002b78000d390 example.TestInfo
    -> 000002b78000d328 System.Reflection.RuntimeMethodInfo
    -> 000002b78000d1f8 System.RuntimeType+RuntimeTypeCache
    -> 000002b78000d1d0 System.RuntimeType
    -> 000002b78000ce40 System.Reflection.LoaderAllocator

Found 3 roots.
```

L’étape suivante consiste à déterminer où se trouve la racine afin de pouvoir la corriger. Dans le cas le plus simple, la racine est un emplacement de pile ou un registre de processeur. Dans ce cas, le `gcroot` affiche le nom de la fonction dont le frame contient la racine et le thread qui exécute cette fonction. La situation est plus complexe quand la racine est une variable statique ou un handle de GC.

Dans l’exemple précédent, la première racine est un local de type `System.Reflection.RuntimeMethodInfo` stocké dans le frame de la fonction `example.Program.Main(System.String[])` à l’adresse `rbp-20` (`rbp` est le registre de processeur `rbp` et -20 est un décalage hexadécimal de ce registre).

La deuxième racine est un `GCHandle` normal (fort) qui contient une référence à une instance de la classe `test.Test`.

La troisième racine est un `GCHandle` épinglé. Il s’agit en fait d’une variable statique, mais malheureusement, il n’existe aucun moyen de le savoir. Les variables statiques pour les types références sont stockées dans un tableau d’objets managés dans des structures de runtime internes.

Le déchargement d’un `AssemblyLoadContext` peut aussi ne pas aboutir quand un thread a le frame d’une méthode d’un assembly chargé dans l’`AssemblyLoadContext` sur sa pile. Pour vérifier cela, videz les piles d’appels managées de tous les threads :

```console
~*e !clrstack
```

La commande signifie « appliquer à tous les threads la commande `!clrstack` ». Voici la sortie de cette commande pour l’exemple. Malheureusement, LLDB sur UNIX n’a aucun moyen d’appliquer une commande à tous les threads. vous devez donc basculer manuellement les threads et répéter la `clrstack` commande. Ignore tous les threads où le débogueur indique « Impossible de parcourir la pile managée ».

```console
OS Thread Id: 0x6ba8 (0)
        Child SP               IP Call Site
0000001fc697d5c8 00007ffb50d9de12 [HelperMethodFrame: 0000001fc697d5c8] System.Diagnostics.Debugger.BreakInternal()
0000001fc697d6d0 00007ffa864765fa System.Diagnostics.Debugger.Break()
0000001fc697d700 00007ffa864736bc example.Program.Main(System.String[]) [E:\unloadability\example\Program.cs @ 70]
0000001fc697d998 00007ffae5fdc1e3 [GCFrame: 0000001fc697d998]
0000001fc697df28 00007ffae5fdc1e3 [GCFrame: 0000001fc697df28]
OS Thread Id: 0x2ae4 (1)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x61a4 (2)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x7fdc (3)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x5390 (4)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x5ec8 (5)
        Child SP               IP Call Site
0000001fc70ff6e0 00007ffb5437f6e4 [DebuggerU2MCatchHandlerFrame: 0000001fc70ff6e0]
OS Thread Id: 0x4624 (6)
        Child SP               IP Call Site
GetFrameContext failed: 1
0000000000000000 0000000000000000
OS Thread Id: 0x60bc (7)
        Child SP               IP Call Site
0000001fc727f158 00007ffb5437fce4 [HelperMethodFrame: 0000001fc727f158] System.Threading.Thread.SleepInternal(Int32)
0000001fc727f260 00007ffb37ea7c2b System.Threading.Thread.Sleep(Int32)
0000001fc727f290 00007ffa865005b3 test.Program.ThreadProc() [E:\unloadability\test\Program.cs @ 17]
0000001fc727f2c0 00007ffb37ea6a5b System.Threading.Thread.ThreadMain_ThreadStart()
0000001fc727f2f0 00007ffadbc4cbe3 System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object)
0000001fc727f568 00007ffae5fdc1e3 [GCFrame: 0000001fc727f568]
0000001fc727f7f0 00007ffae5fdc1e3 [DebuggerU2MCatchHandlerFrame: 0000001fc727f7f0]

```

Comme vous pouvez le voir, le dernier thread a `test.Program.ThreadProc()`. Il s’agit d’une fonction de l’assembly chargé dans `AssemblyLoadContext` qui maintient `AssemblyLoadContext` actif.

## <a name="example-source-with-unloadability-issues"></a>Exemple de source avec des problèmes de déchargement

Le code suivant est utilisé dans l’exemple de débogage précédent.

### <a name="main-testing-program"></a>Programme de test principal

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a>Programme chargé dans TestAssemblyLoadContext

Le code suivant représente l' *test.dll* passé à la `ExecuteAndUnload` méthode dans le programme de test principal.

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
