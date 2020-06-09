---
title: Utilisation du modèle asynchrone basé sur les tâches
description: Apprenez à utiliser le modèle asynchrone basé sur des tâches (TAP) quand vous travaillez avec des opérations asynchrones.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: 033cf871-ae24-433d-8939-7a3793e547bf
ms.openlocfilehash: 2553a573a9827b8f9232ddab132bd9331586a0f1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84583828"
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a>Utilisation du modèle asynchrone basé sur les tâches

Lorsque vous utilisez le modèle asynchrone basé sur les tâches (TAP) pour travailler avec des opérations asynchrones, vous pouvez utiliser des rappels pour terminer l’attente sans blocage.  Pour les tâches, vous pouvez faire de même à l’aide de méthodes telles que <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>. La prise en charge asynchrone basée sur le langage masque les rappels en permettant aux opérations asynchrones d’être attendues dans le flux de contrôle normal, et le code généré par le compilateur fournit cette même prise en charge au niveau de l’API.

## <a name="suspending-execution-with-await"></a>Suspension de l’exécution avec Await
 À partir de .NET Framework 4.5, vous pouvez utiliser le mot clé [await](../../csharp/language-reference/operators/await.md) en C# et l’[opérateur Await](../../visual-basic/language-reference/operators/await-operator.md) en Visual Basic pour attendre de manière asynchrone les objets <xref:System.Threading.Tasks.Task> et <xref:System.Threading.Tasks.Task%601>. Quand vous attendez une <xref:System.Threading.Tasks.Task>, l’expression `await` est de type `void`. Quand vous attendez une <xref:System.Threading.Tasks.Task%601>, l’expression `await` est de type `TResult`. Une expression `await` doit se produire dans le corps d’une méthode asynchrone. Pour plus d’informations sur la prise en charge des langages C# et Visual Basic dans .NET Framework 4.5, consultez les spécifications des langages C# et Visual Basic.

 En arrière-plan, la fonctionnalité await installe un rappel sur la tâche à l’aide d’une continuation.  Ce rappel reprend la méthode asynchrone au point d’interruption. Quand la méthode asynchrone est reprise, si l’opération attendue s’est terminée correctement et est une <xref:System.Threading.Tasks.Task%601>, son `TResult` est retourné.  Si la <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> attendue s’est terminée dans l’état <xref:System.Threading.Tasks.TaskStatus.Canceled>, une exception <xref:System.OperationCanceledException> est levée.  Si la <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> attendue s’est terminée dans l’état <xref:System.Threading.Tasks.TaskStatus.Faulted>, l’exception qui a entraîné l’erreur est levée. Une `Task` peut échouer à cause de plusieurs exceptions, mais seule une de ces exceptions est propagée. Toutefois, la propriété <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> retourne une exception <xref:System.AggregateException> qui contient toutes les erreurs.

 Si un contexte de synchronisation (objet <xref:System.Threading.SynchronizationContext>) est associé au thread qui exécutait la méthode asynchrone au moment de la suspension (par exemple, si la propriété <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> n’est pas `null`), la méthode asynchrone reprend sur ce même contexte de synchronisation à l’aide de la méthode <xref:System.Threading.SynchronizationContext.Post%2A> du contexte. Dans le cas contraire, elle s’appuie sur le planificateur de tâches (objet <xref:System.Threading.Tasks.TaskScheduler>) qui était en cours au moment de la suspension. En général, il s’agit du planificateur de tâches par défaut (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), qui cible le pool de threads. Le planificateur de tâches détermine si l’opération asynchrone attendue doit reprendre où elle s’est terminée ou si la reprise doit être planifiée. Le planificateur par défaut permet généralement à la continuation de s’exécuter sur le thread qui a effectué l’opération attendue.

 Lorsqu’une méthode asynchrone est appelée, elle exécute simultanément le corps de la fonction jusqu'à la première expression await sur une instance prenant en charge await qui n’est pas encore terminée. À ce moment, l’appel retourne à l’appelant. Si la méthode asynchrone ne retourne pas `void`, un objet <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> est retourné pour représenter le calcul en cours. Dans une méthode asynchrone non void, si une instruction de retour est rencontrée ou si la fin du corps de la méthode est atteinte, la tâche est terminée dans l’état final <xref:System.Threading.Tasks.TaskStatus.RanToCompletion>. Si une exception non gérée cause la sortie du contrôle du corps de la méthode asynchrone, la tâche se termine dans l’état <xref:System.Threading.Tasks.TaskStatus.Faulted>. S’il s’agit d’une exception <xref:System.OperationCanceledException>, la tâche se termine dans l’état <xref:System.Threading.Tasks.TaskStatus.Canceled>. De cette manière, la publication du résultat ou de l’exception a finalement lieu.

 Il existe plusieurs variations importantes de ce comportement.  Pour des raisons de performances, si une tâche est déjà terminée au moment où la tâche est attendue avec await, le contrôle n’est pas transmis et la fonction continue à s’exécuter.  En outre, le retour au contexte d’origine n’est pas toujours souhaitable et ce comportement peut être modifié. Cette opération est décrite plus en détail dans la section suivante.

### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a>Configuration de la suspension et de la reprise avec Yield et ConfigureAwait
 Plusieurs méthodes fournissent davantage de contrôle sur l’exécution d’une méthode asynchrone. Par exemple, vous pouvez utiliser la méthode <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> pour introduire un point de transmission dans la méthode asynchrone :

```csharp
public class Task : …
{
    public static YieldAwaitable Yield();
    …
}
```

 Cela équivaut à la publication asynchrone ou à la replanification vers le contexte actuel.

```csharp
Task.Run(async delegate
{
    for(int i=0; i<1000000; i++)
    {
        await Task.Yield(); // fork the continuation into a separate work item
        ...
    }
});
```

 Vous pouvez également utiliser la méthode <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> pour mieux contrôler la suspension et la reprise dans une méthode asynchrone.  Comme mentionné précédemment, par défaut, le contexte actuel est capturé au moment où une méthode asynchrone est interrompue, et ce contexte capturé est utilisé pour appeler la continuation de la méthode asynchrone lors de la reprise.  Dans de nombreux cas, il s’agit du comportement exact que vous souhaitez.  Dans d’autres cas, vous pouvez ne pas vous soucier du contexte de continuation, et vous pouvez obtenir de meilleures performances en évitant d’effectuer ces publications vers le contexte d’origine.  Pour ce faire, utilisez la méthode <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> pour informer l’opération await de ne pas capturer et reprendre sur le contexte, mais plutôt de poursuivre l’exécution quand l’opération asynchrone attendue est terminée :

```csharp
await someTask.ConfigureAwait(continueOnCapturedContext:false);
```

## <a name="canceling-an-asynchronous-operation"></a>Annulation d'une opération asynchrone
 À compter de .NET Framework 4, les méthodes TAP qui prennent en charge l’annulation fournissent au moins une surcharge qui accepte un jeton d’annulation (objet <xref:System.Threading.CancellationToken>).

 Un jeton d’annulation est créé via une source de jeton d’annulation (objet <xref:System.Threading.CancellationTokenSource>).  La propriété <xref:System.Threading.CancellationTokenSource.Token%2A> de la source retourne le jeton d’annulation qui sera signalé quand la méthode <xref:System.Threading.CancellationTokenSource.Cancel%2A> de la source sera appelée.  Par exemple, si vous souhaitez télécharger une page web unique et que vous souhaitiez être en mesure d’annuler l’opération, vous créez un objet <xref:System.Threading.CancellationTokenSource>, passez son jeton à la méthode TAP et appelez ensuite la méthode <xref:System.Threading.CancellationTokenSource.Cancel%2A> de la source quand vous êtes prêt à annuler l’opération :

```csharp
var cts = new CancellationTokenSource();
string result = await DownloadStringAsync(url, cts.Token);
… // at some point later, potentially on another thread
cts.Cancel();
```

 Pour annuler plusieurs appels asynchrones, vous pouvez passer le même jeton pour tous les appels :

```csharp
var cts = new CancellationTokenSource();
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));
    // at some point later, potentially on another thread
    …
    cts.Cancel();
```

 Ou bien, vous pouvez passer le même jeton à un sous-ensemble sélectif d’opérations :

```csharp
var cts = new CancellationTokenSource();
    byte [] data = await DownloadDataAsync(url, cts.Token);
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);
    … // at some point later, potentially on another thread
    cts.Cancel();
```

 Les demandes d’annulation peuvent être lancées à partir de n’importe quel thread.

 Vous pouvez passer la valeur <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> à toute méthode qui accepte les jetons d’annulation pour indiquer que l’annulation ne sera jamais demandée.  La propriété <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> retourne alors `false`, et la méthode appelée peut optimiser en conséquence.  À des fins de test, vous pouvez également transmettre un jeton pré-annulation instancié à l’aide du constructeur qui accepte une valeur booléenne pour indiquer si le jeton doit démarrer dans un état non annulable ou déjà annulé.

 Cette approche de l’annulation présente plusieurs avantages :

- Vous pouvez passer le même jeton d’annulation à n’importe quel nombre d’opérations asynchrones ou synchrones.

- La même demande d’annulation peut être déployée vers n’importe quel nombre d’écouteurs.

- Le développeur de l’API asynchrone a le contrôle complet de la possibilité de demander l’annulation et du timing de la prise d’effet.

- Le code qui utilise l’API peut déterminer de manière sélective les appels asynchrones qui seront transmis aux demandes d’annulation.

## <a name="monitoring-progress"></a>Contrôle de la progression
 Certaines méthodes asynchrones exposent la progression via une interface de progression transmise à la méthode asynchrone.  Par exemple, considérez une fonction qui télécharge une chaîne de texte de façon asynchrone et qui, tout au long du processus, déclenche des mises à jour de progression qui incluent le pourcentage de téléchargement terminé jusqu'à présent.  Cette méthode peut être utilisée dans une application Windows Presentation Foundation (WPF), comme suit :

```csharp
private async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.IsEnabled = false;
    try
    {
        txtResult.Text = await DownloadStringAsync(txtUrl.Text,
            new Progress<int>(p => pbDownloadProgress.Value = p));
    }
    finally { btnDownload.IsEnabled = true; }
}
```

<a name="combinators"></a>
## <a name="using-the-built-in-task-based-combinators"></a>Utilisation des combinateurs intégrés sur les tâches
 L’espace de noms <xref:System.Threading.Tasks> inclut plusieurs méthodes de composition et d’utilisation des tâches.

### <a name="taskrun"></a>Task.Run
 La classe <xref:System.Threading.Tasks.Task> inclut plusieurs méthodes <xref:System.Threading.Tasks.Task.Run%2A> qui vous permettent de décharger facilement du travail en tant que <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> dans le pool de threads, par exemple :

```csharp
public async void button1_Click(object sender, EventArgs e)
{
    textBox1.Text = await Task.Run(() =>
    {
        // … do compute-bound work here
        return answer;
    });
}
```

 Certaines de ces méthodes <xref:System.Threading.Tasks.Task.Run%2A>, telles que la surcharge <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, existent en tant que raccourcis pour la méthode <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType>.  D’autres surcharges, telles que <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, vous permettent d’utiliser await dans le travail déchargé, par exemple :

```csharp
public async void button1_Click(object sender, EventArgs e)
{
    pictureBox1.Image = await Task.Run(async() =>
    {
        using(Bitmap bmp1 = await DownloadFirstImageAsync())
        using(Bitmap bmp2 = await DownloadSecondImageAsync())
        return Mashup(bmp1, bmp2);
    });
}
```

 D’un point de vue logique, ces surcharges reviennent à utiliser la méthode <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> conjointement avec la méthode d’extension <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> dans la bibliothèque parallèle de tâches.

### <a name="taskfromresult"></a>Task.FromResult
 Utilisez la méthode <xref:System.Threading.Tasks.Task.FromResult%2A> dans les scénarios où les données peuvent être déjà disponibles et doivent simplement être retournées par une méthode retournant des tâches élevée dans une <xref:System.Threading.Tasks.Task%601> :

```csharp
public Task<int> GetValueAsync(string key)
{
    int cachedValue;
    return TryGetCachedValue(out cachedValue) ?
        Task.FromResult(cachedValue) :
        GetValueAsyncInternal();
}

private async Task<int> GetValueAsyncInternal(string key)
{
    …
}
```

### <a name="taskwhenall"></a>Task.WhenAll
 Utilisez la méthode <xref:System.Threading.Tasks.Task.WhenAll%2A> pour attendre de façon asynchrone plusieurs opérations asynchrones représentées en tant que tâches.  La méthode a plusieurs surcharges qui prennent en charge un ensemble de tâches non génériques ou un ensemble non uniforme de tâches génériques (par exemple, l’attente asynchrone de plusieurs opérations qui retournent void, ou l’attente asynchrone de plusieurs méthodes retournant des valeurs où chaque valeur peut avoir un type différent) ou prennent en charge un ensemble uniforme de tâches génériques (comme l’attente asynchrone de plusieurs méthodes retournant `TResult`).

 Supposons que vous souhaitez envoyer des messages électroniques à plusieurs clients. Vous pouvez superposer l’envoi des messages afin de ne pas attendre la fin de l’envoi d’un message avant d’envoyer le suivant. Vous saurez également quand les opérations d’envoi se sont terminées et si des erreurs se sont produites :

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
await Task.WhenAll(asyncOps);
```

 Ce code ne gère pas explicitement les exceptions qui peuvent se produire, mais laisse les exceptions propager le `await` sur la tâche obtenue à partir de <xref:System.Threading.Tasks.Task.WhenAll%2A>.  Pour gérer les exceptions, vous pouvez utiliser le code suivant :

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
try
{
    await Task.WhenAll(asyncOps);
}
catch(Exception exc)
{
    ...
}
```

 Dans ce cas, si une opération asynchrone échoue, toutes les exceptions sont consolidées dans une exception <xref:System.AggregateException>, qui est stockée dans la <xref:System.Threading.Tasks.Task> retournée par la méthode <xref:System.Threading.Tasks.Task.WhenAll%2A>.  Toutefois, une seul de ces exceptions est propagée par le mot-clé `await`.  Si vous souhaitez examiner toutes les exceptions, vous pouvez réécrire le code précédent comme suit :

```csharp
Task [] asyncOps = (from addr in addrs select SendMailAsync(addr)).ToArray();
try
{
    await Task.WhenAll(asyncOps);
}
catch(Exception exc)
{
    foreach(Task faulted in asyncOps.Where(t => t.IsFaulted))
    {
        … // work with faulted and faulted.Exception
    }
}
```

 Prenons un exemple de téléchargement de plusieurs fichiers à partir du web de manière asynchrone.  Dans ce cas, toutes les opérations asynchrones ont des types de résultats homogènes, et il est facile d’accéder aux résultats :

```csharp
string [] pages = await Task.WhenAll(
    from url in urls select DownloadStringAsync(url));
```

 Vous pouvez utiliser les mêmes techniques de gestion des exceptions que celles évoquées dans le scénario précédent qui retournait void :

```csharp
Task [] asyncOps =
    (from url in urls select DownloadStringAsync(url)).ToArray();
try
{
    string [] pages = await Task.WhenAll(asyncOps);
    ...
}
catch(Exception exc)
{
    foreach(Task<string> faulted in asyncOps.Where(t => t.IsFaulted))
    {
        … // work with faulted and faulted.Exception
    }
}
```

### <a name="taskwhenany"></a>Task.WhenAny
 Vous pouvez utiliser la méthode <xref:System.Threading.Tasks.Task.WhenAny%2A> pour attendre de façon asynchrone qu’une seule des multiples opérations asynchrones représentées en tant que tâches soit effectuée.  Cette méthode couvre quatre principaux cas d’utilisation :

- Redondance : Exécution d’une opération plusieurs fois et sélection de celle qui se termine en premier (par exemple, en contactant plusieurs services web de cotation boursière qui produiront un résultat unique et en sélectionnant celui qui se terminera le plus rapidement).

- Entrelacement : Lancement de plusieurs opérations, en attendant que toutes se terminent, mais en traitant chacune lors de leur achèvement.

- Limitation : Autorisation du lancement de nouvelles opérations lorsque d’autres se terminent.  Il s’agit d’une extension de l’entrelacement.

- Interruption anticipée : par exemple, une opération représentée par la tâche t1 peut être regroupée dans une tâche <xref:System.Threading.Tasks.Task.WhenAny%2A> avec une autre tâche t2, et vous pouvez attendre la tâche <xref:System.Threading.Tasks.Task.WhenAny%2A>. La tâche t2 peut représenter un délai d’attente, une annulation ou un autre signal qui provoque l’achèvement de la tâche <xref:System.Threading.Tasks.Task.WhenAny%2A> avant la fin de t1.

#### <a name="redundancy"></a>Redondance
 Prenons un cas où vous souhaitez prendre une décision sur la nécessité d’acheter une action.  Il existe plusieurs services de recommandation de cotation boursière auxquels vous faites confiance, mais selon la charge quotidienne, chaque service peut avoir des lenteurs à des moments différents.  Vous pouvez utiliser la méthode <xref:System.Threading.Tasks.Task.WhenAny%2A> pour recevoir une notification quand une opération est terminée :

```csharp
var recommendations = new List<Task<bool>>()
{
    GetBuyRecommendation1Async(symbol),
    GetBuyRecommendation2Async(symbol),
    GetBuyRecommendation3Async(symbol)
};
Task<bool> recommendation = await Task.WhenAny(recommendations);
if (await recommendation) BuyStock(symbol);
```

 Contrairement à <xref:System.Threading.Tasks.Task.WhenAll%2A>, qui retourne les résultats non encapsulés de toutes les tâches qui se sont terminées avec succès, <xref:System.Threading.Tasks.Task.WhenAny%2A> retourne la tâche qui s’est terminée. Si une tâche échoue, il est important de savoir qu’elle a échoué, et si une tâche réussit, il est important de savoir la tâche à laquelle la valeur de retour est associée.  Par conséquent, vous devez accéder au résultat de la tâche retournée ou l’attendre davantage, comme le montre cet exemple.

 Tout comme avec <xref:System.Threading.Tasks.Task.WhenAll%2A>, vous devez être en mesure de prendre en compte les exceptions.  Étant donné que vous recevez la tâche terminée, vous pouvez attendre la tâche retournée pour propager les erreurs, et utiliser `try/catch` dessus comme nécessaire, par exemple :

```csharp
Task<bool> [] recommendations = …;
while(recommendations.Count > 0)
{
    Task<bool> recommendation = await Task.WhenAny(recommendations);
    try
    {
        if (await recommendation) BuyStock(symbol);
        break;
    }
    catch(WebException exc)
    {
        recommendations.Remove(recommendation);
    }
}
```

 En outre, même si une première tâche se termine avec succès, les tâches suivantes peuvent échouer.  À ce stade, vous disposez de plusieurs options pour la gestion des exceptions : vous pouvez attendre que toutes les tâches lancées soient terminées, auquel cas vous pouvez utiliser la méthode <xref:System.Threading.Tasks.Task.WhenAll%2A>, ou vous pouvez décider que toutes les exceptions sont importantes et doivent être journalisées.  Dans ce cas, vous pouvez utiliser les continuations de recevoir une notification lorsque des tâches se sont terminées de manière asynchrone :

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => { if (t.IsFaulted) Log(t.Exception); });
}
```

 ou :

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => Log(t.Exception), TaskContinuationOptions.OnlyOnFaulted);
}
```

 ou même :

```csharp
private static async void LogCompletionIfFailed(IEnumerable<Task> tasks)
{
    foreach(var task in tasks)
    {
        try { await task; }
        catch(Exception exc) { Log(exc); }
    }
}
…
LogCompletionIfFailed(recommendations);
```

 Enfin, vous souhaiterez peut-être annuler toutes les opérations restantes :

```csharp
var cts = new CancellationTokenSource();
var recommendations = new List<Task<bool>>()
{
    GetBuyRecommendation1Async(symbol, cts.Token),
    GetBuyRecommendation2Async(symbol, cts.Token),
    GetBuyRecommendation3Async(symbol, cts.Token)
};

Task<bool> recommendation = await Task.WhenAny(recommendations);
cts.Cancel();
if (await recommendation) BuyStock(symbol);
```

#### <a name="interleaving"></a>Entrelacement
 Prenons un cas où vous téléchargez des images à partir du web et traitez chaque image (par exemple, en ajoutant l’image à un contrôle d’interface utilisateur).  Vous devez effectuer le traitement de manière séquentielle sur le thread d’interface utilisateur, mais vous souhaitez télécharger autant d’images en même temps que possible. En outre, vous ne voulez pas retarder l’ajout d’images à l’interface utilisateur jusqu'à ce qu’elles soient toutes téléchargées : vous souhaitez les ajouter quand elles sont prêtes :

```csharp
List<Task<Bitmap>> imageTasks =
    (from imageUrl in urls select GetBitmapAsync(imageUrl)).ToList();
while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch{}
}
```

 Vous pouvez également appliquer l’entrelacement à un scénario qui implique un traitement intensif par calcul sur le <xref:System.Threading.ThreadPool> des images téléchargées, par exemple :

```csharp
List<Task<Bitmap>> imageTasks =
    (from imageUrl in urls select GetBitmapAsync(imageUrl)
         .ContinueWith(t => ConvertImage(t.Result)).ToList();
while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch{}
}
```

#### <a name="throttling"></a>Limitation
 Prenons l’exemple de l’entrelacement, sauf qu’ici l’utilisateur télécharge tant d’images que les téléchargements doivent être limités. Par exemple, vous ne souhaitez qu’un certain nombre de téléchargements simultanés. Pour ce faire, vous pouvez démarrer un sous-ensemble d’opérations asynchrones.  Lorsque les opérations sont terminées, vous pouvez démarrer des opérations supplémentaires pour prendre leur place :

```csharp
const int CONCURRENCY_LEVEL = 15;
Uri [] urls = …;
int nextIndex = 0;
var imageTasks = new List<Task<Bitmap>>();
while(nextIndex < CONCURRENCY_LEVEL && nextIndex < urls.Length)
{
    imageTasks.Add(GetBitmapAsync(urls[nextIndex]));
    nextIndex++;
}

while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch(Exception exc) { Log(exc); }

    if (nextIndex < urls.Length)
    {
        imageTasks.Add(GetBitmapAsync(urls[nextIndex]));
        nextIndex++;
    }
}
```

#### <a name="early-bailout"></a>Interruption anticipée
 Considérez que vous attendez de façon asynchrone qu’une opération se termine tout en répondant simultanément à la demande d’annulation d’un utilisateur (par exemple, lorsque l’utilisateur clique sur un bouton Annuler). Le code suivant illustre ce scénario :

```csharp
private CancellationTokenSource m_cts;

public void btnCancel_Click(object sender, EventArgs e)
{
    if (m_cts != null) m_cts.Cancel();
}

public async void btnRun_Click(object sender, EventArgs e)
{
    m_cts = new CancellationTokenSource();
    btnRun.Enabled = false;
    try
    {
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text);
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);
        if (imageDownload.IsCompleted)
        {
            Bitmap image = await imageDownload;
            panel.AddImage(image);
        }
        else imageDownload.ContinueWith(t => Log(t));
    }
    finally { btnRun.Enabled = true; }
}

private static async Task UntilCompletionOrCancellation(
    Task asyncOp, CancellationToken ct)
{
    var tcs = new TaskCompletionSource<bool>();
    using(ct.Register(() => tcs.TrySetResult(true)))
        await Task.WhenAny(asyncOp, tcs.Task);
    return asyncOp;
}
```

 Cette implémentation réactive l’interface utilisateur dès que vous décidez de quitter la procédure, mais n’annule pas les opérations asynchrones sous-jacentes.  Une autre solution serait d’annuler les opérations en attente lorsque vous décidez de quitter la procédure, mais de ne pas rétablir l’interface utilisateur avant que les opérations soient réellement terminées, éventuellement en raison d’une fin anticipée suite à une demande d’annulation :

```csharp
private CancellationTokenSource m_cts;

public async void btnRun_Click(object sender, EventArgs e)
{
    m_cts = new CancellationTokenSource();

    btnRun.Enabled = false;
    try
    {
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text, m_cts.Token);
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);
        Bitmap image = await imageDownload;
        panel.AddImage(image);
    }
    catch(OperationCanceledException) {}
    finally { btnRun.Enabled = true; }
}
```

 Un autre exemple d’interruption anticipée impliquerait l’utilisation de la méthode <xref:System.Threading.Tasks.Task.WhenAny%2A> conjointement avec la méthode <xref:System.Threading.Tasks.Task.Delay%2A>, comme décrit dans la section suivante.

### <a name="taskdelay"></a>Task.Delay
 Vous pouvez utiliser la méthode <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> pour introduire des pauses dans l’exécution d’une méthode asynchrone.  Cela est utile pour de nombreux types de fonctionnalités, notamment la création de boucles d’interrogation et le retardement du traitement des entrées d’utilisateur pour une période prédéterminée.  La méthode <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> peut également être utile si elle est combinée avec <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> pour implémenter des délais d’attente.

 Si une tâche qui fait partie d’une opération asynchrone plus vaste (par exemple, un service web ASP.NET) prend trop de temps, l’opération globale peut en pâtir, en particulier si elle ne se termine jamais.  Pour cette raison, il est important d’être en mesure de quitter la procédure lors de l’attente sur une opération asynchrone.  Les méthodes synchrones <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> acceptent des valeurs de délai d’attente, à la différence des méthodes <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> correspondantes et des méthodes <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> mentionnées précédemment qui n’en acceptent pas.  Vous pouvez, à la place, utiliser <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> conjointement pour implémenter un délai d’attente.

 Par exemple, dans votre application d’interface utilisateur, supposons que vous souhaitez télécharger une image et désactivez l’interface utilisateur pendant le téléchargement de l’image. Toutefois, si le téléchargement est trop long, vous souhaitez réactiver l’interface utilisateur et ignorer le téléchargement :

```csharp
public async void btnDownload_Click(object sender, EventArgs e)
{
    btnDownload.Enabled = false;
    try
    {
        Task<Bitmap> download = GetBitmapAsync(url);
        if (download == await Task.WhenAny(download, Task.Delay(3000)))
        {
            Bitmap bmp = await download;
            pictureBox.Image = bmp;
            status.Text = "Downloaded";
        }
        else
        {
            pictureBox.Image = null;
            status.Text = "Timed out";
            var ignored = download.ContinueWith(
                t => Trace("Task finally completed"));
        }
    }
    finally { btnDownload.Enabled = true; }
}
```

 La même règle s’applique à plusieurs téléchargements, car <xref:System.Threading.Tasks.Task.WhenAll%2A> retourne une tâche :

```csharp
public async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.Enabled = false;
    try
    {
        Task<Bitmap[]> downloads =
            Task.WhenAll(from url in urls select GetBitmapAsync(url));
        if (downloads == await Task.WhenAny(downloads, Task.Delay(3000)))
        {
            foreach(var bmp in downloads) panel.AddImage(bmp);
            status.Text = "Downloaded";
        }
        else
        {
            status.Text = "Timed out";
            downloads.ContinueWith(t => Log(t));
        }
    }
    finally { btnDownload.Enabled = true; }
}
```

## <a name="building-task-based-combinators"></a>Création de combinateurs basés sur les tâches
 Une tâche étant en mesure de représenter une opération asynchrone et de fournir des fonctions synchrones et asynchrones pour effectuer la liaison avec l’opération, récupérer ses résultats et ainsi de suite, vous pouvez créer des bibliothèques utiles de combinateurs qui composent les tâches pour créer des modèles plus grands.  Comme expliqué dans la section précédente, .NET Framework inclut plusieurs combinateurs intégrés, mais vous pouvez également créer les vôtres. Les sections suivantes fournissent plusieurs exemples de types et méthodes de combinateurs potentiels.

### <a name="retryonfault"></a>RetryOnFault
 Dans de nombreuses situations, vous souhaiterez peut-être retenter une opération si une tentative précédente échoue.  Pour le code synchrone, vous pouvez créer une méthode d’assistance telle que `RetryOnFault` dans l’exemple suivant pour y parvenir :

```csharp
public static T RetryOnFault<T>(
    Func<T> function, int maxTries)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return function(); }
        catch { if (i == maxTries-1) throw; }
    }
    return default(T);
}
```

 Vous pouvez créer une méthode d’assistance presque identique pour les opérations asynchrones qui sont implémentées avec TAP et donc renvoyer des tâches :

```csharp
public static async Task<T> RetryOnFault<T>(
    Func<Task<T>> function, int maxTries)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return await function().ConfigureAwait(false); }
        catch { if (i == maxTries-1) throw; }
    }
    return default(T);
}
```

 Vous pouvez ensuite utiliser ce combinateur pour encoder les nouvelles tentatives dans la logique de l’application ; par exemple :

```csharp
// Download the URL, trying up to three times in case of failure
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3);
```

 Vous pouvez étendre la fonction `RetryOnFault`. Par exemple, la fonction peut accepter une autre `Func<Task>` qui sera appelée entre chaque tentative pour déterminer quand recommencer l’opération, par exemple :

```csharp
public static async Task<T> RetryOnFault<T>(
    Func<Task<T>> function, int maxTries, Func<Task> retryWhen)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return await function().ConfigureAwait(false); }
        catch { if (i == maxTries-1) throw; }
        await retryWhen().ConfigureAwait(false);
    }
    return default(T);
}
```

 Vous pouvez ensuite utiliser la fonction comme suit pour attendre une seconde avant de recommencer l’opération :

```csharp
// Download the URL, trying up to three times in case of failure,
// and delaying for a second between retries
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));
```

### <a name="needonlyone"></a>NeedOnlyOne
 Parfois, vous pouvez tirer parti de la redondance pour améliorer la latence et les chances de réussite d’une opération.  Supposons que nous avons plusieurs services web qui fournissent des cotations boursières, mais qu’à différents moments de la journée, chaque service peut fournir différents niveaux de qualité et de réactivité.  Pour faire face à ces variations, vous pouvez émettre des demandes pour tous les services web et, dès que vous obtenez une réponse à partir d’un d’entre eux, annuler les demandes restantes.  Vous pouvez implémenter une fonction d’assistance pour faciliter l’implémentation de ce modèle commun de lancement de plusieurs opérations, d’attente qu’une d’entre elles se termine et d’annulation du reste. La fonction `NeedOnlyOne` dans l’exemple suivant illustre ce scénario :

```csharp
public static async Task<T> NeedOnlyOne(
    params Func<CancellationToken,Task<T>> [] functions)
{
    var cts = new CancellationTokenSource();
    var tasks = (from function in functions
                 select function(cts.Token)).ToArray();
    var completed = await Task.WhenAny(tasks).ConfigureAwait(false);
    cts.Cancel();
    foreach(var task in tasks)
    {
        var ignored = task.ContinueWith(
            t => Log(t), TaskContinuationOptions.OnlyOnFaulted);
    }
    return completed;
}
```

 Vous pouvez ensuite utiliser cette fonction comme suit :

```csharp
double currentPrice = await NeedOnlyOne(
    ct => GetCurrentPriceFromServer1Async("msft", ct),
    ct => GetCurrentPriceFromServer2Async("msft", ct),
    ct => GetCurrentPriceFromServer3Async("msft", ct));
```

### <a name="interleaved-operations"></a>Opérations entrelacées
 Il existe un problème potentiel de performances avec l’utilisation de la méthode <xref:System.Threading.Tasks.Task.WhenAny%2A> pour prendre en charge un scénario d’entrelacement quand vous travaillez avec de très grands ensembles de tâches. Chaque appel à <xref:System.Threading.Tasks.Task.WhenAny%2A> entraîne une continuation enregistrée avec chaque tâche. Pour N nombre de tâches, cela entraîne la création de continuations O (N<sup>2</sup>) au cours de la durée de vie de l’opération d’entrelacement. Si vous utilisez un grand nombre de tâches, vous pouvez utiliser un combinateur ( `Interleaved` dans l’exemple suivant) pour résoudre le problème de performances :

```csharp
static IEnumerable<Task<T>> Interleaved<T>(IEnumerable<Task<T>> tasks)
{
    var inputTasks = tasks.ToList();
    var sources = (from _ in Enumerable.Range(0, inputTasks.Count)
                   select new TaskCompletionSource<T>()).ToList();
    int nextTaskIndex = -1;
    foreach (var inputTask in inputTasks)
    {
        inputTask.ContinueWith(completed =>
        {
            var source = sources[Interlocked.Increment(ref nextTaskIndex)];
            if (completed.IsFaulted)
                source.TrySetException(completed.Exception.InnerExceptions);
            else if (completed.IsCanceled)
                source.TrySetCanceled();
            else
                source.TrySetResult(completed.Result);
        }, CancellationToken.None,
           TaskContinuationOptions.ExecuteSynchronously,
           TaskScheduler.Default);
    }
    return from source in sources
           select source.Task;
}
```

 Vous pouvez ensuite utiliser le combinateur pour traiter les résultats des tâches terminées ; par exemple :

```csharp
IEnumerable<Task<int>> tasks = ...;
foreach(var task in Interleaved(tasks))
{
    int result = await task;
    …
}
```

### <a name="whenallorfirstexception"></a>WhenAllOrFirstException
 Dans certains scénarios de dispersion/regroupement, vous souhaiterez attendre toutes les tâches dans un jeu, à moins qu’une d’elles rencontre une erreur, auquel cas vous souhaiterez cesser d’attendre dès que l’exception se produit.  Vous pouvez accomplir cela avec une méthode de combinateur comme `WhenAllOrFirstException` dans l’exemple suivant :

```csharp
public static Task<T[]> WhenAllOrFirstException<T>(IEnumerable<Task<T>> tasks)
{
    var inputs = tasks.ToList();
    var ce = new CountdownEvent(inputs.Count);
    var tcs = new TaskCompletionSource<T[]>();

    Action<Task> onCompleted = (Task completed) =>
    {
        if (completed.IsFaulted)
            tcs.TrySetException(completed.Exception.InnerExceptions);
        if (ce.Signal() && !tcs.Task.IsCompleted)
            tcs.TrySetResult(inputs.Select(t => t.Result).ToArray());
    };

    foreach (var t in inputs) t.ContinueWith(onCompleted);
    return tcs.Task;
}
```

## <a name="building-task-based-data-structures"></a>Création de structures de données basées sur les tâches
 Outre la possibilité de générer des combinateurs de tâches personnalisés, avoir une structure de données dans <xref:System.Threading.Tasks.Task> et <xref:System.Threading.Tasks.Task%601> qui représente les résultats d’une opération asynchrone et la synchronisation nécessaire pour la joindre en fait un type très puissant avec lequel vous pouvez créer des structures de données personnalisées à utiliser dans des scénarios asynchrones.

### <a name="asynccache"></a>AsyncCache
 Un aspect important d’une tâche est qu’elle peut être remise à plusieurs consommateurs, qui peuvent tous utiliser await dessus, enregistrer des continuations de registre dessus, obtenir ses résultats ou exceptions (dans le cas de <xref:System.Threading.Tasks.Task%601>), et ainsi de suite.  Cela permet d’utiliser parfaitement <xref:System.Threading.Tasks.Task> et <xref:System.Threading.Tasks.Task%601> dans une infrastructure de mise en cache asynchrone.  Voici un exemple de cache asynchrone petit, mais puissant, reposant sur <xref:System.Threading.Tasks.Task%601> :

```csharp
public class AsyncCache<TKey, TValue>
{
    private readonly Func<TKey, Task<TValue>> _valueFactory;
    private readonly ConcurrentDictionary<TKey, Lazy<Task<TValue>>> _map;

    public AsyncCache(Func<TKey, Task<TValue>> valueFactory)
    {
        if (valueFactory == null) throw new ArgumentNullException("loader");
        _valueFactory = valueFactory;
        _map = new ConcurrentDictionary<TKey, Lazy<Task<TValue>>>();
    }

    public Task<TValue> this[TKey key]
    {
        get
        {
            if (key == null) throw new ArgumentNullException("key");
            return _map.GetOrAdd(key, toAdd =>
                new Lazy<Task<TValue>>(() => _valueFactory(toAdd))).Value;
        }
    }
}
```

 La [classe \<TKey,TValue> classe asynccache](https://devblogs.microsoft.com/pfxteam/parallelextensionsextras-tour-12-asynccache/) accepte comme délégué à son constructeur une fonction qui prend un `TKey` et retourne un <xref:System.Threading.Tasks.Task%601> .  Toutes les valeurs précédemment accessibles à partir du cache sont stockées dans le dictionnaire interne, et `AsyncCache` garantit qu’une seule tâche est générée par clé, même en cas d’accès simultané au cache.

 Par exemple, vous pouvez créer un cache de pages web téléchargées :

```csharp
private AsyncCache<string,string> m_webPages =
    new AsyncCache<string,string>(DownloadStringAsync);
```

 Vous pouvez ensuite utiliser ce cache dans les méthodes asynchrones chaque fois que vous avez besoin du contenu d’une page web. La classe `AsyncCache` garantit que vous téléchargez aussi peu de pages que possible, et met les résultats en cache.

```csharp
private async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.IsEnabled = false;
    try
    {
        txtContents.Text = await m_webPages["https://www.microsoft.com"];
    }
    finally { btnDownload.IsEnabled = true; }
}
```

### <a name="asyncproducerconsumercollection"></a>AsyncProducerConsumerCollection
 Vous pouvez également utiliser des tâches pour créer des structures de données pour la coordination des activités asynchrones.  Considérez un des modèles de conception parallèle classiques : le modèle producteur/consommateur.  Dans ce modèle, les producteurs génèrent des données qui sont utilisées par les consommateurs, et les producteurs et les consommateurs peuvent s’exécuter en parallèle. Par exemple, le consommateur traite l’élément 1, qui a été généré précédemment par un producteur qui produit maintenant l’élément 2.  Dans le modèle producteur/consommateur, vous avez toujours besoin d’une structure de données pour stocker les données créées par les producteurs afin que les consommateurs puissent être informés des nouvelles données et le trouver lorsqu’elles sont disponibles.

 Voici une structure de données simple basée sur les tâches qui permet d’utiliser des méthodes asynchrones en tant que producteurs et consommateurs :

```csharp
public class AsyncProducerConsumerCollection<T>
{
    private readonly Queue<T> m_collection = new Queue<T>();
    private readonly Queue<TaskCompletionSource<T>> m_waiting =
        new Queue<TaskCompletionSource<T>>();

    public void Add(T item)
    {
        TaskCompletionSource<T> tcs = null;
        lock (m_collection)
        {
            if (m_waiting.Count > 0) tcs = m_waiting.Dequeue();
            else m_collection.Enqueue(item);
        }
        if (tcs != null) tcs.TrySetResult(item);
    }

    public Task<T> Take()
    {
        lock (m_collection)
        {
            if (m_collection.Count > 0)
            {
                return Task.FromResult(m_collection.Dequeue());
            }
            else
            {
                var tcs = new TaskCompletionSource<T>();
                m_waiting.Enqueue(tcs);
                return tcs.Task;
            }
        }
    }
}
```

 Avec cette structure de données en place, vous pouvez écrire le code suivant :

```csharp
private static AsyncProducerConsumerCollection<int> m_data = …;
…
private static async Task ConsumerAsync()
{
    while(true)
    {
        int nextItem = await m_data.Take();
        ProcessNextItem(nextItem);
    }
}
…
private static void Produce(int data)
{
    m_data.Add(data);
}
```

L’espace de noms <xref:System.Threading.Tasks.Dataflow> inclut le type <xref:System.Threading.Tasks.Dataflow.BufferBlock%601>, que vous pouvez utiliser de manière similaire, mais sans avoir à créer de type de collection personnalisé :

```csharp
private static BufferBlock<int> m_data = …;
…
private static async Task ConsumerAsync()
{
    while(true)
    {
        int nextItem = await m_data.ReceiveAsync();
        ProcessNextItem(nextItem);
    }
}
…
private static void Produce(int data)
{
    m_data.Post(data);
}
```

> [!NOTE]
> L’espace de noms <xref:System.Threading.Tasks.Dataflow> est disponible dans .NET Framework 4.5 via **NuGet**. Pour installer l’assembly qui contient l'espace de noms <xref:System.Threading.Tasks.Dataflow>, ouvrez votre projet dans Visual Studio, choisissez **Manage NuGet Packages** dans le menu Projet et recherchez en ligne le package Microsoft.Tpl.Dataflow.

## <a name="see-also"></a>Voir aussi

- [Modèle asynchrone basé sur les tâches (TAP, Task-based Asynchronous Pattern)](task-based-asynchronous-pattern-tap.md)
- [Implémentation du modèle asynchrone basé sur des tâches](implementing-the-task-based-asynchronous-pattern.md)
- [Interopérabilité avec d’autres types et modèles asynchrones](interop-with-other-asynchronous-patterns-and-types.md)
