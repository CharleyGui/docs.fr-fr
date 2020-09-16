---
title: Traiter les tâches asynchrones terminées
description: Cet exemple montre comment utiliser Task. WhenAny en C# pour démarrer plusieurs tâches et traiter leurs résultats à mesure qu’ils se terminent, au lieu de les traiter dans l’ordre de début.
ms.date: 08/19/2020
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: 520953eaf851dc82440e39b348aa4b246255e126
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557305"
---
# <a name="process-asynchronous-tasks-as-they-complete-c"></a>Traiter les tâches asynchrones à mesure qu’elles se terminent (C#)

À l’aide de <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> , vous pouvez démarrer plusieurs tâches en même temps et les traiter une par une lorsqu’elles sont terminées, au lieu de les traiter dans l’ordre dans lequel elles sont démarrées.

L’exemple suivant utilise une requête pour créer une collection de tâches. Chaque tâche télécharge le contenu d’un site web spécifié. À chaque itération d’une boucle while, un appel attendu à <xref:System.Threading.Tasks.Task.WhenAny%2A> retourne la tâche de la collection de tâches dont le téléchargement se termine en premier. Cette tâche est supprimée de la collection et traitée. La boucle se répète jusqu’à ce que la collection ne contienne plus aucune tâche.

## <a name="create-example-application"></a>Créer un exemple d’application

Créez une application de console .NET Core. Vous pouvez en créer un à l’aide de la commande [dotnet New console](../../../../core/tools/dotnet-new.md#console) ou de [Visual Studio](/visualstudio/install/install-visual-studio). Ouvrez le fichier *Program.cs* dans votre éditeur de code favori.

### <a name="replace-using-statements"></a>Remplacer les instructions using

Remplacez les instructions using existantes par les déclarations suivantes :

```csharp
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Linq;
using System.Net.Http;
using System.Threading.Tasks;
```

## <a name="add-fields"></a>Ajouter des champs

Dans la `Program` définition de classe, ajoutez les deux champs suivants :

```csharp
static readonly HttpClient s_client = new HttpClient
{
    MaxResponseContentBufferSize = 1_000_000
};

static readonly IEnumerable<string> s_urlList = new string[]
{
    "https://docs.microsoft.com",
    "https://docs.microsoft.com/aspnet/core",
    "https://docs.microsoft.com/azure",
    "https://docs.microsoft.com/azure/devops",
    "https://docs.microsoft.com/dotnet",
    "https://docs.microsoft.com/dynamics365",
    "https://docs.microsoft.com/education",
    "https://docs.microsoft.com/enterprise-mobility-security",
    "https://docs.microsoft.com/gaming",
    "https://docs.microsoft.com/graph",
    "https://docs.microsoft.com/microsoft-365",
    "https://docs.microsoft.com/office",
    "https://docs.microsoft.com/powershell",
    "https://docs.microsoft.com/sql",
    "https://docs.microsoft.com/surface",
    "https://docs.microsoft.com/system-center",
    "https://docs.microsoft.com/visualstudio",
    "https://docs.microsoft.com/windows",
    "https://docs.microsoft.com/xamarin"
};
```

Le `HttpClient` expose la possibilité d’envoyer des requêtes http et de recevoir des réponses http. Le `s_urlList` contient toutes les URL que l’application envisage de traiter.

## <a name="update-application-entry-point"></a>Mettre à jour le point d’entrée de l’application

Le point d’entrée principal dans l’application console est la `Main` méthode. Remplacez la méthode existante par le code suivant :

```csharp
static Task Main() => SumPageSizesAsync();
```

La méthode mise à jour `Main` est maintenant considérée comme une [main asynchrone](../../../whats-new/csharp-7-1.md#async-main), ce qui permet d’obtenir un point d’entrée asynchrone dans l’exécutable. Il s’agit d’un appel à `SumPageSizesAsync` .

## <a name="create-the-asynchronous-sum-page-sizes-method"></a>Créer la méthode de taille de page Sum asynchrone

Sous la `Main` méthode, ajoutez la `SumPageSizesAsync` méthode :

```csharp
static async Task SumPageSizesAsync()
{
    var stopwatch = Stopwatch.StartNew();

    IEnumerable<Task<int>> downloadTasksQuery =
        from url in s_urlList
        select ProcessUrlAsync(url, s_client);

    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();

    int total = 0;
    while (downloadTasks.Any())
    {
        Task<int> finishedTask = await Task.WhenAny(downloadTasks);
        downloadTasks.Remove(finishedTask);
        total += await finishedTask;
    }

    stopwatch.Stop();

    Console.WriteLine($"\nTotal bytes returned:  {total:#,#}");
    Console.WriteLine($"Elapsed time:          {stopwatch.Elapsed}\n");
}
```

La méthode commence par instancier et démarrer un <xref:System.Diagnostics.Stopwatch> . Il comprend ensuite une requête qui, lorsqu’elle est exécutée, crée une collection de tâches. Chaque appel à `ProcessUrlAsync` dans le code suivant retourne un <xref:System.Threading.Tasks.Task%601>, où `TResult` est un entier :

```csharp
IEnumerable<Task<int>> downloadTasksQuery =
    from url in s_urlList
    select ProcessUrlAsync(url, s_client);
```

En raison d’une [exécution différée](../../../../standard/linq/deferred-execution-example.md) avec LINQ, vous appelez <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> pour démarrer chaque tâche.

```csharp
List<Task<int>> downloadTasks = downloadTasksQuery.ToList();
```

La `while` boucle effectue les étapes suivantes pour chaque tâche de la collection :

1. Attend un appel à `WhenAny` pour identifier la première tâche de la collection dont le téléchargement est terminé.

    ```csharp
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);
    ```

1. Elle supprime cette tâche de la collection.

    ```csharp
    downloadTasks.Remove(firstFinishedTask);
    ```

1. Elle attend `finishedTask`, qui est retourné par un appel à `ProcessUrlAsync`. La variable `finishedTask` est un <xref:System.Threading.Tasks.Task%601> où `TResult` est un entier. La tâche est déjà terminée, mais vous l’attendez pour récupérer la longueur du site web téléchargé, comme le montre l’exemple suivant. Si la tâche est défaillante, `await` lèvera la première exception enfant stockée dans le `AggregateException` , contrairement à la lecture de la <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> propriété, qui lèverait `AggregateException` .

    ```csharp
    total += await finishedTask;
    ```

## <a name="add-process-method"></a>Ajouter une méthode de traitement

Ajoutez la méthode suivante en `ProcessUrlAsync` dessous de la `SumPageSizesAsync` méthode :

```csharp
static async Task<int> ProcessUrlAsync(string url, HttpClient client)
{
    byte[] content = await client.GetByteArrayAsync(url);
    Console.WriteLine($"{url,-60} {content.Length,10:#,#}");

    return content.Length;
}
```

Pour une URL donnée, la méthode utilise l' `client` instance fournie pour obtenir la réponse en tant que `byte[]` . La longueur est retournée une fois que l’URL et la longueur sont écrites dans la console.

Exécutez le programme plusieurs fois pour vérifier que les longueurs téléchargées n’apparaissent pas toujours dans le même ordre.

> [!CAUTION]
> Vous pouvez utiliser `WhenAny` dans une boucle, comme décrit dans l’exemple, pour résoudre les problèmes qui impliquent un petit nombre de tâches. Cependant, d’autres approches sont plus efficaces si vous avez un grand nombre de tâches à traiter. Pour plus d’informations et d’exemples, consultez [traitement des tâches lorsqu’elles sont terminées](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete).

## <a name="complete-example"></a>Exemple complet

Le code suivant est le texte complet du fichier *Program.cs* pour l’exemple.

:::code language="csharp" source="snippets/multiple-tasks/Program.cs":::

## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [Programmation asynchrone avec Async et await (C#)](index.md)
