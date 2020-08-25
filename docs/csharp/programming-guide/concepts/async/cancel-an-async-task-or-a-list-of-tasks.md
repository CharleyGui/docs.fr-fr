---
title: Annuler une liste de tâches (C#)
description: Découvrez comment utiliser des jetons d’annulation pour signaler une demande d’annulation à une liste de tâches.
ms.date: 08/19/2020
ms.topic: tutorial
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 000b6a89a9240344508a5ae6b248572c8a2177dc
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811481"
---
# <a name="cancel-a-list-of-tasks-c"></a>Annuler une liste de tâches (C#)

Vous pouvez annuler une application console Async si vous ne souhaitez pas attendre qu’elle se termine. En suivant l’exemple de cette rubrique, vous pouvez ajouter une annulation à une application qui télécharge le contenu d’une liste de sites Web. Vous pouvez annuler de nombreuses tâches en associant l' <xref:System.Threading.CancellationTokenSource> instance à chaque tâche. Si vous sélectionnez la touche <kbd>entrée</kbd> , vous annulez toutes les tâches qui ne sont pas encore terminées.

Ce didacticiel contient les sections suivantes :

> [!div class="checklist"]
>
> - Création d’une application console .NET
> - Écriture d’une application Async qui prend en charge l’annulation
> - Démonstration de l’annulation de la signalisation

## <a name="prerequisites"></a>Prérequis

Ce didacticiel requiert les éléments suivants :

- [.NET 5,0 ou kit de développement logiciel (SDK) ultérieur](https://dotnet.microsoft.com/download/dotnet/5.0)
- Environnement de développement intégré (IDE)
  - [Nous vous recommandons Visual Studio, Visual Studio Code ou Visual Studio pour Mac](https://visualstudio.microsoft.com)

### <a name="create-example-application"></a>Créer un exemple d’application

Créez une application de console .NET Core. Vous pouvez en créer un à l’aide de la commande [dotnet New console](../../../../core/tools/dotnet-new.md#console) ou de [Visual Studio](/visualstudio/install/install-visual-studio). Ouvrez le fichier *Program.cs* dans votre éditeur de code favori.

### <a name="replace-using-statements"></a>Remplacer les instructions using

Remplacez les instructions using existantes par les déclarations suivantes :

```csharp
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Net.Http;
using System.Threading;
using System.Threading.Tasks;
```

## <a name="add-fields"></a>Ajouter des champs

Dans la `Program` définition de classe, ajoutez les trois champs suivants :

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

Le <xref:System.Threading.CancellationTokenSource> est utilisé pour signaler une annulation demandée à un <xref:System.Threading.CancellationToken> . Le `HttpClient` expose la possibilité d’envoyer des requêtes http et de recevoir des réponses http. Le `s_urlList` contient toutes les URL que l’application envisage de traiter.

## <a name="update-application-entry-point"></a>Mettre à jour le point d’entrée de l’application

Le point d’entrée principal dans l’application console est la `Main` méthode. Remplacez la méthode existante par le code suivant :

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

La méthode mise à jour `Main` est maintenant considérée comme une [main asynchrone](../../../whats-new/csharp-7-1.md#async-main), ce qui permet d’obtenir un point d’entrée asynchrone dans l’exécutable. Il écrit quelques messages d’instructions dans la console, puis déclare une <xref:System.Threading.Tasks.Task> instance nommée `cancelTask` , qui lira les séquences de touches de la console. Si la touche <kbd>entrée</kbd> est enfoncée, un appel à <xref:System.Threading.CancellationTokenSource.Cancel?displayProperty=nameWithType> est effectué. Cela signalera l’annulation. Ensuite, la `sumPageSizesTask` variable est assignée à partir de la `SumPageSizesAsync` méthode. Les deux tâches sont ensuite transmises à <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])?displayProperty=nameWithType> , qui se poursuivra quand l’une des deux tâches sera terminée.

## <a name="create-the-asynchronous-sum-page-sizes-method"></a>Créer la méthode de taille de page Sum asynchrone

Sous la `Main` méthode, ajoutez la `SumPageSizesAsync` méthode :

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

La méthode commence par instancier et démarrer un <xref:System.Diagnostics.Stopwatch> . Il parcourt ensuite chaque URL dans le `s_urlList` et appelle `ProcessUrlAsync` . Avec chaque itération, le `s_cts.Token` est passé dans la `ProcessUrlAsync` méthode et le code retourne un <xref:System.Threading.Tasks.Task%601> , où `TResult` est un entier :

```csharp
int total = 0;
foreach (string url in s_urlList)
{
    int contentLength = await ProcessUrlAsync(url, s_client, s_cts.Token);
    total += contentLength;
}
```

## <a name="add-process-method"></a>Ajouter une méthode de traitement

Ajoutez la méthode suivante en `ProcessUrlAsync` dessous de la `SumPageSizesAsync` méthode :

```csharp
static async Task<int> ProcessUrlAsync(string url, HttpClient client, CancellationToken token)
{
    HttpResponseMessage response = await client.GetAsync(url, token);
    byte[] content = await response.Content.ReadAsByteArrayAsync(token);
    Console.WriteLine($"{url,-60} {content.Length,10:#,#}");

    return content.Length;
}
```

Pour une URL donnée, la méthode utilise l' `client` instance fournie pour obtenir la réponse en tant que `byte[]` . L' <xref:System.Threading.CancellationToken> instance est passée dans les <xref:System.Net.Http.HttpClient.GetAsync(System.String,System.Threading.CancellationToken)?displayProperty=nameWithType> <xref:System.Net.Http.HttpContent.ReadAsByteArrayAsync(System.Threading.CancellationToken)?displayProperty=nameWithType> méthodes et. Le `token` est utilisé pour s’inscrire à l’annulation demandée. La longueur est retournée une fois que l’URL et la longueur sont écrites dans la console.

### <a name="example-application-output"></a>Exemple de sortie d’application

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

## <a name="complete-example"></a>Exemple complet

Le code suivant est le texte complet du fichier *Program.cs* pour l’exemple.

:::code language="csharp" source="snippets/cancel-tasks/cancel-tasks/Program.cs":::

## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.CancellationToken>
- <xref:System.Threading.CancellationTokenSource>
- [Programmation asynchrone avec Async et await (C#)](index.md)

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Annuler des tâches async après une période spécifique (C#)](cancel-async-tasks-after-a-period-of-time.md)
