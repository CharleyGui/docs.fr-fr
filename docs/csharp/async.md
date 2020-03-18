---
title: Programmation asynchrone - C#
description: Découvrez le modèle de programmation asynchrone au niveau du langage C# fourni par .NET Core.
author: cartermp
ms.date: 06/20/2016
ms.technology: csharp-async
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.openlocfilehash: 38d7c856e9a536db9ef26349175ad440a49f5fe2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713951"
---
# <a name="asynchronous-programming"></a><span data-ttu-id="38731-103">Programmation asynchrone</span><span class="sxs-lookup"><span data-stu-id="38731-103">Asynchronous programming</span></span>

<span data-ttu-id="38731-104">Si vous avez besoin d’écrire du code qui utilise les E/S de manière intensive (par exemple, pour récupérer des données d’un réseau ou accéder à une base de données), optez pour la programmation asynchrone.</span><span class="sxs-lookup"><span data-stu-id="38731-104">If you have any I/O-bound needs (such as requesting data from a network or accessing a database), you'll want to utilize asynchronous programming.</span></span>  <span data-ttu-id="38731-105">L’écriture de code asynchrone est également indiquée si votre code utilise le processeur de manière intensive, notamment pour effectuer un calcul complexe.</span><span class="sxs-lookup"><span data-stu-id="38731-105">You could also have CPU-bound code, such as performing an expensive calculation, which is also a good scenario for writing async code.</span></span>

<span data-ttu-id="38731-106">C# fournit un modèle de programmation asynchrone de niveau de langage. Ce modèle facilite l’écriture de code asynchrone, en vous évitant d’effectuer des rappels multiples ou de vous conformer à une bibliothèque qui prend en charge l’asynchronisme.</span><span class="sxs-lookup"><span data-stu-id="38731-106">C# has a language-level asynchronous programming model which allows for easily writing asynchronous code without having to juggle callbacks or conform to a library which supports asynchrony.</span></span> <span data-ttu-id="38731-107">Il suit ce que l’on appelle le [modèle asynchrone basé sur des tâches (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="38731-107">It follows what is known as the [Task-based Asynchronous Pattern (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span></span>

## <a name="basic-overview-of-the-asynchronous-model"></a><span data-ttu-id="38731-108">Vue d’ensemble du modèle asynchrone</span><span class="sxs-lookup"><span data-stu-id="38731-108">Basic Overview of the Asynchronous Model</span></span>

<span data-ttu-id="38731-109">La programmation asynchrone est basée sur les objets `Task` et `Task<T>`, qui modélisent les opérations asynchrones.</span><span class="sxs-lookup"><span data-stu-id="38731-109">The core of async programming is the `Task` and `Task<T>` objects, which model asynchronous operations.</span></span>  <span data-ttu-id="38731-110">Ces objets sont exposés à l’aide des mots clés `async` et `await`.</span><span class="sxs-lookup"><span data-stu-id="38731-110">They are supported by the `async` and `await` keywords.</span></span>  <span data-ttu-id="38731-111">Dans la plupart des cas, le modèle est assez simple :</span><span class="sxs-lookup"><span data-stu-id="38731-111">The model is fairly simple in most cases:</span></span>

<span data-ttu-id="38731-112">Pour du code utilisant les E/S de manière intensive, vous spécifiez une opération `await` qui retourne un objet `Task` ou `Task<T>` dans une méthode `async`.</span><span class="sxs-lookup"><span data-stu-id="38731-112">For I/O-bound code, you `await` an operation which returns a `Task` or `Task<T>` inside of an `async` method.</span></span>

<span data-ttu-id="38731-113">Pour du code utilisant le processeur de manière intensive, vous spécifiez une opération `await` qui est démarrée sur un thread d’arrière-plan avec la méthode `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="38731-113">For CPU-bound code, you `await` an operation which is started on a background thread with the `Task.Run` method.</span></span>

<span data-ttu-id="38731-114">Le mot clé `await` trouve ici toute son utilité.</span><span class="sxs-lookup"><span data-stu-id="38731-114">The `await` keyword is where the magic happens.</span></span> <span data-ttu-id="38731-115">Il cède le contrôle à l’appelant de la méthode qui a effectué l’opération `await`. Au final, c’est ce qui rend une interface utilisateur réactive ou un service élastique.</span><span class="sxs-lookup"><span data-stu-id="38731-115">It yields control to the caller of the method that performed `await`, and it ultimately allows a UI to be responsive or a service to be elastic.</span></span>

<span data-ttu-id="38731-116">Il y a d’autres approches du code asynchrone que les approches `async` et `await` décrites dans l’article sur le modèle TAP mentionné ci-dessus, mais la suite de ce document traite en particulier des constructions de niveau de langage.</span><span class="sxs-lookup"><span data-stu-id="38731-116">There are other ways to approach async code than `async` and `await` outlined in the TAP article linked above, but this document will focus on the language-level constructs from this point forward.</span></span>

### <a name="io-bound-example-downloading-data-from-a-web-service"></a><span data-ttu-id="38731-117">Exemple de code utilisant les E/S de manière intensive : télécharger des données d’un service web</span><span class="sxs-lookup"><span data-stu-id="38731-117">I/O-Bound Example: Downloading data from a web service</span></span>

<span data-ttu-id="38731-118">Imaginons que vous souhaitez écrire du code qui télécharge des données d’un service web quand un utilisateur appuie sur un bouton, mais qui ne bloque pas le thread d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="38731-118">You may need to download some data from a web service when a button is pressed, but don’t want to block the UI thread.</span></span> <span data-ttu-id="38731-119">Il vous suffit d’écrire ce code :</span><span class="sxs-lookup"><span data-stu-id="38731-119">It can be accomplished simply like this:</span></span>

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

<span data-ttu-id="38731-120">Vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="38731-120">And that’s it!</span></span> <span data-ttu-id="38731-121">Le code exprime l’intention (télécharger des données de façon asynchrone) sans que cela nécessite des interactions compliquées avec les objets Task.</span><span class="sxs-lookup"><span data-stu-id="38731-121">The code expresses the intent (downloading some data asynchronously) without getting bogged down in interacting with Task objects.</span></span>

### <a name="cpu-bound-example-performing-a-calculation-for-a-game"></a><span data-ttu-id="38731-122">Exemple de code utilisant le processeur de manière intensive : effectuer un calcul dans un jeu</span><span class="sxs-lookup"><span data-stu-id="38731-122">CPU-bound Example: Performing a Calculation for a Game</span></span>

<span data-ttu-id="38731-123">Supposons que vous développez un jeu pour mobile dans lequel l’appui sur un bouton peut causer des dommages à de nombreux ennemis à l’écran.</span><span class="sxs-lookup"><span data-stu-id="38731-123">Say you're writing a mobile game where pressing a button can inflict damage on many enemies on the screen.</span></span>  <span data-ttu-id="38731-124">Le calcul des dommages infligés peut nécessiter beaucoup de ressources. Si ce calcul est effectué sur le thread d’interface utilisateur, le jeu risque d’être considérablement ralenti pendant la durée du calcul.</span><span class="sxs-lookup"><span data-stu-id="38731-124">Performing the damage calculation can be expensive, and doing it on the UI thread would make the game appear to pause as the calculation is performed!</span></span>

<span data-ttu-id="38731-125">La meilleure façon de gérer cette situation est de démarrer un thread d’arrière-plan qui effectue le travail à l’aide de `Task.Run`, et retourne le résultat `await`.</span><span class="sxs-lookup"><span data-stu-id="38731-125">The best way to handle this is to start a background thread which does the work using `Task.Run`, and `await` its result.</span></span>  <span data-ttu-id="38731-126">Ainsi, l’interface utilisateur conserve les mêmes performances pendant le calcul.</span><span class="sxs-lookup"><span data-stu-id="38731-126">This will allow the UI to feel smooth as the work is being done.</span></span>

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
    // performs its work.  The UI thread is free to perform other work.
    var damageResult = await Task.Run(() => CalculateDamageDone());
    DisplayDamage(damageResult);
};
```

<span data-ttu-id="38731-127">Et le tour est joué !</span><span class="sxs-lookup"><span data-stu-id="38731-127">And that's it!</span></span>  <span data-ttu-id="38731-128">Ce code exprime clairement l’intention de l’événement de clic du bouton. Il ne nécessite pas de gérer un thread d’arrière-plan manuellement et il effectue le travail de façon non bloquante.</span><span class="sxs-lookup"><span data-stu-id="38731-128">This code cleanly expresses the intent of the button's click event, it doesn't require managing a background thread manually, and it does so in a non-blocking way.</span></span>

### <a name="what-happens-under-the-covers"></a><span data-ttu-id="38731-129">Les dessous du code</span><span class="sxs-lookup"><span data-stu-id="38731-129">What happens under the covers</span></span>

<span data-ttu-id="38731-130">Il y a de nombreux éléments variables en ce qui concerne les opérations asynchrones.</span><span class="sxs-lookup"><span data-stu-id="38731-130">There's a lot of moving pieces where asynchronous operations are concerned.</span></span>  <span data-ttu-id="38731-131">Si vous souhaitez connaître tous les dessous des objets `Task` et `Task<T>`, consultez l’article [Async en détail](../standard/async-in-depth.md).</span><span class="sxs-lookup"><span data-stu-id="38731-131">If you're curious about what's happening underneath the covers of `Task` and `Task<T>`, checkout the [Async in-depth](../standard/async-in-depth.md) article for more information.</span></span>

<span data-ttu-id="38731-132">Sur le plan du langage C#, le compilateur transforme votre code en une machine à états qui effectue le suivi des événements, tels que la suspension de l’exécution en présence d’un `await` et la reprise de l’exécution à la fin d’un travail en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="38731-132">On the C# side of things, the compiler transforms your code into a state machine which keeps track of things like yielding execution when an `await` is reached and resuming execution when a background job has finished.</span></span>

<span data-ttu-id="38731-133">D’un point de vue théorique, il s’agit d’une implémentation du [modèle de promesses d’asynchronisme](https://en.wikipedia.org/wiki/Futures_and_promises).</span><span class="sxs-lookup"><span data-stu-id="38731-133">For the theoretically-inclined, this is an implementation of the [Promise Model of asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises).</span></span>

## <a name="key-pieces-to-understand"></a><span data-ttu-id="38731-134">Points clés à comprendre</span><span class="sxs-lookup"><span data-stu-id="38731-134">Key Pieces to Understand</span></span>

* <span data-ttu-id="38731-135">Le code asynchrone peut être utilisé pour du code utilisant les E/S ou le processeur de manière intensive, mais il est utilisé de manière différente dans chaque scénario.</span><span class="sxs-lookup"><span data-stu-id="38731-135">Async code can be used for both I/O-bound and CPU-bound code, but differently for each scenario.</span></span>
* <span data-ttu-id="38731-136">Le code asynchrone utilise les objets `Task<T>` et `Task`, qui sont des constructions servant à modéliser le travail effectué en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="38731-136">Async code uses `Task<T>` and `Task`, which are constructs used to model work being done in the background.</span></span>
* <span data-ttu-id="38731-137">Le mot clé `async` définit une méthode comme asynchrone, ce qui vous permet d’utiliser le mot clé `await` dans le corps de la méthode.</span><span class="sxs-lookup"><span data-stu-id="38731-137">The `async` keyword turns a method into an async method, which allows you to use the `await` keyword in its body.</span></span>
* <span data-ttu-id="38731-138">Quand le mot clé `await` est utilisé, il suspend la méthode d’appel et cède le contrôle à son appelant jusqu’à ce que la tâche awaited soit terminée.</span><span class="sxs-lookup"><span data-stu-id="38731-138">When the `await` keyword is applied, it suspends the calling method and yields control back to its caller until the awaited task is complete.</span></span>
* <span data-ttu-id="38731-139">Le mot clé `await` peut uniquement être utilisé dans une méthode asynchrone.</span><span class="sxs-lookup"><span data-stu-id="38731-139">`await` can only be used inside an async method.</span></span>

## <a name="recognize-cpu-bound-and-io-bound-work"></a><span data-ttu-id="38731-140">Déterminer si un travail utilise le processeur ou les E/S de manière intensive</span><span class="sxs-lookup"><span data-stu-id="38731-140">Recognize CPU-Bound and I/O-Bound Work</span></span>

<span data-ttu-id="38731-141">Les deux premiers exemples de ce guide vous ont montré comment utiliser `async` et `await` pour un travail utilisant les E/S et le processeur de manière intensive.</span><span class="sxs-lookup"><span data-stu-id="38731-141">The first two examples of this guide showed how you can use `async` and `await` for I/O-bound and CPU-bound work.</span></span>  <span data-ttu-id="38731-142">Il est primordial de savoir déterminer si un travail à effectuer utilise les E/S ou le processeur de manière intensive, car ce point peut avoir un impact important sur les performances de votre code et entraîner une utilisation incorrecte de certaines constructions.</span><span class="sxs-lookup"><span data-stu-id="38731-142">It's key that you can identify when a job you need to do is I/O-bound or CPU-bound, because it can greatly affect the performance of your code and could potentially lead to misusing certain constructs.</span></span>

<span data-ttu-id="38731-143">Voici deux questions à vous poser avant d’écrire du code :</span><span class="sxs-lookup"><span data-stu-id="38731-143">Here are two questions you should ask before you write any code:</span></span>

1. <span data-ttu-id="38731-144">Votre code doit-il « attendre » quelque chose, par exemple des données d’une base de données ?</span><span class="sxs-lookup"><span data-stu-id="38731-144">Will your code be "waiting" for something, such as data from a database?</span></span>

    <span data-ttu-id="38731-145">Si la réponse est « oui », le travail **utilise les E/S de manière intensive**.</span><span class="sxs-lookup"><span data-stu-id="38731-145">If your answer is "yes", then your work is **I/O-bound**.</span></span>

2. <span data-ttu-id="38731-146">Le code doit-il effectuer un calcul très complexe ?</span><span class="sxs-lookup"><span data-stu-id="38731-146">Will your code be performing a very expensive computation?</span></span>

    <span data-ttu-id="38731-147">Si la réponse est « oui », le travail **utilise le processeur de manière intensive**.</span><span class="sxs-lookup"><span data-stu-id="38731-147">If you answered "yes", then your work is **CPU-bound**.</span></span>

<span data-ttu-id="38731-148">Si le travail à faire **utilise les E/S de manière intensive**, utilisez `async` et `await` *sans* `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="38731-148">If the work you have is **I/O-bound**, use `async` and `await` *without* `Task.Run`.</span></span>  <span data-ttu-id="38731-149">Vous *ne devez pas* utiliser la bibliothèque parallèle de tâches.</span><span class="sxs-lookup"><span data-stu-id="38731-149">You *should not* use the Task Parallel Library.</span></span>  <span data-ttu-id="38731-150">La raison à cela est expliquée dans l’article [Async en détail](../standard/async-in-depth.md).</span><span class="sxs-lookup"><span data-stu-id="38731-150">The reason for this is outlined in the [Async in Depth article](../standard/async-in-depth.md).</span></span>

<span data-ttu-id="38731-151">Si le travail à faire **utilise le processeur de manière intensive** et que la réactivité est une exigence, utilisez `async` et `await`, mais transférez le travail sur un autre thread *avec* `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="38731-151">If the work you have is **CPU-bound** and you care about responsiveness, use `async` and `await` but spawn the work off on another thread *with* `Task.Run`.</span></span>  <span data-ttu-id="38731-152">S’il accepte la concurrence et le parallélisme, vous pouvez également utiliser la [bibliothèque parallèle de tâches](../standard/parallel-programming/task-parallel-library-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="38731-152">If the work is appropriate for concurrency and parallelism, you should also consider using the [Task Parallel Library](../standard/parallel-programming/task-parallel-library-tpl.md).</span></span>

<span data-ttu-id="38731-153">De plus, vous devez toujours mesurer les performances d’exécution de votre code.</span><span class="sxs-lookup"><span data-stu-id="38731-153">Additionally, you should always measure the execution of your code.</span></span>  <span data-ttu-id="38731-154">Par exemple, vous constaterez peut-être que le coût d’un travail utilisant le processeur de manière intensive n’est pas si élevé que cela par rapport à la surcharge des changements de contexte induits par le multithreading.</span><span class="sxs-lookup"><span data-stu-id="38731-154">For example, you may find yourself in a situation where your CPU-bound work is not costly enough compared with the overhead of context switches when multithreading.</span></span>  <span data-ttu-id="38731-155">Chaque solution ayant ses compromis, choisissez le meilleur compromis pour votre scénario.</span><span class="sxs-lookup"><span data-stu-id="38731-155">Every choice has its tradeoff, and you should pick the correct tradeoff for your situation.</span></span>

## <a name="more-examples"></a><span data-ttu-id="38731-156">Plus d'exemples</span><span class="sxs-lookup"><span data-stu-id="38731-156">More Examples</span></span>

<span data-ttu-id="38731-157">Les exemples suivants montrent diverses façons d’écrire du code asynchrone dans C#.</span><span class="sxs-lookup"><span data-stu-id="38731-157">The following examples demonstrate various ways you can write async code in C#.</span></span>  <span data-ttu-id="38731-158">Ils correspondent à plusieurs scénarios différents que vous êtes susceptible de rencontrer.</span><span class="sxs-lookup"><span data-stu-id="38731-158">They cover a few different scenarios you may come across.</span></span>

### <a name="extracting-data-from-a-network"></a><span data-ttu-id="38731-159">Extraire des données d’un réseau</span><span class="sxs-lookup"><span data-stu-id="38731-159">Extracting Data from a Network</span></span>

<span data-ttu-id="38731-160">Cet extrait de code télécharge le code HTML à partir de la page d’accueil du site [www.dotnetfoundation.org](https://www.dotnetfoundation.org) et compte le nombre d’occurrences de la chaîne « .NET » dans le code HTML.</span><span class="sxs-lookup"><span data-stu-id="38731-160">This snippet downloads the HTML from the homepage at [www.dotnetfoundation.org](https://www.dotnetfoundation.org) and counts the number of times the string ".NET" occurs in the HTML.</span></span>  <span data-ttu-id="38731-161">Il utilise ASP.NET MVC pour définir une méthode de contrôleur web qui exécute cette tâche et retourne le nombre.</span><span class="sxs-lookup"><span data-stu-id="38731-161">It uses ASP.NET MVC to define a web controller method which performs this task, returning the number.</span></span>

> [!NOTE]
> <span data-ttu-id="38731-162">Si vous prévoyez d’effectuer une analyse HTML dans le code de production, n’utilisez pas d’expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="38731-162">If you plan on doing HTML parsing in production code, don't use regular expressions.</span></span> <span data-ttu-id="38731-163">Utilisez plutôt une bibliothèque d’analyse.</span><span class="sxs-lookup"><span data-stu-id="38731-163">Use a parsing library instead.</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

[HttpGet]
[Route("DotNetCount")]
public async Task<int> GetDotNetCountAsync()
{
    // Suspends GetDotNetCountAsync() to allow the caller (the web server)
    // to accept another request, rather than blocking on this one.
    var html = await _httpClient.GetStringAsync("https://dotnetfoundation.org");

    return Regex.Matches(html, @"\.NET").Count;
}
```

<span data-ttu-id="38731-164">Voici le même scénario écrit pour une application Windows universelle, qui effectue la même tâche quand l’utilisateur appuie sur un bouton :</span><span class="sxs-lookup"><span data-stu-id="38731-164">Here's the same scenario written for a Universal Windows App, which performs the same task when a Button is pressed:</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

private async void SeeTheDotNets_Click(object sender, RoutedEventArgs e)
{
    // Capture the task handle here so we can await the background task later.
    var getDotNetFoundationHtmlTask = _httpClient.GetStringAsync("https://www.dotnetfoundation.org");

    // Any other work on the UI thread can be done here, such as enabling a Progress Bar.
    // This is important to do here, before the "await" call, so that the user
    // sees the progress bar before execution of this method is yielded.
    NetworkProgressBar.IsEnabled = true;
    NetworkProgressBar.Visibility = Visibility.Visible;

    // The await operator suspends SeeTheDotNets_Click, returning control to its caller.
    // This is what allows the app to be responsive and not block the UI thread.
    var html = await getDotNetFoundationHtmlTask;
    int count = Regex.Matches(html, @"\.NET").Count;

    DotNetCountLabel.Text = $"Number of .NETs on dotnetfoundation.org: {count}";

    NetworkProgressBar.IsEnabled = false;
    NetworkProgressBar.Visibility = Visibility.Collapsed;
}
```

### <a name="waiting-for-multiple-tasks-to-complete"></a><span data-ttu-id="38731-165">Attendre la fin de plusieurs tâches</span><span class="sxs-lookup"><span data-stu-id="38731-165">Waiting for Multiple Tasks to Complete</span></span>

<span data-ttu-id="38731-166">Vous pouvez avoir un scénario qui nécessite de récupérer plusieurs éléments de données simultanément.</span><span class="sxs-lookup"><span data-stu-id="38731-166">You may find yourself in a situation where you need to retrieve multiple pieces of data concurrently.</span></span>  <span data-ttu-id="38731-167">L’API `Task` fournit deux méthodes, `Task.WhenAll` et `Task.WhenAny`, que vous pouvez utiliser pour écrire du code asynchrone qui spécifie une attente non bloquante sur plusieurs travaux en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="38731-167">The `Task` API contains two methods, `Task.WhenAll` and `Task.WhenAny` which allow you to write asynchronous code which performs a non-blocking wait on multiple background jobs.</span></span>

<span data-ttu-id="38731-168">Cet exemple vous montre comment récupérer des données `User` pour plusieurs `userId`.</span><span class="sxs-lookup"><span data-stu-id="38731-168">This example shows how you might grab `User` data for a set of `userId`s.</span></span>

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

<span data-ttu-id="38731-169">Voici une façon plus succincte d’écrire ce code, en utilisant LINQ :</span><span class="sxs-lookup"><span data-stu-id="38731-169">Here's another way to write this a bit more succinctly, using LINQ:</span></span>

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

<span data-ttu-id="38731-170">Si vous choisissez de combiner LINQ avec du code asynchrone, pour réduire la quantité de code, faites-le avec précaution.</span><span class="sxs-lookup"><span data-stu-id="38731-170">Although it's less code, take care when mixing LINQ with asynchronous code.</span></span>  <span data-ttu-id="38731-171">Du fait que LINQ utilise l’exécution différée, les appels asynchrones ne sont pas effectués immédiatement comme c’est le cas dans une boucle `foreach()`, sauf si vous forcez l’itération de la séquence générée avec un appel à `.ToList()` ou `.ToArray()`.</span><span class="sxs-lookup"><span data-stu-id="38731-171">Because LINQ uses deferred (lazy) execution, async calls won't happen immediately as they do in a `foreach()` loop unless you force the generated sequence to iterate with a call to `.ToList()` or `.ToArray()`.</span></span>

## <a name="important-info-and-advice"></a><span data-ttu-id="38731-172">Informations et conseils importants</span><span class="sxs-lookup"><span data-stu-id="38731-172">Important Info and Advice</span></span>

<span data-ttu-id="38731-173">La programmation asynchrone est relativement simple, mais il y a quelques points à garder à l’esprit pour éviter un comportement inattendu du code.</span><span class="sxs-lookup"><span data-stu-id="38731-173">Although async programming is relatively straightforward, there are some details to keep in mind which can prevent unexpected behavior.</span></span>

* <span data-ttu-id="38731-174">`async` **Les méthodes doivent contenir un mot clé** `await` **dans leur corps pour pouvoir être suspendues.**</span><span class="sxs-lookup"><span data-stu-id="38731-174">`async` **methods need to have an** `await` **keyword in their body or they will never yield!**</span></span>

<span data-ttu-id="38731-175">Il ne faut pas oublier ce point.</span><span class="sxs-lookup"><span data-stu-id="38731-175">This is important to keep in mind.</span></span>  <span data-ttu-id="38731-176">Si `await` n’est pas utilisé dans le corps d’une méthode `async`, le compilateur C# génère un avertissement, mais le code est compilé et exécuté comme s’il s’agissait d’une méthode standard.</span><span class="sxs-lookup"><span data-stu-id="38731-176">If `await` is not used in the body of an `async` method, the C# compiler will generate a warning, but the code will compile and run as if it were a normal method.</span></span>  <span data-ttu-id="38731-177">Notez également que cela n’aurait aucune utilité, car la machine à états générée par le compilateur C# pour la méthode async n’accomplirait aucune opération dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="38731-177">Note that this would also be incredibly inefficient, as the state machine generated by the C# compiler for the async method would not be accomplishing anything.</span></span>

* <span data-ttu-id="38731-178">**Vous devez ajouter "Async" comme suffixe de chaque nom de méthode async que vous écrivez.**</span><span class="sxs-lookup"><span data-stu-id="38731-178">**You should add "Async" as the suffix of every async method name you write.**</span></span>

<span data-ttu-id="38731-179">Cette convention de .NET aide à différencier les méthodes synchrones et asynchrones.</span><span class="sxs-lookup"><span data-stu-id="38731-179">This is the convention used in .NET to more-easily differentiate synchronous and asynchronous methods.</span></span> <span data-ttu-id="38731-180">Notez que cela n’est pas obligatoire pour certaines méthodes qui ne sont pas explicitement appelées par votre code (par exemple, les gestionnaires d’événements et les méthodes de contrôleur web).</span><span class="sxs-lookup"><span data-stu-id="38731-180">Note that certain methods which aren’t explicitly called by your code (such as event handlers or web controller methods) don’t necessarily apply.</span></span> <span data-ttu-id="38731-181">L’attribution d’un nom explicite pour ces méthodes a moins d’importance.</span><span class="sxs-lookup"><span data-stu-id="38731-181">Because these are not explicitly called by your code, being explicit about their naming isn’t as important.</span></span>

* <span data-ttu-id="38731-182">`async void` **ne doit être utilisé que pour les gestionnaires d’événements.**</span><span class="sxs-lookup"><span data-stu-id="38731-182">`async void` **should only be used for event handlers.**</span></span>

<span data-ttu-id="38731-183">L’utilisation de `async void` est le seul moyen de permettre le fonctionnement des gestionnaires d’événements asynchrones, car les événements n’ont pas de types de retour (et ne peuvent donc pas utiliser les objets `Task` et `Task<T>`).</span><span class="sxs-lookup"><span data-stu-id="38731-183">`async void` is the only way to allow asynchronous event handlers to work because events do not have return types (thus cannot make use of `Task` and `Task<T>`).</span></span> <span data-ttu-id="38731-184">Toute autre utilisation de la méthode `async void` ne suit pas le modèle TAP et peut être difficile à implémenter, comme expliqué ci-après :</span><span class="sxs-lookup"><span data-stu-id="38731-184">Any other use of `async void` does not follow the TAP model and can be challenging to use, such as:</span></span>

* <span data-ttu-id="38731-185">Les exceptions levées dans une méthode `async void` ne peuvent pas être interceptées en dehors de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="38731-185">Exceptions thrown in an `async void` method can’t be caught outside of that method.</span></span>
* <span data-ttu-id="38731-186">Les méthodes `async void` sont très difficiles à tester.</span><span class="sxs-lookup"><span data-stu-id="38731-186">`async void` methods are very difficult to test.</span></span>
* <span data-ttu-id="38731-187">Les méthodes `async void` peuvent avoir des effets secondaires gênants si l’appelant n’attend pas de méthodes asynchrones.</span><span class="sxs-lookup"><span data-stu-id="38731-187">`async void` methods can cause bad side effects if the caller isn’t expecting them to be async.</span></span>

* <span data-ttu-id="38731-188">**Définissez le thread avec précaution si vous utilisez des expressions lambda asynchrones dans des expressions LINQ.**</span><span class="sxs-lookup"><span data-stu-id="38731-188">**Tread carefully when using async lambdas in LINQ expressions**</span></span>

<span data-ttu-id="38731-189">Dans LINQ, les expressions lambda utilisent l’exécution différée, ce qui signifie que l’exécution du code peut s’arrêter à un point que vous n’aviez pas prévu.</span><span class="sxs-lookup"><span data-stu-id="38731-189">Lambda expressions in LINQ use deferred execution, meaning code could end up executing at a time when you’re not expecting it to.</span></span> <span data-ttu-id="38731-190">L’introduction de tâches bloquantes dans ce code peut facilement provoquer un interblocage si le code n’est pas écrit correctement.</span><span class="sxs-lookup"><span data-stu-id="38731-190">The introduction of blocking tasks into this can easily result in a deadlock if not written correctly.</span></span> <span data-ttu-id="38731-191">De plus, l’imbrication de code asynchrone peut rendre la logique d’exécution du code plus compliquée.</span><span class="sxs-lookup"><span data-stu-id="38731-191">Additionally, the nesting of asynchronous code like this can also make it more difficult to reason about the execution of the code.</span></span> <span data-ttu-id="38731-192">Combiner du code asynchrone et du code LINQ offre beaucoup de possibilités, mais nécessite d’être fait avec précaution et de manière claire.</span><span class="sxs-lookup"><span data-stu-id="38731-192">Async and LINQ are powerful, but should be used together as carefully and clearly as possible.</span></span>

* <span data-ttu-id="38731-193">**Écrivez du code qui attend certaines tâches de façon non bloquante.**</span><span class="sxs-lookup"><span data-stu-id="38731-193">**Write code that awaits Tasks in a non-blocking manner**</span></span>

<span data-ttu-id="38731-194">Si vous choisissez de bloquer le thread actuel pour attendre la fin d’une tâche, vous risquez de provoquer des interblocages et le blocage de threads de contexte, et de gérer moins facilement les erreurs.</span><span class="sxs-lookup"><span data-stu-id="38731-194">Blocking the current thread as a means to wait for a Task to complete can result in deadlocks and blocked context threads, and can require significantly more complex error-handling.</span></span> <span data-ttu-id="38731-195">Le tableau suivant fournit des conseils pour attendre la fin de tâches de façon non bloquante :</span><span class="sxs-lookup"><span data-stu-id="38731-195">The following table provides guidance on how to deal with waiting for Tasks in a non-blocking way:</span></span>

| <span data-ttu-id="38731-196">Élément à utiliser...</span><span class="sxs-lookup"><span data-stu-id="38731-196">Use this...</span></span> | <span data-ttu-id="38731-197">Au lieu de...</span><span class="sxs-lookup"><span data-stu-id="38731-197">Instead of this...</span></span> | <span data-ttu-id="38731-198">Pour</span><span class="sxs-lookup"><span data-stu-id="38731-198">When wishing to do this</span></span> |
| --- | --- | --- |
| `await` | <span data-ttu-id="38731-199">`Task.Wait` ou `Task.Result`</span><span class="sxs-lookup"><span data-stu-id="38731-199">`Task.Wait` or `Task.Result`</span></span> | <span data-ttu-id="38731-200">Extraire le résultat d’une tâche en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="38731-200">Retrieving the result of a background task</span></span> |
| `await Task.WhenAny` | `Task.WaitAny` | <span data-ttu-id="38731-201">Attendre la fin d’une tâche</span><span class="sxs-lookup"><span data-stu-id="38731-201">Waiting for any task to complete</span></span> |
| `await Task.WhenAll` | `Task.WaitAll` | <span data-ttu-id="38731-202">Attendre la fin de toutes les tâches</span><span class="sxs-lookup"><span data-stu-id="38731-202">Waiting for all tasks to complete</span></span> |
| `await Task.Delay` | `Thread.Sleep` | <span data-ttu-id="38731-203">Attendre pendant une période</span><span class="sxs-lookup"><span data-stu-id="38731-203">Waiting for a period of time</span></span> |

* <span data-ttu-id="38731-204">**Limitez l’écriture de code avec état.**</span><span class="sxs-lookup"><span data-stu-id="38731-204">**Write less stateful code**</span></span>

<span data-ttu-id="38731-205">Écrivez du code qui ne dépend pas de l’état d’objets globaux ou de l’exécution de certaines méthodes.</span><span class="sxs-lookup"><span data-stu-id="38731-205">Don’t depend on the state of global objects or the execution of certain methods.</span></span> <span data-ttu-id="38731-206">Le code doit uniquement dépendre des valeurs de retour des méthodes.</span><span class="sxs-lookup"><span data-stu-id="38731-206">Instead, depend only on the return values of methods.</span></span> <span data-ttu-id="38731-207">Pourquoi ?</span><span class="sxs-lookup"><span data-stu-id="38731-207">Why?</span></span>

* <span data-ttu-id="38731-208">La logique du code sera plus facile à comprendre.</span><span class="sxs-lookup"><span data-stu-id="38731-208">Code will be easier to reason about.</span></span>
* <span data-ttu-id="38731-209">Le code sera plus facile à tester.</span><span class="sxs-lookup"><span data-stu-id="38731-209">Code will be easier to test.</span></span>
* <span data-ttu-id="38731-210">Combiner du code asynchrone et du code synchrone est beaucoup plus simple.</span><span class="sxs-lookup"><span data-stu-id="38731-210">Mixing async and synchronous code is far simpler.</span></span>
* <span data-ttu-id="38731-211">Les concurrences critiques peuvent généralement être évitées.</span><span class="sxs-lookup"><span data-stu-id="38731-211">Race conditions can typically be avoided altogether.</span></span>
* <span data-ttu-id="38731-212">Rendre le code dépendant des valeurs de retour facilite la coordination du code asynchrone.</span><span class="sxs-lookup"><span data-stu-id="38731-212">Depending on return values makes coordinating async code simple.</span></span>
* <span data-ttu-id="38731-213">En prime, le code fonctionne parfaitement avec l’injection de dépendances.</span><span class="sxs-lookup"><span data-stu-id="38731-213">(Bonus) it works really well with dependency injection.</span></span>

<span data-ttu-id="38731-214">L’objectif recommandé est d’atteindre une [transparence référentielle](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) complète ou quasi-complète dans votre code.</span><span class="sxs-lookup"><span data-stu-id="38731-214">A recommended goal is to achieve complete or near-complete [Referential Transparency](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) in your code.</span></span> <span data-ttu-id="38731-215">Votre base de code sera alors prédictible, testable et facile à gérer.</span><span class="sxs-lookup"><span data-stu-id="38731-215">Doing so will result in an extremely predictable, testable, and maintainable codebase.</span></span>

## <a name="other-resources"></a><span data-ttu-id="38731-216">Autres ressources</span><span class="sxs-lookup"><span data-stu-id="38731-216">Other Resources</span></span>

* <span data-ttu-id="38731-217">L’article [Async en détail](../standard/async-in-depth.md) fournit des informations supplémentaires sur le fonctionnement des tâches.</span><span class="sxs-lookup"><span data-stu-id="38731-217">[Async in-depth](../standard/async-in-depth.md) provides more information about how Tasks work.</span></span>
* [<span data-ttu-id="38731-218">Programmation asynchrone avec async et attente (C)</span><span class="sxs-lookup"><span data-stu-id="38731-218">Asynchronous programming with async and await (C#)</span></span>](./programming-guide/concepts/async/index.md)
* <span data-ttu-id="38731-219">Les vidéos [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) de Lucian Wischik sont une ressource très utile pour la programmation asynchrone.</span><span class="sxs-lookup"><span data-stu-id="38731-219">Lucian Wischik's [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) are a wonderful resource for async programming</span></span>
