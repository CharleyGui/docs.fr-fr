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
# <a name="asynchronous-programming"></a>Programmation asynchrone

Si vous avez des besoins liés aux e/s (par exemple, la demande de données à un réseau, l’accès à une base de données ou la lecture et l’écriture dans un système de fichiers), vous pouvez utiliser la programmation asynchrone. L’écriture de code asynchrone est également indiquée si votre code utilise le processeur de manière intensive, notamment pour effectuer un calcul complexe.

C# possède un modèle de programmation asynchrone au niveau du langage, qui permet d’écrire facilement du code asynchrone, sans avoir à jongler avec les rappels ni à se conformer à une bibliothèque qui prend en charge l’asynchronie. Il suit ce que l’on appelle le [modèle asynchrone basé sur des tâches (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).

## <a name="overview-of-the-asynchronous-model"></a>Vue d’ensemble du modèle asynchrone

La programmation asynchrone est basée sur les objets `Task` et `Task<T>`, qui modélisent les opérations asynchrones. Ces objets sont exposés à l’aide des mots clés `async` et `await`. Dans la plupart des cas, le modèle est assez simple :

- Pour le code lié aux e/s, vous attendez une opération qui retourne un `Task` ou `Task<T>` à l’intérieur d’une `async` méthode.
- Pour le code lié au processeur, vous attendez une opération démarrée sur un thread d’arrière-plan avec la <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> méthode.

Le mot clé `await` trouve ici toute son utilité. Il cède le contrôle à l’appelant de la méthode qui a effectué l’opération `await`. Au final, c’est ce qui rend une interface utilisateur réactive ou un service élastique. Bien qu' [il existe des façons](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) d’aborder du code asynchrone autre que `async` et `await` , cet article se concentre sur les constructions de niveau de langage.

### <a name="io-bound-example-download-data-from-a-web-service"></a>Exemple de liaison d’e/s : Télécharger des données à partir d’un service Web

Vous devrez peut-être télécharger des données à partir d’un service Web lorsque vous appuyez sur un bouton, mais ne souhaitez pas bloquer le thread d’interface utilisateur. Il peut être accompli de la façon suivante :

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

Le code exprime l’intention (en téléchargeant les données de façon asynchrone) sans être coincés dans l’interaction avec les `Task` objets.

### <a name="cpu-bound-example-perform-a-calculation-for-a-game"></a>Exemple de processeur dépendant : effectuer un calcul pour un jeu

Supposons que vous développez un jeu pour mobile dans lequel l’appui sur un bouton peut causer des dommages à de nombreux ennemis à l’écran. Le calcul des dommages infligés peut nécessiter beaucoup de ressources. Si ce calcul est effectué sur le thread d’interface utilisateur, le jeu risque d’être considérablement ralenti pendant la durée du calcul.

La meilleure façon de gérer cela est de démarrer un thread d’arrière-plan, qui effectue le travail à l’aide de `Task.Run` , et d’attendre son résultat à l’aide de `await` . Cela permet à l’interface utilisateur de paraître lisse au fur et à mesure que le travail est effectué.

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

Ce code exprime clairement l’intention de l’événement de clic du bouton. Il ne nécessite pas de gérer un thread d’arrière-plan manuellement et il effectue le travail de façon non bloquante.

### <a name="what-happens-under-the-covers"></a>Les dessous du code

Il y a de nombreux éléments mobiles dans lesquels des opérations asynchrones sont concernées. Si vous êtes curieux de savoir ce qui se passe sous les couvertures de `Task` et `Task<T>` , consultez l’article [Async in-Depth](../standard/async-in-depth.md) pour plus d’informations.

Du côté du C#, le compilateur transforme votre code en une machine à États qui effectue le suivi d’opérations telles que le traitement de l’exécution quand un `await` est atteint et la reprise de l’exécution lorsqu’une tâche en arrière-plan est terminée.

D’un point de vue théorique, il s’agit d’une implémentation du [modèle de promesses d’asynchronisme](https://en.wikipedia.org/wiki/Futures_and_promises).

## <a name="key-pieces-to-understand"></a>Éléments clés à comprendre

* Le code asynchrone peut être utilisé pour du code utilisant les E/S ou le processeur de manière intensive, mais il est utilisé de manière différente dans chaque scénario.
* Le code asynchrone utilise les objets `Task<T>` et `Task`, qui sont des constructions servant à modéliser le travail effectué en arrière-plan.
* Le mot clé `async` définit une méthode comme asynchrone, ce qui vous permet d’utiliser le mot clé `await` dans le corps de la méthode.
* Quand le mot clé `await` est utilisé, il suspend la méthode d’appel et cède le contrôle à son appelant jusqu’à ce que la tâche awaited soit terminée.
* Le mot clé `await` peut uniquement être utilisé dans une méthode asynchrone.

## <a name="recognize-cpu-bound-and-io-bound-work"></a>Reconnaître le travail lié au processeur et à l’e/s

Les deux premiers exemples de ce guide vous ont montré comment utiliser `async` et `await` pour un travail utilisant les E/S et le processeur de manière intensive. Il est primordial de savoir déterminer si un travail à effectuer utilise les E/S ou le processeur de manière intensive, car ce point peut avoir un impact important sur les performances de votre code et entraîner une utilisation incorrecte de certaines constructions.

Voici deux questions à vous poser avant d’écrire du code :

1. Votre code doit-il « attendre » quelque chose, par exemple des données d’une base de données ?

   Si la réponse est « oui », le travail **utilise les E/S de manière intensive**.

1. Votre code effectuera-t-il un calcul coûteux ?

   Si la réponse est « oui », le travail **utilise le processeur de manière intensive**.

Si le travail à faire **utilise les E/S de manière intensive**, utilisez `async` et `await` *sans* `Task.Run`. Vous *ne devez pas* utiliser la bibliothèque parallèle de tâches. Cette raison est décrite en détail dans [Async](../standard/async-in-depth.md).

Si le travail que vous avez est lié à l' **UC** et que vous vous souciez de la réactivité, utilisez `async` et `await` , mais générez le travail sur un autre thread *avec* `Task.Run` . Si le travail est approprié pour la concurrence et le parallélisme, envisagez également d’utiliser la [bibliothèque parallèle de tâches](../standard/parallel-programming/task-parallel-library-tpl.md).

De plus, vous devez toujours mesurer les performances d’exécution de votre code. Par exemple, vous constaterez peut-être que le coût d’un travail utilisant le processeur de manière intensive n’est pas si élevé que cela par rapport à la surcharge des changements de contexte induits par le multithreading. Chaque solution ayant ses compromis, choisissez le meilleur compromis pour votre scénario.

## <a name="more-examples"></a>Plus d'exemples

Les exemples suivants montrent diverses façons d’écrire du code asynchrone dans C#. Ils correspondent à plusieurs scénarios différents que vous êtes susceptible de rencontrer.

### <a name="extract-data-from-a-network"></a>Extraire des données à partir d’un réseau

Cet extrait de code télécharge le code HTML à partir de la page d’accueil de <https://dotnetfoundation.org> et compte le nombre de fois que la chaîne « .net » se produit dans le code html. Elle utilise ASP.NET pour définir une méthode de contrôleur d’API Web qui effectue cette tâche et retourne le nombre.

> [!NOTE]
> Si vous prévoyez d’effectuer une analyse HTML dans le code de production, n’utilisez pas d’expressions régulières. Utilisez plutôt une bibliothèque d’analyse.

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

Voici le même scénario écrit pour une application Windows universelle, qui effectue la même tâche quand l’utilisateur appuie sur un bouton :

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

### <a name="wait-for-multiple-tasks-to-complete"></a>Attendre la fin de plusieurs tâches

Vous pouvez avoir un scénario qui nécessite de récupérer plusieurs éléments de données simultanément. L' `Task` API contient deux méthodes, <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> , qui vous permettent d’écrire du code asynchrone qui exécute une attente non bloquante sur plusieurs travaux en arrière-plan.

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

Voici une autre façon de l’écrire de façon plus succincte, à l’aide de LINQ :

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

Si vous choisissez de combiner LINQ avec du code asynchrone, pour réduire la quantité de code, faites-le avec précaution. Du fait que LINQ utilise l’exécution différée, les appels asynchrones ne sont pas effectués immédiatement comme c’est le cas dans une boucle `foreach`, sauf si vous forcez l’itération de la séquence générée avec un appel à `.ToList()` ou `.ToArray()`.

## <a name="important-info-and-advice"></a>Informations et conseils importants

Avec la programmation asynchrone, il existe des détails à garder à l’esprit qui peuvent empêcher un comportement inattendu.

* `async` **Les méthodes doivent contenir un mot clé** `await` **dans leur corps pour pouvoir être suspendues.**

  Il ne faut pas oublier ce point. Si `await` n’est pas utilisé dans le corps d’une `async` méthode, le compilateur C# génère un avertissement, mais le code se compile et s’exécute comme s’il s’agissait d’une méthode normale. Cela est incroyablement inefficace, car l’ordinateur d’État généré par le compilateur C# pour la méthode Async n’accomplit rien.

* **Vous devez ajouter « Async » comme suffixe de chaque nom de méthode Async que vous écrivez.**

Il s’agit de la Convention utilisée dans .NET pour différencier plus facilement les méthodes synchrones et asynchrones. Certaines méthodes qui ne sont pas explicitement appelées par votre code (telles que les gestionnaires d’événements ou les méthodes de contrôleur Web) ne s’appliquent pas nécessairement. Étant donné qu’elles ne sont pas explicitement appelées par votre code, il n’est pas aussi important d’être explicite quant à leur nom.

* `async void`**doit uniquement être utilisé pour les gestionnaires d’événements.**

L’utilisation de `async void` est le seul moyen de permettre le fonctionnement des gestionnaires d’événements asynchrones, car les événements n’ont pas de types de retour (et ne peuvent donc pas utiliser les objets `Task` et `Task<T>`). Toute autre utilisation de la méthode `async void` ne suit pas le modèle TAP et peut être difficile à implémenter, comme expliqué ci-après :

* Les exceptions levées dans une `async void` méthode ne peuvent pas être interceptées en dehors de cette méthode.
* `async void`les méthodes sont difficiles à tester.
* `async void`les méthodes peuvent provoquer des effets secondaires incorrects si l’appelant ne s’attend pas à ce qu’ils soient asynchrones.

* **Définissez le thread avec précaution si vous utilisez des expressions lambda asynchrones dans des expressions LINQ.**

Les expressions lambda dans LINQ utilisent l’exécution différée, ce qui signifie que le code peut finir à s’exécuter à un moment où vous ne l’attendiez pas. L’introduction de tâches bloquantes dans ce code peut facilement provoquer un interblocage si le code n’est pas écrit correctement. De plus, l’imbrication de code asynchrone peut rendre la logique d’exécution du code plus compliquée. Combiner du code asynchrone et du code LINQ offre beaucoup de possibilités, mais nécessite d’être fait avec précaution et de manière claire.

* **Écrivez du code qui attend certaines tâches de façon non bloquante.**

Le blocage du thread actuel comme un moyen d’attendre qu’un `Task` se termine peut entraîner des interblocages et bloquer les threads de contexte, et peut nécessiter une gestion des erreurs plus complexe. Le tableau suivant fournit des conseils sur la façon de traiter l’attente des tâches de façon non bloquante :

| Élément à utiliser...          | Au lieu de...           | Lorsque vous souhaitez effectuer cette opération...                 |
|----------------------|------------------------------|--------------------------------------------|
| `await`              | `Task.Wait` ou `Task.Result` | Extraire le résultat d’une tâche en arrière-plan |
| `await Task.WhenAny` | `Task.WaitAny`               | Attendre la fin d’une tâche           |
| `await Task.WhenAll` | `Task.WaitAll`               | Attendre la fin de toutes les tâches          |
| `await Task.Delay`   | `Thread.Sleep`               | Attendre pendant une période               |

* **Envisagez d’utiliser** `ValueTask` **dans** la mesure du possible

Le retour d’un objet `Task` à partir de méthodes async peut introduire des goulots d’étranglement au niveau des performances dans certains chemins. `Task` est un type référence. Si vous l’utilisez, vous allouez donc un objet. Dans les cas où une méthode déclarée avec le `async` modificateur retourne un résultat mis en cache ou se termine de façon synchrone, les allocations supplémentaires peuvent devenir un coût de temps significatif dans les sections de code critiques pour les performances. Cela peut devenir coûteux si ces allocations se produisent dans des boucles serrées. Pour plus d’informations, consultez [types de retour asynchrones généralisés](whats-new/csharp-7.md#generalized-async-return-types).

* **Envisagez d’utiliser** `ConfigureAwait(false)`

Une question courante est « quand dois-je utiliser la <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> méthode ? ». La méthode permet à une `Task` instance de configurer son await. Il s’agit d’un élément important à prendre en compte et sa définition de manière incorrecte peut avoir une incidence sur les performances et même des blocages. Pour plus d’informations sur `ConfigureAwait` , consultez le [Forum aux questions ConfigureAwait](https://devblogs.microsoft.com/dotnet/configureawait-faq).

* **Limitez l’écriture de code avec état.**

Ne dépendez pas de l’état des objets globaux ou de l’exécution de certaines méthodes. Le code doit uniquement dépendre des valeurs de retour des méthodes. Pourquoi ?

* La logique du code sera plus facile à comprendre.
* Le code sera plus facile à tester.
* Combiner du code asynchrone et du code synchrone est beaucoup plus simple.
* Les concurrences critiques peuvent généralement être évitées.
* Rendre le code dépendant des valeurs de retour facilite la coordination du code asynchrone.
* En prime, le code fonctionne parfaitement avec l’injection de dépendances.

L’objectif recommandé est d’atteindre une [transparence référentielle](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) complète ou quasi-complète dans votre code. Votre base de code sera alors prédictible, testable et facile à gérer.

## <a name="other-resources"></a>Autres ressources

* L’article [Async en détail](../standard/async-in-depth.md) fournit des informations supplémentaires sur le fonctionnement des tâches.
* [Programmation asynchrone avec Async et await (C#)](./programming-guide/concepts/async/index.md)
* Les vidéos [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) de Lucian Wischik sont une ressource très utile pour la programmation asynchrone.
