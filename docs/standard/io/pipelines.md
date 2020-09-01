---
title: Pipelines d’e/s-.NET
description: Apprenez à utiliser efficacement des pipelines d’e/s dans .NET et évitez les problèmes dans votre code.
ms.date: 08/27/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- Pipelines
- Pipelines I/O
- I/O [.NET], Pipelines
author: rick-anderson
ms.author: riande
ms.openlocfilehash: a24d7f5c22c936cd3fd3fdc51f0f3ace56386574
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271982"
---
# <a name="systemiopipelines-in-net"></a>System. IO. pipelines dans .NET

<xref:System.IO.Pipelines> est une nouvelle bibliothèque conçue pour faciliter l’exécution d’e/s hautes performances dans .NET. Il s’agit d’une bibliothèque ciblant .NET Standard qui fonctionne sur toutes les implémentations .NET.

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a>Quel est le problème résolu par System. IO. pipelines ?

<!-- corner case doesn't MT (machine translate)   -->
Les applications qui analysent les données de streaming sont composées de code réutilisable avec de nombreux flux de code spécialisés et inhabituels. Le code réutilisable et cas particulier est complexe et difficile à gérer.

`System.IO.Pipelines` a été conçu pour :

* Ont des données de diffusion en continu d’analyse hautes performances.
* Réduisez la complexité du code.

Le code suivant est courant pour un serveur TCP qui reçoit des messages délimités par des lignes (délimités par `'\n'` ) d’un client :

```csharp
async Task ProcessLinesAsync(NetworkStream stream)
{
    var buffer = new byte[1024];
    await stream.ReadAsync(buffer, 0, buffer.Length);

    // Process a single line from the buffer
    ProcessLine(buffer);
}
```

Le code précédent présente plusieurs problèmes :

* Le message entier (fin de ligne) ne peut pas être reçu dans un seul appel à `ReadAsync` .
* Il ignore le résultat de `stream.ReadAsync` . `stream.ReadAsync` retourne la quantité de données qui a été lue.
* Elle ne gère pas le cas où plusieurs lignes sont lues en un seul `ReadAsync` appel.
* Elle alloue un `byte` tableau à chaque lecture.

Pour résoudre les problèmes précédents, les modifications suivantes sont requises :

* Met en mémoire tampon les données entrantes jusqu’à ce qu’une nouvelle ligne soit trouvée.
* Analyse toutes les lignes retournées dans la mémoire tampon.
* Il est possible que la ligne dépasse 1 Ko (1024 octets). Le code doit redimensionner la mémoire tampon d’entrée jusqu’à ce que le délimiteur soit trouvé afin d’ajuster la ligne complète à l’intérieur de la mémoire tampon.

  * Si la mémoire tampon est redimensionnée, davantage de copies de mémoire tampon sont effectuées à mesure que des lignes plus longues apparaissent dans l’entrée.
  * Pour réduire l’espace gaspillé, compactez la mémoire tampon utilisée pour la lecture des lignes.

* Envisagez d’utiliser le regroupement de mémoires tampons pour éviter d’allouer de la mémoire à plusieurs reprises.
* Le code suivant résout certains de ces problèmes :

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs" id="snippet":::

Le code précédent est complexe et ne traite pas tous les problèmes identifiés. La mise en réseau hautes performances implique généralement l’écriture de code très complexe pour optimiser les performances. `System.IO.Pipelines` a été conçu pour faciliter l’écriture de ce type de code.

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="pipe"></a>Pipe

La <xref:System.IO.Pipelines.Pipe> classe peut être utilisée pour créer une `PipeWriter/PipeReader` paire. Toutes les données écrites dans le `PipeWriter` sont disponibles dans le `PipeReader` :

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/Pipe.cs" id="snippet2":::

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a>Utilisation de base du canal

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/Pipe.cs" id="snippet":::

Il existe deux boucles :

* `FillPipeAsync` lit les `Socket` et écrit dans le `PipeWriter` .
* `ReadPipeAsync` lit `PipeReader` et analyse les lignes entrantes.

Aucune mémoire tampon explicite n’est allouée. La gestion de la mémoire tampon est déléguée aux `PipeReader` `PipeWriter` implémentations et. La délégation de la gestion des tampons facilite la consommation du code pour se concentrer uniquement sur la logique métier.

Dans la première boucle :

* <xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> est appelé pour récupérer la mémoire à partir du writer sous-jacent.
* <xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> est appelé pour indiquer la `PipeWriter` quantité de données qui a été écrite dans la mémoire tampon.
* <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> est appelé pour rendre les données disponibles pour le `PipeReader` .

Dans la deuxième boucle, le `PipeReader` consomme les mémoires tampons écrites par `PipeWriter` . Les mémoires tampons proviennent du Socket. L’appel à `PipeReader.ReadAsync` :

* Retourne un <xref:System.IO.Pipelines.ReadResult> qui contient deux informations importantes :

  * Données qui ont été lues sous la forme de `ReadOnlySequence<byte>` .
  * Valeur booléenne `IsCompleted` qui indique si la fin de données (EOF) a été atteinte.

Après avoir trouvé le délimiteur de fin de ligne (EOL) et l’analyse de la ligne :

* La logique traite la mémoire tampon pour ignorer ce qui est déjà traité.
* `PipeReader.AdvanceTo` est appelé pour indiquer la `PipeReader` quantité de données consommées et examinées.

Les boucles de lecteur et d’enregistreur se terminent en appelant `Complete` . `Complete` permet au canal sous-jacent de libérer la mémoire qu’il a allouée.

### <a name="backpressure-and-flow-control"></a>Contrôle de la contre-pression et du fluide

Dans l’idéal, la lecture et l’analyse fonctionnent ensemble :

* Le thread d’écriture consomme des données à partir du réseau et les place dans des tampons.
* Le thread d’analyse est chargé de construire les structures de données appropriées.

En règle générale, l’analyse prend plus de temps que la simple copie des blocs de données à partir du réseau :

* Le thread de lecture avance le thread d’analyse.
* Le thread de lecture doit ralentir ou allouer davantage de mémoire pour stocker les données du thread d’analyse.

Pour des performances optimales, il existe un équilibre entre les pauses fréquentes et l’allocation de mémoire supplémentaire.

Pour résoudre le problème précédent, le `Pipe` a deux paramètres pour contrôler le workflow de données :

* <xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Détermine la quantité de données qui doit être mise en mémoire tampon avant les appels à <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> suspendre.
* <xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Détermine la quantité de données que le lecteur doit observer avant d’appeler pour `PipeWriter.FlushAsync` reprendre.

![Diagramme avec ResumeWriterThreshold et PauseWriterThreshold](media/pipelines/resume-pause.png)

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:

* Retourne un incomplet `ValueTask<FlushResult>` lorsque la quantité de données dans le `Pipe` croise `PauseWriterThreshold` .
* Se termine `ValueTask<FlushResult>` lorsqu’il devient inférieur à `ResumeWriterThreshold` .

Deux valeurs sont utilisées pour empêcher un cycle rapide, ce qui peut se produire si une valeur est utilisée.

### <a name="examples"></a>Exemples

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a>PipeScheduler

En général, lors de l’utilisation de `async` et `await` , le code asynchrone reprend sur un <xref:System.Threading.Tasks.TaskScheduler> ou sur le actuel <xref:System.Threading.SynchronizationContext> .

Lors des e/s, il est important de contrôler précisément l’emplacement d’exécution des e/s. Ce contrôle permet de tirer efficacement parti des caches de l’UC. Une mise en cache efficace est essentielle pour les applications hautes performances, comme les serveurs Web. <xref:System.IO.Pipelines.PipeScheduler> permet de contrôler l’emplacement d’exécution des rappels asynchrones. Par défaut :

* Le actuel <xref:System.Threading.SynchronizationContext> est utilisé.
* S’il n’y `SynchronizationContext` en a pas, il utilise le pool de threads pour exécuter les rappels.

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/Program.cs" id="snippet":::

[PipeScheduler. ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) est l' <xref:System.IO.Pipelines.PipeScheduler> implémentation qui met en file d’attente les rappels dans le pool de threads. `PipeScheduler.ThreadPool` est la valeur par défaut et généralement le meilleur choix. [PipeScheduler. Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) peut entraîner des conséquences inattendues, telles que les blocages.

### <a name="pipe-reset"></a>Réinitialisation du canal

Il est souvent efficace de réutiliser l' `Pipe` objet. Pour réinitialiser le canal, appelez <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> quand et sont tous les deux `PipeReader` `PipeWriter` terminés.

## <a name="pipereader"></a>PipeReader

<xref:System.IO.Pipelines.PipeReader> gère la mémoire au nom de l’appelant. **Always** Appelez toujours <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> après l’appel de <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType> . Cela permet de `PipeReader` savoir quand l’appelant est en mesure d’effectuer un suivi de la mémoire. Le `ReadOnlySequence<byte>` retourné par `PipeReader.ReadAsync` est valide uniquement jusqu’à l’appel de `PipeReader.AdvanceTo` . Il n’est pas conforme d’utiliser `ReadOnlySequence<byte>` après l’appel de `PipeReader.AdvanceTo` .

`PipeReader.AdvanceTo` accepte deux <xref:System.SequencePosition> arguments :

* Le premier argument détermine la quantité de mémoire consommée.
* Le deuxième argument détermine la quantité de mémoire tampon observée.

Le marquage des données comme consommées signifie que le canal peut retourner la mémoire au pool de mémoires tampons sous-jacent. Le marquage des données comme observées détermine ce que fait l’appel suivant à `PipeReader.ReadAsync` . Le fait de marquer tout comme observé signifie que le prochain appel à `PipeReader.ReadAsync` ne retourne pas jusqu’à ce qu’il y ait plus de données écrites dans le canal. Toute autre valeur effectue l’appel suivant pour qu’il `PipeReader.ReadAsync` retourne immédiatement les données observées *et* non prises en compte, mais pas celles qui ont déjà été consommées.

### <a name="read-streaming-data-scenarios"></a>Lire les scénarios de données de streaming

Il existe deux modèles typiques qui émergent lorsque vous tentez de lire des données de streaming :

* En fonction d’un flux de données, analysez un message unique.
* À partir d’un flux de données, analysez tous les messages disponibles.

Les exemples suivants utilisent la `TryParseMessage` méthode pour analyser des messages à partir d’un `ReadOnlySequence<byte>` . `TryParseMessage` analyse un message unique et met à jour la mémoire tampon d’entrée pour supprimer le message analysé de la mémoire tampon. `TryParseMessage` ne fait pas partie de .NET, il s’agit d’une méthode écrite par l’utilisateur, utilisée dans les sections suivantes.

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a>Lire un seul message

Le code suivant lit un message unique à partir d’un `PipeReader` et le retourne à l’appelant.

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs" id="snippet":::

Le code précédent :

* Analyse un message unique.
* Met à jour le consommé `SequencePosition` et examiné `SequencePosition` pour qu’il pointe vers le début de la mémoire tampon d’entrée tronquée.

Les deux `SequencePosition` arguments sont mis à jour, car `TryParseMessage` supprime le message analysé de la mémoire tampon d’entrée. En général, lors de l’analyse d’un message unique à partir de la mémoire tampon, la position examinée doit être l’une des suivantes :

* Fin du message.
* Fin de la mémoire tampon reçue si aucun message n’a été trouvé.

Le cas de message unique présente le risque d’erreurs. Le passage des valeurs incorrectes à l' *examen* peut entraîner une exception de mémoire insuffisante ou une boucle infinie. Pour plus d’informations, consultez la section [problèmes courants PipeReader](#gotchas) dans cet article.

### <a name="reading-multiple-messages"></a>Lecture de plusieurs messages

Le code suivant lit tous les messages d’un `PipeReader` et appelle `ProcessMessageAsync` sur chacun d’eux.

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyConnection1.cs" id="snippet":::

### <a name="cancellation"></a>Annulation

`PipeReader.ReadAsync`:

* Prend en charge le passage d’un <xref:System.Threading.CancellationToken> .
* Lève une exception <xref:System.OperationCanceledException> si le `CancellationToken` est annulé alors qu’une lecture est en attente.
* Prend en charge un moyen d’annuler l’opération de lecture en cours via <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType> , ce qui évite de déclencher une exception. L’appel de `PipeReader.CancelPendingRead` entraîne l’appel de l’appel actuel ou suivant à `PipeReader.ReadAsync` pour retourner un <xref:System.IO.Pipelines.ReadResult> avec ayant la `IsCanceled` valeur `true` . Cela peut être utile pour arrêter la boucle de lecture existante de manière non destructrice et non exceptionnelle.

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyConnection.cs" id="snippet":::

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a>Problèmes courants liés à PipeReader

* Le passage des valeurs incorrectes à `consumed` ou `examined` peut entraîner la lecture des données déjà lues.
* Le passage `buffer.End` en tant que examiné peut aboutir à :

  * Données bloquées
  * Une exception éventuelle de mémoire insuffisante (insuffisance) si les données ne sont pas consommées. Par exemple, `PipeReader.AdvanceTo(position, buffer.End)` lors du traitement d’un seul message à la fois à partir de la mémoire tampon.

* Le passage des valeurs incorrectes à `consumed` ou `examined` peut entraîner une boucle infinie. Par exemple, `PipeReader.AdvanceTo(buffer.Start)` si `buffer.Start` l’opération n’a pas changé, le prochain appel à `PipeReader.ReadAsync` retourne immédiatement avant l’arrivée de nouvelles données.
* Le passage des valeurs incorrectes à `consumed` ou `examined` peut entraîner une mise en mémoire tampon infinie (éventuellement insuffisance).
* L’utilisation de `ReadOnlySequence<byte>` après l’appel `PipeReader.AdvanceTo` de peut entraîner une altération de la mémoire (à utiliser après Free).
* L’échec de `PipeReader.Complete/CompleteAsync` l’appel peut entraîner une fuite de mémoire.
* <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType>La vérification et la sortie de la logique de lecture avant le traitement de la mémoire tampon entraînent une perte de données. La condition de sortie de boucle doit être basée sur `ReadResult.Buffer.IsEmpty` et `ReadResult.IsCompleted` . Une telle erreur peut entraîner une boucle infinie.

#### <a name="problematic-code"></a>Code problématique

❌ **Perte de données**

Le `ReadResult` peut retourner le dernier segment de données lorsque `IsCompleted` a la valeur `true` . Le fait de ne pas lire ces données avant de quitter la boucle de lecture entraînera une perte de données.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Boucle infinie**

La logique suivante peut entraîner une boucle infinie si `Result.IsCompleted` est, `true` mais qu’il n’y a jamais de message complet dans la mémoire tampon.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet2":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

Voici un autre morceau de code avec le même problème. Il recherche une mémoire tampon non vide avant de procéder à la vérification `ReadResult.IsCompleted` . Dans la mesure où elle se trouve dans un `else if` , elle est en boucle infinie s’il n’y a jamais de message complet dans la mémoire tampon.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet3":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Blocage inattendu**

L’appel sans condition de `PipeReader.AdvanceTo` avec `buffer.End` dans la `examined` position peut entraîner des blocages lors de l’analyse d’un message unique. L’appel suivant à `PipeReader.AdvanceTo` ne retourne pas tant que :

* Il y a plus de données écrites dans le canal.
* Et les nouvelles données n’ont pas été examinées précédemment.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet4":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Mémoire insuffisante (insuffisance)**

Dans les conditions suivantes, le code suivant assure la mise en mémoire tampon jusqu’à ce qu’un <xref:System.OutOfMemoryException> se produise :

* Il n’y a aucune taille de message maximale.
* Les données retournées par le `PipeReader` ne font pas l’intégralité d’un message. Par exemple, il ne fait pas de message complet, car l’autre côté écrit un message volumineux (par exemple, un message de 4 Go).

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet5":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Altération** de la mémoire

Lors de l’écriture d’applications auxiliaires qui lisent la mémoire tampon, toute charge utile retournée doit être copiée avant d’appeler `Advance` . L’exemple suivant retourne la mémoire que le `Pipe` a ignoré et peut le réutiliser pour l’opération suivante (lecture/écriture).

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippetMessage":::

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet6":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a>PipeWriter

Le <xref:System.IO.Pipelines.PipeWriter> gère les mémoires tampons pour l’écriture au nom de l’appelant. `PipeWriter` implémente [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601) . `IBufferWriter<byte>` permet d’obtenir l’accès aux mémoires tampons pour effectuer des opérations d’écriture sans copie supplémentaire des mémoires tampons.

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyPipeWriter.cs" id="snippet":::

Le code précédent :

* Demande une mémoire tampon d’au moins 5 octets à l' `PipeWriter` aide de <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> .
* Écrit des octets pour la chaîne ASCII `"Hello"` dans le retourné `Memory<byte>` .
* Appelle <xref:System.IO.Pipelines.PipeWriter.Advance%2A> pour indiquer le nombre d’octets qui ont été écrits dans la mémoire tampon.
* Vide le `PipeWriter` , qui envoie les octets à l’appareil sous-jacent.

La méthode d’écriture précédente utilise les mémoires tampons fournies par `PipeWriter` . Vous pouvez également <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType> :

* Copie la mémoire tampon existante dans le `PipeWriter` .
* Appelle `GetSpan` , le `Advance` cas échéant, et appelle <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> .

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyPipeWriter.cs" id="snippet2":::

### <a name="cancellation"></a>Annulation

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> prend en charge le passage d’un <xref:System.Threading.CancellationToken> . La transmission d’un `CancellationToken` résultat dans un `OperationCanceledException` si le jeton est annulé alors qu’il y a un vidage en attente. `PipeWriter.FlushAsync` prend en charge un moyen d’annuler l’opération de vidage en cours via <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> sans lever d’exception. `PipeWriter.CancelPendingFlush`L’appel de entraîne l’appel actuel ou suivant à `PipeWriter.FlushAsync` ou `PipeWriter.WriteAsync` pour retourner un <xref:System.IO.Pipelines.FlushResult> avec ayant la `IsCanceled` valeur `true` . Cela peut être utile pour stopper le vidage à l’arrêt d’une façon non destructrice et non exceptionnelle.

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a>Problèmes courants liés à PipeWriter

* <xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> et <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> retournent une mémoire tampon avec au moins la quantité de mémoire demandée. **Ne** supposez pas des tailles de mémoire tampon exactes.
* Il n’y a aucune garantie que les appels successifs retourneront la même mémoire tampon ou la même mémoire tampon de taille.
* Une nouvelle mémoire tampon doit être demandée après l’appel <xref:System.IO.Pipelines.PipeWriter.Advance%2A> de pour continuer à écrire davantage de données. Impossible d’écrire dans la mémoire tampon acquise précédemment.
* L’appel de `GetMemory` ou `GetSpan` pendant qu’il y a un appel incomplet à `FlushAsync` n’est pas sécurisé.
* L’appel de `Complete` ou `CompleteAsync` pendant qu’il y a des données dévidées peut entraîner une altération de la mémoire.

## <a name="iduplexpipe"></a>IDuplexPipe

Le <xref:System.IO.Pipelines.IDuplexPipe> est un contrat pour les types qui prennent en charge la lecture et l’écriture. Par exemple, une connexion réseau est représentée par un `IDuplexPipe` .

 Contrairement à `Pipe` , qui contient un `PipeReader` et un `PipeWriter` , `IDuplexPipe` représente un côté unique d’une connexion duplex intégral. Cela signifie que ce qui est écrit dans le n’est `PipeWriter` pas lu à partir du `PipeReader` .

## <a name="streams"></a>Flux

Lors de la lecture ou de l’écriture de données de flux, vous lisez généralement les données à l’aide d’un désérialiseur et écrivez des données à l’aide d’un sérialiseur. La plupart de ces API de flux de lecture et d’écriture ont un `Stream` paramètre. Pour faciliter l’intégration avec ces API existantes `PipeReader` et `PipeWriter` exposer une <xref:System.IO.Pipelines.PipeReader.AsStream%2A> méthode. <xref:System.IO.Pipelines.PipeWriter.AsStream%2A> retourne une `Stream` implémentation autour de `PipeReader` ou `PipeWriter` .

### <a name="stream-example"></a>Exemple de flux

`PipeReader``PipeWriter`les instances et peuvent être créées à l’aide des méthodes statiques à partir `Create` d’un <xref:System.IO.Stream> objet et d’options de création correspondantes facultatives.

Le <xref:System.IO.Pipelines.StreamPipeReaderOptions> permet de contrôler la création de l' `PipeReader` instance avec les paramètres suivants :

- <xref:System.IO.Pipelines.StreamPipeReaderOptions.BufferSize?displayProperty=nameWithType> taille minimale de la mémoire tampon, en octets, utilisée lors de la location de mémoire à partir du pool, et la valeur par défaut est `4096` .
- <xref:System.IO.Pipelines.StreamPipeReaderOptions.LeaveOpen?displayProperty=nameWithType> indicateur détermine si le flux sous-jacent est laissé ouvert après la `PipeReader` fin de la, et prend par défaut la valeur `false` .
- <xref:System.IO.Pipelines.StreamPipeReaderOptions.MinimumReadSize?displayProperty=nameWithType> représente le seuil des octets restants dans la mémoire tampon avant l’allocation d’une nouvelle mémoire tampon, et la valeur par défaut de `1024` .
- <xref:System.IO.Pipelines.StreamPipeReaderOptions.Pool?displayProperty=nameWithType> est `MemoryPool<byte>` utilisé lors de l’allocation de mémoire, et prend par défaut la valeur `null` .

Le <xref:System.IO.Pipelines.StreamPipeWriterOptions> permet de contrôler la création de l' `PipeWriter` instance avec les paramètres suivants :

- <xref:System.IO.Pipelines.StreamPipeWriterOptions.LeaveOpen?displayProperty=nameWithType> indicateur détermine si le flux sous-jacent est laissé ouvert après la `PipeWriter` fin de la, et prend par défaut la valeur `false` .
- <xref:System.IO.Pipelines.StreamPipeWriterOptions.MinimumBufferSize?displayProperty=nameWithType> représente la taille de mémoire tampon minimale à utiliser lors de la location de mémoire à partir de la <xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool> , et la valeur par défaut est `4096` .
- <xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool?displayProperty=nameWithType> est `MemoryPool<byte>` utilisé lors de l’allocation de mémoire, et prend par défaut la valeur `null` .

> [!IMPORTANT]
> Lorsque `PipeReader` vous créez des `PipeWriter` instances et à l’aide des `Create` méthodes, vous devez prendre en compte la `Stream` durée de vie des objets. Si vous avez besoin d’accéder au flux une fois que le lecteur ou l’enregistreur est terminé, vous devez définir l' `LeaveOpen` indicateur `true` sur dans les options de création. Dans le cas contraire, le flux est fermé.

Le code suivant illustre la création d' `PipeReader` `PipeWriter` instances et à l’aide des `Create` méthodes d’un flux.

:::code language="csharp" source="snippets/pipelines/Program.cs":::

L’application utilise un <xref:System.IO.StreamReader> pour lire le fichier *lorem-ipsum.txt* sous forme de flux. <xref:System.IO.FileStream>Est passé à <xref:System.IO.Pipelines.PipeReader.Create%2A?displayProperty=nameWithType> , qui instancie un `PipeReader` objet. L’application console transmet ensuite son flux de sortie standard à <xref:System.IO.Pipelines.PipeWriter.Create%2A?displayProperty=nameWithType> à l’aide de <xref:System.Console.OpenStandardOutput?displayProperty=nameWithType> . L’exemple prend en charge l' [annulation](#cancellation).
