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
# <a name="asynchronous-programming"></a>Programmation asynchrone

Si vous avez besoin d’écrire du code qui utilise les E/S de manière intensive (par exemple, pour récupérer des données d’un réseau ou accéder à une base de données), optez pour la programmation asynchrone.  L’écriture de code asynchrone est également indiquée si votre code utilise le processeur de manière intensive, notamment pour effectuer un calcul complexe.

C# fournit un modèle de programmation asynchrone de niveau de langage. Ce modèle facilite l’écriture de code asynchrone, en vous évitant d’effectuer des rappels multiples ou de vous conformer à une bibliothèque qui prend en charge l’asynchronisme. Il suit ce que l’on appelle le [modèle asynchrone basé sur des tâches (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).

## <a name="basic-overview-of-the-asynchronous-model"></a>Vue d’ensemble du modèle asynchrone

La programmation asynchrone est basée sur les objets `Task` et `Task<T>`, qui modélisent les opérations asynchrones.  Ces objets sont exposés à l’aide des mots clés `async` et `await`.  Dans la plupart des cas, le modèle est assez simple :

Pour du code utilisant les E/S de manière intensive, vous spécifiez une opération `await` qui retourne un objet `Task` ou `Task<T>` dans une méthode `async`.

Pour du code utilisant le processeur de manière intensive, vous spécifiez une opération `await` qui est démarrée sur un thread d’arrière-plan avec la méthode `Task.Run`.

Le mot clé `await` trouve ici toute son utilité. Il cède le contrôle à l’appelant de la méthode qui a effectué l’opération `await`. Au final, c’est ce qui rend une interface utilisateur réactive ou un service élastique.

Il y a d’autres approches du code asynchrone que les approches `async` et `await` décrites dans l’article sur le modèle TAP mentionné ci-dessus, mais la suite de ce document traite en particulier des constructions de niveau de langage.

### <a name="io-bound-example-downloading-data-from-a-web-service"></a>Exemple de code utilisant les E/S de manière intensive : télécharger des données d’un service web

Imaginons que vous souhaitez écrire du code qui télécharge des données d’un service web quand un utilisateur appuie sur un bouton, mais qui ne bloque pas le thread d’interface utilisateur. Il vous suffit d’écrire ce code :

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

Vous avez terminé. Le code exprime l’intention (télécharger des données de façon asynchrone) sans que cela nécessite des interactions compliquées avec les objets Task.

### <a name="cpu-bound-example-performing-a-calculation-for-a-game"></a>Exemple de code utilisant le processeur de manière intensive : effectuer un calcul dans un jeu

Supposons que vous développez un jeu pour mobile dans lequel l’appui sur un bouton peut causer des dommages à de nombreux ennemis à l’écran.  Le calcul des dommages infligés peut nécessiter beaucoup de ressources. Si ce calcul est effectué sur le thread d’interface utilisateur, le jeu risque d’être considérablement ralenti pendant la durée du calcul.

La meilleure façon de gérer cette situation est de démarrer un thread d’arrière-plan qui effectue le travail à l’aide de `Task.Run`, et retourne le résultat `await`.  Ainsi, l’interface utilisateur conserve les mêmes performances pendant le calcul.

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

Et le tour est joué !  Ce code exprime clairement l’intention de l’événement de clic du bouton. Il ne nécessite pas de gérer un thread d’arrière-plan manuellement et il effectue le travail de façon non bloquante.

### <a name="what-happens-under-the-covers"></a>Les dessous du code

Il y a de nombreux éléments variables en ce qui concerne les opérations asynchrones.  Si vous souhaitez connaître tous les dessous des objets `Task` et `Task<T>`, consultez l’article [Async en détail](../standard/async-in-depth.md).

Sur le plan du langage C#, le compilateur transforme votre code en une machine à états qui effectue le suivi des événements, tels que la suspension de l’exécution en présence d’un `await` et la reprise de l’exécution à la fin d’un travail en arrière-plan.

D’un point de vue théorique, il s’agit d’une implémentation du [modèle de promesses d’asynchronisme](https://en.wikipedia.org/wiki/Futures_and_promises).

## <a name="key-pieces-to-understand"></a>Points clés à comprendre

* Le code asynchrone peut être utilisé pour du code utilisant les E/S ou le processeur de manière intensive, mais il est utilisé de manière différente dans chaque scénario.
* Le code asynchrone utilise les objets `Task<T>` et `Task`, qui sont des constructions servant à modéliser le travail effectué en arrière-plan.
* Le mot clé `async` définit une méthode comme asynchrone, ce qui vous permet d’utiliser le mot clé `await` dans le corps de la méthode.
* Quand le mot clé `await` est utilisé, il suspend la méthode d’appel et cède le contrôle à son appelant jusqu’à ce que la tâche awaited soit terminée.
* Le mot clé `await` peut uniquement être utilisé dans une méthode asynchrone.

## <a name="recognize-cpu-bound-and-io-bound-work"></a>Déterminer si un travail utilise le processeur ou les E/S de manière intensive

Les deux premiers exemples de ce guide vous ont montré comment utiliser `async` et `await` pour un travail utilisant les E/S et le processeur de manière intensive.  Il est primordial de savoir déterminer si un travail à effectuer utilise les E/S ou le processeur de manière intensive, car ce point peut avoir un impact important sur les performances de votre code et entraîner une utilisation incorrecte de certaines constructions.

Voici deux questions à vous poser avant d’écrire du code :

1. Votre code doit-il « attendre » quelque chose, par exemple des données d’une base de données ?

    Si la réponse est « oui », le travail **utilise les E/S de manière intensive**.

2. Le code doit-il effectuer un calcul très complexe ?

    Si la réponse est « oui », le travail **utilise le processeur de manière intensive**.

Si le travail à faire **utilise les E/S de manière intensive**, utilisez `async` et `await` *sans* `Task.Run`.  Vous *ne devez pas* utiliser la bibliothèque parallèle de tâches.  La raison à cela est expliquée dans l’article [Async en détail](../standard/async-in-depth.md).

Si le travail à faire **utilise le processeur de manière intensive** et que la réactivité est une exigence, utilisez `async` et `await`, mais transférez le travail sur un autre thread *avec* `Task.Run`.  S’il accepte la concurrence et le parallélisme, vous pouvez également utiliser la [bibliothèque parallèle de tâches](../standard/parallel-programming/task-parallel-library-tpl.md).

De plus, vous devez toujours mesurer les performances d’exécution de votre code.  Par exemple, vous constaterez peut-être que le coût d’un travail utilisant le processeur de manière intensive n’est pas si élevé que cela par rapport à la surcharge des changements de contexte induits par le multithreading.  Chaque solution ayant ses compromis, choisissez le meilleur compromis pour votre scénario.

## <a name="more-examples"></a>Plus d'exemples

Les exemples suivants montrent diverses façons d’écrire du code asynchrone dans C#.  Ils correspondent à plusieurs scénarios différents que vous êtes susceptible de rencontrer.

### <a name="extracting-data-from-a-network"></a>Extraire des données d’un réseau

Cet extrait de code télécharge le code HTML à partir de la page d’accueil du site [www.dotnetfoundation.org](https://www.dotnetfoundation.org) et compte le nombre d’occurrences de la chaîne « .NET » dans le code HTML.  Il utilise ASP.NET MVC pour définir une méthode de contrôleur web qui exécute cette tâche et retourne le nombre.

> [!NOTE]
> Si vous prévoyez d’effectuer une analyse HTML dans le code de production, n’utilisez pas d’expressions régulières. Utilisez plutôt une bibliothèque d’analyse.

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

Voici le même scénario écrit pour une application Windows universelle, qui effectue la même tâche quand l’utilisateur appuie sur un bouton :

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

### <a name="waiting-for-multiple-tasks-to-complete"></a>Attendre la fin de plusieurs tâches

Vous pouvez avoir un scénario qui nécessite de récupérer plusieurs éléments de données simultanément.  L’API `Task` fournit deux méthodes, `Task.WhenAll` et `Task.WhenAny`, que vous pouvez utiliser pour écrire du code asynchrone qui spécifie une attente non bloquante sur plusieurs travaux en arrière-plan.

Cet exemple vous montre comment récupérer des données `User` pour plusieurs `userId`.

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

Voici une façon plus succincte d’écrire ce code, en utilisant LINQ :

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

Si vous choisissez de combiner LINQ avec du code asynchrone, pour réduire la quantité de code, faites-le avec précaution.  Du fait que LINQ utilise l’exécution différée, les appels asynchrones ne sont pas effectués immédiatement comme c’est le cas dans une boucle `foreach()`, sauf si vous forcez l’itération de la séquence générée avec un appel à `.ToList()` ou `.ToArray()`.

## <a name="important-info-and-advice"></a>Informations et conseils importants

La programmation asynchrone est relativement simple, mais il y a quelques points à garder à l’esprit pour éviter un comportement inattendu du code.

* `async` **Les méthodes doivent contenir un mot clé** `await` **dans leur corps pour pouvoir être suspendues.**

Il ne faut pas oublier ce point.  Si `await` n’est pas utilisé dans le corps d’une méthode `async`, le compilateur C# génère un avertissement, mais le code est compilé et exécuté comme s’il s’agissait d’une méthode standard.  Notez également que cela n’aurait aucune utilité, car la machine à états générée par le compilateur C# pour la méthode async n’accomplirait aucune opération dans ce cas.

* **Vous devez ajouter "Async" comme suffixe de chaque nom de méthode async que vous écrivez.**

Cette convention de .NET aide à différencier les méthodes synchrones et asynchrones. Notez que cela n’est pas obligatoire pour certaines méthodes qui ne sont pas explicitement appelées par votre code (par exemple, les gestionnaires d’événements et les méthodes de contrôleur web). L’attribution d’un nom explicite pour ces méthodes a moins d’importance.

* `async void` **ne doit être utilisé que pour les gestionnaires d’événements.**

L’utilisation de `async void` est le seul moyen de permettre le fonctionnement des gestionnaires d’événements asynchrones, car les événements n’ont pas de types de retour (et ne peuvent donc pas utiliser les objets `Task` et `Task<T>`). Toute autre utilisation de la méthode `async void` ne suit pas le modèle TAP et peut être difficile à implémenter, comme expliqué ci-après :

* Les exceptions levées dans une méthode `async void` ne peuvent pas être interceptées en dehors de cette méthode.
* Les méthodes `async void` sont très difficiles à tester.
* Les méthodes `async void` peuvent avoir des effets secondaires gênants si l’appelant n’attend pas de méthodes asynchrones.

* **Définissez le thread avec précaution si vous utilisez des expressions lambda asynchrones dans des expressions LINQ.**

Dans LINQ, les expressions lambda utilisent l’exécution différée, ce qui signifie que l’exécution du code peut s’arrêter à un point que vous n’aviez pas prévu. L’introduction de tâches bloquantes dans ce code peut facilement provoquer un interblocage si le code n’est pas écrit correctement. De plus, l’imbrication de code asynchrone peut rendre la logique d’exécution du code plus compliquée. Combiner du code asynchrone et du code LINQ offre beaucoup de possibilités, mais nécessite d’être fait avec précaution et de manière claire.

* **Écrivez du code qui attend certaines tâches de façon non bloquante.**

Si vous choisissez de bloquer le thread actuel pour attendre la fin d’une tâche, vous risquez de provoquer des interblocages et le blocage de threads de contexte, et de gérer moins facilement les erreurs. Le tableau suivant fournit des conseils pour attendre la fin de tâches de façon non bloquante :

| Élément à utiliser... | Au lieu de... | Pour |
| --- | --- | --- |
| `await` | `Task.Wait` ou `Task.Result` | Extraire le résultat d’une tâche en arrière-plan |
| `await Task.WhenAny` | `Task.WaitAny` | Attendre la fin d’une tâche |
| `await Task.WhenAll` | `Task.WaitAll` | Attendre la fin de toutes les tâches |
| `await Task.Delay` | `Thread.Sleep` | Attendre pendant une période |

* **Limitez l’écriture de code avec état.**

Écrivez du code qui ne dépend pas de l’état d’objets globaux ou de l’exécution de certaines méthodes. Le code doit uniquement dépendre des valeurs de retour des méthodes. Pourquoi ?

* La logique du code sera plus facile à comprendre.
* Le code sera plus facile à tester.
* Combiner du code asynchrone et du code synchrone est beaucoup plus simple.
* Les concurrences critiques peuvent généralement être évitées.
* Rendre le code dépendant des valeurs de retour facilite la coordination du code asynchrone.
* En prime, le code fonctionne parfaitement avec l’injection de dépendances.

L’objectif recommandé est d’atteindre une [transparence référentielle](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) complète ou quasi-complète dans votre code. Votre base de code sera alors prédictible, testable et facile à gérer.

## <a name="other-resources"></a>Autres ressources

* L’article [Async en détail](../standard/async-in-depth.md) fournit des informations supplémentaires sur le fonctionnement des tâches.
* [Programmation asynchrone avec async et attente (C)](./programming-guide/concepts/async/index.md)
* Les vidéos [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) de Lucian Wischik sont une ressource très utile pour la programmation asynchrone.
