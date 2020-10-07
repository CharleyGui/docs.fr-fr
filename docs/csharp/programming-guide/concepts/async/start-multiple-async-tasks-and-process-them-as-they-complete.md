---
title: Traiter les tâches asynchrones terminées
description: Cet exemple montre comment utiliser Task. WhenAny en C# pour démarrer plusieurs tâches et traiter leurs résultats à mesure qu’ils se terminent, au lieu de les traiter dans l’ordre de début.
ms.date: 08/19/2020
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: 860e94a9c3973ce56e7321741a1136f752aa3d18
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91805237"
---
# <a name="process-asynchronous-tasks-as-they-complete-c"></a><span data-ttu-id="52cec-103">Traiter les tâches asynchrones à mesure qu’elles se terminent (C#)</span><span class="sxs-lookup"><span data-stu-id="52cec-103">Process asynchronous tasks as they complete (C#)</span></span>

<span data-ttu-id="52cec-104">À l’aide de <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> , vous pouvez démarrer plusieurs tâches en même temps et les traiter une par une lorsqu’elles sont terminées, au lieu de les traiter dans l’ordre dans lequel elles sont démarrées.</span><span class="sxs-lookup"><span data-stu-id="52cec-104">By using <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, you can start multiple tasks at the same time and process them one by one as they're completed rather than process them in the order in which they're started.</span></span>

<span data-ttu-id="52cec-105">L’exemple suivant utilise une requête pour créer une collection de tâches.</span><span class="sxs-lookup"><span data-stu-id="52cec-105">The following example uses a query to create a collection of tasks.</span></span> <span data-ttu-id="52cec-106">Chaque tâche télécharge le contenu d’un site web spécifié.</span><span class="sxs-lookup"><span data-stu-id="52cec-106">Each task downloads the contents of a specified website.</span></span> <span data-ttu-id="52cec-107">À chaque itération d’une boucle while, un appel attendu à <xref:System.Threading.Tasks.Task.WhenAny%2A> retourne la tâche de la collection de tâches dont le téléchargement se termine en premier.</span><span class="sxs-lookup"><span data-stu-id="52cec-107">In each iteration of a while loop, an awaited call to <xref:System.Threading.Tasks.Task.WhenAny%2A> returns the task in the collection of tasks that finishes its download first.</span></span> <span data-ttu-id="52cec-108">Cette tâche est supprimée de la collection et traitée.</span><span class="sxs-lookup"><span data-stu-id="52cec-108">That task is removed from the collection and processed.</span></span> <span data-ttu-id="52cec-109">La boucle se répète jusqu’à ce que la collection ne contienne plus aucune tâche.</span><span class="sxs-lookup"><span data-stu-id="52cec-109">The loop repeats until the collection contains no more tasks.</span></span>

## <a name="create-example-application"></a><span data-ttu-id="52cec-110">Créer un exemple d’application</span><span class="sxs-lookup"><span data-stu-id="52cec-110">Create example application</span></span>

<span data-ttu-id="52cec-111">Créez une application de console .NET Core.</span><span class="sxs-lookup"><span data-stu-id="52cec-111">Create a new .NET Core console application.</span></span> <span data-ttu-id="52cec-112">Vous pouvez en créer un à l’aide de la commande [dotnet New console](../../../../core/tools/dotnet-new.md#console) ou de [Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="52cec-112">You can create one by using the [dotnet new console](../../../../core/tools/dotnet-new.md#console) command or from [Visual Studio](/visualstudio/install/install-visual-studio).</span></span> <span data-ttu-id="52cec-113">Ouvrez le fichier *Program.cs* dans votre éditeur de code favori.</span><span class="sxs-lookup"><span data-stu-id="52cec-113">Open the *Program.cs* file in your favorite code editor.</span></span>

### <a name="replace-using-statements"></a><span data-ttu-id="52cec-114">Remplacer les instructions using</span><span class="sxs-lookup"><span data-stu-id="52cec-114">Replace using statements</span></span>

<span data-ttu-id="52cec-115">Remplacez les instructions using existantes par les déclarations suivantes :</span><span class="sxs-lookup"><span data-stu-id="52cec-115">Replace the existing using statements with these declarations:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Linq;
using System.Net.Http;
using System.Threading.Tasks;
```

## <a name="add-fields"></a><span data-ttu-id="52cec-116">Ajouter des champs</span><span class="sxs-lookup"><span data-stu-id="52cec-116">Add fields</span></span>

<span data-ttu-id="52cec-117">Dans la `Program` définition de classe, ajoutez les deux champs suivants :</span><span class="sxs-lookup"><span data-stu-id="52cec-117">In the `Program` class definition, add the following two fields:</span></span>

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

<span data-ttu-id="52cec-118">Le `HttpClient` expose la possibilité d’envoyer des requêtes http et de recevoir des réponses http.</span><span class="sxs-lookup"><span data-stu-id="52cec-118">The `HttpClient` exposes the ability to send HTTP requests and receive HTTP responses.</span></span> <span data-ttu-id="52cec-119">Le `s_urlList` contient toutes les URL que l’application envisage de traiter.</span><span class="sxs-lookup"><span data-stu-id="52cec-119">The `s_urlList` holds all of the URLs that the application plans to process.</span></span>

## <a name="update-application-entry-point"></a><span data-ttu-id="52cec-120">Mettre à jour le point d’entrée de l’application</span><span class="sxs-lookup"><span data-stu-id="52cec-120">Update application entry point</span></span>

<span data-ttu-id="52cec-121">Le point d’entrée principal dans l’application console est la `Main` méthode.</span><span class="sxs-lookup"><span data-stu-id="52cec-121">The main entry point into the console application is the `Main` method.</span></span> <span data-ttu-id="52cec-122">Remplacez la méthode existante par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="52cec-122">Replace the existing method with the following:</span></span>

```csharp
static Task Main() => SumPageSizesAsync();
```

<span data-ttu-id="52cec-123">La méthode mise à jour `Main` est maintenant considérée comme une [main asynchrone](../../../whats-new/csharp-7.md#async-main), ce qui permet d’obtenir un point d’entrée asynchrone dans l’exécutable.</span><span class="sxs-lookup"><span data-stu-id="52cec-123">The updated `Main` method is now considered an [Async main](../../../whats-new/csharp-7.md#async-main), which allows for an asynchronous entry point into the executable.</span></span> <span data-ttu-id="52cec-124">Il s’agit d’un appel à `SumPageSizesAsync` .</span><span class="sxs-lookup"><span data-stu-id="52cec-124">It is expressed a call to `SumPageSizesAsync`.</span></span>

## <a name="create-the-asynchronous-sum-page-sizes-method"></a><span data-ttu-id="52cec-125">Créer la méthode de taille de page Sum asynchrone</span><span class="sxs-lookup"><span data-stu-id="52cec-125">Create the asynchronous sum page sizes method</span></span>

<span data-ttu-id="52cec-126">Sous la `Main` méthode, ajoutez la `SumPageSizesAsync` méthode :</span><span class="sxs-lookup"><span data-stu-id="52cec-126">Below the `Main` method, add the `SumPageSizesAsync` method:</span></span>

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

<span data-ttu-id="52cec-127">La méthode commence par instancier et démarrer un <xref:System.Diagnostics.Stopwatch> .</span><span class="sxs-lookup"><span data-stu-id="52cec-127">The method starts by instantiating and starting a <xref:System.Diagnostics.Stopwatch>.</span></span> <span data-ttu-id="52cec-128">Il comprend ensuite une requête qui, lorsqu’elle est exécutée, crée une collection de tâches.</span><span class="sxs-lookup"><span data-stu-id="52cec-128">It then includes a query that, when executed, creates a collection of tasks.</span></span> <span data-ttu-id="52cec-129">Chaque appel à `ProcessUrlAsync` dans le code suivant retourne un <xref:System.Threading.Tasks.Task%601>, où `TResult` est un entier :</span><span class="sxs-lookup"><span data-stu-id="52cec-129">Each call to `ProcessUrlAsync` in the following code returns a <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer:</span></span>

```csharp
IEnumerable<Task<int>> downloadTasksQuery =
    from url in s_urlList
    select ProcessUrlAsync(url, s_client);
```

<span data-ttu-id="52cec-130">En raison d’une [exécution différée](../../../../standard/linq/deferred-execution-example.md) avec LINQ, vous appelez <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> pour démarrer chaque tâche.</span><span class="sxs-lookup"><span data-stu-id="52cec-130">Due to [deferred execution](../../../../standard/linq/deferred-execution-example.md) with the LINQ, you call <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> to start each task.</span></span>

```csharp
List<Task<int>> downloadTasks = downloadTasksQuery.ToList();
```

<span data-ttu-id="52cec-131">La `while` boucle effectue les étapes suivantes pour chaque tâche de la collection :</span><span class="sxs-lookup"><span data-stu-id="52cec-131">The `while` loop performs the following steps for each task in the collection:</span></span>

1. <span data-ttu-id="52cec-132">Attend un appel à `WhenAny` pour identifier la première tâche de la collection dont le téléchargement est terminé.</span><span class="sxs-lookup"><span data-stu-id="52cec-132">Awaits a call to `WhenAny` to identify the first task in the collection that has finished its download.</span></span>

    ```csharp
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);
    ```

1. <span data-ttu-id="52cec-133">Elle supprime cette tâche de la collection.</span><span class="sxs-lookup"><span data-stu-id="52cec-133">Removes that task from the collection.</span></span>

    ```csharp
    downloadTasks.Remove(firstFinishedTask);
    ```

1. <span data-ttu-id="52cec-134">Elle attend `finishedTask`, qui est retourné par un appel à `ProcessUrlAsync`.</span><span class="sxs-lookup"><span data-stu-id="52cec-134">Awaits `finishedTask`, which is returned by a call to `ProcessUrlAsync`.</span></span> <span data-ttu-id="52cec-135">La variable `finishedTask` est un <xref:System.Threading.Tasks.Task%601> où `TResult` est un entier.</span><span class="sxs-lookup"><span data-stu-id="52cec-135">The `finishedTask` variable is a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span> <span data-ttu-id="52cec-136">La tâche est déjà terminée, mais vous l’attendez pour récupérer la longueur du site web téléchargé, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="52cec-136">The task is already complete, but you await it to retrieve the length of the downloaded website, as the following example shows.</span></span> <span data-ttu-id="52cec-137">Si la tâche est défaillante, `await` lèvera la première exception enfant stockée dans le `AggregateException` , contrairement à la lecture de la <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> propriété, qui lèverait `AggregateException` .</span><span class="sxs-lookup"><span data-stu-id="52cec-137">If the task is faulted, `await` will throw the first child exception stored in the `AggregateException`, unlike reading the <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> property, which would throw the `AggregateException`.</span></span>

    ```csharp
    total += await finishedTask;
    ```

## <a name="add-process-method"></a><span data-ttu-id="52cec-138">Ajouter une méthode de traitement</span><span class="sxs-lookup"><span data-stu-id="52cec-138">Add process method</span></span>

<span data-ttu-id="52cec-139">Ajoutez la méthode suivante en `ProcessUrlAsync` dessous de la `SumPageSizesAsync` méthode :</span><span class="sxs-lookup"><span data-stu-id="52cec-139">Add the following `ProcessUrlAsync` method below the `SumPageSizesAsync` method:</span></span>

```csharp
static async Task<int> ProcessUrlAsync(string url, HttpClient client)
{
    byte[] content = await client.GetByteArrayAsync(url);
    Console.WriteLine($"{url,-60} {content.Length,10:#,#}");

    return content.Length;
}
```

<span data-ttu-id="52cec-140">Pour une URL donnée, la méthode utilise l' `client` instance fournie pour obtenir la réponse en tant que `byte[]` .</span><span class="sxs-lookup"><span data-stu-id="52cec-140">For any given URL, the method will use the `client` instance provided to get the response as a `byte[]`.</span></span> <span data-ttu-id="52cec-141">La longueur est retournée une fois que l’URL et la longueur sont écrites dans la console.</span><span class="sxs-lookup"><span data-stu-id="52cec-141">The length is returned after the URL and length is written to the console.</span></span>

<span data-ttu-id="52cec-142">Exécutez le programme plusieurs fois pour vérifier que les longueurs téléchargées n’apparaissent pas toujours dans le même ordre.</span><span class="sxs-lookup"><span data-stu-id="52cec-142">Run the program several times to verify that the downloaded lengths don't always appear in the same order.</span></span>

> [!CAUTION]
> <span data-ttu-id="52cec-143">Vous pouvez utiliser `WhenAny` dans une boucle, comme décrit dans l’exemple, pour résoudre les problèmes qui impliquent un petit nombre de tâches.</span><span class="sxs-lookup"><span data-stu-id="52cec-143">You can use `WhenAny` in a loop, as described in the example, to solve problems that involve a small number of tasks.</span></span> <span data-ttu-id="52cec-144">Cependant, d’autres approches sont plus efficaces si vous avez un grand nombre de tâches à traiter.</span><span class="sxs-lookup"><span data-stu-id="52cec-144">However, other approaches are more efficient if you have a large number of tasks to process.</span></span> <span data-ttu-id="52cec-145">Pour plus d’informations et d’exemples, consultez [traitement des tâches lorsqu’elles sont terminées](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete).</span><span class="sxs-lookup"><span data-stu-id="52cec-145">For more information and examples, see [Processing tasks as they complete](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete).</span></span>

## <a name="complete-example"></a><span data-ttu-id="52cec-146">Exemple complet</span><span class="sxs-lookup"><span data-stu-id="52cec-146">Complete example</span></span>

<span data-ttu-id="52cec-147">Le code suivant est le texte complet du fichier *Program.cs* pour l’exemple.</span><span class="sxs-lookup"><span data-stu-id="52cec-147">The following code is the complete text of the *Program.cs* file for the example.</span></span>

:::code language="csharp" source="snippets/multiple-tasks/Program.cs":::

## <a name="see-also"></a><span data-ttu-id="52cec-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52cec-148">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="52cec-149">Programmation asynchrone avec Async et await (C#)</span><span class="sxs-lookup"><span data-stu-id="52cec-149">Asynchronous programming with async and await (C#)</span></span>](index.md)
