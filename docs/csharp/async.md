---
title: Programmation asynchrone - C#
description: Découvrez le modèle de programmation asynchrone au niveau du langage C# fourni par .NET Core.
author: cartermp
ms.date: 05/20/2020
ms.technology: csharp-async
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.openlocfilehash: b5643dd7eddefebc9cbf922ff5cce75d72dee4dd
ms.sourcegitcommit: 4ad2f8920251f3744240c3b42a443ffbe0a46577
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/08/2020
ms.locfileid: "86100897"
---
# <a name="asynchronous-programming"></a><span data-ttu-id="dd2f1-103">Programmation asynchrone</span><span class="sxs-lookup"><span data-stu-id="dd2f1-103">Asynchronous programming</span></span>

<span data-ttu-id="dd2f1-104">Si vous avez des besoins liés aux e/s (par exemple, la demande de données à un réseau, l’accès à une base de données ou la lecture et l’écriture dans un système de fichiers), vous pouvez utiliser la programmation asynchrone.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-104">If you have any I/O-bound needs (such as requesting data from a network, accessing a database, or reading and writing to a file system), you'll want to utilize asynchronous programming.</span></span> <span data-ttu-id="dd2f1-105">L’écriture de code asynchrone est également indiquée si votre code utilise le processeur de manière intensive, notamment pour effectuer un calcul complexe.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-105">You could also have CPU-bound code, such as performing an expensive calculation, which is also a good scenario for writing async code.</span></span>

<span data-ttu-id="dd2f1-106">C# possède un modèle de programmation asynchrone au niveau du langage, qui permet d’écrire facilement du code asynchrone, sans avoir à jongler avec les rappels ni à se conformer à une bibliothèque qui prend en charge l’asynchronie.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-106">C# has a language-level asynchronous programming model, which allows for easily writing asynchronous code, without having to juggle callbacks or conform to a library that supports asynchrony.</span></span> <span data-ttu-id="dd2f1-107">Il suit ce que l’on appelle le [modèle asynchrone basé sur des tâches (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="dd2f1-107">It follows what is known as the [Task-based Asynchronous Pattern (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span></span>

## <a name="overview-of-the-asynchronous-model"></a><span data-ttu-id="dd2f1-108">Vue d’ensemble du modèle asynchrone</span><span class="sxs-lookup"><span data-stu-id="dd2f1-108">Overview of the asynchronous model</span></span>

<span data-ttu-id="dd2f1-109">La programmation asynchrone est basée sur les objets `Task` et `Task<T>`, qui modélisent les opérations asynchrones.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-109">The core of async programming is the `Task` and `Task<T>` objects, which model asynchronous operations.</span></span> <span data-ttu-id="dd2f1-110">Ces objets sont exposés à l’aide des mots clés `async` et `await`.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-110">They are supported by the `async` and `await` keywords.</span></span> <span data-ttu-id="dd2f1-111">Dans la plupart des cas, le modèle est assez simple :</span><span class="sxs-lookup"><span data-stu-id="dd2f1-111">The model is fairly simple in most cases:</span></span>

- <span data-ttu-id="dd2f1-112">Pour le code lié aux e/s, vous attendez une opération qui retourne un `Task` ou `Task<T>` à l’intérieur d’une `async` méthode.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-112">For I/O-bound code, you await an operation that returns a `Task` or `Task<T>` inside of an `async` method.</span></span>
- <span data-ttu-id="dd2f1-113">Pour le code lié au processeur, vous attendez une opération démarrée sur un thread d’arrière-plan avec la <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-113">For CPU-bound code, you await an operation that is started on a background thread with the <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="dd2f1-114">Le mot clé `await` trouve ici toute son utilité.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-114">The `await` keyword is where the magic happens.</span></span> <span data-ttu-id="dd2f1-115">Il cède le contrôle à l’appelant de la méthode qui a effectué l’opération `await`. Au final, c’est ce qui rend une interface utilisateur réactive ou un service élastique.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-115">It yields control to the caller of the method that performed `await`, and it ultimately allows a UI to be responsive or a service to be elastic.</span></span> <span data-ttu-id="dd2f1-116">Bien qu' [il existe des façons](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) d’aborder du code asynchrone autre que `async` et `await` , cet article se concentre sur les constructions de niveau de langage.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-116">While [there are ways](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) to approach async code other than `async` and `await`, this article focuses on the language-level constructs.</span></span>

### <a name="io-bound-example-download-data-from-a-web-service"></a><span data-ttu-id="dd2f1-117">Exemple de liaison d’e/s : Télécharger des données à partir d’un service Web</span><span class="sxs-lookup"><span data-stu-id="dd2f1-117">I/O-bound example: Download data from a web service</span></span>

<span data-ttu-id="dd2f1-118">Vous devrez peut-être télécharger des données à partir d’un service Web lorsque vous appuyez sur un bouton, mais ne souhaitez pas bloquer le thread d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-118">You may need to download some data from a web service when a button is pressed, but don't want to block the UI thread.</span></span> <span data-ttu-id="dd2f1-119">Il peut être accompli de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="dd2f1-119">It can be accomplished like this:</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

downloadButton.Clicked += async (o, e) =>
{
    // This line will yield control to the UI as the request
    // from the web service is happening.
    //
    // The UI thread is now free to perform other work.
    var stringData = await _httpClient.GetStringAsync(URL);
    DoSomethingWithData(stringData);
};
```

<span data-ttu-id="dd2f1-120">Le code exprime l’intention (en téléchargeant les données de façon asynchrone) sans être coincés dans l’interaction avec les `Task` objets.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-120">The code expresses the intent (downloading data asynchronously) without getting bogged down in interacting with `Task` objects.</span></span>

### <a name="cpu-bound-example-perform-a-calculation-for-a-game"></a><span data-ttu-id="dd2f1-121">Exemple de processeur dépendant : effectuer un calcul pour un jeu</span><span class="sxs-lookup"><span data-stu-id="dd2f1-121">CPU-bound example: Perform a calculation for a game</span></span>

<span data-ttu-id="dd2f1-122">Supposons que vous développez un jeu pour mobile dans lequel l’appui sur un bouton peut causer des dommages à de nombreux ennemis à l’écran.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-122">Say you're writing a mobile game where pressing a button can inflict damage on many enemies on the screen.</span></span> <span data-ttu-id="dd2f1-123">Le calcul des dommages infligés peut nécessiter beaucoup de ressources. Si ce calcul est effectué sur le thread d’interface utilisateur, le jeu risque d’être considérablement ralenti pendant la durée du calcul.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-123">Performing the damage calculation can be expensive, and doing it on the UI thread would make the game appear to pause as the calculation is performed!</span></span>

<span data-ttu-id="dd2f1-124">La meilleure façon de gérer cela est de démarrer un thread d’arrière-plan, qui effectue le travail à l’aide de `Task.Run` , et d’attendre son résultat à l’aide de `await` .</span><span class="sxs-lookup"><span data-stu-id="dd2f1-124">The best way to handle this is to start a background thread, which does the work using `Task.Run`, and await its result using `await`.</span></span> <span data-ttu-id="dd2f1-125">Cela permet à l’interface utilisateur de paraître lisse au fur et à mesure que le travail est effectué.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-125">This allows the UI to feel smooth as the work is being done.</span></span>

```csharp
private DamageResult CalculateDamageDone()
{
    // Code omitted:
    //
    // Does an expensive calculation and returns
    // the result of that calculation.
}

calculateButton.Clicked += async (o, e) =>
{
    // This line will yield control to the UI while CalculateDamageDone()
    // performs its work. The UI thread is free to perform other work.
    var damageResult = await Task.Run(() => CalculateDamageDone());
    DisplayDamage(damageResult);
};
```

<span data-ttu-id="dd2f1-126">Ce code exprime clairement l’intention de l’événement de clic du bouton. Il ne nécessite pas de gérer un thread d’arrière-plan manuellement et il effectue le travail de façon non bloquante.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-126">This code cleanly expresses the intent of the button's click event, it doesn't require managing a background thread manually, and it does so in a non-blocking way.</span></span>

### <a name="what-happens-under-the-covers"></a><span data-ttu-id="dd2f1-127">Les dessous du code</span><span class="sxs-lookup"><span data-stu-id="dd2f1-127">What happens under the covers</span></span>

<span data-ttu-id="dd2f1-128">Il y a de nombreux éléments mobiles dans lesquels des opérations asynchrones sont concernées.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-128">There are many moving pieces where asynchronous operations are concerned.</span></span> <span data-ttu-id="dd2f1-129">Si vous êtes curieux de savoir ce qui se passe sous les couvertures de `Task` et `Task<T>` , consultez l’article [Async in-Depth](../standard/async-in-depth.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-129">If you're curious about what's happening underneath the covers of `Task` and `Task<T>`, see the [Async in-depth](../standard/async-in-depth.md) article for more information.</span></span>

<span data-ttu-id="dd2f1-130">Du côté du C#, le compilateur transforme votre code en une machine à États qui effectue le suivi d’opérations telles que le traitement de l’exécution quand un `await` est atteint et la reprise de l’exécution lorsqu’une tâche en arrière-plan est terminée.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-130">On the C# side of things, the compiler transforms your code into a state machine that keeps track of things like yielding execution when an `await` is reached and resuming execution when a background job has finished.</span></span>

<span data-ttu-id="dd2f1-131">D’un point de vue théorique, il s’agit d’une implémentation du [modèle de promesses d’asynchronisme](https://en.wikipedia.org/wiki/Futures_and_promises).</span><span class="sxs-lookup"><span data-stu-id="dd2f1-131">For the theoretically-inclined, this is an implementation of the [Promise Model of asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises).</span></span>

## <a name="key-pieces-to-understand"></a><span data-ttu-id="dd2f1-132">Éléments clés à comprendre</span><span class="sxs-lookup"><span data-stu-id="dd2f1-132">Key pieces to understand</span></span>

* <span data-ttu-id="dd2f1-133">Le code asynchrone peut être utilisé pour du code utilisant les E/S ou le processeur de manière intensive, mais il est utilisé de manière différente dans chaque scénario.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-133">Async code can be used for both I/O-bound and CPU-bound code, but differently for each scenario.</span></span>
* <span data-ttu-id="dd2f1-134">Le code asynchrone utilise les objets `Task<T>` et `Task`, qui sont des constructions servant à modéliser le travail effectué en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-134">Async code uses `Task<T>` and `Task`, which are constructs used to model work being done in the background.</span></span>
* <span data-ttu-id="dd2f1-135">Le mot clé `async` définit une méthode comme asynchrone, ce qui vous permet d’utiliser le mot clé `await` dans le corps de la méthode.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-135">The `async` keyword turns a method into an async method, which allows you to use the `await` keyword in its body.</span></span>
* <span data-ttu-id="dd2f1-136">Quand le mot clé `await` est utilisé, il suspend la méthode d’appel et cède le contrôle à son appelant jusqu’à ce que la tâche awaited soit terminée.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-136">When the `await` keyword is applied, it suspends the calling method and yields control back to its caller until the awaited task is complete.</span></span>
* <span data-ttu-id="dd2f1-137">Le mot clé `await` peut uniquement être utilisé dans une méthode asynchrone.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-137">`await` can only be used inside an async method.</span></span>

## <a name="recognize-cpu-bound-and-io-bound-work"></a><span data-ttu-id="dd2f1-138">Reconnaître le travail lié au processeur et à l’e/s</span><span class="sxs-lookup"><span data-stu-id="dd2f1-138">Recognize CPU-bound and I/O-bound work</span></span>

<span data-ttu-id="dd2f1-139">Les deux premiers exemples de ce guide vous ont montré comment utiliser `async` et `await` pour un travail utilisant les E/S et le processeur de manière intensive.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-139">The first two examples of this guide showed how you can use `async` and `await` for I/O-bound and CPU-bound work.</span></span> <span data-ttu-id="dd2f1-140">Il est primordial de savoir déterminer si un travail à effectuer utilise les E/S ou le processeur de manière intensive, car ce point peut avoir un impact important sur les performances de votre code et entraîner une utilisation incorrecte de certaines constructions.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-140">It's key that you can identify when a job you need to do is I/O-bound or CPU-bound, because it can greatly affect the performance of your code and could potentially lead to misusing certain constructs.</span></span>

<span data-ttu-id="dd2f1-141">Voici deux questions à vous poser avant d’écrire du code :</span><span class="sxs-lookup"><span data-stu-id="dd2f1-141">Here are two questions you should ask before you write any code:</span></span>

1. <span data-ttu-id="dd2f1-142">Votre code doit-il « attendre » quelque chose, par exemple des données d’une base de données ?</span><span class="sxs-lookup"><span data-stu-id="dd2f1-142">Will your code be "waiting" for something, such as data from a database?</span></span>

   <span data-ttu-id="dd2f1-143">Si la réponse est « oui », le travail **utilise les E/S de manière intensive**.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-143">If your answer is "yes", then your work is **I/O-bound**.</span></span>

1. <span data-ttu-id="dd2f1-144">Votre code effectuera-t-il un calcul coûteux ?</span><span class="sxs-lookup"><span data-stu-id="dd2f1-144">Will your code be performing an expensive computation?</span></span>

   <span data-ttu-id="dd2f1-145">Si la réponse est « oui », le travail **utilise le processeur de manière intensive**.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-145">If you answered "yes", then your work is **CPU-bound**.</span></span>

<span data-ttu-id="dd2f1-146">Si le travail à faire **utilise les E/S de manière intensive**, utilisez `async` et `await` *sans* `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-146">If the work you have is **I/O-bound**, use `async` and `await` *without* `Task.Run`.</span></span> <span data-ttu-id="dd2f1-147">Vous *ne devez pas* utiliser la bibliothèque parallèle de tâches.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-147">You *should not* use the Task Parallel Library.</span></span> <span data-ttu-id="dd2f1-148">Cette raison est décrite en détail dans [Async](../standard/async-in-depth.md).</span><span class="sxs-lookup"><span data-stu-id="dd2f1-148">The reason for this is outlined in [Async in Depth](../standard/async-in-depth.md).</span></span>

<span data-ttu-id="dd2f1-149">Si le travail que vous avez est lié à l' **UC** et que vous vous souciez de la réactivité, utilisez `async` et `await` , mais générez le travail sur un autre thread *avec* `Task.Run` .</span><span class="sxs-lookup"><span data-stu-id="dd2f1-149">If the work you have is **CPU-bound** and you care about responsiveness, use `async` and `await`, but spawn off the work on another thread *with* `Task.Run`.</span></span> <span data-ttu-id="dd2f1-150">Si le travail est approprié pour la concurrence et le parallélisme, envisagez également d’utiliser la [bibliothèque parallèle de tâches](../standard/parallel-programming/task-parallel-library-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="dd2f1-150">If the work is appropriate for concurrency and parallelism, also consider using the [Task Parallel Library](../standard/parallel-programming/task-parallel-library-tpl.md).</span></span>

<span data-ttu-id="dd2f1-151">De plus, vous devez toujours mesurer les performances d’exécution de votre code.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-151">Additionally, you should always measure the execution of your code.</span></span> <span data-ttu-id="dd2f1-152">Par exemple, vous constaterez peut-être que le coût d’un travail utilisant le processeur de manière intensive n’est pas si élevé que cela par rapport à la surcharge des changements de contexte induits par le multithreading.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-152">For example, you may find yourself in a situation where your CPU-bound work is not costly enough compared with the overhead of context switches when multithreading.</span></span> <span data-ttu-id="dd2f1-153">Chaque solution ayant ses compromis, choisissez le meilleur compromis pour votre scénario.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-153">Every choice has its tradeoff, and you should pick the correct tradeoff for your situation.</span></span>

## <a name="more-examples"></a><span data-ttu-id="dd2f1-154">Plus d'exemples</span><span class="sxs-lookup"><span data-stu-id="dd2f1-154">More examples</span></span>

<span data-ttu-id="dd2f1-155">Les exemples suivants montrent diverses façons d’écrire du code asynchrone dans C#.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-155">The following examples demonstrate various ways you can write async code in C#.</span></span> <span data-ttu-id="dd2f1-156">Ils correspondent à plusieurs scénarios différents que vous êtes susceptible de rencontrer.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-156">They cover a few different scenarios you may come across.</span></span>

### <a name="extract-data-from-a-network"></a><span data-ttu-id="dd2f1-157">Extraire des données à partir d’un réseau</span><span class="sxs-lookup"><span data-stu-id="dd2f1-157">Extract data from a network</span></span>

<span data-ttu-id="dd2f1-158">Cet extrait de code télécharge le code HTML à partir de la page d’accueil de <https://dotnetfoundation.org> et compte le nombre de fois que la chaîne « .net » se produit dans le code html.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-158">This snippet downloads the HTML from the homepage at <https://dotnetfoundation.org> and counts the number of times the string ".NET" occurs in the HTML.</span></span> <span data-ttu-id="dd2f1-159">Elle utilise ASP.NET pour définir une méthode de contrôleur d’API Web qui effectue cette tâche et retourne le nombre.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-159">It uses ASP.NET to define a Web API controller method, which performs this task and returns the number.</span></span>

> [!NOTE]
> <span data-ttu-id="dd2f1-160">Si vous prévoyez d’effectuer une analyse HTML dans le code de production, n’utilisez pas d’expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-160">If you plan on doing HTML parsing in production code, don't use regular expressions.</span></span> <span data-ttu-id="dd2f1-161">Utilisez plutôt une bibliothèque d’analyse.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-161">Use a parsing library instead.</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

[HttpGet, Route("DotNetCount")]
public async Task<int> GetDotNetCount()
{
    // Suspends GetDotNetCount() to allow the caller (the web server)
    // to accept another request, rather than blocking on this one.
    var html = await _httpClient.GetStringAsync("https://dotnetfoundation.org");

    return Regex.Matches(html, @"\.NET").Count;
}
```

<span data-ttu-id="dd2f1-162">Voici le même scénario écrit pour une application Windows universelle, qui effectue la même tâche quand l’utilisateur appuie sur un bouton :</span><span class="sxs-lookup"><span data-stu-id="dd2f1-162">Here's the same scenario written for a Universal Windows App, which performs the same task when a Button is pressed:</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

private async void OnSeeTheDotNetsButtonClick(object sender, RoutedEventArgs e)
{
    // Capture the task handle here so we can await the background task later.
    var getDotNetFoundationHtmlTask = _httpClient.GetStringAsync("https://dotnetfoundation.org");

    // Any other work on the UI thread can be done here, such as enabling a Progress Bar.
    // This is important to do here, before the "await" call, so that the user
    // sees the progress bar before execution of this method is yielded.
    NetworkProgressBar.IsEnabled = true;
    NetworkProgressBar.Visibility = Visibility.Visible;

    // The await operator suspends OnSeeTheDotNetsButtonClick(), returning control to its caller.
    // This is what allows the app to be responsive and not block the UI thread.
    var html = await getDotNetFoundationHtmlTask;
    int count = Regex.Matches(html, @"\.NET").Count;

    DotNetCountLabel.Text = $"Number of .NETs on dotnetfoundation.org: {count}";

    NetworkProgressBar.IsEnabled = false;
    NetworkProgressBar.Visibility = Visibility.Collapsed;
}
```

### <a name="wait-for-multiple-tasks-to-complete"></a><span data-ttu-id="dd2f1-163">Attendre la fin de plusieurs tâches</span><span class="sxs-lookup"><span data-stu-id="dd2f1-163">Wait for multiple tasks to complete</span></span>

<span data-ttu-id="dd2f1-164">Vous pouvez avoir un scénario qui nécessite de récupérer plusieurs éléments de données simultanément.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-164">You may find yourself in a situation where you need to retrieve multiple pieces of data concurrently.</span></span> <span data-ttu-id="dd2f1-165">L' `Task` API contient deux méthodes, <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> , qui vous permettent d’écrire du code asynchrone qui exécute une attente non bloquante sur plusieurs travaux en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-165">The `Task` API contains two methods, <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, that allow you to write asynchronous code that performs a non-blocking wait on multiple background jobs.</span></span>

<span data-ttu-id="dd2f1-166">Cet exemple vous montre comment récupérer des données `User` pour plusieurs `userId`.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-166">This example shows how you might grab `User` data for a set of `userId`s.</span></span>

```csharp
public async Task<User> GetUserAsync(int userId)
{
    // Code omitted:
    //
    // Given a user Id {userId}, retrieves a User object corresponding
    // to the entry in the database with {userId} as its Id.
}

public static async Task<IEnumerable<User>> GetUsersAsync(IEnumerable<int> userIds)
{
    var getUserTasks = new List<Task<User>>();
    foreach (int userId in userIds)
    {
        getUserTasks.Add(GetUserAsync(userId));
    }

    return await Task.WhenAll(getUserTasks);
}
```

<span data-ttu-id="dd2f1-167">Voici une autre façon de l’écrire de façon plus succincte, à l’aide de LINQ :</span><span class="sxs-lookup"><span data-stu-id="dd2f1-167">Here's another way to write this more succinctly, using LINQ:</span></span>

```csharp
public async Task<User> GetUserAsync(int userId)
{
    // Code omitted:
    //
    // Given a user Id {userId}, retrieves a User object corresponding
    // to the entry in the database with {userId} as its Id.
}

public static async Task<User[]> GetUsersAsync(IEnumerable<int> userIds)
{
    var getUserTasks = userIds.Select(id => GetUserAsync(id));
    return await Task.WhenAll(getUserTasks);
}
```

<span data-ttu-id="dd2f1-168">Si vous choisissez de combiner LINQ avec du code asynchrone, pour réduire la quantité de code, faites-le avec précaution.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-168">Although it's less code, take care when mixing LINQ with asynchronous code.</span></span> <span data-ttu-id="dd2f1-169">Du fait que LINQ utilise l’exécution différée, les appels asynchrones ne sont pas effectués immédiatement comme c’est le cas dans une boucle `foreach`, sauf si vous forcez l’itération de la séquence générée avec un appel à `.ToList()` ou `.ToArray()`.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-169">Because LINQ uses deferred (lazy) execution, async calls won't happen immediately as they do in a `foreach` loop unless you force the generated sequence to iterate with a call to `.ToList()` or `.ToArray()`.</span></span>

## <a name="important-info-and-advice"></a><span data-ttu-id="dd2f1-170">Informations et conseils importants</span><span class="sxs-lookup"><span data-stu-id="dd2f1-170">Important info and advice</span></span>

<span data-ttu-id="dd2f1-171">Avec la programmation asynchrone, il existe des détails à garder à l’esprit qui peuvent empêcher un comportement inattendu.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-171">With async programming there are some details to keep in mind which can prevent unexpected behavior.</span></span>

* <span data-ttu-id="dd2f1-172">`async` **Les méthodes doivent contenir un mot clé** `await` **dans leur corps pour pouvoir être suspendues.**</span><span class="sxs-lookup"><span data-stu-id="dd2f1-172">`async` **methods need to have an** `await` **keyword in their body or they will never yield!**</span></span>

  <span data-ttu-id="dd2f1-173">Il ne faut pas oublier ce point.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-173">This is important to keep in mind.</span></span> <span data-ttu-id="dd2f1-174">Si `await` n’est pas utilisé dans le corps d’une `async` méthode, le compilateur C# génère un avertissement, mais le code se compile et s’exécute comme s’il s’agissait d’une méthode normale.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-174">If `await` is not used in the body of an `async` method, the C# compiler generates a warning, but the code compiles and runs as if it were a normal method.</span></span> <span data-ttu-id="dd2f1-175">Cela est incroyablement inefficace, car l’ordinateur d’État généré par le compilateur C# pour la méthode Async n’accomplit rien.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-175">This is incredibly inefficient, as the state machine generated by the C# compiler for the async method is not accomplishing anything.</span></span>

* <span data-ttu-id="dd2f1-176">**Vous devez ajouter « Async » comme suffixe de chaque nom de méthode Async que vous écrivez.**</span><span class="sxs-lookup"><span data-stu-id="dd2f1-176">**You should add "Async" as the suffix of every async method name you write.**</span></span>

<span data-ttu-id="dd2f1-177">Il s’agit de la Convention utilisée dans .NET pour différencier plus facilement les méthodes synchrones et asynchrones.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-177">This is the convention used in .NET to more easily differentiate synchronous and asynchronous methods.</span></span> <span data-ttu-id="dd2f1-178">Certaines méthodes qui ne sont pas explicitement appelées par votre code (telles que les gestionnaires d’événements ou les méthodes de contrôleur Web) ne s’appliquent pas nécessairement.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-178">Certain methods that aren't explicitly called by your code (such as event handlers or web controller methods) don't necessarily apply.</span></span> <span data-ttu-id="dd2f1-179">Étant donné qu’elles ne sont pas explicitement appelées par votre code, il n’est pas aussi important d’être explicite quant à leur nom.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-179">Because they are not explicitly called by your code, being explicit about their naming isn't as important.</span></span>

* <span data-ttu-id="dd2f1-180">`async void`**doit uniquement être utilisé pour les gestionnaires d’événements.**</span><span class="sxs-lookup"><span data-stu-id="dd2f1-180">`async void` **should only to be used for event handlers.**</span></span>

<span data-ttu-id="dd2f1-181">L’utilisation de `async void` est le seul moyen de permettre le fonctionnement des gestionnaires d’événements asynchrones, car les événements n’ont pas de types de retour (et ne peuvent donc pas utiliser les objets `Task` et `Task<T>`).</span><span class="sxs-lookup"><span data-stu-id="dd2f1-181">`async void` is the only way to allow asynchronous event handlers to work because events do not have return types (thus cannot make use of `Task` and `Task<T>`).</span></span> <span data-ttu-id="dd2f1-182">Toute autre utilisation de la méthode `async void` ne suit pas le modèle TAP et peut être difficile à implémenter, comme expliqué ci-après :</span><span class="sxs-lookup"><span data-stu-id="dd2f1-182">Any other use of `async void` does not follow the TAP model and can be challenging to use, such as:</span></span>

* <span data-ttu-id="dd2f1-183">Les exceptions levées dans une `async void` méthode ne peuvent pas être interceptées en dehors de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-183">Exceptions thrown in an `async void` method can't be caught outside of that method.</span></span>
* <span data-ttu-id="dd2f1-184">`async void`les méthodes sont difficiles à tester.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-184">`async void` methods are difficult to test.</span></span>
* <span data-ttu-id="dd2f1-185">`async void`les méthodes peuvent provoquer des effets secondaires incorrects si l’appelant ne s’attend pas à ce qu’ils soient asynchrones.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-185">`async void` methods can cause bad side effects if the caller isn't expecting them to be async.</span></span>

* <span data-ttu-id="dd2f1-186">**Définissez le thread avec précaution si vous utilisez des expressions lambda asynchrones dans des expressions LINQ.**</span><span class="sxs-lookup"><span data-stu-id="dd2f1-186">**Tread carefully when using async lambdas in LINQ expressions**</span></span>

<span data-ttu-id="dd2f1-187">Les expressions lambda dans LINQ utilisent l’exécution différée, ce qui signifie que le code peut finir à s’exécuter à un moment où vous ne l’attendiez pas.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-187">Lambda expressions in LINQ use deferred execution, meaning code could end up executing at a time when you're not expecting it to.</span></span> <span data-ttu-id="dd2f1-188">L’introduction de tâches bloquantes dans ce code peut facilement provoquer un interblocage si le code n’est pas écrit correctement.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-188">The introduction of blocking tasks into this can easily result in a deadlock if not written correctly.</span></span> <span data-ttu-id="dd2f1-189">De plus, l’imbrication de code asynchrone peut rendre la logique d’exécution du code plus compliquée.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-189">Additionally, the nesting of asynchronous code like this can also make it more difficult to reason about the execution of the code.</span></span> <span data-ttu-id="dd2f1-190">Combiner du code asynchrone et du code LINQ offre beaucoup de possibilités, mais nécessite d’être fait avec précaution et de manière claire.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-190">Async and LINQ are powerful, but should be used together as carefully and clearly as possible.</span></span>

* <span data-ttu-id="dd2f1-191">**Écrivez du code qui attend certaines tâches de façon non bloquante.**</span><span class="sxs-lookup"><span data-stu-id="dd2f1-191">**Write code that awaits Tasks in a non-blocking manner**</span></span>

<span data-ttu-id="dd2f1-192">Le blocage du thread actuel comme un moyen d’attendre qu’un `Task` se termine peut entraîner des interblocages et bloquer les threads de contexte, et peut nécessiter une gestion des erreurs plus complexe.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-192">Blocking the current thread as a means to wait for a `Task` to complete can result in deadlocks and blocked context threads, and can require more complex error-handling.</span></span> <span data-ttu-id="dd2f1-193">Le tableau suivant fournit des conseils sur la façon de traiter l’attente des tâches de façon non bloquante :</span><span class="sxs-lookup"><span data-stu-id="dd2f1-193">The following table provides guidance on how to deal with waiting for tasks in a non-blocking way:</span></span>

| <span data-ttu-id="dd2f1-194">Élément à utiliser...</span><span class="sxs-lookup"><span data-stu-id="dd2f1-194">Use this...</span></span>          | <span data-ttu-id="dd2f1-195">Au lieu de...</span><span class="sxs-lookup"><span data-stu-id="dd2f1-195">Instead of this...</span></span>           | <span data-ttu-id="dd2f1-196">Lorsque vous souhaitez effectuer cette opération...</span><span class="sxs-lookup"><span data-stu-id="dd2f1-196">When wishing to do this...</span></span>                 |
|----------------------|------------------------------|--------------------------------------------|
| `await`              | <span data-ttu-id="dd2f1-197">`Task.Wait` ou `Task.Result`</span><span class="sxs-lookup"><span data-stu-id="dd2f1-197">`Task.Wait` or `Task.Result`</span></span> | <span data-ttu-id="dd2f1-198">Extraire le résultat d’une tâche en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="dd2f1-198">Retrieving the result of a background task</span></span> |
| `await Task.WhenAny` | `Task.WaitAny`               | <span data-ttu-id="dd2f1-199">Attendre la fin d’une tâche</span><span class="sxs-lookup"><span data-stu-id="dd2f1-199">Waiting for any task to complete</span></span>           |
| `await Task.WhenAll` | `Task.WaitAll`               | <span data-ttu-id="dd2f1-200">Attendre la fin de toutes les tâches</span><span class="sxs-lookup"><span data-stu-id="dd2f1-200">Waiting for all tasks to complete</span></span>          |
| `await Task.Delay`   | `Thread.Sleep`               | <span data-ttu-id="dd2f1-201">Attendre pendant une période</span><span class="sxs-lookup"><span data-stu-id="dd2f1-201">Waiting for a period of time</span></span>               |

* <span data-ttu-id="dd2f1-202">**Envisagez d’utiliser** `ValueTask` **dans** la mesure du possible</span><span class="sxs-lookup"><span data-stu-id="dd2f1-202">**Consider using** `ValueTask` **where possible**</span></span>

<span data-ttu-id="dd2f1-203">Le retour d’un objet `Task` à partir de méthodes async peut introduire des goulots d’étranglement au niveau des performances dans certains chemins.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-203">Returning a `Task` object from async methods can introduce performance bottlenecks in certain paths.</span></span> <span data-ttu-id="dd2f1-204">`Task` est un type référence. Si vous l’utilisez, vous allouez donc un objet.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-204">`Task` is a reference type, so using it means allocating an object.</span></span> <span data-ttu-id="dd2f1-205">Dans les cas où une méthode déclarée avec le `async` modificateur retourne un résultat mis en cache ou se termine de façon synchrone, les allocations supplémentaires peuvent devenir un coût de temps significatif dans les sections de code critiques pour les performances.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-205">In cases where a method declared with the `async` modifier returns a cached result or completes synchronously, the extra allocations can become a significant time cost in performance critical sections of code.</span></span> <span data-ttu-id="dd2f1-206">Cela peut devenir coûteux si ces allocations se produisent dans des boucles serrées.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-206">It can become costly if those allocations occur in tight loops.</span></span> <span data-ttu-id="dd2f1-207">Pour plus d’informations, consultez [types de retour asynchrones généralisés](whats-new/csharp-7.md#generalized-async-return-types).</span><span class="sxs-lookup"><span data-stu-id="dd2f1-207">For more information, see [generalized async return types](whats-new/csharp-7.md#generalized-async-return-types).</span></span>

* <span data-ttu-id="dd2f1-208">**Envisagez d’utiliser** `ConfigureAwait(false)`</span><span class="sxs-lookup"><span data-stu-id="dd2f1-208">**Consider using** `ConfigureAwait(false)`</span></span>

<span data-ttu-id="dd2f1-209">Une question courante est « quand dois-je utiliser la <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> méthode ? ».</span><span class="sxs-lookup"><span data-stu-id="dd2f1-209">A common question is, "when should I use the <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> method?".</span></span> <span data-ttu-id="dd2f1-210">La méthode permet à une `Task` instance de configurer son await.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-210">The method allows for a `Task` instance to configure its awaiter.</span></span> <span data-ttu-id="dd2f1-211">Il s’agit d’un élément important à prendre en compte et sa définition de manière incorrecte peut avoir une incidence sur les performances et même des blocages.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-211">This is an important consideration and setting it incorrectly could potentially have performance implications and even deadlocks.</span></span> <span data-ttu-id="dd2f1-212">Pour plus d’informations sur `ConfigureAwait` , consultez le [Forum aux questions ConfigureAwait](https://devblogs.microsoft.com/dotnet/configureawait-faq).</span><span class="sxs-lookup"><span data-stu-id="dd2f1-212">For more information on `ConfigureAwait`, see the [ConfigureAwait FAQ](https://devblogs.microsoft.com/dotnet/configureawait-faq).</span></span>

* <span data-ttu-id="dd2f1-213">**Limitez l’écriture de code avec état.**</span><span class="sxs-lookup"><span data-stu-id="dd2f1-213">**Write less stateful code**</span></span>

<span data-ttu-id="dd2f1-214">Ne dépendez pas de l’état des objets globaux ou de l’exécution de certaines méthodes.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-214">Don't depend on the state of global objects or the execution of certain methods.</span></span> <span data-ttu-id="dd2f1-215">Le code doit uniquement dépendre des valeurs de retour des méthodes.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-215">Instead, depend only on the return values of methods.</span></span> <span data-ttu-id="dd2f1-216">Pourquoi ?</span><span class="sxs-lookup"><span data-stu-id="dd2f1-216">Why?</span></span>

* <span data-ttu-id="dd2f1-217">La logique du code sera plus facile à comprendre.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-217">Code will be easier to reason about.</span></span>
* <span data-ttu-id="dd2f1-218">Le code sera plus facile à tester.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-218">Code will be easier to test.</span></span>
* <span data-ttu-id="dd2f1-219">Combiner du code asynchrone et du code synchrone est beaucoup plus simple.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-219">Mixing async and synchronous code is far simpler.</span></span>
* <span data-ttu-id="dd2f1-220">Les concurrences critiques peuvent généralement être évitées.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-220">Race conditions can typically be avoided altogether.</span></span>
* <span data-ttu-id="dd2f1-221">Rendre le code dépendant des valeurs de retour facilite la coordination du code asynchrone.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-221">Depending on return values makes coordinating async code simple.</span></span>
* <span data-ttu-id="dd2f1-222">En prime, le code fonctionne parfaitement avec l’injection de dépendances.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-222">(Bonus) it works really well with dependency injection.</span></span>

<span data-ttu-id="dd2f1-223">L’objectif recommandé est d’atteindre une [transparence référentielle](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) complète ou quasi-complète dans votre code.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-223">A recommended goal is to achieve complete or near-complete [Referential Transparency](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) in your code.</span></span> <span data-ttu-id="dd2f1-224">Votre base de code sera alors prédictible, testable et facile à gérer.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-224">Doing so will result in an extremely predictable, testable, and maintainable codebase.</span></span>

## <a name="other-resources"></a><span data-ttu-id="dd2f1-225">Autres ressources</span><span class="sxs-lookup"><span data-stu-id="dd2f1-225">Other resources</span></span>

* <span data-ttu-id="dd2f1-226">L’article [Async en détail](../standard/async-in-depth.md) fournit des informations supplémentaires sur le fonctionnement des tâches.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-226">[Async in-depth](../standard/async-in-depth.md) provides more information about how Tasks work.</span></span>
* [<span data-ttu-id="dd2f1-227">Programmation asynchrone avec Async et await (C#)</span><span class="sxs-lookup"><span data-stu-id="dd2f1-227">Asynchronous programming with async and await (C#)</span></span>](./programming-guide/concepts/async/index.md)
* <span data-ttu-id="dd2f1-228">Les vidéos [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) de Lucian Wischik sont une ressource très utile pour la programmation asynchrone.</span><span class="sxs-lookup"><span data-stu-id="dd2f1-228">Lucian Wischik's [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) are a wonderful resource for async programming</span></span>
