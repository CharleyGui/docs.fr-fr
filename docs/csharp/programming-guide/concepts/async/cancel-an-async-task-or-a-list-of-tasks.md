---
title: Annuler une liste de tâches (C#)
description: Découvrez comment utiliser des jetons d’annulation pour signaler une demande d’annulation à une liste de tâches.
ms.date: 08/19/2020
ms.topic: tutorial
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 84cd1bb413d20b6c13be8415c13c72b57873b1cf
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654703"
---
# <a name="cancel-a-list-of-tasks-c"></a><span data-ttu-id="e1c67-103">Annuler une liste de tâches (C#)</span><span class="sxs-lookup"><span data-stu-id="e1c67-103">Cancel a list of tasks (C#)</span></span>

<span data-ttu-id="e1c67-104">Vous pouvez annuler une application console Async si vous ne souhaitez pas attendre qu’elle se termine.</span><span class="sxs-lookup"><span data-stu-id="e1c67-104">You can cancel an async console application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="e1c67-105">En suivant l’exemple de cette rubrique, vous pouvez ajouter une annulation à une application qui télécharge le contenu d’une liste de sites Web.</span><span class="sxs-lookup"><span data-stu-id="e1c67-105">By following the example in this topic, you can add a cancellation to an application that downloads the contents of a list of websites.</span></span> <span data-ttu-id="e1c67-106">Vous pouvez annuler de nombreuses tâches en associant l' <xref:System.Threading.CancellationTokenSource> instance à chaque tâche.</span><span class="sxs-lookup"><span data-stu-id="e1c67-106">You can cancel many tasks by associating the <xref:System.Threading.CancellationTokenSource> instance with each task.</span></span> <span data-ttu-id="e1c67-107">Si vous sélectionnez la touche <kbd>entrée</kbd> , vous annulez toutes les tâches qui ne sont pas encore terminées.</span><span class="sxs-lookup"><span data-stu-id="e1c67-107">If you select the <kbd>Enter</kbd> key, you cancel all tasks that aren't yet complete.</span></span>

<span data-ttu-id="e1c67-108">Ce didacticiel contient les sections suivantes :</span><span class="sxs-lookup"><span data-stu-id="e1c67-108">This tutorial covers:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="e1c67-109">Création d’une application console .NET</span><span class="sxs-lookup"><span data-stu-id="e1c67-109">Creating a .NET console application</span></span>
> - <span data-ttu-id="e1c67-110">Écriture d’une application Async qui prend en charge l’annulation</span><span class="sxs-lookup"><span data-stu-id="e1c67-110">Writing an async application that supports cancellation</span></span>
> - <span data-ttu-id="e1c67-111">Démonstration de l’annulation de la signalisation</span><span class="sxs-lookup"><span data-stu-id="e1c67-111">Demonstrating signaling cancellation</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e1c67-112">Prérequis</span><span class="sxs-lookup"><span data-stu-id="e1c67-112">Prerequisites</span></span>

<span data-ttu-id="e1c67-113">Ce didacticiel requiert les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="e1c67-113">This tutorial requires the following:</span></span>

- [<span data-ttu-id="e1c67-114">.NET 5,0 ou kit de développement logiciel (SDK) ultérieur</span><span class="sxs-lookup"><span data-stu-id="e1c67-114">.NET 5.0 or later SDK</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
- <span data-ttu-id="e1c67-115">Environnement de développement intégré (IDE)</span><span class="sxs-lookup"><span data-stu-id="e1c67-115">Integrated development environment (IDE)</span></span>
  - [<span data-ttu-id="e1c67-116">Nous vous recommandons Visual Studio, Visual Studio Code ou Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="e1c67-116">We recommend Visual Studio, Visual Studio Code, or Visual Studio for Mac</span></span>](https://visualstudio.microsoft.com)

### <a name="create-example-application"></a><span data-ttu-id="e1c67-117">Créer un exemple d’application</span><span class="sxs-lookup"><span data-stu-id="e1c67-117">Create example application</span></span>

<span data-ttu-id="e1c67-118">Créez une application de console .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e1c67-118">Create a new .NET Core console application.</span></span> <span data-ttu-id="e1c67-119">Vous pouvez en créer un à l’aide de la [`dotnet new console`](../../../../core/tools/dotnet-new.md#console) commande ou de [Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="e1c67-119">You can create one by using the [`dotnet new console`](../../../../core/tools/dotnet-new.md#console) command or from [Visual Studio](/visualstudio/install/install-visual-studio).</span></span> <span data-ttu-id="e1c67-120">Ouvrez le fichier *Program.cs* dans votre éditeur de code favori.</span><span class="sxs-lookup"><span data-stu-id="e1c67-120">Open the *Program.cs* file in your favorite code editor.</span></span>

### <a name="replace-using-statements"></a><span data-ttu-id="e1c67-121">Remplacer les instructions using</span><span class="sxs-lookup"><span data-stu-id="e1c67-121">Replace using statements</span></span>

<span data-ttu-id="e1c67-122">Remplacez les instructions using existantes par les déclarations suivantes :</span><span class="sxs-lookup"><span data-stu-id="e1c67-122">Replace the existing using statements with these declarations:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Net.Http;
using System.Threading;
using System.Threading.Tasks;
```

## <a name="add-fields"></a><span data-ttu-id="e1c67-123">Ajouter des champs</span><span class="sxs-lookup"><span data-stu-id="e1c67-123">Add fields</span></span>

<span data-ttu-id="e1c67-124">Dans la `Program` définition de classe, ajoutez les trois champs suivants :</span><span class="sxs-lookup"><span data-stu-id="e1c67-124">In the `Program` class definition, add these three fields:</span></span>

```csharp
static readonly CancellationTokenSource s_cts = new CancellationTokenSource();

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

<span data-ttu-id="e1c67-125">Le <xref:System.Threading.CancellationTokenSource> est utilisé pour signaler une annulation demandée à un <xref:System.Threading.CancellationToken> .</span><span class="sxs-lookup"><span data-stu-id="e1c67-125">The <xref:System.Threading.CancellationTokenSource> is used to signal a requested cancellation to a <xref:System.Threading.CancellationToken>.</span></span> <span data-ttu-id="e1c67-126">Le `HttpClient` expose la possibilité d’envoyer des requêtes http et de recevoir des réponses http.</span><span class="sxs-lookup"><span data-stu-id="e1c67-126">The `HttpClient` exposes the ability to send HTTP requests and receive HTTP responses.</span></span> <span data-ttu-id="e1c67-127">Le `s_urlList` contient toutes les URL que l’application envisage de traiter.</span><span class="sxs-lookup"><span data-stu-id="e1c67-127">The `s_urlList` holds all of the URLs that the application plans to process.</span></span>

## <a name="update-application-entry-point"></a><span data-ttu-id="e1c67-128">Mettre à jour le point d’entrée de l’application</span><span class="sxs-lookup"><span data-stu-id="e1c67-128">Update application entry point</span></span>

<span data-ttu-id="e1c67-129">Le point d’entrée principal dans l’application console est la `Main` méthode.</span><span class="sxs-lookup"><span data-stu-id="e1c67-129">The main entry point into the console application is the `Main` method.</span></span> <span data-ttu-id="e1c67-130">Remplacez la méthode existante par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="e1c67-130">Replace the existing method with the following:</span></span>

```csharp
static async Task Main()
{
    Console.WriteLine("Application started.");
    Console.WriteLine("Press the ENTER key to cancel...\n");

    Task cancelTask = Task.Run(() =>
    {
        while (Console.ReadKey().Key != ConsoleKey.Enter)
        {
            Console.WriteLine("Press the ENTER key to cancel...");
        }

        Console.WriteLine("\nENTER key pressed: cancelling downloads.\n");
        s_cts.Cancel();
    });

    Task sumPageSizesTask = SumPageSizesAsync();

    await Task.WhenAny(new[] { cancelTask, sumPageSizesTask });

    Console.WriteLine("Application ending.");
}
```

<span data-ttu-id="e1c67-131">La méthode mise à jour `Main` est maintenant considérée comme une [main asynchrone](../../../whats-new/csharp-7-1.md#async-main), ce qui permet d’obtenir un point d’entrée asynchrone dans l’exécutable.</span><span class="sxs-lookup"><span data-stu-id="e1c67-131">The updated `Main` method is now considered an [Async main](../../../whats-new/csharp-7-1.md#async-main), which allows for an asynchronous entry point into the executable.</span></span> <span data-ttu-id="e1c67-132">Il écrit quelques messages d’instructions dans la console, puis déclare une <xref:System.Threading.Tasks.Task> instance nommée `cancelTask` , qui lira les séquences de touches de la console.</span><span class="sxs-lookup"><span data-stu-id="e1c67-132">It writes a few instructional messages to the console, then declares a <xref:System.Threading.Tasks.Task> instance named `cancelTask`, which will read console key strokes.</span></span> <span data-ttu-id="e1c67-133">Si la touche <kbd>entrée</kbd> est enfoncée, un appel à <xref:System.Threading.CancellationTokenSource.Cancel?displayProperty=nameWithType> est effectué.</span><span class="sxs-lookup"><span data-stu-id="e1c67-133">If the <kbd>Enter</kbd> key is pressed, a call to <xref:System.Threading.CancellationTokenSource.Cancel?displayProperty=nameWithType> is made.</span></span> <span data-ttu-id="e1c67-134">Cela signalera l’annulation.</span><span class="sxs-lookup"><span data-stu-id="e1c67-134">This will signal cancellation.</span></span> <span data-ttu-id="e1c67-135">Ensuite, la `sumPageSizesTask` variable est assignée à partir de la `SumPageSizesAsync` méthode.</span><span class="sxs-lookup"><span data-stu-id="e1c67-135">Next, the `sumPageSizesTask` variable is assigned from the `SumPageSizesAsync` method.</span></span> <span data-ttu-id="e1c67-136">Les deux tâches sont ensuite transmises à <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])?displayProperty=nameWithType> , qui se poursuivra quand l’une des deux tâches sera terminée.</span><span class="sxs-lookup"><span data-stu-id="e1c67-136">Both tasks are then passed to <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])?displayProperty=nameWithType>, which will continue when any of the two tasks have completed.</span></span>

## <a name="create-the-asynchronous-sum-page-sizes-method"></a><span data-ttu-id="e1c67-137">Créer la méthode de taille de page Sum asynchrone</span><span class="sxs-lookup"><span data-stu-id="e1c67-137">Create the asynchronous sum page sizes method</span></span>

<span data-ttu-id="e1c67-138">Sous la `Main` méthode, ajoutez la `SumPageSizesAsync` méthode :</span><span class="sxs-lookup"><span data-stu-id="e1c67-138">Below the `Main` method, add the `SumPageSizesAsync` method:</span></span>

```csharp
static async Task SumPageSizesAsync()
{
    var stopwatch = Stopwatch.StartNew();

    int total = 0;
    foreach (string url in s_urlList)
    {
        int contentLength = await ProcessUrlAsync(url, s_client, s_cts.Token);
        total += contentLength;
    }

    stopwatch.Stop();

    Console.WriteLine($"\nTotal bytes returned:  {total:#,#}");
    Console.WriteLine($"Elapsed time:          {stopwatch.Elapsed}\n");
}
```

<span data-ttu-id="e1c67-139">La méthode commence par instancier et démarrer un <xref:System.Diagnostics.Stopwatch> .</span><span class="sxs-lookup"><span data-stu-id="e1c67-139">The method starts by instantiating and starting a <xref:System.Diagnostics.Stopwatch>.</span></span> <span data-ttu-id="e1c67-140">Il parcourt ensuite chaque URL dans le `s_urlList` et appelle `ProcessUrlAsync` .</span><span class="sxs-lookup"><span data-stu-id="e1c67-140">It then loops through each URL in the `s_urlList` and calls `ProcessUrlAsync`.</span></span> <span data-ttu-id="e1c67-141">Avec chaque itération, le `s_cts.Token` est passé dans la `ProcessUrlAsync` méthode et le code retourne un <xref:System.Threading.Tasks.Task%601> , où `TResult` est un entier :</span><span class="sxs-lookup"><span data-stu-id="e1c67-141">With each iteration, the `s_cts.Token` is passed into the `ProcessUrlAsync` method and the code returns a <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer:</span></span>

```csharp
int total = 0;
foreach (string url in s_urlList)
{
    int contentLength = await ProcessUrlAsync(url, s_client, s_cts.Token);
    total += contentLength;
}
```

## <a name="add-process-method"></a><span data-ttu-id="e1c67-142">Ajouter une méthode de traitement</span><span class="sxs-lookup"><span data-stu-id="e1c67-142">Add process method</span></span>

<span data-ttu-id="e1c67-143">Ajoutez la méthode suivante en `ProcessUrlAsync` dessous de la `SumPageSizesAsync` méthode :</span><span class="sxs-lookup"><span data-stu-id="e1c67-143">Add the following `ProcessUrlAsync` method below the `SumPageSizesAsync` method:</span></span>

```csharp
static async Task<int> ProcessUrlAsync(string url, HttpClient client, CancellationToken token)
{
    HttpResponseMessage response = await client.GetAsync(url, token);
    byte[] content = await response.Content.ReadAsByteArrayAsync();
    Console.WriteLine($"{url,-60} {content.Length,10:#,#}");

    return content.Length;
}
```

<span data-ttu-id="e1c67-144">Pour une URL donnée, la méthode utilise l' `client` instance fournie pour obtenir la réponse en tant que `byte[]` .</span><span class="sxs-lookup"><span data-stu-id="e1c67-144">For any given URL, the method will use the `client` instance provided to get the response as a `byte[]`.</span></span> <span data-ttu-id="e1c67-145">L' <xref:System.Threading.CancellationToken> instance est passée dans les <xref:System.Net.Http.HttpClient.GetAsync(System.String,System.Threading.CancellationToken)?displayProperty=nameWithType> <xref:System.Net.Http.HttpContent.ReadAsByteArrayAsync?displayProperty=nameWithType> méthodes et.</span><span class="sxs-lookup"><span data-stu-id="e1c67-145">The <xref:System.Threading.CancellationToken> instance is passed into the <xref:System.Net.Http.HttpClient.GetAsync(System.String,System.Threading.CancellationToken)?displayProperty=nameWithType> and <xref:System.Net.Http.HttpContent.ReadAsByteArrayAsync?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="e1c67-146">Le `token` est utilisé pour s’inscrire à l’annulation demandée.</span><span class="sxs-lookup"><span data-stu-id="e1c67-146">The `token` is used to register for requested cancellation.</span></span> <span data-ttu-id="e1c67-147">La longueur est retournée une fois que l’URL et la longueur sont écrites dans la console.</span><span class="sxs-lookup"><span data-stu-id="e1c67-147">The length is returned after the URL and length is written to the console.</span></span>

### <a name="example-application-output"></a><span data-ttu-id="e1c67-148">Exemple de sortie d’application</span><span class="sxs-lookup"><span data-stu-id="e1c67-148">Example application output</span></span>

```console
Application started.
Press the ENTER key to cancel...

https://docs.microsoft.com                                       37,357
https://docs.microsoft.com/aspnet/core                           85,589
https://docs.microsoft.com/azure                                398,939
https://docs.microsoft.com/azure/devops                          73,663
https://docs.microsoft.com/dotnet                                67,452
https://docs.microsoft.com/dynamics365                           48,582
https://docs.microsoft.com/education                             22,924

ENTER key pressed: cancelling downloads.

Application ending.
```

## <a name="complete-example"></a><span data-ttu-id="e1c67-149">Exemple complet</span><span class="sxs-lookup"><span data-stu-id="e1c67-149">Complete example</span></span>

<span data-ttu-id="e1c67-150">Le code suivant est le texte complet du fichier *Program.cs* pour l’exemple.</span><span class="sxs-lookup"><span data-stu-id="e1c67-150">The following code is the complete text of the *Program.cs* file for the example.</span></span>

:::code language="csharp" source="snippets/cancel-tasks/cancel-tasks/Program.cs":::

## <a name="see-also"></a><span data-ttu-id="e1c67-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1c67-151">See also</span></span>

- <xref:System.Threading.CancellationToken>
- <xref:System.Threading.CancellationTokenSource>
- [<span data-ttu-id="e1c67-152">Programmation asynchrone avec Async et await (C#)</span><span class="sxs-lookup"><span data-stu-id="e1c67-152">Asynchronous programming with async and await (C#)</span></span>](index.md)

## <a name="next-steps"></a><span data-ttu-id="e1c67-153">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="e1c67-153">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e1c67-154">Annuler des tâches async après une période spécifique (C#)</span><span class="sxs-lookup"><span data-stu-id="e1c67-154">Cancel async tasks after a period of time (C#)</span></span>](cancel-async-tasks-after-a-period-of-time.md)
