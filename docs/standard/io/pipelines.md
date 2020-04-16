---
title: I/O pipelines - .NET
description: Apprenez à utiliser efficacement les pipelines I/O en .NET et évitez les problèmes de votre code.
ms.date: 10/01/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- Pipelines
- Pipelines I/O
- I/O [.NET], Pipelines
author: rick-anderson
ms.author: riande
ms.openlocfilehash: 8822e731ae805e83d4072c5bd78dff3fcf9a31a1
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81462519"
---
# <a name="systemiopipelines-in-net"></a>System.IO.Pipelines en .NET

<xref:System.IO.Pipelines>est une nouvelle bibliothèque qui est conçu pour le rendre plus facile à faire haute performance I / O en .NET. C’est une bibliothèque ciblant .NET Standard qui fonctionne sur toutes les implémentations .NET.

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a>Quel problème le problème ne System.IO.Pipelines résoudre

<!-- corner case doesn't MT (machine translate)   -->
Les applications qui analysent les données de streaming sont composées de code boilerplate ayant de nombreux flux de code spécialisés et inhabituels. La plaque chauffante et le code de cas spécial est complexe et difficile à entretenir.

`System.IO.Pipelines`a été conçu pour :

* Avoir des données de diffusion en continu de haute performance.
* Réduisez la complexité du code.

Le code suivant est typique pour un serveur TCP qui reçoit des `'\n'`messages délimités en ligne (délimités par) d’un client :

```csharp
async Task ProcessLinesAsync(NetworkStream stream)
{
    var buffer = new byte[1024];
    await stream.ReadAsync(buffer, 0, buffer.Length);

    // Process a single line from the buffer
    ProcessLine(buffer);
}
```

Le code précédent a plusieurs problèmes :

* L’ensemble du message (fin de ligne) pourrait `ReadAsync`ne pas être reçu en un seul appel à .
* C’est ignorer le `stream.ReadAsync`résultat de . `stream.ReadAsync`retourne la quantité de données lues.
* Il ne gère pas le cas où `ReadAsync` plusieurs lignes sont lues en un seul appel.
* Il alloue un `byte` tableau à chaque lecture.

Pour résoudre les problèmes précédents, les changements suivants sont nécessaires :

* Tamponner les données entrantes jusqu’à ce qu’une nouvelle ligne soit trouvée.
* Parse toutes les lignes retournées dans le tampon.
* Il est possible que la ligne soit supérieure à 1 KB (1024 octets). Le code doit resize le tampon d’entrée jusqu’à ce que le délimitateur soit trouvé afin d’adapter la ligne complète à l’intérieur du tampon.

  * Si le tampon est resized, plus de copies tampons sont faites à mesure que des lignes plus longues apparaissent dans l’entrée.
  * Pour réduire l’espace gaspillé, compactez le tampon utilisé pour les lignes de lecture.

* Envisagez d’utiliser la mise en commun des tampons pour éviter d’allouer la mémoire à plusieurs reprises.
* Le code suivant traite de certains de ces problèmes :

[!code-csharp[](~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs?name=snippet)]

Le code précédent est complexe et ne traite pas de tous les problèmes identifiés. Le réseautage haute performance signifie généralement écrire du code très complexe pour maximiser les performances. `System.IO.Pipelines`a été conçu pour faciliter l’écriture de ce type de code.

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="pipe"></a>Pipe

La <xref:System.IO.Pipelines.Pipe> classe peut être `PipeWriter/PipeReader` utilisée pour créer une paire. Toutes les données `PipeWriter` inscrites `PipeReader`dans le est disponible dans le :

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet2)]

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a>Utilisation de base de pipe

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet)]

Il y a deux boucles :

* `FillPipeAsync`lit de `Socket` la et `PipeWriter`écrit à la .
* `ReadPipeAsync`lit à `PipeReader` partir des lignes entrantes et analyse.

Il n’y a pas de tampons explicites alloués. Toute gestion des tampons `PipeReader` `PipeWriter` est déléguée aux mises en œuvre et aux mises en œuvre. La délégation de la gestion des tampons permet de se concentrer plus facilement sur la logique métier.

Dans la première boucle:

* <xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType>est appelé à obtenir la mémoire de l’écrivain sous-jacent.
* <xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType>est appelé à `PipeWriter` dire combien de données ont été écrites au tampon.
* <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>est appelé à mettre les `PipeReader`données à la disposition du .

Dans la deuxième `PipeReader` boucle, le consomme `PipeWriter`les tampons écrits par . Les tampons proviennent de la prise. L’appel `PipeReader.ReadAsync`à :

* Renvoie <xref:System.IO.Pipelines.ReadResult> un qui contient deux éléments d’information importants :

  * Les données qui ont été `ReadOnlySequence<byte>`lues sous la forme de .
  * Un boolean `IsCompleted` qui indique si la fin des données (EOF) a été atteinte.

Après avoir trouvé la fin de la ligne (EOL) délimiter et d’analyser la ligne:

* La logique traite le tampon pour sauter ce qui est déjà traité.
* `PipeReader.AdvanceTo`est appelé à `PipeReader` dire combien de données ont été consommées et examinées.

Le lecteur et les boucles `Complete`d’écrivain se terminent par l’appel . `Complete`permet au Tuyau sous-jacent de libérer la mémoire qu’il a allouée.

### <a name="backpressure-and-flow-control"></a>Rétropression et contrôle du débit

Idéalement, la lecture et l’analyse travaillent ensemble :

* Le fil d’écriture consomme les données du réseau et les met dans des tampons.
* Le fil d’analyse est responsable de la construction des structures de données appropriées.

En règle générale, l’analyse prend plus de temps que de simplement copier des blocs de données du réseau :

* Le fil de lecture prend de l’avance sur le fil d’analyse.
* Le fil de lecture doit soit ralentir ou allouer plus de mémoire pour stocker les données pour le fil d’analyse.

Pour des performances optimales, il y a un équilibre entre les pauses fréquentes et l’attribution de plus de mémoire.

Pour résoudre le problème `Pipe` précédent, le a deux paramètres pour contrôler le flux de données:

* <xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Détermine la quantité de données qui <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> doivent être tamponnées avant les appels à faire une pause.
* <xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Détermine la quantité de données que `PipeWriter.FlushAsync` le lecteur doit observer avant les appels à reprendre.

![Diagramme avec ResumeWriterThreshold et PauseWriterThreshold](./media/pipelines/resume-pause.png)

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:

* Retourne une `ValueTask<FlushResult>` incomplet lorsque `Pipe` la `PauseWriterThreshold`quantité de données dans les croix .
* Se `ValueTask<FlushResult>` termine quand il `ResumeWriterThreshold`devient inférieur à .

Deux valeurs sont utilisées pour prévenir le cycle rapide, qui peut se produire si une valeur est utilisée.

### <a name="examples"></a>Exemples

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a>PipeScheduler PipeScheduler

Typiquement lors `async` `await`de l’utilisation et , code asynchrone reprend sur un <xref:System.Threading.Tasks.TaskScheduler> ou sur le courant <xref:System.Threading.SynchronizationContext>.

Lorsque vous faites I / O, il est important d’avoir un contrôle à grain fin sur l’endroit où l’I / O est effectué. Ce contrôle permet de tirer parti efficacement des caches CPU. La mise en cache efficace est essentielle pour les applications haute performance comme les serveurs Web. <xref:System.IO.Pipelines.PipeScheduler>donne un contrôle sur l’endroit où les rappels asynchrones s’exécutent. Par défaut :

* Le <xref:System.Threading.SynchronizationContext> courant est utilisé.
* S’il n’y a pas, `SynchronizationContext`il utilise le pool de thread pour exécuter des rappels.

[!code-csharp[](~/samples/snippets/csharp/pipelines/Program.cs?name=snippet)]

[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) est <xref:System.IO.Pipelines.PipeScheduler> la mise en œuvre que les files d’attente rappelle à la piscine de fil. `PipeScheduler.ThreadPool`est la valeur par défaut et généralement le meilleur choix. [PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) peut causer des conséquences imprévues telles que des impasses.

### <a name="pipe-reset"></a>Réinitialisation de tuyau

Il est souvent efficace de `Pipe` réutiliser l’objet. Pour réinitialiser le `PipeReader` `PipeWriter` tuyau, appelez <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> lorsque le et sont terminés.

## <a name="pipereader"></a>PipeReader PipeReader

<xref:System.IO.Pipelines.PipeReader>gère la mémoire au nom de l’appelant. **Toujours** <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> appeler <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>après avoir appelé . Cela permet `PipeReader` de savoir quand l’appelant est fait avec la mémoire afin qu’il puisse être suivi. Le `ReadOnlySequence<byte>` retour `PipeReader.ReadAsync` n’est valable `PipeReader.AdvanceTo`que jusqu’à l’appel le . Il est illégal `ReadOnlySequence<byte>` d’utiliser après avoir appelé `PipeReader.AdvanceTo`.

`PipeReader.AdvanceTo`prend <xref:System.SequencePosition> deux arguments:

* Le premier argument détermine la quantité de mémoire consommée.
* Le deuxième argument détermine la quantité de tampon observée.

Le marquage des données consommées signifie que le tuyau peut retourner la mémoire dans le pool tampon sous-jacent. Le marquage des données observées `PipeReader.ReadAsync` contrôle ce que le prochain appel à faire. Marquer tout ce qui est `PipeReader.ReadAsync` observé signifie que le prochain appel à ne pas revenir jusqu’à ce qu’il y ait plus de données écrites sur le tuyau. Toute autre valeur fera le `PipeReader.ReadAsync` prochain appel pour revenir immédiatement avec les données observées *et* non observées, mais pas les données qui ont déjà été consommées.

### <a name="read-streaming-data-scenarios"></a>Lire les scénarios de données en streaming

Il ya un couple de modèles typiques qui émergent lorsque vous essayez de lire les données en streaming:

* Compte tenu d’un flux de données, analysez un seul message.
* Compte tenu d’un flux de données, analysez tous les messages disponibles.

Les exemples `TryParseMessage` suivants utilisent la méthode `ReadOnlySequence<byte>`pour analyser les messages à partir d’un . `TryParseMessage`analyse un seul message et met à jour le tampon d’entrée pour couper le message analysé à partir du tampon. `TryParseMessage`ne fait pas partie de .NET, c’est une méthode écrite par l’utilisateur utilisée dans les sections suivantes.

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a>Lire un seul message

Le code suivant lit un `PipeReader` seul message à partir d’un et le renvoie à l’appelant.

[!code-csharp[ReadSingleMsg](~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs?name=snippet)]

Le code précédent :

* Parses un seul message.
* Mises à `SequencePosition` jour `SequencePosition` de la consommation et examinée pour indiquer le début du tampon d’entrée coupé.

Les `SequencePosition` deux arguments `TryParseMessage` sont mis à jour parce que supprime le message analysé du tampon d’entrée. En général, lors de l’analyse d’un seul message à partir du tampon, la position examinée doit être l’une des suivantes :

* La fin du message.
* La fin du tampon reçu si aucun message n’a été trouvé.

Le cas de message unique a le plus de potentiel d’erreurs. Passer les mauvaises valeurs à *examiner* peut entraîner une exception hors mémoire ou une boucle infinie. Pour plus d’informations, consultez la section [des problèmes courants de PipeReader](#gotchas) dans cet article.

### <a name="reading-multiple-messages"></a>Lecture de plusieurs messages

Le code suivant lit `PipeReader` tous `ProcessMessageAsync` les messages d’un et appelle sur chacun.

[!code-csharp[MyConnection1](~/samples/snippets/csharp/pipelines/MyConnection1.cs?name=snippet)]

### <a name="cancellation"></a>Annulation

`PipeReader.ReadAsync`:

* Soutient l’adoption d’un <xref:System.Threading.CancellationToken>.
* Jette un <xref:System.OperationCanceledException> si `CancellationToken` le est annulé alors qu’il ya une lecture en attente.
* Prend en charge un moyen <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>d’annuler l’opération de lecture en cours via , ce qui évite de soulever une exception. L’appel `PipeReader.CancelPendingRead` provoque l’appel actuel <xref:System.IO.Pipelines.ReadResult> `IsCanceled` ou `true`suivant pour `PipeReader.ReadAsync` retourner un avec réglé à . Cela peut être utile pour arrêter la boucle de lecture existante d’une manière non destructive et non exceptionnelle.

[!code-csharp[MyConnection](~/samples/snippets/csharp/pipelines/MyConnection.cs?name=snippet)]

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a>Problèmes courants PipeReader

* Passer les mauvaises `consumed` `examined` valeurs à ou peut entraîner la lecture déjà des données lues.
* La `buffer.End` réussite examinée peut entraîner :

  * Données bloquées
  * Peut-être une éventuelle exception hors mémoire (OOM) si les données ne sont pas consommées. Par exemple, `PipeReader.AdvanceTo(position, buffer.End)` lors du traitement d’un seul message à la fois à partir du tampon.

* Passer les mauvaises `consumed` `examined` valeurs à ou peut entraîner une boucle infinie. Par `PipeReader.AdvanceTo(buffer.Start)` exemple, `buffer.Start` si n’a pas changé `PipeReader.ReadAsync` fera le prochain appel de revenir immédiatement avant l’arrivée de nouvelles données.
* Passer les mauvaises `consumed` `examined` valeurs à l’OOM ou peut entraîner une mise en mémoire tampon infinie (éventuellement OOM).
* L’utilisation `PipeReader.AdvanceTo` de l’appel `ReadOnlySequence<byte>` après peut entraîner une corruption de mémoire (utilisation après gratuit).
* Ne pas `PipeReader.Complete/CompleteAsync` appeler peut entraîner une fuite de mémoire.
* La <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> vérification et la sortie de la logique de lecture avant le traitement du tampon entraînent une perte de données. L’état de sortie `ReadResult.Buffer.IsEmpty` de `ReadResult.IsCompleted`boucle doit être basé sur et . Faire cela incorrectement pourrait entraîner une boucle infinie.

#### <a name="problematic-code"></a>Code problématique

❌**Perte de données**

Le `ReadResult` peut retourner le segment `IsCompleted` final `true`de données quand est réglé à . Ne pas lire ces données avant de sortir de la boucle de lecture entraînera une perte de données.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#1](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Boucle infinie**

La logique suivante peut entraîner une `Result.IsCompleted` `true` boucle infinie si l’est, mais il n’y a jamais un message complet dans le tampon.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#2](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet2)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

Voici un autre morceau de code avec le même problème. Il vérifie un tampon non vide `ReadResult.IsCompleted`avant de vérifier . Parce qu’il `else if`est dans un , il va boucler pour toujours s’il n’y a jamais un message complet dans le tampon.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#3](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet3)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Hang inattendu**

Appeler `PipeReader.AdvanceTo` sans `buffer.End` condition `examined` dans la position peut entraîner des pendaisons lors de l’analyse d’un seul message. Le prochain `PipeReader.AdvanceTo` appel à ne pas revenir jusqu’à ce que:

* Il y a plus de données écrites sur le tuyau.
* Et les nouvelles données n’ont pas été examinées auparavant.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#4](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet4)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Hors mémoire (OOM)**

Dans les conditions suivantes, le code <xref:System.OutOfMemoryException> suivant conserve la mise en mémoire tampon jusqu’à ce qu’un se produise :

* Il n’y a pas de taille maximale de message.
* Les données retournées de la `PipeReader` ne fait pas un message complet. Par exemple, il ne fait pas un message complet parce que l’autre côté écrit un grand message (par exemple, un message de 4 Go).

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#5](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet5)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Corruption de mémoire**

Lors de l’écriture d’aides qui lisent le `Advance`tampon, toute charge utile retournée doit être copiée avant d’appeler . L’exemple suivant rendra `Pipe` la mémoire que le a jeté et peut la réutiliser pour la prochaine opération (lire/écrire).

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#Message](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippetMessage)]

[!code-csharp[DoNotUse#6](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet6)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a>PipeWriter (pipeWriter)

Le <xref:System.IO.Pipelines.PipeWriter> gère les tampons pour écrire au nom de l’appelant. `PipeWriter`met [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601)en œuvre . `IBufferWriter<byte>`permet d’avoir accès à des tampons pour effectuer des écritures sans copies tampons supplémentaires.

[!code-csharp[MyPipeWriter](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet)]

Le code précédent:

* Demande un tampon d’au moins `PipeWriter` 5 octets de l’utilisation <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>.
* Écrit des octets pour `"Hello"` la chaîne `Memory<byte>`ASCII au retour .
* Appels <xref:System.IO.Pipelines.PipeWriter.Advance%2A> pour indiquer combien d’octets ont été écrits au tampon.
* Flushes `PipeWriter`le , qui envoie les octets à l’appareil sous-jacent.

La méthode précédente d’écriture utilise `PipeWriter`les tampons fournis par le . Alternativement, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:

* Copie le tampon `PipeWriter`existant à la .
* Appels `GetSpan` `Advance` , le <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>cas échéant et les appels .

[!code-csharp[MyPipeWriter#2](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet2)]

### <a name="cancellation"></a>Annulation

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>soutient l’adoption d’un <xref:System.Threading.CancellationToken>. Passer `CancellationToken` un résultat `OperationCanceledException` dans un si le jeton est annulé alors qu’il ya une chasse d’eau en attente. `PipeWriter.FlushAsync`prend en charge un moyen <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> d’annuler l’opération de chasse d’eau en cours via sans soulever une exception. `PipeWriter.CancelPendingFlush` L’appel provoque l’appel `PipeWriter.WriteAsync` actuel <xref:System.IO.Pipelines.FlushResult> ou `IsCanceled` suivant `true`à `PipeWriter.FlushAsync` ou de retourner un avec réglé à . Cela peut être utile pour arrêter la chasse d’eau de rendement d’une manière non destructive et non exceptionnelle.

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a>Problèmes courants PipeWriter

* <xref:System.IO.Pipelines.PipeWriter.GetSpan%2A>et <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> retourner un tampon avec au moins la quantité demandée de mémoire. **N’assumez pas** les tailles exactes de tampon.
* Il n’y a aucune garantie que les appels successifs retourneront le même tampon ou le même tampon de taille.
* Un nouveau tampon doit <xref:System.IO.Pipelines.PipeWriter.Advance%2A> être demandé après avoir appelé pour continuer à écrire plus de données. Le tampon précédemment acquis ne peut pas être écrit à.
* Appeler `GetMemory` `GetSpan` ou pendant qu’il `FlushAsync` y a un appel incomplet n’est pas sûr.
* Appeler `Complete` `CompleteAsync` ou pendant qu’il y a des données non gonflées peut entraîner une corruption de la mémoire.

## <a name="iduplexpipe"></a>IDuplexPipe

Il <xref:System.IO.Pipelines.IDuplexPipe> s’agit d’un contrat pour les types qui prennent en charge à la fois la lecture et l’écriture. Par exemple, une connexion réseau serait `IDuplexPipe`représentée par un .

 Contrairement `Pipe` à `PipeReader` ce `PipeWriter`qui `IDuplexPipe` contient a et a , représente un seul côté d’une connexion en duplex complet. Cela signifie que ce `PipeWriter` qui est écrit `PipeReader`à la volonté ne sera pas lu de la .

## <a name="streams"></a>Flux

Lorsque vous lisez ou écrivez des données de flux, vous lisez généralement des données à l’aide d’un dé-serializer et écrivez des données à l’aide d’un sérialisateur. La plupart de ces API `Stream` de lecture et d’écriture ont un paramètre. Pour faciliter l’intégration à ces `PipeReader` API existantes, et `PipeWriter` exposer un <xref:System.IO.Pipelines.PipeReader.AsStream%2A>.  <xref:System.IO.Pipelines.PipeWriter.AsStream%2A>retourne `Stream` une mise `PipeReader` `PipeWriter`en œuvre autour de la ou .
